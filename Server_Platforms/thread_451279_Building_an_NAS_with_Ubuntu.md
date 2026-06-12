---
title: "Building an NAS with Ubuntu"
date: 2007-05-22
forum: Server Platforms
---

### Post by Jaymo on 2007-05-22
I am in dire need of a storage solution with expandability.
I am considering using Ubuntu server as a base for an NAS, but I have a few concerns and would like to seek the help of the Ubuntu community in my endeavor.
In my NAS I would like to see support for
- Raid 0+1
- SMB, SSH, HTTP and FTP access

The only problem is that I'm not sure where to start. If I set up RAID 0+1 in the motherboard's own RAID tool (pre-POST) will that require any extra configuration in the OS?
Secondly, will I have to install each protocol's server separately or is there a metapackage that I can use?
The box should be accessible from Windows, Mac OS X and Linux clients.

Your advice is greatly appreciated,
Jaymo

---

### Post by tribaal on 2007-05-22
Usually when your motherboard takes care of he RAID setup you don't have any additional setup to do in the OS. Your storage space will be viewed as a single SCSI volume.

I don't think there is a NAS metapackage available, but installing samba, ssh, apache and ftpd would be a good start. You might want to check out the forums and google for more info on theses.

Hope this helps :)

- trib'

---

### Post by jethro10 on 2007-05-22
I know its not ubuntu and not quite linux but its close,

what about :-

