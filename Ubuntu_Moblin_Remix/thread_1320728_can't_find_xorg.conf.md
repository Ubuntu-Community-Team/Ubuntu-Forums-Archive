---
title: "can't find xorg.conf"
date: 2009-11-09
forum: Ubuntu Moblin Remix
---

### Post by wimduk on 2009-11-09
Dear reader,


[LIST=1]
[*]I have installed the Ubuntu 9.10 remix on my Asus EeePC 1000h.
[*]On this machine I have attached a 19"Medion monitor
[*]If the Asus is started up with the external monitor attached the resolution is set for both screens to 840x460
[*]I found a possible solution in post [http://wiki.eeeuser.com/howto:external_monitor](http://wiki.eeeuser.com/howto:external_monitor), which requires updating xorg.conf
[*]I  looked for it in /etc/X11 but no xorg.conf file is there :( see listing #1
[*]Then I processed the command Sudo find -name xorg*.* from the root directory, but no xorg.conf results, see listing #2
[/LIST]

Can somebody help me to fix this problem?
Many thanks in advance

Kind regards wimduk
 
Listing #1 ------------------------------------------------------------------------------------------------------------------------------
/etc/X11 directory

drwxr-xr-x 2 root root  4096 2009-10-28 22:23 app-defaults
drwxr-xr-x 2 root root  4096 2009-10-28 22:23 cursors
-rw-r--r-- 1 root root    14 2009-10-28 22:24 default-display-manager
drwxr-xr-x 6 root root  4096 2009-10-28 22:19 fonts
-rw-r--r-- 1 root root 17394 2009-06-23 00:57 rgb.txt
lrwxrwxrwx 1 root root    13 2009-11-02 14:57 X -> /usr/bin/Xorg
drwxr-xr-x 3 root root  4096 2009-10-28 22:23 xinit
drwxr-xr-x 2 root root  4096 2009-10-28 22:14 xkb
drwxr-xr-x 2 root root  4096 2009-10-28 22:15 Xresources
-rwxr-xr-x 1 root root  3730 2008-06-25 04:05 Xsession
drwxr-xr-x 2 root root  4096 2009-10-28 22:24 Xsession.d
-rw-r--r-- 1 root root   265 2008-06-25 04:05 Xsession.options
-rw-r--r-- 1 root root    13 2009-08-25 02:37 XvMCConfig
-rw------- 1 root root   601 2009-10-28 22:15 Xwrapper.config

Listing #2 ------------------------------------------------------------------------------------------------------------------------------
Sudo find -name xorg*.* from root directory

./var/lib/dpkg/info/xorg-docs-core.list
./var/lib/dpkg/info/xorg.preinst
./var/lib/dpkg/info/xorg.list
./var/lib/dpkg/info/xorg-docs-core.md5sums
./etc/dbus-1/system.d/xorg-server.conf
./usr/lib/python2.6/dist-packages/XKit/xorgparser.py
./usr/lib/python2.6/dist-packages/XKit/xorgparser.pyc
./usr/lib/python2.6/dist-packages/jockey/xorg_driver.py
./usr/lib/python2.6/dist-packages/jockey/xorg_driver.pyc
./usr/lib/python2.6/dist-packages/DistUpgrade/xorg_fix_proprietary.pyc
./usr/lib/python2.6/dist-packages/DistUpgrade/xorg_fix_proprietary.py
./usr/lib/python2.5/site-packages/jockey/xorg_driver.py
./usr/lib/python2.5/site-packages/DistUpgrade/xorg_fix_proprietary.py
./usr/share/man/man5/xorg.conf.5.gz
./usr/share/icons/oxygen/128x128/apps/xorg.png
./usr/share/icons/oxygen/16x16/apps/xorg.png
./usr/share/icons/oxygen/22x22/apps/xorg.png
./usr/share/icons/oxygen/32x32/apps/xorg.png
./usr/share/icons/oxygen/48x48/apps/xorg.png
./usr/share/icons/oxygen/64x64/apps/xorg.png
./usr/share/X11/xkb/rules/xorg.xml
./usr/share/X11/xkb/rules/xorg.lst
./usr/share/pyshared/XKit/xorgparser.py
./usr/share/pyshared/jockey/xorg_driver.py
./usr/share/pyshared/DistUpgrade/xorg_fix_proprietary.py
./usr/share/kde4/apps/katepart/syntax/xorg.xml

---

### Post by viralmeme on 2009-11-09
[http://ubuntuforums.org/showthread.php?t=1174702](http://ubuntuforums.org/showthread.php?t=1174702)

---

### Post by wimduk on 2009-11-09
ymitchell, thanks :) regards wimduk ):P

---

