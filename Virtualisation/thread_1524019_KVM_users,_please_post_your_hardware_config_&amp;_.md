---
title: "KVM users, please post your hardware config &amp; VMs"
date: 2010-07-04
forum: Virtualisation
---

### Post by naelq on 2010-07-04
hi all,
i'm looking for getting some new hardware for running KVM in my lab, to learn/master it, along with different networking/storage combos reflecting near to real-world usage.
my main concern right now, is the hardware to get, & before someone jumps up with:
***just throw a 2x X5650 Xeons along with 32GB RAM & 5x 300GB SAS in RAID5... & you would would be fine!*** :D
seriously, for the mean time, i would prefer to spend the money wisely getting a *good* testing box for warming up, & by the time i need more power, the same amount of money should let me get better hardware..

i would like to ask those of you running KVM: (no VB/VMWare/XEN)
what hardware do you have? [ CPU(s) / RAM / Storage config ] & what's the number of simultaneous running VM's?

PS, i'm sure that this will help other people heading for the same direction :)
 
thanks

---

### Post by sh1ny on 2010-07-05
One of my current hosts has the following :

2x Intel(R) Xeon(R) CPU E5520  @ 2.27GHz
12 GB RAM
MegaRAID 8708ELP
6x500GB SATAII

Running a raid6 and a raid1.

virsh list :

  2 bluewing       running
  3 yellowwing           running
  5 purplewing           running
  6 whitewing            running
  7 dev                  running
  8 redwing              running


2 of those machines are given 4G ram each and the rest vary between 512Mb and 2G. If it wasn't the memory leak in lucid kvm ( fixed in proposed ) i'd be holding at around 5-8G RAM usage. It can take a few more VM's - like 2 or 3, before going nuts i guess. The machines are running a web hosting + a zimbra server + a dedicated databse server ( postgresql ) and it's actually quite stable.

About raid5 - it's cool and all , but i had too many cases where 2 disks go down at the same time. Most important thing ? Make sure your kvm images are using RAW format and are preallocated or it will lag hard if you do large writes from the network.

I'd really recommend getting 5520+ Xeon/s . They will get you most for your money. If it's just for testing, Core2Duo 8800 or so would be fine. Just make sure it has VT/d .

---

### Post by naelq on 2010-07-05
hi & thank you for your post :)
you have a nice rig, is it a custom build or branded?

since i'll be learning/testing, i doubt it, at least for now, that'll be needing SMP power. anyway, here is what i have in mind:

**option 1** a DELL R210:
X3430
2x 4GB
2x 1TB SATAII

**option 2** a DELL R310:
X3430
2x 4GB
4x 500GB SATAII

**option 3** custom built:
Core i7 860
Intel DQ57TM
2x 4GB DDR3
6x 500GB SATAII

price is almost the same, (i'm not in the US!) the 860 is faster than the x3430, the R210 has only 2x internal HDD's, the R310 has 4x hotswap, both the DELLs support 32BG RAM (x3430 vs 860)...

for a start, i think that 8GB will be enough, & worst case i'll be adding another 8GB, which will be good for the 3 options above.
i'm aiming for system capable of running 4 VMs simultaneously:
> Linux Server
> Win2k3 or Win2K8
> WinXP or Win7
> Linux client

all in a virtual network.. what do you say?


thanks

---

### Post by sh1ny on 2010-07-05
I'm using Supermicro as they come cheaper than Dell/HP and offer the same quality and perfomance for lower price. I'd suggest sticking to xeons instead of i7. Also google for "tsc unstable clocksource" and see if anyone mentions your cpu of choice as having an unstable clock source. The fix for this is in 2.6.35 or 34 ( not very sure ), but the lucid kernel/kvm will have problems on such cpu's if your vm's are under a lot of load. I know i'm having troubles with this on a 5405 Xeon, so do a little research  before you buy stuff.

---

### Post by naelq on 2010-07-07
OMG!!
i think that i'm in the wrong place! the "ubuntu-linux-forums" is overloaded with VirtualBox stuff, but no KVM users?! this is shocking!

anyway, thank you for your input **sh1ny**, i think that i'll be going with option 3 for the moment, & when a more powerful system is needed, i'll go the Xeon (Opteron) route ;)

nael

---

