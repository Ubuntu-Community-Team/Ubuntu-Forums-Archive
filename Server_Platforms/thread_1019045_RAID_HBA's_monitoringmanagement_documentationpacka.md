---
title: "RAID HBA's monitoring/management: documentation/packages (all vendors!)"
date: 2008-12-22
forum: Server Platforms
---

### Post by eL_vErDe on 2008-12-22
Hello,

I'm working on a website to make sysadmin's life easier.
I have packaged and written documentation for most monitoring and management tools of RAID HBAs.

For now I have stuff for:

* 3Ware Eskald
* LSI MegaRAID
* LSI MegaRAID SAS
* LSI Fusion MTP
* Adaptec AACRAID
* HP/Compaq SmartArray

Here is a list of packaged software:
[http://hwraid.le-vert.net/wiki/DebianPackages](http://hwraid.le-vert.net/wiki/DebianPackages)

Please check the website and tell me your mind.
If you have some hardware to test and/or requests, feel free to ask me and I'll try to help you asap :)


Regards, Adam.


[http://hwraid.le-vert.net](http://hwraid.le-vert.net)

---

### Post by eL_vErDe on 2008-12-23
I hoped someone would be interrested in :/

---

### Post by eL_vErDe on 2008-12-23
Hi,

I'm currently working on packages for others vendors.

If you have Areca (packages on the way, but no hardware for testing and documentation...), Qlogic, Emulex or any other weird RAID hardware, please tell me here :)

Thanks.

---

### Post by eL_vErDe on 2009-05-13
Hello,

Ubuntu packages are now available for hardy, intrepid and jaunty :)

Enjoy.


PS: I still have untested packages for Areca hardware.
Looking for someone to test it...

---

### Post by fjgaude on 2009-05-13
Thank you! Your work is greatly appreciated, and useful!

---

### Post by eL_vErDe on 2009-05-13
> **fjgaude said:**
> Thank you! Your work is greatly appreciated, and useful!

Thanks :D
I was wondering if there's at least one guy interrested in my work.
You're the first one ;-)

What hardware are you running ?

---

### Post by fjgaude on 2009-05-13
Well, I'm a graphic designer that uses **mdadm** raid5 on three machines. Notice my signature.

My son uses lots of hardware raid at his Fortune 500 company where money is of little priority, mostly Dell stuff.

---

### Post by eL_vErDe on 2009-05-13
Okay :)

Most of developpement and example have been done on Dell hardware too.

---

### Post by eL_vErDe on 2009-05-15
Up :)

---

### Post by eL_vErDe on 2009-06-10
Hello,

I'm still looking for feedbacks and Areca testers :/

---

### Post by televisi on 2009-06-13
Hi eL_vErDe,
I'm about to install Ubuntu 8.04 server using Adaptec Hardware RAID (detail in [_this thread_]("http://ubuntuforums.org/showthread.php?p=7451897#post7451897")), I will give your package a try once I get to know on how to use it :)

I will let you know the progress

---

### Post by eL_vErDe on 2009-06-14
> **televisi said:**
> Hi eL_vErDe,
I'm about to install Ubuntu 8.04 server using Adaptec Hardware RAID (detail in [_this thread_]("http://ubuntuforums.org/showthread.php?p=7451897#post7451897")), I will give your package a try once I get to know on how to use it :)

I will let you know the progress


Great!

Thanks in advance :)

---

### Post by ducksun43 on 2009-06-14
that 
[http://sunoano.name/ws/public_xhtml/hardware.html#adaptec_31205_raid_hba](http://sunoano.name/ws/public_xhtml/hardware.html#adaptec_31205_raid_hba)
might be exactly what you look with regards to your RAID task

---

### Post by eL_vErDe on 2009-08-19
Hello mates,

I'm still looking for feedbacks and don't see much coming from ubuntu users sadly :)
Come one ;)

---

### Post by trundlenut on 2009-08-20
Just stumbled across this thread and having looked at your site I will try out the package for my old proliant server, I had been looking for something like this.

I'll let you know how I get on.

---

### Post by eL_vErDe on 2009-08-20
Great.

If it works fine and your card is not already listed, please provide lspci -nn so I'll add it !

---

### Post by trundlenut on 2009-08-21
Neither cciss-vol-status or hpacucli work.
The server is a Proliant 800 and the relevant bits from lspci -nn are:

