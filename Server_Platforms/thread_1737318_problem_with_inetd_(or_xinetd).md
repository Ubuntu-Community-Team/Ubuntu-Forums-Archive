---
title: "problem with inetd (or xinetd)"
date: 2011-04-23
forum: Server Platforms
---

### Post by mahmoodn on 2011-04-23
Hi,
I am trying to configure a diskless cluster with ubuntu server from [https://wiki.edubuntu.org/EasyUbuntuClustering/UbuntuKerrighedClusterGuide](https://wiki.edubuntu.org/EasyUbuntuClustering/UbuntuKerrighedClusterGuide)

However some instructions are vague. For example, in section "1.2: Setting up the TFTP server and PXE bootloader", it is stated:
> Open its configuration file, /etc/inetd.conf, and change the tftp line to the following. If there is no tftp line, add this

There is no "inetd.conf" file in my system. Also there is no package named inetd. I have t say I install xinetd

```
mahmood@server:~$ sudo apt-get install xinetd 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xinetd is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 101 not upgraded.

mahmood@server:~$ sudo apt-get install inetd 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package inetd

mahmood@server:~$ ls /etc/inetd.conf
ls: cannot access /etc/inetd.conf: No such file or directory
```

So what should I do?

---

### Post by falko on 2011-04-23
> **mahmoodn said:**
> Also there is no package named inetd.
On Ubuntu, it is named openbsd-inetd.

---

### Post by mahmoodn on 2011-04-23
Should I remove xinetd?

---