### Post by keithweddell on 2010-07-07
I use kvm in my home network so no requirement for 24/7 99.99% reliability.  I use VMs to provide some separation of services and for the learning experience.  None are heavily loaded.  I use:

AMD Athlon LE-1640 @ 2.6 GHz single core
4 GB RAM
1 x 500 GB Sata HD (plus 1 x backup HD)
Ubuntu 10.04 Server Edition

I run 3 VMs:
Web / Jabber server
Mail / IMAP server
Rsyslog server / music server / apt-cacher server

I also run some services on the physical server for my home lan only.  This set up runs well and hardly breaks into a sweat.

Keith

---

### Post by naelq on 2010-07-13
i thought i should update, here is what i 've ordered:

CPU: Intel Xeon X3400
MoBo: Intel S3420GPLC
RAM: 12GB - 6x 2GB Kingston DDR3 1333MHz REG ECC KVR1333D3D8R9S/2GI

i'm still researching, HDD's (& maybe a RAID controller, not sure) but 1st i'll try & test the kernel built-in software RAID. i'm looking at:

option 1:
x4 WD 500GB RE4 WD5003ABYX

option 2:
x6 WD 640GB Black WD6401AALS


will keep you posted,
nael

---

### Post by sh1ny on 2010-07-13
Go ahead with software raid. If it's a learning experience, you better get started with it.

Again from my experience LSI SAS raids are very good ( don't be mislead, they support both SAS and SATA hdd's ). I'm using LSI MegaSAS 9260 - as well as the one i wrote about above - both are somewhat same price here, but the performance of this one is double. ( [http://www.lsi.com/storage_home/products_home/internal_raid/megaraid_sas/6gb_s_value_line/sas9260-8i/index.html](http://www.lsi.com/storage_home/products_home/internal_raid/megaraid_sas/6gb_s_value_line/sas9260-8i/index.html) ).

For hdd's - Western Digital WD 1TB 7200RPM 32MB 24X7 SATA 3 3.5 - WD1002FBYS-02A6B0 ( Enterprise HDD) : [http://www.systemsassurance.com/sysSystemsRelated.asp?pn=WD1002FBYS-02A6B0](http://www.systemsassurance.com/sysSystemsRelated.asp?pn=WD1002FBYS-02A6B0)

For more ( and good ) info on hwraids read [http://hwraid.le-vert.net](http://hwraid.le-vert.net) . It also has some debian/ubuntu packages of the proprietary utils for many hwraids which are usually only built in rpm formats for RH/Centos.

---

### Post by naelq on 2010-07-13
thanks for the input sh1ny :)

as for the software raid, well i'm not an expert, but i think that i've already learned it the Gentoo way :D but sure, we do learn everyday..
the controller you've mentioned is already on my list, but i'll still working on the prices.

the HDD's, well, my experience with WD's Black is exceptional, very fast (tested 6x in both RAID5 & RAID10 -- kernel software) & i do have x4 RE3 250GB ones running great 3 years now with no problem.. but the thing is with capacity, that i already have a NAS for storage, & since this is a lab rig, local +1TB for the VM's is overkill.. that's why i didn't mention 1TB's ones.. but i'll look into it :)

Oh, & thank you for the link regarding the RAID controllers, great info.


PS, i think that i'll be using Gentoo for the host..

nael

---

### Post by sh1ny on 2010-07-13
> **naelq said:**
> 

PS, i think that i'll be using Gentoo for the host..

nael

That's what freedom is about, but i just can't stop wondering why ? I mean, i started using linux back 2001 or so with slack and RH at the time. I tried freebsd and stuff and it always amazed me why people would choose an OS where you'd have to compile stuff on your own, rather than something that comes packaged and tested ( well at least tested more than i'd be able to do myself ). Sure i do have an arch  boot and i fancy rebuilding gnome from time to time, but that's just on my home box where i can rm -rf / and not care about it. For anything that more than a toy and that i have intents of getting serious about i like to rely on others to do the hard work for me...simply because one man can't do it all.

---

### Post by naelq on 2010-07-13
by no means, i'm not about to start a distro-war :)
but the only reason for Gentoo, is to control the host's footprint to the minimum & with Gentoo, which i know the most (8 years now) it will be easier!
Proxmox VE is another want-to-try, especially since it's already stripped down with some nice features that i'm considering. & of course, i always have to option to go with Ubuntu :)

