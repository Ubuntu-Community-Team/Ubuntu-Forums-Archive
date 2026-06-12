---
title: "No virtualbox-ose-modules for kernel 2.6.24-21"
date: 2008-08-18
forum: Virtualisation
---

### Post by infroger on 2008-08-18
Hi,
I've upgraded my hardy box yesterday and the kernel got a new version (2.6.24-21).


roger@dell:~$ uname -a
Linux dell 2.6.24-21-generic #1 SMP Tue Aug 12 13:37:22 UTC 2008 i686 GNU/Linux



Now Virtual Box says :

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


CÃ³digo de Resultado: 
0x80004005
Componente: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 


There's no virtualbox-ose-modules-2.6.24-21 package yet.



roger@dell:~$ apt-cache search virtualbox-ose-modules-2.6.24 generic
virtualbox-ose-modules-2.6.24-16-generic - virtualbox-ose module for linux-image-2.6.24-16-generic
virtualbox-ose-modules-2.6.24-18-generic - virtualbox-ose module for linux-image-2.6.24-18-generic
virtualbox-ose-modules-2.6.24-19-generic - virtualbox-ose module for linux-image-2.6.24-19-generic
virtualbox-ose-modules-2.6.24-20-generic - virtualbox-ose module for linux-image-2.6.24-20-generic


Anyone knows if there's a prevision for the release of this package?

Regards,
Roger

---

### Post by circlemaster on 2008-08-18
I asked this in #ubuntu and they said that it is because you have "proposed" software sources checked. But I don't know why they don't update the vbox module at the same time...

---

### Post by infroger on 2008-08-18
Thanks for the ultra fast response!

I'll keep both kernels until the virtualbox module is released.

Regards,
Roger

---

### Post by nco71 on 2008-08-19
I found this solution on ubuntu forum. It is very easy to download the sources and compilate your own version althought I agree it would be more transparent if somebody just uppdate the sources on synaptic.

But the kernel is quite often updated so instead of waiting I prefer to use this method


sudo apt-get install virtualbox-ose-source
sudo m-a update
sudo m-a prepare
sudo m-a a-i virtualbox-ose
sudo /etc/init.d/vboxdrv restart

I don't remember who posted that, sorry if I don't have the sources.

---

### Post by njama on 2008-08-22
Hello, I'm very new to Linux world.

I followed the previous post. Now I get this (look attached file).
Please help.:confused:

---

### Post by b0b138 on 2008-08-22
make sure your username is in the virtualbox group  system/administration/users and groups


I believe running "sudo /etc/init.d/vboxdrv setup" will get vbox back up and running after a kernel update.

---

### Post by njama on 2008-08-22
ok, success. thank you.

---

### Post by penguins01 on 2008-08-23
Thanks very much for the help, also thanks to who-ever posted that code in the first place.

---

### Post by lg5productions on 2008-08-24
All these steps helped me to bring up my VirtualBox XP Session. Gracias for all the help! ;) \\:D/ :cool:

---

### Post by charles.figura on 2008-09-02
nco71 - I went to try your solution, but it fails, as I don't have the linux-headers-2.6.24-21.  Synaptic (as well as a search on packages.ubuntu.com) doesn't show any headers for 2.6.24-20 or 2.6.24-21 - only for -19 and earlier.

How did you get the header files?

---

### Post by Bastaard on 2008-09-10
I think the non open source version (the one in the repositories is open source) doesn't have this problem. Download it from [http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by anarhell on 2008-10-30
that work for me thx

---

### Post by Arabiest on 2008-11-02
Thank you my problem with ubuntu 8.10 upgrade is fixed.

Regards,

---

