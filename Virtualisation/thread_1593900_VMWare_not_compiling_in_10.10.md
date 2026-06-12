---
title: "VMWare not compiling in 10.10"
date: 2010-10-11
forum: Virtualisation
---

### Post by jon.reeve on 2010-10-11
I haven't been able to get VMWare to work with Maverick. I downloaded the latest vmware player (3.1.2) and ran the installer, but every time it tries to compile the kernel modules it exits with this error: 

```
Oct 11 21:07:48.648: app-140674097211136| Log for VMware Workstation pid=7334 version=7.1.2 build=build-301548 option=Release
Oct 11 21:07:48.648: app-140674097211136| The process is 64-bit.
Oct 11 21:07:48.648: app-140674097211136| Host codepage=UTF-8 encoding=UTF-8
Oct 11 21:07:48.648: app-140674097211136| Logging to /tmp/vmware-root/setup-7334.log
Oct 11 21:07:48.936: app-140674097211136| modconf query interface initialized
Oct 11 21:07:48.937: app-140674097211136| modconf library initialized
Oct 11 21:07:48.983: app-140674097211136| Your GCC version: 4.4
Oct 11 21:07:48.994: app-140674097211136| Your GCC version: 4.4
Oct 11 21:07:49.009: app-140674097211136| Your GCC version: 4.4
Oct 11 21:07:49.028: app-140674097211136| Your GCC version: 4.4
Oct 11 21:07:49.042: app-140674097211136| Your GCC version: 4.4
Oct 11 21:07:49.087: app-140674097211136| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 11 21:07:49.091: app-140674097211136| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 11 21:07:49.094: app-140674097211136| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 11 21:07:49.099: app-140674097211136| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 11 21:07:49.102: app-140674097211136| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 11 21:07:49.135: app-140674097211136| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 11 21:07:49.139: app-140674097211136| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 11 21:07:49.143: app-140674097211136| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 11 21:07:49.147: app-140674097211136| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 11 21:07:49.151: app-140674097211136| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 11 21:07:49.161: app-140674097211136| Your GCC version: 4.4
Oct 11 21:07:49.177: app-140674097211136| Your GCC version: 4.4
Oct 11 21:07:49.255: app-140674097211136| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 11 21:07:49.259: app-140674097211136| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 11 21:07:49.263: app-140674097211136| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 11 21:07:49.266: app-140674097211136| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 11 21:07:49.270: app-140674097211136| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 11 21:07:49.278: app-140674097211136| Your GCC version: 4.4
Oct 11 21:07:49.316: app-140674097211136| Your GCC version: 4.4
Oct 11 21:07:49.430: app-140674097211136| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 11 21:07:49.434: app-140674097211136| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 11 21:07:49.438: app-140674097211136| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 11 21:07:49.442: app-140674097211136| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 11 21:07:49.446: app-140674097211136| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 11 21:07:50.350: app-140674097211136| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 11 21:07:50.351: app-140674097211136| Building module vmmon.
Oct 11 21:07:50.351: app-140674097211136| Extracting the sources of the vmmon module.
Oct 11 21:07:50.424: app-140674097211136| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-bui
ld SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.35-22-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.5
Oct 11 21:08:02.020: app-140674097211136| Failed to compile module vmmon!

```

Has anyone had any success in compiling VMWare on 10.10? If so, are there any tricks to accomplishing this?

---

### Post by xyexz on 2010-10-12
Hey there, I had the same issue with my vmware player and found this link via the google :D

