---
title: "Need help, installed gprolog on my 20.04 server and it installed everything"
date: 2022-11-15
forum: Server Platforms
---

### Post by 21Jerry on 2022-11-15
I had been using gprolog, the prolog programming language, at the command line for a while.  I forgot I had to change my path, typed in "gprolog", ubuntu said it wasn't found, and can be installed with "sudo apt install gprolog".  I figured, what the hell, it would probably clean up my path problem.  I had installed it manually a while back. I wasn't paying attention to the installation list and said "yes".   Apt then decided to install **everything** to make my server a desktop, I assume, because it installed X, gnome, etc.  The list is almost endless.

I went into the apt log and I can find all the packages, but I'm worried about just manually telling apt to uninstall them. 

Here's what it installed below.  Is it possible to fix this easily? I run owncloud, minidlna, and postfix mail server (iredmail) on this machine and that's it.

Thanks,

Jerry

```

The following additional packages will be installed:
  adwaita-icon-theme apg aptdaemon aptdaemon-data aspell aspell-en
  at-spi2-core avahi-utils bluez bubblewrap cheese-common colord colord-data
  cracklib-runtime cups-pk-helper dbus-x11 dconf-cli desktop-file-utils
  docbook-xml enchant-2 evolution-data-server evolution-data-server-common
  fprintd gcr gdm3 geoclue-2.0 gir1.2-accountsservice-1.0 gir1.2-atk-1.0
  gir1.2-atspi-2.0 gir1.2-freedesktop gir1.2-gck-1 gir1.2-gcr-3
  gir1.2-gdesktopenums-3.0 gir1.2-gdkpixbuf-2.0 gir1.2-gdm-1.0
  gir1.2-geoclue-2.0 gir1.2-gnomebluetooth-1.0 gir1.2-gnomedesktop-3.0
  gir1.2-graphene-1.0 gir1.2-gtk-3.0 gir1.2-gweather-3.0 gir1.2-ibus-1.0
  gir1.2-json-1.0 gir1.2-mutter-6 gir1.2-nm-1.0 gir1.2-nma-1.0
  gir1.2-notify-0.7 gir1.2-pango-1.0 gir1.2-polkit-1.0 gir1.2-rsvg-2.0
  gir1.2-secret-1 gir1.2-soup-2.4 gir1.2-upowerglib-1.0 gir1.2-vte-2.91 gjs
  gkbd-capplet gnome-control-center gnome-control-center-data
  gnome-control-center-faces gnome-desktop3-data gnome-icon-theme
  gnome-keyring gnome-keyring-pkcs11 gnome-menus gnome-online-accounts
  gnome-session-bin gnome-session-common gnome-settings-daemon
  gnome-settings-daemon-common gnome-shell gnome-shell-common
  gnome-startup-applications gnome-user-docs gprolog-doc
  gstreamer1.0-clutter-3.0 gstreamer1.0-gl gstreamer1.0-plugins-good
  gstreamer1.0-pulseaudio gstreamer1.0-x gtk-update-icon-cache
  hicolor-icon-theme humanity-icon-theme hunspell-en-us ibus ibus-data
  ibus-gtk ibus-gtk3 iio-sensor-proxy im-config ippusbxd
  language-selector-gnome libaa1 libappindicator3-1 libasound2-plugins
  libaspell15 libasyncns0 libatk-bridge2.0-0 libatk1.0-0 libatk1.0-data
  libatspi2.0-0 libavahi-glib1 libavc1394-0 libbluetooth3 libcaca0
  libcamel-1.2-62 libcanberra-gtk3-0 libcanberra-gtk3-module libcanberra-pulse
  libcheese-gtk25 libcheese8 libclutter-1.0-0 libclutter-1.0-common
  libclutter-gst-3.0-0 libclutter-gtk-1.0-0 libcogl-common libcogl-pango20
  libcogl-path20 libcogl20 libcolord-gtk1 libcolord2 libcolorhug2 libcrack2
  libdbusmenu-glib4 libdbusmenu-gtk3-4 libdv4 libebackend-1.2-10
  libebook-1.2-20 libebook-contacts-1.2-3 libecal-2.0-1 libedata-book-1.2-26
  libedata-cal-2.0-1 libedataserver-1.2-24 libedataserverui-1.2-2 libegl-mesa0
  libegl1 libenchant-2-2 libepoxy0 libfile-basedir-perl
  libfile-desktopentry-perl libfile-mimeinfo-perl libfontenc1 libfprint-2-2
  libgail-common libgail18 libgbm1 libgck-1-0 libgcr-base-3-1 libgcr-ui-3-1
  libgdata-common libgdata22 libgdm1 libgee-0.8-2 libgeoclue-2-0
  libgeocode-glib0 libgirara-gtk3-3 libgjs0g libgl1 libgl1-mesa-dri
  libglapi-mesa libgles2 libglvnd0 libglx-mesa0 libglx0 libgnome-autoar-0-0
  libgnome-bluetooth13 libgnome-desktop-3-19 libgnomekbd-common libgnomekbd8
  libgoa-1.0-0b libgoa-1.0-common libgoa-backend-1.0-1 libgphoto2-6
  libgphoto2-l10n libgphoto2-port12 libgraphene-1.0-0 libgsound0
  libgssdp-1.2-0 libgstreamer-gl1.0-0 libgstreamer-plugins-good1.0-0
  libgtk-3-0 libgtk-3-bin libgtk-3-common libgtk2.0-0 libgtk2.0-bin
  libgtk2.0-common libgtop-2.0-11 libgtop2-common libgupnp-1.2-0
  libgupnp-av-1.0-2 libgupnp-dlna-2.0-3 libgweather-3-16 libgweather-common
  libharfbuzz-icu0 libhunspell-1.7-0 libhyphen0 libibus-1.0-5 libical3 libice6
  libiec61883-0 libieee1284-3 libinput-bin libinput10
  libipc-system-simple-perl libjack-jackd2-0 libjavascriptcoregtk-4.0-18
  libmbim-glib4 libmbim-proxy libmediaart-2.0-0 libmm-glib0 libmozjs-68-0
  libmtdev1 libmutter-6-0 libndp0 libnet-dbus-perl libnm0 libnma0 libnotify4
  libopengl0 libpam-fprintd libpam-gnome-keyring libpangoxft-1.0-0
  libpcsclite1 libpeas-1.0-0 libpeas-common libphonenumber7 libprotobuf17
  libpulse-mainloop-glib0 libpulse0 libpulsedsp libpwquality-common
  libpwquality1 libqmi-glib5 libqmi-proxy libraw1394-11 librest-0.7-0
  librygel-core-2.6-2 librygel-db-2.6-2 librygel-renderer-2.6-2
  librygel-server-2.6-2 libsamplerate0 libsane libsane-common libsbc1
  libsecret-1-0 libsecret-common libshout3 libsm6 libsnapd-glib1 libsndfile1
  libsnmp-base libsnmp35 libsoup-gnome2.4-1 libspeexdsp1
  libstartup-notification0 libsynctex2 libtag1v5 libtag1v5-vanilla
  libteamdctl0 libtie-ixhash-perl libv4l-0 libv4lconvert0 libvte-2.91-0
  libvte-2.91-common libvulkan1 libwacom-bin libwacom-common libwacom2
  libwayland-client0 libwayland-cursor0 libwayland-egl1 libwayland-server0
  libwebkit2gtk-4.0-37 libwebpdemux2 libwebrtc-audio-processing1
  libwhoopsie-preferences0 libwhoopsie0 libwoff1 libx11-protocol-perl
  libxatracker2 libxaw7 libxcb-glx0 libxcb-icccm4 libxcb-image0
  libxcb-keysyms1 libxcb-randr0 libxcb-render-util0 libxcb-res0 libxcb-shape0
  libxcb-util1 libxcb-xkb1 libxcb-xv0 libxcomposite1 libxcursor1 libxdamage1
  libxfont2 libxft2 libxi6 libxinerama1 libxkbcommon-x11-0 libxkbcommon0
  libxkbfile1 libxklavier16 libxml-twig-perl libxml-xpathengine-perl libxmu6
  libxrandr2 libxss1 libxt6 libxtst6 libxv1 libxvmc1 libxxf86dga1 libxxf86vm1
  libyelp0 mesa-vulkan-drivers midori mobile-broadband-provider-info
  modemmanager mousetweaks mutter mutter-common network-manager
  network-manager-gnome network-manager-pptp p11-kit p11-kit-modules
  pinentry-gnome3 ppp pptp-linux pulseaudio pulseaudio-module-bluetooth
  pulseaudio-utils python3-aptdaemon python3-aptdaemon.gtk3widgets
  python3-cairo python3-cups python3-cupshelpers python3-defer
  python3-ibus-1.0 python3-macaroonbakery python3-protobuf rtkit rygel
  sane-utils session-migration sgml-base sgml-data switcheroo-control
  system-config-printer system-config-printer-common
  system-config-printer-udev ubuntu-docs ubuntu-mono ubuntu-session
  ubuntu-wallpapers ubuntu-wallpapers-focal usb-modeswitch usb-modeswitch-data
  whoopsie-preferences wpasupplicant x11-common x11-utils x11-xkb-utils
  x11-xserver-utils xdg-dbus-proxy xdg-utils xfonts-base xfonts-encodings
  xfonts-utils xml-core xserver-common xserver-xephyr xserver-xorg
  xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-libinput
  xserver-xorg-input-wacom xserver-xorg-legacy xserver-xorg-video-all
  xserver-xorg-video-amdgpu xserver-xorg-video-ati xserver-xorg-video-fbdev
  xserver-xorg-video-intel xserver-xorg-video-nouveau xserver-xorg-video-qxl
  xserver-xorg-video-radeon xserver-xorg-video-vesa xserver-xorg-video-vmware
  xwayland yaru-theme-gnome-shell yelp yelp-xsl zathura zathura-pdf-poppler
  zenity zenity-common
Suggested packages:
  aspell-doc spellutils colord-sensor-argyll docbook docbook-dsssl docbook-xsl
  docbook-defguide evolution gnome-orca gnome-software | gnome-packagekit
  gnome-user-share realmd libcanberra-gtk-module usbguard chrome-gnome-shell
  gir1.2-telepathyglib-0.12 gnome-themes-standard-data gnome-backgrounds
  gir1.2-telepathylogger-0.2 hunspell openoffice.org-hunspell
  | openoffice.org-core ibus-clutter ibus-doc indicator-application libdv-bin
  oss-compat libenchant-2-voikko gphoto2 gvfs jackd2 pcscd libraw1394-doc
  hplip snmp-mibs-downloader gstreamer1.0-libav libunicode-map8-perl
  libunicode-string-perl xml-twig-tools avahi-autoipd libteam-utils
  network-manager-openconnect-gnome network-manager-openvpn-gnome
  network-manager-vpnc-gnome network-manager-pptp-gnome pinentry-doc pavumeter
  pavucontrol paman paprefs ubuntu-sounds gstreamer1.0-plugins-ugly
  rygel-playbin rygel-preferences rygel-ruih rygel-tracker tumbler unpaper
  sgml-base-doc perlsgml w3-recs opensp libxml2-utils gnome-software
  python3-smbc ubuntu-wallpapers-karmic ubuntu-wallpapers-lucid
  ubuntu-wallpapers-maverick ubuntu-wallpapers-natty ubuntu-wallpapers-oneiric
  ubuntu-wallpapers-precise ubuntu-wallpapers-quantal ubuntu-wallpapers-raring
  ubuntu-wallpapers-saucy ubuntu-wallpapers-trusty ubuntu-wallpapers-utopic
  ubuntu-wallpapers-vivid ubuntu-wallpapers-wily ubuntu-wallpapers-xenial
  ubuntu-wallpapers-yakkety ubuntu-wallpapers-zesty ubuntu-wallpapers-artful
  ubuntu-wallpapers-bionic ubuntu-wallpapers-cosmic ubuntu-wallpapers-disco
  ubuntu-wallpapers-eoan comgt wvdial wpagui libengine-pkcs11-openssl
  mesa-utils nickle cairo-5c xorg-docs-core xfonts-100dpi | xfonts-75dpi
  xfonts-scalable xinput firmware-amd-graphics xserver-xorg-video-r128
  xserver-xorg-video-mach64 firmware-misc-nonfree zathura-ps zathura-djvu
  zathura-cb
The following NEW packages will be installed:
  adwaita-icon-theme apg aptdaemon aptdaemon-data aspell aspell-en
  at-spi2-core avahi-utils bluez bubblewrap cheese-common colord colord-data
  cracklib-runtime cups-pk-helper dbus-x11 dconf-cli desktop-file-utils
  docbook-xml enchant-2 evolution-data-server evolution-data-server-common
  fprintd gcr gdm3 geoclue-2.0 gir1.2-accountsservice-1.0 gir1.2-atk-1.0
  gir1.2-atspi-2.0 gir1.2-freedesktop gir1.2-gck-1 gir1.2-gcr-3
  gir1.2-gdesktopenums-3.0 gir1.2-gdkpixbuf-2.0 gir1.2-gdm-1.0
  gir1.2-geoclue-2.0 gir1.2-gnomebluetooth-1.0 gir1.2-gnomedesktop-3.0
  gir1.2-graphene-1.0 gir1.2-gtk-3.0 gir1.2-gweather-3.0 gir1.2-ibus-1.0
  gir1.2-json-1.0 gir1.2-mutter-6 gir1.2-nm-1.0 gir1.2-nma-1.0
  gir1.2-notify-0.7 gir1.2-pango-1.0 gir1.2-polkit-1.0 gir1.2-rsvg-2.0
  gir1.2-secret-1 gir1.2-soup-2.4 gir1.2-upowerglib-1.0 gir1.2-vte-2.91 gjs
  gkbd-capplet gnome-control-center gnome-control-center-data
  gnome-control-center-faces gnome-desktop3-data gnome-icon-theme
  gnome-keyring gnome-keyring-pkcs11 gnome-menus gnome-online-accounts
  gnome-session-bin gnome-session-common gnome-settings-daemon
  gnome-settings-daemon-common gnome-shell gnome-shell-common
  gnome-startup-applications gnome-user-docs gprolog gprolog-doc
  gstreamer1.0-clutter-3.0 gstreamer1.0-gl gstreamer1.0-plugins-good
  gstreamer1.0-pulseaudio gstreamer1.0-x gtk-update-icon-cache
  hicolor-icon-theme humanity-icon-theme hunspell-en-us ibus ibus-data
  ibus-gtk ibus-gtk3 iio-sensor-proxy im-config ippusbxd
  language-selector-gnome libaa1 libappindicator3-1 libasound2-plugins
  libaspell15 libasyncns0 libatk-bridge2.0-0 libatk1.0-0 libatk1.0-data
  libatspi2.0-0 libavahi-glib1 libavc1394-0 libbluetooth3 libcaca0
  libcamel-1.2-62 libcanberra-gtk3-0 libcanberra-gtk3-module libcanberra-pulse
  libcheese-gtk25 libcheese8 libclutter-1.0-0 libclutter-1.0-common
  libclutter-gst-3.0-0 libclutter-gtk-1.0-0 libcogl-common libcogl-pango20
  libcogl-path20 libcogl20 libcolord-gtk1 libcolord2 libcolorhug2 libcrack2
  libdbusmenu-glib4 libdbusmenu-gtk3-4 libdv4 libebackend-1.2-10
  libebook-1.2-20 libebook-contacts-1.2-3 libecal-2.0-1 libedata-book-1.2-26
  libedata-cal-2.0-1 libedataserver-1.2-24 libedataserverui-1.2-2 libegl-mesa0
  libegl1 libenchant-2-2 libepoxy0 libfile-basedir-perl
  libfile-desktopentry-perl libfile-mimeinfo-perl libfontenc1 libfprint-2-2
  libgail-common libgail18 libgbm1 libgck-1-0 libgcr-base-3-1 libgcr-ui-3-1
  libgdata-common libgdata22 libgdm1 libgee-0.8-2 libgeoclue-2-0
  libgeocode-glib0 libgirara-gtk3-3 libgjs0g libgl1 libgl1-mesa-dri
  libglapi-mesa libgles2 libglvnd0 libglx-mesa0 libglx0 libgnome-autoar-0-0
  libgnome-bluetooth13 libgnome-desktop-3-19 libgnomekbd-common libgnomekbd8
  libgoa-1.0-0b libgoa-1.0-common libgoa-backend-1.0-1 libgphoto2-6
  libgphoto2-l10n libgphoto2-port12 libgraphene-1.0-0 libgsound0
  libgssdp-1.2-0 libgstreamer-gl1.0-0 libgstreamer-plugins-good1.0-0
  libgtk-3-0 libgtk-3-bin libgtk-3-common libgtk2.0-0 libgtk2.0-bin
  libgtk2.0-common libgtop-2.0-11 libgtop2-common libgupnp-1.2-0
  libgupnp-av-1.0-2 libgupnp-dlna-2.0-3 libgweather-3-16 libgweather-common
  libharfbuzz-icu0 libhunspell-1.7-0 libhyphen0 libibus-1.0-5 libical3 libice6
  libiec61883-0 libieee1284-3 libinput-bin libinput10
  libipc-system-simple-perl libjack-jackd2-0 libjavascriptcoregtk-4.0-18
  libmbim-glib4 libmbim-proxy libmediaart-2.0-0 libmm-glib0 libmozjs-68-0
  libmtdev1 libmutter-6-0 libndp0 libnet-dbus-perl libnm0 libnma0 libnotify4
  libopengl0 libpam-fprintd libpam-gnome-keyring libpangoxft-1.0-0
  libpcsclite1 libpeas-1.0-0 libpeas-common libphonenumber7 libprotobuf17
  libpulse-mainloop-glib0 libpulse0 libpulsedsp libpwquality-common
  libpwquality1 libqmi-glib5 libqmi-proxy libraw1394-11 librest-0.7-0
  librygel-core-2.6-2 librygel-db-2.6-2 librygel-renderer-2.6-2
  librygel-server-2.6-2 libsamplerate0 libsane libsane-common libsbc1
  libsecret-1-0 libsecret-common libshout3 libsm6 libsnapd-glib1 libsndfile1
  libsnmp-base libsnmp35 libsoup-gnome2.4-1 libspeexdsp1
  libstartup-notification0 libsynctex2 libtag1v5 libtag1v5-vanilla
  libteamdctl0 libtie-ixhash-perl libv4l-0 libv4lconvert0 libvte-2.91-0
  libvte-2.91-common libvulkan1 libwacom-bin libwacom-common libwacom2
  libwayland-client0 libwayland-cursor0 libwayland-egl1 libwayland-server0
  libwebkit2gtk-4.0-37 libwebpdemux2 libwebrtc-audio-processing1
  libwhoopsie-preferences0 libwhoopsie0 libwoff1 libx11-protocol-perl
  libxatracker2 libxaw7 libxcb-glx0 libxcb-icccm4 libxcb-image0
  libxcb-keysyms1 libxcb-randr0 libxcb-render-util0 libxcb-res0 libxcb-shape0
  libxcb-util1 libxcb-xkb1 libxcb-xv0 libxcomposite1 libxcursor1 libxdamage1
  libxfont2 libxft2 libxi6 libxinerama1 libxkbcommon-x11-0 libxkbcommon0
  libxkbfile1 libxklavier16 libxml-twig-perl libxml-xpathengine-perl libxmu6
  libxrandr2 libxss1 libxt6 libxtst6 libxv1 libxvmc1 libxxf86dga1 libxxf86vm1
  libyelp0 mesa-vulkan-drivers midori mobile-broadband-provider-info
  modemmanager mousetweaks mutter mutter-common network-manager
  network-manager-gnome network-manager-pptp p11-kit p11-kit-modules
  pinentry-gnome3 ppp pptp-linux pulseaudio pulseaudio-module-bluetooth
  pulseaudio-utils python3-aptdaemon python3-aptdaemon.gtk3widgets
  python3-cairo python3-cups python3-cupshelpers python3-defer
  python3-ibus-1.0 python3-macaroonbakery python3-protobuf rtkit rygel
  sane-utils session-migration sgml-base sgml-data switcheroo-control
  system-config-printer system-config-printer-common
  system-config-printer-udev ubuntu-docs ubuntu-mono ubuntu-session
  ubuntu-wallpapers ubuntu-wallpapers-focal usb-modeswitch usb-modeswitch-data
  whoopsie-preferences wpasupplicant x11-common x11-utils x11-xkb-utils
  x11-xserver-utils xdg-dbus-proxy xdg-utils xfonts-base xfonts-encodings
  xfonts-utils xml-core xserver-common xserver-xephyr xserver-xorg
  xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-libinput
  xserver-xorg-input-wacom xserver-xorg-legacy xserver-xorg-video-all
  xserver-xorg-video-amdgpu xserver-xorg-video-ati xserver-xorg-video-fbdev
  xserver-xorg-video-intel xserver-xorg-video-nouveau xserver-xorg-video-qxl
  xserver-xorg-video-radeon xserver-xorg-video-vesa xserver-xorg-video-vmware
  xwayland yaru-theme-gnome-shell yelp yelp-xsl zathura zathura-pdf-poppler
  zenity zenity-common

```

