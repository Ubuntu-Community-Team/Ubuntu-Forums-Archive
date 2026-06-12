---
title: "silent low cost file server ?"
date: 2006-12-14
forum: The Cafe
---

### Post by techrush on 2006-12-14
The title sums it up im looking for the cheapest and quietest way to run a 250+ GB file server on my home network. A few HD clicks doesnt bother me but the drone of high pitched fans drives me nuts. I was thinking of trying my luck with a used system from some place like [www.retrobox.com](www.retrobox.com) and then just adding storage myself. The only problem with this is i think a lot of these older used systems may be quite noisy.  Any advice or ideas are appreciated....

---

### Post by dbott67 on 2006-12-14
I've got a NexStar LX NAS (NST-375LX) device --- about $80.00 CDN; just add your own hard drive.

10/100 Ethernet, USB, SMB, FTP, Web interface, Passive cooling.

[http://www.vantecusa.com/product-storage.html](http://www.vantecusa.com/product-storage.html)
[IMG]http://www.vantecusa.com/products/nexstarLX/images/lx02.jpg[/IMG]

---

### Post by K.Mandla on 2006-12-14
At risk of sounding like a brute, any old fanless PC (P3 or earlier, even) with a decent network connection and a server install of Ubuntu should be viable. I use an old 750Mhz laptop to serve music around the house, via 11Mbps wireless card. Is that an option for you?

---

### Post by techrush on 2006-12-14
an old laptop isnt exactly what i had in mind but a cheap($250 or less) fanless PC of some sort is. i just dont  know where to look for something like that.

---

### Post by K.Mandla on 2006-12-14
If I recall correctly, a lot of the mini-itx systems are designed to run on AC adapters (not power supplies) and have no fans, since they have to be pressed into a very small space. Check [http://www.mini-itx.com](http://www.mini-itx.com) if you're keen on something brand new, designed as fanless and silent.

---

### Post by K.Mandla on 2006-12-14
> **techrush said:**
> an old laptop isnt exactly what i had in mind but a cheap($250 or less) fanless PC of some sort is. i just dont  know where to look for something like that.
If you want something older that can do the job, Celerons as far back as 400Mhz were shipped without fans. But of course the power supplies still had fans, and would still make a little noise.

---

### Post by marcus2004 on 2006-12-14
I went with a Linksys Nslu2 and upgraded the firmware on it to the Unslung one which allows running a form of linux on it. 

[http://www.nslu2-linux.org/](http://www.nslu2-linux.org/)

[http://www.directdial.com/ca/shoplinksys/item/NSLU2-CA.html](http://www.directdial.com/ca/shoplinksys/item/NSLU2-CA.html) (for a pic)

It can be had for $50 to $100 depending on where you look (ebay is a good choice). You just hook it up and hook a hardrive in enclosure via usb to it. Then if you want to put linux on it you can update the firmware. It is nice and quiet and can do some pretty cool things. I think there are mail servers web servers and bit torrent downloaders for it amount other things.

---

### Post by RandomJoe on 2006-12-14
I have a Dell Optiplex GX200 that is virtually silent (sure wouldn't hear it unless the room is silent) and it is a 1GHz P3.  I got several different models for free from my office, no one else thought they were worth much after the new lease machines showed up.

I've found most of the Optiplex line to be nicely silent, especially the towers - wish I could say the same for the Dimensions...  (Made the mistake of buying one of those expecting the same quietness.)

The stock PSU would be plenty for one or two drives.  I actually shelled out for a large PCP&C PSU for this one, as I am considering putting my 1TB RAID into it (the PowerEdge server I have was hideously noisy until I started swapping fans on it).

---

### Post by AndyCooll on 2006-12-14
I use a box I've cobbled together using my old parts of pc's. Sits in a corner, stores my files and has my printer attached to it. I think it's a P3 933 or something like that. Works great and does what it says on the tin!

:cool:

---

### Post by prizrak on 2006-12-14
Anything with like 400Mhz+ should do the job just fine. Just make sure that the drives are fast enough for 100mbps connection (yes I had a system whose drives could not keep up). As far as fans go, anything that old doesn't really need active cooling. Also look for Shuttle barebone systems I think you can put one together with an HDD for less than $300 and if you look around for used ones even less. They tend to use mobile CPU's so heat is a non issue and fans are extremely quiet.

---

### Post by techrush on 2006-12-15
Interesting to note that the optiplex line is quiet. [www.retrobox.com](www.retrobox.com) has quite a few of them for pretty cheap right now but id still have to shell out money for the drive(s).

Im also very interested in that linksys slug NAS thingy. Looks really cool and also fun to hack around with a bit. 

Its between those 2 solutions but i cant decide :neutral:

---

### Post by RMorris78 on 2006-12-15
i have heard great things about this as well.....

[www.freenas.org](www.freenas.org)

how cant ya love open source:)

---

### Post by prizrak on 2006-12-15
> **techrush said:**
> Interesting to note that the optiplex line is quiet. [www.retrobox.com](www.retrobox.com) has quite a few of them for pretty cheap right now but id still have to shell out money for the drive(s).

Im also very interested in that linksys slug NAS thingy. Looks really cool and also fun to hack around with a bit. 

Its between those 2 solutions but i cant decide :neutral:

I would suggest the Linksys solution as it would take the pain out of configuring it. One thing you might want to find out is what protocol it uses. Not sure if you have any Windows machines and use Samba. I find that in a 100% Linux environment NFS is a better choice as the drives are seen as local. Also with asymetric transfer it tends to be faster.

---

### Post by marcus2004 on 2006-12-15
The nslu2 (slug) can run samba (I am not sure about nfs though) and ftp etc.

---

### Post by Erik Trybom on 2006-12-15
HAHAHA!! I read your topic as "silent cow lost file server". :D 

Sorry about the off-topic. Won't happen again.

---

### Post by techrush on 2007-01-08
i went with the linksys nslu2 and a 250gb USB drive. installed debian etch and am running NFS and netatalk/AFP and its working great...

---

