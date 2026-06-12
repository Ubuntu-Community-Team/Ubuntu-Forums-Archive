---
title: "vmware wireless network"
date: 2007-10-12
forum: Virtualisation
---

### Post by akkad on 2007-10-12
i have 2 Ethernet cards on my laptop wired and wireless, i configured vmware workstation to bridge the network on the wired network where it went fine, but when i bridge the wireless network i cant access it in the vmware, any idea?

---

### Post by akkad on 2007-10-13
no answer ??

---

### Post by knightluo on 2007-10-21
I have the same probolem, where after I install the vmware-tools, my bridged network would not work.
I want to know the reason, too.

---

### Post by c9ops on 2007-11-13
I also have the exact same trouble currently.  I have noticed from some other similar posts that we might could use NAT instead of BRIDGE mode.  

I would prefer not to do that, and have an isolated IP address for the virtual machine (XP).  So I am not really wanting to take that route, but I can see where using NAT mode should work.

I'm thinking the problem lies in VMware using the host OS (ubuntu) eth0 port instead of the wireless port. I am not versed enough in linux and ubuntu 'yet' to know how to make the host use 'whatever interface is active' or to specify 'wi0'.  I'm thinking that if possible, this would be the first place to make the host VMWare use that interface path.  So it is either a linux/ubuntu coding update needed here or a coding update to VMWare to make it use a certain interface or whatever interface is active.

Much thanks for your time in reading this and HUGE thanks to the person who supplies the answers :)

---

### Post by Ctrl+Alt+Del on 2007-11-14
Your guess is right. I was having the same problem with my Desktop running Gentoo and Vmware WS 5.5. Ethernet for my vmware was bridged to eth0. When only eth1 was connected vmware didn't recognize that fact. On my Desktop i could simply rerun vmware-config.pl and add a second bridged interface and use that as via the "custom" option. Unfortunately this doesn't work on my new Notebook running Ubuntu and Vmware WS 6. I'm still trying to find out what's going wrong there. Will keep you guys updated...

Currently it looks like this:
The following bridged networks have been defined:

. vmnet0 is bridged to eth0
. vmnet2 is bridged to eth1

should work, unfortunately it does not

---

### Post by c9ops on 2007-11-14
I have been doing a lot of searching on this issue.  Here are some of the things I have found:


- VMWare Player will allow for Bridge mode on the Guest OS through a Wireless NIC on the Host OS
- NAT mode will allow the Guest OS to connect to the internet and so forth, but will not connect to your LAN without some routing trickery.
- from reading on VMWare's forums it looks like Server 1.x will not ever support this method of connecting to a LAN/internet connection.
- VMWare Server 2.0 Beta is available now, and is rumored to support the 'new' Wireless drivers unlike 1.x (i will not be able to test this right away)
- i have tried spoofing the MAC address on the NIC inside the guest OS with the wireless MAC address of the host OS; after changing to bridge mode it did not work, in my case.
- using a Wired Ethernet Connection WILL allow for your Guest OS to be in Bridge mode and on your LAN accessing all files/services, etc. with no problems.

So for now, VMWare server 1.x will not allow you connect a Guest OS in Bridge mode to a LAN/Internet through a Wireless Connection.  I believe this would apply to both USB and integrated Wireless NICs.


I have to go make a super-long Cat5 cable now....

---

### Post by Ctrl+Alt+Del on 2007-11-14
Ok, found a fix at least for VMWare Workstation 6.X
[http://communities.vmware.com/thread/95630?tstart=0&start=30](http://communities.vmware.com/thread/95630?tstart=0&start=30)

took me the better part of the evening but it works. My VM is connected via wireless :)

---

### Post by c9ops on 2007-11-14
the link didn't work.. was that the full url?

---

### Post by Ctrl+Alt+Del on 2007-11-15
works for me...
anyway.. here is the interesting part:
 (1) Download Hauke-m's patched vmnet.tar file from here:

 [http://www.hauke-m.de/fileadmin/vmware/vmnet.tar](http://www.hauke-m.de/fileadmin/vmware/vmnet.tar) 

 (2) Go to /usr/lib/vmware/modules/source and rename the original vmnet.tar to vmnetOLD.tar or something like that.

 (3) Copy Hauke-m's patched vmnet.tar to /usr/lib/vmware/modules/source/.

 (4) Run vmware-config.pl.

 That should do it.

---

### Post by keskew on 2007-11-15
I can confirm the directions given by Ctrl+Alt+Del worked for me.  I am now using bridged networking through my wireless network card.  This is awesome.  The following information about my system might be helpful.

Host OS - Ubunutu 7.10
Guest OS - Windows XP SP2
VMware Server 1.0.4
Wireless Network Card Driver - bcm43xx

Thanks Ctrl+Alt+Del !

---

### Post by tiger74 on 2007-11-18
Yes, I can confirm it.
I have a similar problem with Vmware server 1.0.4 on Gutys.
Actuall wifi bridged worked on Feisty, but since upgrading to Gutsy it stops. 
After I applied the patch, wifi bridged works again :)
Thank you.

