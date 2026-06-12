---
title: "Can't Remove KaliTools from system"
date: 2015-08-20
forum: Ubuntu/Debian BASED
---

### Post by secofshadow on 2015-08-20
hi all,
i have problem whith kali tool it cant remove and when a type in tirminal sudo apt-get upgrade it n't work 
tht pic abaut my problem 

[IMG]http://im47.gulfup.com/OeNpRB.png[/IMG]http://im47.gulfup.com/OeNpRB.png

```

root@Shadow-Hack:/home/wolf# sudo apt-get upgrade
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Calculating upgrade... The following packages were automatically installed and are no longe
r required:
  gir1.2-gtk-2.0 icu-devtools java-wrappers john john-data libblas-common libblas3
  libcairo-script-interpreter2 libdigest-md5-file-perl libexpat1-dev libfontconfig1-dev
  libfreetype6-dev libglib2.0-dev libharfbuzz-dev libharfbuzz-gobject0
  libhttp-server-simple-perl libice-dev libicu-dev libjavascriptcoregtk-1.0-0
  libjavascriptcoregtk-1.0-dev liblinear1 libpcre3-dev libpcrecpp0 libpixman-1-dev
  libpng12-dev libpthread-stubs0-dev libruby1.9.1 libsm-dev libwebkitgtk-1.0-0
  libwebkitgtk-1.0-common libwww-mechanize-perl libx11-dev libx11-doc libxau-dev
  libxcb-render0-dev libxcb-shm0-dev libxcb1-dev libxcomposite-dev libxcursor-dev
  libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev libxft-dev libxi-dev
  libxinerama-dev libxml2-dev libxrandr-dev libxrender-dev libxt-dev ndiff nmap
  openjdk-7-jdk pkg-config postgresql ruby1.9.1 x11proto-composite-dev x11proto-core-dev
  x11proto-damage-dev x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev
  x11proto-randr-dev x11proto-render-dev x11proto-xext-dev x11proto-xinerama-dev
  xorg-sgml-doctools xtrans-dev
Use 'apt-get autoremove' to remove them.
Done
The following packages will be upgraded:
  apport
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
Need to get 0 B/6,187 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 201747 files and directories currently installed.)
Preparing to unpack .../apport_2.17.2-0ubuntu1.3_all.deb ...
  File "/usr/bin/pyclean", line 63
    except (IOError, OSError), e:
                             ^
SyntaxError: invalid syntax
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
  File "/usr/bin/pyclean", line 63
    except (IOError, OSError), e:
                             ^
SyntaxError: invalid syntax
dpkg: error processing archive /var/cache/apt/archives/apport_2.17.2-0ubuntu1.3_all.deb (--
unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/apport_2.17.2-0ubuntu1.3_all.deb
sh: 1: /usr/share/kali-menu/update-kali-menu: not found
E: Sub-process /usr/bin/dpkg returned an error code (1)
E: Problem executing scripts DPkg::Post-Invoke '/usr/share/kali-menu/update-kali-menu wait_
dpkg'
E: Sub-process returned an error code
root@Shadow-Hack:/home/wolf# 

```

help me plz

---

### Post by howefield on 2015-08-20
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by secofshadow on 2015-08-20
ok but plz help

---

