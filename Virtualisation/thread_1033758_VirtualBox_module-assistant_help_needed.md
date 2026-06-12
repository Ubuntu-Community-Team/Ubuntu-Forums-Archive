---
title: "VirtualBox module-assistant help needed"
date: 2009-01-07
forum: Virtualisation
---

### Post by xoros on 2009-01-07
Trying to do this with virtualbox-ose: 
```
sudo apt-get install virtualbox-ose-source module-assistant
sudo module-assistant auto-install virtualbox-ose-source
sudo /etc/init.d/vboxdrv start
```

Gives this:

```
:/# module-assistant auto-install virtualbox-ose-source

Updated infos about 1 packages
Getting source for kernel version: 2.6.27-9-generic
Kernel headers available in /usr/src/linux-headers-2.6.27-9-generic
Creating symlink...
apt-get install build-essential 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  debootstrap kpartx python-cheetah
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Done!
unpack 
The source tarball could not be found!
Package virtualbox-ose-source not installed?
Running "m-a -f get virtualbox-ose-source" may help.
"/usr/share/modass/packages/default.sh" build KVERS=2.6.27-9-generic KSRC=/usr/src/linux KDREV=2.6.27-9.19 kdist_image
find: `/usr/src/modules/virtualbox*': No such file or directory
:/#
```

---

### Post by xoros on 2009-01-07
I see someone is having the same problem in this bug report (near the end of the thread)
[https://bugs.launchpad.net/ubuntu/intrepid/+source/virtualbox-ose-modules/+bug/303199](https://bugs.launchpad.net/ubuntu/intrepid/+source/virtualbox-ose-modules/+bug/303199)

However, there is no bug report filed yet for intrepid.

> Auto-install is expecting to find the virtualbox sources under /usr/src and doesn't, so fails. The file list reveals that the sources are not being placed where auto-install expects them:

[http://packages.ubuntu.com/intrepid/all/virtualbox-ose-source/filelist](http://packages.ubuntu.com/intrepid/all/virtualbox-ose-source/filelist)

---

### Post by craigmiller on 2009-01-27
Hello,

Has there been any progress with solving/getting-around this issue?


System Details:
```
Linux server2 2.6.27-7-server #1 SMP Fri Oct 24 07:20:47 UTC 2008 x86_64 GNU/Linux
```

I'm also trying to run this:

```
sudo apt-get install virtualbox-ose-source module-assistant
sudo module-assistant auto-install virtualbox-ose-source
sudo /etc/init.d/vboxdrv start
```

Output:

```
Updated infos about 1 packages
Getting source for kernel version: 2.6.27-7-server
Kernel headers available in /usr/src/linux
Creating symlink...
Couldn't create the /usr/src/linux symlink!
apt-get install build-essential
Reading package lists... Done
Building dependency tree
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 51 not upgraded.

Done!
unpack
The source tarball could not be found!
Package virtualbox-ose-source not installed?
Running "m-a -f get virtualbox-ose-source" may help.
"/usr/share/modass/packages/default.sh" build KVERS=2.6.27-7-server KSRC=/usr/src/linux-headers-2.6.27-7-server KDREV=2.6.27-7.16 kdist_image
find: `/usr/src/modules/virtualbox*': No such file or directory
```


Thanks!
Craig

---

### Post by sanemanmad on 2009-02-13
H, Same exact problem also.

AMD64 - 2.6.27-11-server

---

### Post by CheshireMac on 2009-03-06
Bump.
Same issue, 2.6.24-21-generic

---