---

### Post by Holger_Gehrke on 2022-11-15
I'd remove gprolog with 'sudo apt remove --purge gprolog' and then do a simulation of the removal of orphaned packages with 'apt-get -s autoremove'. If the latter doesn't show any packages you still need being candidates for removal, re-run that command but omit the '-s' (simulation) option and prepend a 'sudo'. 

The probable cause for your problem are recommended packages. Those are optional dependencies which will get installed unless you give the option '--no-install-recommends'. 'gprolog' recommends 'gprolog-doc' which recommends 'www-browser' and 'pdf-viewer'. I don't quite understand why these two virtual packages (there are no such packages, but packages can 'provide' the virtual package by having a header 'Provides: pdf-viewer') lead to the installation of most of a complete desktop, but since 'gprolog' has only 'libc6' as a dependency and gprolog-doc has none but both have recommendations they are the only explanation.

And regarding the path problem that led to this situation: add the directory where the gprolog executable resides to PATH by adding a line like 'PATH=$PATH:/directory/with/gprolog/in/it/' to your ~/.bashrc. After restarting you shell / logging out and back in you should then be able to call gprolog no matter what your current working directory is.

Holger

---

### Post by 21Jerry on 2022-11-15
thanks, Holger, I'll give that a try when I get back from my next meeting.