```

00:06.0 SCSI storage controller [0100]: LSI Logic / Symbios Logic 53c875 [1000:000f] (rev 14)
00:06.1 SCSI storage controller [0100]: LSI Logic / Symbios Logic 53c875 [1000:000f] (rev 14)
01:0a.0 RAID bus controller [0104]: Digital Equipment Corporation DECchip 21554 [1011:0046] (rev 01)
```

When I run cciss-vol-status I get:
```
cciss_vol_status: /dev/ida/c0d0, ID_CONTROLLER ioctl failed, Invalid argument, returning -1
```
And hpacucli gives:
```
Error: No controllers detected.
```

The controller is listed as a smart array 431 in dmesg

Any ideas?

---

### Post by eL_vErDe on 2009-08-21
Hi,

I have no idea yet.
There's one thing we are sure of, it's not an HP/Compaq controller.

I'll try to found some tools for this "DEC" RAID controller (never heard about this...)

Adam.

---

### Post by eL_vErDe on 2009-08-21
Could you please paste me full dmesg, full lspci and lsmod ?

---

### Post by eL_vErDe on 2009-08-21
Hey,

I just had a look to Linux kernel sources and this PCI looks like an Adaptec chip based RAID card:

In drivers/scsi/aacraid/linit.h
        { 0x1011, 0x0046, 0x9005, 0x1364, 0, 0, 55 }, /* Dell PERC2/QC */
        { 0x1011, 0x0046, 0x103c, 0x10c2, 0, 0, 56 }, /* HP NetRAID-4M */

Could you please check if the driver in use is really aacraid ?
If so, try installing aacraid-status package, it should works fine :)
If you prefer something graphical, check adaptec storage manager.

---

### Post by trundlenut on 2009-08-21
Here you go.

---

### Post by eL_vErDe on 2009-08-21
Okay I understand what's wrong.

It seems there's too drivers for HP/Compaq controllers:
* cciss which handle recent cards an works fine with cciss-vol-status and hpacucli
* cparray, yours which seems old and I don't have any tool for this one yet

---

### Post by eL_vErDe on 2009-08-21
[http://packages.ubuntu.com/search?keywords=cpqarrayd](http://packages.ubuntu.com/search?keywords=cpqarrayd)

Try this one and tell me if it works :)

---

### Post by trundlenut on 2009-08-21
installed cpqarrayd, it picks up the controller OK, I just need to work out how to get the output from it now...

Right so I have worked out any output goes to /var/log/messages and what this will do is allow me to monitor any changes on the controller.

---

### Post by bernard.guiliano on 2009-08-25
Greetings from Indonesia :)

I am very interested with this thread, and I hope you can help me.

I just bought new machine, spec as follow
Supermicro SuperServer 6016T-3F
Proc. 2 x Quad Core Xeon E5530 (2.4 GHz) Cache 8 MB
Chipset Intel 5520 (MB : X8DT3-F)
Memory 12 x 2 GB DDR3-1066 ECC REG
HDD 4 x 146 GB 10K RPM 2.5” SAS Hot Swap
LSI 1068E 8-Port SAS Controller, RAID 0, 1 & 10 (Onboard)
Dual LAN with Intel 82576 Gigabit Ethernet
Matrox G200eW
Power Supply : 560 W (Single)
Chasing : 1U Rackmount (SC111T-560CB)

I am trying to install Ubuntu 9.04 server edition, and stuck on drives detection phase
I've tried to use all MPT* and MEGARAID* driver that came on the media and result with no luck

Being honest, this is my first server and first time doing installation, which I didn't wish to encounter incompatibility issue

hope you can help me to give a step by step tutorial how to use your driver.

Thank you so much in advance.
Bernard.

---

### Post by trundlenut on 2009-08-25
You probably need to set up a raid array using the raid card setup programme.

---

### Post by eL_vErDe on 2009-08-25
Beware of low cost LSI MPT cards !!!
It may be a stupid half-hardware card which needs the proprietary driver "megasr"

Please send us lspci -nn first.

---

### Post by bernard.guiliano on 2009-08-26
Dear All,

Thank you for prompt response

First of all I did manage to setup raid 10 on 4 disk so it became 1 array, which not detected by ubuntu 9.04 AMD64 server edition.

Herewith I attached lspci -nn and demsg result that I produce by using Ubuntu 9.04 i386 Desktop Edition on live cd environtment.

Thank you for your helping hands.

Bernard.

---

### Post by eL_vErDe on 2009-08-26
Hi,

