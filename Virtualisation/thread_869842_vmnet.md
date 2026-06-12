---
title: "vmnet"
date: 2008-07-25
forum: Virtualisation
---

### Post by Norfolk 'n' Good on 2008-07-25
Hi,

I am trying to install vmware workstation 6 onto Hardy and keep getting to this... 

```
Extracting the sources of the vmnet module.

Building the vmnet module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config3/vmnet-only'
make -C /lib/modules/2.6.24-19-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /tmp/vmware-config3/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config3/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config3/vmnet-only/userif.o
  CC [M]  /tmp/vmware-config3/vmnet-only/netif.o
  CC [M]  /tmp/vmware-config3/vmnet-only/bridge.o
/tmp/vmware-config3/vmnet-only/bridge.c: In function ‘VNetBridgeDevCompatible’:
/tmp/vmware-config3/vmnet-only/bridge.c:278: error: implicit declaration of function ‘dev_net’
/tmp/vmware-config3/vmnet-only/bridge.c: In function ‘VNetBridgeUp’:
/tmp/vmware-config3/vmnet-only/bridge.c:903: warning: passing argument 1 of ‘__dev_get_by_name’ makes pointer from integer without a cast
/tmp/vmware-config3/vmnet-only/bridge.c:941: warning: passing argument 1 of ‘sk_alloc’ makes pointer from integer without a cast
make[2]: *** [/tmp/vmware-config3/vmnet-only/bridge.o] Error 1
make[1]: *** [_module_/tmp/vmware-config3/vmnet-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [vmnet.ko] Error 2
make: Leaving directory `/tmp/vmware-config3/vmnet-only'
Unable to build the vmnet module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

I don't know what to do, so any help would be greatly appreciated.

Thanks:confused:

---

### Post by billgoldberg on 2008-07-25
I'm not familiar with vmware server, but is there a reason you can't use virtual box?

I found it to be much better.

---

### Post by scooper71 on 2008-07-29
I have the exact same problem when trying to install VMware Server 1.0.6

Building the vmnet module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config2/vmnet-only'
make -C /lib/modules/2.6.24-19-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /tmp/vmware-config2/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config2/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config2/vmnet-only/userif.o
  CC [M]  /tmp/vmware-config2/vmnet-only/netif.o
  CC [M]  /tmp/vmware-config2/vmnet-only/bridge.o