Jerry

---

### Post by 21Jerry on 2022-12-12
I have to kick this open.  For a number of reasons, I never was able to find the time to take steps to remove everything installed by accident.  Over the weekend, the power went out, the UPS failed, machine rebooted and the console came up as a desktop.  This caused pain for me as I couldn't get into terminal.  Then the machine started shutting down.  Turns out it was going into suspend due to a power timeout setup by the desktop.  

So I need to fix this issue.  I have the logs.  I know a little about apt.  I'm worried about removing libraries that could be used for other things.  I use the server for backups for timemachine, file history on PCs, amanda backups, owncloud (mostly) postfix email server using iRedmail architecture, and minidlna. I use it as a cloud for rsync backups as well.  My primary concern is why it started up as a desktop on the console machine.

If I were to reinstall ubuntu server, I assume it would wipeout all my apps above, correct.

How should I proceed?

THanks,

Jerry

---

### Post by 21Jerry on 2022-12-12
I did a 'sudo apt remove gprolog' and it printed this:

The following packages were automatically installed and are no longer required:

augeas-lenses libaugeas0 **python3-acme** python3-augeas **python3-certbot** python3-configargparse python3-future
  python3-icu python3-josepy python3-mock python3-parsedatetime python3-pbr python3-requests-toolbelt
  python3-zope.component python3-zope.event python3-zope.hookable

