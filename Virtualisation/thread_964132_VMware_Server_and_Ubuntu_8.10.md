---
title: "VMware Server and Ubuntu 8.10"
date: 2008-10-30
forum: Virtualisation
---

### Post by flainn on 2008-10-30
Hi,

I had VMware server working correctly under 8.04, but today I upgraded to 8.10 and VMware broke. When I try to run "vmware" from the command line, I get:

[FONT="Courier New"]@@PRODUCT_NAME@@ is installed, but it has not been (correctly) configured for the running kernel. To (re-)configure it, invoke the following command: /usr/bin/vmware-config.pl.
[/FONT]

So I run [FONT="Courier New"]sudo /usr/bin/vmware-config.pl[/FONT] and get:

[FONT="Courier New"]
Making sure services for VMware Server are stopped.

Stopping VMware autostart virtual machines:
   Virtual machines                                                   failed
Stopping VMware management services:
   VMware Virtual Infrastructure Web Access
   VMware Server Host Agent                                           failed
Stopping VMware services:
   VMware Authentication Daemon                                        done
   VM communication interface socket family:                           done
   Virtual machine communication interface                             done
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   Host network detection                                              done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                    done

None of the pre-built vmmon modules for VMware Server is suitable for your running kernel.  Do you want this program to try to build the vmmon module for your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running kernel? [/lib/modules/2.6.27-7-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Unknown VMware Server 2.0.0 build 116503 detected. Building for Server 1.0.0.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.27-7-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/./include/x86.h:24,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:53:
/tmp/vmware-config0/vmmon-only/./include/x86paging.h:61:1: warning: "PTE_PFN_MASK" redefined
In file included from include/asm/paravirt.h:7,
                 from include/asm/irqflags.h:55,
                 from include/linux/irqflags.h:57,
                 from include/asm/system.h:11,
                 from include/asm/processor.h:17,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:16:
include/asm/page.h:22:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config0/vmmon-only/linux/vmhost.h:13,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:84:
/tmp/vmware-config0/vmmon-only/./include/compat_semaphore.h:5:27: error: asm/semaphore.h: No such file or directory
/tmp/vmware-config0/vmmon-only/linux/driver.c:171: error: unknown field &#8216;nopage&#8217; specified in initializer
/tmp/vmware-config0/vmmon-only/linux/driver.c:172: warning: initialization from incompatible pointer type
/tmp/vmware-config0/vmmon-only/linux/driver.c:175: error: unknown field &#8216;nopage&#8217; specified in initializer
/tmp/vmware-config0/vmmon-only/linux/driver.c:176: warning: initialization from incompatible pointer type
/tmp/vmware-config0/vmmon-only/linux/driver.c: In function &#8216;__LinuxDriver_Ioctl&#8217;:
/tmp/vmware-config0/vmmon-only/linux/driver.c:1781: error: too many arguments to function &#8216;smp_call_function&#8217;
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please visit our Web site at "http://www.vmware.com/go/unsup-linux-products" and  "http://www.vmware.com/go/unsup-linux-tools".

Execution aborted.

[/FONT]

Wondering if anyone else has run into this. I'm not sure where to go from here.

---

### Post by Jimwin on 2008-10-31
I have the exact same issue.

---

### Post by nnahler on 2008-10-31
Same occurs with VMWare Workstation:

--------------

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.27-7-generic/build/include]                          

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.27-7-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/./include/x86.h:24,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:84:
/tmp/vmware-config0/vmmon-only/./include/x86paging.h:61:1: warning: "PTE_PFN_MASK" redefined
In file included from include/asm/paravirt.h:7,
                 from include/asm/irqflags.h:55,
                 from include/linux/irqflags.h:57,
                 from include/asm/system.h:11,
                 from include/asm/processor.h:17,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:12:
