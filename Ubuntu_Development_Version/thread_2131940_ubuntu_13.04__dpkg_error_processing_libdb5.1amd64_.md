---
title: "ubuntu 13.04  dpkg: error processing libdb5.1:amd64 (--configure):"
date: 2013-04-03
forum: Ubuntu Development Version
---

### Post by Crossle Song on 2013-04-03
uname -a 
Linux klpu 3.8.0-15-generic #25-Ubuntu SMP Wed Mar 27 19:19:30 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

```

le at klpu in ~ 
$ sudo apt-get upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  accountsservice aptdaemon aptdaemon-data esound-common libaccountsservice0 libbonobo2-0 libbonobo2-common libcogl-common
  libcogl-pango12 libcogl12 libdb5.1++ libesd0:i386 libgeis1 libgksu2-0 libgnome2-0 libgnome2-bin libgnome2-common
  libgnomevfs2-0 libgnomevfs2-common libimobiledevice3 liblightdm-gobject-1-0 liborbit2 libpurple-bin libpurple0 lightdm
  obexd-client parcellite pidgin pidgin-data python-aptdaemon python-aptdaemon.gtk3widgets python-dbus python-dbus-dev
  python3-aptdaemon python3-aptdaemon.gtk3widgets python3-aptdaemon.pkcompat python3-dbus ubuntu-desktop ubuntu-minimal
  ubuntu-standard vim vim-common vim-gnome vim-gui-common vim-runtime vim-tiny
46 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/13.8 MB of archives.
After this operation, 30.7 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: error processing libdb5.1:amd64 (--configure):
 package libdb5.1:amd64 is not ready for configuration
 cannot configure (current status `half-installed')
Errors were encountered while processing:
 libdb5.1:amd64
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


Preconfiguring packages ...
dpkg: error processing libdb5.1:amd64 (--configure):
 package libdb5.1:amd64 is not ready for configuration
 cannot configure (current status `half-installed')
Errors were encountered while processing:
 libdb5.1:amd64
E: Sub-process /usr/bin/dpkg returned an error code (1)

help?

---

### Post by wojox on 2013-04-03
Try the following```
sudo apt-get install -f
sudo dpkg --configure -a
sudo apt-get --fix-broken install
sudo apt-get --fix-missing install

```

---

### Post by Crossle Song on 2013-04-03
$ sudo apt-get --fix-missing install               
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 46 not upgraded.
1 not fully installed or removed.
Need to get 0 B/705 kB of archives.
After this operation, 0 B of additional disk space will be used.
dpkg: error processing libdb5.1:amd64 (--configure):
 package libdb5.1:amd64 is not ready for configuration
 cannot configure (current status `half-installed')
Errors were encountered while processing:
 libdb5.1:amd64
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by wojox on 2013-04-03
```
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get --fix-missing install
```

---

### Post by Crossle Song on 2013-04-03
dpkg: error processing libdb5.1:amd64 (--configure):
 package libdb5.1:amd64 is not ready for configuration
 cannot configure (current status `half-installed')
Errors were encountered while processing:
 libdb5.1:amd64
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Crossle Song on 2013-04-03
Use 

$ sudo apt-get install --reinstall libdb5.1:amd64

OK .thanks!!!

---

### Post by wojox on 2013-04-03
```
sudo apt-get build-dep libdb5.1
sudo apt-get install
```

---

### Post by wojox on 2013-04-03
> **Crossle Song said:**
> Use 

$ sudo apt-get install --reinstall libdb5.1:amd64

OK .thanks!!!

Great :)

---