[http://www.rrfx.net/2010/06/vmware-vmmon-module-compilation-issues.html]("http://www.rrfx.net/2010/06/vmware-vmmon-module-compilation-issues.html")

Commands you need to run extracted from above link:

[PHP]cd /tmp
tar xvf /usr/lib/vmware/modules/source/vmmon.tar -C /tmp
perl -pi -e 's,_range,,' vmmon-only/linux/iommu.c
tar cvf /usr/lib/vmware/modules/source/vmmon.tar vmmon-only[/PHP]

The writer also has a fix that allows you to stop vmware from recompiling everytime you launch vmware, I've not tried it yet as it's not that big a deal and also it could break other things.

The whole issue resides in the new kernel that Maverick uses has had functions renamed that the vmware source files use, thus being the reason gcc craps out when it can't build against the non-existent functions.

Why oh why to programmers lot refactoring code to make life miserable for the rest of us?  As a programmer myself I can safely say... "because it's fun!"

---

### Post by calixtine on 2010-10-13
Find a fix here [http://www.debuntu.org/how-wmware-workstation-7.1-ubuntu-maverick-meerkat-10.10]("http://www.debuntu.org/how-wmware-workstation-7.1-ubuntu-maverick-meerkat-10.10")

if you have problems with compiling the VMCI Socket module, you'll know because vmware will ask to recompile every time you launch it.

---

### Post by fjgaude on 2010-10-13
Thanks to all for showing how to run Player in 10.10.

Now, the VMCI Sockets, is there any downside to not compiling them?

---

### Post by skrangama on 2010-10-14
[SIZE=3]I also ran into the same issue but finally fixed it. Here are what I did in order to VMWare Workstation 7.1.2 build-301548 to get work in my newly install Ubuntu 10.10 (maverick merrcat) 64bit machine.
[/SIZE]

[SIZE=5]Do these things...
[/SIZE][SIZE=3][COLOR=Green]cd /tmp
wget [http://www.sputnick-area.net/scripts/vmware7.1.1-patch-kernel-2.6.35.bash](http://www.sputnick-area.net/scripts/vmware7.1.1-patch-kernel-2.6.35.bash)
sudo chmod +x vmware7.1.1-patch-kernel-2.6.35.bash
sudo ./vmware7.1.1-patch-kernel-2.6.35.bash
[/COLOR][/SIZE][SIZE=5]
The script will say...
[SIZE=3]
[/SIZE][/SIZE][SIZE=3]sudo vmware-modconfig --console --install-all[/SIZE]


[SIZE=5]Then...[/SIZE]
[SIZE=5]
start the VMWare workstation as usual from...
 [SIZE=4][COLOR=Blue]Applications > System Tools > VMWare Workstation

[COLOR=Black]OK that's it :)
Enjoy Virtualization....
[/COLOR][/COLOR][/SIZE][/SIZE]

---

### Post by Evil Dax on 2010-10-15
Thanks skrangama,
That did the trick!
:-)

---

### Post by Chrison999 on 2010-10-15
> **xyexz said:**
> Hey there, I had the same issue with my vmware player and found this link via the google :D

[http://www.rrfx.net/2010/06/vmware-vmmon-module-compilation-issues.html](http://www.rrfx.net/2010/06/vmware-vmmon-module-compilation-issues.html)



The instructions at this link worked for me.  You saved my bacon!  Thanks! :smile:

> **xyexz said:**
> 
Why oh why to programmers lot refactoring code to make life miserable for the rest of us?  As a programmer myself I can safely say... "because it's fun!"

I'm not a programmer, but I'm a project manager who works with programmers.  So, as an end-user I say "Shame on you!" but with my PM hat on I say "Yeah, it *is* fun, isn't it!?!?"  \\:D/ :lolflag:

Thanks again...

Regards,

Chris

---

### Post by f-schaefer on 2010-10-27
> **calixtine said:**
> Find a fix here [http://www.debuntu.org/how-wmware-workstation-7.1-ubuntu-maverick-meerkat-10.10]("http://www.debuntu.org/how-wmware-workstation-7.1-ubuntu-maverick-meerkat-10.10")

if you have problems with compiling the VMCI Socket module, you'll know because vmware will ask to recompile every time you launch it.

Works great.

---

### Post by albertwt on 2010-10-27
thanks Guys, you are great.

Initially my installation is always failing eventhough i already executed ```
sudo apt-get install build-essential linux-headers-`uname -r`

```



Cheers,

Albert

---

### Post by ksnyders26 on 2011-07-12
> **xyexz said:**
> Hey there, I had the same issue with my vmware player and found this link via the google :D

[http://www.rrfx.net/2010/06/vmware-vmmon-module-compilation-issues.html](http://www.rrfx.net/2010/06/vmware-vmmon-module-compilation-issues.html)

Commands you need to run extracted from above link:

[PHP]cd /tmp
tar xvf /usr/lib/vmware/modules/source/vmmon.tar -C /tmp
perl -pi -e 's,_range,,' vmmon-only/linux/iommu.c
tar cvf /usr/lib/vmware/modules/source/vmmon.tar vmmon-only[/PHP]The writer also has a fix that allows you to stop vmware from recompiling everytime you launch vmware, I've not tried it yet as it's not that big a deal and also it could break other things.

The whole issue resides in the new kernel that Maverick uses has had functions renamed that the vmware source files use, thus being the reason gcc craps out when it can't build against the non-existent functions.

Why oh why to programmers lot refactoring code to make life miserable for the rest of us?  As a programmer myself I can safely say... "because it's fun!"

This worked perfect.  Thanks.

---

### Post by northd_tech on 2011-09-06
I just tried to build VMWare Tools from a source "vmware-tools-distrib" that I got from an .ISO from VMware's website and got the following results:

> **sudo ./vmware-install.pl **
[sudo] password for *user*: 
Creating a new VMware Tools installer database using the tar4 format.

Installing VMware Tools.

In which directory do you want to install the binary files? 
[/usr/bin] 

What is the directory that contains the init directories (rc0.d/ to rc6.d/)? 
[/etc] 

What is the directory that contains the init scripts? 
[/etc/init.d] 

In which directory do you want to install the daemon files? 
[/usr/sbin] 

In which directory do you want to install the library files? 
[/usr/lib/vmware-tools] 

The path "/usr/lib/vmware-tools" does not exist currently. This program is 
going to create it, including needed parent directories. Is this what you want?
[yes] 

In which directory do you want to install the documentation files? 
[/usr/share/doc/vmware-tools] 

The path "/usr/share/doc/vmware-tools" does not exist currently. This program 
is going to create it, including needed parent directories. Is this what you 
want? [yes] 

The installation of VMware Tools 8.6.0 build-425873 for Linux completed 
successfully. You can decide to remove this software from your system at any 
time by invoking the following command: "/usr/bin/vmware-uninstall-tools.pl".

Before running VMware Tools for the first time, you need to configure it by 
invoking the following command: "/usr/bin/vmware-config-tools.pl". Do you want 
this program to invoke the command for you now? [yes] 

Initializing...

This configuration program is to be executed in a virtual machine.

Execution aborted.

I can't seem to get a GUI or vmware-toolbox running (but it looks like most of the programs are in /usr/bin/ )

Here are some links to VMWare downloads:

[http://www.vmware.com/products/server/overview.html](http://www.vmware.com/products/server/overview.html)

[https://www.vmware.com/tryvmware/?p=vmware-vsphere5-ent&lp=1&cid=70180000000wMmf](https://www.vmware.com/tryvmware/?p=vmware-vsphere5-ent&lp=1&cid=70180000000wMmf)

---

