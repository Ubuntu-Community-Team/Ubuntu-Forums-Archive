---
title: "&quot; The VirtualBox support driver&quot; error"
date: 2008-07-31
forum: Virtualisation
---

### Post by newbuntuxx on 2008-07-31
Hey,

I was playing around with Sun virtualbox, then decided to go back to the virtualbox in the repos. After doing so, whenever i try to start the virtual machine i get the following error:


```
The VirtualBox support driver which is running is from a different version of VirtualBox. You can correct this by stopping all running instances of VirtualBox and reinstalling the software..
VBox status code: -1912 (VERR_VM_DRIVER_VERSION_MISMATCH).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

```

any suggestions?

---

### Post by Vadi on 2008-07-31
Well, either go back to Suns version, or you'll need to install the kernel modules for the one in repositories (I forget the name of the package).

---

### Post by overdrank on 2008-07-31
moved to Virtualization  :)

---

### Post by newbuntuxx on 2008-08-01
> **Vadi said:**
> Well, either go back to Suns version, or you'll need to install the kernel modules for the one in repositories (I forget the name of the package).

How can I find out what the kernel name is? and honestly, I am just lost and confused! Why when I totally remove virtualbox using:

```
sudo aptitude --purge remove virtualbox
```

and then reinstall it from the repos, it doesn't install the correct kernel? Thats just puzzling! Do I really need to know the structure of the program, and the name of its components before being able to install and use it?

at any rate, i am not bothered with learning this stuff. So, my question is: What are the components that I must download to be able to use virtualbox (not the sun one)? And if someone has the time and knowledge, please briefly explain the function of each component.

Also, is there a how-to to install virtualbox on hardy heron? because i looked around and only found how-tos for 7.10 and nothing really for 8.04.

thanks again

Edit: 

Thanks for moving it to the right forum overdrank.

---

### Post by newbuntuxx on 2008-08-01
so, i looked in the pinned threads and came across this tutorial:

[http://gaming.gwos.org/doku.php/udsf:virtualbox](http://gaming.gwos.org/doku.php/udsf:virtualbox)

I followed it to the dot. Then, when I get to:


```
sudo apt-get install virtualbox
```

I get this:

```

ali@ali-desktop:~$ sudo apt-get install virtualbox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package virtualbox is a virtual package provided by:
  virtualbox-ose 1.5.6-dfsg-6ubuntu1
You should explicitly select one to install.
E: Package virtualbox has no installation candidate

```

and i am supposed to know the difference between: virtualbox-ose and 1.5.6dfsg-6ubuntu1? 

and how many versions are there of the virtualbox? honestly, things just get way out of hand and confusing to the user when you have 10 different applications called the same name and each have their own kernel modules (whatever that is!) and drivers that need to be installed.....

sorry for venting guys, but i've been trying to perform a very simple task for the past five hours: remove bad software, reboot machine, reinstall software, software works! but thats proven to be a pain in the ****.

---

### Post by newbuntuxx on 2008-08-01
this is what i get when i type:

```
ali@ali-desktop:~$ dpkg -l |grep virtual
ii  gvfs                                       0.2.5-0ubuntu2                                     userspace virtual filesystem - server
ii  gvfs-backends                              0.2.5-0ubuntu2                                     userspace virtual filesystem - backends
ii  gvfs-fuse                                  0.2.5-0ubuntu2                                     userspace virtual filesystem - fuse server
ii  libgvfscommon0                             0.2.5-0ubuntu2                                     userspace virtual filesystem - library
ii  virtualbox                                 1.5.6-28266_Ubuntu_hardy                           innotek VirtualBox
rc  virtualbox-ose                             1.5.6-dfsg-6ubuntu1                                x86 virtualization solution - binaries
ii  virtualbox-ose-modules-2.6.24-19-generic   24.0.4                                             virtualbox-ose module for linux-image-2.6.24
ii  virtualbox-ose-modules-generic             24.0.4                                             virtualbox-ose module for linux-image-generi

```

---

### Post by Vadi on 2008-08-01
Try

> sudo apt-get remove virtualbox virtualbox-ose virtualbox-ose-modules-2.6.24-19-generic virtualbox-ose-modules-generic

And

> sudo apt-get install virtualbox virtualbox-ose-modules-generic

---

### Post by newbuntuxx on 2008-08-01
hey,

when i try this:

```

sudo apt-get install virtualbox virtualbox-ose-modules-generic 
```

i get this:

```

admin@ali-desktop:~$ sudo apt-get install virtualbox virtualbox-ose-modules-generic 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package virtualbox is a virtual package provided by:
  virtualbox-ose 1.5.6-dfsg-6ubuntu1
You should explicitly select one to install.
E: Package virtualbox has no installation candidate
admin@ali-desktop:~$ 

```

---

### Post by Vadi on 2008-08-01
I'm at loss at this point. Virtualbox isn't really flexible in getting it's different versions swapped back and forth.

---

### Post by newbuntuxx on 2008-08-02
could it be my software sources list? thats why apt-get is not finding the right: virtualbox?

Here is my list:


```

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb http://archive.canonical.com/ubuntu dapper-commercial main


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://archive.canonical.com/ubuntu dapper-commercial main

# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb http://archive.ubuntu.com/ubuntu/ hardy multiverse restricted universe main
deb http://security.ubuntu.com/ubuntu/ hardy-security restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ hardy-updates restricted main multiverse universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

## zman0900's PPA
deb http://ppa.launchpad.net/zman0900/ubuntu hardy main
deb-src http://ppa.launchpad.net/zman0900/ubuntu hardy main

# deb http://ppa.launchpad.net/spring/ubuntu hardy main
# deb-src http://ppa.launchpad.net/spring/ubuntu hardy main
# deb http://ppa.launchpad.net/fta/ubuntu hardy main

# Innotek repository for VirtualBox
deb http://www.virtualbox.org/debian edgy non-free


```

Even if the two different versions were installed one after the other on the same system, there should be away to just clean the system from all the virtualbox files/directories etc... (which is what an uninstall is meant for) and then a reinstall is done.

---

### Post by Vadi on 2008-08-02
Remove "deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) edgy non-free"

---

### Post by newbuntuxx on 2008-08-03
did that...but i still get the same error:

```
admin@ali-desktop:~$ sudo apt-get install virtualbox virtualbox-ose-modules-generic 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package virtualbox is a virtual package provided by:
  virtualbox-ose 1.5.6-dfsg-6ubuntu1
You should explicitly select one to install.
E: Package virtualbox has no installation candidate

```

I pray that I dont have to reinstall the entire operating system just to get one program to work...

---

### Post by erez001 on 2008-08-19
remove all the vboxdrv.ko from /lib/modules/...
the reinstall the kernel modules

worked for me !


erez.

---

### Post by yiorgos on 2009-02-10
> **erez001 said:**
> remove all the vboxdrv.ko from /lib/modules/...
the reinstall the kernel modules

worked for me !


erez.

worked for me to for upgrading from
Virtualbox Version 2.0 to 2.1

---

