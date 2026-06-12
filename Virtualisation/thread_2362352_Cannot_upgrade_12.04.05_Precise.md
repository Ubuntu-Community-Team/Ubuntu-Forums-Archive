---
title: "Cannot upgrade 12.04.05 Precise"
date: 2017-05-27
forum: Virtualisation
---

### Post by muhzilla on 2017-05-27
Hello,
I would like to upgrade to 14.04 as it is told me by the system after logging in:


> Welcome to Ubuntu 12.04.5 LTS (GNU/Linux 2.6.32-042stab120.20 x86_64)

 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)
New release '14.04.3 LTS' available.
Run 'do-release-upgrade' to upgrade to it.

> root@pflauni:~# uname -a
Linux pflauni 2.6.32-042stab120.20 #1 SMP Fri Mar 10 16:52:50 MSK 2017 x86_64 x86_64 x86_64 GNU/Linux

I did apt-get update/upgrade:

> root@pflauni:~# apt-get update
Hit [ftp://ftp.fu-berlin.de](ftp://ftp.fu-berlin.de) precise Release.gpg
Hit [ftp://ftp.fu-berlin.de](ftp://ftp.fu-berlin.de) precise Release
Hit [ftp://ftp.fu-berlin.de](ftp://ftp.fu-berlin.de) precise/main Sources
Hit [ftp://ftp.fu-berlin.de](ftp://ftp.fu-berlin.de) precise/main amd64 Packages
Hit [ftp://ftp.fu-berlin.de](ftp://ftp.fu-berlin.de) precise/main i386 Packages
Hit [ftp://ftp.fu-berlin.de](ftp://ftp.fu-berlin.de) precise/main TranslationIndex
Hit [ftp://ftp.fu-berlin.de](ftp://ftp.fu-berlin.de) precise/main Translation-en
Hit [ftp://ftp.fu-berlin.de](ftp://ftp.fu-berlin.de) precise/main Translation-de
Reading package lists... Done
root@pflauni:~# apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


The update-manager is installed, it is configured to update to LTS versions only. However, it continues to tell me "no new version found":
root@pflauni:~# do-release-upgrade
Checking for a new Ubuntu release
No new release found

Content of /etc/update-manager/release-upgrades:
> Prompt=lts


Content of /etc/apt/sources.list
> deb [ftp://ftp.fu-berlin.de/linux/ubuntu/](ftp://ftp.fu-berlin.de/linux/ubuntu/) precise main
deb-src [ftp://ftp.fu-berlin.de/linux/ubuntu/](ftp://ftp.fu-berlin.de/linux/ubuntu/) precise main

I had to switch to another mirror, as I couldn't update the package lists from the default ubuntu servers (stuck with "Waiting for headers").

I need to upgrade the servers Ubuntu, what can I do?

---

### Post by muhzilla on 2017-05-27
After using tcpdump to see what do-release-upgrade actually tries to do I found that it tries to access [http://changelogs.ubuntu.com/](http://changelogs.ubuntu.com/) to check for a new version.

Since I already had problems in the sources.list files with archive.ubuntu.com, I believe that my machine has the same problem when trying to access changelogs.ubuntu.com. What can I do? DNS resolving and pinging changelogs/archive.ubuntu.com works fine. Using archive.ubuntu.com in sources.list fails (100% [Waiting for headers]), do-release-upgrade still tells me "No new version found" :/

---

### Post by mörgæs on 2017-05-27
Hi, welcome to the fora.

It surprises me that you are recommended to upgrade to 14.04.3 when 14.04.5 is available. Also I see that you are using the root account which normally is [discouraged]("https://help.ubuntu.com/community/RootSudo"). 

Upgrades are by many users considered risky and often people prefer to do a clean install. Upgrades can be even more troublesome if the old operative system is out of support like 12.04.

If you manage to get to 14.04 you will have to upgrade again from this one some day, probably to 16.04. That might also cause a number of difficulties. 


A clean install of 16.04.2 would solve many problems in one go. Is that an option?

---

### Post by muhzilla on 2017-05-27
Hi there,
thanks for your reply. I managed to upgrade by fetching the file meta-release from changelogs.ubuntu.com manually, storing it on my own servers apache and letting /etc/update-manager/meta-release point to the new location. 

Dirty, but did the job. I upgraded to 16.04 immediately after the upgrade to 14.04. Some things with apache2 were messed up and I still am not able to use php7, but overall it's okay.

The only problem I have now is that the kernel version is still stuck at 2.6.x:

> Linux pflauni 2.6.32-042stab120.20 #1 SMP Fri Mar 10 16:52:50 MSK 2017 x86_64 x86_64 x86_64 GNU/Linux



Although I saw the 4.x kernel beeing unpacked and apt-get tells me it is installed 0o:
> root@pflauni:~# sudo apt-get install linux-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
linux-generic is already the newest version (4.4.0.78.84).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.



---

### Post by deadflowr on 2017-05-27
> The only problem I have now is that the kernel version is still stuck at 2.6.x:
Have you rebooted yet?

---

### Post by muhzilla on 2017-05-27
Sure :)

---

### Post by deadflowr on 2017-05-27
> **muhzilla said:**
> Sure :)

Not clear what that means, but if it means you did reboot, then next try updating grub:
```
sudo update-grub
```

---

### Post by muhzilla on 2017-05-27
> root@pflauni:~# sudo update-grub
/usr/sbin/grub-probe: error: failed to get canonical path of `/dev/ploop31913p1'.


My host seems to have an interesting sense of humor regarding server and device names ... :/

---

### Post by deadflowr on 2017-05-27
/dev/ploop? is this an openvz system, by chance?

---

### Post by muhzilla on 2017-05-27
I have not reliable information about that. It's a vserver, so it is virtualized for sure, but I don't know which software is used to manage the virtual machines. If it's of any help, the hoster is "linevast".

---

### Post by deadflowr on 2017-05-28
Moved to *Virtualization* then

---