---

### Post by Mayk on 2007-11-20
I too can confirm the patch vrom ctrl-alt-del works.. I was pulling out the hair on my head, not being able to bridge my wifi ..  Now after applying the patch it works like a charm.

THANX

---

### Post by Ktse on 2007-11-22
I tried the patch out yesterday and it works beautifully.  Fantastic, I'm extremely happy as bridging is far more efficient than port forwarding through NAT especially when streaming media to the outer world.

THANK YOU!

---

### Post by bcjordo on 2007-11-27
This information was excellent and fixed the problem I've been fighting with all day.  Thanks for the help

---

### Post by Nicu Alecu on 2007-11-29
It worked! =D>
Thanks for the tip!

---

### Post by bkraptor on 2007-12-12
Doesn't work for me with vmware-server installed from the repositories.

At step (2) I don't have a /usr/lib/vmware/ dir, instead I have a /usr/lib/vmware-server/ dir
At step (4) I don't have a vmware-config.pl, instead I have a vmware-config-network.pl

Other than that, I followed the instructions and it doesn't work, not even with VMware Player.

---

### Post by digitalbenji on 2007-12-26
I can confirm that this does not work with vmware installed from the Gutsy repository.  However, I can also confirm that this does work with vmware installed from the tarball available on vmware's website.  

I was unable to get this working with the repository package, but it worked perfectly for bridge on my wireless with the package of vmware server (not workstation) from vmware's website.  

BTW, to the poster, I'll be using this to VPN, but I noticed you said to play WoW on your onw server.  That's sounds pretty neat, care to give some details?

Regards, and Merry X-Mas

---

### Post by jonnymccullagh on 2007-12-29
thanks - worked for me

---

### Post by Tybris on 2008-01-07
because the confirmations gave me hope. ;)

Works for me with VMWare server 1.0.4 on Ubuntu 7.10 x86_64 with Minix3 as a guest and network over wireless (broadcom BCM4318 ). I had some trouble at first, but this worked for me:

During install, when /usr/lib/vmware structure is created, copied vmnet.tar to /usr/lib/vmware/modules/sources
Used eth1 (wireless) as (only) bridge network.
Disabled NAT and host only.
Reboot after installation.

Thanks Ctrl+Alt+Del, Hauke-m and everyone else.

---

### Post by chadjohnson on 2008-01-13
This worked for me on Ubuntu Gutsy with VMWare Server 1.0.4 built from the tar.gz package. I simply applied the patch which modified bridge.c, re-ran vmware-config.pl, and added vmnet2 as a bridge connection to ath0. I'm using a Trendnet TEW 441PC.

---

### Post by mdragos on 2008-01-20
another one that thanks you CTRLALTDEL (ubuntu 7.04 + vmware server 1.0.3)

---

### Post by saltydog on 2008-01-22
I confirm this does not work on vmware-server installed from canonical partner repository

---

### Post by h-kan on 2008-01-28
Anyone tried this on the new Hardy kernel?

I had to use the vmware-any-any-update-116.tgz patch here and the wireless patch posted her doesnt work with it...

---

### Post by mrvanes on 2008-02-06
I'm running 2.6.24 since today and had to switch my wireless driver from ipw3945 to built-in iwl3945. After the upgrade this patch doesn't work anymore. I can see my eth0 interface going into promisc state but eth1 doesn't, the vmnet modules compile without any complaints btw.

I have no idea if switching from ipw3945 to iwl3945 broke WL bridge, or 2.6.24. Anyway, I'm looking forward to a fix! :)

---

### Post by mrvanes on 2008-02-11
Tested with 2.6.24 and patched ipw3945. Problem persists, so it's not iwl3945.

---

### Post by mdelfede on 2008-02-14
Many thanks Ctrl+Alt+Del, Hauke-m and everyone else !
Bridging was driving me mad !

Max

---

### Post by XProgrammer on 2008-02-20
Thanks Ctrl+Alt+Del.

it worked for me.