Here the line for your card:
03:00.0 SCSI storage controller [0100]: LSI Logic / Symbios Logic MegaRAID SAS 8208ELP/8208ELP [1000:0059] (rev 08)

It looks like a real LSI card, MegaRAID series which should work like a charm.

Could you please try to load megaraid-sas kernel module by hand and check dmesg again to see if there's something new ?

Adam.

---

### Post by bernard.guiliano on 2009-08-26
Dear eL_vErDe,

would you describe more how to " try to load megaraid-sas kernel module by hand"

if it was by doing selection on driver that listed on installation process when disk is not detected, I already tried it and result with no luck.

or did I have to go to shell execute and doing modprobe?
what command that i should use?

I found few threads on other ubuntu forum that gave hint to disable acpi and ide controller on bios, will try it and kept you update the result.

thanks.

---

### Post by eL_vErDe on 2009-08-26
I just looked at google again.

Forget it, it's a crap card with a proprietary driver only available for redhat and suse.
However, I made a package for the driver ([http://mentors.debian.net/debian/pool/non-free/m/megasr/](http://mentors.debian.net/debian/pool/non-free/m/megasr/)) but I haven't been able to test if it really works (it does build and insert with 2.6.26 debian lenny kernel).

Please note that if you decide to use this driver, you may have some non-fixable bugs and ubuntu's upgrade may be impossible if the driver doesn't build anymore with new kernels.

If you decide to use it, please ask someone to build a megasr module with my package for ubuntu's installer kernel. I don't know how to do that but I'm sure someone will do !

---

### Post by jmarks on 2009-09-13
Dear Adam
I have just found your site (and then this thread) after days of looking for help. It seems like most everyone does fakeraid or BIOS-based software RAID. 
Instead, I would like to install 64-bit Jaunty desktop (not server) onto a new true hardware RAID system that I am building. I have done Ubuntu installs, but never with a RAID card. (Lots of Windows installs onto RAID array.)

My plan is to use an Adaptec 2405 and build a 3 drive SATA-2 RAID 1 array on an i7 chip and EVGA X58 SLI motherboard, and install jaunty, but I want to get everything planned for trouble-free installation. (Since this is an office machine, I was going to install windows onto the array first, then Ubuntu as a dual boot. As I can gradually move my apps to open source, I should use Windows less and less.)

Would you mind helping with several newbie questions?

I don't understand how to obtain and supply aacraid packages to the Ubuntu installer so it can see and partition the RAID array. 
From your site, I gather that the process is straightforward. I just can't figure out what to do. Do I have to download packages ahead of time and put them on a USB drive? When does the installer ask for them? I hope I don't have to recompile the kernel, as that is probably beyond my time availability.

Thanks very much for your help!
Jeremy Marks

---

### Post by rh200 on 2009-09-14
Hi , I'm rather new at the whole linux think and hence not the best at these things. I have a supermicro X8DT3-F mbo with a LSI 1068E raid controller and 16 15k SAS disks.

I have this system on loan to be able to see if I can set up a rotating data buffer that can write at 1 GB/s. On a prevouis system wich had 8 disks 650 MB/s was no problem using mdadm raid 0.

I see this ssytem in lspci is using the pci-e bus so I am presuming bandwidth should not be a problem.

Any advice on the best way to set this up and what drivers are needed would be apreciated. I've got the latestest Jaunty 64 bit decktop version.

Thanks

---

### Post by eL_vErDe on 2009-09-15
> **jmarks said:**
> Dear Adam
I have just found your site (and then this thread) after days of looking for help. It seems like most everyone does fakeraid or BIOS-based software RAID. 
Instead, I would like to install 64-bit Jaunty desktop (not server) onto a new true hardware RAID system that I am building. I have done Ubuntu installs, but never with a RAID card. (Lots of Windows installs onto RAID array.)

My plan is to use an Adaptec 2405 and build a 3 drive SATA-2 RAID 1 array on an i7 chip and EVGA X58 SLI motherboard, and install jaunty, but I want to get everything planned for trouble-free installation. (Since this is an office machine, I was going to install windows onto the array first, then Ubuntu as a dual boot. As I can gradually move my apps to open source, I should use Windows less and less.)

Would you mind helping with several newbie questions?

I don't understand how to obtain and supply aacraid packages to the Ubuntu installer so it can see and partition the RAID array. 
From your site, I gather that the process is straightforward. I just can't figure out what to do. Do I have to download packages ahead of time and put them on a USB drive? When does the installer ask for them? I hope I don't have to recompile the kernel, as that is probably beyond my time availability.

Thanks very much for your help!
Jeremy Marks

Hi jmarks,

Once the array is created inside the card BIOS there's nothing to do. Just start the installer as usual, it will report one disk only if you're card is really and hardware one).

Adam.

---

### Post by eL_vErDe on 2009-09-15
> **rh200 said:**
> Hi , I'm rather new at the whole linux think and hence not the best at these things. I have a supermicro X8DT3-F mbo with a LSI 1068E raid controller and 16 15k SAS disks.

I have this system on loan to be able to see if I can set up a rotating data buffer that can write at 1 GB/s. On a prevouis system wich had 8 disks 650 MB/s was no problem using mdadm raid 0.

I see this ssytem in lspci is using the pci-e bus so I am presuming bandwidth should not be a problem.

Any advice on the best way to set this up and what drivers are needed would be apreciated. I've got the latestest Jaunty 64 bit decktop version.

Thanks

I'm not sure I understood what you mean but with cheap controller with NO BATTERY on them, Write Cache is disabled by default because it's unsecure if a power lost occurs.

---

### Post by jmarks on 2009-09-15
[quote=eL_vErDe;7953603]Once the array is created inside the card BIOS there's nothing to do. Just start the installer as usual, it will report one disk only if you're card is really and hardware one).
/quote]
My understanding from your site and the Adaptec site is that the Adaptec 2405 card is real hardware RAID. 
[http://www.adaptec.com/en-US/products/Controllers/Hardware/sas/entry/SAS-2405/](http://www.adaptec.com/en-US/products/Controllers/Hardware/sas/entry/SAS-2405/)

Do you agree this is hardware RAID?
thanks for your help.

---

### Post by eL_vErDe on 2009-09-15
> **jmarks said:**
> [quote=eL_vErDe;7953603]Once the array is created inside the card BIOS there's nothing to do. Just start the installer as usual, it will report one disk only if you're card is really and hardware one).
/quote]
My understanding from your site and the Adaptec site is that the Adaptec 2405 card is real hardware RAID. 
[http://www.adaptec.com/en-US/products/Controllers/Hardware/sas/entry/SAS-2405/](http://www.adaptec.com/en-US/products/Controllers/Hardware/sas/entry/SAS-2405/)

Do you agree this is hardware RAID?
thanks for your help.

Yep, aacraid driver = full hardware card

---

### Post by fjgaude on 2009-09-15
Looking over the Adaptic 2405, surely it is hardware, but I don't see a driver for Ubuntu-type OSs, no Debian types, just RPMs and the like.

It would be fast on PCI-E x8 bus with only raid0, 1, and 10 capabilities.

Its price indicates why only on 0, 1, and 10 raid levels, no raid5 or 6.

---

### Post by Schwyl on 2009-11-19
LSI Logic MegaRaid 8308ELP PCI-e

DOes this card work with ubuntu no it wont have the os loaded onto it

---

### Post by Heeter on 2009-12-09
Awesome work, eL_vErDe

I have bookmarked your site and this thread for my setup.

I am presently using a Promise Fasttrak 4310, works fine, but I don't have a RAID monitor to see the real-time status of the drives and the arrays.

I think that I will be moving to an adaptec.

Are you a company of people or just yourself? This is a great deal of work, and must be commended.


Heeter

---

### Post by eL_vErDe on 2009-12-15
Hey Heeter,

SadlyI haven't got any Promise in my hands yet so I won't be able to help you much with it.

I started this work at my compagny, which allowed me to publish all what's already done. It's now shared work between my real work and my free time :)

Regards, Adam.

---

### Post by Heeter on 2009-12-15
Again, commendations on your great work.

Because of my concerns with this Promise card, I ordered an Adaptec ASR-5805. 

Looking back, I should of checked to see if this was on your list.

Is my new adaptec on your list?

Heeter

---

### Post by eL_vErDe on 2009-12-15
I don't think so ;)

Send me lspci -nn !

---

### Post by eL_vErDe on 2010-09-22
Hey mates,

Just a status update to inform you that both Karmic & Lucid repositories have been added.

I've also update all Adaptec tools to latest version and both command line cli and java client/server graphical application (ASM) should work as expected.

Hope you'll tell me if it's fine for you too!

Regards, Adam.

---

### Post by Heeter on 2010-09-22
Thanks a million, eL_vErDe.

Can update my setup.

Heeter

---

