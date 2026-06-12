---
title: "Problem Installing Lazarus"
date: 2014-02-11
forum: Ubuntu Application Development
---

### Post by evagelos on 2014-02-11
I am trying to install lazarus 1.0.14 and i get this problem. I uninstalled previous installed version but i still get this :

ekriezis@ekriezis-VGN-SR19VN:~/Downloads$ sudo dpkg -i *.deb
Selecting previously unselected package fpc.
(Reading database ... 418101 files and directories currently installed.)
Unpacking fpc (from fpc_2.6.2-0_amd64.deb) ...
dpkg: error processing fpc_2.6.2-0_amd64.deb (--install):
 trying to overwrite '/usr/lib/fpc/2.6.2/msg/errores.msg', which is also in package fp-compiler-2.6.2 2.6.2-5
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking fpc-src (from fpc-src_2.6.2-0_amd64.deb) ...
dpkg: error processing fpc-src_2.6.2-0_amd64.deb (--install):
 trying to overwrite '/usr/share/fpcsrc/2.6.2/rtl/nativent/tthread.inc', which is also in package fpc-source-2.6.2 2.6.2-5
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Selecting previously unselected package lazarus.
Unpacking lazarus (from lazarus_1.0.10+dfsg-1_all.deb) ...
Preparing to replace lazarus 1.0.10+dfsg-1 (using lazarus_1.0.14-0_amd64.deb) ...
Unpacking replacement lazarus ...
More than one copy of package lazarus has been unpacked
 in this run !  Only configuring it once.
dpkg: dependency problems prevent configuration of lazarus:
 lazarus depends on fpc (>= 2.6.2) | fp-ide (>= 2.6.2); however:
  Package fpc is not installed.
  Package fpc is not installed.
  Package fp-ide is not installed.
 lazarus depends on fpc (>= 2.6.2) | fp-units-db (>= 2.6.2); however:
  Package fpc is not installed.
  Package fpc is not installed.
  Package fp-units-db is not installed.
 lazarus depends on fpc (>= 2.6.2) | fp-units-fv (>= 2.6.2); however:
  Package fpc is not installed.
  Package fpc is not installed.
  Package fp-units-fv is not installed.
 lazarus depends on fpc (>= 2.6.2) | fp-units-gfx (>= 2.6.2); however:
  Package fpc is not installed.
  Package fpc is not installed.
  Package fp-units-gfx is not installed.
 lazarus depends on fpc (>= 2.6.2) | fp-units-gnome1 (>= 2.6.2); however:
  Package fpc is not installed.
  Package fpc is not installed.
  Package fp-units-gnome1 is not installed.
 lazarus depends on fpc (>= 2.6.2) | fp-units-gtk (>= 2.6.2); however:
  Package fpc is not install
dpkg: error processing lazarus (--install):
 dependency problems - leaving unconfigured
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support ...
Processing triggers for man-db ...
Errors were encountered while processing:
 fpc_2.6.2-0_amd64.deb
 fpc-src_2.6.2-0_amd64.deb
 lazarus

---

### Post by Elfy on 2014-02-11
Thread closed. Please do not post duplicates, it dilutes community effort.

---