include/asm/page.h:22:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config0/vmmon-only/linux/vmhost.h:13,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:115:
/tmp/vmware-config0/vmmon-only/./include/compat_semaphore.h:5:27: error: asm/semaphore.h: No such file or directory
/tmp/vmware-config0/vmmon-only/linux/driver.c:197: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config0/vmmon-only/linux/driver.c:198: warning: initialization from incompatible pointer type
/tmp/vmware-config0/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config0/vmmon-only/linux/driver.c:1801: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

---------------------

Worked before with 8.04, too. Anybody an idea if any libraries got removed in the update process from 8.04 to 8.10?

---

### Post by downforce on 2008-10-31
Here is the fix:

[http://www.insecure.ws/2008/10/20/vmware-specific-specific-55x-and-kernel-2627](http://www.insecure.ws/2008/10/20/vmware-specific-specific-55x-and-kernel-2627)

I was getting same error w/ Server 1.06 on 8.10 and this fixed it :D

---

### Post by dcabot on 2008-10-31
You have to upgrade to vmware server 2.0.

---

### Post by nnahler on 2008-10-31
Do not attempt the fix mentioned by downforce with VMWare Workstation 6.x. You will get a version mismatch for VMmon.

In my case an update to the most recent version of VMWare Workstation 6.5 fixed the problem (of course requires a license ...) This is stated here: [https://bugs.launchpad.net/ubuntu/+bug/263837]("https://bugs.launchpad.net/ubuntu/+bug/263837")

---

### Post by AreonEpta on 2008-10-31
> **nnahler said:**
> Do not attempt the fix mentioned by downforce with VMWare Workstation 6.x. You will get a version mismatch for VMmon.

In my case an update to the most recent version of VMWare Workstation 6.5 fixed the problem (of course requires a license ...) This is stated here: [https://bugs.launchpad.net/ubuntu/+bug/263837](https://bugs.launchpad.net/ubuntu/+bug/263837)
I'm noticing that VMware Server has been updated as of the 29th. I'm guessing that this was our much needed fix. I'll update here to say whether is works for me out of the box or not.

---

### Post by fjgaude on 2008-10-31
I used "downforce" update with 1.0.7 and Intrepid 8.10 and it worked fine with my old WinXP guest. Great news!

Best to read the **Sticky** on how to do this. It's at the top of this forum.

---

### Post by mrchet on 2008-11-01
Just another option...

I was struggling with VMWare Server 2 after my 8.10 upgrade from 8.04 (where it ran great). I read about the updated build of vmware server and went and downloaded the latest build:

122956

I was previously on a 11XXXX build.

I installed normally but the vsock module would not build. After some googling I found this:

[http://kramfs.com/2008/07/13/vmware-server-2-unable-to-build-the-vsock-modu]("http://kramfs.com/2008/07/13/vmware-server-2-unable-to-build-the-vsock-modu")

I applied the workaround and was able to build my vsock module. Once I restarted the vmware server as directed everything came up and my XP guest is running fine now.

Good luck!

Oh, BTW FWIW I am on 64bit 8.10. I also had to reinstall the Firefox console plugin but that part was painless (just restarted FF after plugin install and I was up and running).

---

### Post by matbroadbent on 2008-11-02
Further to downforce's reply, I found:

[http://ubuntu-tutorials.com/2008/11/01/vmware-server-107-on-ubuntu-810-intrepid-2627-7-generic/](http://ubuntu-tutorials.com/2008/11/01/vmware-server-107-on-ubuntu-810-intrepid-2627-7-generic/)

....a more complete How-To, if you're using VMWare Server 1.0.7.  VMWare is alive and kicking again!

---

### Post by _Poincare on 2008-11-02
I have the same problem however I am running VMWare Fusion. How can I fix this in Fusion? I am not using VMware Server. Help please !! I get the same errors when I run ./vmware-install.pl.  Can anyone help?

---

### Post by drogatoo on 2008-11-02
I am too experiencing the same problem in Vmware Fusion with the vsock module and the fix for server doesn't work.

---

### Post by _Poincare on 2008-11-02
Help please, does anyone know how to fix the open-vm-tools/vm-tools problem so that it will not fubar when it gets to VSOCK?  How can we compile open-vm-tools successfully under VMWare Fusion with Intrepid 8.10??  

I have apt-get install'ed open-vm-tools open-vm-source open-vm-toolbox but none of these helped. I thought Intrepid was STABLE at this point!?  :confused:

---

### Post by The_night on 2008-11-02
I have been searching for something for vmware-tools as well but all I find is this ominous post by vmware.

[http://communities.vmware.com/thread/177150;jsessionid=91B450BDFDDCCF4985A0FC44F1943167?tstart=0](http://communities.vmware.com/thread/177150;jsessionid=91B450BDFDDCCF4985A0FC44F1943167?tstart=0)

---

### Post by _Poincare on 2008-11-02
Yeah ... seems they're not doing much to fix the problem. Makes me feel like we're all driving 10 miles per hour thru 20 miles of orange barrels in a construction zone and at the end is just two guys sitting around doing nothing.....

---

### Post by daladheri on 2008-11-03
I am having the same problem with fusion and it has driven me up the wall. If vmware doesnt get their act together I am gonna fire up virtual box and give vmware the one fingered salute. 

...Anyways

Anyways the vsock module does not want to work after I used the manual build solution 

[http://kramfs.com/2008/07/13/vmware-server-2-unable-to-build-the-vsock-module/](http://kramfs.com/2008/07/13/vmware-server-2-unable-to-build-the-vsock-module/)

I also tried a few other things but it is geared to help vmware server folks. This vsock thing needs fixin bad. :-x

---

### Post by mastabog on 2008-11-05
there are tons of messages about problems with intrepid and vmware regarding vsock and also the vmmouse Xorg driver (which either gets wrong x,y coords or does not seamlessly go from guest to host and vice versa)

I just fixed both issues. I tested it on WS 6.5 but i'm sure it works on all other vmware jun...stuff :)

**1. vsock**: I simply installed the 2.6.24-21 kernel and reconfig'ed vmware tools; this is until vmwre updates their tools. To do that you can add the hardy repository to your apt sources file

/etc/apt/sources.list

```
deb http://archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted
```

then do

```
# apt-get update
# apt-get install linux-image-2.6.24-21-generic linux-headers-2.6.24-21-generic linux-headers-2.6.24-21 linux-restricted-modules-2.6.24-21-generic gcc-4.2
```

you need gcc-4.2 to compile against the 2.4.24-21 headers (it failed when i tried with 4.3). you can remove the hardy repository from the apt sources file at this point. 

then reboot, this time using kernel 2.6.24-21 (i'd make it default in grub's menu.lst) and run these to install vmware tools:

```
# ln -sf gcc-4.2 /usr/bin/gcc
# vmware-config-tools
(it will cmoplain about gcc being 4.2.4 instead of 4.2.3 ... just continue)
# ln -sf gcc-4.3 /usr/bin/gcc
```

voila, vsock now works as long as you use the 2.6.24 kernel


**2. vmmouse**: Bryce Harrington has just fixed the vmmouse driver for Xorg 7.4: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-vmmouse/+bug/285305](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-vmmouse/+bug/285305)

to install it, I added the intrepid-proposed repository to my apt sources

/etc/apt/sources.list

```
deb http://archive.ubuntu.com/ubuntu/ intrepid-proposed main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-proposed main restricted
```

and pinned it accordingly in the apt preferences :P

/etc/apt/preferences

```
Package: xserver-xorg-input-vmmouse
Pin: release a=intrepid-proposed
Pin-Priority: 999

Package: *
Pin: release a=intrepid-proposed
Pin-Priority: 400
```

then just do

```
# apt-get update
# apt-get install xserver-xorg-input-vmmouse
```

and restart your Xorg server (ctrl-alt-backspace for the brutes :D)

this all works fine for me ... i'm not going to fret about not using the newest kernel nor wait for vmware to update their tools

hopefully I haven't missed any important commands

hope this helps

cheers

---

### Post by le_vainqueur on 2008-11-06
2.0 seems to install properly for me, but when I go to run it in a command line I get:

> Launching VMware Web Access using /usr/bin/xdg-open


And a Firefox browser opens up.  What's up with that?

---

### Post by _Poincare on 2008-11-09
I just want to use the standard kernel that comes with 8.10. I don't want to use 8.04, I don't want to mess and fudge around with 300 different patches and old kernel sources. I just want to use the standard kernel in Ubuntu so when their updates are rolled out I can just use software update and won't have to fudge around with finding 300 NEW updates and kooky and crazy messed up patches. 

There was a post on the openSUSE forum and they got vmtools to compile no problem under the same kernel that Ubunutu 8.10 installs. Without messing around with patches or half-arsed semi-updates using old versions. 

I don't see why we users of Ubunutu have to be punished.

---

### Post by veloce on 2008-11-11
> **le_vainqueur said:**
> 2.0 seems to install properly for me, but when I go to run it in a command line I get:



And a Firefox browser opens up.  What's up with that?

That's how vmware server 2 works - the interface is now web based.

---

### Post by veloce on 2008-11-11
I ceased to use the vmware interface to the vm's at about 1.01.  Instead, I think of all the vms as headless and use a remote tool to access them.  

For windows I use rdp (gnome-rdp is an easy interface).
For Ubuntu I use xdmcp.

This way I only use the vmware interface for setting them up to allow remote access.  The klunky non-vmware-tools version is fine for this (so long as you are only doing it once).

---

### Post by glends on 2008-11-12
After upgrading from 8.04 to 8.10 all my VM's freeze the CPU.

Tried installing the latest VMWare Server (2.0.0 Build 122956). It installs fine, and I even tried starting from scratch by removing all VM files except the vmdk's and recreating the whole VM inventory... no luck, the VM's still hog 100% CPU and just freeze :confused:

Anyone experiencing the same problems?

---

### Post by brinktastee on 2008-11-13
> **glends said:**
> After upgrading from 8.04 to 8.10 all my VM's freeze the CPU.

Tried installing the latest VMWare Server (2.0.0 Build 122956). It installs fine, and I even tried starting from scratch by removing all VM files except the vmdk's and recreating the whole VM inventory... no luck, the VM's still hog 100% CPU and just freeze :confused:

Anyone experiencing the same problems?
I have the same problem running the latest version of vmware workstation 6.5 64bit latest build. The system just locks for several seconds even up to a minute. If you wait long enough it will unfreeze. ](*,)
It worked fine in Ubuntu 8.04.

---

### Post by Bobby G on 2008-12-11
Hi all, I hope this helps: here's the steps I used to get VMware server 1.0.8 running on Intrepid 8.10:

Install required packages:
    sudo apt-get install build-essential linux-headers-`uname -r` xinetd linux-source-2.6.27 linux-libc-dev

Install VMware
    tar -xvzf VMware-server-1.0.8-126538.tar.gz
    cd vmware-server-distrib/
    ./vmware-install.pl
    Say yes to every question BUT when asked to run the config script say NO

Patch the kernel module

Tested with 2.6.27-9-generic (2.6.27-7-generic & worked too I understand) from here: http://www.insecure.ws/warehouse/vmware-update-2.6.27-5.5.7-2.tar.gz

    tar -xvzf vmware-update-2.6.27-5.5.7-2.tar.gz
    cd vmware-update-2.6.27-5.5.7-2
    ./runme.pl
    Say yes to everything & press enter to use the default settings.

---

### Post by skamithi on 2009-01-15
I got vmware server to install using "make-vmpkg" and kernel 2.6.27-9-generic cause I wanted to create deb files for everything. created the vmware-server, vmware-kernel-module and vmware-server-console debs.

instructions can be found @ [kenyangeekblogspot.com]("http://kenyangeekboy.blogspot.com")

---

