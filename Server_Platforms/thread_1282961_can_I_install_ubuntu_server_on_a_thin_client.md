---
title: "can I install ubuntu server on a thin client?"
date: 2009-10-05
forum: Server Platforms
---

### Post by kustomjs on 2009-10-05
Hey Guys
I just wanted to know if I could install ubuntu server onto a thin client?

---

### Post by grturner on 2009-10-05
> **kustomjs said:**
> Hey Guys
I just wanted to know if I could install ubuntu server onto a thin client?

what do you mean by thin client?

As to our other poster.
It is much more helpful to start a new post with your questions, but you should look into wine for running windows programs under linux. you wont get total 100% success but it's getting better and better over the years.

---

### Post by kustomjs on 2009-10-05
like I said a thin client google it then you know what Im talking about.

---

### Post by lykwydchykyn on 2009-10-05
> **kustomjs said:**
> like I said a thin client google it then you know what Im talking about.

Do you want to install it ON the thin client, or use the thin client with a terminal services type setup?

You can do both, though whether the former will work or not depends entirely on the specs of the thin client hardware or any limitations the manufacturer might have built in.

What is the make/model/specs of the thin client in question?

---

### Post by kustomjs on 2009-10-05
well see what I was going to use it for is for a boot server for my polycom phone setup. so I need to know the requirements for the server to do this with a thin client.

---

### Post by lykwydchykyn on 2009-10-05
It's been a while since I've installed Ubuntu Server (mostly use Debian on servers), but I believe the base install was around 500-600 Mb.  Supposedly the minimum RAM is 32 Mb and the minimum processor is a Pentium 2, though I would expect extreme slowness at those specs, and you probably don't want to have to swap on a thin client's SSD.

Do you have a thin client you intend to do this with, or are you looking for specs so that you can acquire one that will do the job?

What services will you be installing for this server?

It might be a good idea to set up the server you need in a virtual machine and see if it works.

The more information you give, the better information you'll get back, so please give as much information as you can.

---

### Post by kustomjs on 2009-10-05
only services would be on it would be apache and ftp only. I dont have a thin client picked out so whats a good one to use? because I probley buy a cheap one off of ebay.

---

### Post by scorp123 on 2009-10-06
> **kustomjs said:**
> like I said a thin client google it then you know what Im talking about. Can you please be more specific??? There are several dozen brands and types of "thin clients" out there. With some it might be possible (I have done that myself), with other it simply will not be possible.

So can you please be more specific?

---

### Post by scorp123 on 2009-10-06
> **kustomjs said:**
> I dont have a thin client picked out so whats a good one to use?  Sorry, but that's just daft. If you don't have the thin-client yet then you probably don't even know its tech specs and thus if it even is possible to install anything else on it?!

Why not go for a "nettop" PC? They have the same "Atom" CPU's like netbooks, only consume very little power, and being more or less PC's they will have harddrives and maybe even CD drives, so it will be easy to install any OS --incl. Ubuntu Server-- on them.

