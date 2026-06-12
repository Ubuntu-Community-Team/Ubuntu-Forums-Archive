---
title: "apt-get upgrade not finding upgradeable packages"
date: 2009-10-11
forum: Server Platforms
---

### Post by dthacker on 2009-10-11
Ubuntu Server Version 9.04

This morning I ran apt-get update and apt-get upgrade to get my server current.   When I log in now I see:

5 packages can be updated.
9 updates are security updates.

How can I find out what these packages are and get them upgraded?

TIA!  Dave :)

---

### Post by wojox on 2009-10-11
```
sudo apt-get -u upgrade
```

The -u option causes APT to show the complete list of packages which will be upgraded.

---

### Post by slakkie on 2009-10-11
You could also use aptitude -s safe-upgrade (or apt-get -s upgrade) to simulate the action so you can see what it wants to do.

---

### Post by dthacker on 2009-10-11
I decided to give these both a shot, here's the results of apt-get -u upgrade
5 packages can be updated.
9 updates are security updates.

Last login: Sun Oct 11 12:37:13 2009 from some server.

dthacker@mail3:~$ sudo apt-get -u upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  linux-image-server linux-restricted-modules-server linux-server
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

Got the same results with apt-get -s upgrade.   What's that pesky Landscape utility seeing?

TIA!  Dave






5 packages can be updated.
9 updates are security updates.

---

### Post by wojox on 2009-10-11
Weird, when I saw this I had to ssh into my server to see if I had anything, but didn't. When the last time before this happened you logged in.

Also what kernel are you running.

```
uname -r
```

I run jaunty-server 32 bit and fully updated with kernel 2.6.28-15-server. If you have a lower kernel number you may need to upgrade to the newer and reboot. Then you can upgrade the rest.

---

### Post by dthacker on 2009-10-11
Thanks for your help so far!

I had not been on the server for about a month before this morning.....

dthacker@mail3:~$ uname -r
2.6.28-13-server

dthacker@mail3:~$ sudo apt-get upgrade linux-server
[sudo] password for dthacker:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  linux-image-server linux-restricted-modules-server linux-server
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

How can I get the kernel upgraded with apt-get?

---

### Post by slakkie on 2009-10-11
Could you post your sources.list file?

grep "^deb " /etc/apt/sources.list

Should be enough.

---

### Post by wojox on 2009-10-11
Could also try:

```
sudo apt-get -u install linux-image-server linux-restricted-modules-server linux-server
```

---

### Post by lesswatts on 2009-10-12
Have you tried using the command:

```
sudo apt-get dist-upgrade
```

---