nael

---

### Post by sh1ny on 2010-07-13
> **naelq said:**
> by no means, i'm not about to start a distro-war :)
but the only reason for Gentoo, is to control the host's footprint to the minimum & with Gentoo, which i know the most (8 years now) it will be easier!
Proxmox VE is another want-to-try, especially since it's already stripped down with some nice features that i'm considering. & of course, i always have to option to go with Ubuntu :)

nael

I wasn't trying to start a distro-war either. As i said , to each his own. I was just curious and asked, exactly because you didn't look like the kind of guy that would start a flame war :)

---

### Post by naelq on 2010-07-13
thanks :)

by the way, did you happen to try Proxmox VE? i'm asking this, assuming you use your setup for production, & it's interesting to try & compare it to ESXi **management-wise**..
ohh, & another question, besides using virt-manager, is there any other web-based tools that one could count on?

nael

---

### Post by sh1ny on 2010-07-14
Proxmox is good. I played around it with and it seemed fine, had almost everything i needed, except for user access control ( which i needed for reselling openvz containers and/or KVM ). As far as i've read that functionality is also coming in the near future.

On the other question - no, i haven't found anything suitable. Maybe oVirt, but then you're stuck at using fedora :/

---

### Post by naelq on 2010-07-14
i've happened to pass by ConVirt, they have an open-source edition which available under GPL, [http://www.convirture.com/products_opensource.html](http://www.convirture.com/products_opensource.html)
looks nice, that i might try along with Gentoo, have you tried it?

---

### Post by sh1ny on 2010-07-14
I've had a quick look and it looks decent, but i fancy sticking to libvirt based things.

---

### Post by TheFu on 2010-07-15
> **naelq said:**
> OMG!!
i think that i'm in the wrong place! the "ubuntu-linux-forums" is overloaded with VirtualBox stuff, but no KVM users?! this is shocking!

Ubuntu is historically known as a desktop distribution. I suspect most of the folks watching this thread are using desktop virtualization, so of course the cheapest solution with the prettiest GUI will be used - VirtualBox.

I've been running *nix virtualization on servers for 11+ years and tested KVM on 10.04.  For our needs, it simply isn't ready for production use.  Obviously, this is just my opinion and others may have had greater  success. I can't speak for anyone else.  I don't think VirtualBox is ready for server virtualization either.  We run Xen, ESX and ESXi in-house for production systems AND at client locations.  Most systems are Dell 2950-class connected to a Dell M3000i array serving iSCSI. We tend to prefer 2+ physical servers that can run VMs - think redundancy and a way to migrate VMs to an alternate system when longer than normal server maintenance is needed without dramatically impacting users.

Having a NAS/SAN/iSCSI network storage is just as important as having virtualized servers, IMHO. Both provide flexibility.

Whenever I'm selecting hardware, I try to consider the server lifetime and how an initial purchase for a lab may be put into production, then made into test or DR later, so making a good choice up front matters.  For example, even if a server is planned to use KVM, I always look at the ESX HCL to ensure a redeployment with ESX (which is pickier than other virtualization technologies) will work. That usually means being careful about NICs and disk controllers, especially for the boot disk(s).

As to whether HW or SW RAID should be deployed, that's a holy war for many.  I tend to go with SW RAID for increased flexibility and HW independence unless I have a specific reason for HW RAID.  Knowing that you can swap arrays between servers and not concern yourself with the HDD controller hardware is nice. I've done this a few times and the arrays just re-assembled nicely. HW-RAID makes sense sometimes too - usually for enterprise customers or when the highest possible disk performance possible is needed and you don't have a SAN (with HW RAID and lots of caching RAM).  Also, if you have an iSCSI network array, then HW/SW RAID question really goes away.

Sorry if I went too far off topic.

---

### Post by sh1ny on 2010-07-16
> **TheFu said:**
> 
I've been running *nix virtualization on servers for 11+ years and tested KVM on 10.04.  For our needs, it simply isn't ready for production use.  Obviously, this is just my opinion and others may have had greater  success. I can't speak for anyone else.  