The two I marked in bold, Certbot and acme are used for renewing my certificates.  Why would it be listing that stuff?  

I then did a 'apt-get -s autoremove'  and it wants to remove those packages, 16 in total and I don't see like the x-desktop (or whatever it is called) or anything related.  When the desktop came up, nothing worked except the browser.  Anyway, I sort of hosed up my server, if it can even be called that anymore.

My brother mentioned something about being able to boot a previous install?  Is there a way to rollback these changes?

Advice?

Thanks.

---

### Post by ajgreeny on 2022-12-12
I think your best course of action is exactly what Holger suggested in post #2 as that will remove everything that was installed along with your chosen gprolog and should get you back to the position you were in before this happened.

Let this be a warning to read carefully exactly what is going to happen when running any apt command in order to avoid getting into such unexpected situations.

Good luck!

---

### Post by HermanAB on 2022-12-12
In my experience, when messing with startup stuff, first ensure that the SSH server is working, then you can connect from another machine when you cannot get into a local terminal.

---

### Post by MAFoElffen on 2022-12-12
You have the list of everything it installed as new... I use lists to do migrations. This would be the opposite:
```

#!/bin/bash

# The list of what it said it installed as new
prog_set=' adwaita-icon-theme
    apg 
    aptdaemon 
    aptdaemon-data 
    aspell 
    aspell-en
    at-spi2-core 
    avahi-utils 
    bluez 
    bubblewrap 
    cheese-common 
    colord 
    colord-data
    cracklib-runtime 
    cups-pk-helper 
    dbus-x11 
    dconf-cli 
    desktop-file-utils
    docbook-xml 
    enchant-2 
    evolution-data-server 
    evolution-data-server-common
    fprintd 
    gcr 
    gdm3 
    geoclue-2.0 
    gir1.2-accountsservice-1.0 
    gir1.2-atk-1.0
    gir1.2-atspi-2.0 
    gir1.2-freedesktop 
    gir1.2-gck-1 
    gir1.2-gcr-3
    gir1.2-gdesktopenums-3.0 
    gir1.2-gdkpixbuf-2.0 
    gir1.2-gdm-1.0
    gir1.2-geoclue-2.0 
    gir1.2-gnomebluetooth-1.0 
    gir1.2-gnomedesktop-3.0
    gir1.2-graphene-1.0 
    gir1.2-gtk-3.0 
    gir1.2-gweather-3.0 
    gir1.2-ibus-1.0
    gir1.2-json-1.0 
    gir1.2-mutter-6 
    gir1.2-nm-1.0 
    gir1.2-nma-1.0
    gir1.2-notify-0.7 
    gir1.2-pango-1.0 
    gir1.2-polkit-1.0 
    gir1.2-rsvg-2.0
    gir1.2-secret-1 
    gir1.2-soup-2.4 
    gir1.2-upowerglib-1.0 
    gir1.2-vte-2.91 gjs
    gkbd-capplet 
    gnome-control-center 
    gnome-control-center-data
    gnome-control-center-faces 
    gnome-desktop3-data 
    gnome-icon-theme
    gnome-keyring 
    gnome-keyring-pkcs11 
    gnome-menus 
    gnome-online-accounts
    gnome-session-bin 
    gnome-session-common 
    gnome-settings-daemon
    gnome-settings-daemon-common 
    gnome-shell 
    gnome-shell-common
    gnome-startup-applications 
    gnome-user-docs 
    gprolog 
    gprolog-doc
    gstreamer1.0-clutter-3.0 
    gstreamer1.0-gl 
    gstreamer1.0-plugins-good
    gstreamer1.0-pulseaudio 
    gstreamer1.0-x 
    gtk-update-icon-cache
    hicolor-icon-theme 
    humanity-icon-theme 
    hunspell-en-us 
    ibus 
    ibus-data
    ibus-gtk 
    ibus-gtk3 
    iio-sensor-proxy 
    im-config ippusbxd
    language-selector-gnome 
    libaa1 
    libappindicator3-1 
    libasound2-plugins
    libaspell15 
    libasyncns0 
    libatk-bridge2.0-0 
    libatk1.0-0 
    libatk1.0-data
    libatspi2.0-0 
    libavahi-glib1 
    libavc1394-0 
    libbluetooth3 
    libcaca0
    libcamel-1.2-62 
    libcanberra-gtk3-0 
    libcanberra-gtk3-module 
    libcanberra-pulse
    libcheese-gtk25 
    libcheese8 
    libclutter-1.0-0 
    libclutter-1.0-common
    libclutter-gst-3.0-0 
    libclutter-gtk-1.0-0 
    libcogl-common 
    libcogl-pango20
    libcogl-path20 
    libcogl20 
    libcolord-gtk1 
    libcolord2 
    libcolorhug2 
    libcrack2
    libdbusmenu-glib4 
    libdbusmenu-gtk3-4 
    libdv4 
    libebackend-1.2-10
    libebook-1.2-20 
    libebook-contacts-1.2-3 
    libecal-2.0-1 
    libedata-book-1.2-26
    libedata-cal-2.0-1 
    libedataserver-1.2-24 
    libedataserverui-1.2-2 
    libegl-mesa0
    libegl1 
    libenchant-2-2 
    libepoxy0 
    libfile-basedir-perl
    libfile-desktopentry-perl 
    libfile-mimeinfo-perl 
    libfontenc1 
    libfprint-2-2
    libgail-common 
    libgail18 
    libgbm1 
    libgck-1-0 
    libgcr-base-3-1 
    libgcr-ui-3-1
    libgdata-common 
    libgdata22 
    libgdm1 
    libgee-0.8-2 
    libgeoclue-2-0
    libgeocode-glib0 
    libgirara-gtk3-3 
    libgjs0g 
    libgl1 
    libgl1-mesa-dri
    libglapi-mesa 
    libgles2 
    libglvnd0 
    libglx-mesa0 
    libglx0 
    libgnome-autoar-0-0
    libgnome-bluetooth13 
    libgnome-desktop-3-19 
    libgnomekbd-common 
    libgnomekbd8
    libgoa-1.0-0b 
    libgoa-1.0-common 
    libgoa-backend-1.0-1 
    libgphoto2-6
    libgphoto2-l10n 
    libgphoto2-port12 
    libgraphene-1.0-0 
    libgsound0
    libgssdp-1.2-0 
    libgstreamer-gl1.0-0 
    libgstreamer-plugins-good1.0-0
    libgtk-3-0 
    libgtk-3-bin 
    libgtk-3-common 
    libgtk2.0-0 
    libgtk2.0-bin
    libgtk2.0-common 
    libgtop-2.0-11 
    libgtop2-common 
    libgupnp-1.2-0
    libgupnp-av-1.0-2 
    libgupnp-dlna-2.0-3 
    libgweather-3-16 
    libgweather-common
    libharfbuzz-icu0 
    libhunspell-1.7-0 
    libhyphen0 
    libibus-1.0-5 
    libical3 
    libice6
    libiec61883-0 
    libieee1284-3 
    libinput-bin 
    libinput10
    libipc-system-simple-perl 
    libjack-jackd2-0 
    libjavascriptcoregtk-4.0-18
    libmbim-glib4 
    libmbim-proxy 
    libmediaart-2.0-0 
    libmm-glib0 
    libmozjs-68-0
    libmtdev1 
    libmutter-6-0 
    libndp0 
    libnet-dbus-perl 
    libnm0 
    libnma0 
    libnotify4
    libopengl0 
    libpam-fprintd 
    libpam-gnome-keyring 
    libpangoxft-1.0-0
    libpcsclite1 
    libpeas-1.0-0 
    libpeas-common 
    libphonenumber7 
    libprotobuf17
    libpulse-mainloop-glib0 
    libpulse0 
    libpulsedsp 
    libpwquality-common
    libpwquality1 
    libqmi-glib5 
    libqmi-proxy 
    libraw1394-11 
    librest-0.7-0
    librygel-core-2.6-2 
    librygel-db-2.6-2 
    librygel-renderer-2.6-2
    librygel-server-2.6-2 
    libsamplerate0 
    libsane 
    libsane-common 
    libsbc1
    libsecret-1-0 
    libsecret-common 
    libshout3 
    libsm6 
    libsnapd-glib1 
    libsndfile1
    libsnmp-base 
    libsnmp35 
    libsoup-gnome2.4-1 
    libspeexdsp1
    libstartup-notification0 
    libsynctex2 
    libtag1v5 
    libtag1v5-vanilla
    libteamdctl0 
    libtie-ixhash-perl 
    libv4l-0 
    libv4lconvert0 
    libvte-2.91-0
    libvte-2.91-common 
    libvulkan1 
    libwacom-bin 
    libwacom-common 
    libwacom2
    libwayland-client0 
    libwayland-cursor0 
    libwayland-egl1 
    libwayland-server0
    libwebkit2gtk-4.0-37 
    libwebpdemux2 
    libwebrtc-audio-processing1
    libwhoopsie-preferences0 
    libwhoopsie0 
    libwoff1 
    libx11-protocol-perl
    libxatracker2 
    libxaw7 
    libxcb-glx0 
    libxcb-icccm4 
    libxcb-image0
    libxcb-keysyms1 
    libxcb-randr0 
    libxcb-render-util0 
    libxcb-res0 
    libxcb-shape0
    libxcb-util1 
    libxcb-xkb1 
    libxcb-xv0 
    libxcomposite1 
    libxcursor1 
    libxdamage1
    libxfont2 
    libxft2 
    libxi6 
    libxinerama1 
    libxkbcommon-x11-0 
    libxkbcommon0
    libxkbfile1 
    libxklavier16 
    libxml-twig-perl 
    libxml-xpathengine-perl 
    libxmu6
    libxrandr2 
    libxss1 
    libxt6 
    libxtst6 
    libxv1 
    libxvmc1 
    libxxf86dga1 
    libxxf86vm1
    libyelp0 
    mesa-vulkan-drivers 
    midori 
    mobile-broadband-provider-info
    modemmanager 
    mousetweaks 
    mutter 
    mutter-common 
    network-manager
    network-manager-gnome 
    network-manager-pptp 
    p11-kit 
    p11-kit-modules
    pinentry-gnome3 
    ppp 
    pptp-linux 
    pulseaudio 
    pulseaudio-module-bluetooth
    pulseaudio-utils 
    python3-aptdaemon 
    python3-aptdaemon.gtk3widgets
    python3-cairo 
    python3-cups 
    python3-cupshelpers 
    python3-defer
    python3-ibus-1.0 
    python3-macaroonbakery 
    python3-protobuf 
    rtkit 
    rygel
    sane-utils 
    session-migration 
    sgml-base 
    sgml-data 
    switcheroo-control
    system-config-printer 
    system-config-printer-common
    system-config-printer-udev 
    ubuntu-docs 
    ubuntu-mono 
    ubuntu-session
    ubuntu-wallpapers 
    ubuntu-wallpapers-focal 
    usb-modeswitch 
    usb-modeswitch-data
    whoopsie-preferences 
    wpasupplicant 
    x11-common 
    x11-utils 
    x11-xkb-utils
    x11-xserver-utils 
    xdg-dbus-proxy 
    xdg-utils 
    xfonts-base 
    xfonts-encodings
    xfonts-utils 
    xml-core 
    xserver-common 
    xserver-xephyr 
    xserver-xorg
    xserver-xorg-core 
    xserver-xorg-input-all 
    xserver-xorg-input-libinput
    xserver-xorg-input-wacom 
    xserver-xorg-legacy 
    xserver-xorg-video-all
    xserver-xorg-video-amdgpu 
    xserver-xorg-video-ati 
    xserver-xorg-video-fbdev
    xserver-xorg-video-intel 
    xserver-xorg-video-nouveau 
    xserver-xorg-video-qxl
    xserver-xorg-video-radeon 
    xserver-xorg-video-vesa 
    xserver-xorg-video-vmware
    xwayland 
    yaru-theme-gnome-shell 
    yelp 
    yelp-xsl 
    zathura 
    zathura-pdf-poppler
    zenity 
    zenity-common '
  
 for prog in ${prog_set}
 do
     sudo apt remove --purge $prog
 done

```

