---
title: "A (Server) Beginner's Question"
date: 2008-03-13
forum: Server Platforms
---

### Post by LeoSolaris on 2008-03-13
I am trying to make a NAS set up with an old PCCHIPS Mobo, running a VIA C3 chipset ($20 Ebay special), and a 30G 2.5' ATA, with a 2.5' - 3.5' converter cable, from my old laptop. (Motherboard blew on it) I currently only have 128M of RAM, but I can up it a little if needed. I found a cheap wire computer monitor stand at Walmart that I intend to bolt it all into then set the wireless router on top since I intend to just wire it to my wireless router to use it throughout the house with my new laptop. (The desktop is wired to the wireless router simply, too, because it is close enough and I don't have the money for an extra card.)

My question is: will Ubuntu be light enough on the system to work properly? Can Ubuntu operate as a NAS, or should I look at other alternatives like FreeNAS?

Incidentally, will this even work at all, or does having a server require some form of specialize hardware setup? From everything that I have researched so far, I 'should' be alright with these pieces in the creation of a server, but since this is my first try at this part of computing, I want to make sure. I know it will be slow and grumpy, but I will not be putting anything truly critical on it, since it's a test run. Sort of a proof of concept, if you will, to learn the basics with.

I am not going to try a RAID array just yet, since the Mobo doesn't support it natively anyways. I am not truly sure if one of the RAID controller cards would even work properly, since PCCHIPS is a little on the cheap side, and may not have set up the BIOS to even work with one. (I have no idea to tell ya the truth, never found any info on it at all after a few months of casually looking.)

I did find an industrial flash drive that connects to ATA 133 that I could fit the OS on and use the second HD as the shared drive, is this a possible configuration? If so, is it going to be a lot more difficult to arrange?

I just love being a noob...

Thanks in advance!

Leo S.

P.S. Sorry bout the deluge of questions. I figured it was better to ask than spend any more money on the project.

---

### Post by faulkes on 2008-03-14
> **LeoSolaris said:**
> 
My question is: will Ubuntu be light enough on the system to work properly? Can Ubuntu operate as a NAS, or should I look at other alternatives like FreeNAS?


It can be, I run 7.04 server on a 350mhz ppc g4 w/ 256mb of ram, quite snappy for transferring files.

> 
I am not going to try a RAID array just yet, since the Mobo doesn't support it natively anyways. I am not truly sure if one of the RAID controller cards would even work properly,


The raid controller would be worth more than the PC itself
at this point.

> 
I did find an industrial flash drive that connects to ATA 133 that I could fit the OS on and use the second HD as the shared drive, is this a possible configuration? If so, is it going to be a lot more difficult to arrange?


Unknown without details on the flash drive.

More or less, it will do what you are asking it to do.  If you start
planning to store TB's of data, you'll probably want to upgrade.

Faulkes
I just love being a noob...

Thanks in advance!

Leo S.

P.S. Sorry bout the deluge of questions. I figured it was better to ask than spend any more money on the project.[/QUOTE]

---

### Post by LeoSolaris on 2008-03-14
OK  that's good news indeed! I had no idea what to expect out of the server side of Ubuntu. The desktop is nice, but would have been waaay to memory intense to work on that set up.

