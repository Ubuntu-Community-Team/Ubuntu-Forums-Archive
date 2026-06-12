---
title: "Cannot get lock for updates"
date: 2019-09-09
forum: Ubuntu/Debian BASED
---

### Post by ray42 on 2019-09-09
Updates do not work via software centre or terminal

Have tried the following:

```

sudo apt update && sudo apt upgrade -y




sudo apt clean
sudo apt update -m
sudo dpkg --configure -a
sudo apt install -f
sudo apt dist-upgrade
sudo apt autoremove --purge

```

---

### Post by deadflowr on 2019-09-09
Post the output you get when running
```
sudo apt full-upgrade
```

---

### Post by #&amp;thj^% on 2019-09-09
Try and post back:
```
sudo killall apt apt-get
```
Niinja'd by deadflowr ;)

---

### Post by ray42 on 2019-09-09
```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed
  linux-headers-4.15.0-62 linux-headers-4.15.0-62-generic
  linux-image-4.15.0-62-generic linux-modules-4.15.0-62-generic
  linux-modules-extra-4.15.0-62-generic
The following packages will be upgraded:
  appstream-data-pop appstream-data-pop-icons firmware-manager-notify
  firmware-manager-shared libfirmware-manager libpython2.7
  libpython2.7-minimal libpython2.7-stdlib libpython3.6 libpython3.6-minimal
  libpython3.6-stdlib linux-generic linux-headers-generic linux-image-generic
  pop-shop python2.7 python2.7-minimal python3.6 python3.6-minimal
The following packages will be DOWNGRADED:
  geary
19 to upgrade, 5 to newly install, 1 to downgrade, 0 to remove and 0 not to upgrade.
Need to get 82.4 MB of archives.
After this operation, 331 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
```

NOTE:
It does go through the update process of 331mb and looks successful, but I can run the same command and get the same output at a later time.

---

### Post by ray42 on 2019-09-09
```
sudo killall apt apt-get
apt: no process found
apt-get: no process found

```

---

### Post by deadflowr on 2019-09-09
Looks fine with the exception of downgrading geary.
Not sure what's happening with that.
What does 
```
apt policy geary
```
show?

---

### Post by ray42 on 2019-09-09
> **deadflowr said:**
> Looks fine with the exception of downgrading geary.
Not sure what's happening with that.
What does 
```
apt policy geary
```
show?

```

apt policy gearygeary:
  Installed: 0.13.3-1~bionic1
  Candidate: 0.13.3-1~bionic1
  Version table:
 *** 0.13.3-1~bionic1 500
        500 http://ppa.launchpad.net/geary-team/releases/ubuntu bionic/main amd64 Packages
        100 /var/lib/dpkg/status
     0.13.3-1~bionic1 1001
       1001 http://ppa.launchpad.net/system76/pop/ubuntu bionic/main amd64 Packages

```

---

### Post by deadflowr on 2019-09-09
Interesting.
Seems the system76 ppa has a higher priority (1001) over the geary-team ppa (500)
So it wants to replace the package with that from system76.
Looks like they shows as the same package version.

(looking at the ppa home pages they were even uploaded by the same maintainer for both, one week apart from each other)

If you run the apt full-upgrade command again and select Y what happens?
Does it still fail to get a lock?

---

### Post by ray42 on 2019-09-09
> **deadflowr said:**
> Interesting.
Seems the system76 ppa has a higher priority (1001) over the geary-team ppa (500)
So it wants to replace the package with that from system76.
Looks like they shows as the same package version.

(looking at the ppa home pages they were even uploaded by the same maintainer for both, one week apart from each other)

If you run the apt full-upgrade command again and select Y what happens?
Does it still fail to get a lock?

