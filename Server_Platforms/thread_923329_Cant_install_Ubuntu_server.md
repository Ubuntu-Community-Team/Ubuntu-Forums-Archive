---
title: "Cant install Ubuntu server"
date: 2008-09-18
forum: Server Platforms
---

### Post by ascii2k8 on 2008-09-18
Hi, i recently grabbed the Ubuntu Server 8.04.1 image.  I planned to install it on a Gateway ALR 7400 server machine.  Unfortunately I cannot seem to get it to install. This is a machine from ~2001-2002.  I have installed Linux on it many times but had never tried Ubuntu.  The install goes OK until it starts to copy the packages from the CD/DVD and then it just stops and eventually times out.  When I look at the terminal screen to see the output it is showing I/O errors and what seems to be ata controller resets.  OK, Here are the basic hardware specs.

Gateway ALR 7400 Server
384 MB RAM Registered-ECC
Intel ServerWorks Chipset/MB
Integrated Intel Ethernet
OnBoard Ultra SCSI3 controller (Symbios Logic - SYM53C1010)
ATI Rage XL onboard video
(3) 9GB SCSi drives
 1 IDE 20GB drive for OS
 1 IDE CD-ROM/DVD Drive 


OK, nothing too extreme there.  Here is what I have tried.

1.  Downloaded Ubuntu server image twice.  Verified both iso files with MD5 sum.

2. Burned image to CD as well as DVD

3. Tried 52x CD Drive as well as newer DVD-Writer drive

4. Tried the CD in another machine which worked perfectly.


I dont give up easily but i am about out of ideas and i was really looking forward to trying the ubuntu server.  Any suggestions would be GREATLY appreciated.

Todd

---

### Post by jamesrfla on 2008-09-18
Looks like it is having issues talking to your hard drives.

---

### Post by jamesrfla on 2008-09-19
If you can't install Ubuntu Server and it is a issue with your hard drive I don't think you will have much luck installing slackware. Try to make sure that all connections from the hard drive to the motherboard are in all the way. Are they SATA hard drives or ATA hard drives. If they are SATA hard drives you might have to go into the BOIS and enable the SATA controller. Hope this helps.

---

### Post by Pamir on 2008-09-19
Hi,

I think, there is something wrong with scsi hard drive. I had a similar problem. I was think the CD is gone bad. But I tried installin on different machine it works. I have not tried on my Server with scsi yet again.

---

### Post by HermanAB on 2008-09-19
Do try the usual obstreperous hardware cheat codes when you install: noapic nolapic

That usually works for me.

Cheers,

Herman

---

### Post by jamesrfla on 2008-09-19
> **HermanAB said:**
> Do try the usual obstreperous hardware cheat codes when you install: noapic nolapic

That usually works for me.

Cheers,

Herman

I have to use acpi=off in order for me to run Ubuntu at all.

---

### Post by nathan42100 on 2008-09-19
I had this problem and was just able to fix it today for my PowerEdge 2500. It had something to do with the kind of CD Rom drive. If you have a spare IDE one, try switching them out (IDE as in uses an IDE cable too, even if the mobo says IDE...). If you don't actually use IDE, invest in an IDE controller that you can return if it doesn't work.

---

### Post by ascii2k8 on 2008-09-20
Thanks everyone for your comments.  I had to take a break from it after 2 hours the other night so I havent tried again.  As I said in my original post.  I have installed Linux on this server many times in the past with little or no trouble and the exact same hardware..  There are no pci cards installed right now. So everything in on the mobo.  I may still try a different distro.  If Slackware works then it would seem to be a problem with Ubuntu.  If not then I will go back to troubleshooting the hardware.  Thanks again for your help.

---

### Post by Pamir on 2008-09-20
It seems Ubuntu 8.04 has a problem with scsi. Since you have IDEs simply disable scsi and try it. If works than you have found the guilty part! Just an idea.

---

### Post by windependence on 2008-09-20
I believe there is an alternate CD installation for when your hardware doesn't support the regular CD.

-Tim

---

### Post by nathan42100 on 2008-09-21
> **windependence said:**
> I believe there is an alternate CD installation for when your hardware doesn't support the regular CD.

-Tim

Not for the server version.

---

