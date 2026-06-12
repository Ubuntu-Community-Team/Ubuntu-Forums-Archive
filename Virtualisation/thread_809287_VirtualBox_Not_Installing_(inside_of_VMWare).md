---
title: "VirtualBox Not Installing (inside of VMWare)"
date: 2008-05-27
forum: Virtualisation
---

### Post by FredJones on 2008-05-27
I am getting an error when I start a VirtualBox machine:

```


VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

```

but everything seems to be installed but NOT working. Also I am in the vboxusers group and I rebooted also. Here is my CLI:

```

fred@virtual-ubuntu:~$ sudo apt-get install virtualbox-ose virtualbox-ose-modules-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
virtualbox-ose is already the newest version.
virtualbox-ose-modules-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
fred@virtual-ubuntu:~$ sudo modprobe vboxdrv
FATAL: Module vboxdrv not found.

```

Let me clarify that this Ubuntu is actually not a 'real' Ubu--it's Ubu run as a virtual machine inside of VMWare. 

Does anyone know if what I am trying to do is possible? Install VirtualBox inside of this VMWare Ubuntu Client?

Why am I doing this, you ask? Because VirtualBox won't run on Win 2K and I have a VBox I downloaded that I want to run. :)

---

### Post by dRock1286 on 2008-05-27
You need to load the previous kernel.  2.6.24-16 is the one needed.  don't know why, but vbox only runs on a certain kernel and has to be updated by Sun everytime a new kernel comes out (right now anyways)


To load it, press Esc at the grub menu and select the xxx16 one.  xxx17 is the current and vbox won't run in it...

---

### Post by FredJones on 2008-05-27
Didn't seem to help:

```

fred@virtual-ubuntu:~$ uname -r
2.6.24-16-generic
fred@virtual-ubuntu:~$ sudo apt-get install virtualbox-ose virtualbox-ose-modules-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
virtualbox-ose is already the newest version.
virtualbox-ose-modules-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
fred@virtual-ubuntu:~$ sudo modprobe vboxdrv
FATAL: Module vboxdrv not found.
hershel@virtual-ubuntu:~$ 

```

Unless I am missing something...

---

### Post by Jose Catre-Vandis on 2008-05-27
You may need to install some or all of these to get the vboxdrv module to run
```
sudo apt-get install linux-source
sudo apt-get install make gcc build-essential
sudo apt-get install xen-headers #[choose the version you need, in this case - 2.6.19-4-server]
sudo apt-get install xen-headers-2.6.19-4-server
sudo apt-get install linux-headers-$(uname -r)

and perhaps

sudo aptitude install virtualbox-ose-modules-generic
```

also check on the virtualbox.org forum for other reasons vboxdrv is not loading

---

### Post by forestpixie on 2008-05-27
Well that sounds like fun, run a virtual inside a virtual :D - are you sure that vbox won't run on 2k, I thought I did previously.

Have you tried to download and install the sun version rather than the buntu one in the repos.

I bet working out the memory for the first virtual machine is going to be fun bearing in mind the second one will need to use some of it :)

And no I don't know if it's possible - but you can but try.

---

### Post by Shazaam on 2008-05-27
VMware won't run inside a virtual machine (it pops up a box and tells you that) so I imagine VirtualBox won't either.

---

### Post by Jose Catre-Vandis on 2008-05-27
Also the changelog for VirtualBox 1.5.2 says they have fixed the installation issues for Windows 2000. Suggest you try the closed source version 1.6 from SUN or find a closed source version of 1.5.2

---

### Post by FredJones on 2008-05-27
> are you sure that vbox won't run on 2k, I thought I did previously.

COuld be--the current version won't install--fails and says it requires XP.

> Also the changelog for VirtualBox 1.5.2 says they have fixed the installation issues for Windows 2000. Suggest you try the closed source version 1.6 from SUN or find a closed source version of 1.5.2

The version I have is 1.6 and it's from Sun AFAIK. Where else can I download? You have a link?

> You may need to install some or all of these to get the vboxdrv module to run

Tried those. This one:

> sudo apt-get install xen-headers-2.6.19-4-server

failed--couldn't find package.

All the others worked, but still VBox doesnt' work. So I rebooted and forgot to select the .16 in GRUB so it went into .17 with no menus at all. Heh heh.

So I rebooted into .16 and the menus are there. :)

> also check on the virtualbox.org forum for other reasons vboxdrv is not loading

Thanks. Will do

---

### Post by lswest on 2008-05-27
try this: ```
sudo /etc/init.d/vboxdrv setup
``` it works on the non-OSE version of virtualbox.

---

### Post by FredJones on 2008-05-27
Didn't help:

```

fred@virtual-ubuntu:~$ sudo /etc/init.d/vboxdrv setup
 * Usage: /etc/init.d/vboxdrv {start|stop|restart|status}
fred@virtual-ubuntu:~$ sudo /etc/init.d/vboxdrv restart
 * Stopping VirtualBox kernel module vboxdrv                             [ OK ] 
 * Starting VirtualBox kernel module vboxdrv                                    
 * Modprobe vboxdrv failed. Please use 'dmesg' to find out why.

```

---

### Post by Benbow on 2008-05-27
I don't normally chip in on someone else's posting but I have had exactly the same problem as Fredjones. I followed jose catre-vandis'posting and had the following result -


VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

---

### Post by FredJones on 2008-05-27
> I have had exactly the same problem as Fredjones.

The EXACT same? Meaning your Ubuntu is not a 'real' install, it's inside of VMWare? You mean you are mildly bonkers, like me?

---

### Post by mia.king on 2008-06-01
[from virtualbox forum]: if you just want to extract some files from the VM that someone gave you and don't want a real ubuntu installation, why not try the new 8.04 live cd - apparently with wubi - it can install a semi-temporary Ubuntu on a virtual disk that is "persistent" - but doesn't affect your Win/harddisk.

I know nothing about it, but look it up, and see if it will solve your problem.

---

### Post by FredJones on 2008-06-01
Version 1.5.2 worked on my Win 2K box:

[http://www.filehippo.com/download_virtualbox/](http://www.filehippo.com/download_virtualbox/)

:)

---

### Post by degel3030 on 2009-04-27
Even though this is old, I was having this same issue on a ubuntu server 8.04 edition (8.04.2) 2.6.24-23-server kernel and I found that for whatever reason vboxdrv wasn't started
at the command prompt
root@ubuntu:~# /etc/init.d/vboxdrv start

hope this helps for anyone else in the future

---

