---
title: "How to upgrade vboxdrv 5.0 -&gt; 5.2?"
date: 2017-11-30
forum: Virtualisation
---

### Post by ruslan-primak on 2017-11-30
I have installed VirtualBox 5.2 from official download site.
But it does not work.
It shows the next error:
 > RTR3InitEx failed with rc=-1912 (rc=-1912)

The VirtualBox kernel modules do not match this version of VirtualBox. The installation of VirtualBox was apparently not successful. Executing

[COLOR=#0000ff]'/sbin/vboxconfig'[/COLOR]

may correct this. Make sure that you do not mix the OSE version and the PUEL version of VirtualBox.

where: supR3HardenedMainInitRuntime what: 4 VERR_VM_DRIVER_VERSION_MISMATCH (-1912) - The installed support driver doesn't match the version of the user. 


I have spent some days in looking for solution: I have tried completely remove all virtualbox software and install new one. But nothing helps.
What I can see that I have vboxdrv 5.0 and suppose it mismatches with Virtualbox5.2.
```

ruslan@RuslanLaptop:~$ modinfo vboxdrv
filename:       /lib/modules/4.10.0-40-generic/updates/dkms/vboxdrv.ko
version:        5.0.40_Ubuntu r115130 (0x00240000)
license:        GPL
description:    Oracle VM VirtualBox Support Driver
author:         Oracle Corporation
srcversion:     82C46C8652E09674C56E7F1
depends:        
vermagic:       4.10.0-40-generic SMP mod_unload 
parm:           force_async_tsc:force the asynchronous TSC mode (int)

```
But I don't know how to upgrade it.
Ubuntu 16.04.
I'm newbie with Ubuntu

---

### Post by SeijiSensei on 2017-11-30
Remove everything you've installed, then follow the instructions at [https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions) to add the Oracle repository and install the virtualbox-5.2 package from there.  It will download any other dependencies, like the kernel headers and gcc compiler needed to compile the VB kernel module to match your installation. When you open the VB manager, you'll be prompted to download and install the extensions.

---

### Post by deadflowr on 2017-11-30
It seems like you had virtualbox installed or installed virtualbox from Ubuntu's already available Software .
Lets' look at what virtualboxs are installed
open the terminal and run
```
dpkg -l | grep virtualbox | awk '{print $1,$2,$3}'
```
this should show the current state (installed, not installed half-installed, etc) the package names, and the versions.

For what it's worth the vboxdrv version is the matching version for the virtualbox installable from the Ubuntu Software.
If that makes some sense.

---

### Post by ruslan-primak on 2017-11-30
> **SeijiSensei said:**
> Remove everything you've installed, then follow the instructions at [https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions) to add the Oracle repository and install the virtualbox-5.2 package from there.  It will download any other dependencies, like the kernel headers and gcc compiler needed to compile the VB kernel module to match your installation. When you open the VB manager, you'll be prompted to download and install the extensions.
Hi, SeijiSensei!
Thank you for help. I have read your answer in the thread [https://ubuntuforums.org/showthread.php?t=2304851](https://ubuntuforums.org/showthread.php?t=2304851)
Also I have done all instructions from the [https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions)
So let me follow your recommendations step by step.

Hi, deadflowr! Thank you for help!
I'll use your recommendations too.

1. What I have:
> 
ruslan@RuslanLaptop:~$ dpkg -l | grep virtualbox | awk '{print $1,$2,$3}'
rc virtualbox 5.0.40-dfsg-0ubuntu1.16.04.1
ii virtualbox-5.2 5.2.2-119230~Ubuntu~xenial
rc virtualbox-qt 5.0.40-dfsg-0ubuntu1.16.04.1

2. Do clean ```
sudo apt-get remove --purge virtualbox virtualbox*
```
3. What I have now:
> ruslan@RuslanLaptop:~$ dpkg -l | grep virtualbox | awk '{print $1,$2,$3}'
ruslan@RuslanLaptop:~$ 

I.e. nothing
4. But vboxdrv is still here:
> ruslan@RuslanLaptop:~$ dpkg -l | grep virtualbox | awk '{print $1,$2,$3}'
ruslan@RuslanLaptop:~$ modinfo vboxdrv
filename:       /lib/modules/4.10.0-40-generic/updates/dkms/vboxdrv.ko
version:        5.0.40_Ubuntu r115130 (0x00240000)
license:        GPL
description:    Oracle VM VirtualBox Support Driver
author:         Oracle Corporation
srcversion:     82C46C8652E09674C56E7F1
depends:        
vermagic:       4.10.0-40-generic SMP mod_unload 
parm:           force_async_tsc:force the asynchronous TSC mode (int)

Any suggestions how to remove it? Or upgrade?

---

### Post by vasa1 on 2017-12-01
```
ruslan@RuslanLaptop:~$ dpkg -l | grep virtualbox | awk '{print $1,$2,$3}'
ruslan@RuslanLaptop:~$ modinfo vboxdrv
```[s]Shouldn't you grep for *vboxdrv* and not *virtualbox*?[/s]

On my system:```
$ dpkg -l | grep virtualbox
ii  virtualbox-5.2                                  5.2.0-118431~Ubuntu~xenial                               amd64        Oracle VM VirtualBox
$ dpkg -l | grep vboxdrv
$ locate vboxdrv
/etc/systemd/system/multi-user.target.wants/vboxdrv.service
/etc/udev/rules.d/60-vboxdrv.rules
/lib/modules/4.10.0-38-generic/misc/vboxdrv.ko
/lib/modules/4.10.0-40-generic/misc/vboxdrv.ko
/lib/systemd/system/vboxdrv.service
/sbin/rcvboxdrv
/usr/lib/virtualbox/vboxdrv.sh
/usr/share/virtualbox/src/vboxhost/vboxdrv
/usr/share/virtualbox/src/vboxhost/vboxdrv/Makefile
...
many more lines
```

---

### Post by ruslan-primak on 2017-12-01
Hello, vasa1

Thank you for help!
It seems that on your system you have the same vboxdrv version as me and it seems to work well with VirtualBox5.2. Isn't it?
What I have in according to your terminal commands:
```
ruslan@RuslanLaptop:~$ dpkg -l | grep virtualbox
ruslan@RuslanLaptop:~$ dpkg -l | grep vboxdrv
ruslan@RuslanLaptop:~$ locate vboxdrv
/lib/modules/4.10.0-40-generic/updates/dkms/vboxdrv.ko
```

Do you remember how you install and configure VirtualBox on your system?

---

### Post by vasa1 on 2017-12-01
> **ruslan-primak said:**
> Hello, vasa1

Thank you for help!
It seems that on your system you have the same vboxdrv version as me and it seems to work well with VirtualBox5.2. Isn't it?
What I have in according to your terminal commands:
```
ruslan@RuslanLaptop:~$ dpkg -l | grep virtualbox
ruslan@RuslanLaptop:~$ dpkg -l | grep vboxdrv
ruslan@RuslanLaptop:~$ locate vboxdrv
/lib/modules/4.10.0-40-generic/updates/dkms/vboxdrv.ko
```

Do you remember how you install and configure VirtualBox on your system?
I'm sorry but I don't have enough experience in installing and configuring VirtualBox! I somehow got it to work and I'm not going to mess with it until 18.04.2 is released.

In short, I downloaded from [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads) but now that site is offering v5.2.2. I didn't go the ppa route.

The older version is here: [https://www.virtualbox.org/wiki/Download_Old_Builds_5_2](https://www.virtualbox.org/wiki/Download_Old_Builds_5_2) but there's not mention of the corresponding Guest Additions.

---

### Post by deadflowr on 2017-12-01
Perhaps try removing all virtualbox packages again.
Then do a reboot
Then check if the vboxdrv module still exists.
If not then try installing your deb file.
(or follow the advice in post #2 to add the oracle repos)

---

### Post by ruslan-primak on 2017-12-01
I have upgraded Ubuntu 16.04 up to 18.04 and achieved desired result. I cannot consider it as solution but as possible variant.
So thread can be closed.

---

### Post by vasa1 on 2017-12-01
> **ruslan-primak said:**
> I have upgraded Ubuntu 16.04 up to 18.04 and achieved desired result. I cannot consider it as solution but as possible variant.
So thread can be closed.I hope things work out for you. Upgrading to 18.04 at this early stage in 18.04's development is okay only if the machine you've done this on is purely for experimentation.

Thread closed at OP's request.

---

