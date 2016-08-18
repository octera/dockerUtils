FROM resin/raspberrypi2-node:latest

# Install apt deps
RUN apt-get clean && apt-get update && apt-get install -y \
  apt-utils \
  xserver-xorg-core xserver-xorg-input-all xserver-xorg-video-fbdev xorg \
  libgtk2.0 libxss1 libgconf2-dev libasound2 libnss3\
  clang \
  fluxbox \
  libraspberrypi0 \
  fbset \
  usbutils \
  omxplayer \
  && rm -rf /var/lib/apt/lists/*

# Set Xorg and FLUXBOX preferences
RUN mkdir ~/.fluxbox
RUN echo "xset s off\nxserver-command=X -s 0 dpms" > ~/.fluxbox/startup
RUN echo "#!/bin/sh\n\nexec /usr/bin/X -s 0 dpms -nocursor -nolisten tcp "$@"" > /etc/X11/xinit/xserverrc

# Set npm
RUN npm config set unsafe-perm true