---

### Post by slickymaster on 2022-12-12
*Thread moved to **Server Platforms**.*

---

### Post by 21Jerry on 2022-12-12
Why is it not uninstalling x-server, I wonder?  I have the log of all it installed and what it wants to uninstall, but I don't see the xserver, midori, etc.

---

### Post by MAFoElffen on 2022-12-13
Those are in the uninstall script I created for you... Just saying that your last post is missing some context in what you did, and the results of.

Uninstalling just a few things does not uninstall all the dependencies that were the waterfall affect of that. That is why I created that script for you based on what it said was the resulting packages that were installed as new...

---

### Post by TheFu on 2022-12-13
For a system as important as this one seems to be, why not just restore from the backups you make daily, automatically?  Wouldn't that be easier?

---

### Post by 21Jerry on 2022-12-13
I appreciate the script and I was working on a command by command version.  Based on what was installed as new, did you see anything in the list that would be risky to remove?  I'm primarily concerned about something that would prevent me getting to the server after reboot.  Also, what is starting up the desktop on the console?  Should I remove that first so that at least the console will come up in command line if things go to hell?  I have a full disk clone backup prior to the email server being moved to this machine.  It would be a pain to reload but not a disaster.

context if it helps:

What I did was stupid.  I've had ubuntu server (now 20.04) running for years, primarily for owncloud and backups but I recently moved my mail server over there with iredmail.  

