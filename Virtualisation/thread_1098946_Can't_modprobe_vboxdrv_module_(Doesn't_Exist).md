---
title: "Can't modprobe vboxdrv module (Doesn't Exist)"
date: 2009-03-17
forum: Virtualisation
---

### Post by Jordanwb on 2009-03-17
I installed virtualbox-2.1 on my Acer Aspire 5515, it installed okay and I ran 

```
sudo /etc/init.d/vboxdrv setup
```

It compiles the module but when it tries to modprobe the driver it says it can't find the module:

> root@jordanwb-laptop:/home/jordanwb# /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module                                             *  done.
 * Removing old VirtualBox netflt kernel module                                  *  done.
 * Removing old VirtualBox kernel module                                         *  done.
 * Recompiling VirtualBox kernel module                                          *  done.
 * Starting VirtualBox kernel module                                            
 * modprobe vboxdrv failed. Please use 'dmesg' to find out why

I'm getting the same problem with virtualbox-2.0 and the ose edition.

---

### Post by mocoloco on 2009-03-17
So what does dmesg say?  Try "dmesg | grep VirtualBox" or "dmesg | grep vbox"
Seems like I've seen that before and it was because I didn't have the kernel-headers installed.  Plus if you don't already I think you need build-essental:
```
sudo apt-get install linux-headers-generic build-essential
```

---

### Post by Jordanwb on 2009-03-17
```
sudo apt-get install linux-headers-generic build-essential
```

I ran that then reran the command to build the module but it still failed. grepping dmesg for "virtualbox", "VirtualBox", or "vbox" gave no output.

---

### Post by mocoloco on 2009-03-17
Hmm.  Guess I didn't pay clear attention to the output, shame on me :oops:
Says it's able to recompile the new module fine, so what I said before wasn't helpful.  Try running "sudo modprobe -v vboxdrv".  If that doesn't show anything helpful, run dmesg right after and look through the last few lines for anything that might suggest what the failure is.  Post here if you get stuck.

---

### Post by Jordanwb on 2009-03-17
> jordanwb@jordanwb-laptop:~$ sudo modprobe -v vboxdrv
[sudo] password for jordanwb: 
FATAL: Module vboxdrv not found.

File not found

Perhaps when it compiles the module it doesn't run "make install"?

I'm not sure if this is the right use of find but:

> root@jordanwb-laptop:/# find / -name vboxdrv -type f -print
/etc/init.d/vboxdrv
root@jordanwb-laptop:/#

---

### Post by HankB on 2009-03-18
> **Jordanwb said:**
> File not found

Perhaps when it compiles the module it doesn't run "make install"?

I'm not sure if this is the right use of find but:

Try:
```
root@jordanwb-laptop:/# find / -name **[COLOR="Red"]"[/COLOR]**vboxdrv**[COLOR="Red"]*"[/COLOR]** -type f -print
/etc/init.d/vboxdrv
root@jordanwb-laptop:/# 
```

Your commmand will only find files with the name vboxdrv. I get:
```
root@cypress:~# find / -mount -name "vboxdrv*" -type f -print
/var/lib/dkms/vboxdrv/2.1.4/2.6.27-13-generic/x86_64/module/vboxdrv.ko
/var/lib/dkms/vboxdrv/2.1.4/2.6.27-12-generic/x86_64/module/vboxdrv.ko
/lib/modules/2.6.27-9-generic/misc/vboxdrv.ko
/lib/modules/2.6.27-13-generic/updates/dkms/vboxdrv.ko
/lib/modules/2.6.27-9-server/misc/vboxdrv.ko
/lib/modules/2.6.27-12-generic/updates/dkms/vboxdrv.ko
/etc/init.d/vboxdrv
root@cypress:~# 

```

---

