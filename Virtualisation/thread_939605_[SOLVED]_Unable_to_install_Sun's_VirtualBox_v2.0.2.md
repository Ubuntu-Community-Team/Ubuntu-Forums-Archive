---
title: "[SOLVED] Unable to install Sun's VirtualBox v2.0.2 on Gutsy Gibbon"
date: 2008-10-06
forum: Virtualisation
---

### Post by terrorsathan on 2008-10-06
-

---

### Post by MystaMax on 2008-10-06
you can run the following command from the terminal:

```
sudo aptitude install libqt4-core
```

I'm not sure this package is in the gutsy repositories.

---

### Post by Jose Catre-Vandis on 2008-10-06
You wil probably need all of these too:
```
sudo apt-get install libqt4-assistant libqt4-core libqt4-dbus libqt4-designer libqt4-gui libqt4-network libqt4-opengl libqt4-script libqt4-svg libqt4-test libqt4-xml libqtcore4 libqtgui4
```
(discovered when seeking to install VBox2 on a command line system with Openbox as a window manager (Hardy))

---

### Post by terrorsathan on 2008-10-06
-

---

### Post by Quarg on 2008-10-06
can't you just use the repos?

---

### Post by terrorsathan on 2008-10-08
-

---

### Post by Jose Catre-Vandis on 2008-10-08
Try running this at a terminal
```
sudo apt-get install -f
```

This command should pick up the broken packages on which virtualbox is dependent, install them and complete the vbox install.

remember to add your use to the vboxusers group

---

### Post by terrorsathan on 2008-10-11
-

---

### Post by Jose Catre-Vandis on 2008-10-13
Suggest you recheck your installation of libqt4-core and all other dependencies, and then retry to install Vbox.

Alternatively, uninstall libqt4-core and then try VBox. libqt4-core should be in the repos, as I have it on my Fiesty machine here (version 4.3.0.4 from fiesty-backports) :)

---

### Post by Jose Catre-Vandis on 2008-10-13
Suggest you recheck your installation of libqt4-core and all other dependencies, and then retry to install Vbox.

Alternatively, uninstall libqt4-core and then try VBox. libqt4-core should be in the repos, as I have it on my Fiesty machine here (version 4.3.0.4 from fiesty-backports) :)

---

### Post by terrorsathan on 2008-10-13
-

---

### Post by Jose Catre-Vandis on 2008-10-15
> **terrorsathan said:**
> The package seems to be installed normal:
```
$ dpkg -l libqt4-core
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                           Version                        Description
+++-==============================-==============================-============================================================================
ii  libqt4-core                    4.3.2-0ubuntu3.2               Qt 4 core non-GUI functionality runtime library

```


This sounds like a good idea to me, but it looks like I will have to remove some other packages upon running aptitude remove libqt4-core:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
**The following packages are BROKEN:**
  keepassx libqt4-gui libqt4-qt3support libqt4-sql qt4-qtconfig skype virtualbox-2.0 
The following packages will be REMOVED:
  libqt4-core 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 5399kB will be freed.
The following packages have unmet dependencies:
  libqt4-qt3support: Depends: libqt4-core (>= 4.3.2) but it is not installable
  virtualbox-2.0: Depends: libqt4-core (>= 4.3.2) but it is not installable
  skype: Depends: libqt4-core (>= 4.2.1) but it is not installable
  libqt4-gui: Depends: libqt4-core (>= 4.3.2) but it is not installable
  keepassx: Depends: libqt4-core (>= 4.2.2) but it is not installable
  libqt4-sql: Depends: libqt4-core (>= 4.3.2) but it is not installable
  qt4-qtconfig: Depends: libqt4-core (>= 4.3.2) but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
keepassx
libqt4-gui
libqt4-qt3support
libqt4-sql
qt4-qtconfig
skype
virtualbox-2.0

Score is -905

Accept this solution? [Y/n/q/?]
```
Looks like those packages are broken ... that's weird. I suppose I will have to reinstall them, maybe that will fix the problem.

EDIT:
Damn it! I just discovered the problem and it's all my fault :/ ... I downloaded the deb-package for Hardy and not for Gutsy (yes I'm still using it as I mentioned in my first post) ... that's why it didn't work, damn am I stupid. Sorry about that ...
Anyway, thanks for your time and help :)

Best regards,
terrorsathan

I was going to suggest checking your deb for virtualbox but i re-read your thread and you had the gutsy deb listed so didn't mention it :)

Glad you got it all sorted :)

---

