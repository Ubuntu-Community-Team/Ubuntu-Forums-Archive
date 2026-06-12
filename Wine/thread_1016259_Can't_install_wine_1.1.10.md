---
title: "Can't install wine 1.1.10"
date: 2008-12-19
forum: Wine
---

### Post by warzt on 2008-12-19
How to install newest version wine 1.1.10, I did try:
sudo apt-get install wine
And then i have wine 1.01, not 1.1.10 :(

---

### Post by ajgreeny on 2008-12-19
Go to the [wine]("http://www.winehq.org/") hq and there it tells you how to enable their own repos.  That way you will always have the most up-to-date version.

---

### Post by warzt on 2008-12-19
**       I did download wine-1.1.10.tar.bz2. Then i try to install it**
gary@gary-laptop:~$ ls /tmp
atievntX.0jL0az
FR Starcraft+Broodwar v1.15.2 (No-CD No-INSTALL Ready-to-LAN).torrent
keyring-CiQJPO
orbit-gary
orbit-root
plugtmp
pulse-gary
seahorse-hq5n9T
totem.gary.3865459798
Tracker-gary.7386
virtual-gary.L0T7kl
_wine-1.1.10.tar.bz2_
gary@gary-laptop:~$ _tar xjvf wine-1.1.10.tar.bz2_
tar: wine-1.1.10.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
 
**DAMN, i don't see where is my mistake. I can't install tar.bz2 file by "tar xjvf " command**

---

### Post by binbash on 2008-12-19
> **warzt said:**
> **       I did download wine-1.1.10.tar.bz2. Then i try to install it**
gary@gary-laptop:~$ ls /tmp
atievntX.0jL0az
FR Starcraft+Broodwar v1.15.2 (No-CD No-INSTALL Ready-to-LAN).torrent
keyring-CiQJPO
orbit-gary
orbit-root
plugtmp
pulse-gary
seahorse-hq5n9T
totem.gary.3865459798
Tracker-gary.7386
virtual-gary.L0T7kl
_wine-1.1.10.tar.bz2_
gary@gary-laptop:~$ _tar xjvf wine-1.1.10.tar.bz2_
tar: wine-1.1.10.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
 
**DAMN, i don't see where is my mistake. I can't install tar.bz2 file by "tar xjvf " command**


No dude add this repository : 

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by albinootje on 2008-12-19
> **warzt said:**
> **       I did download wine-1.1.10.tar.bz2. Then i try to install it**
gary@gary-laptop:~$ ls /tmp
atievntX.0jL0az
FR Starcraft+Broodwar v1.15.2 (No-CD No-INSTALL Ready-to-LAN).torrent
keyring-CiQJPO
orbit-gary
orbit-root
plugtmp
pulse-gary
seahorse-hq5n9T
totem.gary.3865459798
Tracker-gary.7386
virtual-gary.L0T7kl
_wine-1.1.10.tar.bz2_
gary@gary-laptop:~$ _tar xjvf wine-1.1.10.tar.bz2_
tar: wine-1.1.10.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

In that cause you either would have done :
1) cd /tmp ; tar xjvf wine-1.1.10.tar.bz2
OR : 2) tar xjvf /tmp/wine-1.1.10.tar.bz2

in case 1) it would have ended up in /tmp
in case 2) it would be in your home directory

But it's recommended to install the deb packages.
The winehq has the instructions.
Compiling Wine from source is a looooooong process, and probably not needed here.

Even easier is to install PlayOnLinux, which will install different wine-version for you.
[http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)

---

### Post by warzt on 2008-12-19
**To binbash**: before u tell me I did try it and I found this
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/intrepid.list](http://wine.budgetdedicated.com/apt/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/winehq.list
   So I type it in terminal
gary@gary-laptop:~$ sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/intrepid.list](http://wine.budgetdedicated.com/apt/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/winehq.list
--2008-12-19 23:20:36--  [http://wine.budgetdedicated.com/apt/sources.list.d/intrepid.list](http://wine.budgetdedicated.com/apt/sources.list.d/intrepid.list)
Resolving wine.budgetdedicated.com... 81.171.111.184
Connecting to wine.budgetdedicated.com|81.171.111.184|:80... 
   And it looks like that for 5 minutes, I think i can't connect with [http://wine.budgetdedicated.com/apt/sources.list.d/intrepid.list](http://wine.budgetdedicated.com/apt/sources.list.d/intrepid.list). I try go that website in by firefox, and i can't access that website.
 
  **To albinootje**: I try case 1, and it extract all files in wine-1.1.10.tar.bz2, I though that command will install it. But i am looking for install tar.bz2 file command
I tried Playonlinux, and it said I must install wine, that means i must install wine 1.01, but my porpose is install wine 1.1.10 :(

---

### Post by cogadh on 2008-12-19
The WineHQ repository is currently down (happens once in a great while). I'm sure it will be back up soon. Just be patient and you can install the appropriate .deb package.

The .tar ball you downloaded is the Wine source code, which requires you to compile it before it can be installed and used. If you want to try doing that, you first need to install the build-essential package and all of the wine build dependencies:
```
sudo apt-get install build-essential
apt-get build-dep wine
```
However, I recommend just waiting for the WineHQ repository to come back up, its much easier and way more reliable to use the .deb package.

---

### Post by albinootje on 2008-12-19
> **warzt said:**
> 
I tried Playonlinux, and it said I must install wine, that means i must install wine 1.01, but my porpose is install wine 1.1.10 :(

If you install the Ubuntu of PlayOnLinux it will install Wine for you from the Ubuntu repositories. 

But the moment you start using PlayOnLinux you can switch between various wine-version *per* "bottle" and PlayOnLinux will install it for you.
See : -> Tools -> Manage Wine Versions

---

### Post by hikaricore on 2008-12-19
> **warzt said:**
> 
gary@gary-laptop:~$ ls /tmp
atievntX.0jL0az
**FR Starcraft+Broodwar v1.15.2 (No-CD No-INSTALL Ready-to-LAN).torrent**
keyring-CiQJPO
orbit-gary
orbit-root
plugtmp
pulse-gary
seahorse-hq5n9T
totem.gary.3865459798
Tracker-gary.7386
virtual-gary.L0T7kl


You gotta love when someone accidentally shows us their recent adventures into software piracy.  :lolflag:

---

### Post by OrbJinzo on 2008-12-19
zomg piracy!!!!1 someone phone teh hax police!

---

