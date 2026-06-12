---
title: "Software Centre, constant errors when trying to install apps"
date: 2012-04-14
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by terrykiwi83 on 2012-04-14
Ever since attempting to install clamav from source I cannot install / remove any software via Software Centre. Constantly get the following error.

```

installArchives() failed: Selecting previously unselected package recordmydesktop. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 270045 files and directories currently installed.) 
Unpacking recordmydesktop (from .../recordmydesktop_0.3.8.1+svn602-1ubuntu3_amd64.deb) ... 
Selecting previously unselected package gtk-recordmydesktop. 
Unpacking gtk-recordmydesktop (from .../gtk-recordmydesktop_0.3.8-4.1ubuntu1_all.deb) ... 
Processing triggers for man-db ... 
Processing triggers for desktop-file-utils ... 
Processing triggers for bamfdaemon ... 
Rebuilding /usr/share/applications/bamf.index... 
Processing triggers for gnome-menus ... 
Setting up clamav-base (0.97.3+dfsg-2.1ubuntu1) ... 
adduser: The user `clamav' already exists. Exiting. 
dpkg: error processing clamav-base (--configure): 
 subprocess installed post-installation script returned error exit status 1 
dpkg: dependency problems prevent configuration of clamav-freshclam: 
 clamav-freshclam depends on clamav-base (>= 0.97.3+dfsg-2.1ubuntu1); however: 
  Package clamav-base is not configured yet. 
dpkg: error processing clamav-freshclam (--configure): 
 dependency problems - leaving unconfigured 
Setting up recordmydesktop (0.3.8.1+svn602-1ubuntu3) ... 
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
Setting up gtk-recordmydesktop (0.3.8-4.1ubuntu1) ... 
Errors were encountered while processing: 
 clamav-base 
 clamav-freshclam 
Setting up clamav-base (0.97.3+dfsg-2.1ubuntu1) ... 
adduser: The user `clamav' already exists. Exiting. 
dpkg: error processing clamav-base (--configure): 
 subprocess installed post-installation script returned error exit status 1 
dpkg: dependency problems prevent configuration of clamav-freshclam: 
 clamav-freshclam depends on clamav-base (>= 0.97.3+dfsg-2.1ubuntu1); however: 
  Package clamav-base is not configured yet. 
dpkg: error processing clamav-freshclam (--configure): 
 dependency problems - leaving unconfigured 
Errors were encountered while processing:

```

My mind is boggled?

---

### Post by theknightlinux on 2012-04-14
Open up a terminal by typing ctrl-alt-t simultaneously and type: sudo apt-get update
the type: sudo apt-get install.

---

### Post by bdarb on 2012-04-14
Have u tried to configure the package that says needs configuration (clamav-base)

```
sudo dpkg-reconfigure clamav-base
```

also try if that doesn't work

```
sudo apt-get install -f
```

---

### Post by cariboo on 2012-04-15
I'd suggest trying the second command bdarb gave you first.

---

### Post by terrykiwi83 on 2012-04-15
thanks for the replies, to fix I had to remove the packages involved. Using this command:

```

sudo apt-get remove clamav-base clamav-freshclam

```

I then **sudo apt-get update** and reinstalled clamav via software center.

All was fixed.

Thanks :)

---

