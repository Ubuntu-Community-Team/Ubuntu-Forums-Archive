---
title: "Unable to build guest addions kernel module for 10.04 guest"
date: 2011-02-08
forum: Virtualisation
---

### Post by ThaddeusW on 2011-02-08
Hello Everyone,
I have been wanting to play around with Ubuntu Studio and I figured a VM install is the easiest way to go. I am using Virtual box 4.0 on 64bit vista.

My problem is building the guest addition kernel modules. For some reason It cannot find the kernel headers to build the module. Now I have installed every single package I could think of for compiling a kernel and still no dice.

Here is the output:
```
sudo ./VBoxLinuxAdditions.run 
Verifying archive integrity... All good.
Uncompressing VirtualBox 4.0.2 Guest Additions for Linux..........
VirtualBox Guest Additions installer
Removing installed version 4.0.2 of VirtualBox Guest Additions...
tar: Record size = 8 blocks
Removing existing VirtualBox DKMS kernel modules ...done.
Removing existing VirtualBox non-DKMS kernel modules ...done.
Building the VirtualBox Guest Additions kernel modules
The headers for the current running kernel were not found. If the following
module compilation fails then this could be the reason.
 ...fail!
Your system does not seem to be set up to build kernel modules.
Look at /var/log/vboxadd-install.log to find out what went wrong.
Once you have corrected it, you can run

  /etc/init.d/vboxadd setup

to build them.

Doing non-kernel setup of the Guest Additions ...done.
Installing the Window System drivers
Installing X.Org Server 1.7 modules ...done.
Setting up the Window System to use the Guest Additions ...done.
You may need to restart the hal service and the Window System (or just restart
the guest system) to enable the Guest Additions.

Installing graphics libraries and desktop services components ...done.
```

And here is the output of /var/log/vboxadd-install.log:

```
Uninstalling modules from DKMS
Attempting to install using DKMS

Creating symlink /var/lib/dkms/vboxguest/4.0.2/source ->
                 /usr/src/vboxguest-4.0.2

DKMS: add Completed.

Error! Your kernel headers for kernel 2.6.32-28-generic cannot be found at
/lib/modules/2.6.32-28-generic/build or /lib/modules/2.6.32-28-generic/source.
You can use the --kernelsourcedir option to tell DKMS where it's located, or you could install the linux-headers-2.6.32-28-generic package.
Failed to install using DKMS, attempting to install without
Makefile:23: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again..  Stop.
Creating user for the Guest Additions.
Creating udev rule for the Guest Additions kernel module.
```


I am confused as to which package actually contains the kernel headers and where it should be located. Downloading the kernel source only placed a compressed tar archive in my /usr/src directory and using another method to download the source placed a few archives into my home folder (where I ran the command "apt-get source ....").

Am I downloading the wrong packages? /lib/modules sounds like a strange place for kernel header source.

I have ran into this extremely frustrating problem before when using an older version of Virtual box and plain Ubuntu 10.04. And now Ubuntu Studio 10.04 is giving me the same exact problem. I cannot be the only person having such a hard time. Every tutorial I have looked at simply says to run the Vbox-Linux guest install and everything will work.

Any ideas?

---

### Post by Hedgehog1 on 2011-02-10
I just got this to work, and posted it a few minutes ago:

[http://http://ubuntuforums.org/showthread.php?t=1685020]("http://http://ubuntuforums.org/showthread.php?t=1685020")

The same .iso has the drivers for windows and Linux and solaris.

I do need to say that I was doing this in Vbox 4.0.2.

:KS

---

### Post by b0b138 on 2011-02-10
you need the linux-headers-generic package

---

### Post by ThaddeusW on 2011-02-13
> **b0b138 said:**
> you need the linux-headers-generic package

THANK YOU! That fixed it!

What really burns me up about this problem is the simple fact that every tutorial to install the guest additions says nothing about installing any packages. So my question is:

Why did I have problems trying to get two separate Ubuntu 10.04 VM installs working and everyone else on the internet writing these dead simple tutorials did not? Why was I missing that package?

I was cursing allot while trying to solve this problem. Thank you for that simple tip.

---

### Post by CharlesA on 2011-02-13
I had no problems installing the guest additions on Ubuntu 10.04.1 Desktop, either 32-bit or 64-bit. The headers are included by default with Ubuntu Desktop, but maybe they aren't included with Ubuntu Studio?

---

### Post by ThaddeusW on 2011-02-13
> **CharlesA said:**
> I had no problems installing the guest additions on Ubuntu 10.04.1 Desktop, either 32-bit or 64-bit. The headers are included by default with Ubuntu Desktop, but maybe they aren't included with Ubuntu Studio?

You are probably right as I just installed Ubuntu 10.04 and the module built with no problems.

BUT I did have this exact problem before with 10.04, it might have been a very early release or even a beta, I cant rememebr as it was a while ago.

Thank you everyone for the help.

---

### Post by mciverza on 2011-02-16
> **CharlesA said:**
> The headers are included by default with Ubuntu Desktop, but maybe they aren't included with Ubuntu Studio?

+1 that seems true

---

