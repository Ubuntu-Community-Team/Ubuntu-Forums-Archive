---
title: "Unable to set preferences in Nautilus"
date: 2016-03-04
forum: Ubuntu Development Version
---

### Post by pfeiffep on 2016-03-04
I performed software update gui after fresh install.

I am unable to set preferences in Nautilus when using gnome flashback metacity. Additionally nautilus is VERY sluggish.
When using unity Nautilus is behaving as I expect.

This is an annoyance, but I was able to set preferences to my liking while using Unity, and of course the preferences are set for Metacity

This is a throwaway install - just testing 16.04

---

### Post by $yl9pAR%t on 2016-03-04
You are not alone, look here at #7 and later

[http://ubuntuforums.org/showthread.php?t=2315377](http://ubuntuforums.org/showthread.php?t=2315377)

edit:
[Sorry, I should not post here, I misplaced "properties" and "preferences" in my memory]

---

### Post by Bucky Ball on 2016-03-04
I have changed the thread title to increase the effectiveness of your post. Please use descriptive thread titles in future. 'Nautilus' doesn't say anything about what you up against. Thanks. ;)

---

### Post by mc4man on 2016-03-05
> **pfeiffep said:**
> I performed software update gui after fresh install.

I am unable to set preferences in Nautilus when using gnome flashback metacity. Additionally nautilus is VERY sluggish.
When using unity Nautilus is behaving as I expect.

This is an annoyance, but I was able to set preferences to my liking while using Unity, and of course the preferences are set for Metacity

This is a throwaway install - just testing 16.04
Not sure why they even bother with flashback anymore, obviously in poor shape, particularly in regards to nautilus. Users that want a gnome2 experience should use mate instead.

---

### Post by pfeiffep on 2016-03-05
Is mate a desktop environment that can be added to a 'standard Ubuntu install"?
I'm relatively new to Ubuntu. After spending 40 years in the computer industry spanning Mainframes, Commodore 64, Apple II, Macs, PC, and Sun Solaris I have a small amount of bandwidth with which to experiment. 
I settled on Ubuntu at 12.10 and was delighted when I got to 14 LTS. I'm just testing the waters with 16 for the future.
TIA

---

### Post by pfeiffep on 2016-03-05
Update, there's a bug that's been reported (Bug #1552074 reported) so I'll be trying mate shortly

---

### Post by mc4man on 2016-03-05
If I was to try/use mate I'd use this
[http://cdimage.ubuntu.com/ubuntu-mate/daily-live/current/](http://cdimage.ubuntu.com/ubuntu-mate/daily-live/current/)

---

### Post by pfeiffep on 2016-03-06
> **mc4man said:**
> If I was to try/use mate I'd use this
[http://cdimage.ubuntu.com/ubuntu-mate/daily-live/current/](http://cdimage.ubuntu.com/ubuntu-mate/daily-live/current/)
Thanks, I tried the desktop add on to Ubuntu - not a good idea if flashback already installed.

Since this is just a test of 16.04 I'll fresh install Mate and give it a whirl.

I decided to also try Ubuntu Gnome as well as Mate ... Mate is certainly my choice!
Thanks again.

I don't want to mark this solved because Nautilus is still problematic in flashback

---

### Post by kansasnoob on 2016-03-07
I had not noticed this but I added a comment at this bug report:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1274740](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1274740)

---

### Post by kansasnoob on 2016-03-07
> **mc4man said:**
> Not sure why they even bother with flashback anymore, obviously in poor shape, particularly in regards to nautilus. Users that want a gnome2 experience should use mate instead.

Using Mate w/Marco would be problematic for Edubuntu's LTSP thin client installs because of its reliance on so many apps foreign to default Ubuntu:

```
lance@lance-AMD-desktop:~$ sudo apt install ubuntu-mate-core
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  atril atril-common avahi-discover avahi-dnsconfd brltty-x11 caja caja-common
  caja-extensions-common caja-gksu caja-open-terminal caja-sendto
  caja-wallpaper compton cpufrequtils desktop-base engrampa engrampa-common
  eom eom-common espeak ffmpegthumbnailer fonts-mathjax fonts-noto
  fonts-noto-hinted fonts-noto-mono fonts-noto-unhinted fonts-opendyslexic
  galculator gawk gdebi gdebi-core gir1.2-gtk-2.0 gir1.2-mate-panel
  gir1.2-wnck-1.0 gksu gnome-system-tools gnome-themes-standard
  gnome-themes-standard-data grub2-themes-ubuntu-mate gtk2-engines
  indicator-application-gtk2 indicator-sound-gtk2 inxi iproute
  libappindicator1 libatrildocument3 libatrilview3 libavahi-compat-libdnssd1
  libblas-common libblas3 libcaja-extension1 libconfig9 libconfuse-common
  libconfuse0 libegl1-mesa-drivers libfakekey0 libffmpegthumbnailer4v5
  libgfortran3 libgksu2-0 libglade2-0 libgtkmm-2.4-1v5 libgtksourceview2.0-0
  libgtksourceview2.0-common libido-0.1-0 libindicator7
  libjavascriptcoregtk-1.0-0 libjs-mathjax liblapack3 libmarco-private0
  libmate-desktop-2-17 libmate-menu2 libmate-panel-applet-4-1
  libmate-sensors-applet-plugin0 libmate-slab0 libmate-window-settings1
  libmatedict6 libmatekbd-common libmatekbd4 libmatemixer-common libmatemixer0
  libmateweather-common libmateweather1 liboobs-1-5 libopts25 libsigsegv2
  libtopmenu-client-gtk2-0 libtopmenu-client-gtk3-0 libtopmenu-server-gtk2-0
  libtopmenu-server-gtk3-0 libunique-1.0-0 libvte-common libvte9
  libwebkitgtk-1.0-0 libwebkitgtk-1.0-common libwnck-common libwnck22
  lightdm-gtk-greeter lm-sensors marco marco-common mate-applet-topmenu
  mate-applets mate-applets-common mate-backgrounds mate-control-center
  mate-control-center-common mate-desktop mate-desktop-common
  mate-desktop-environment-core mate-dock-applet mate-gnome-main-menu-applet
  mate-icon-theme mate-icon-theme-faenza mate-indicator-applet
  mate-indicator-applet-common mate-media mate-media-common mate-menu
  mate-menus mate-netbook mate-netbook-common mate-netspeed
  mate-netspeed-common mate-notification-daemon
  mate-notification-daemon-common mate-optimus mate-panel mate-panel-common
  mate-polkit mate-polkit-common mate-power-manager mate-power-manager-common
  mate-screensaver mate-screensaver-common mate-sensors-applet
  mate-sensors-applet-common mate-session-manager mate-settings-daemon
  mate-settings-daemon-common mate-system-monitor mate-system-monitor-common
  mate-terminal mate-terminal-common mate-themes mate-tweak mate-user-guide
  mate-utils mate-utils-common menu menu-xdg mesa-utils mozo ntp p7zip-full
  pinentry-gtk2 pluma pluma-common plymouth-theme-ubuntu-mate-logo
  plymouth-theme-ubuntu-mate-text python-avahi python-configobj python-crypto
  python-gdbm python-glade2 python-gobject python-gobject-2 python-gtk2
  python-gtksourceview2 python-ldb python-mate-menu python-samba python-tdb
  python-wnck python-xlib python3-decorator python3-numpy python3-psutil
  python3-scipy qt4-qtconfig samba-common samba-common-bin smbclient
  syslinux-utils system-tools-backends tilda topmenu-gtk-common topmenu-gtk2
  topmenu-gtk3 ubuntu-mate-artwork ubuntu-mate-default-settings
  ubuntu-mate-icon-themes ubuntu-mate-lightdm-theme ubuntu-mate-themes
  ubuntu-mate-wallpapers ubuntu-mate-wallpapers-common
  ubuntu-mate-wallpapers-xenial xzoom
Suggested packages:
  meld pidgin | gajim gnome | kde-standard | xfce4 | wmaker arj lha lzip lzop
  ncompress rar rpm2cpio rzip sharutils unace unalz zoo gawk-doc
  gnome-control-center fonts-mathjax-extras libjs-mathjax-doc fancontrol
  sensord read-edid i2c-tools rss-glx xscreensaver-data
  mate-sensors-applet-nvidia mate-desktop-environment menu-l10n ntp-doc
  p7zip-rar pinentry-doc python-configobj-doc python-crypto-dbg
  python-crypto-doc python-gdbm-dbg python-gtk2-doc python-gobject-2-dbg
  libgtksourceview2.0-dev gfortran python-numpy-doc python3-dev python3-nose
  python3-numpy-dbg python-psutil-doc python-scipy-doc heimdal-clients
  cifs-utils libcrypt-passwdmd5-perl
The following NEW packages will be installed:
  atril atril-common avahi-discover avahi-dnsconfd brltty-x11 caja caja-common
  caja-extensions-common caja-gksu caja-open-terminal caja-sendto
  caja-wallpaper compton cpufrequtils desktop-base engrampa engrampa-common
  eom eom-common espeak ffmpegthumbnailer fonts-mathjax fonts-noto
  fonts-noto-hinted fonts-noto-mono fonts-noto-unhinted fonts-opendyslexic
  galculator gawk gdebi gdebi-core gir1.2-gtk-2.0 gir1.2-mate-panel
  gir1.2-wnck-1.0 gksu gnome-system-tools gnome-themes-standard
  gnome-themes-standard-data grub2-themes-ubuntu-mate gtk2-engines
  indicator-application-gtk2 indicator-sound-gtk2 inxi iproute
  libappindicator1 libatrildocument3 libatrilview3 libavahi-compat-libdnssd1
  libblas-common libblas3 libcaja-extension1 libconfig9 libconfuse-common
  libconfuse0 libegl1-mesa-drivers libfakekey0 libffmpegthumbnailer4v5
  libgfortran3 libgksu2-0 libglade2-0 libgtkmm-2.4-1v5 libgtksourceview2.0-0
  libgtksourceview2.0-common libido-0.1-0 libindicator7
  libjavascriptcoregtk-1.0-0 libjs-mathjax liblapack3 libmarco-private0
  libmate-desktop-2-17 libmate-menu2 libmate-panel-applet-4-1
  libmate-sensors-applet-plugin0 libmate-slab0 libmate-window-settings1
  libmatedict6 libmatekbd-common libmatekbd4 libmatemixer-common libmatemixer0
  libmateweather-common libmateweather1 liboobs-1-5 libopts25 libsigsegv2
  libtopmenu-client-gtk2-0 libtopmenu-client-gtk3-0 libtopmenu-server-gtk2-0
  libtopmenu-server-gtk3-0 libunique-1.0-0 libvte-common libvte9
  libwebkitgtk-1.0-0 libwebkitgtk-1.0-common libwnck-common libwnck22
  lightdm-gtk-greeter lm-sensors marco marco-common mate-applet-topmenu
  mate-applets mate-applets-common mate-backgrounds mate-control-center
  mate-control-center-common mate-desktop mate-desktop-common
  mate-desktop-environment-core mate-dock-applet mate-gnome-main-menu-applet
  mate-icon-theme mate-icon-theme-faenza mate-indicator-applet
  mate-indicator-applet-common mate-media mate-media-common mate-menu
  mate-menus mate-netbook mate-netbook-common mate-netspeed
  mate-netspeed-common mate-notification-daemon
  mate-notification-daemon-common mate-optimus mate-panel mate-panel-common
  mate-polkit mate-polkit-common mate-power-manager mate-power-manager-common
  mate-screensaver mate-screensaver-common mate-sensors-applet
  mate-sensors-applet-common mate-session-manager mate-settings-daemon
  mate-settings-daemon-common mate-system-monitor mate-system-monitor-common
  mate-terminal mate-terminal-common mate-themes mate-tweak mate-user-guide
  mate-utils mate-utils-common menu menu-xdg mesa-utils mozo ntp p7zip-full
  pinentry-gtk2 pluma pluma-common plymouth-theme-ubuntu-mate-logo
  plymouth-theme-ubuntu-mate-text python-avahi python-configobj python-crypto
  python-gdbm python-glade2 python-gobject python-gobject-2 python-gtk2
  python-gtksourceview2 python-ldb python-mate-menu python-samba python-tdb
  python-wnck python-xlib python3-decorator python3-numpy python3-psutil
  python3-scipy qt4-qtconfig samba-common samba-common-bin smbclient
  syslinux-utils system-tools-backends tilda topmenu-gtk-common topmenu-gtk2
  topmenu-gtk3 ubuntu-mate-artwork ubuntu-mate-core
  ubuntu-mate-default-settings ubuntu-mate-icon-themes
  ubuntu-mate-lightdm-theme ubuntu-mate-themes ubuntu-mate-wallpapers
  ubuntu-mate-wallpapers-common ubuntu-mate-wallpapers-xenial xzoom
0 upgraded, 198 newly installed, 0 to remove and 0 not upgraded.
Need to get 195 MB of archives.
After this operation, 663 MB of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.

```

Even w/o recommends it's heavy:

```
lance@lance-AMD-desktop:~$ sudo apt install ubuntu-mate-core --no-install-recommends
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  atril atril-common avahi-discover avahi-dnsconfd brltty-x11 caja caja-common
  caja-extensions-common caja-gksu caja-open-terminal caja-sendto
  caja-wallpaper compton engrampa engrampa-common eom eom-common espeak
  ffmpegthumbnailer fonts-mathjax fonts-noto fonts-noto-hinted
  fonts-noto-unhinted fonts-opendyslexic galculator gawk gdebi gdebi-core
  gir1.2-gtk-2.0 gir1.2-mate-panel gir1.2-wnck-1.0 gksu gnome-system-tools
  grub2-themes-ubuntu-mate gtk2-engines indicator-application-gtk2
  indicator-sound-gtk2 inxi iproute libappindicator1 libatrildocument3
  libatrilview3 libavahi-compat-libdnssd1 libblas-common libblas3
  libcaja-extension1 libconfig9 libconfuse-common libconfuse0
  libegl1-mesa-drivers libfakekey0 libffmpegthumbnailer4v5 libgfortran3
  libgksu2-0 libglade2-0 libgtkmm-2.4-1v5 libgtksourceview2.0-0
  libgtksourceview2.0-common libido-0.1-0 libindicator7
  libjavascriptcoregtk-1.0-0 libjs-mathjax liblapack3 libmarco-private0
  libmate-desktop-2-17 libmate-menu2 libmate-panel-applet-4-1
  libmate-sensors-applet-plugin0 libmate-slab0 libmate-window-settings1
  libmatedict6 libmatekbd-common libmatekbd4 libmatemixer-common libmatemixer0
  libmateweather-common libmateweather1 liboobs-1-5 libopts25 libsigsegv2
  libtopmenu-client-gtk2-0 libtopmenu-client-gtk3-0 libtopmenu-server-gtk2-0
  libtopmenu-server-gtk3-0 libunique-1.0-0 libvte-common libvte9
  libwebkitgtk-1.0-0 libwebkitgtk-1.0-common libwnck-common libwnck22
  lightdm-gtk-greeter marco marco-common mate-applet-topmenu mate-applets
  mate-applets-common mate-backgrounds mate-control-center
  mate-control-center-common mate-desktop mate-desktop-common
  mate-desktop-environment-core mate-dock-applet mate-gnome-main-menu-applet
  mate-icon-theme mate-icon-theme-faenza mate-indicator-applet
  mate-indicator-applet-common mate-media mate-media-common mate-menu
  mate-menus mate-netbook mate-netbook-common mate-netspeed
  mate-netspeed-common mate-notification-daemon
  mate-notification-daemon-common mate-optimus mate-panel mate-panel-common
  mate-polkit mate-polkit-common mate-power-manager mate-power-manager-common
  mate-screensaver mate-screensaver-common mate-sensors-applet
  mate-sensors-applet-common mate-session-manager mate-settings-daemon
  mate-settings-daemon-common mate-system-monitor mate-system-monitor-common
  mate-terminal mate-terminal-common mate-themes mate-tweak mate-user-guide
  mate-utils mate-utils-common menu-xdg mesa-utils mozo ntp p7zip-full
  pinentry-gtk2 pluma pluma-common plymouth-theme-ubuntu-mate-logo
  plymouth-theme-ubuntu-mate-text python-avahi python-configobj python-crypto
  python-gdbm python-glade2 python-gobject python-gobject-2 python-gtk2
  python-gtksourceview2 python-ldb python-mate-menu python-samba python-tdb
  python-wnck python-xlib python3-decorator python3-numpy python3-psutil
  python3-scipy qt4-qtconfig samba-common samba-common-bin smbclient
  syslinux-utils system-tools-backends tilda topmenu-gtk-common topmenu-gtk2
  topmenu-gtk3 ubuntu-mate-artwork ubuntu-mate-default-settings
  ubuntu-mate-icon-themes ubuntu-mate-lightdm-theme ubuntu-mate-themes
  ubuntu-mate-wallpapers ubuntu-mate-wallpapers-common
  ubuntu-mate-wallpapers-xenial xzoom
Suggested packages:
  meld pidgin | gajim arj lha lzip lzop ncompress rar rpm2cpio rzip sharutils
  unace unalz zoo gawk-doc gnome-control-center fonts-mathjax-extras
  libjs-mathjax-doc rss-glx xscreensaver-data mate-sensors-applet-nvidia
  mate-desktop-environment ntp-doc p7zip-rar pinentry-doc python-configobj-doc
  python-crypto-dbg python-crypto-doc python-gdbm-dbg python-gtk2-doc
  python-gobject-2-dbg libgtksourceview2.0-dev gfortran python-numpy-doc
  python3-dev python3-nose python3-numpy-dbg python-psutil-doc
  python-scipy-doc heimdal-clients cifs-utils libcrypt-passwdmd5-perl
Recommended packages:
  fonts-noto-mono lm-sensors desktop-base gnome-themes-standard cpufrequtils
  menu
The following NEW packages will be installed:
  atril atril-common avahi-discover avahi-dnsconfd brltty-x11 caja caja-common
  caja-extensions-common caja-gksu caja-open-terminal caja-sendto
  caja-wallpaper compton engrampa engrampa-common eom eom-common espeak
  ffmpegthumbnailer fonts-mathjax fonts-noto fonts-noto-hinted
  fonts-noto-unhinted fonts-opendyslexic galculator gawk gdebi gdebi-core
  gir1.2-gtk-2.0 gir1.2-mate-panel gir1.2-wnck-1.0 gksu gnome-system-tools
  grub2-themes-ubuntu-mate gtk2-engines indicator-application-gtk2
  indicator-sound-gtk2 inxi iproute libappindicator1 libatrildocument3
  libatrilview3 libavahi-compat-libdnssd1 libblas-common libblas3
  libcaja-extension1 libconfig9 libconfuse-common libconfuse0
  libegl1-mesa-drivers libfakekey0 libffmpegthumbnailer4v5 libgfortran3
  libgksu2-0 libglade2-0 libgtkmm-2.4-1v5 libgtksourceview2.0-0
  libgtksourceview2.0-common libido-0.1-0 libindicator7
  libjavascriptcoregtk-1.0-0 libjs-mathjax liblapack3 libmarco-private0
  libmate-desktop-2-17 libmate-menu2 libmate-panel-applet-4-1
  libmate-sensors-applet-plugin0 libmate-slab0 libmate-window-settings1
  libmatedict6 libmatekbd-common libmatekbd4 libmatemixer-common libmatemixer0
  libmateweather-common libmateweather1 liboobs-1-5 libopts25 libsigsegv2
  libtopmenu-client-gtk2-0 libtopmenu-client-gtk3-0 libtopmenu-server-gtk2-0
  libtopmenu-server-gtk3-0 libunique-1.0-0 libvte-common libvte9
  libwebkitgtk-1.0-0 libwebkitgtk-1.0-common libwnck-common libwnck22
  lightdm-gtk-greeter marco marco-common mate-applet-topmenu mate-applets
  mate-applets-common mate-backgrounds mate-control-center
  mate-control-center-common mate-desktop mate-desktop-common
  mate-desktop-environment-core mate-dock-applet mate-gnome-main-menu-applet
  mate-icon-theme mate-icon-theme-faenza mate-indicator-applet
  mate-indicator-applet-common mate-media mate-media-common mate-menu
  mate-menus mate-netbook mate-netbook-common mate-netspeed
  mate-netspeed-common mate-notification-daemon
  mate-notification-daemon-common mate-optimus mate-panel mate-panel-common
  mate-polkit mate-polkit-common mate-power-manager mate-power-manager-common
  mate-screensaver mate-screensaver-common mate-sensors-applet
  mate-sensors-applet-common mate-session-manager mate-settings-daemon
  mate-settings-daemon-common mate-system-monitor mate-system-monitor-common
  mate-terminal mate-terminal-common mate-themes mate-tweak mate-user-guide
  mate-utils mate-utils-common menu-xdg mesa-utils mozo ntp p7zip-full
  pinentry-gtk2 pluma pluma-common plymouth-theme-ubuntu-mate-logo
  plymouth-theme-ubuntu-mate-text python-avahi python-configobj python-crypto
  python-gdbm python-glade2 python-gobject python-gobject-2 python-gtk2
  python-gtksourceview2 python-ldb python-mate-menu python-samba python-tdb
  python-wnck python-xlib python3-decorator python3-numpy python3-psutil
  python3-scipy qt4-qtconfig samba-common samba-common-bin smbclient
  syslinux-utils system-tools-backends tilda topmenu-gtk-common topmenu-gtk2
  topmenu-gtk3 ubuntu-mate-artwork ubuntu-mate-core
  ubuntu-mate-default-settings ubuntu-mate-icon-themes
  ubuntu-mate-lightdm-theme ubuntu-mate-themes ubuntu-mate-wallpapers
  ubuntu-mate-wallpapers-common ubuntu-mate-wallpapers-xenial xzoom
0 upgraded, 191 newly installed, 0 to remove and 0 not upgraded.
Need to get 188 MB of archives.
After this operation, 646 MB of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.

```

The flashback session adds very little:

```
lance@lance-AMD-desktop:~$ sudo apt-get install gnome-panel
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  alacarte gir1.2-panelapplet-5.0 gnome-applets gnome-applets-data
  gnome-flashback gnome-flashback-common gnome-media gnome-panel-data
  gnome-session-flashback gstreamer0.10-gconf gstreamer0.10-plugins-base
  gstreamer0.10-plugins-good gstreamer0.10-pulseaudio gstreamer0.10-x
  indicator-applet-complete libcpufreq0 libgstreamer-plugins-base0.10-0
  libgstreamer0.10-0 libpanel-applet0 metacity
Suggested packages:
  tomboy evolution-common desktop-base libvisual-0.4-plugins
  gstreamer0.10-tools gnome-control-center
The following NEW packages will be installed:
  alacarte gir1.2-panelapplet-5.0 gnome-applets gnome-applets-data
  gnome-flashback gnome-flashback-common gnome-media gnome-panel
  gnome-panel-data gnome-session-flashback gstreamer0.10-gconf
  gstreamer0.10-plugins-base gstreamer0.10-plugins-good
  gstreamer0.10-pulseaudio gstreamer0.10-x indicator-applet-complete
  libcpufreq0 libgstreamer-plugins-base0.10-0 libgstreamer0.10-0
  libpanel-applet0 metacity
0 upgraded, 21 newly installed, 0 to remove and 22 not upgraded.
Need to get 10.3 MB/12.0 MB of archives.
After this operation, 51.6 MB of additional disk space will be used.
```

Are bug reports filed for the issues that make flashback ***obviously in poor shape***?

There are at least two devs actively involved in the development of gnome flashback and I find them to be quite responsive :D

One issue I've not been able to reproduce is broken configurations in Precise > Trusty release upgrades so it's been impossible to figure out exactly what's wrong, but release upgrades are problematic in general.

---

### Post by kansasnoob on 2016-03-07
I asked at the mailing list:

[https://mail.gnome.org/archives/gnome-flashback-list/2016-March/msg00003.html](https://mail.gnome.org/archives/gnome-flashback-list/2016-March/msg00003.html)

Sorry I hadn't noticed this but my use of nautilus is pretty mundane, out-of-box and it hadn't come to my attention :redface:

---

### Post by mc4man on 2016-03-07
> **kansasnoob said:**
> 

Are bug reports filed for the issues that make flashback ***obviously in poor shape***?

There are at least two devs actively involved in the development of gnome flashback and I find them to be quite responsive :D

One issue I've not been able to reproduce is broken configurations in Precise > Trusty release upgrades so it's been impossible to figure out exactly what's wrong, but release upgrades are problematic in general.

Well then maybe they should try using gnome-flashback more than just a cursory look. Now it could be me but it seems a complete menu causes all sorts of issues in nautilus. What do you get if - 
log in to flashback > compiz
open nautilus, click on the hamburger menu icon (last icon on right) & try some of the entries 
Here most of them cause nautilus to peg a cpu & become unresponsive for a period of time. The open terminal option opens a terminal that continually flashes for some time, ect.

---

### Post by Smask on 2016-03-07
> **mc4man said:**
> Well then maybe they should try using gnome-flashback more than just a cursory look. Now it could be me but it seems a complete menu causes all sorts of issues in nautilus. What do you get if - 
log in to flashback > compiz
open nautilus, click on the hamburger menu icon (last icon on right) & try some of the entries 
Here most of them cause nautilus to peg a cpu & become unresponsive for a period of time. The open terminal option opens a terminal that continually flashes for some time, ect.

Thumbnailing? One of the first steps I do on a fresh install is to turn off everything thumbnails. Thumbnails makes network file operations molasses slow. Yes, I want to thumbnail everything in the trash can, especially when I'm emptying it.

---

### Post by kansasnoob on 2016-03-07
> **mc4man said:**
> Well then maybe they should try using gnome-flashback more than just a cursory look. Now it could be me but it seems a complete menu causes all sorts of issues in nautilus. What do you get if - 
log in to flashback > compiz
open nautilus, click on the hamburger menu icon (last icon on right) & try some of the entries 
Here most of them cause nautilus to peg a cpu & become unresponsive for a period of time. The open terminal option opens a terminal that continually flashes for some time, ect.

I never mess with Compiz but I see that effects the metacity session too. I just hadn't noticed it until now :(

I also never got around to messing with Wily much at all because [kernel and X bugs prevented me from running any flavor on 2/3 of my hardware]("http://ubuntuforums.org/showthread.php?t=2300290&p=13378777#post13378777").

Is there already a bug report about that CPU usage when Nautilus > Location options is opened?

I need to do a fresh install of Edubuntu and check some things out closer ASAP. To be honest I don't bother much with it until final beta because Canonical doesn't seem to pay much attention to Edubuntu until the last minute. Then I have to try and see if any bugs I find in Edubuntu (both with Unity and flashback) can be reproduced in stock Ubuntu.

---

### Post by kansasnoob on 2016-03-07
Nautilus freezing and gobbling CPU also effects out-of-box Ubuntu GNOME:

[ATTACH=CONFIG]267689[/ATTACH]

So I need to file a new bug report for that. The missing preferences menu in flashback is probably because that session should be using Ubuntu's menus rather than using Ubuntu GNOME's menus. Some of these things are bound to crop up because the Unity DE does not exist in Debian (our upstream), and also we're stuck on an older version of Nautilus.

---

### Post by mc4man on 2016-03-07
> **kansasnoob said:**
> 

Is there already a bug report about that CPU usage when Nautilus > Location options is opened?


Didn't see one but it seems that just simply opening that menu (not actually picking anything in it) starts the bad business

---

### Post by mc4man on 2016-03-07
Here - feel free to add to, alter or whatever as needed
[https://bugs.launchpad.net/ubuntu/+source/gnome-flashback/+bug/1554171](https://bugs.launchpad.net/ubuntu/+source/gnome-flashback/+bug/1554171)

---

### Post by kansasnoob on 2016-03-07
> **mc4man said:**
> Here - feel free to add to, alter or whatever as needed
[https://bugs.launchpad.net/ubuntu/+source/gnome-flashback/+bug/1554171](https://bugs.launchpad.net/ubuntu/+source/gnome-flashback/+bug/1554171)

Many thanks :D

---