/tmp/vmware-config2/vmnet-only/bridge.c: In function ‘VNetBridgeDevCompatible’:
/tmp/vmware-config2/vmnet-only/bridge.**c:278: error: implicit declaration of function ‘dev_net’**
/tmp/vmware-config2/vmnet-only/bridge.c: In function ‘VNetBridgeUp’:
/tmp/vmware-config2/vmnet-only/bridge.c:903: warning: passing argument 1 of ‘__dev_get_by_name’ makes pointer from integer without a cast
/tmp/vmware-config2/vmnet-only/bridge.c:941: warning: passing argument 1 of ‘sk_alloc’ makes pointer from integer without a cast
make[2]: *** [/tmp/vmware-config2/vmnet-only/bridge.o] Error 1
make[1]: *** [_module_/tmp/vmware-config2/vmnet-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [vmnet.ko] Error 2
make: Leaving directory `/tmp/vmware-config2/vmnet-only'
Unable to build the vmnet module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.


I found a patch ( [http://vmkernelnewbies.googlegroups.com/web/vmware-any-any-update117c.tar.gz](http://vmkernelnewbies.googlegroups.com/web/vmware-any-any-update117c.tar.gz) ) but this doesn't resolve the problem.

I'm stuck! Any ideas on this one?

---

### Post by kdb424 on 2008-07-29
I recommend Virtualbox too. Support open source! And it's better.

---

### Post by El Conquistador on 2008-07-29
> **kdb424 said:**
> I recommend Virtualbox too. Support open source! And it's better.

Virtualbox for the WIN!

---

### Post by bodhi.zazen on 2008-07-29
At the risk fo starting a flame war, vmware has a few features over vbox including support for 64 bit guests and bridging wireless network cards, lol

VBox is nice too and has some cool features lacking in VMWare.

At any rate, see this thread :

[How to VMWare in Ubuntu 8.04 - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=779934")

---

### Post by fjgaude on 2008-07-29
> **bodhi.zazen said:**
> At the risk fo starting a flame war, vmware has a few features over vbox including support for 64 bit guests and bridging wireless network cards, lol

VBox is nice too and has some cool features lacking in VMWare.

At any rate, see this thread :

[How to VMWare in Ubuntu 8.04 - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=779934")

Say, can you tell us what are the cool features that VBox has?

BTW, should you not give credit for your tagline quotation, to Archbishop Desmond Tutu, 1999? Seems the right thing to do, eh? Or am I wrong in thinking it comes from the good Archbishop? <smile>

---

### Post by bodhi.zazen on 2008-07-29
> **fjgaude said:**
> Say, can you tell us what are the cool features that VBox has?

To be honest I do not use VBox as much these days so I may not be as up to date.

Some things I like about vbox are: I like that there is an open source edition. The clipboard mouse integration works quite well and they have a RDP server built in.

Nowadays I use openvz, kvm, and vmware server. kvm is quite easy if you are familiar with qemu, otherwise the gui tools are a little lacking ... IMO.

> BTW, should you not give credit for your tagline quotation, to Archbishop Desmond Tutu, 1999? Seems the right thing to do, eh? Or am I wrong in thinking it comes from the good Archbishop? <smile>Done, w/ linkage.

---

### Post by axel1973 on 2008-09-14
> **kdb424 said:**
> I recommend Virtualbox too. Support open source! And it's better.

Does VirtualBox comes with a bridging driver so u can install virtual servers , OUT OF THE BOX ?

Does VirtualBox runs as "Service" in the background when system boots up (OUT OF THE BOX) ??

Does VirtualBox autostart several virtual machines ? (guests) OOTB ?

Why VirtualBox ***** up on my fresh installed ubuntu desktop with 10 different error messages about missing dependencies, missing permissions (group membershit) and even after fixing all this it STILL is not working ?!

VirtualBox comes packaged for ubuntu... i preciate that.. but it still isnt working out of the box. and that realy sucks!

---

### Post by lronclawbigun on 2008-09-15
Now today we discuss the game of warhammer online. Warhammer online is the full name of this game ,warhammer always abbreviation of war ,so [warhammer power leveling](http://www.item4u.com/Warhammer-Online/Power-Leveling) often called war power leveling, and in fact. All war power leveling , [war power leveling](http://www.item4u.com/Warhammer-Online/Power-Leveling), [warhammer online power leveling](http://www.item4u.com/Warhammer-Online/Power-Leveling) is the same meaning ,so here not to puzzle with this.firstly ,when you want  [Warhammer cd key](http://www.item4u.com/bestSelling-CDKey/Warhammer-Online-CDKey),i suggest you go to gamevive.com. They sell the lowest price for warhammer gold and other [warhammer online cd key](http://www.item4u.com/bestSelling-CDKey/Warhammer-Online-CDKey) .and their delivery  is fastest.it is worth to try.

---

### Post by herald on 2008-10-19
Does anyone have a fix for this?  Did the Original Poster notice if this got fixed by anything in the VMware install guide thread?  I've seen this before, and I had to go in and modify something in the code somewhere, but I can't find any references to that original article.  Basically, this is one of the reasons people keep rolling out new versions of the vmware-any-any patches.  Unfortunately, there is not a new patch out yet...

---

### Post by bodhi.zazen on 2008-10-19
> **herald said:**
> Does anyone have a fix for this?  Did the Original Poster notice if this got fixed by anything in the VMware install guide thread?  I've seen this before, and I had to go in and modify something in the code somewhere, but I can't find any references to that original article.  Basically, this is one of the reasons people keep rolling out new versions of the vmware-any-any patches.  Unfortunately, there is not a new patch out yet...

The "fix" as far as I know is to follow the sticky I referenced. There have been a number of changes with VMware and Ubuntu in the last few months, but I have not heard that the sticky is not working.

I will re-do a VMware and probably VBox sticky with 8.10 (new versions all around) ;)

---

### Post by herald on 2008-10-19
> **bodhi.zazen said:**
> The "fix" as far as I know is to follow the sticky I referenced. There have been a number of changes with VMware and Ubuntu in the last few months, but I have not heard that the sticky is not working.

I will re-do a VMware and probably VBox sticky with 8.10 (new versions all around) ;)

Well unfortunately, those instructions don't work with the latest version of VMware Server and the latest version of the kernel (2.6.24-21-server is what I'm using)  See this thread for a few more details.
[http://ubuntuforums.org/showthread.php?t=952784]("http://ubuntuforums.org/showthread.php?t=952784")

---

### Post by bodhi.zazen on 2008-10-19
> **herald said:**
> Well unfortunately, those instructions don't work with the latest version of VMware Server and the latest version of the kernel (2.6.24-21-server is what I'm using)  See this thread for a few more details.
[http://ubuntuforums.org/showthread.php?t=952784](http://ubuntuforums.org/showthread.php?t=952784)

On your thread you state you are using the any-any update. This is not the same as the sticky which does not use the any-any update.

I suggest you download or untar a new copy of vmware and do not use the any-any update ;)

---

### Post by herald on 2008-10-19
> **bodhi.zazen said:**
> On your thread you state you are using the any-any update. This is not the same as the sticky which does not use the any-any update.

I suggest you download or untar a new copy of vmware and do not use the any-any update ;)

Indeed you are correct, sir.  I did a full and manual uninstall, ran through the installer (with all correct kernel headers installed this time) and everything went like cake.  Thanks for the help!

---

### Post by bodhi.zazen on 2008-10-19
> **herald said:**
> Indeed you are correct, sir.  I did a full and manual uninstall, ran through the installer (with all correct kernel headers installed this time) and everything went like cake.  Thanks for the help!

You are most welcome, and thank you for the feedback (nice to see what works and what does not. Recently I have seen then any-any update cause issues and FYI wireless bridging works if you do not use the any-any update).

---

