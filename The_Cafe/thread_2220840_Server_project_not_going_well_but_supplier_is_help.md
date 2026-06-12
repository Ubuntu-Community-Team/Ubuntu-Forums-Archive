---
title: "Server project not going well but supplier is helpful"
date: 2014-04-29
forum: The Cafe
---

### Post by m-dw on 2014-04-29
Just thought I'd share my experiences, because I'm not in a position to actually install an OS on my server, and like the crowd here.

Bought a load of bits with the aim of building a server.  Essentially quite a simple build:
[LIST]
[*]Jetway dual-core Atom D525 motherboard with 6 SATA II ports.
[*]CFI NAS case with 4 hot-swap and 2 internal drive bays
[*]2.5" drive for OS
[*]5 x 3.5" drives for RAID 10 array
[*]4GB RAM (official maximum for the board though it is reported to go to 8GB)
[/LIST]

The case importer let the supplier down, so it was about 3 weeks later than planned.  Case finally arrived.  Assembled the system and it just failed to POST and the fans and disks completely failed to spin up.  Took RAM out, still nothing, so phoned the supplier.  Known possibility of incompatibility between case PSU and motherboard, so he test same combination with same result as me.  Sends out a brand new FSP180 power supply and arranges to collect the dud by UPS next day.

Assemble the system again (well just put the the PSU in really).  This time disks spin up, lights and fans come on, but still no POST.  Take RAM out and restart.  Continuous long beeps. Still no display on monitor.

Ring supplier, not sure if its RAM or mainboard, but I didn't buy RAM from him (it is Kingston Value RAM, matching the motherboard specification).  Supplier recomends the same brand, but currently has no stock, so is sending me the known working SoDIMM he used in his test-bed in the mail to rule out mainboard failure.  

Amazon (who I bought the RAM from) have told me it is past its 30 day return window.  Thought I'd share this story to illustrate benefit of going to a small independent supplier over a massive discounter.

---

### Post by m-dw on 2014-05-01
Sigh... test RAM still not arrived....

---

### Post by JayKay3OOO on 2014-05-04
I buy all my PC build bits from Ebuyer.com - I had a dead board and they sent a delivery guy around to to pick it up the next day for free.

Good luck though, always sucks when hardware fails.

---

### Post by PJs Ronin on 2014-05-04
Add me to the 'interested bystanders' list.

---

### Post by m-dw on 2014-05-07
I should have mentioned the supplier by name.  They are [LinITX.]("http://www.linitx.com")  As the name suggests, they are Linux friendly, and specialise in miniITX.

And.... the memory arrived on Friday and it worked.  Big relief that there were no problems with the motherboard at all, so I've ordered memory of the same specification (but maxing the board to 8GBytes).  I had to order it from DABS, as my guy is out of stock, but he's said I can hang onto the RAM until mine arrives so I have a working home server.  Had a few problems with the installation, more to do with difficulties creating a bootable startup disk from Ubuntu 14.04 (on desktop) than anything else.

Am at last wiping my old NAS with srm before preparing it for sale.

So far I have the server running as:
[LIST]
[*]Logitech Media Server (transcoding OggFLAC to FLAC without breaking a sweat)
[*]NFS4 server
[*]DNS forwarder (will add local DNS zone later)
[*]Local NTP server
[*]Web server
[/LIST]