Can you be a bit more specific ? I'm not advocating KVM, nor do i have you years of experience and maybe that's exactly why i want to know what made you say that about KVM. I've never ran VMWare on production, mainly because of it's price ( too high for the market here ) but i want to know what makes you happy in xen that isn't in kvm. Just asking, no virt-war intended :)

---

### Post by Khakilang on 2010-07-16
Intel Dual Core 1.8GHz, 1.5GB RAM 160GB hard disk, nVidia 7200GS, DVD RW and Virtual Box PUEL. No problem installing Window XP. The USB work and hence my Lexmark all in one printer works too.

---

### Post by sh1ny on 2010-07-16
> **Khakilang said:**
> Intel Dual Core 1.8GHz, 1.5GB RAM 160GB hard disk, nVidia 7200GS, DVD RW and Virtual Box PUEL. No problem installing Window XP. The USB work and hence my Lexmark all in one printer works too.

Wrong topic :)

---

### Post by naelq on 2010-07-16
> **TheFu said:**
> Ubuntu is historically known as a desktop distribution. I suspect most of the folks watching this thread are using desktop virtualization, so of course the cheapest solution with the prettiest GUI will be used - VirtualBox.
no comment!

> **TheFu said:**
> I've been running *nix virtualization on servers for 11+ years and tested KVM on 10.04.  For our needs, it simply isn't ready for production use..
could you elaborate some more? that it's true VMWare had been long before KVM, which means there products are mature enough, but eliminating KVM as a production solution is interesting. what is it lacks? performance? management?.. it's good to hear from people with your experience ;)

> **TheFu said:**
> Having a NAS/SAN/iSCSI network storage is just as important as having virtualized servers, IMHO. Both provide flexibility.
i agree, after i finish building the virtualization box, i'll start with the NAS, in fact i have all the hardware needed, i just need to decide on the HDD's to put in.

> **TheFu said:**
> Whenever I'm selecting hardware, I try to consider the server lifetime and how an initial purchase for a lab may be put into production, then made into test or DR later, so making a good choice up front matters.  For example, even if a server is planned to use KVM, I always look at the ESX HCL to ensure a redeployment with ESX (which is pickier than other virtualization technologies) will work. That usually means being careful about NICs and disk controllers, especially for the boot disk(s).
i won't lie, before deciding on this setup, especially the MoBo, i made sure that it will be 100% compatible with ESXi, simply to have a plan C in case i'll be disappointed with KVM. (which i hope not!)

> **TheFu said:**
> I tend to go with SW RAID for increased flexibility and HW independence unless I have a specific reason for HW RAID.  Knowing that you can swap arrays between servers and not concern yourself with the HDD controller hardware is nice. I've done this a few times and the arrays just re-assembled nicely..
so you are saying, that you also use software RAID for production? :)

@ **Khakilang** LOL! :popcorn:


nael

---

### Post by gtdaqua on 2010-07-16
> could you elaborate some more? that it's true VMWare had been long before KVM, which means there products are mature enough, but eliminating KVM as a production solution is interesting. what is it lacks? performance? management?.. 

Performance is two thumbs up! But lacks management. I've started a separate thread here: [http://ubuntuforums.org/showthread.php?t=1532214](http://ubuntuforums.org/showthread.php?t=1532214)

I am serioulsy conisdering moving my VMWare infra to KVM. I am not even looking for an enterprise grade management tool - just a simple tool that even windows users can logon to KVM server to see console, add VMs without having to use root password.

---

### Post by sh1ny on 2010-07-16
> **gtdaqua said:**
> Performance is two thumbs up! But lacks management. I've started a separate thread here: [http://ubuntuforums.org/showthread.php?t=1532214](http://ubuntuforums.org/showthread.php?t=1532214)

I am serioulsy conisdering moving my VMWare infra to KVM. I am not even looking for an enterprise grade management tool - just a simple tool that even windows users can logon to KVM server to see console, add VMs without having to use root password.

I've replied to your other topic. I know the management is not top-notch, but it's fine for a young ( relatively ) virtualization.

---

### Post by TheFu on 2010-07-18
> **sh1ny said:**
> Can you be a bit more specific ? I'm not advocating KVM, nor do i have you years of experience and maybe that's exactly why i want to know what made you say that about KVM. I've never ran VMWare on production, mainly because of it's price ( too high for the market here ) but i want to know what makes you happy in xen that isn't in kvm. Just asking, no virt-war intended :)

