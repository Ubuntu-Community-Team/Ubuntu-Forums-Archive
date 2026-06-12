---
title: "Cannot get Sun VirtualBox to work..."
date: 2009-08-16
forum: Virtualisation
---

### Post by the.drizzle on 2009-08-16
New to kubuntu, but have been using linux for quite a few years now.  But now, I'm stuck.

I need to get VirtualBox up and running, but I just cannot seem to get it to work.  In particular, if I use a binary version from [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian), I get the same problem with every version (and I've tried both version 2 and 3, intrepid and jaunty releases).

VirtualBox starts up OK, and I can map my (existing) .vdi file as a machine (I've migrated from gentoo this past week).  However, when I attempt to start the machine, I get the error:

```
Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Re-setup the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.
```

which leads to

```
user@klatu:~$ sudo /etc/init.d/vboxdrv setup                      
[sudo] password for user:
* Stopping VirtualBox kernel module
*  done.
* Removing old VirtualBox netadp kernel module
*  done.
* Removing old VirtualBox netflt kernel module
*  done.
* Removing old VirtualBox kernel module
*  done.
* Recompiling VirtualBox kernel module
*  done.
* Starting VirtualBox kernel module
* modprobe vboxdrv failed. Please use 'dmesg' to find out why
user@klatu:~$ dmesg | grep VirtualBox
[   56.197273] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
```

At which point I don't know how to proceed.

Things I've tried:

- all available versions (same error for all)

- installing restricted kernel modules (dependency issues; all fixed now, but no effect on vbox problem)

- compiled + installed OSE version from source (similar problem, forgot to record it before removing non-working program...)

- swore at computer vigorously.

Nothing has worked!  I really need to get this program up and running, as the .vdi image has quite a bit of important data on it.  I'm not looking forward to having to re-istall gentoo again just for this one item, as I'm otherwise very pleased with kubuntu... :(

Thanks in advance!

---

### Post by edwardtilbury on 2009-08-17
does it show in the synaptic package manager? if so right click and choose remove all files..

Other than that.. I'm pretty much a noob, you might have to do a file search and trash it's directories , but that would be pretty scary.

---

### Post by scorp123 on 2009-08-17
> **the.drizzle said:**
>  [   56.197273] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)[/CODE]
 [http://forums.virtualbox.org/viewtopic.php?f=7&t=15828#p66409](http://forums.virtualbox.org/viewtopic.php?f=7&t=15828#p66409)

But that of course does not fix your problem. :D

So let's talk about your computer. Is it a 64-bit machine? And you also tried to run the 64-bit VirtualBox? Yes?

The only thing that comes to my mind is that you might have forgotten to install compilers and such. You did install the "build-essential" package, right?

```
sudo apt-get install build-essential
```

Because without that package nothing can be compiled. And I'd say it's the most frequent "problem" people trying out VMware or VirtualBox run into ... they simply forgot to install this package.

Can you check if the package is there on your system and if it would change anything?

BTW ... I'd also recommend to use Sun's Debian repository. Copy and paste this stuff here:
```
# wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -
deb http://download.virtualbox.org/virtualbox/debian jaunty non-free

```

... Store those lines into a file:
**/etc/apt/sources.list.d/virtualbox.list**

One way to do it would be e.g. by typing this command:
```
gksudo gedit /etc/apt/sources.list.d/virtualbox.list
```

Edit: KDE Users (e.g. on Kubuntu) would use this command:
```
kdesu kate /etc/apt/sources.list.d/virtualbox.list
```

Then do what the comment in the first line says:
```
wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -
```

That will get Sun's repository crypto-keys and you're fine to go:
```
sudo apt-get install virtualbox-3.0
```

With the repos configured you'd be automagically informed whenever there is an update to their product. And enabling the repos also has the positive side-effect that any dependency problems will now be auto-handled by the package manager.

---

### Post by the.drizzle on 2009-08-17
> **scorp123 said:**
> So let's talk about your computer. Is it a 64-bit machine? And you also tried to run the 64-bit VirtualBox? Yes?

Nope; Intel core 2 duo running kubuntu 9.04 x86 desktop.

> **scorp123 said:**
> The only thing that comes to my mind is that you might have forgotten to install compilers and such. You did install the "build-essential" package, right?

I have now!  Like I said, new to *buntu!  I had to pull in all sorts of -dev packages to compile the ose version from source, so I'm surprised that particular package was not pulled in then.  Oh well, live and learn ;)


> **scorp123 said:**
>  ... they simply forgot to install this package.

Or didn't know about it! :)

> **scorp123 said:**
>  I'd also recommend to use Sun's Debian repository. 

Already done.

OK, packages updated, VirtualBox re-installed, error persists.

I'll try rebooting the computer, but I'm not terribly hopeful at this point...

EDIT:

No change, but it seems that /dev/vbox doesn't seem to exist.  Perhaps I should manually create it in /etc/fstab?

---

### Post by the.drizzle on 2009-08-18
OK, got tired of failing binaries.  So did things myself ;)

In case anyone else is having this problem, I simply got the source for the required kernel module from [here]("http://gentoo.zerodev.it/files/"), and compiled it myself; I put the .ko files into /lib/modules/2.6.28-11-generic/misc/ and edited /etc/modules to autoload them at boot.

Works like a charm!

---

### Post by steveneddy on 2009-08-18
You have to add yourself to the vbox users profile.

[http://ubuntuforums.org/showthread.php?t=504328](http://ubuntuforums.org/showthread.php?t=504328)

---

### Post by the.drizzle on 2009-08-18
> **steveneddy said:**
> You have to add yourself to the vbox users profile.

[http://ubuntuforums.org/showthread.php?t=504328](http://ubuntuforums.org/showthread.php?t=504328)

Thanks, but no.  Already done before starting thread in the first place, please see my above post.

---

