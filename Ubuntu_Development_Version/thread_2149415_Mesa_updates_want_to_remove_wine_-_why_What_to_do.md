---
title: "Mesa updates want to remove wine - why? What to do?"
date: 2013-05-28
forum: Ubuntu Development Version
---

### Post by deri on 2013-05-28
sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  libgl1-mesa-dri:i386 libgl1-mesa-glx:i386 libglapi-mesa:i386 libglu1-mesa:i386
  libosmesa6:i386 playonlinux wine wine1.5 wine1.5-amd64 wine1.5-i386:i386
  winetricks
The following packages will be upgraded:
  libegl1-mesa libegl1-mesa-dbg libegl1-mesa-dev libegl1-mesa-drivers
  libegl1-mesa-drivers-dbg libgl1-mesa-dev libgl1-mesa-dri libgl1-mesa-glx
  libgl1-mesa-glx-dbg libglapi-mesa libglapi-mesa-dbg libgles1-mesa
  libgles1-mesa-dbg libgles1-mesa-dev libgles2-mesa libgles2-mesa-dbg
  libgles2-mesa-dev libosmesa6 mesa-common-dev
19 upgraded, 0 newly installed, 11 to remove and 0 not upgraded.
Need to get 12,4 MB/12,4 MB of archives.
After this operation, 267 MB disk space will be freed.

---

### Post by Mark Phelps on 2013-05-28
This is what typically happens when you request an upgrade -- some packages get removed, some get updated, others get added.

It's not the mesa updates per se, it's doing a standard distro upgrade.

---

### Post by The musmula on 2013-05-28
What you should do is back up ur files and then remove the old ubuntu, and make a clean install of the new one, place ur files back in place, install all ur programs back, and done.

I know it is a lot of work but the upgrade takes about 2h, so... it is not that much work. but it gets done right

---

### Post by deri on 2013-05-28
I have kubuntu 13.10 saucy. I don't understand why mesa wants to remove my wine installations. I have some version of mesa already installed. If I answer yes to that question, does it remove my steam and my steam games too?

---

### Post by Mark Phelps on 2013-05-29
Version 13.10 is an early alpha -- and you should NOT be using that unless you are very experienced in Ubuntu, know how to make repairs on your own, and can handle daily crashes.  You would do better using a released version like 13.04 or 12.10.

---

### Post by howefield on 2013-05-29
Thread moved to the "*Ubuntu+1*" forum.

---

### Post by grahammechanical on 2013-05-29
Why do you want to run apt-get dist-upgrade? What is wrong with using apt-get update followed by apt-get upgrade. You may find that wine is not going to be removed if you do it that way.

Wine is using libraries that are going to be removed and so wine will also be removed so that you do not have a broken application. Read this wiki page

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

Notice item 3 under Maintenance Commands. You have chosen a command that 
> 
add the "smart upgrade" checkbox. It tells APT to use "smart" conflict  resolution system, and it will attempt to upgrade the most important  packages at the expense of less important ones if necessary.

Apt is only doing what you have told it to do. Oh, and by the way as you are using Saucy, if you are ever asked to run a Partial Upgrade - don't do it. You most likely will end up with a broken OS.

Regards.

---

### Post by VinDSL on 2013-05-29
> **Mark Phelps said:**
> It's not the mesa updates per se, it's doing a**[COLOR="#B22222"] standard distro upgrade[/COLOR]**.
Exactly!

This is a subtle point (sudo apt-get upgrade vs sudo apt-get dist-upgrade) but there are major differences in the way upgrades are performed.

In Synaptic, these are referred to as "**Default** Upgrade" (sudo apt-get upgrade) and "**Smart** Upgrade" (sudo apt-get dist-upgrade).  That pretty much says it all...  ;)

Example:  I *had* to upgrade libpango the other day. Using the dist-upgrade/smart upgrade method, it wanted to remove 10s or 100s of packages.  If I had said "Yes", it would have removed half of my OS.  But, by _selectively_ using a combination of dist-upgrade/smart upgrade and standard/default upgrade, on individual packages, I was finally able to upgrade libpango without doing a fresh install.

Actually, doing tricks like this, I haven't had to perform a fresh install since 2011...  :D

```
vindsl@Zuul:~$ ls -ld /var/log/installer | awk '{ print $6 " " $7 " " $8 }'
**[COLOR="#0000CD"]Oct 13 2011[/COLOR]**
```

BTW, as a side-note, I *think* Synaptic defaults to dist-upgrade/smart upgrade when you install it, which can get you into a lot of trouble.

The first thing I do, when I install Synaptic, is change the preferences, so Synaptic "Asks" me (every time) which upgrade method I want to use.

[INDENT][ATTACH=CONFIG]243225[/ATTACH][/INDENT]

---

