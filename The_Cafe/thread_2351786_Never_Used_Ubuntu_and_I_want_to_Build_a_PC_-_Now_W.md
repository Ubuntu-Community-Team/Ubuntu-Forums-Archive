---
title: "Never Used Ubuntu and I want to Build a PC - Now What"
date: 2017-02-06
forum: The Cafe
---

### Post by gatorbite on 2017-02-06
Hi,

I have never used Ubuntu (or any variant of Linux) or built a PC, but I want to do both :D

I am looking to get input/help along the way with stuff like hardware selection, dual boot, RAID, etc...

Is there a particular sub forum that I should post in to cover an entire build?

Rich

---

### Post by wildmanne39 on 2017-02-06
You can only ask one question per thread, so this one is about what computer or hardware to use so I will move this thread to the appropriate forum for choosing hardware, then when you need install help you will want to start a thread in Installing/Upgrades.

---

### Post by grahammechanical on 2017-02-06
My advice would be to go to a newsagents and buy a computer magazine that gives reviews of the different pieces of computer hardware and study up.

Linux/Ubuntu will install on all standard computer hardware. We do not need special hardware to use Linux. Keep in mind that the Linux developers have keep Linux up to date with newer hardware and that can take a bit of time. So, Linux may not have hardware drivers for the very, very latest hardware. And you will also need the very latest version of Ubuntu to get the most up to date drivers. At the present time Ubuntu is released every six months at the end of April & the End of October each year.

If you do not have an existing machine you can often get a copy of Ubuntu on a DVD disc supplied free of charge by some Linux magazines. That is how I got my first version of Ubuntu back in 2007. And it was for a self-built machine.

What do you want to use the machine for? Games? Then you will be interested in this site. It often has hardware comparisons along with comparisons with how well Linux runs on the hardware in comparison with another well know computer OS.

[http://www.phoronix.com/scan.php?page=home](http://www.phoronix.com/scan.php?page=home)

If only want Ubuntu on the machine then installing will be very simple. If you intend to have both Ubuntu and Microsoft Windows on the machine, then you need a bit more preparation.

Regards.

---

### Post by gatorbite on 2017-02-06
My primary use will be productivity, web browsing and media streaming since I don't have a TV.

But I also want to learn about this OS and other stuff.

Dual boot windows and ubuntu on separate SSDs
RAID 1 (RAID 10 in the future) data storage able to be accessed from both OS

I'm not trying to do a high end build, but rather something I can grow with if the need arises.

Is there a way to see if the motherboard(s) and other components are supported with the current release of Ubuntu?

---

### Post by oldrocker99 on 2017-02-06
Practically every motherboard currently available is supported by the Linux kernel. Generally, the only drivers needed are for graphics cards. If a piece of hardware is more than 6 months old, it's almost certainly supported.

---

### Post by SeijiSensei on 2017-02-07
My daughter built a gaming PC from a kit at [Newegg]("https://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=30000007%2031001489&IsNodeId=1").  They have them in all price ranges.

---

### Post by mastablasta on 2017-02-07
> **gatorbite said:**
> 
Dual boot windows and ubuntu on separate SSDs
RAID 1 (RAID 10 in the future) data storage able to be accessed from both OS


throwing Windows in the mix Will add complication. ubutnu can easilly be installed in virtualbox if needed. : [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)


Raid - what kind of raid - hardware or software. again windows adds to complication. i am not sure why you need two OS for the things you mentioned. windows is actually needed for some specific windows based software (MS Office, windows based games, CAD programs...). RAID in linux (especially at home) is usually done via mdadm.

why do you need RAID for the tasks you mentioned? it is not necessary. it doesn't guard against data loss. it only guards against disk failure. to guard yourself against data loss you need good and versioned backups. RAID is important in servers that have to be accessible 24/7. for home use it is a bit of an overkill. versioned backups is what you need for your important data.

windows uses NTFS file system while linux needs it's own file system for the OS. default is ext4, but one can also use BTRFS, ZFS... linux can read and write to NTFS, but it doesn't have all the tools needed to do maintenance on it.

---

### Post by oldfred on 2017-02-07
My build is probably not what you want.
I wanted a smaller form factor, so smaller case and no video card.
But I liked that pcpartpicker told me I had incorrect hard drive (3.5") when small case needed the laptop size 2.5" drive.
It also gave me an idea on prices, although I went with Amazon for everything for just a few $ more as my Wife has the free shipping on just about everything.

 oldfred's new SFF system with skylake i5-6500 and 16.04
[http://ubuntuforums.org/showthread.php?t=2315007&p=13449024#post13449024](http://ubuntuforums.org/showthread.php?t=2315007&p=13449024#post13449024)
[http://pcpartpicker.com/p/8QKkCJ](http://pcpartpicker.com/p/8QKkCJ)

---

### Post by gatorbite on 2017-02-07
I have looked at several of the configuration websites to try and get an idea of what I am wanting to purchase. I will probably source everything through newegg. I don't think I need a video card at this time either.

 I understand that using 2 operating systems makes things a bit more complicated but it seems like there are a bunch of people that have it implemented successfully.

As for RAID, I think a software solution would work but I'm not sure what I am looking for. I want to learn more about RAID and implementing it seems like a good way to learn. Kinda the same thought as using Ubuntu in the first place, I want to learn about it.

---

### Post by SurfaceUnits on 2017-02-07
you can also use a builder guide like

[http://www.logicalincrements.com/](http://www.logicalincrements.com/)
and
[http://www.tomshardware.com/t/build-your-own/](http://www.tomshardware.com/t/build-your-own/)

among many similar sites

---

### Post by SeijiSensei on 2017-02-07
The Intel video on most motherboards is fine for most things except gaming.

I would recommend just installing Ubuntu on the machine and running Windows inside a [VirtualBox]("http://www.virtualbox.com/").  Dual-booting between operating systems doesn't make as much sense as it once did before there were free and convenient methods to run virtual machines.  The only good reason to install Windows on the bare hardware is if you want to play games.  In that case you'll need a heftier video adapter; I prefer NVIDIA myself.

Get yourself at least 8 GB of memory so both operating systems will have room for maneuver. 

If you want to dual-boot Windows and Linux and use RAID, you'll need to invest in a [hardware RAID adapter]("https://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007607&IsNodeId=1&srchInDesc=linux&bop=And&ActiveSearchResult=True&Order=RATING&PageSize=36") with full support for both operating systems.  Good RAID cards are pricey.  Linux software RAID works fine in Linux, but the drives will be invisible to Windows.  If you see a card that mentions "software RAID," it's pretty unlikely to support Linux.  I'd leave out the RAID part for now and get some experience with Linux first.  You can always add more drives to the machine down the road.

---

