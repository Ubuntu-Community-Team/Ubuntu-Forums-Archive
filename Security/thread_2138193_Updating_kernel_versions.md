---
title: "Updating kernel versions"
date: 2013-04-23
forum: Security
---

### Post by jsvidyad on 2013-04-23
Hello,

 I use ubuntu/kubuntu 10.04. To update the packages on my ubuntu/kubuntu 10.04, I have been using the following commands in the given order:
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get dselect-upgrade

I was under the impression that the above commands would install all security upgrades for my ubuntu/kubuntu 10.04 systems. When I ran the above commands, occasionally there would also be kernel upgrades available which I would install to my system. So I was under the impression that security upgrades for the kernel were also being applied to my system and everything was okay regarding security updates. But, recently I ran the command 'apt-cache search linux-image --names-only' and found kernel versions available which were newer than the one on my system. The command 'uname -r' run on my system gives the output '2.6.32-46-generic'. But kernel versions of upto '3.0.0-32' seem to be available in the repositories. So, when I update my system, why don't I get the latest kernel version available in the repositories? Am I missing something on the security updates front?

---

### Post by ibjsb4 on 2013-04-23
I do not run 10o4 anymore, but my guess is that kernel upgrade is optional.  12o4 offers something similar.  Kernel 3.2 upgrades are standard, but I have a option to go to the 3.5 kernel.  If you want to do the 3.0 upgrade just use synaptic package manager.

---

### Post by Frogs Hair on 2013-04-23
The kernels are modified/patched to run with a specific Ubuntu version . There is a kernel freeze during development and only improvements are added to that kernel version during the life of the release in normal updates. It is possible to manually upgrade the kernel but I don't know if the kernel drivers/ firmware are updated automatically. The Ubuntu meta packages determine what is updated and 10.04 loses support on May 9th so the repositories will be disabled. It may be time to think about an upgrade because upgrading the kernel will not ensure continued security updates for 10.04.  

[https://help.ubuntu.com/community/MetaPackages](https://help.ubuntu.com/community/MetaPackages)

---

### Post by jsvidyad on 2013-04-26
Okay,

  But the three commands I gave in my first post when executed in that order should apply all available security updates to my ubuntu/kubuntu system, right?

---

### Post by ibjsb4 on 2013-04-26
The first two commands I think is all you need.

---

### Post by Frogs Hair on 2013-04-26
[COLOR=#000000]> But the three commands I gave in my first post when executed in that order should apply all available security updates to my ubuntu/kubuntu system, right?

Yes , but only until May 9th if running 10.04. The repository for 10.04 closes on that day. See the link for release support dates. [/COLOR][https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by cariboo on 2013-04-26
> **Frogs Hair said:**
> [COLOR=#000000]

Yes , but only until May 9th if running 10.04. The repository for 10.04 closes on that day. See the link for release support dates. [/COLOR][https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

The 10.04 server version is supported until 2015, but you won't get any desktop bug fixes, only security updates.

---