### Post by Jordanwb on 2009-03-18
```
jordanwb@jordanwb-laptop:~$ sudo su
[sudo] password for jordanwb: 
root@jordanwb-laptop:/home/jordanwb# find / -name "vboxdrv*" -type f -print
/etc/init.d/vboxdrv
/lib/modules/2.6.27-9-generic/misc/vboxdrv.ko
/lib/modules/2.6.27-11-generic/updates/dkms/vboxdrv.ko
/lib/modules/2.6.27-9-server/misc/vboxdrv.ko
/var/lib/dkms/vboxdrv/2.1.4/2.6.27-11-generic/i686/module/vboxdrv.ko
root@jordanwb-laptop:/home/jordanwb# 
```

It seems that there isn't a kernel module in /lib/modules/2.6.27-11-generic/misc/ I'm currently running 2.6.27-11. I'm gonna try removing those two 2.6.27-9 folders because I don't use that kernel anymore. I don't even have it installed. :-k

I tried installing vbox from the console and it told me build log would be written to /var/log/vbox-install.log:

> jordanwb@jordanwb-laptop:~$ cat /var/log/vbox-install.log
** Compiling vboxdrv
Attempting to install using DKMS

Creating symlink /var/lib/dkms/vboxdrv/2.1.4/source ->
                 /usr/src/vboxdrv-2.1.4

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=2.6.27-11-generic -C /lib/modules/2.6.27-11-generic/build M=/var/lib/dkms/vboxdrv/2.1.4/build.........

Running the post_build script:
cleaning build area....

DKMS: build Completed.
Running module version sanity check.

vboxdrv.ko:
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.27-11-generic/updates/dkms/

depmod....(bad exit status: 1)

DKMS: install Completed.
** Compiling vboxnetflt
Attempting to install using DKMS

Creating symlink /var/lib/dkms/vboxnetflt/2.1.4/source ->
                 /usr/src/vboxnetflt-2.1.4

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Running the pre_build script:

Building module:
cleaning build area....
make KERNELRELEASE=2.6.27-11-generic -C /lib/modules/2.6.27-11-generic/build M=/var/lib/dkms/vboxnetflt/2.1.4/build........
cleaning build area....

DKMS: build Completed.
Running module version sanity check.

vboxnetflt.ko:
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.27-11-generic/updates/dkms/

depmod....(bad exit status: 1)

DKMS: install Completed.
jordanwb@jordanwb-laptop:~$ 


---

### Post by Jordanwb on 2009-03-20
Bump.

---

### Post by HankB on 2009-03-20
IAME (I am no expert ;) )

```
Running module version sanity check.

vboxdrv.ko:
- Original module
- No original module exists within this kernel
- Installation
- Installing to /lib/modules/2.6.27-11-generic/updates/dkms/

**depmod....(bad exit status: 1)**
```

From your listing, this is the first indication I see of a problem. Questions I have:

Is vboxdrv.ko left in /lib/modules/2.6.27-11-generic/updates/dkms/?

What happens when you run depmod from the command line?```
hbarta@cypress:~$ sudo depmod -a
hbarta@cypress:~$
``` 

-hank

---

### Post by Jordanwb on 2009-03-20
> **HankB said:**
> Is vboxdrv.ko left in /lib/modules/2.6.27-11-generic/updates/dkms/?

Yes

> **HankB said:**
> What happens when you run depmod from the command line?```
hbarta@cypress:~$ sudo depmod -a
hbarta@cypress:~$
``` 


```
root@jordanwb-laptop:/home/jordanwb# depmod -a
root@jordanwb-laptop:/home/jordanwb# 
```

Yay I can modprobe vboxdrv!!

---

### Post by obelisk001 on 2010-02-23
Try this: sudo chown [your username] /lib/modules/2.x.xx-xx-generic/

2.x.xx-xx-generic - your kernel

Example: eduard@eduard-laptop ~ $ sudo chown eduard /lib/modules/2.6.31-14-generic/

---

### Post by Jordanwb on 2010-02-23
Please check the last post on the first page. I got VirtualBox working and this was almost a year ago.

---

