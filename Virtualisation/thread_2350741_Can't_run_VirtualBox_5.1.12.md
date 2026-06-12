---
title: "Can't run VirtualBox 5.1.12"
date: 2017-01-27
forum: Virtualisation
---

### Post by chunkydrew2 on 2017-01-27
I need help. I want to run Virtual Box, but after I create a virtual machine and try to start it, I get an error message```
Kernel driver not installed (rc=-1908)
```

It then says I should ***run /sbin/vboxconfig as root***. When I do that, the operation fails, as shown below. Any suggestions, anyone?
```

~$ sudo /sbin/vboxconfig
vboxdrv.sh: Building VirtualBox kernel modules
vboxdrv.sh: Starting VirtualBox services
vboxdrv.sh: Building VirtualBox kernel modules
vboxdrv.sh: failed: modprobe vboxdrv failed. Please use 'dmesg' to find out why
There were problems setting up VirtualBox.  To re-start the set-up process, run   /sbin/vboxconfig as root
```

I have tried to run this to test multiple distros, with the same result. I am using Ubuntu 16.04 LTS. I have also tried Virtual Box 5.1.14, but went back to 5.1.12 to see if the version was an issue, to no avail. I am running on a Dell Inspiron 5447 which originally has Windows 8.1 installed (now deleted), so it does have UEFI. Could this be part of my problem?

---

### Post by slickymaster on 2017-01-27
Try the following at a terminal window in the host system```
sudo apt-get install linux-headers-generic build-essential dkms
sudo apt-get remove --purge virtualbox-dkms
sudo apt-get install virtualbox-dkms
```

---

### Post by SeijiSensei on 2017-01-27
Alternatively, follow the instructions here to download the version of VirtualBox that Oracle maintains:  [https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions)

It will download any missing dependencies and automatically recompile the kernel module when the package is updated.

---

### Post by Habitual on 2017-01-27
I read yesterday over on LinuxMint forums that 5.1.x didn't require dkms, and I unistalled these from my host
```
sudo apt-get remove -y dkms virtualbox-guest-utils virtualbox-guest-x11 virtualbox --purge
```
5.1.**14**-112924 installed from their site, didn't seem to mind.

YMMV!

---

### Post by chunkydrew2 on 2017-01-28
Thanks for the suggestions. After I disabled secure boot in UEFI, I was able to run the software.

---

