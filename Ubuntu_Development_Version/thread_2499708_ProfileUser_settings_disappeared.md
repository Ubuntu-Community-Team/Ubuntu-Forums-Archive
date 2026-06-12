---
title: "Profile/User settings disappeared"
date: 2024-08-07
forum: Ubuntu Development Version
---

### Post by ubername on 2024-08-07
Hi. When I logged in today, after rebooting from yesterday's session, most of my user configuration options had been reset to defaults. e.g. my GNOME terminal profiles had gone, my dash no longer had my apps pinned to it, but the defaults had reappeared, the desktop background had been reset  etc. Any clues as to a: why/how it happened and b: how I can restore? Thanks in advance.

(Obvs, I do an apt update && apt full-upgrade at least once a day so my hunch is it was something in yesterday's updates (6 July to avoid confusing our friends who differently format DD/MM))

---

### Post by #&amp;thj^% on 2024-08-07
August 6th or July 6th?   I noticed it yesterday on XFCE4 as well, I have not looked at my updates yet other pressing matters first.

---

### Post by #&amp;thj^% on 2024-08-07
So I reverted back 1 week, all is as it should be.
Now the upgrades again
```

Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  nvidia-firmware-555-555.52.04 python3-proton-vpn-connection python3-proton-vpn-killswitch
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  libibmad5 libibumad3 libjxl0.10 libnvidia-egl-wayland1 libpoppler140
  nvidia-firmware-555-555.58.02 python3-proton-vpn-killswitch-network-manager-wireguard
  python3-proton-vpn-network-manager-wireguard
The following packages will be upgraded:
  amd64-microcode apparmor apparmor-utils apport apport-core-dump-handler apport-gtk apt apt-utils
  bpfcc-tools conky-all cpio cpp-13 cpp-13-x86-64-linux-gnu cpp-14 cpp-14-x86-64-linux-gnu dpkg
  dpkg-dev dvisvgm evolution-data-server-common firefox g++-14 g++-14-x86-64-linux-gnu gcc-13
  gcc-13-base gcc-13-x86-64-linux-gnu gcc-14 gcc-14-base gcc-14-x86-64-linux-gnu gcr4 gdebi
  gdebi-core gettext gettext-base gimp gimp-data gir1.2-glib-2.0 gir1.2-gst-plugins-bad-1.0
  gir1.2-gst-plugins-base-1.0 gir1.2-gstreamer-1.0 gir1.2-nm-1.0 gir1.2-vte-2.91
  gsettings-desktop-schemas gstreamer1.0-alsa gstreamer1.0-gl gstreamer1.0-plugins-bad
  gstreamer1.0-plugins-base gstreamer1.0-plugins-ugly gstreamer1.0-tools gstreamer1.0-vaapi
  gstreamer1.0-x kwin-common kwin-data kwin-x11 libamdhip64-5 libapparmor1 libappimage1.0abi1t64
  libapt-pkg6.0t64 libasan8 libatomic1 libbpfcc libcamel-1.2-64t64 libcares2 libcc1-0
  libcryptsetup12 libdpkg-perl libdrm-amdgpu1 libdrm-common libdrm-dev libdrm-intel1
  libdrm-nouveau2 libdrm-radeon1 libdrm2 libdynaloader-functions-perl libebackend-1.2-11t64
  libebook-1.2-21t64 libebook-contacts-1.2-4t64 libedata-book-1.2-27t64 libedataserver-1.2-27t64
  libfftw3-double3 libfftw3-single3 libfribidi0 libgcc-13-dev libgcc-14-dev libgcc-s1 libgck-2-2
  libgcr-4-4 libgdcm-dev libgdcm3.0t64 libgfortran5 libgimp2.0t64 libgirepository-2.0-0
  libglib2.0-0t64 libglib2.0-bin libglib2.0-data libglib2.0-dev libglib2.0-dev-bin libgomp1
  libgstreamer-gl1.0-0 libgstreamer-opencv1.0-0 libgstreamer-plugins-bad1.0-0
  libgstreamer-plugins-bad1.0-dev libgstreamer-plugins-base1.0-0 libgstreamer-plugins-base1.0-dev
  libgstreamer1.0-0 libgstreamer1.0-dev libhtml-parser-perl libhwasan0 libimlib2t64
  libio-stringy-perl libitm1 libjs-sphinxdoc libkpathsea6 libkwineffects14 libkwinglutils14
  libllvm17t64 liblouisutdml-bin liblouisutdml-data liblouisutdml9t64 liblsan0 libmysqlclient21
  libnetpbm11t64 libnm0 libnvidia-cfg1-555 libnvidia-common-555 libnvidia-compute-555
  libnvidia-decode-555 libnvidia-encode-555 libnvidia-extra-555 libnvidia-fbc1-555
  libnvidia-gl-555 libnvme1t64 libobjc4 libopenconnect5 libpcsclite1 libpipewire-0.3-0t64
  libpipewire-0.3-common libpipewire-0.3-modules libpoppler-cpp1 libpoppler-glib8t64
  libpoppler-qt5-1t64 libptexenc1 libpython3-stdlib libqalculate-data libqalculate23
  libqt5concurrent5t64 libqt5core5t64 libqt5dbus5t64 libqt5gui5t64 libqt5network5t64
  libqt5opengl5t64 libqt5printsupport5t64 libqt5sql5-mysql libqt5sql5-sqlite libqt5sql5t64
  libqt5test5t64 libqt5waylandclient5 libqt5waylandcompositor5 libqt5widgets5t64 libqt5xml5t64
  libqt6core6t64 libqt6dbus6 libqt6gui6 libqt6network6 libqt6opengl6 libqt6sql6 libqt6sql6-sqlite
  libqt6widgets6 libqt6xml6 libquadmath0 librabbitmq4 libsdl2-2.0-0 libsepol-dev libsepol2
  libspa-0.2-bluetooth libspa-0.2-modules libssh2-1t64 libssl3t64 libstdc++-14-dev libstdc++6
  libsuperlu6 libsynctex2 libtdb1 libtexlua53-5 libthunarx-3-0 libtsan2 libubsan1 libucx0
  libvte-2.91-0 libvte-2.91-common libwayland-bin libwayland-client0 libwayland-cursor0
  libwayland-dev libwayland-egl1 libwayland-server0 libxapian30 lintian linux-firmware lzip
  media-player-info netpbm network-manager nvidia-compute-utils-555 nvidia-dkms-555
  nvidia-driver-555 nvidia-kernel-common-555 nvidia-kernel-source-555 nvidia-utils-555
  openssh-client openssl pcmciautils pipewire pipewire-alsa pipewire-audio-client-libraries
  pipewire-bin pipewire-jack pipewire-pulse poppler-utils proton-vpn-gnome-desktop
  proton-vpn-gtk-app python3 python3-apparmor python3-apport python3-bpfcc python3-click
  python3-constantly python3-cpuinfo python3-distupgrade python3-gdbm python3-hyperlink
  python3-importlib-metadata python3-libapparmor python3-mako python3-minimal python3-numpy
  python3-problem-report python3-proton-core python3-proton-vpn-api-core
  python3-proton-vpn-killswitch-network-manager python3-proton-vpn-network-manager python3-six
  python3-tdb python3-tk python3-twisted python3-zipp qt5-gtk-platformtheme qt6-gtk-platformtheme
  qt6-qpa-plugins qtwayland5 spice-vdagent surfshark tdb-tools texlive-binaries thunar thunar-data
  tpm-udev ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk xfburn xfce4-power-manager
  xfce4-power-manager-data xfce4-power-manager-plugins xserver-xorg-video-nvidia-555 zip
264 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,177 MB of archives.
After this operation, 84.2 MB of additional disk space will be used.
Do you want to continue? [Y/n] 


```
Nothing stands out, but possibles are:
```
  gsettings-desktop-schemas  python3-tdb python3-tk python3-twisted python3-zipp qt5-gtk-platformtheme qt6-gtk-platformtheme
  qt6-qpa-plugins qtwayland5 spice-vdagent surfshark tdb-tools texlive-binaries thunar thunar-data
  tpm-udev ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk xfburn xfce4-power-manager
  xfce4-power-manager-data xfce4-power-manager-plugins xserver-xorg-video-nvidia-555 zip
```
After a reboot I'll check again

---

### Post by #&amp;thj^% on 2024-08-07
Disregard all the above, Mine was due to "importing my rpool to my Arch server, I needed some stuff.
I found that in my terminal history.

Happenstance that we both noticed a similar setting change.

All Good Here, but I hope you find your culprit.

---

### Post by ubername on 2024-08-08
Thanks! Sorry about the month confusion - you were right, Aug 6. I am afraid I do not know how to revert 1 week, nor how to find my culprit, but I am glad you got sorted. It implies my settings are still kicking around somewhere - I just need to find them and re-use. (Or at least use them to remind me what and how to reconfigure)

---

### Post by #&amp;thj^% on 2024-08-08
Typically I keep at least 2 copies of ".config" and "cache" or Just a copy of my entire "/home/USER" on a backup drive.

My revert comes from a snapshot, not to be confused with snap or snapd...(Yuck ;))

I'm surprised at how many folks don't use back-ups of any kind, they are literally data life-savers, should any form of disaster hit.

---