I had a path issue with gprolog.  When I tried to execute some prolog code, it gave me one of those, "can't find gprolog" but it can be installed with "apt install gprolog". So I thought, what the hell, it had been running fine on the server except I alway had to go look for it and setup the environment variables so I ran the "apt install".  I wasn't paying attention and gprolog source, which I compiled and made executable is 3.6MB and command line only AFAIK.   So I hit 'y' after not looking at the list of libraries to be installed that had scrolled up the window.  I didn't even know there was a gui version for gprolog and I couldn't even find it on the desktop, or anything except midori.  After I saw what it was installing, I thought about canceling it but thought that was a bad idea.

So now I want all that off my server so that it is back to a somewhat vanilla 20.04 server.  I'm primarily worried about the console coming up with that hosed, minimal desktop.  Should I kill that first?

Thanks for the script and help.

Jerry

---

### Post by TheFu on 2022-12-13
If a restore takes over about 45 minutes, time to find a better solution.  Image-based backs are just too much hassle and make having daily, automatic, versioned, backups next to impossible.  Nobody has that much time or that much storage to hold 180 days of images.

Mixing important applications on the same OS install is a bad idea. I'd undo that ASAP.  Use containers or VMs for each major service.  email is high risk.  owncloud/nextcloud should be low risk, since they shouldn't be available on the internet directly anyways.  Access to those should require a full VPN or be blocked.

