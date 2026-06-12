---
title: "VMware Server failure to launch; seeking error interpretations"
date: 2009-07-19
forum: Virtualisation
---

### Post by sgstrayer on 2009-07-19
I am attempting to install, configure and use VMware Server 1.0.9 on my laptop which has the following specifications.

Ubuntu 8.04 Hardy Heron, Gnome 2.22.3
Kernal: Linux 2.6.24.24-generic, compiled on: gcc version 4.2.4
Dell Laptop: Inspiron 1420, Intel Core 2 Duo T250 @ 1.5 GHZ

I consider myself to have a very marginal skill set for this project, but I have previously had some success with VMware Server on this same computer, thanks to this forum in general, and to Bodhi Zazen's stickies in particular.  Before going any further I would like to first apologize for the length of this post.   

I suspect my working VM Server installations in the past have been broken by my naively allowing newer versions of the gcc (gnu C compiler?) to be put on my machine.  Now I have decided to try to stick to the Long Term Stable (LTS) releases of Ubuntu and ignore any future proposed gcc updates.  By the by, I believe I cannot use Virtual Box or KVM because my investigations have led me to believe that my CPU does not have the requisite virtualization support features. 

After doing the install and configuration processes I get the following message: 

[INDENT]The configuration of VMware Server 1.0.9 build-156507 for Linux for this running kernel completed successfully.[/INDENT]

When I attempt to launch VM Server the following messages return: 

sgstrayer@Radegonde:~/src/VMWare/vmware-server-distrib$ sudo vmware

[INDENT]/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)[/INDENT]

Following these error messages, I looked to see if I could find the gcc 3.4 and gcc 4.2.0. Which I did, as you can verify for yourself two paragraphs below although I am not sure these gcc's are where they need to be in order for vmware to make use of them.

At this point I am stuck and am seeking some pointers/insight.  

What I have appended below is basically a record of my terminal as I attempted the install and configuration.  I have included it for completeness, but I hope some wise benefactor will be able to point me in the right direction from what they have seen above without having to read through all that follows below.  An additional and probably minor detail is that even though the configuration script claims that the program is configured, the little VMware launch icon never appeared in my Applications pull-down-menu on the menu bar at the top of my Gnome desktop whereas on my previous installs, this feature had always been present.  When I attempt to add the VMserver application to my menu bar; the list of available applications does not offer VMware Server as a choice.

 

sgstrayer@Radegonde:~/src/VMWare/vmware-server-distrib$ ls [INDENT]/usr/bin/gcc*
/usr/bin/gcc  /usr/bin/gcc-3.4  /usr/bin/gcc-4.2  /usr/bin/gccbug-3.4  /usr/bin/gccmakedep[/INDENT]

So I believe the gcc 3.4 and gcc 4.2.0 are present and accounted for despite the error messages.  

So the actual record of my install, configure, and run process starts here after I made sure there are no conflicts with stray VMware fragments leftover from my previous installation attempts by running a /usr/bin/vmware-uninstall.pl script.  It returned.

[INDENT]The removal of VMware Server 1.0.9 build-156507 for Linux completed 
successfully. Thank you for having tried this software.
[/INDENT]

I also wanted to check that the update is available in the same directory as the install.pl script, so

sgstrayer@Radegonde:~/src/VMWare/vmware-server-distrib$ ls
[INDENT]bin  doc  etc  FILES  installer  lib  man  sbin  vmware-install.pl  vmware-update-2.6.27-5.5.7-2  vmware-vix
[/INDENT]

Next I launched the installer proper, and away we go. . .

sgstrayer@Radegonde:~/src/VMWare/vmware-server-distrib$ sudo ./vmware-install.pl

Creating a new installer database using the tar3 format.

Installing the content of the package.

In which directory do you want to install the binary files? 
[/usr/bin] 

What is the directory that contains the init directories (rc0.d/ to rc6.d/)? 
[/etc] 

What is the directory that contains the init scripts? 
[/etc/init.d] 

In which directory do you want to install the daemon files? 
[/usr/sbin] 

In which directory do you want to install the library files? 
[/usr/lib/vmware] 

