---
title: "Build module using DKMS"
date: 2010-09-04
forum: Server Platforms
---

### Post by atuls on 2010-09-04
Hi All,

I was trying to update the drive for my adaptec raid controller. Unfortunately, Adaptec only provides RPM packages. So I converted the package using alien. After dpkg install, I then tried using dkms to build the module:

```
root@atulsatom# dkms add -m aacraid -v 1.1.5.26400
```
Adding driver was successful, but I got some error during the build

```
root@atulsatom# dkms build -m aacraid -v 1.1.5.26400
Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=2.6.32-24-generic -C /lib/modules/2.6.32-24-generic/build SUBDIRS=/var/lib/dkms/aacraid/1.1.5.26400/build modules....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.32-24-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/aacraid/1.1.5.26400/build/ for more information.
0
0

```

In make.log, it shows:
```
  CC [M]  /var/lib/dkms/aacraid/1.1.5.26400/build/linit.o
cc1: error: unrecognized command line option "-ferror_Please_build_this_driver_in_the_Linux_Kernel_tree"
make[1]: *** [/var/lib/dkms/aacraid/1.1.5.26400/build/linit.o] Error 1
make: *** [_module_/var/lib/dkms/aacraid/1.1.5.26400/build] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic'

```

At the moment, I feel clueless. Can someone point me into the right direction?

Thank you in advance,

Chris

---

### Post by atuls on 2010-09-07
I'm still pretty stuck. Hopefully, someone can throw in some ideas

---

### Post by ema.rainho on 2010-10-11
I have the same problem on my host

# tail /var/lib/dkms/aacraid/1.1.5.26400/build/make.log 

DKMS make.log for aacraid-1.1.5.26400 for kernel 2.6.32-5-686-bigmem (i686)
Mon Oct 11 15:05:46 WEST 2010
make: Entering directory `/usr/src/linux-headers-2.6.32-5-686-bigmem'
  CC [M]  /var/lib/dkms/aacraid/1.1.5.26400/build/linit.o
cc1: error: unrecognized command line option "-ferror_Please_build_this_driver_in_the_Linux_Kernel_tree"
make[3]: *** [/var/lib/dkms/aacraid/1.1.5.26400/build/linit.o] Error 1
make[2]: *** [_module_/var/lib/dkms/aacraid/1.1.5.26400/build] Error 2
make[1]: *** [sub-make] Error 2
make: *** [all] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.32-5-686-bigmem'

---

### Post by Paul S on 2010-10-13
I made a dkms package for a problem mouse module.  It's posted at [http://ubuntuforums.org/showthread.php?t=1589390&highlight=dkms+mouse]("http://ubuntuforums.org/showthread.php?t=1589390&highlight=dkms+mouse")

Suggest you take a look at it and use it as an example, along with "man dkms"

Did you create a dkms.conf file in the source directory?

I had similar problems with the make command erroring due to having wrong directories in it.  

Test it in a terminal and use trial and error until it actually works, then copy it into the dkms.conf file.

hth

---

### Post by electrofreak on 2010-10-14
I am having the exact same problem. I've been in talks with adaptec about it... then they decided to send me the exact same instructions that I already followed...

So I figured I'd come here to see if others are having the same problem, and as luck would have it, I found this post.

It seems the problem is that dkms is not putting the source into a kernel tree for some reason. But I tried running:

```
todd@sub:~$ sudo dkms build -m aacraid -v 1.1.5.26400 --kernelsourcedir /usr/src/linux-headers-`uname -r`
[sudo] password for todd:

Preparing kernel 2.6.32-25-server for module build:
(This is not compiling a kernel, just preparing kernel symbols)
Storing current .config to be restored when complete
Running Generic preparation routine
make mrproper....(bad exit status: 2)
using /usr/src/linux-headers-2.6.32-25-server/.config
(I hope this is the correct config for this kernel)
make oldconfig....
make prepare-all....(bad exit status: 2)

