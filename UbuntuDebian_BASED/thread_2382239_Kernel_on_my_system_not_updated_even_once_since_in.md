---
title: "Kernel on my system not updated even once since installation? If so, how to resolve?"
date: 2018-01-10
forum: Ubuntu/Debian BASED
---

### Post by teropesonen on 2018-01-10
Hello everyone,


I was checking if my 16.04 desktop installation is already updated to the meltdown-patched kernel, and found something quite peculiar that I do not understand.


According to uname -a, I have:


Linux Tuxedo-1 4.7.4-040704-generic #201609150330 SMP Thu Sep 15 07:32:22 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


That is, I am supposedly running a kernel version from 2016! This makes no sense, since I have the latest linux-generic  also installed (4.4.0.109.114). Moreover, I have not installed any kernel updates myself, but have only used the software updater and let it handle all system-level updates. On the other hande, I did not install the system originally myself, but rather got the machine pre-configured from a German Linux PC vendor called Tuxedo.


If it is true that I am running a 2016 kernel, how can I resolve the issue safely? The major version implied by uname (4.7.4) is certainly higher than the 4.4 series of which the patched kernel is. At the same time, I want to update to a secure kernel version, but do not want to wreck this system, since it is my primary work machine. How would you suggest I proceed?


Thanks,
Tero Pesonen

---

### Post by Frogs Hair on 2018-01-10
Hello and Welcome

> [COLOR=#000000]Linux Tuxedo-1 4.7.4-040704[/COLOR] I never seen Linux Tuxedo in an output for uname -a , do you have a kernel PPA of some sort installed ?

Post the output of the following.
```
apt-cache policy linux-generic
```

---

### Post by QIII on 2018-01-10
Moved to Ubuntu/Debian BASED

Linux Tuxedo is an Xubuntu-based spin installed on Tuxedo laptops.  A German company, I believe.

---

### Post by teropesonen on 2018-01-11
Hi,

the output is:

  Installed: 4.4.0.109.114
  Candidate: 4.4.0.109.114
  Version table:
 *** 4.4.0.109.114 500
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 Packages
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     4.4.0.21.22 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main amd64 Packages

--end of output--

Tuxedo provides ready-installed Linux PCs. Mine is their Xubuntu-configured hardware.

---

### Post by teropesonen on 2018-01-11
I just found out I also have 

linux-image-4.7.4-040704-generic

installed as well, according to Synaptic.

---

### Post by deadflowr on 2018-01-11
Your uname -a version is simply too new and of a higher value than the linux-generic package version.
You see the same issue of people who run the Ubuntu mainline kernel builds and have the linux-generic package installed.
The kernel with the higher number take precedent. So 4.7 beats 4.4 every time.

Easy fix would actually be to instead of doing anything about the linx-generic package and it's 4.4 kernels, instead just install the 
linux-generic-hwe-16.04 package (and corresponding graphics driver: xserver-xorg-hwe-16.04)
Running
```
sudo apt install linux-generic-hwe-16.04 xserver-xorg-hwe-16.04
```
will install the packages and put the new kernel version at 4.13.XXX and you will then have a kernel of higher value than 4.7.XXXX.

You could then uninstall the normal linux-generic package since it would no longer be useful and more likely a burden since it'll still install the updated kernel for it.

You can also read up on what the hew-16.04 packages are all about here:
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack")

Hope that makes some sense.

---

### Post by teropesonen on 2018-01-11
Yes, it makes sense, thank you! I will give this a go.

---

### Post by teropesonen on 2018-01-11
OK, a couple of minutes later, and I seem to be successfully running the 4.13 branch according to uname. I also removed the old 4.4-generic in corollary. So, the issue appears to be fixed.

Thank you!

---