The path "/usr/lib/vmware" does not exist currently. This program is going to 
create it, including needed parent directories. Is this what you want? 
[yes] 

In which directory do you want to install the manual files? 
[/usr/share/man] 

In which directory do you want to install the documentation files? 
[/usr/share/doc/vmware] 

The path "/usr/share/doc/vmware" does not exist currently. This program is 
going to create it, including needed parent directories. Is this what you want?
[yes] 

The installation of VMware Server 1.0.9 build-156507 for Linux completed 
successfully. You can decide to remove this software from your system at any 
time by invoking the following command: "/usr/bin/vmware-uninstall.pl".

Before running VMware Server for the first time, you need to configure it by 
invoking the following command: "/usr/bin/vmware-config.pl". Do you want this 
program to invoke the command for you now? [yes] 

Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done

**EULA happened here. Removed for brevity**

Do you accept? (yes/no) y

Thank you.

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons? 
[/usr/share/icons] 

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] 

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

/usr/share/applications/vmware-server.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
/usr/share/applications/vmware-console-uri-handler.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.24-24-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.24-24-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-24-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/task.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmx86.o
/tmp/vmware-config0/vmmon-only/common/vmx86.c: In function ‘Vmx86_GetkHzEstimate’:
/tmp/vmware-config0/vmmon-only/common/vmx86.c:1899: warning: passing argument 4 of ‘Div643264’ from incompatible pointer type
/tmp/vmware-config0/vmmon-only/common/vmx86.c:1908: warning: passing argument 4 of ‘Div643232’ from incompatible pointer type
  CC [M]  /tmp/vmware-config0/vmmon-only/vmcore/moduleloop.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config0/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-24-generic'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
The module loads perfectly in the running kernel.

Do you want networking for your virtual machines? (yes/no/help) [yes] 

Configuring a bridged network for vmnet0.

Your computer has multiple ethernet network interfaces available: eth0, 
eth0:avahi, wlan0. Which one do you want to bridge to vmnet0? [eth0] 

The following bridged networks have been defined:

. vmnet0 is bridged to eth0

Do you wish to configure another bridged network? (yes/no) [no] 

Do you want to be able to use NAT networking in your virtual machines? (yes/no)
[yes] 

Configuring a NAT network for vmnet8.

Do you want this program to probe for an unused private subnet? (yes/no/help) 
[yes] 

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.98.0/255.255.255.0 appears to be unused.

The following NAT networks have been defined:

. vmnet8 is a NAT network on private subnet 172.16.98.0.

Do you wish to configure another NAT network? (yes/no) [no] 

Do you want to be able to use host-only networking in your virtual machines? 
[yes] 

Configuring a host-only network for vmnet1.

Do you want this program to probe for an unused private subnet? (yes/no/help) 
[yes] 

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.220.0/255.255.255.0 appears to be unused.

The following host-only networks have been defined:

. vmnet1 is a host-only network on private subnet 172.16.220.0.

Do you wish to configure another host-only network? (yes/no) [no] 

Extracting the sources of the vmnet module.

Building the vmnet module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmnet-only'
make -C /lib/modules/2.6.24-24-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-24-generic'
  CC [M]  /tmp/vmware-config0/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config0/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config0/vmnet-only/userif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/netif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/bridge.o
  CC [M]  /tmp/vmware-config0/vmnet-only/procfs.o
  CC [M]  /tmp/vmware-config0/vmnet-only/smac_compat.o
  SHIPPED /tmp/vmware-config0/vmnet-only/smac_linux.x386.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /tmp/vmware-config0/vmnet-only/.smac_linux.x386.o.cmd for /tmp/vmware-config0/vmnet-only/smac_linux.x386.o
  CC      /tmp/vmware-config0/vmnet-only/vmnet.mod.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-24-generic'