Building module:
cleaning build area....
make KERNELRELEASE=2.6.32-25-server -C /usr/src/linux-headers-2.6.32-25-server SUBDIRS=/var/lib/dkms/aacraid/1.1.5.26400/build modules....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.32-25-server (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/aacraid/1.1.5.26400/build/ for more information.
0
0
ERROR: binary package for aacraid: 1.1.5.26400 not found

```

So I must not be doing that right. I don't know how to make dkms put it into a kernel structure... 

I'm going to link the adaptec people to this discussion... because I'd really like to get this resolved.

My card actually works (functions) with the existing driver module from ubuntu... but it seems there are permission issues preventing asm from working without root (since ubuntu doesn't have root passwords). They claim using their sources should clear up these problems... but I've been unable to support that claim yet.

Issuing commands via 'sudo /usr/StorMan/arcconf ...' does work. But I'd really like to get the permissions setup so that users in the admin group can do that. ASM wants logins to user accounts. I login as my admin user, but it doesn't have enough access to the device to be of any use. Only logging in to ASM with the root account will work... but you can't because ubuntu doesn't have root passwords (and I don't want to set one...).

---

### Post by electrofreak on 2010-10-14
> **Paul S said:**
> I made a dkms package for a problem mouse module.  It's posted at [http://ubuntuforums.org/showthread.php?t=1589390&highlight=dkms+mouse]("http://ubuntuforums.org/showthread.php?t=1589390&highlight=dkms+mouse")

Suggest you take a look at it and use it as an example, along with "man dkms"

Did you create a dkms.conf file in the source directory?

I had similar problems with the make command erroring due to having wrong directories in it.  

Test it in a terminal and use trial and error until it actually works, then copy it into the dkms.conf file.

hth

Your dkms file doesn't seem to have any more fields than the dkms.conf provided by adaptec with this module. I was expecting a possible option of "BUILD_IN_KERNEL_SOURCE_DIRECTORY=true" or something along those lines... but I don't see anything that explicitly makes that happen.

---

### Post by pauledwards03 on 2011-03-04
OK, so here's what I did.. sorry to necropost but I feel it's worth an answer


set up kernel source tree:

installed linux-source from apt, extracted it to /usr/src/linux-source-2.6.32, copy .config from current kernel, make mrproper, make modules_prepare

manually compile aacraid.ko:
```

# make -C /usr/src/linux-source-2.6.32 SUBDIRS=/var/lib/dkms/aacraid/1.1.5.26400/build modules

```

I now have /var/lib/dkms/aacraid/1.1.5.26400/build/aacraid.ko that I fully expect to work against 2.6.32-generic .. I will also need to build one for 2.6.32-server I bet, but that won't be hard. I already did all the hard stuff...


I am considering purchasing an Adaptec RAID controller but I want to have the module ready to roll so I can load it before I install Ubuntu Server 10.04, so there are no delays.

As a side note, I really hope this DKMS thing does not catch on... why couldn't adaptec just have provided us with a normal makefile? :rolleyes:


EDIT: here is my module, built with Ubuntu Server 10.04 i686


edit 2: oops, forgot to include Module.symvers... here's a fixed one. I do not have the hardware yet, so maybe that is why I get a "no such device" when trying to insert it? Shouldn't you be able to load modules for devices you don't have? I am a linux kernel module noob...

---

### Post by pauledwards03 on 2011-03-04
> **pauledwards03 said:**
> OK, so here's what I did.. sorry to necropost but I feel it's worth an answer


set up kernel source tree:

installed linux-source from apt, extracted it to /usr/src/linux-source-2.6.32, copy .config from current kernel, make mrproper, make modules_prepare

manually compile aacraid.ko:
```

# make -C /usr/src/linux-source-2.6.32 SUBDIRS=/var/lib/dkms/aacraid/1.1.5.26400/build modules

```

I now have /var/lib/dkms/aacraid/1.1.5.26400/build/aacraid.ko that I fully expect to work against 2.6.32-generic .. I will also need to build one for 2.6.32-server I bet, but that won't be hard. I already did all the hard stuff...


I am considering purchasing an Adaptec RAID controller but I want to have the module ready to roll so I can load it before I install Ubuntu Server 10.04, so there are no delays.

As a side note, I really hope this DKMS thing does not catch on... why couldn't adaptec just have provided us with a normal makefile? :rolleyes:


EDIT: here is my module, built with Ubuntu Server 10.04 i686


edit 2: oops, forgot to include Module.symvers... here's a fixed one. I do not have the hardware yet, so maybe that is why I get a "no such device" when trying to insert it? Shouldn't you be able to load modules for devices you don't have? I am a linux kernel module noob...

so I did some further investigation, and loading the driver that comes with ubuntu (/lib/modules/2.6.32-generic/kernel/drivers/scsi/aacraid/aacraid.ko) produces no shell output, but does produce the exact thing in dmesg that attempting to load my version does:

Mine:
```

Adaptec aacraid driver 1.1-5[26400]dkms

```
ubuntu:
```

Adaptec aacraid driver 1.1-5[2461]-ms

```

but loading the stock driver does show itself in lsmod, whereas mine does not?

Nevertheless, I am fairly certain that my module will work, I just haven't purchased the card yet to know for sure. Guess there's only one thing left to do...

---