The performance under Xen was significantly better than under KVM.  KVM was even slower than VirtualBox on our lab systems.  It isn't about pretty GUIs for us. We need to have 10+ VMs per physical server and with either Xen or ESX we can easily do that.

Xen isn't part of either RH or Ubuntu server repositories for the new LTS distros, so we're still on Hardy and hoping that KVM matures with performance before we're forced to go with ESX instead.

---

### Post by naelq on 2010-07-18
@ **TheFu**, could you please provide more info regarding the tested KVM VM's? is it windows/linux? CPU intensive? I/O intensive? when was it the last time you've done those tests? (KVM/Kernel version? libvirt version?) it's not that we always have the opportunity to get the info from experienced production people, thus the so many questions :)

thank you,
nael

---

### Post by sh1ny on 2010-07-19
> **TheFu said:**
> The performance under Xen was significantly better than under KVM.  KVM was even slower than VirtualBox on our lab systems.  It isn't about pretty GUIs for us. We need to have 10+ VMs per physical server and with either Xen or ESX we can easily do that.

Xen isn't part of either RH or Ubuntu server repositories for the new LTS distros, so we're still on Hardy and hoping that KVM matures with performance before we're forced to go with ESX instead.

AFAIK, KVM handles CPU and Network just fine, the only possible bottleneck could be disk I/O. And running 10 virtual machines on a single host is just fine with KVM.

---

### Post by Ztoragefool on 2010-09-02
hello, 

i am quite new in here (and in virtualizing servers in general).

the bad KVM performance i experienced really surprised me. after reading so much about how good ubuntu server and kvm fit each other, i expected less than 18% host cpu on just one idling guest. 

my specs on this: 

[LIST]
[*]amd X3 440, 3 vt-capable cores @ 3ghz
[*]4gb ram ddr3
[*]2 x 1tb sata (peaking @ 150mb/s)
[*]ubuntu server 10.04 x64
[/LIST]
 targeting an all-in-one server for small business purposes.

sharing my disappointment with TheFu, i read things like...

> **sh1ny said:**
> AFAIK, KVM handles CPU and Network just fine...

and wonder if i just have to cancel my out-of-the-box approach and have to do some magical configuration to get rid of this kvm cpu brake... Sh1ny, did you do any configuration to yield "fine cpu handling"? EDIT: not talking about i/o optimization, invoking TOP and seeing 10% cpu for a 3-second top inside the guest is just disencouraging. and yes, kvm-amd and this other module are loaded. 

by the way, testing on citrix´ XenServer 5.6.0 gave me back some confidence in my hardware selection - it just did very well. but i´d prefer an ubuntu host, and i could imagine i´ve missed some point...

-helpful hints appreciated-

---

### Post by sh1ny on 2010-09-02
If you're comparing Xen PV with KVM, the edge could be on the Xen side ;)

For performance, i've recently came across a setting that improved I/O performance a lot ( and lowered CPU usage on host by a factor of 10 under heavy loads ). You can read my thread in the ubuntu-server lists here :

[https://lists.ubuntu.com/archives/ubuntu-server/2010-September/004594.html](https://lists.ubuntu.com/archives/ubuntu-server/2010-September/004594.html)

---

### Post by JeremyA on 2010-12-07
a delayed response for sure, but I'm running (at current) 6 guest VMs on my lucid server:

Lucid 10.04.01 LTS
Biostar A740G M2+ mobo
Athlon 64 X2 5400+ (dual-core)
8GB DDR2 @400mhz
2x 1TB Samsung drives in a soft-RAID1 array hold all my VMs (other drives are attached for other stuff)
Intel e1000 NIC for vms/LAN

I'm pretty happy with performance -- solaris notably takes a lot less cpu than it used to.  I'll be doubling the number of VMs by end of day, but in use, the system seems a lot more responsive than it did with VirtualBox and vmware running.

at current, my guests are:
ubuntu 10.10, rhel4.6, rhel6, sles8, sles9, and solaris10u4

unfortunately, I'm still seeing hard lockups on this box -- every few hours, even with acpi disabled and X windows deactivated -- It didn't happen under 8.04, but it does happen under 10.04.

---