[http://www.freenas.org](http://www.freenas.org)

its well developed and an all in one solution

J

---

### Post by Jaymo on 2007-05-22
> **jethro10 said:**
> I know its not ubuntu and not quite linux but its close,

what about :-

[http://www.freenas.org](http://www.freenas.org)

its well developed and an all in one solution

J

I had a look at FreeNAS during my research but It didn't seem modular enough for my liking. I figure that if my server is running Ubuntu I can throw on various other servers and applications (e.g. Ventrilo).
If FreeNAS was based on Ubuntu I'd be a bit more enthusiastic about it :).

---

### Post by DrNick on 2007-05-22
A word or two about RAID.

The sad truth is that if the RAID controller is SATA or IDE RAID, and it's on the motherboard, then there is a 90% chance it isn't true hardware RAID, but rather something called fakeRAID.  A google search on it will bring up 100's of links to forums, newsgroups and mailing lists with people attempting to use these devices on Linux.

So what is fakeRAID all about and why is it fake?  Firstly, a true hardware RAID controller will do all the RAID functions on the card itself with dedicated hardware and dedicated memory. In addition to this there will be a RAID BIOS on the card which will allow booting from the RAID device, which will be presented to the system as one disk.  Software RAID on the other hand (as you probably know) does all this in software with any disks you happen to have attached to the system's normal disk interfaces.  FakeRAID is essentially a cost cutting exercise.  IDE/SATA "RAID" controllers which are fakeRAID will not have a dedicated RAID processor to handle RAID functions, nor will they have dedicated memory.  Instead, RAID functions on a fakeRAID card are handled by the CPU of the computer.  So it is, essentially, software RAID, with a RAID BIOS to enable booting from the array.  So why did they do this?  Well, it enables them to sell a product branded as a "hardware RAID" card, with a tiny fraction of the manufacturing costs of a proper RAID controller.  They are of course hoping that people buy it thinking they're getting hardware RAID for what to them seems an amazingly good price.  Well, it isn't.  No such thing as free beer.

So why does this present a problem for Linux?  Well, a fakeRAID card is much the same as a "winmodem", in that, the RAID functions are handled by a windows driver which runs software on the system's CPU to co-ordinate RAID.  The disks themselves are still presented to the system as individual disks, it is up to the driver to work out if they're part of an array and use them as such.  In the linux world, the chances are if you try and install your favourite distro on a fakeRAID array, linux will see the array as what it truely is - the seperate disks themselves.  

The next thing you're probably wondering is, well is there a solution?  Well yes, there is, in fact there are three.  Firstly, if you would like proper hardware RAID, you could go and buy a proper hardware controller.  It is safe to say all SCSI and SAS RAID controllers are true hardware RAID.  People would be pretty annoyed if they paid £300 or more for one of those controllers, only to find it isn't actually proper hardware RAID.  Obviously though, SCSI and SAS will cost you the earth.  There are also proper hardware SATA and IDE RAID controllers, which are made by a company called 3ware.  These controllers cost less than SCSI/SAS RAID, but obviously are still more expensive than cheapo fakeRAID controllers.  If you have money to spend, this would be a very nice option - 3ware make some good hardware.

The second option is to use Linux's own software RAID.  The advantage of this is that you will be able to monitor and admin the array without taking the system down using the excellent mdadmin program.  You will also find performance from a Linux Software RAID device to be better than using fakeRAID.  Unless you have other requirements or want to spend money on a 3ware controller, this would be what I'd recommend.

The last option, is that if you really want to use fakeRAID on linux, you can.  At least, its possible to.  But I'm certainly not saying there won't be problems or that is isn't hard :)  Installing the OS on fakeRAID does vary depending on the distro in question, and also if you're installing from the liveCD or not.  But, the program you need to check out is called dmRAID, short for Device Mapper RAID.  If you'd like to go down this route, this is the URL you need to check out:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Personally however, unless you already have data on a fakeRAID array that you need to use, I'd avoid it.

Hope this info helps, and good luck.

---

### Post by hartz on 2007-05-22
Thanx to DrNick for posting this.

I hate FakeRAID for one reason: If something happens to your motherboard, you're pretty much buggered.

To import the disks from the array on a new motherboard, most FakeRAID BIOSes will reinitialize the disks.  This is so bad you can't even take an existing plan formatted disk and add a "FakeRAID mirror" to it without re-initializing the disk!!!  (Someone correct me if this situation has improved in the last 12 months)

My advice: Steer clear from fakeRAID.

---

### Post by jethro10 on 2007-05-22
> **Jaymo said:**
> I had a look at FreeNAS during my research but It didn't seem modular enough for my liking. I figure that if my server is running Ubuntu I can throw on various other servers and applications (e.g. Ventrilo).
If FreeNAS was based on Ubuntu I'd be a bit more enthusiastic about it :).

I do agree, but i thought i'd point it out just incase you wern't aware of it !!!

Looks like you've opened a can of worms with this FakeRAID thing

good luck
J

---

### Post by EmmEff on 2007-05-22
FWIW, I've been very successful using the built-in software RAID in Linux.  My RAID5 array is built on 5 x 160GB ATA/100 drives, each running on their own IDE channel (which means adding two Promise ATA/133 PCI cards).

My array has been running for a couple of years now on a lowly Pentium II 350 running Dapper (and Gentoo Linux before that).  It's not fast because of the slow CPU but I've had redundant, reliable storage on my home network.

You may want to consider this option as well.  Otherwise, spend the $$$, get a 3Ware RAID card.

---

### Post by regomodo on 2007-06-01
[http://www.smallnetbuilder.com/content/view/27840/77/](http://www.smallnetbuilder.com/content/view/27840/77/)

This guy did it with Ubuntu 6.06 with Raid 5. He went the hardware route and its definetely a project i am considering

---

### Post by EmmEff on 2007-06-01
I would have gone the hardware route as well, but my whole software RAID5 array was less than the price of a capable 3Ware card...  that wasn't in my budget for a home server.

---

### Post by regomodo on 2007-06-01
> **EmmEff said:**
> I would have gone the hardware route as well, but my whole software RAID5 array was less than the price of a capable 3Ware card...  that wasn't in my budget for a home server.

yeah, i know. I'm keeping my eye on LSI Logic cards atm. I don't want to use software raid as i think a 500MHZ mini itx board can't cope with software raid-5 too well. I may be totally wrong but i'd prefer a hardware setup.

---

### Post by EmmEff on 2007-06-01
My setup uses a PII 350 and it works fine...  it's not fast but I was more interested in reliability than performance.

---

### Post by reckless2k2 on 2007-06-01
yeah freenas is a good solution without bugging around in ubuntu to get everything working. smeserver is first class as well.

---

### Post by dfreer on 2007-06-02
Can you use linux software RAID with unmatched IDE hard drives, let's say a maxtor 160GB and a seagate 250GB :D I'm pretty sure the I in RAID also stood for Identical Disks, but my question is Linux software RAID limited by this?

---

### Post by AlanRogers on 2007-06-03
RAID = Redundant Array of Inexpensive Disks. The change to Independant is recent and not fully sanctioned or adopted. That said, if you use differing sized disks, you'll be wasting the extra on the larger one because you can only mirror or stripe identical sized disks.

---

### Post by EmmEff on 2007-06-03
> **dfreer said:**
> Can you use linux software RAID with unmatched IDE hard drives, let's say a maxtor 160GB and a seagate 250GB :D I'm pretty sure the I in RAID also stood for Identical Disks, but my question is Linux software RAID limited by this?

The "stripe" size can only be as large as the smallest disk, so if you used a 160 and a 250, the "stripe" size would be 160GB and you'd be wasting 90GB on the 250GB disk.  You could use this space, just not in the RAID array.

FWIW, one of my disks is a 200GB drive because I couldn't get a 160GB...  so I have 4 160GB drives, and a 200GB drive.

---