As for the little flash drive, I can pick one up here... _[http://www.logicsupply.com/categories/flash_memory/40_pin_ide_flash_modules](http://www.logicsupply.com/categories/flash_memory/40_pin_ide_flash_modules)_

They are the precursors to the SSD, little more unstable, kinda like USB flash. They can only take so many read/write cycles. For a proof of concept built, just to learn from though, that will not really be an issue.

The idea is to use one of the little 1G (or how ever small a size I can shoehorn the OS into so I can save a dime or two) DOM's to hold the server OS, and share the full power of the recycled notebook hdd.I may upgrade the little 30G notebook hdd later on, but that will not be for some time in the future.

---

### Post by dca on 2008-03-14
This is my opinion:  I think it's easier to install & config Ubuntu Server Edition (any vers) than FreeNAS...  There were some issues I had in the past that put me off when it came to FreeNAS.  Wouldn't work because ethernet driver req'd (I can understand wireless hardware needing drivers/config but...) and a few others.  The only thing that made it easier (if I remember correctly) was the particular webmin utility on the FreeNAS side.  It's been so long since I bothered installing or using any webmin utility I couldn't tell you which one is better...
 
For a NAS running Ubuntu, the install was quicker, more options to config partitions during instal...  Once Ubuntu was installed, I installed SSH, Samba, VSFTPD, and some vers of Webmin and that was it...

---

### Post by volkswagner on 2008-03-14
> I did find an industrial flash drive that connects to ATA 133 that I could fit the OS on and use the second HD as the shared drive, is this a possible configuration? If so, is it going to be a lot more difficult to arrange?

Not sure why you want to do this.  Those seem pricey.  Depending on your reasons, I would opt for a larger ATA disk for the files.  Use the smaller 2.5 for the O/S.

I don't think 1G is enough for the O/S and swap space.

To keep Things on the cheap:
[LIST=1]
[*]Install the Ubuntu Server of your choice on the 2.5"
[*]Partition the drive to allow OS and Data on different partitions
[*]Save your money and get a big disk for data
[/LIST]

Again without knowing why you want the flash disk(reliability, energy savings, etc) I would install like so:

Partitions
[LIST=1]
[*]2-5 gig ext3 mount at / (root for OS)
[*]512 meg mount as swap
[*]remainder can be devided or all allocated to /home ext3 or /home and /data (or any name of your choice)
[/LIST]

---

### Post by Brazen on 2008-03-14
Be sure you use Ubuntu 6.06.  Despite the fact that you should stick to LTS releases for any server that is of any importance, I've heard any release later than 6.06 will not run on the Via C3 processors.

But really if anything, consider yourself lucky in being forced to go with an LTS release, it's much more stable and reliable than the later release (due to different priorities for the LTS releases).  I just hope that the next LTS release (Hardy, due in April) will again have support for the VIA C3 processors.

Also, that system will be plenty powerfull for an Ubuntu LTS Server system.  I've run Ubuntu LTS servers with as little as 48mb of RAM and they are still quite snappy.

---

### Post by jonabyte on 2008-03-14
I am running a test web application server, with Ubuntu 6.06 server edition and 64mb ram and have had no problems. It does get a fair bit of traffic throughout the day.
It doesn't compare with a file server but its proof that it runs well.

---

### Post by LeoSolaris on 2008-03-14
> **volkswagner said:**
> Not sure why you want to do this.  Those seem pricey.  Depending on your reasons, I would opt for a larger ATA disk for the files.  Use the smaller 2.5 for the O/S.

I don't think 1G is enough for the O/S and swap space.

To keep Things on the cheap:[LIST=1]
[*]Install the Ubuntu Server of your choice on the 2.5"
[*]Partition the drive to allow OS and Data on different partitions
[*]Save your money and get a big disk for data[/LIST]
Again without knowing why you want the flash disk(reliability, energy savings, etc) I would install like so:

Partitions[LIST=1]
[*]2-5 gig ext3 mount at / (root for OS)
[*]512 meg mount as swap
[*]remainder can be devided or all allocated to /home ext3 or /home and /data (or any name of your choice)[/LIST]

I was hoping that a gig would be large enough for the root and swap, and toss the home over in the big drive on a small partition. It's not like anything other than the very bare necessary daemons will be running or installed. The flash was just to actually see if it worked the way I wanted, and to cut down on noise, since the HDD wouldn't have spun up unless there was activity, but if it will take that much for the OS, I might as well do it all on the small laptop HDD. If I find some spare change I may try it out later with a referbed 2 gig.

[quote=dca]This is my opinion: I think it's easier to install & config Ubuntu Server Edition (any vers) than FreeNAS... There were some issues I had in the past that put me off when it came to FreeNAS. Wouldn't work because ethernet driver req'd (I can understand wireless hardware needing drivers/config but...) and a few others. The only thing that made it easier (if I remember correctly) was the particular webmin utility on the FreeNAS side. It's been so long since I bothered installing or using any webmin utility I couldn't tell you which one is better...
 
For a NAS running Ubuntu, the install was quicker, more options to config partitions during instal... Once Ubuntu was installed, I installed SSH, Samba, VSFTPD, and some vers of Webmin and that was it...[/quote]

Thanks! That was what I was worried about. FreeNAS is still prerelease, and while nothing highly important will sit on this, reliable is a good thing.

[quote=Brazen]Be sure you use Ubuntu 6.06. Despite the fact that you should stick to LTS releases for any server that is of any importance, I've heard any release later than 6.06 will not run on the Via C3 processors.

But really if anything, consider yourself lucky in being forced to go with an LTS release, it's much more stable and reliable than the later release (due to different priorities for the LTS releases). I just hope that the next LTS release (Hardy, due in April) will again have support for the VIA C3 processors.

Also, that system will be plenty powerfull for an Ubuntu LTS Server system. I've run Ubuntu LTS servers with as little as 48mb of RAM and they are still quite snappy.[/quote]

!! Interesting, they stopped supporting the C3's. That certainly kept at least a couple of hairs from turning gray or being yanked out.

Well, if this mobo and HDD last 2 more years, it will suprize me.

Leo S.

---

