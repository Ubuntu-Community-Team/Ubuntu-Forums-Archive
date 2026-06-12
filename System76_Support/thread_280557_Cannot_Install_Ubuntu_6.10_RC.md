---
title: "Cannot Install Ubuntu 6.10 RC"
date: 2006-10-19
forum: System76 Support
---

### Post by frainbart on 2006-10-19
Today I upgraded to the new System76 driver, so I can upgrade to 6.10. I am having trouble installing the new Ubuntu 6.10 RC. It keeps giving me an error about installing ubuntu-desktop and does not complete the process. Attached is them main.log file in /var/log/dist-upgrade/

```
2006-10-19 16:39:19,768 DEBUG Foreign: sy.lgstem76-driver poppler-utils gsynaptics libgl1-mesa-dri beryl-plugins skype libtunepimp2c2a libxss1 beryl-settings libdvdcss2 beryl-plugins-data beryl xserver-xorg-driver-ati libgl1-mesa libwnck-common unace compiz-plugins beryl-core beryl-manager libxfixes3 linux-dri-modules-2.6.15-26-686 libdrm2 libxcomposite1 libpoppler1 emerald libwnck18 libglu1-mesa xserver-xorg-driver-i810 w32codecs libpoppler1-glib mesa-utils linux-dri-modules-common gnome-session xserver-xorg-air-core wine
2006-10-19 16:39:19,768 DEBUG Obsolete: gnome-doc-utils wpasupplicant gstreamer0.10-alsa libcupsimage2 python-gmenu emerald-themes-extra language-selector democracyplayer-data gdm compiz-gnome python-pyorbit gtk2-engines-thinice gtk2-engines-lighthouseblue gtk2-engines-industrial compiz-core pam-keyring-0.0.8 nautilus-cd-burner libgtkhtml3.8-15 libtotem-plparser1 gtk2-engines-crux app-install-data libgtk2.0-0 gnome-about evince gtkhtml3.8 libgtksourceview-common gnome-control-center ubuntu-standard gnome-applets libglib2.0-0 cupsys-bsd libgnomeui-common compiz-manager compiz libgnome-menu2 libcupsys2 gstreamer0.10-plugins-base-apps gnome-accessibility-themes language-pack-en libgnome-desktop-2 gtk2-engines-pixbuf libsoup2.2-8 acpi-support libeel2-2 libgstreamer-plugins-base0.10-0 libgnomeprint2.2-data gnome-terminal gtk2-engines-smooth ubuntu-minimal gnome-panel gnome-games gstreamer0.10-x libgtkmm-2.4-1c2a pcmcia-cs libgnomevfs2-0 gtk2-engines-clearlooks gnome-media nautilus-data capplets-data language-pack-gnome-en python-vte pmount oem-config-locale libglib2.0-data libpango1.0-common libgtk2.0-bin libgtksourceview1.0-0 xserver-xorg-core gtk2-engines-redmond95 gtk2-engines-highcontrast libnautilus-burn3 gnome-panel-data language-pack-en-base gnome-terminal-data gtk2-engines-mist xserver-xorg-input-mouse localechooser-data file-roller libpanel-applet2-0 libgnomecups1.0-1 libeel2-data cupsys libgnomevfs2-common metacity gnome-screensaver app-install-data-commercial python2.4-gtkglext1 democracyplayer gedit-common ubuntu-docs language-selector-common libglibmm-2.4-1c2a sound-juicer libvte4 gnome-menus nautilus gstreamer0.10-plugins-base gnome-themes libmetacity0 zenity gedit base-files gnome-app-install libgnomevfs2-extra csm gstreamer0.10-gnomevfs gnome-desktop-data gnome-games-data gnome-applets-data libgnomevfs2-bin libgtk2.0-common language-pack-gnome-en-base libgnomeprint2.2-0 cupsys-client libpango1.0-0 desktop-file-utils eog libnautilus-extension1 yelp python2.4-pyorbit deskbar-applet libgnomeui-0 libvte-common
2006-10-19 16:39:19,769 DEBUG updateSourcesList()
2006-10-19 16:39:19,808 DEBUG rewriteSourcesList()
2006-10-19 16:39:20,169 DEBUG examining: 'deb http://packages.freecontrib.org/plf/ dapper free non-free'
2006-10-19 16:39:20,170 DEBUG entry '# deb http://packages.freecontrib.org/plf/ dapper free non-free' was disabled (unknown mirror)
2006-10-19 16:39:20,170 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted'
2006-10-19 16:39:20,171 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted' updated to new dist
2006-10-19 16:39:20,171 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted'
2006-10-19 16:39:20,171 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted' updated to new dist
2006-10-19 16:39:20,171 DEBUG examining: 'deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse main restricted'
2006-10-19 16:39:20,171 DEBUG entry 'deb http://archive.ubuntu.com/ubuntu/ edgy universe multiverse main restricted' updated to new dist
2006-10-19 16:39:20,171 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe multiverse'
2006-10-19 16:39:20,171 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe multiverse' updated to new dist
2006-10-19 16:39:20,172 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse'
2006-10-19 16:39:20,172 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse' updated to new dist
2006-10-19 16:39:20,172 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu dapper-security main restricted'
2006-10-19 16:39:20,172 DEBUG entry 'deb http://security.ubuntu.com/ubuntu edgy-security main restricted' updated to new dist
2006-10-19 16:39:20,172 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted'
2006-10-19 16:39:20,172 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted' updated to new dist
2006-10-19 16:39:20,172 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu dapper-security universe'
2006-10-19 16:39:20,172 DEBUG entry 'deb http://security.ubuntu.com/ubuntu edgy-security universe' updated to new dist
2006-10-19 16:39:20,173 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu dapper-security universe'
2006-10-19 16:39:20,173 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu edgy-security universe' updated to new dist
2006-10-19 16:39:20,173 DEBUG examining: 'deb http://theli.free.fr/packages/ dapper listen'
2006-10-19 16:39:20,174 DEBUG entry '# deb http://theli.free.fr/packages/ dapper listen' was disabled (unknown mirror)
2006-10-19 16:39:20,174 DEBUG examining: 'deb http://planet76.com/repositories/ ./'
2006-10-19 16:39:20,175 DEBUG entry '# deb http://planet76.com/repositories/ ./' was disabled (unknown mirror)
2006-10-19 16:39:20,175 DEBUG examining: 'deb http://xgl.compiz.info/ dapper aiglx'
2006-10-19 16:39:20,177 DEBUG entry '# deb http://xgl.compiz.info/ dapper aiglx' was disabled (unknown mirror)
2006-10-19 16:39:20,177 DEBUG examining: 'deb http://xgl.compiz.info/ dapper main'
2006-10-19 16:39:20,178 DEBUG entry '# deb http://xgl.compiz.info/ dapper main' was disabled (unknown mirror)
2006-10-19 16:39:20,178 DEBUG examining: 'deb http://wine.budgetdedicated.com/apt dapper main'
2006-10-19 16:39:20,179 DEBUG entry '# deb http://wine.budgetdedicated.com/apt dapper main' was disabled (unknown mirror)
2006-10-19 16:39:20,179 DEBUG examining: 'deb http://ubuntu.beryl-project.org/ dapper main aiglx'
2006-10-19 16:39:20,180 DEBUG entry '# deb http://ubuntu.beryl-project.org/ dapper main aiglx' was disabled (unknown mirror)
2006-10-19 16:40:01,913 DEBUG Purging 'xorg-common' (Distro PostUpgradePurge rule)
2006-10-19 16:40:01,913 DEBUG Purging 'libgl1-mesa' (Distro PostUpgradePurge rule)
2006-10-19 16:40:01,915 DEBUG running edgyQuirks handler
2006-10-19 16:40:01,921 DEBUG Installing 'python-tk' (python2.4->python upgrade rule)
2006-10-19 16:40:01,969 DEBUG Installing 'python-pycurl' (python2.4->python upgrade rule)
2006-10-19 16:40:01,971 DEBUG Installing 'python-sqlite' (python2.4->python upgrade rule)
2006-10-19 16:40:01,976 DEBUG Installing 'python-egenix-mxtexttools' (python2.4->python upgrade rule)
2006-10-19 16:40:01,977 DEBUG Installing 'python-ldap' (python2.4->python upgrade rule)
2006-10-19 16:40:01,990 DEBUG Installing 'xserver-xorg-input-mouse' (xserver-xorg-input fixup rule)
2006-10-19 16:40:01,992 DEBUG Installing 'xserver-xorg-input-synaptics' (xserver-xorg-input fixup rule)
2006-10-19 16:40:02,003 DEBUG Installing 'python-clientcookie' (python2.4->python upgrade rule)
2006-10-19 16:40:02,007 DEBUG Installing 'python-soappy' (python2.4->python upgrade rule)
2006-10-19 16:40:02,008 DEBUG Installing 'python-xmpp' (python2.4->python upgrade rule)
2006-10-19 16:40:02,008 DEBUG Installing 'python-gadfly' (python2.4->python upgrade rule)
2006-10-19 16:40:02,010 DEBUG Installing 'python-reportlab' (python2.4->python upgrade rule)
2006-10-19 16:40:02,011 DEBUG Installing 'python-jabber' (python2.4->python upgrade rule)
2006-10-19 16:40:02,012 DEBUG Installing 'python-pylibacl' (python2.4->python upgrade rule)
2006-10-19 16:40:02,013 DEBUG Installing 'python-syck' (python2.4->python upgrade rule)
2006-10-19 16:40:02,016 DEBUG Installing 'python-gtk2' (python2.4->python upgrade rule)
2006-10-19 16:40:02,016 DEBUG Installing 'python-unit' (python2.4->python upgrade rule)
2006-10-19 16:40:02,017 DEBUG Installing 'python-geoip' (python2.4->python upgrade rule)
2006-10-19 16:40:02,019 DEBUG Installing 'python-kjbuckets' (python2.4->python upgrade rule)
2006-10-19 16:40:02,020 DEBUG Installing 'python-id3lib' (python2.4->python upgrade rule)
2006-10-19 16:40:02,024 DEBUG Installing 'python-eunuchs' (python2.4->python upgrade rule)
2006-10-19 16:40:02,029 DEBUG Installing 'python-libxml2' (python2.4->python upgrade rule)
2006-10-19 16:40:02,030 DEBUG Installing 'python-glade2' (python2.4->python upgrade rule)
2006-10-19 16:40:02,030 DEBUG Installing 'python-pyxattr' (python2.4->python upgrade rule)
2006-10-19 16:40:02,032 DEBUG Installing 'python-imaging-sane' (python2.4->python upgrade rule)
2006-10-19 16:40:02,033 DEBUG Installing 'python-pyorbit' (python2.4->python upgrade rule)
2006-10-19 16:40:02,034 DEBUG Installing 'python-gdbm' (python2.4->python upgrade rule)
2006-10-19 16:40:02,037 DEBUG Installing 'python-pgsql' (python2.4->python upgrade rule)
2006-10-19 16:40:02,040 DEBUG Installing 'python-apt' (python2.4->python upgrade rule)
2006-10-19 16:40:02,040 DEBUG Installing 'python-pyopenssl' (python2.4->python upgrade rule)
2006-10-19 16:40:02,042 DEBUG Installing 'python-numeric' (python2.4->python upgrade rule)
2006-10-19 16:40:02,044 DEBUG Installing 'python-htmlgen' (python2.4->python upgrade rule)
2006-10-19 16:40:02,044 DEBUG Installing 'python-egenix-mxtools' (python2.4->python upgrade rule)
2006-10-19 16:40:02,044 DEBUG Installing 'xserver-xorg-input-kbd' (xserver-xorg-input fixup rule)
2006-10-19 16:40:02,045 DEBUG Installing 'python-simpletal' (python2.4->python upgrade rule)
2006-10-19 16:40:02,052 DEBUG Installing 'python-pexpect' (python2.4->python upgrade rule)
2006-10-19 16:40:02,053 DEBUG Installing 'python-libxslt1' (python2.4->python upgrade rule)
2006-10-19 16:40:02,055 DEBUG Installing 'python-egenix-mxproxy' (python2.4->python upgrade rule)
2006-10-19 16:40:02,055 DEBUG Installing 'python-htmltmpl' (python2.4->python upgrade rule)
2006-10-19 16:40:02,057 DEBUG Installing 'python-egenix-mxstack' (python2.4->python upgrade rule)
2006-10-19 16:40:02,057 DEBUG Installing 'python-pam' (python2.4->python upgrade rule)
2006-10-19 16:40:02,058 DEBUG Installing 'python-mysqldb' (python2.4->python upgrade rule)
2006-10-19 16:40:02,059 DEBUG Installing 'python-gd' (python2.4->python upgrade rule)
2006-10-19 16:40:02,062 DEBUG Installing 'python-imaging' (python2.4->python upgrade rule)
2006-10-19 16:40:02,064 DEBUG Installing 'xserver-xorg-input-evdev' (xserver-xorg-input fixup rule)
2006-10-19 16:40:02,064 DEBUG Installing 'python-xml' (python2.4->python upgrade rule)
2006-10-19 16:40:02,065 DEBUG Installing 'python-gnome2-extras' (python2.4->python upgrade rule)
2006-10-19 16:40:02,065 DEBUG Installing 'xserver-xorg-input-elographics' (xserver-xorg-input fixup rule)
2006-10-19 16:40:02,067 DEBUG Installing 'python-epydoc' (python2.4->python upgrade rule)
2006-10-19 16:40:02,068 DEBUG Installing 'python-adns' (python2.4->python upgrade rule)
2006-10-19 16:40:02,070 DEBUG Installing 'python-gnome2-desktop' (python2.4->python upgrade rule)
2006-10-19 16:40:02,070 DEBUG Installing 'python-gnome2' (python2.4->python upgrade rule)
2006-10-19 16:40:02,071 DEBUG Installing 'python-crypto' (python2.4->python upgrade rule)
2006-10-19 16:40:02,072 DEBUG Installing 'python-opengl' (python2.4->python upgrade rule)
2006-10-19 16:40:02,075 DEBUG Installing 'hpijs' (hpijs quirk upgrade rule)
2006-10-19 16:40:02,127 DEBUG no {ubuntu,edubuntu,kubuntu}-desktop pkg installed
2006-10-19 16:40:02,127 DEBUG guessing 'ubuntu-desktop' as missing meta-pkg
2006-10-19 16:40:02,176 ERROR failed to mark 'ubuntu-desktop' for install (E:Unable to correct problems, you have held broken packages.)
2006-10-19 16:40:06,430 ERROR Dist-upgrade failed: 'Can't upgrade required meta-packages'

```