Most thin-clients will _NOT_ allow you to do that. Fujitsu-Siemens "Futro" thin-clients for example are very very PC-like but there is no way to connect any disk to it or to replace the embedded OS. Fail. Some VXL "Itona" thin-clients have an internal IDE-connector so it is possible to remove Windows CE and install Linux on it. I have done that myself:
[http://ubuntuforums.org/showpost.php?p=7328985&postcount=13](http://ubuntuforums.org/showpost.php?p=7328985&postcount=13)

Other thin-clients such as the "Sun Ray" will not ever run anything because they don't even have a CPU of their own to begin with.

So "thin-client" can mean many things and you better do your homework or else that thin-client that you buy will be a useless piece of plastic for you. :D

---

### Post by kustomjs on 2009-10-06
I am looking at HP T5520 or VXL Itona TC3533-LI on ebay.

---

### Post by scorp123 on 2009-10-06
> **kustomjs said:**
> VXL Itona TC3533-LI on ebay. That one might work. And the "LI" seems to indicate that there already is some form of Linux on it. 

If they have not changed the design then it should have a VIA C7 CPU, around 1 GHz and 256 MB RAM. And it should have 1 maybe even 2 internal IDE connectors. I think you might get it working with this.

Taking a quickie look at the specs:
[http://www.vxl.net/products/tc3533-li-pro.html](http://www.vxl.net/products/tc3533-li-pro.html)

There it says "64 MB IDE Flash" ... so that one definitely has IDE connectors inside.

Please read this posting on how I modded my VXL (... just ignore the rest in the posting that is irrelevant to you, OK? In that thread we were discussing some kind of sophisticated "parental control" software ... just skip over those parts and scroll further down to the thin-client part, OK? )

[http://ubuntuforums.org/showpost.php?p=7622202&postcount=17](http://ubuntuforums.org/showpost.php?p=7622202&postcount=17)

Here's how mine looked for a while :lolflag:

[IMG]http://i121.photobucket.com/albums/o217/scorp123_2006/Hardware/th_HPIM0651.jpg[/IMG]

Link to full-size picture:
[http://i121.photobucket.com/albums/o217/scorp123_2006/Hardware/HPIM0651.jpg](http://i121.photobucket.com/albums/o217/scorp123_2006/Hardware/HPIM0651.jpg)

Lo' and behold ... the first "chair computer". I have a small daughter and she was touching everything ... so I could not spread the parts over my table, I had to go up and up so the cables were out of reach for her :D

So ... what do we see here:


Table:

- external PC-type power supply so I could power up an external CD drive. That VXL thin-client has two IDE connectors but only _ONE_ internal power cable for drives. As it is unable to boot via USB (some limitation in the BIOS it seems? The option is there but it doesn't do a thing ...)  I had to come up with a way how I might power two devices: the 8 GB IDE Flash drive _AND_ an external CD drive.

The solution: Unplug the VXL's own power supply from the motherboard and have it powered by an external PC-type power supply. Taddaaaa. It works. With that construction my VXL was able to boot off a standard Ubuntu desktop CD (32-bit).


First chair:

- 2.5" Laptop HD. Works. But there is almost not enough space in the inside of the VXL's case. Instead I placed that 2.5" laptop harddisk into an external USB case that is connected via a USB cable. Works tip top now.

- behind the 2.5" Laptop harddrive you can see the original 32 MB IDE-Flash drive (the thing that looks like a memory bank and which is standing upright on the chair, just behind the harddrive) that contains Windows CE. Yuck.

- behind the IDE-flash drive you can see my VXL thin-client


Second chair:

- IDE CD drive, getting its power from the external power supply and connected to the VXL's 2nd internal IDE connector

The first internal IDE connector is occupied with that 8 GB IDE-Flash from Transcend.


After Ubuntu was installed I removed the external power supply and the CD drive, I put everything back together ... and taddaaaaa. It works.

Just don't expect any speed miracles from that thing. Those VXL's are slooooow (around 1 GHz max. speed) and they don't really have lots of RAM.

Talking of which: I tried to put more RAM inside but it seems there is a limitation in the BIOS?? My VXL can't see beyond the first 384 MB of RAM. I tested with several 1 GB RAM banks that I was able to borrow and all of them would only show 384 MB .... I felt this was quite a waste so I put back the original 256 MB RAM bank. So for now I am running with that.

I use my VXL mainly for remote access, VPN, Dropbox, and Torrentflux (a BitTorrent client that runs on top of Apache ... so I can login from my office and tell it to download Linux ISO's and what not for me while I am at work .... )

Good luck and have fun with your's :D

---

### Post by kustomjs on 2009-10-06
well I bought that VXL Itona TC3533-LI and I wanted to know what kind of memory it uses and your saying 384 is the max memory that is allowed on it and I also bought a 1GB IDE-Flash.

---

### Post by scorp123 on 2009-10-06
> **kustomjs said:**
> well I bought that VXL Itona TC3533-LI and I wanted to know what kind of memory it uses Check the link I gave earlier. There is a link to a PDF datasheet. And that one says that your's uses SDRAM modules.

> **kustomjs said:**
>   and your saying 384 is the max memory that is allowed on it  Well, with mine it seems so. My VXL takes DDR2 modules ... but no matter what I put in there (1 GB modules, 2 GB modules ...) I only see the first 384 MB. It's either a limitation of the CPU or the BIOS. Not sure why that is.

> **kustomjs said:**
>  and I also bought a 1GB IDE-Flash. That might be enough for a really small Linux distro such as "Damn Small Linux", "Puppy Linux" or for a smaller BSD variant. But 1 GB might not be enough for a big desktop distro such as Ubuntu. BTW, you could add USB sticks and include them in your partitioning too, e.g. one stick could be /home, another one could serve as /usr, and so on. So if you have any spare USB sticks I'd use them that way and thus increase the VXL's "disk capacity". Or you do it like I did and simply hook up an external harddrive of sufficient size via USB. Problem solved: you'd put the root filesystem "/" and the basic OS on that IDE-Flash drive, the rest could live on the USB disk ....  Not really efficient speed-wise, but those VXL thingies are no speed miracles anyway.

---

### Post by kustomjs on 2009-10-06
I am going to use ubuntu server not desktop so I think I should be fine with that 1GB card.

---

### Post by hantechbl on 2009-10-06
You have to have enough ram, cpu power, hdd space, and be able to boot of cd/usb/mem card for install

---

### Post by kustomjs on 2009-10-06
I am not a newbie here I know what all I need to do. I have a ubuntu server on 10gb hard drive and 128mb of memory and like 933Mhz P3 so I think I know what I need.

> **hantechbl said:**
> You have to have enough ram, cpu power, hdd space, and be able to boot of cd/usb/mem card for install

---

### Post by scorp123 on 2009-10-07
> **hantechbl said:**
> You have to have enough ram The alternate install and the server install CD's will run with as little as 64 MB RAM. It's only the desktop Live CD that needs 256 MB RAM or more. So RAM should not be an issue.

> **hantechbl said:**
>  cpu power My VXL has 1 GHz, the model OP bought has 800 MHz. That's more than enough for Linux :)

> **hantechbl said:**
>  hdd space That's only an issue of you leave those thin-clients "as is". The 32 MB IDE-flash disk my VXL thin-client shipped with was definitely too small for any serious OS ... So I replaced that one with a 8 GB IDE-Flash from Transcend and now it works tip top. OP did the same and bought a 1 GB IDE-Flash. For a server install this might be enough, especially if he ditches unneeded or unwanted packages.

> **hantechbl said:**
>  and be able to boot of cd See above. No problem whatsoever if you know how.

---

### Post by scorp123 on 2009-10-07
> **kustomjs said:**
> I am going to use ubuntu server not desktop so I think I should be fine with that 1GB card. If you ditch unneeded stuff and keep the install to an absolute minimum ... Yes, definitely. No problem.

You could still hook up an external HD via USB and then mount that one as e.g. /home .... That's what I did, and it works OK.

I may have found yet another use for those VXL thingies ... The company I work for will participate in a technology exposition. We were already there last year ... and guess what: The WiFi access the organisers were supposed to give us failed for several hours. That sucked.

This year we're participating again ... So why not turn my VXL into a 3G router? If you buy 3G/WiFi routers in a store they are expensive like hell. So given that I have Linux on my VXL and given that I own one of those 3G/UMTS/HSUPA USB sticks (which works tip top on Linux) I think I could easily build a 3G router out of this thing ... So if the exposition's WiFi fails again I can hook up my VXL to my demo machines and still have Internet ...

This really sounds like a fun experiment I should definitely try. :D

---

### Post by kustomjs on 2009-10-07
now on that VXL then client was the IDE-flash a 40 or 44 pin?

---

### Post by scorp123 on 2009-10-07
> **kustomjs said:**
> now on that VXL then client was the IDE-flash a 40 or 44 pin? Standard 40-pin IDE.

---

