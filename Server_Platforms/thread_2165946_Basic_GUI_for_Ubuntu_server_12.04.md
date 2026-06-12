---
title: "Basic GUI for Ubuntu server 12.04"
date: 2013-08-07
forum: Server Platforms
---

### Post by salmendar on 2013-08-07
hi i want to have the basic GUI for ubuntu server ... the command i am using is 

[FONT=verdana, arial, sans-serif][COLOR=#333333]sudo apt-get install --no-install-recommends ubuntu-desktop[/COLOR][/FONT]


[FONT=verdana, arial, sans-serif][COLOR=#333333]but it returns the following error.
[/COLOR][/FONT]

[ATTACH=CONFIG]245148[/ATTACH]

please help.

---

### Post by volkswagner on 2013-08-07
ubuntu-desktop package is not a basic GUI ;)

Do you have broken packages from previous attempts?

First try:
```
sudo apt-get install -f
```

That should fix any broken/partial packages, or give you a sane error.

When installing the desktop package without-recommends you can miss out on some
important functions.  I recall missing out on policykit-desktop-privileges, when using without-recommends.

It would be a good Idea to capture what is recommended and required by first running a simulation.
Copy the package list for what would be installed, then run the same with --no-install-recommends.

For example when I run the simulation on my 12.04 server I get the following for recommended packages.

```
sudo apt-get install --no-install-recommends ubuntu-desktop -s
```

The -s = simulate (don't install anything).

```
Recommended packages:
  python-apport python-dateutil python-gst0.10 sessioninstaller packagekit
  foomatic-db-engine cups-client printer-driver-min12xxw printer-driver-hpijs
  poppler-utils colord gnome-online-accounts mousetweaks ubuntu-docs
  indicator-sound indicator-power libpam-gnome-keyring libcanberra-pulse
  gstreamer0.10-x indicator-application libcanberra-gtk3-module libpam-cap
  enchant hwdata libgtk2.0-bin hunspell-en-us hunspell-dictionary
  myspell-dictionary network-manager mobile-broadband-provider-info
  libpaper-utils qdbus libqt4-sql-mysql libqt4-sql-odbc libqt4-sql-psql
  libqt4-sql-sqlite zeitgeist zeitgeist-core brasero notify-osd-icons vbetool
  pulseaudio-module-x11 rtkit gir1.2-gudev-1.0 sane-utils libjs-jquery
  python-pam python-serial gir1.2-launchpad-integration-3.0
  system-config-printer-udev avahi-utils acpi-support
  activity-log-manager-control-center aisleriot app-install-data-partner
  apport-gtk avahi-autoipd bluez bluez-alsa bluez-cups bluez-gstreamer
  branding-ubuntu brltty cups-bsd deja-dup empathy example-content firefox
  firefox-gnome-support fonts-kacst-one fonts-khmeros-core fonts-lao
  fonts-liberation fonts-nanum fonts-takao-pgothic fonts-thai-tlwg gcc ginn
  gnome-accessibility-themes gnome-disk-utility gnome-orca gnome-sudoku
  gnomine gvfs-fuse gwibber ibus ibus-gtk3 ibus-pinyin ibus-pinyin-db-android
  ibus-table jockey-gtk kerneloops-daemon landscape-client-ui-install
  libgail-common libnss-mdns libproxy1-plugin-gsettings
  libproxy1-plugin-networkmanager libreoffice-calc libreoffice-gnome
  libreoffice-help-en-us libreoffice-impress libreoffice-math
  libreoffice-style-human libreoffice-writer libwmf0.2-7-gtk mahjongg
  nautilus-share network-manager-gnome network-manager-pptp onboard
  overlay-scrollbar pcmciautils plymouth-theme-ubuntu-logo
  policykit-desktop-privileges printer-driver-sag-gdi
  pulseaudio-module-bluetooth pulseaudio-module-gconf
  python-aptdaemon.pkcompat qt-at-spi remmina rhythmbox
  rhythmbox-plugin-magnatune rhythmbox-ubuntuone shotwell simple-scan sni-qt
  speech-dispatcher telepathy-idle thunderbird-gnome-support totem-mozilla
  transmission-gtk ttf-indic-fonts-core ttf-punjabi-fonts
  ttf-ubuntu-font-family ttf-wqy-microhei ubuntuone-client-gnome
  ubuntuone-installer usb-creator-gtk vino whoopsie xcursor-themes xdg-utils
  xul-ext-ubufox mtools cryptsetup-bin unity-lens-applications
  unity-lens-files unity-lens-music unity-lens-video indicator-appmenu
  indicator-datetime indicator-messages indicator-printers indicator-session
  gir1.2-dbusmenu-gtk-0.4 gir1.2-unity-5.0 xfonts-scalable

```


Notice Policy-kit is only recommended but it is required for proper permissions of users to use the shutdown function.

For a more lightweight or basic desktop environment, I'd suggest Lubuntu-Deskto, or Lubuntu-core.

---

### Post by ibjsb4 on 2013-08-07
I would use 

```
sudo apt-get install --no-install-recommends gnome-session-fallback
```

also have a look here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=server+gui&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=server+gui&sa=Search&cof=FORID:9)

---

### Post by newbie-user on 2013-08-07
ubuntu-desktop is a metapackage that refers to a collection of programs that make up the Ubuntu desktop. If you want a GUI, you'd probably want to check out some of the lighter desktop environments, such as lxde or xfce

---

### Post by ibjsb4 on 2013-08-07
With/without recommends, look at the difference between ubuntu-desktop and fallback (also called gnome-classic).

[http://packages.ubuntu.com/precise/ubuntu-desktop](http://packages.ubuntu.com/precise/ubuntu-desktop)

[http://packages.ubuntu.com/precise/gnome-session-fallback](http://packages.ubuntu.com/precise/gnome-session-fallback)

---

### Post by terabyte128 on 2013-08-08
You could also try [webmin]("http://www.webmin.com/"), it runs a local web server and gives you a GUI to do a lot of server management.

---

### Post by salmendar on 2013-08-12
there was an issue with the language package ... i cant find any way to fix that... 
can i somehow update the language package

---

### Post by hansamurai on 2013-08-12
> **terabyte128 said:**
> You could also try [webmin]("http://www.webmin.com/"), it runs a local web server and gives you a GUI to do a lot of server management.

I've been using Ajenti and enjoying it, which is in the repositories.

---

### Post by salmendar on 2013-08-12
the thing is that I am quiet new to Ubuntu. I had good experience when I used Ubuntu desktop in my Operating Systems course but the thing is that although I prefer using basic batch files and console commands in windows, its no more secure and private. I the first thing I will work on after getting this working is to secure it completely shift to Ubuntu. but the thing is I am Pakistani and privacy is becoming a major issue. I had major hack attempts on my system as I also write articles for news papers and to secure it nothing is better then Linux . they may see what I see but can't see what I think. GUI is for my articles that I work on. I wish to contribute to people of this Ubuntu by my services but indeed I need time to learn it. thank you guys for your help.

---

### Post by wordpressuser on 2013-08-12
Thanks for the suggestion, hansamurai. I installed Ajenti.... looks good!!

---

### Post by salmendar on 2013-08-13
the problemis in the language package. can i know if i can update the language package.my package is a little specific to asian english region. can i chane it to US en package

---