[COLOR=#000000]NOTE:[/COLOR]
[COLOR=#000000]It does go through the update process of 331mb and looks successful, but I can run the same command and get the same output at a later time.[/COLOR]

---

### Post by deadflowr on 2019-09-09
Next time it happens perhaps check top and see if apt or dpkg or even unattended-upgrades is running.
If anyone of those is running then it can cause it to lock.

---

### Post by ray42 on 2019-09-09
When I run this

```
sudo apt update && sudo apt upgrade -y

```

I get this:

```
sudo apt update && sudo apt upgrade -y
Hit:1 http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu bionic InRelease
Hit:2 http://archive.ubuntu.com/ubuntu bionic InRelease                        
Ign:3 http://dl.google.com/linux/chrome/deb stable InRelease                   
Get:4 http://linux.teamviewer.com/deb stable InRelease [9,388 B]               
Hit:5 http://ppa.launchpad.net/geary-team/releases/ubuntu bionic InRelease     
Hit:6 http://dl.google.com/linux/chrome/deb stable Release                     
Hit:7 http://archive.ubuntu.com/ubuntu bionic-updates InRelease                
Hit:8 https://repo.skype.com/deb stable InRelease                              
Hit:9 https://deb.opera.com/opera-stable stable InRelease                      
Hit:10 http://ppa.launchpad.net/linrunner/tlp/ubuntu bionic InRelease          
Hit:11 http://archive.ubuntu.com/ubuntu bionic-security InRelease              
Hit:12 http://ppa.launchpad.net/mkusb/ppa/ubuntu bionic InRelease              
Hit:13 http://archive.ubuntu.com/ubuntu bionic-backports InRelease             
Hit:14 http://apt.pop-os.org/proprietary bionic InRelease                      
Hit:15 http://ppa.launchpad.net/rednotebook/stable/ubuntu bionic InRelease     
Hit:16 http://ppa.launchpad.net/system76/pop/ubuntu bionic InRelease           
Hit:17 http://ppa.launchpad.net/teejee2008/ppa/ubuntu bionic InRelease         
Hit:18 http://ppa.launchpad.net/umang/indicator-stickynotes/ubuntu bionic InRelease
Hit:20 https://packagecloud.io/slacktechnologies/slack/debian jessie InRelease 
Fetched 9,388 B in 3s (3,030 B/s)                   
Reading package lists... Done
Building dependency tree       
Reading state information... Done
19 packages can be upgraded. Run 'apt list --upgradable' to see them.
W: Skipping acquire of configured file 'multiverse/source/Sources' as repository 'http://archive.ubuntu.com/ubuntu bionic InRelease' doesn't have the component 'multiverse' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'universe/source/Sources' as repository 'http://archive.ubuntu.com/ubuntu bionic InRelease' doesn't have the component 'universe' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'restricted/source/Sources' as repository 'http://archive.ubuntu.com/ubuntu bionic InRelease' doesn't have the component 'restricted' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'restricted/binary-amd64/Packages' as repository 'http://archive.ubuntu.com/ubuntu bionic InRelease' doesn't have the component 'restricted' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'restricted/binary-i386/Packages' as repository 'http://archive.ubuntu.com/ubuntu bionic InRelease' doesn't have the component 'restricted' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'restricted/dep11/Components-amd64.yml' as repository 'http://archive.ubuntu.com/ubuntu bionic InRelease' doesn't have the component 'restricted' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'restricted/dep11/icons-48x48.tar' as repository 'http://archive.ubuntu.com/ubuntu bionic InRelease' doesn't have the component 'restricted' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'restricted/dep11/icons-64x64.tar' as repository 'http://archive.ubuntu.com/ubuntu bionic InRelease' doesn't have the component 'restricted' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'restricted/dep11/icons-64x64@2.tar' as repository 'http://archive.ubuntu.com/ubuntu bionic InRelease' doesn't have the component 'restricted' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'restricted/dep11/icons-128x128.tar' as repository 'http://archive.ubuntu.com/ubuntu bionic InRelease' doesn't have the component 'restricted' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'restricted/cnf/Commands-amd64' as repository 'http://archive.ubuntu.com/ubuntu bionic InRelease' doesn't have the component 'restricted' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'universe/binary-amd64/Packages' as repository 'http://archive.ubuntu.com/ubuntu bionic InRelease' doesn't have the component 'universe' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'universe/binary-i386/Packages' as repository 'http://archive.ubuntu.com/ubuntu bionic InRelease' doesn't have the component 'universe' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'universe/dep11/Components-amd64.yml' as repository 'http://archive.ubuntu.com/ubuntu bionic InRelease' doesn't have the component 'universe' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'universe/dep11/icons-48x48.tar' as repository 'http://archive.ubuntu.com/ubuntu bionic InRelease' doesn't have the component 'universe' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'universe/dep11/icons-64x64.tar' as repository 'http://archive.ubuntu.com/ubuntu bionic InRelease' doesn't have the component 'universe' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'universe/dep11/icons-64x64@2.tar' as repository 'http://archive.ubuntu.com/ubuntu bionic InRelease' doesn't have the component 'universe' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'universe/dep11/icons-128x128.tar' as repository 'http://archive.ubuntu.com/ubuntu bionic InRelease' doesn't have the component 'universe' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'universe/cnf/Commands-amd64' as repository 'http://archive.ubuntu.com/ubuntu bionic InRelease' doesn't have the component 'universe' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'multiverse/binary-i386/Packages' as repository 'http://archive.ubuntu.com/ubuntu bionic InRelease' doesn't have the component 'multiverse' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'multiverse/binary-amd64/Packages' as repository 'http://archive.ubuntu.com/ubuntu bionic InRelease' doesn't have the component 'multiverse' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'multiverse/dep11/Components-amd64.yml' as repository 'http://archive.ubuntu.com/ubuntu bionic InRelease' doesn't have the component 'multiverse' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'multiverse/dep11/icons-48x48.tar' as repository 'http://archive.ubuntu.com/ubuntu bionic InRelease' doesn't have the component 'multiverse' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'multiverse/dep11/icons-64x64.tar' as repository 'http://archive.ubuntu.com/ubuntu bionic InRelease' doesn't have the component 'multiverse' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'multiverse/dep11/icons-64x64@2.tar' as repository 'http://archive.ubuntu.com/ubuntu bionic InRelease' doesn't have the component 'multiverse' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'multiverse/dep11/icons-128x128.tar' as repository 'http://archive.ubuntu.com/ubuntu bionic InRelease' doesn't have the component 'multiverse' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'multiverse/cnf/Commands-amd64' as repository 'http://archive.ubuntu.com/ubuntu bionic InRelease' doesn't have the component 'multiverse' (component misspelt in sources.list?)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed
  linux-headers-4.15.0-62 linux-headers-4.15.0-62-generic
  linux-image-4.15.0-62-generic linux-modules-4.15.0-62-generic
  linux-modules-extra-4.15.0-62-generic
The following packages will be upgraded:
  appstream-data-pop appstream-data-pop-icons firmware-manager-notify
  firmware-manager-shared libfirmware-manager libpython2.7
  libpython2.7-minimal libpython2.7-stdlib libpython3.6 libpython3.6-minimal
  libpython3.6-stdlib linux-generic linux-headers-generic linux-image-generic
  pop-shop python2.7 python2.7-minimal python3.6 python3.6-minimal
The following packages will be DOWNGRADED:
  geary
19 to upgrade, 5 to newly install, 1 to downgrade, 0 to remove and 0 not to upgrade.
E: Packages were downgraded and -y was used without --allow-downgrades.



```

---

### Post by ray42 on 2019-09-09
> **deadflowr said:**
> Next time it happens perhaps check top and see if apt or dpkg or even unattended-upgrades is running.
If anyone of those is running then it can cause it to lock.

Check top?

---

### Post by #&amp;thj^% on 2019-09-09
```
E: Packages were downgraded and -y was used without --allow-downgrades
```
Maybe remove and purge, then let the package manger install it.
Example:
```
sudo apt remove --purge geary
```
Now run your update  upgrade command again.
Either way the maintainer should be made aware of this.

---

