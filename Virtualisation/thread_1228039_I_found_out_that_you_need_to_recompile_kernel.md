---
title: "I found out that you need to recompile kernel"
date: 2009-07-31
forum: Virtualisation
---

### Post by irv on 2009-07-31
I found out when you update the kernel you need to recompile the VirtualBox kernel also. When you try to start a virtual session you will get an error after updating.  Here is what I had to do to get it going again.

> irv@irv-new-laptop:~$ sudo /etc/init.d/vboxdrv setup
[sudo] password for irv: 
 * Stopping VirtualBox kernel module                                             *  done.
 * Recompiling VirtualBox kernel module                                          *  done.
 * Starting VirtualBox kernel module                                             *  done.
irv@irv-new-laptop:~$ 

I hope this helps someone else who runs into this problem. I am using VirtualBox 3.0.
Here is a copy of my vbox-install.log (/var/log).
> Attempting to install using DKMS

Creating symlink /var/lib/dkms/vboxdrv/3.0.2/source ->
                 /usr/src/vboxdrv-3.0.2

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=2.6.28-14-generic -C /lib/modules/2.6.28-14-generic/build M=/var/lib/dkms/vboxdrv/3.0.2/build...........

Running the post_build script:
cleaning build area....

DKMS: build Completed.

vboxdrv.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.28-14-generic/updates/dkms/

depmod.......

DKMS: install Completed.
Attempting to install using DKMS

Creating symlink /var/lib/dkms/vboxnetflt/3.0.2/source ->
                 /usr/src/vboxnetflt-3.0.2

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Running the pre_build script:

Building module:
cleaning build area....
make KERNELRELEASE=2.6.28-14-generic -C /lib/modules/2.6.28-14-generic/build M=/var/lib/dkms/vboxnetflt/3.0.2/build..........
cleaning build area....

DKMS: build Completed.

vboxnetflt.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.28-14-generic/updates/dkms/

depmod....

DKMS: install Completed.
Attempting to install using DKMS

Creating symlink /var/lib/dkms/vboxnetadp/3.0.2/source ->
                 /usr/src/vboxnetadp-3.0.2

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Running the pre_build script:

Building module:
cleaning build area....
make KERNELRELEASE=2.6.28-14-generic -C /lib/modules/2.6.28-14-generic/build M=/var/lib/dkms/vboxnetadp/3.0.2/build.........
cleaning build area....

DKMS: build Completed.

vboxnetadp.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.28-14-generic/updates/dkms/

depmod....

DKMS: install Completed.

---

### Post by bodhi.zazen on 2009-07-31
With the PUEL edition this is usually done for you automatically.

Not sure about the OSE.

If it does not happen automatically you occasionally need to build it yourself as you suggest.

And you are not re-compiling the kernel, you are compiling the virtualbox kernel module (which is a bit different).

---

### Post by irv on 2009-07-31
> **bodhi.zazen said:**
> With the PUEL edition this is usually done for you automatically.

Not sure about the OSE.

If it does not happen automatically you occasionally need to build it yourself as you suggest.

And you are not re-compiling the kernel, you are compiling the virtualbox kernel module (which is a bit different).
Thanks for the clarification. I don't know why it didn't do it automatically I am using the PUEL. I installed it off their website.

---

### Post by bodhi.zazen on 2009-07-31
s[s]h[/s]tuff happens ...

this particular issues is uncommon but not rare and I see you already posted the solution =)

---

### Post by irv on 2009-07-31
Actually, when the error comes up it tells you how to fix it so I wouldn't have had to post here. I know new users might not see the fix so I am covering all bases in case someone does a search for a fix.

---

### Post by bodhi.zazen on 2009-07-31
> **irv said:**
> Actually, when the error comes up it tells you how to fix it so I wouldn't have had to post here. I know new users might not see the fix so I am covering all bases in case someone does a search for a fix.

+1 thank you for that.

---

