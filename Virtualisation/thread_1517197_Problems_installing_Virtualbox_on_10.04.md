---
title: "Problems installing Virtualbox on 10.04"
date: 2010-06-24
forum: Virtualisation
---

### Post by Landshark on 2010-06-24
There are many threads on the problems I'm having, and I haven't been able to solve what I'm running into.  I've tried the repo's and the download from the VB site. I would appreciate any feedback.

Lucid 10.04
Kernel: 2.6.34-999-generic 64-bit

After installing from the repo's, I can start the program but receive the following:

WARNING: The character device /dev/vboxdrv does not exist.
         Please install the virtualbox-ose-dkms package and the appropriate
         headers, most likely linux-headers-generic.

         You will not be able to start VMs until this problem is fixed.

virtualbox-ose-dkms is already installed.

There are numerous posts about this, some solved and some not.

I created the vboxusers group and added myself to it.

I already have the kernel headers installed for my kernel.


Suggestions have included:

sudo /etc/init.d/vboxdrv setup

But I don't have /etc/init.d/vboxdrv. I have:

-rwxr-xr-x   1 root root 11116 2010-06-08 07:34 vboxdrv.dpkg-bak
-rwxr-xr-x   1 root root  6160 2010-05-29 15:35 virtualbox-ose

(I started these.) Still no luck.

sudo modprobe vboxdrv >> FATAL: Module vboxdrv not found.

How do I install this separately from what I've already done?

cat /var/log/vbox-install.log produces:


Creating symlink /var/lib/dkms/vboxdrv/3.2.4/source ->
                 /usr/src/vboxdrv-3.2.4

DKMS: add Completed.

Error! Your kernel headers for kernel 2.6.34-999-generic cannot be found at
/lib/modules/2.6.34-999-generic/build or /lib/modules/2.6.34-999-generic/source.
You can use the --kernelsourcedir option to tell DKMS where it's located, or you could install the linux-headers-2.6.34-999-generic package.
Failed to install using DKMS, attempting to install without
Makefile:159: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.


Any other thoughts or suggestions? I'm stumped.

Landshark

---

### Post by TheFu on 2010-06-26
Just a few shots in the dark ...  I believe I'm running the latest patched Ubuntu kernel and it is 2.6.32-22-???, not 2.6.34-whatever. Virtualization hypervisors are tightly connected to the specific kernel, so by being on a dev kernel tree, you will need to build everything from source for DKMS and virtualbox. 

Or you can drop back to the stable, 2.6.32-xxx kernels.

---

### Post by Landshark on 2010-06-28
Good input. Thanks. I jumped onto the current kernel I'm running to solve some other hardware issues. I'll play around.

---

### Post by do0b on 2010-06-30
i had the same problem like 2days ago. had a fresh install of 10.04 with the updates installed. installed virtual box, installed my iso. next day i got that same error.

what i did was went to terminal and typed in

```
sudo apt-get update
sudo apt-get upgrade
```reboot.

virutual box started working again.

---

### Post by Landshark on 2010-07-03
Thinkpad T40  10.04  2.6.34-020634-generic

Thanks for the advice from you both. I'm between a rock and a hard place: I need to use the 2.6.34 kernel because it solves a longstanding suspend issue wherein my USB fails after waking up on 2.6.32. But I did install the latest XXX.34 stable version: 2.6.34-020634-generic rather than the one I was using before.

However, although Virtual box worked great under the 2.6.32 kernel, it fails under 2.6.34. (The package works but not the VM itself.)  At the command line it gives me:

WARNING: The character device /dev/vboxdrv does not exist.
         Please install the virtualbox-ose-dkms package and the appropriate
         headers, most likely linux-headers-generic.
         You will not be able to start VMs until this problem is fixed.

(Both packages are installed.)

When attempting to start the VM, I get:

Please install the virtualbox-ose-dkms package and execute 'modprobe vboxdrv' as root.

(The package is installed but modprobe gives me FATAL: Module vboxdrv not found.)

update and upgrade didn't help.

So it's telling me that packages that are installed don't exist. It also can't find the module.

Any thoughts?

---

### Post by Landshark on 2010-07-03
I *think* I can answer part of the question myself:

I am running the 2.6.34-generic kernel that solves the suspend / USB issue, but I need the version of Virtualbox that is appropriate for the new kernel.

Uh, how do I go about getting that? Would that be through backports?

---

### Post by TheFu on 2010-07-04
> **Landshark said:**
> 
Uh, how do I go about getting that? Would that be through backports?

It seems you have two choices if you aren't willing to change back to the current kernel.
1) Download the source and start compiling.
2) Wait for THAT kernel to be supported by Oracle's vbox builds.

Backports are for older system support, not newer.

---

### Post by Landshark on 2010-07-07
Thank you. Good input. Before I started compiling a new kernel, I started from a clean slate and installed current VBox PUEL version straight from the Sun / Oracle. It worked.

---