Ubuntu 7.10 + Vmware 1.0.3 + ipw2200 wireless. 

Thanks,

---

### Post by bhavin66 on 2008-02-21
I can confirm the directions provided by Ctrl+Alt+Del is the way to go

PC - Gigabyte M/B Pentium 4 2.9 Ghz HAL
Host OS - Ubunutu 7.10
Guest OS - Windows 2003 server
Guest OS - Windows 2003 server
Guest OS - Ubuntu Desktop 7.10
Guest OS - Fedora 8
VMware Server 1.0.4
Wireless Network Card Driver - RT2600 802.11 MIMO PCI

Notebook - Compaq Presario V2570NR
Host OS - Ubunutu 7.10
Guest OS - joes 7.10
VMware Server 1.0.4
Wireless Network Card Driver - bcm43xx (4318) 

I have a third PC which i will be working on tonite. need to have a lot of servers and PC environment for testing and recreating environment.

Thanks again

---

### Post by Liken on 2008-03-02
I have found the solution.

Vmware with wireless bridge and kernel 2.6.24

[http://liken.otsoa.net/blog/index.php?entry=entry080301-173023](http://liken.otsoa.net/blog/index.php?entry=entry080301-173023)

---

### Post by eras2r on 2008-03-05
I had originally tried running h-kan's patched vmnet.tar on VMWare Server 1.04 under Gutsy. This indeed did fix the bridging capabilities of the wireless card, however it gave me terrible CPU problems where vmware-vmx was eating up 100% of my CPU with an idle XP guest host.

In my simple brain I attributed this to the fact that h-kan's vmnet.tar is from the source of VMWare Workstation 6 and not Server 1.04. So I read through his site on what he changed in the bridge.c file and made my own patched vmnet.tar that comes directly from the VMWare Server 1.04 source code. After moving this to the /usr/lib/vmware/modules/source dir, and running vmware-config.pl I tested everything out. Bridging worked and I had no CPU issues.

So I am attaching my vmnet.tar file that I created off of the VMWare Server 1.04 source. If you've run the any-any patch or previously used another vmnet.tar or vmmon.tar you will want to clear out the /usr/lib/vmware/modules/source dir and copy over the original files from the vmware-server-1.04 tar.gz that comes from vmware's site. Or simply re-install vmware-server. Once you have the original files in place, simply copy my vmnet.tar over the original one in /usr/lib/vmware/modules/source. Re-run vmware-config.pl. Then you should be set.

This is currently working an tested on Ubuntu Gutsy 7.10 running kernel 2.6.22-14-generic on a Dell Latitude D820.

I am new to these forums and not sure whether I can attach this file to my post. If it gets removed, please PM me if you have a website that this can be posted on for everyone to download.

Regards,
e

---

### Post by doctormentalo on 2008-03-08
It works very well! 
Working on Laptop Toshiba P100-342 

Host OS - Ubunutu 7.10  kernel 2.6.22-14-generic 
Guest OS - Windows XP SP2
VMware Server 1.0.4 mode brigded

wificard and CPU ok!

Thank you very much **h-kan's** & **eras2r ** !! =D> =D> =D>

---

### Post by Starks on 2008-03-11
eras2r, did you have to muck around with the ipw3945 drivers in order to get this to work?

---

### Post by vmware on 2008-03-17
hi friends,

i have installed Ubuntu 7.10 -1386 on VMWare workstation and I am trying to configure wireless network in ubuntu. My laptop has broadcom wirless card. I have tried using ndiswrapper for installing broadcom drivers, but this approach is not working.

My host operating system is windows XP.

Il appreciate if anybody can help me on this????

---

### Post by scorp123 on 2008-03-17
> **vmware said:**
>  i have installed Ubuntu 7.10 -1386 on VMWare workstation and I am trying to configure wireless network in ubuntu .... My host operating system is windows XP.  You have Ubuntu ***inside*** VMware Workstation on Windows?? In case you haven't noticed: VMware always emulates the same set of hardware, e.g. AMD PCnet32 Ethernet adapter, LSI or BusLogic SCSI adapter, "VMware Inc." VGA adapter, Soundblaster 16 sound card. That's it. That's all the hardware you will ever get inside a VMware virtual machine. There are some limited options to let a VMware virtual machine directly communicate to USB devices, but that's about it.

In other words: You can't configure a "wireless interface" on your Ubuntu inside VMware.

What you can do is enable bridged networking to go over your real wireless network ... but from the perspective of a operating system running inside VMware this is still an Ethernet connection.

---

### Post by moistk on 2008-03-19
OK, not sure if this applies but I am running Ubuntu 2.6.22-14-generic WS 7.10 as the host with VM server 1.0.4 build-56528.  I am trying to get XP as a guest to work with wireless.  I have added the vmnet.tar that was compiled from src from vmserver 1.0.4 re-ran the runme.pl from the vmware-any-any-update115.  Let default set up vmnet0 to eth0 and vmnet2 to eth1, removed or did not create NAT and Host.  In the vmware guest config I add a second NIC as bridged so I have 2 nics with bridged, start the XP guest and no wireless.  I understand that the network connection will look like wired but the wireless client does not come up, also both nics pull a DHCP address but no wireless.  What am i still missing?

---

### Post by glbyers on 2008-03-21
> **digitalbenji said:**
> I can confirm that this does not work with vmware installed from the Gutsy repository.  However, I can also confirm that this does work with vmware installed from the tarball available on vmware's website.  

I was unable to get this working with the repository package, but it worked perfectly for bridge on my wireless with the package of vmware server (not workstation) from vmware's website.  

BTW, to the poster, I'll be using this to VPN, but I noticed you said to play WoW on your onw server.  That's sounds pretty neat, care to give some details?

Regards, and Merry X-Mas

Hello,

Please be aware that the patch does work against the packages installed from the partner repository. You simply need to rebuild the vmnet module for this to take effect. ie ;

# cd /usr/lib/vmware-server/modules/source
# tar xvpf vmnet.tar
# patch -p0 < vmware-wireless.patch
# cd vmnet-only && make
# cp vmnet.ko /lib/modules/`uname -r`/vmware-server
# /etc/init.d/vmware restart

Thankyou for the patch.

Regards,
Grant

---

### Post by chronniff on 2008-03-24
dude...just wanted to say thanks for the patch,  you have know idea how helpful it was

---

### Post by luvit on 2008-03-26
> **Ctrl+Alt+Del said:**
> [COLOR="Red"]works for me...
anyway.. here is the interesting part:
 (1) Download Hauke-m's patched vmnet.tar file from here:

 [http://www.hauke-m.de/fileadmin/vmware/vmnet.tar](http://www.hauke-m.de/fileadmin/vmware/vmnet.tar) 

 (2) Go to /usr/lib/vmware/modules/source and rename the original vmnet.tar to vmnetOLD.tar or something like that.

 (3) Copy Hauke-m's patched vmnet.tar to /usr/lib/vmware/modules/source/.

 (4) Run vmware-config.pl.

 That should do it.[/COLOR]
**[COLOR="Blue"]I followed Ctrl]+Alt+Del's advise on VMWARE SERVER 1.0.5 build-80187 to solve my problem ;)[/COLOR]**

---

### Post by SyCo123 on 2008-03-30
Thanks for the post glbyers but I'm having problems with your suggestion.


> # cd /usr/lib/vmware-server/modules/source
# tar xvpf vmnet.tar
# patch -p0 < vmware-wireless.patch
# cd vmnet-only && make
# cp vmnet.ko /lib/modules/`uname -r`/vmware-server
# /etc/init.d/vmware restart


not sure about this line here.
# patch -p0 < vmware-wireless.patch

As there is nothing called  vmware-wireless.patch inside the tar file what should this be exactly?

---

### Post by jonny_boy27 on 2008-03-31
> **SyCo123 said:**
> Thanks for the post glbyers but I'm having problems with your suggestion.




not sure about this line here.
# patch -p0 < vmware-wireless.patch

As there is nothing called  vmware-wireless.patch inside the tar file what should this be exactly?

same here - i also get "WARNING: could not find /usr/lib/vmware-server/modules/source/vmnet-only/.smac_linux.x386.o.cmd for /usr/lind/vmware-server/modules/source/vmnet-only/smac_linux.x386.o

would be really nice if i could get this patch working without having to remove vmware server and re-install from scratch

---

### Post by luvit on 2008-03-31
> **luvit said:**
> **[COLOR="Blue"]I followed Ctrl+Alt+Del's advise on VMWARE SERVER 1.0.5 build-80187 to solve my problem ;)[/COLOR]**
[B][COLOR="Red"]I think I should point out that I downloaded & installed the latest version of VMware Server... I did not use the Synaptic package that came with my Ubuntu installation. 

Then I followed Ctrl+Alt+Del's advice on the patch...[/COLOR][/B]

---

### Post by edmundo.vn on 2008-04-06
Im using Ubuntu 7.10 with the vmware-server installed using apt-get. Here is how to rebuild the package from the repository to make the wireless bridge work:

Get tools needed:
```
sudo apt-get install build-essential fakeroot devscripts dpkg-dev
```

Get build dependencies:
```
sudo apt-get build-dep vmware-server-kernel-modules-2.6.22-14
```

Get source, change and repackage:
```
mkdir temp_build_dir
cd temp_build_dir
apt-get source vmware-server-kernel-modules-2.6.22-14
cd vmware-server-kernel-modules-2.6.22-2.6.22.0/vmware-server/
mkdir patches
cd patches
wget http://www.hauke-m.de/fileadmin/vmware/vmware-wireless.patch
cd ../../

export DEBEMAIL="your name <your.name@yourisp.com>"
VERSION=$(dpkg-parsechangelog | sed -ne 's,^Version:,,p')
dch -v $VERSION+0.local.1 -- Patched support for wireless bridge

dpkg-buildpackage -rfakeroot -uc -us
cd ..
dpkg -i vmware-server-kernel-modules-2.6.22-14_2.6.22.0-1+0.local.1_i386.deb
```

Thats it, restart your vmware:
```
sudo /etc/init.d/vmware-server restart
```

Now you have your own local patched package that makes the wireless bridge work.

---

### Post by cdukes on 2008-04-19
> **edmundo.vn said:**
> Im using Ubuntu 7.10 with the vmware-server installed using apt-get. Here is how to rebuild the package from the repository to make the wireless bridge work:


Confirmed! This worked for me using Gutsy 64bit
You rock dude, thanks!

---

### Post by scorp123 on 2008-04-19
Brilliant! Thanks so much.

---

### Post by shootermk on 2008-05-16
Thanks a million, this works great!!:guitar:

---

### Post by soichih on 2008-06-27
I couldn't get the patch compiled in Ubuntu 8.04.. Has anyone had luck on this distribution?

---

### Post by tastybrains on 2008-08-27
this worked perfectly for me! wow i've been annoyed by this for months thanks ctr+alt+del!!!

---

### Post by ethos101 on 2008-09-24
I tried the patch from c+a+d and got this message while running vmware-config.pl

I am trying to bridge vmnet3 to ath0, I have madwifi installed on my Acer Aspire 5720Z.

. vmnet1 is a host-only network on private subnet 172.16.25.0.
. vmnet2 is bridged to eth0
. vmnet8 is a NAT network on private subnet 192.168.84.0.


Any help appreciated.

=====================================================
Extracting the sources of the vmnet module.

Building the vmnet module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config3/vmnet-only'
make -C /lib/modules/2.6.24-19-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /tmp/vmware-config3/vmnet-only/driver.o
In file included from /tmp/vmware-config3/vmnet-only/vnet.h:13,
                 from /tmp/vmware-config3/vmnet-only/vnetInt.h:10,
                 from /tmp/vmware-config3/vmnet-only/driver.c:40:
/tmp/vmware-config3/vmnet-only/vm_basic_types.h:170: error: conflicting types for ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
In file included from /tmp/vmware-config3/vmnet-only/vm_basic_asm.h:28,
                 from /tmp/vmware-config3/vmnet-only/vm_oui.h:14,
                 from /tmp/vmware-config3/vmnet-only/vnetInt.h:11,
                 from /tmp/vmware-config3/vmnet-only/driver.c:40:
/tmp/vmware-config3/vmnet-only/x86cpuid.h:383:1: warning: "BIT_MASK" redefined
In file included from include/linux/kernel.h:15,
                 from /tmp/vmware-config3/vmnet-only/driver.c:9:
include/linux/bitops.h:7:1: warning: this is the location of the previous definition
make[2]: *** [/tmp/vmware-config3/vmnet-only/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config3/vmnet-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [vmnet.ko] Error 2
make: Leaving directory `/tmp/vmware-config3/vmnet-only'
Unable to build the vmnet module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

---

### Post by amadib on 2010-01-18
Was anyone able to get the above suggested fix working in Karmic?  I'm using VMware Server 2.0.

Thanks.
~ahmad

---

### Post by dubfazer on 2010-01-27
I had this problem in the past (with workstation not player  - but I'd guess it was the same underlying cause). I'm now running a Karmic host with multiple guests with the latest vmware versions and wireless and wired booth work in bridged mode with no issues (i.e. no need to apply any fix)

---

### Post by amadib on 2010-01-27
yeah, thanks for your reply.  

I ended up buying a new PCI network card and it works fine now :)

---

