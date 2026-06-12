---
title: "Computer setup ideas (RAID array and Myth TV)"
date: 2007-01-22
forum: The Cafe
---

### Post by Peepsalot on 2007-01-22
So lately I've been thinking about building a couple new computers for my home.  Just wondering if anyone has some advice, comments, alternative ideas, words of wisdom, or if you'd rather just call me crazy.

So my idea is to build two computers:
1) A headless file server on the local network, w/ RAID 5 array, 4 drives, ~1TB, kept in a closet
2) A media center box (Myth TV) for the living room, with TV out, capturing hardware, etc.

And I would keep my existing computer as a general purpose machine that stays on my office desk.  

I want the media center (Myth TV) box to be in as small a form factor as possible while still meeting the requirements of a media center PC.  Hopefully resembling something like a dvd or vhs player next to my TV.  I want this box to be very silent, possibly even going to the extreme of having no moving parts.  Compact flash for boot drive, passive cooling, etc(...well crap I might want a dvd drive with moving parts :rolleyes: ).  I think compact flash hard drive will be good since I only need room for the OS and apps(2GB maybe).  For all other files, it should be able to store and retrieve them from the networked file server.  It may need substantial processing power for the purpose of encoding/decoding high res video.

The file server on the other hand can be bulky, ugly, noisy, etc since I can hide it away in a closet and leave it there.  It's only IO will be a gigabit ethernet card. For this box I think CPU requirements would be very small since pushing data back and forth doesn't require much processing power(AFAIK).

I think I will build my file server first, pause for a bit to replenish my pocket book, then start on the myth TV box.

So right now I am trying to figure out my parts list for the file server.  I have never made a RAID array, but it's something I've always wanted to do.  I have heard that there are two kinds of RAID cards: real hardware RAID, and cheapo software RAID.  Apparently the software ones rely on the CPU to do all the work, while the real hardware process the splitting/merging of data amongst the drives themselves.  So real hardware RAID sounds nice, but the only problem is I think they don't sell for any less than $500 or so.  Is there a way to keep the costs down without hurting performance too much?

---

### Post by teet on 2007-01-22
Why not make the fileserver your mythbackend as well?

If you want a small, silent box to sit on top of your TV it would work better if it was a mythfrontend only.  I think it would work out cheaper that way...in your frontend machine you could go with a really cheap VIA C3 processor that runs really cool (I think they're like 1.0-1.5 Ghz or so, more than enough for a frontend).  Slap in a halfway decent video card with the proper outputs, a wireless card, and you're good to go.

-teet

---

### Post by Peepsalot on 2007-01-22
Ok, I guess I didn't realize MythTV was already designed to be split into frontend/backend.  I have more homework to do :oops:

---

### Post by teet on 2007-01-22
haha...mythtv really has a lot of features.  It can be a bear to work with at times, but if you can gets things working right you'll have yourself one sweet setup.

For what it's worth, there are a few places on the net that sell preconfigured mythboxes.  If you want it to "just work" you may want to look into one of those.  But that kind of takes all the fun out of building it yourself...even if your version does end up costing just as much money and a ton more time than the prebuilt one.

-teet

---

### Post by saulgoode on 2007-01-22
I will share a couple of my thoughts but my knowledge is dated and should be taken with a grain of salt (perhaps even a cattlelick-sized block).

I don't think that CPU load is a major concern and would recommend that you save some bucks going the software RAID route. You will need to purchase a multi-channel IDE controller such as the "Supermicro Add-on Card AOC-SAT2-MV8" (there is no advantage to RAIDing two partitions if they are on the same IDE ribbon cable). Such controllers run about $100-150. You can always add a hardware RAID controller at a later date.

I believe ATA harddrives still hold an advantage with respect to $/G but higher-end SATA offer faster disk access. I suspect that if you are striping your drive , the higher SATA disk access will probably not come into play (four ATA drives will saturate the PCI bus). You might be able to save some $$$ by using ATA drives (worth investigating, anyway).

---

### Post by Mateo on 2007-01-22
sounds like a fun project.  if you don't want the hassle you can just get a dragon:

[http://mythic.tv/product_info.php?products_id=44](http://mythic.tv/product_info.php?products_id=44)

but pretty expensive.

---

### Post by migla on 2007-01-23
I believe the choice of tv-capture card (if it has the encoding built in) will let you use it on a back end box with not too much processing power...(?)

---

### Post by RandomJoe on 2007-01-23
I currently have the RAID setup you are thinking about - I use software RAID 5, originally used two of the PATA add-in cards they used to give bundled with new hard drives.  I have since upgraded to SATA, and bought a 4-port SATA card.  The software RAID's processor loading is insignificant.  My server has CPU scaling enabled and _never_ comes off 600MHz (it's a 2.4GHz P4) during network I/O (with gigabit NIC) unless I'm using SCP, which of course has the encryption overhead.

I also used to have MythTV set up, I had the backend computer - a beefier machine so I could have sufficient hard drive space right inside (faster access than across the network, I liked high-quality which meant high bitrate).  Put it in the back closet with the server, and I could watch TV from any computer in the house - or even outside, via wireless.  54Mbps is sufficient for most viewing.  This route also means you have a lot more options in getting the low-power, silent machine for set-top.

Edit:
I thought I would clarify - you do NOT need a RAID card of _any_ sort to use the Linux kernel's software RAID.  Just get cards that attach the drives to the system.  The PATA cards I used were regular 'ol dumb IDE interfaces.  The SATA card does have "software raid functionality" in it, but I didn't enable it, I just use the kernel's RAID support.

---

### Post by mips on 2007-01-23
> **Peepsalot said:**
> 
I want the media center (Myth TV) box to be in as small a form factor as possible while still meeting the requirements of a media center PC.  Hopefully resembling something like a dvd or vhs player next to my TV.  I want this box to be very silent, possibly even going to the extreme of having no moving parts. 

You get some nice cases that look similair to hi-fi / dvd equipment. Don't ask me for a link but i have seen them. 

You will have to look at a low power/heat cpu and use passive cooling for it.

---