Coming soon:
[LIST]
[*]DHCP (also to update local DNS zone)
[*]DNLA media server (with transcoding)
[*]OpenVPN server (so I can access it without exposing too many services directly to the Internet.
[*]IMAP Server
[*]Webmail interface to IMAP server
[/LIST]

Before I do all that though I need to set up automatic backups.  I can't off-site them but I don't really have a business case as it's a home server.

---

### Post by ssam on 2014-05-07
If the original RAM from Amazon was defective you are entitled to a replacement or refund. You are covered by statutory rights regardless of their returns or guarantee policy.

Also, LinITX are a great shop. I have a similar NAS setup from them, though I currently have 3 3TB drives in BTRFS raid1.

---

### Post by mastablasta on 2014-05-08
nice shop. seems to have quite expencive components. are they all of good quality or high performance or why such prices? i am still searching for a small server that would do pictures and films backups and that i could access all these relatively fast. i was thinking Rpi, but it has it's limitations.

actually is Atom fast enough for server accessed by a few people (4-8)?

---

### Post by ssam on 2014-05-08
> **mastablasta said:**
> nice shop. seems to have quite expencive components. are they all of good quality or high performance or why such prices? i am still searching for a small server that would do pictures and films backups and that i could access all these relatively fast. i was thinking Rpi, but it has it's limitations.

actually is Atom fast enough for server accessed by a few people (4-8)?

Should be fine. Serving files is not especially CPU intensive, and the recent atoms are 64bit dual-core with hyperthreading. Disk and network bandwidth are probably the things you want to worry about, and having a board with gigabit network and SATA is a big step up from a raspberrypi (where the ethernet competes for USB bandwidth with your storage (I like the raspberrypi for many tasks, but its not great as a file server)).

---

### Post by mastablasta on 2014-05-08
ok but on lintx site boards cost almosts as new HP micro server. i am sure the atom is more energy saving but the HP server's CPU is faster. and with the baord you srtill need, ram, PSU, disk... while the server has htis included. i was expecting to see baords with atoms arround 100-130 EUR not 200EUR. which is why i wonder is the quality of these baords so good or the CPU maybe so efficient/ne wor something.

curiously i can not find many baords with low power AMD APU. the E series i mean...

well so far i have Rpi as media center and works fine for what i need it. but i am still looking for something that would be low power and efficient at doing backups of picture during night from family computers. and i know there are NAS boxes that do that quite nicely, but they are limited in what you can do with them as well as in upgrade options. plus those with 4 drive bays are kind of pricy. and disks can fill fast if we decide to get a an HD camera in the future or better photo camera.

i was thinking a descent Atom baord in ATX frame. but usualyl htose baords have limits on 2 sata plugs. or the SATA is slower trasfer rate.

---

### Post by m-dw on 2014-05-08
> **mastablasta said:**
> nice shop. seems to have quite expencive components. are they all of good quality or high performance or why such prices? i am still searching for a small server that would do pictures and films backups and that i could access all these relatively fast. i was thinking Rpi, but it has it's limitations.

actually is Atom fast enough for server accessed by a few people (4-8)?

I got a Jetway NF99FL-525.  I'd never heard of Jetway before this project, but my main reason for choosing it was the 6 on-board SATA II ports, and the (undocumented) support for 8Gig of RAM.  I also got a case with 4 front-loading drive bays.  I couldn't find an equivalent bare-bones system for less, and proprietary NAS appliances aren't as flexible.  And it's been a great learning process (both the physical build and the install/configure).

Performance-wise it's great even with "only" 2Gig RAM.  Am getting about 350Mbit/s sustained reads and about 200Mbit/s sustained write over NFS4 (single transfer) with no attempt at tuning beyond enabling jumbo frames.  It can achieve the same transfer rates while transcoding AAC+ radio streams to FLAC on the fly than streaming to 4 receivers in sync, so I would think it's quite capable of serving files to 8 users - possibly a bit over the top really.

---

### Post by m-dw on 2014-05-08
> **mastablasta said:**
> ok but on lintx site boards cost almosts as new HP micro server.

I looked at some HP micro-servers with similar thoughts as you, but none of them met my specs.  Also, many of them come with a single small disk so you still have to buy additional storage.  The alternative was a NAS of some sort, but I eventually decided that they were too limited.

---

### Post by mastablasta on 2014-05-09
> **m-dw said:**
> , but my main reason for choosing it was the 6 on-board SATA II ports, .


that part caught my attention as well!

so how much was the total?

i found a nice mobo with 6 sata 6gb but it's for FM2 socket and micro ATX. but the celerons they sells would use way more power than Atom. atom baords they seem to have mostly odl here and usualyl only 2 or max 4 sata2

HP micro servers do come with relatively small 250 GB disk. it is ment for system. however they have many configurations and options. you can get it with more ram and no disks for example. then you can add a disk in DVD drive or as i see some just add a usb stick for the OS and fill the bays with disks

found this HP setup with 4GB ram and no HDD: [http://www.redcoon.at/B534837-HP-ProLiant-MicroServer-N54L_Server](http://www.redcoon.at/B534837-HP-ProLiant-MicroServer-N54L_Server)

though it seems to be using twice as much power than Atom.

---

### Post by m-dw on 2014-05-09
> **mastablasta said:**
> so how much was the total?

Let's not include my time, or the memory which didn't work as I'll get that refunded somehow.

Motherboard: £167.10
Case:  £89
Hard disks £293.93 (1 x 2.5inch 320Gig and 4 x WD Green 2TB)
RAM: £57.26 (assuming it works)

So just a touch over £600.  I'm going to try to sell my old ReadyNAS NV+ with 2 disks on EBay to recoup some of the cost, and am salvaging the two newest hard-drives from it for use in a workstation project later in the year.

I should also include the £2.97 I spent on a motherboard speaker which I didn't need (mobo has one)

I don't know the actual power draw, but I suspect it to be about 60W running flat out, and significantly less when idle.

---

### Post by mastablasta on 2014-05-10
and the PSU?

all together quite expencive (i am looking at price without disks) though it will be able to accomodate 6 hard disks and low energy foot print.

---

### Post by m-dw on 2014-05-10
> **mastablasta said:**
> and the PSU?

all together quite expencive (i am looking at price without disks) though it will be able to accomodate 6 hard disks and low energy foot print.

The PSU was included with the case.  For some reason it didn't work with the motherboard, and LinITX replaced it for free with one from their range.  I got the impression it was a known issue with cases from that manufacturer (CFI).

I'm not convinced it's that expensive in comparison to a pre-assembled server even taking the cost of the disks out of the equation, and lowest price is probably not the best way to choose something I'm hoping to keep for 10 years or more before it needs replacing.  All in all I'm happy with it, and I think I'd be less so if I'd compromised on anything (e.g. the front-loading drive bays).  It has a PCI slot and a miniPCIe so could add an eSATA controller later if I run out of storage.

---

### Post by m-dw on 2014-05-12
An update... The Kingston Value RAM supplied by DABS doesn't work either.  This is a real pain, as I was hoping to get it up to 8Gig so I could basically stop messing about with it.

---

### Post by mastablasta on 2014-05-13
hmm strange Kingston is a descent brand. so the baord recognises only 4 GB or nothing at all?

---

### Post by m-dw on 2014-05-13
> **mastablasta said:**
> hmm strange Kingston is a descent brand. so the baord recognises only 4 GB or nothing at all?

I was taking a chance trying to get the board to accept 8GBytes with the second lot TBH. There are some reviews on NewEgg that say the board accepted 2x4Gig modules.  The first lot was **exactly** to specification on paper.  2 x 2GByte DDR3 1066 Non-ECC unbuffered and the board simply didn't post.  The second lot was 2 x 4GByte modules, and it simply wasn't recognised by the board.

At the moment its got a borrowed 2GByte 800MHz module in, and while performance isn't suffering as a result, I had hoped that I could get it running with 8Gig so I wouldn't have to worry about the system running out of memory and starting to use swap.  I've decided to play it safe and get 4Gig of compatibility tested RAM from Crucial.

---

### Post by pqwoerituytrueiwoq on 2014-05-13
> **m-dw said:**
> The PSU was included with the case.  For some reason it didn't work with the motherboard, and LinITX replaced it for free with one from their range.  I got the impression it was a known issue with cases from that manufacturer (CFI).rule of thumb, if the PSU comes with the case it is a very cheap PSU that i would not recommend trusting as far as you can throw it

---

### Post by m-dw on 2014-05-14
> **pqwoerituytrueiwoq said:**
> rule of thumb, if the PSU comes with the case it is a very cheap PSU that i would not recommend trusting as far as you can throw it

Agreed.  On the other hand, they supplied me with an FSP 180W PSU as a replacement so all is good.  Also my RAM arrived from Crucial this morning, and all is good, so the price has dropped to under £600 after the refunds come in from Dabs and Amazon.

---

### Post by mastablasta on 2014-05-15
yesterday i found that Chinese no brand mini PC maker that got excelent reviews. the baord they use uses a Celeron CPU with ultralow power (i think they are 1,1Ghz and 1,8 Ghz if i am not mistaking) capable of 16GB ram. but the issue is motherboard only has limited hard disk space (i mean plugs for sata drives). the whiole thing is just arround 100 EUR. Well plus VAT tax &customs for us in the EU. it think it get's here at about 130-140EUR (motherboard&mini ITX frame). the box is very good as media center and uses really low power (almost as low as atoms, but with more power). i would imagine it functions reaosnably well as mini PC ala MintBOX with less power. i didn't have time to find other boards with these CPU's that would have more plugs for SATA. i can not help but wonder why they do not make these? they seem like perfect choice for NAS or mini home server. why all of them have only one or two SATA plugs? i also see they have some 64 bit Atoms that support more ram (even their motherboards?!) from 2012, but i can't seem to find any motherboards that would have them.

i didnt' have time yet , but i plan to do a bit more digging on that chinese site. to see if maybe this company has something like that to offer.

further what is a "mistery" to me is why all entry level NAS have max two drives. i mean if you put family HD movies on NAS that would fill up fast wouldn't it? and i also did some check on tape backup out fo curiousity (oh its been so long since i've put any data to tape :-) ) and was shocked at the prices!!!! 1500USD for entry level drive, while the tape cartridges have prices comparable to disk drives. if i can accept the cartridge price i find the drive price for home usage absurd. with all data moving into digital i can only but hope that as new methods of backup are discovered and as more people needs to make backup the prices will drop.

---