cp -f vmnet.ko ./../vmnet.o
make: Leaving directory `/tmp/vmware-config0/vmnet-only'
The module loads perfectly in the running kernel.

Please specify a port for remote console connections to use [902] 

 * Stopping internet superserver xinetd                                                                           [ OK ] 
 * Starting internet superserver xinetd                                                                           [ OK ] 
Configuring the VMware VmPerl Scripting API.

Building the VMware VmPerl Scripting API.

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

Installing the VMware VmPerl Scripting API.

The installation of the VMware VmPerl Scripting API succeeded.

Generating SSL Server Certificate

In which directory do you want to keep your virtual machine files? 
[/var/lib/vmware/Virtual Machines] 

The path "/var/lib/vmware/Virtual Machines" does not exist currently. This 
program is going to create it, including needed parent directories. Is this 
what you want? [yes] 

Do you want to enter a serial number now? (yes/no/help) [no] y

Please enter your 20-character serial number.

Type XXXXX-XXXXX-XXXXX-XXXXX or 'Enter' to cancel:  YYYYY-YYYYY-YYYYY-YYYYY 

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                   done
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                          done

[B]The configuration of VMware Server 1.0.9 build-156507 for Linux for this 
running kernel completed successfully.
[/B]
**Bold added by me for emphasis.  Now I tried to launch, and got the following errors, which for convenience, I have already posted near the top.**

sgstrayer@Radegonde:~/src/VMWare/vmware-server-distrib$ sudo vmware
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

sgstrayer@Radegonde:~/src/VMWare/vmware-server-distrib$ ls /usr/bin/gcc*
/usr/bin/gcc  /usr/bin/gcc-3.4  /usr/bin/gcc-4.2  /usr/bin/gccbug-3.4  /usr/bin/gccmakedep

If anyone's still here, thank you for your remarkable patience and consideration.

-Scott****

---

### Post by monkeymac on 2010-02-10
Hi Scott.

Not sure if you've moved on, but. . .

 I'd say you do *not* in fact have gcc-4.2.0 (Hardy uses 4.2.4). Your evidence

```
$ ls/usr/bin/gcc*
/usr/bin/gcc  /usr/bin/gcc-3.4  /usr/bin/gcc-4.2  /usr/bin/gccbug-3.4  /usr/bin/gccmakedep
```is inconclusive: "gcc-4.2" is not "gcc-4.2.0" (you can't just drop the trailing .0 in the version number as you might with an ordinary decimal number).

To find out what version of gcc you have, use this:```
$ gcc --version
```For example, I get this:

```
$ ls /usr/bin/gcc*
/usr/bin/gcc  /usr/bin/gcc-4.2  /usr/bin/gccmakedep
$ gcc --version
gcc (GCC) 4.2.4 (Ubuntu 4.2.4-1ubuntu4) . . . 
```*ls* is not reporting the minor version number (the .4 at the end)

Unfortunately (for you), vmware is being particular about this detail, explicitly requiring 4.2.0 and not accepting 4.2.4.

Happily, there's a fix that should get you up and running. Check out Section 6.4.13 of [http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron-p5](http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron-p5)

 I was getting similar same errors until I applied their "last resort" symlink:

```
$ sudo ln -sf /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1
```This replaces vmware's verson of libgcc_s.so.1 (the location of the problematic code) with one that'll play nicely with gcc-4.2.4. [ Thanks to Oliver Meyer at howtoforge.com for the symlink. ]


[ Of course I'm assuming that this is not a critical procuction system you're building--there might conceivably be good reasons why vmware won't accept gcc-4.2.4 The correct thing to do would be to use a newer version of vmware; I chose  the approach here for a quick fix at home (at the wrong end of a painfully slow ISP) ]

Cheers,

Peter.

---

### Post by sgstrayer on 2010-03-24
Peter,

I have studied your reply and it certainly looks very promising.  Thank you so much for your trouble.  I notice that before posting you had just joined the forum, and that it was your first, and to date, only posting.  All of which makes me feel all the worse for my lagitude in thanking you.

Unfortunately, I cannot even report to you that I applied your suggestion because by the time of your post I had in fact already moved on, as you put it.  I had given up on VMWare and found QEMU which I was able to install and use (and still use) successfully to run my licensed Win XP copy on my Ubuntu/Linux/GNU laptop.

All that is kind of beside the point here where I simply want to recognise your effort and again extend my appreciation to you; as well as, to the forum and its administrators and contributors.
 
Best,

Scott

---