---

### Post by crichell on 2006-10-19
are you running the upgrade via this command?

```
gksu "update-manager -c -d"
```

or changing the repo names?

---

### Post by frainbart on 2006-10-19
> **crichell said:**
> are you running the upgrade via this command?

```
gksu "update-manager -c -d"
```

or changing the repo names?

Yup, I ran that command. The actual error is:
```
Could not calculate the upgrade

A unresolvable problem occurred while calculating the upgrade.

Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.
```

---

### Post by crichell on 2006-10-19
This is related to external XGL packages - the Edgy upgrade doesn't work well with downgrading them to the Edgy supplied XGL packages.  The following should fix the problem:

```
sudo dpkg -r --force-depends libgl1-mesa libgl1-dev
libgl1-dri libglu1-mesa libglu1-mesa-dev mesa-common-dev mesa-utils
```
Then
> sudo apt-get install -f
and finally the upgrade
```
gksu "update-manager -c -d"
```

---

### Post by frainbart on 2006-10-19
I got further along in the install, but still not completed.

my main.log
```
2006-10-19 18:22:32,609 DEBUG Foreign: system76-driver poppler-utils gsynaptics libgl1-mesa-dri beryl-plugins skype libtunepimp2c2a libxss1 beryl-settings libdvdcss2 beryl-plugins-data beryl xserver-xorg-driver-ati libgl1-mesa libwnck-common unace compiz-plugins beryl-core beryl-manager libxfixes3 linux-dri-modules-2.6.15-26-686 libdrm2 libxcomposite1 libpoppler1 emerald libwnck18 libglu1-mesa xserver-xorg-driver-i810 w32codecs libpoppler1-glib mesa-utils linux-dri-modules-common gnome-session xserver-xorg-air-core wine
2006-10-19 18:22:32,610 DEBUG Obsolete: gnome-doc-utils wpasupplicant gstreamer0.10-alsa libcupsimage2 python-gmenu emerald-themes-extra language-selector democracyplayer-data gdm compiz-gnome python-pyorbit gtk2-engines-thinice gtk2-engines-lighthouseblue gtk2-engines-industrial compiz-core pam-keyring-0.0.8 nautilus-cd-burner libgtkhtml3.8-15 libtotem-plparser1 gtk2-engines-crux app-install-data libgtk2.0-0 gnome-about evince gtkhtml3.8 libgtksourceview-common gnome-control-center ubuntu-standard gnome-applets libglib2.0-0 cupsys-bsd libgnomeui-common compiz-manager compiz libgnome-menu2 libcupsys2 gstreamer0.10-plugins-base-apps gnome-accessibility-themes language-pack-en libgnome-desktop-2 gtk2-engines-pixbuf libsoup2.2-8 acpi-support libeel2-2 libgstreamer-plugins-base0.10-0 libgnomeprint2.2-data gnome-terminal gtk2-engines-smooth ubuntu-minimal gnome-panel gnome-games gstreamer0.10-x libgtkmm-2.4-1c2a pcmcia-cs libgnomevfs2-0 gtk2-engines-clearlooks gnome-media nautilus-data capplets-data language-pack-gnome-en python-vte pmount oem-config-locale libglib2.0-data libpango1.0-common libgtk2.0-bin libgtksourceview1.0-0 xserver-xorg-core gtk2-engines-redmond95 gtk2-engines-highcontrast libnautilus-burn3 gnome-panel-data language-pack-en-base gnome-terminal-data gtk2-engines-mist xserver-xorg-input-mouse localechooser-data file-roller libpanel-applet2-0 libgnomecups1.0-1 libeel2-data cupsys libgnomevfs2-common metacity gnome-screensaver app-install-data-commercial python2.4-gtkglext1 democracyplayer gedit-common ubuntu-docs language-selector-common libglibmm-2.4-1c2a sound-juicer libvte4 gnome-menus nautilus gstreamer0.10-plugins-base gnome-themes libmetacity0 zenity gedit base-files gnome-app-install libgnomevfs2-extra csm gstreamer0.10-gnomevfs gnome-desktop-data gnome-games-data gnome-applets-data libgnomevfs2-bin libgtk2.0-common language-pack-gnome-en-base libgnomeprint2.2-0 cupsys-client libpango1.0-0 desktop-file-utils eog libnautilus-extension1 yelp python2.4-pyorbit deskbar-applet libgnomeui-0 libvte-common
2006-10-19 18:22:32,611 DEBUG updateSourcesList()
2006-10-19 18:22:32,641 DEBUG rewriteSourcesList()
2006-10-19 18:22:33,001 DEBUG examining: 'deb http://packages.freecontrib.org/plf/ dapper free non-free'
2006-10-19 18:22:33,003 DEBUG entry '# deb http://packages.freecontrib.org/plf/ dapper free non-free' was disabled (unknown mirror)
2006-10-19 18:22:33,003 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted'
2006-10-19 18:22:33,003 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted' updated to new dist
2006-10-19 18:22:33,003 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted'
2006-10-19 18:22:33,003 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted' updated to new dist
2006-10-19 18:22:33,003 DEBUG examining: 'deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse main restricted'
2006-10-19 18:22:33,004 DEBUG entry 'deb http://archive.ubuntu.com/ubuntu/ edgy universe multiverse main restricted' updated to new dist
2006-10-19 18:22:33,004 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe multiverse'
2006-10-19 18:22:33,004 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe multiverse' updated to new dist
2006-10-19 18:22:33,004 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse'
2006-10-19 18:22:33,004 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse' updated to new dist
2006-10-19 18:22:33,004 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu dapper-security main restricted'
2006-10-19 18:22:33,004 DEBUG entry 'deb http://security.ubuntu.com/ubuntu edgy-security main restricted' updated to new dist
2006-10-19 18:22:33,004 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted'
2006-10-19 18:22:33,005 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted' updated to new dist
2006-10-19 18:22:33,005 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu dapper-security universe'
2006-10-19 18:22:33,005 DEBUG entry 'deb http://security.ubuntu.com/ubuntu edgy-security universe' updated to new dist
2006-10-19 18:22:33,005 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu dapper-security universe'
2006-10-19 18:22:33,005 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu edgy-security universe' updated to new dist
2006-10-19 18:22:33,005 DEBUG examining: 'deb http://theli.free.fr/packages/ dapper listen'
2006-10-19 18:22:33,006 DEBUG entry '# deb http://theli.free.fr/packages/ dapper listen' was disabled (unknown mirror)
2006-10-19 18:22:33,006 DEBUG examining: 'deb http://planet76.com/repositories/ ./'
2006-10-19 18:22:33,008 DEBUG entry '# deb http://planet76.com/repositories/ ./' was disabled (unknown mirror)
2006-10-19 18:22:33,008 DEBUG examining: 'deb http://xgl.compiz.info/ dapper aiglx'
2006-10-19 18:22:33,009 DEBUG entry '# deb http://xgl.compiz.info/ dapper aiglx' was disabled (unknown mirror)
2006-10-19 18:22:33,009 DEBUG examining: 'deb http://xgl.compiz.info/ dapper main'
2006-10-19 18:22:33,010 DEBUG entry '# deb http://xgl.compiz.info/ dapper main' was disabled (unknown mirror)
2006-10-19 18:22:33,010 DEBUG examining: 'deb http://wine.budgetdedicated.com/apt dapper main'
2006-10-19 18:22:33,012 DEBUG entry '# deb http://wine.budgetdedicated.com/apt dapper main' was disabled (unknown mirror)
2006-10-19 18:22:33,012 DEBUG examining: 'deb http://ubuntu.beryl-project.org/ dapper main aiglx'
2006-10-19 18:22:33,013 DEBUG entry '# deb http://ubuntu.beryl-project.org/ dapper main aiglx' was disabled (unknown mirror)
2006-10-19 18:22:41,972 DEBUG Removing 'xscreensaver' (ubuntu-desktop PostUpgradeRemove rule)
2006-10-19 18:22:41,972 DEBUG Purging 'xorg-common' (Distro PostUpgradePurge rule)
2006-10-19 18:22:41,973 DEBUG Purging 'libgl1-mesa' (Distro PostUpgradePurge rule)
2006-10-19 18:22:41,975 DEBUG running edgyQuirks handler
2006-10-19 18:22:41,980 DEBUG Installing 'python-tk' (python2.4->python upgrade rule)
2006-10-19 18:22:42,030 DEBUG Installing 'python-pycurl' (python2.4->python upgrade rule)
2006-10-19 18:22:42,032 DEBUG Installing 'python-sqlite' (python2.4->python upgrade rule)
2006-10-19 18:22:42,037 DEBUG Installing 'python-egenix-mxtexttools' (python2.4->python upgrade rule)
2006-10-19 18:22:42,039 DEBUG Installing 'python-ldap' (python2.4->python upgrade rule)
2006-10-19 18:22:42,044 DEBUG Installing 'xserver-xorg-input-mouse' (xserver-xorg-input fixup rule)
2006-10-19 18:22:42,046 DEBUG Installing 'xserver-xorg-input-synaptics' (xserver-xorg-input fixup rule)
2006-10-19 18:22:42,052 DEBUG Installing 'python-clientcookie' (python2.4->python upgrade rule)
2006-10-19 18:22:42,056 DEBUG Installing 'python-soappy' (python2.4->python upgrade rule)
2006-10-19 18:22:42,056 DEBUG Installing 'python-xmpp' (python2.4->python upgrade rule)
2006-10-19 18:22:42,057 DEBUG Installing 'python-gadfly' (python2.4->python upgrade rule)
2006-10-19 18:22:42,059 DEBUG Installing 'python-reportlab' (python2.4->python upgrade rule)
2006-10-19 18:22:42,060 DEBUG Installing 'python-jabber' (python2.4->python upgrade rule)
2006-10-19 18:22:42,061 DEBUG Installing 'python-pylibacl' (python2.4->python upgrade rule)
2006-10-19 18:22:42,062 DEBUG Installing 'python-syck' (python2.4->python upgrade rule)
2006-10-19 18:22:42,064 DEBUG Installing 'python-gtk2' (python2.4->python upgrade rule)
2006-10-19 18:22:42,065 DEBUG Installing 'python-unit' (python2.4->python upgrade rule)
2006-10-19 18:22:42,065 DEBUG Installing 'python-geoip' (python2.4->python upgrade rule)
2006-10-19 18:22:42,068 DEBUG Installing 'python-kjbuckets' (python2.4->python upgrade rule)
2006-10-19 18:22:42,069 DEBUG Installing 'python-id3lib' (python2.4->python upgrade rule)
2006-10-19 18:22:42,073 DEBUG Installing 'python-eunuchs' (python2.4->python upgrade rule)
2006-10-19 18:22:42,078 DEBUG Installing 'python-libxml2' (python2.4->python upgrade rule)
2006-10-19 18:22:42,078 DEBUG Installing 'python-glade2' (python2.4->python upgrade rule)
2006-10-19 18:22:42,079 DEBUG Installing 'python-pyxattr' (python2.4->python upgrade rule)
2006-10-19 18:22:42,081 DEBUG Installing 'python-imaging-sane' (python2.4->python upgrade rule)
2006-10-19 18:22:42,082 DEBUG Installing 'python-pyorbit' (python2.4->python upgrade rule)
2006-10-19 18:22:42,083 DEBUG Installing 'python-gdbm' (python2.4->python upgrade rule)
2006-10-19 18:22:42,086 DEBUG Installing 'python-pgsql' (python2.4->python upgrade rule)
2006-10-19 18:22:42,090 DEBUG Installing 'python-apt' (python2.4->python upgrade rule)
2006-10-19 18:22:42,090 DEBUG Installing 'python-pyopenssl' (python2.4->python upgrade rule)
2006-10-19 18:22:42,091 DEBUG Installing 'python-numeric' (python2.4->python upgrade rule)
2006-10-19 18:22:42,093 DEBUG Installing 'python-htmlgen' (python2.4->python upgrade rule)
2006-10-19 18:22:42,093 DEBUG Installing 'python-egenix-mxtools' (python2.4->python upgrade rule)
2006-10-19 18:22:42,094 DEBUG Installing 'xserver-xorg-input-kbd' (xserver-xorg-input fixup rule)
2006-10-19 18:22:42,094 DEBUG Installing 'python-simpletal' (python2.4->python upgrade rule)
2006-10-19 18:22:42,101 DEBUG Installing 'python-pexpect' (python2.4->python upgrade rule)
2006-10-19 18:22:42,102 DEBUG Installing 'python-libxslt1' (python2.4->python upgrade rule)
2006-10-19 18:22:42,104 DEBUG Installing 'python-egenix-mxproxy' (python2.4->python upgrade rule)
2006-10-19 18:22:42,105 DEBUG Installing 'python-htmltmpl' (python2.4->python upgrade rule)
2006-10-19 18:22:42,106 DEBUG Installing 'python-egenix-mxstack' (python2.4->python upgrade rule)
2006-10-19 18:22:42,107 DEBUG Installing 'python-pam' (python2.4->python upgrade rule)
2006-10-19 18:22:42,108 DEBUG Installing 'python-mysqldb' (python2.4->python upgrade rule)
2006-10-19 18:22:42,109 DEBUG Installing 'python-gd' (python2.4->python upgrade rule)
2006-10-19 18:22:42,112 DEBUG Installing 'python-imaging' (python2.4->python upgrade rule)
2006-10-19 18:22:42,114 DEBUG Installing 'xserver-xorg-input-evdev' (xserver-xorg-input fixup rule)
2006-10-19 18:22:42,114 DEBUG Installing 'python-xml' (python2.4->python upgrade rule)
2006-10-19 18:22:42,115 DEBUG Installing 'python-gnome2-extras' (python2.4->python upgrade rule)
2006-10-19 18:22:42,115 DEBUG Installing 'xserver-xorg-input-elographics' (xserver-xorg-input fixup rule)
2006-10-19 18:22:42,117 DEBUG Installing 'python-epydoc' (python2.4->python upgrade rule)
2006-10-19 18:22:42,118 DEBUG Installing 'python-adns' (python2.4->python upgrade rule)
2006-10-19 18:22:42,120 DEBUG Installing 'python-gnome2-desktop' (python2.4->python upgrade rule)
2006-10-19 18:22:42,120 DEBUG Installing 'python-gnome2' (python2.4->python upgrade rule)
2006-10-19 18:22:42,121 DEBUG Installing 'python-crypto' (python2.4->python upgrade rule)
2006-10-19 18:22:42,123 DEBUG Installing 'python-opengl' (python2.4->python upgrade rule)
2006-10-19 18:22:42,126 DEBUG Installing 'hpijs' (hpijs quirk upgrade rule)
2006-10-19 18:22:42,173 DEBUG Marking 'ubuntu-desktop' for upgrade
2006-10-19 18:22:42,221 DEBUG Can't mark 'ubuntu-desktop' for upgrade (E:Unable to correct problems, you have held broken packages.)
2006-10-19 18:22:50,877 ERROR Dist-upgrade failed: 'Can't upgrade required meta-packages'

```

