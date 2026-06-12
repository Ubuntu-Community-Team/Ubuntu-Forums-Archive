---
title: "Regressions in gnome-session-flashback"
date: 2014-10-13
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2014-10-13
I'll keep adding to the list:

[Installing gnome-session-flashback in Ubuntu GNOME Utopic provides a Flashback (Compiz) session when compiz is not installed]("https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1380843")

[Menus in gnome-session-flashback are bloated in Utopic]("https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1380850")

[URL="https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1380857"]Can't edit drop down applications menus in Ubuntu GNOME Utopic flashback session
[/URL]
Stay tuned for more ;)

---

### Post by mc4man on 2014-10-13
What does this show (just curious
```
gedit /usr/share/xsessions/gnome-fallback-compiz.desktop
```
Assuming based on previous that it *should*? have this line

TryExec=compiz

---

### Post by kansasnoob on 2014-10-13
> **mc4man said:**
> What does this show (just curious
```
gedit /usr/share/xsessions/gnome-fallback-compiz.desktop
```
Assuming based on previous that it *should*? have this line

TryExec=compiz

Had to go on a hunting expedition:

```
lance@lance-desktop:~$ cat /usr/share/xsessions/gnome-fallback-compiz.desktop
cat: /usr/share/xsessions/gnome-fallback-compiz.desktop: No such file or directory
lance@lance-desktop:~$ gedit /usr/share/xsessions/gnome-fallback-compiz.desktop  **##Displayed blank file so I closed w/o saving.**
lance@lance-desktop:~$ ls /usr/share/xsessions
gnome-classic.desktop  gnome-fallback.desktop
gnome.desktop          gnome-flashback-compiz.desktop
lance@lance-desktop:~$ cat /usr/share/xsessions/gnome-flashback-compiz.desktop
[Desktop Entry]
Name=GNOME Flashback (Compiz)
Comment=This session logs you into GNOME with Compiz window-manager and the traditional panel
Exec=/usr/lib/gnome-panel/gnome-session-flashback --session=gnome-flashback-compiz
TryExec=/usr/lib/gnome-panel/gnome-session-flashback
Icon=
Type=Application
X-LightDM-DesktopName=Unity
X-Ubuntu-Gettext-Domain=gnome-panel-3.0

```

---

### Post by mc4man on 2014-10-13
Well then the fix for trusty (change that line to TryExec=compiz) isn't in 14.10 
Maybe - 
It's not needed
The fact that it's using a different named .desktop allowed the fix to slip thru the cracks &  not be applied
Something else/

If you're in a position to test then try editing (as root) /usr/share/xsessions/gnome-flashback-compiz.desktop & make it - 
TryExec=compiz
Then go about however you're currently seeing the bug & see if it fixes.

---

### Post by ventrical on 2014-10-14
In metacity sesssion:

-Drag n' drop from mouse opens multiple windows of nautilus.
-When attempting to drag an open nautilus window (with jpegs in them) the mouse click will maximize window. Will not do this with normal files or folders.
-tweaking mouse from System Settings does not fix.

---

### Post by mc4man on 2014-10-14
All the bugs in post 1 are fix released

---

### Post by kansasnoob on 2014-10-14
Crazy dependencies now:

```
lance@lance-desktop:~$ sudo apt-get install gnome-panel
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  alacarte evolution evolution-common evolution-plugins gir1.2-gconf-2.0
  gir1.2-panelapplet-4.0 gnome-applets gnome-applets-data gnome-media
  gnome-panel-data gnome-session-flashback gstreamer0.10-gconf
  indicator-applet-complete libcpufreq0 libencode-locale-perl liberror-perl
  libevolution libfile-listing-perl libfont-afm-perl
  libgnome-media-profiles-3.0-0 libgtkhtml-4.0-0 libgtkhtml-4.0-common
  libgtkhtml-editor-4.0-0 libgtkspell3-3-0 libhtml-form-perl
  libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl
  libhtml-tree-perl libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl
  libhttp-message-perl libhttp-negotiate-perl libio-html-perl
  liblwp-mediatypes-perl liblwp-protocol-https-perl libmail-spf-perl
  libnet-http-perl libnetaddr-ip-perl libpanel-applet-4-0 libpst4
  libsys-hostname-long-perl libwww-perl libwww-robotrules-perl libytnef0
  metacity notification-daemon re2c sa-compile spamassassin spamc
Suggested packages:
  evolution-ews evolution-plugins-experimental tomboy desktop-base
  libdata-dump-perl libcrypt-ssleay-perl libauthen-ntlm-perl
  gnome-control-center razor libdbi-perl pyzor libmail-dkim-perl
The following NEW packages will be installed:
  alacarte evolution evolution-common evolution-plugins gir1.2-gconf-2.0
  gir1.2-panelapplet-4.0 gnome-applets gnome-applets-data gnome-media
  gnome-panel gnome-panel-data gnome-session-flashback gstreamer0.10-gconf
  indicator-applet-complete libcpufreq0 libencode-locale-perl liberror-perl
  libevolution libfile-listing-perl libfont-afm-perl
  libgnome-media-profiles-3.0-0 libgtkhtml-4.0-0 libgtkhtml-4.0-common
  libgtkhtml-editor-4.0-0 libgtkspell3-3-0 libhtml-form-perl
  libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl
  libhtml-tree-perl libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl
  libhttp-message-perl libhttp-negotiate-perl libio-html-perl
  liblwp-mediatypes-perl liblwp-protocol-https-perl libmail-spf-perl
  libnet-http-perl libnetaddr-ip-perl libpanel-applet-4-0 libpst4
  libsys-hostname-long-perl libwww-perl libwww-robotrules-perl libytnef0
  metacity notification-daemon re2c sa-compile spamassassin spamc
0 upgraded, 53 newly installed, 0 to remove and 3 not upgraded.
Need to get 15.3 MB of archives.
After this operation, 79.3 MB of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.

```

I'll have to look into that ;)

Even with the --no-install-recommends suffix apt still wants to install evolution:

```
lance@lance-desktop:~$ sudo apt-get install gnome-panel --no-install-recommends -s
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  evolution-common gnome-panel-data libpanel-applet-4-0
Recommended packages:
  evolution alacarte gnome-applets gnome-session-flashback
  indicator-applet-complete
The following NEW packages will be installed:
  evolution-common gnome-panel gnome-panel-data libpanel-applet-4-0
0 upgraded, 4 newly installed, 0 to remove and 10 not upgraded.
Inst evolution-common (3.12.7-0ubuntu1 Ubuntu:14.10/utopic [all])
Inst gnome-panel-data (1:3.8.1-2ubuntu4 Ubuntu:14.10/utopic [all])
Inst libpanel-applet-4-0 (1:3.8.1-2ubuntu4 Ubuntu:14.10/utopic [i386])
Inst gnome-panel (1:3.8.1-2ubuntu4 Ubuntu:14.10/utopic [i386])
Conf evolution-common (3.12.7-0ubuntu1 Ubuntu:14.10/utopic [all])
Conf gnome-panel-data (1:3.8.1-2ubuntu4 Ubuntu:14.10/utopic [all])
Conf libpanel-applet-4-0 (1:3.8.1-2ubuntu4 Ubuntu:14.10/utopic [i386])
Conf gnome-panel (1:3.8.1-2ubuntu4 Ubuntu:14.10/utopic [i386])

```

Looks like the actual depends are just messed up:

```
lance@lance-desktop:~$ apt-cache show gnome-panel 
Package: gnome-panel
Priority: optional
Section: universe/gnome
Installed-Size: 1494
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian GNOME Maintainers <pkg-gnome-maintainers@lists.alioth.debian.org>
Architecture: i386
Version: 1:3.8.1-2ubuntu4
Replaces: gnome-panel-data (<< 2.91)
Depends: evolution-common (>= 3.4.3), gnome-icon-theme-symbolic (>= 3.0.0), gnome-menus (>= 3.1.4), gnome-panel-data (= 1:3.8.1-2ubuntu4), gconf-service, libatk1.0-0 (>= 1.12.4), libc6 (>= 2.7), libcairo2 (>= 1.10.0), libdconf1 (>= 0.14.0), libecal-1.2-16 (>= 3.5.91), libedataserver-1.2-18 (>= 3.5.91), libgconf-2-4 (>= 3.2.5), libgdk-pixbuf2.0-0 (>= 2.25.2), libglib2.0-0 (>= 2.41.1), libgnome-desktop-3-10 (>= 3.2.0), libgnome-menu-3-0 (>= 3.2.0.1), libgtk-3-0 (>= 3.3.16), libgweather-3-6 (>= 3.7.91), libical1 (>= 1.0), libice6 (>= 1:1.0.0), libpanel-applet-4-0 (>= 3.4.1), libpango-1.0-0 (>= 1.18.0), libpolkit-gobject-1-0 (>= 0.99), librsvg2-2 (>= 2.32.0), libsm6, libtelepathy-glib0 (>= 0.14.0), libwnck-3-0 (>= 3.4.6), libx11-6, libxrandr2 (>= 2:1.2.99.3)
Recommends: alacarte, evolution-data-server, gnome-applets, gnome-icon-theme (>= 2.24), gnome-session-flashback, gvfs, indicator-applet-complete, unity-control-center
Suggests: gnome-terminal | x-terminal-emulator, gnome-user-guide, nautilus, yelp
Breaks: gnome-applets (<< 2.91), gnome-control-center (<< 1:2.91), gnome-settings-daemon (<< 2.91), libpanel-applet2-0, netspeed (<< 0.16-2)
Filename: pool/universe/g/gnome-panel/gnome-panel_3.8.1-2ubuntu4_i386.deb
Size: 384770
MD5sum: 227362a4b3b8ef4656d98de628fe8e01
SHA1: 259c67b759b6e2615bcf599cd9316d60920aeb14
SHA256: 1876760a32c93fe9a327d404f13c94dbbd2e08b72bbf3d824b3ff1d0f62fb1f8
Description-en: launcher and docking facility for GNOME
 The GNOME Panel is an essential part of the GNOME Desktop, providing
 toolbar-like “panels” which can be attached to the sides of your desktop.
 They are used to launch applications and embed a number of other
 functions, such as quick launch icons, the clock, the notification area,
 volume controls and the battery charge indicator, and utilities ranging
 from weather forecast to system monitoring.
Description-md5: 02085226815ba9e6a5733ab8ea00c173
Homepage: https://wiki.gnome.org/action/show/Projects/GnomeFlashback
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 9m
Task: edubuntu-desktop-gnome

```

Arrgh - trying to file a bug report but Launchpad keeps puking:

[ATTACH=CONFIG]257218[/ATTACH]

Finally:

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1381232](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1381232)

I'll need this info later:

```
lance@lance-desktop:~$ sudo apt-get install evolution-common -s
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  evolution evolution-plugins libencode-locale-perl liberror-perl libevolution
  libfile-listing-perl libfont-afm-perl libgtkhtml-4.0-0 libgtkhtml-4.0-common
  libgtkhtml-editor-4.0-0 libgtkspell3-3-0 libhtml-form-perl
  libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl
  libhtml-tree-perl libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl
  libhttp-message-perl libhttp-negotiate-perl libio-html-perl
  liblwp-mediatypes-perl liblwp-protocol-https-perl libmail-spf-perl
  libnet-http-perl libnetaddr-ip-perl libpst4 libsys-hostname-long-perl
  libwww-perl libwww-robotrules-perl libytnef0 re2c sa-compile spamassassin
  spamc
Suggested packages:
  evolution-ews evolution-plugins-experimental libdata-dump-perl
  libcrypt-ssleay-perl libauthen-ntlm-perl razor libdbi-perl pyzor
  libmail-dkim-perl
The following NEW packages will be installed:
  evolution evolution-common evolution-plugins libencode-locale-perl
  liberror-perl libevolution libfile-listing-perl libfont-afm-perl
  libgtkhtml-4.0-0 libgtkhtml-4.0-common libgtkhtml-editor-4.0-0
  libgtkspell3-3-0 libhtml-form-perl libhtml-format-perl libhtml-parser-perl
  libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl
  libhttp-daemon-perl libhttp-date-perl libhttp-message-perl
  libhttp-negotiate-perl libio-html-perl liblwp-mediatypes-perl
  liblwp-protocol-https-perl libmail-spf-perl libnet-http-perl
  libnetaddr-ip-perl libpst4 libsys-hostname-long-perl libwww-perl
  libwww-robotrules-perl libytnef0 re2c sa-compile spamassassin spamc
0 upgraded, 37 newly installed, 0 to remove and 10 not upgraded.
Inst libgtkhtml-4.0-common (4.8.4-3 Ubuntu:14.10/utopic [all])
Inst libgtkhtml-4.0-0 (4.8.4-3 Ubuntu:14.10/utopic [i386])
Inst libgtkhtml-editor-4.0-0 (4.8.4-3 Ubuntu:14.10/utopic [i386])
Inst libgtkspell3-3-0 (3.0.6-1 Ubuntu:14.10/utopic [i386])
Inst libytnef0 (1.5-6 Ubuntu:14.10/utopic [i386])
Inst libevolution (3.12.7-0ubuntu1 Ubuntu:14.10/utopic [i386])
Inst evolution-common (3.12.7-0ubuntu1 Ubuntu:14.10/utopic [all])
Inst evolution (3.12.7-0ubuntu1 Ubuntu:14.10/utopic [i386])
Inst libpst4 (0.6.59-1build1 Ubuntu:14.10/utopic [i386])
Inst evolution-plugins (3.12.7-0ubuntu1 Ubuntu:14.10/utopic [i386])
Inst libencode-locale-perl (1.03-1 Ubuntu:14.10/utopic [all])
Inst liberror-perl (0.17-1.1 Ubuntu:14.10/utopic [all])
Inst libhttp-date-perl (6.02-1 Ubuntu:14.10/utopic [all])
Inst libfile-listing-perl (6.04-1 Ubuntu:14.10/utopic [all])
Inst libfont-afm-perl (1.20-1 Ubuntu:14.10/utopic [all])
Inst libhtml-tagset-perl (3.20-2 Ubuntu:14.10/utopic [all])
Inst libhtml-parser-perl (3.71-1build2 Ubuntu:14.10/utopic [i386])
Inst libio-html-perl (1.001-1 Ubuntu:14.10/utopic [all])
Inst liblwp-mediatypes-perl (6.02-1 Ubuntu:14.10/utopic [all])
Inst libhttp-message-perl (6.06-1 Ubuntu:14.10/utopic [all])
Inst libhtml-form-perl (6.03-1 Ubuntu:14.10/utopic [all])
Inst libhtml-tree-perl (5.03-1 Ubuntu:14.10/utopic [all])
Inst libhtml-format-perl (2.11-1 Ubuntu:14.10/utopic [all])
Inst libhttp-cookies-perl (6.00-2 Ubuntu:14.10/utopic [all])
Inst libhttp-daemon-perl (6.01-1 Ubuntu:14.10/utopic [all])
Inst libhttp-negotiate-perl (6.00-2 Ubuntu:14.10/utopic [all])
Inst libnet-http-perl (6.07-1 Ubuntu:14.10/utopic [all])
Inst libwww-robotrules-perl (6.01-1 Ubuntu:14.10/utopic [all])
Inst libwww-perl (6.08-1 Ubuntu:14.10/utopic [all]) []
Inst liblwp-protocol-https-perl (6.06-2 Ubuntu:14.10/utopic [all])
Inst libnetaddr-ip-perl (4.075+dfsg-1build1 Ubuntu:14.10/utopic [i386])
Inst libmail-spf-perl (2.9.0-3 Ubuntu:14.10/utopic [all])
Inst libsys-hostname-long-perl (1.4-3 Ubuntu:14.10/utopic [all])
Inst re2c (0.13.5-1build2 Ubuntu:14.10/utopic [i386])
Inst spamassassin (3.4.0-2ubuntu1 Ubuntu:14.10/utopic [all])
Inst sa-compile (3.4.0-2ubuntu1 Ubuntu:14.10/utopic [all])
Inst spamc (3.4.0-2ubuntu1 Ubuntu:14.10/utopic [i386])
Conf libgtkhtml-4.0-common (4.8.4-3 Ubuntu:14.10/utopic [all])
Conf libgtkhtml-4.0-0 (4.8.4-3 Ubuntu:14.10/utopic [i386])
Conf libgtkhtml-editor-4.0-0 (4.8.4-3 Ubuntu:14.10/utopic [i386])
Conf libgtkspell3-3-0 (3.0.6-1 Ubuntu:14.10/utopic [i386])
Conf libytnef0 (1.5-6 Ubuntu:14.10/utopic [i386])
Conf libevolution (3.12.7-0ubuntu1 Ubuntu:14.10/utopic [i386])
Conf evolution-common (3.12.7-0ubuntu1 Ubuntu:14.10/utopic [all])
Conf evolution (3.12.7-0ubuntu1 Ubuntu:14.10/utopic [i386])
Conf libpst4 (0.6.59-1build1 Ubuntu:14.10/utopic [i386])
Conf evolution-plugins (3.12.7-0ubuntu1 Ubuntu:14.10/utopic [i386])
Conf libencode-locale-perl (1.03-1 Ubuntu:14.10/utopic [all])
Conf liberror-perl (0.17-1.1 Ubuntu:14.10/utopic [all])
Conf libhttp-date-perl (6.02-1 Ubuntu:14.10/utopic [all])
Conf libfile-listing-perl (6.04-1 Ubuntu:14.10/utopic [all])
Conf libfont-afm-perl (1.20-1 Ubuntu:14.10/utopic [all])
Conf libhtml-tagset-perl (3.20-2 Ubuntu:14.10/utopic [all])
Conf libhtml-parser-perl (3.71-1build2 Ubuntu:14.10/utopic [i386])
Conf libio-html-perl (1.001-1 Ubuntu:14.10/utopic [all])
Conf liblwp-mediatypes-perl (6.02-1 Ubuntu:14.10/utopic [all])
Conf libhttp-message-perl (6.06-1 Ubuntu:14.10/utopic [all])
Conf libhtml-form-perl (6.03-1 Ubuntu:14.10/utopic [all])
Conf libhtml-tree-perl (5.03-1 Ubuntu:14.10/utopic [all])
Conf libhtml-format-perl (2.11-1 Ubuntu:14.10/utopic [all])
Conf libhttp-cookies-perl (6.00-2 Ubuntu:14.10/utopic [all])
Conf libhttp-daemon-perl (6.01-1 Ubuntu:14.10/utopic [all])
Conf libhttp-negotiate-perl (6.00-2 Ubuntu:14.10/utopic [all])
Conf libnet-http-perl (6.07-1 Ubuntu:14.10/utopic [all])
Conf libwww-robotrules-perl (6.01-1 Ubuntu:14.10/utopic [all])
Conf libwww-perl (6.08-1 Ubuntu:14.10/utopic [all])
Conf liblwp-protocol-https-perl (6.06-2 Ubuntu:14.10/utopic [all])
Conf libnetaddr-ip-perl (4.075+dfsg-1build1 Ubuntu:14.10/utopic [i386])
Conf libmail-spf-perl (2.9.0-3 Ubuntu:14.10/utopic [all])
Conf libsys-hostname-long-perl (1.4-3 Ubuntu:14.10/utopic [all])
Conf re2c (0.13.5-1build2 Ubuntu:14.10/utopic [i386])
Conf spamassassin (3.4.0-2ubuntu1 Ubuntu:14.10/utopic [all])
Conf sa-compile (3.4.0-2ubuntu1 Ubuntu:14.10/utopic [all])
Conf spamc (3.4.0-2ubuntu1 Ubuntu:14.10/utopic [i386])

```

---

### Post by kansasnoob on 2014-10-14
> **mc4man said:**
> All the bugs in post 1 are fix released

Yep, updates should be hitting the repos soon :D

The flashback project has great devs.

---

### Post by kansasnoob on 2014-10-15
These three regressions are now fixed so I'm marking this solved, then I'll open a new thread about evolution now being a dependency of gnome-panel.

---

