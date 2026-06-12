---
title: "trying to upgrade but terminal doesnt work"
date: 2018-09-13
forum: Ubuntu Development Version
---

### Post by idkwhatimdoing1.0 on 2018-09-13
hey guys I have ubuntu 18.10 and im trying to update it per usual however I have a problem when I use the GUI it says partial upgrade only so I click it and then it says its broken ancd to fix my /usr/bin/python symlink.... So I'm like welp ill just do it off the terminal so I right this ```
sudo apt update
Hit:1 http://security.ubuntu.com/ubuntu cosmic-security InRelease
Hit:2 http://ppa.launchpad.net/openjdk-r/ppa/ubuntu cosmic InRelease
Hit:3 http://ca.archive.ubuntu.com/ubuntu cosmic InRelease                     
Hit:4 http://ca.archive.ubuntu.com/ubuntu cosmic-updates InRelease             
Hit:5 http://ppa.launchpad.net/webupd8team/java/ubuntu cosmic InRelease  
Hit:6 http://ca.archive.ubuntu.com/ubuntu cosmic-backports InRelease     
Hit:7 http://ca.archive.ubuntu.com/ubuntu cosmic-proposed InRelease
Reading package lists... Done                     
Building dependency tree       
Reading state information... Done
2 packages can be upgraded. Run 'apt list --upgradable' to see them.

```
so i follow what it suggest and i right ```
apt list --upgradable
Listing... Done
octave/cosmic-proposed 4.4.1-1 amd64 [upgradable from: 4.4.1~rc2-3ubuntu1]
octave-common/cosmic-proposed,cosmic-proposed 4.4.1-1 all [upgradable from: 4.4.1~rc2-3ubuntu1]

```
so now I'm like cool I know I have two things that can be upgraded so i run ```
sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  octave octave-common
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
```
so yup it doesnt do it and I have no idea what the hell is happening... someone please help

---

### Post by howefield on 2018-09-13
Thread moved to the "*Ubuntu Development Version*" forum.

---

### Post by mc4man on 2018-09-13
Using proposed can cause issues, if you must then use apt-get, i.e,
```
sudo apt-get upgrade octave
```

---

### Post by idkwhatimdoing1.0 on 2018-09-14
that worked! Thanks

---

