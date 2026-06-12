---
title: "Whats the best server motherboard out there?"
date: 2010-02-11
forum: Server Platforms
---

### Post by hockey97 on 2010-02-11
Hi, I am looking to build a server myself. I want to know what are well known and good server motherboards.

What would you recommend. I am right now designing and setting up a server system.

I would like any tips on doing this. I need to know how I can if I can put hard drives in a cabinet. I plan to buy a cabinet and modify it to hold or house all the hard drives that are extended off the server for storage space.

I would like any websites that would have tutorials or teach concepts as to how to keep a good working storage system that includes backing up hard drives too.

Thanks for your time.

I want this to also be ubuntu friendly motherboards/hardware.

---

### Post by jelcoward on 2011-01-05
Hi
Just wondering if you got anywhere with building your own server- I might be about to face doing the same thing (to run Ubuntu of course).

Cheers
Jel

---

### Post by stlsaint on 2011-01-05
I suggest you search for a server you would like to base yours off of then check out the specs of the system.

---

### Post by Skadork on 2011-01-05
for homebrew servers i like to stick with intel boards for stability and compatibility reasons. check out the dell outlet for slightly used or returned before use servers.  You can sometimes find a steal on there.

---

### Post by mdlueck on 2011-01-06
I have been building computers now for 23 years. The best brand by far has been genuine Intel boards. So, my Rx would be an Intel boxed motherboard, and Intel boxed CPU.

---

### Post by VMGuy on 2011-01-06
For (almost) the last 15 years I've used Asus server boards, but two years ago I've switch to Intel for the follwing reasons:
- The remote management stuff is much better
- Also for older boards you get BIOS/EFI updates

So I would also recommend Intel now.

Regards, VMGuy

---

### Post by Schuby007 on 2011-01-24
Hi,

I'm building my first server to use as a Counter Strike: Source game server that I'm hoping will host 24-48 players. I plan on using Ubuntu Server 10.04 64bit. I also plan on using it as my own personal file server.

I'm looking at building it with the Intel Xeon E3110 3.0GHz, 1333MHz, Wolfdale, dual-core processor (LGA 775) as it's cheap and from what I've read, should fit my needs.

Initially I want to build the server with a single SSD drive just to get the system up and running and then later I wanna add another SSD to mirror the original with RAID 1. Then I want to add 4 large capacity SATA drives in a RAID 10 for storage (after I've gotten everything else set up).

Can anyone recommend a motherboard that will fit this setup? I'd really like a motherboard that has built in VGA graphics so I don't have to buy a graphics card just for the install (as I plan on using SSH after I get it up and running). I don't plan on using ECC memory as I need the memory to be fast (for the game server). Because this is my first build, I'm very new to installing/setting up RAID. Do any motherboards exist that have a built-in hardware RAID that will work with Ubuntu and let me do raid 1 and raid 10? Or will I have to get a SATA RAID card? Will hardware based RAID allow me to build a raid 1 array with a SSD drive that's already in use (my system drive) without having to reformat/re-partition?

I've been researching for weeks now, any experience/support would be greatly appreciated.
Thank you.

---

### Post by mdlueck on 2011-01-24
As for RAID with Linux, I recommend a SATA RAID controller from 3Ware, and to get the 3Ware GUI utilities visit: [http://jonas.genannt.name/](http://jonas.genannt.name/) (Yes I know it says "Debian", works just fine on Ubuntu!)

---

### Post by Schuby007 on 2011-01-26
> **mdlueck said:**
> As for RAID with Linux, I recommend a SATA RAID controller from 3Ware, and to get the 3Ware GUI utilities visit: [http://jonas.genannt.name/](http://jonas.genannt.name/) (Yes I know it says "Debian", works just fine on Ubuntu!)

Hey,

Thanks for your reply. After a lot of reading and input from various other forums I've decided to do software RAID in Ubuntu and to forget about SSD drives as their performance gains are dulled with the lack of TRIM support. As well, after reading a lot of reviews on the server motherboards I was looking at, it looks like it's just going to cause more headaches. For example some of the boards I was looking at require special server cases, some needs special adapters to use with with case buttons, lights, etc.

So I've decided to get an Intel Core 2 Duo E8600 which is basically the exact same specs as the Xeon E3110 but it has an increased multiplier to bring it 3.33GHz. And I'm gonna go with the Asus P5QL-VM DO motherboard with the Intel® B43/ ICH10D chipset. I like the design of this motherboard (4 x DDR2 800 slots for up to 16GB of memory), 3 PCI card slots so I can install my own two gigabit network cards, PS/2 keyboard and mouse ports, on-board VGA and DVI graphics, 6 x SATAII ports. I also like that it doesn't have Floppy drive or CD drive connectors as I won't require either of those devices to update the BIOS or install Ubuntu (Live USB). The board has gotten good reviews and it's cheap which allows me to purchase the faster E8600 and more RAM. As far as my initial hard drives: I'm gonna go with two Western Digital VelociRaptor 150GB 10000RPM drives setup in a software RAID 1 for my system drive. I'll add another 4 high capacity drives later to use in software RAID 10 for storage.

Any input or suggestions on this setup would be greatly appreciated.
Thanks.

---