---

### Post by crichell on 2006-10-19
make sure you're getting both lines of this command:

```
sudo dpkg -r --force-depends libgl1-mesa libgl1-dev libgl1-dri libglu1-mesa libglu1-mesa-dev mesa-common-dev mesa-utils
```

Looks like some of these packages are still installed

---

### Post by frainbart on 2006-10-19
I've tried it multiple times, still no go...

---

### Post by crichell on 2006-10-19
I've had this happen during upgrade testing - this bug report fixed it for me:

[https://launchpad.net/distros/ubuntu/+source/update-manager/+bug/58424](https://launchpad.net/distros/ubuntu/+source/update-manager/+bug/58424)

You can also try removing the system76 driver and re-installing after the upgrade.  I haven't had to do this thus far but it's worth a shot.

---

### Post by frainbart on 2006-10-20
[https://launchpad.net/distros/ubuntu/+source/update-manager/+bug/63205]("https://launchpad.net/distros/ubuntu/+source/update-manager/+bug/63205")

I removed the libgl1-mesa-dri package using Synaptic and the installation is successfully proceeding now (it is now fetching all the upgrades), crossing my fingers...

---

### Post by frainbart on 2006-10-20
> **frainbart said:**
> [https://launchpad.net/distros/ubuntu/+source/update-manager/+bug/63205]("https://launchpad.net/distros/ubuntu/+source/update-manager/+bug/63205")

I removed the libgl1-mesa-dri package using Synaptic and the installation is successfully proceeding now (it is now fetching all the upgrades), crossing my fingers...

That did the trick. I had to fix a few options with Beryl afterwards. I didn't remove it before upgrading to Edgy, but removing the AIGLX server options from the gdm.conf-custom file and updating xorg.conf seemed to fix any wonky issues. 

So there you go, confirmed successful upgrade with Beryl running. :D

---

### Post by newlinux on 2006-10-20
Since I have the gazelle 12" with compiz, I'll be looking to this thread for when I upgrade... I upgraded my non system76 desktop with no real hitches (problems with the splash screens, but nothing I can't fix when I have the time). I hope the laptop goes smooth because I use it everyday. It's pretty much my primary machine. If I'd known it would be a headache. I think I would have waited for edgy and then installed Beryl.

---

### Post by crichell on 2006-10-20
The only problem we've encountered is this one.  Removing the packages does the trick but it's a little annoying.

---

### Post by newlinux on 2006-10-20
Yeah. Installing 3rd party stuff is always a little risky. But as long as I get it to upgrade it's fine by me.

---

### Post by frainbart on 2006-10-27
I am having some rare, sporadic issues with beryl at startup. I recommend just removing all XGL/compiz/beryl packages in Dapper before you upgrade to Edgy. Then reinstall beryl from scratch for Edgy from the new repositories.

---

### Post by newlinux on 2006-10-27
Yeah, I figured since it was causing problems with your upgrade that I would do that. Thank for the advice.

---

### Post by Nightknight83 on 2007-01-10
Greetings,

I get the same Issue (Error calculating package size), but removing libgl1-mesa-dri (Via Synapctic) didn't do the Trick.
You guys have any other Idea?
(Yes, I am using Beryl)

---