---

### Post by 21Jerry on 2022-12-13
All my data is on mirrored ZFS, dual pathed on an external frame.  I keep LTO tape backups of the data but since it is sync'ed to 6 or 7 machines, I almost don't care if the server is lost. I've not been able to find software to shadow copy the system.   I use amanda now for remotes, tried bacula, but ganted I've not spent a ton of time on that issue because prior to this, I could just pop the cloned system in and off it would go.  Owncloud, timemachine, plus backups are on the local network with everything on the external drives. 

The external IP address is only going to the email server (I hope, I've tested it). I cloned the system prior to moving the email server over there as I wanted to test the install on another machine.  I don't know the ins/outs of where the iredmail server is loaded to be able to restore it effectively after reloading the clone. it could be ease. Also, I just took an outage as the power went out the day the certificates expired on the server (what are the odds) and don't feel like recreating all that again.  So yes, I can bring the system up with everything except the email server but I have the config files so it might be the better solution.  I was just hoping that apt remove would take all that off with low risk.  So I think I will try the script and rebuild if it bombs.

But what is bringing that desktop up on the console?

---

### Post by 21Jerry on 2022-12-13
so this makes things more interesting.  I ran 'aptitude why gnome.'  so it looks like it put ubuntu-standard down on the system.  If I remove that, will it take it back to server?

i   ubuntu-standard Recommends plymouth                             
i A plymouth        Suggests   desktop-base                         
p   desktop-base    Suggests   gnome | kde-standard | xfce4 | wmaker

---

### Post by MAFoElffen on 2022-12-13
AFAIK 'ubuntu-standard' is minimal console. for instance, it includes 'ed' as a basic editor. Next step up is 'ubuntu-server-minimal', then 'ubuntu-server'... I used to think that re-installing one of these would get you back to a clean Server Edition... but they don't. If you install these on ubuntu-core or ubuntu-base... then it will raise the level up to.

Most people debate on uninstalling 'xserver-xorg' or " 'libx11*' & 'libqt*' " which the later would remove more, but still is not as clean as what my script has said, which gets you back to where you were before you --yes on your install. If a user doesn't know what they installed, then I usually recommend
```

sudo apt remove --purge libx11* libqt*
sudo apt install --reinstall ubuntu-server

```
Which is quick and close to a clean edition as one can get in a few commands.

You are using ZFS but not doing ZFS snapshots? Why not? There you could get back to points of time, piece by piece. Still doesn't replace backups, but... For the future, if you install 'zsys' then there will automatically take a snapshot with very apt process... and add it to a grub "history" menu item. There are pro's and con's to that that can be taken care of by configuration.

---

### Post by TheFu on 2022-12-13
If you don't want a GUI, then removing the GUI server stuff will do that.  Just don't confuse X/Clients from X/Servers, if you have any X/Client software on the system.

If you have ZFS across the OS and data on this system, maybe looking at the list of snapshots will show one from just before the package changes? I thought Ubuntu 20.04 did that automatically.

You mention "shadow copies".  On Unix, we call those "volume snapshots" and ZFS most definitely supports them and Amanda should be pulling the backups from snapshots to avoid data corruption in the backups. You're probably doing this, just forgot.

Initially, I was under the impression that you have 1 system, running lots of network dæmons and had been moving others onto that same box, which is also connected to the internet.  That is where my risk concerns came from.  If you have multiple services loaded onto the system and there's any public IP, then there is increased risk that those other services can be hacked, since 1 failure in 1 open port can provide a foothold for other attacks.  The public IP isn't assigned to "email", it is assigned to the entire system.

If email is on a separate system (even a logically different system as a VM or container would provide), then the risk mitigation is significantly better, as long as the contain has a separate IP and isn't just a port-forward from the host.  

There are lots and lots of security considerations with containers that would be off-topic in this thread.  But containers are a good way to logically separate different services at between 1/10th and 1/100th the overhead of running a full virtual machine.  Depending on the container type, upkeep can be a completely new skill to learn ... or some containers can be treated like virtual machines or physical machines. Just depends.  LXD/LXC managed containers claim to be a hypervisor, more like a VM than a container, but with the overhead more like a typical container.  Anyway, lots to learn and lots of options.

So, back to the "get this GUI off my system" task.  If you remove xorg-server packages (sorry, I don't recall the package names), that should remove all X/Server stuff and the packages dependent on those.  
```
$ dpkg -l xserver* |egrep '^ii'
```
should provide a list for removal.  Be careful.  I ran a command to remove a specific package that I know I'll never need, xserver-xorg-video-vmware-hwe-18.04, and APT decided to remove all xserver-xorg-video*hwe-* packages which would have taken out the full GUI on this system because xserver-xorg-video-all-hwe-18.04 was being removed.  I actually want a lite-GUI on this box, but know I won't need intel or VMware and 1 of the AMD GPU video packages, but I will need the other.

I suspect that MAFoElffen pulled the install logs to create the script.  So, if you trust MAFoElffen not to have made any mistakes (it would be accidental, I'm certain), I'd still check his work and then run the script with a backup at the ready. I 'd also carefully read the responses from apt or apt-get.

You aren't the first person to do this ... this year.   It has been a few years since I did anything like this but I definitely have. My backups aren't tightly coupled between systems, so if it is going to take me more than 45 minutes to fix, I'll just blow away the system and follow my recovery process to get 'er done.  Sure, the DNS servers and time server is hard coded, but most other things work off DNS, so if the DNS records are correct, the correct systems will find each other.

---

### Post by 21Jerry on 2022-12-13
I checked the the script against the log I have and it is correct.  I don't use ZFS for the system files, just the data.   A friend installed on ZFS and he had some issues so I've just kept it as-was. I keep backups of /var /etc /usr /home and a couple other directories in a zfs pool.

With regards to isolation of my email, owncloud, and minidlna, and backups, there could be a way to hack it, I guess and I should setup VMs for each platform.  Everything runs thru a brocade switch into a separate 10Gb interface from the internet.  Everything else goes in through two other 10Gb interfaces from my local dmz.  Then the email uses one web server and owncloud uses another.  Everything uses SSL.  I had the email on another server but the power requirements didn't justify it.  I get well over 500 hits a day on the email server, mostly failed login attempts and that started on day one.  I don't keep anything confidential on owncloud as I don't trust it.

Thanks for all the pointers.  I'll let you know how it goes.

Jerry

---

### Post by MAFoElffen on 2022-12-13
I'm a developer and systems guy. I have a bit of experience with ZFS from supporting Solaris since 2005. Then ZFS on Linux and OpenZFS. There are so many things you can do on ZFS. But you just need to do them and keep up with it. Setting up containers within your pools and scripting routine snapshots. That's the thing about tools. If you don't use them, they tarnish, and collect dust. Like both TheFu and I... We PM each pother to remind each other about things. LOL. He reminds me I'm getting old.

I respect TheFu as being very knowledgeable about systems. He's someone  to talk to about backups, recovery, anything related to LVM2, and security issues  with anything facing out to a Public IP.

I think Zsys would be something that you might be interested in looking into more.
> [ZSYS]("https://github.com/ubuntu/zsys"): It allows running multiple ZFS systems in parallel on the same machine,  get automated snapshots, managing complex zfs dataset layouts separating  user data from system and persistent data, and more.
Not just for Zsys itself, but even in just organizing, normalizing, and compartmentalizing your system's datastructures. Where everything has a logical home and you know what you want to take snapshots of...
.
For example, one of mine:
```

mafoelffen@Mikes-B460M:~/Scripts$ sudo zfs list
[sudo] password for mafoelffen: 
NAME                                               USED  AVAIL     REFER  MOUNTPOINT
bpool                                              253M  1.50G       96K  /boot
bpool/BOOT                                         252M  1.50G       96K  none
bpool/BOOT/ubuntu_2cwpns                           252M  1.50G      252M  /boot
datapool                                           439G  3.08T       96K  none
datapool/DATA                                      439G  3.08T      439G  /data
rpool                                             11.1G   880G       96K  /
rpool/ROOT                                        6.40G   880G       96K  none
rpool/ROOT/ubuntu_2cwpns                          6.40G   880G     4.12G  /
rpool/ROOT/ubuntu_2cwpns/srv                        96K   880G       96K  /srv
rpool/ROOT/ubuntu_2cwpns/usr                       224K   880G       96K  /usr
rpool/ROOT/ubuntu_2cwpns/usr/local                 128K   880G      128K  /usr/local
rpool/ROOT/ubuntu_2cwpns/var                      2.28G   880G       96K  /var
rpool/ROOT/ubuntu_2cwpns/var/games                  96K   880G       96K  /var/games
rpool/ROOT/ubuntu_2cwpns/var/lib                  2.23G   880G     2.10G  /var/lib
rpool/ROOT/ubuntu_2cwpns/var/lib/AccountsService   108K   880G      108K  /var/lib/AccountsService
rpool/ROOT/ubuntu_2cwpns/var/lib/NetworkManager    160K   880G      160K  /var/lib/NetworkManager
rpool/ROOT/ubuntu_2cwpns/var/lib/apt              94.9M   880G     94.9M  /var/lib/apt
rpool/ROOT/ubuntu_2cwpns/var/lib/dpkg             39.9M   880G     39.9M  /var/lib/dpkg
rpool/ROOT/ubuntu_2cwpns/var/log                  45.6M   880G     45.6M  /var/log
rpool/ROOT/ubuntu_2cwpns/var/mail                   96K   880G       96K  /var/mail
rpool/ROOT/ubuntu_2cwpns/var/snap                 1.36M   880G     1.36M  /var/snap
rpool/ROOT/ubuntu_2cwpns/var/spool                 120K   880G      120K  /var/spool
rpool/ROOT/ubuntu_2cwpns/var/www                    96K   880G       96K  /var/www
rpool/USERDATA                                    4.74G   880G       96K  /
rpool/USERDATA/mafoelffen_gtg9x1                  4.73G   880G     4.73G  /home/mafoelffen
rpool/USERDATA/root_gtg9x1                        1.08M   880G     1.08M  /root

```

---

### Post by 21Jerry on 2022-12-15
thanks, the issue is I just don't have the time to learn everything these days.  But I guess I should at a minimum setup VMs for my email (external ip) vs everything else (DMZ).  If people want access to my email, fine, let them sort through the dozen or so ***** enlargement emails I get a day.  But the owncloud and videos need to be secure as I've heard of people stealing them to present them as their family.  weird.  So I have to figure out how to setup the VM environment, basically load it down and migrate the workloads I guess.

---

### Post by TheFu on 2022-12-15
> **21Jerry said:**
> thanks, the issue is I just don't have the time to learn everything these days.  But I guess I should at a minimum setup VMs for my email (external ip) vs everything else (DMZ).  If people want access to my email, fine, let them sort through the dozen or so ***** enlargement emails I get a day.  But the owncloud and videos need to be secure as I've heard of people stealing them to present them as their family.  weird.  So I have to figure out how to setup the VM environment, basically load it down and migrate the workloads I guess.

Seems you think they want to access your email.  Not really their main goal.  They want to pwn the server and use it to launch and manage other attacks, both inside your LAN and towards the outside world.

[https://krebsonsecurity.com/2012/10/the-scrap-value-of-a-hacked-pc-revisited/](https://krebsonsecurity.com/2012/10/the-scrap-value-of-a-hacked-pc-revisited/) is 10 yrs old, but it explains the use in hacking systems.

---

### Post by MAFoElffen on 2022-12-15
I got the list from the OP's Post #1. I just cut and pasted what it said it installed new on his system, into my program editor and created a macro to reformat it into a simple set... So nothing was changed except the format, to make it usable. LOL

Yes. I trust and respect TheFu on any security matters. He has some great ideas and practices for that, based on decades of experience. I love his thoughts on that (among lots of other things). Listen closely to him. Some jewels he shares may just 'sound' subtle, but are full of invaluable details.

For instance, search on his name and backup's... Wow.

---

### Post by 21Jerry on 2022-12-24
all of a suddenly, my server started slowing down and I see a boatload of GDM and other gnome processes.  So I finally didn't have an option but to run the script you guys so kindly made for me.  running it now, looks like it is taking a lot of things out, but if I have to go to my backup before the mail server was added, that's the way it is.

I'll report back after the reboot.

Jerry

---

### Post by MAFoElffen on 2022-12-25
You said you would get back to us after a reboot... Not hearing anything  after that... Was that meaning there was a problem or not?

---

