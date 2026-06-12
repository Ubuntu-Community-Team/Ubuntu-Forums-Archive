---
title: "Preparing for Ubuntu Studio"
date: 2007-03-20
forum: The Cafe
---

### Post by adarkmethod on 2007-03-20
by putting together a cheap, but effective new PC for recording, so far here's what i think im gonna go with.

 BIOSTAR NF325-A7 Socket 754 NVIDIA nForce3 250 ATX AMD Motherboard

 AMD Athlon 64 3200+ Venice 2.2GHz Socket 754 Processor Model ADA3200AI04BX

 Apollo R7000PCI-B3 Radeon 7000 64MB DDR PCI Video Card

 G.SKILL Value 1GB 184-Pin DDR SDRAM DDR 400 (PC 3200) System Memory Model F1-3200PHU1-1GBNT

 Western Digital Caviar SE WD2500JS 250GB 7200 RPM SATA 3.0Gb/s Hard Drive

 ASUS 16X DVD±R DVD Burner with 12X DVD-RAM Write and LightScribe Black E-IDE/ATAPI Model DRW-1612BL-BK


I have two questions for this community. Does anyone see anything on my list that would have trouble working under ubuntu? and Secondly, got any sugestions for a relatively budget Audio Card that will still be effective for recording guitar?

---

### Post by teet on 2007-03-20
Apollo R7000PCI-B3 Radeon 7000 64MB DDR PCI Video Card

ATI + Linux = Bad
Nvidia + Linux = Good

Buy a Nvidia card and save yourself some trouble

-teet

Edit:  For the same price range you could get a Nvidia FX 5200, although this is already an old card.  For an extra $15 or so you could probably upgrade to an FX 6200 or higher.

---

### Post by Sammi on 2007-03-20
To all Linux users: STAY AWAY FROM ATI.

Their Linux drivers are really bad. Intel and Nvidia, however, have made excellent drivers for Linux.

---

### Post by maniacmusician on 2007-03-20
> **adarkmethod said:**
> by putting together a cheap, but effective new PC for recording, so far here's what i think im gonna go with.

 BIOSTAR NF325-A7 Socket 754 NVIDIA nForce3 250 ATX AMD Motherboard

 AMD Athlon 64 3200+ Venice 2.2GHz Socket 754 Processor Model ADA3200AI04BX

 Apollo R7000PCI-B3 Radeon 7000 64MB DDR PCI Video Card

 G.SKILL Value 1GB 184-Pin DDR SDRAM DDR 400 (PC 3200) System Memory Model F1-3200PHU1-1GBNT

 Western Digital Caviar SE WD2500JS 250GB 7200 RPM SATA 3.0Gb/s Hard Drive

 ASUS 16X DVD±R DVD Burner with 12X DVD-RAM Write and LightScribe Black E-IDE/ATAPI Model DRW-1612BL-BK


I have two questions for this community. Does anyone see anything on my list that would have trouble working under ubuntu? and Secondly, got any sugestions for a relatively budget Audio Card that will still be effective for recording guitar?
As others have mentioned. steer away from ATI and buy an Nvidia card. 

Also, if you're going to be recording, shouldn't you be buying a sound card as well? For a budget recording solution that sounds decent, I recommend the [M-Audio Delta 1010LT]("http://www.m-audio.com/products/en_us/Delta1010LT-main.html"). MSRP is $250, but it usually goes for around $200, sometimes a little cheaper if you find a good deal.

Enjoy.

---

### Post by %hMa@?b&lt;C on 2007-03-20
get yourself a socket 939 and opteron 165.  You will be glad.

---

### Post by tehhaxorr on 2007-03-20
I would highly reccomend getting a pair of Genius sound cards. Fully supported in ALSA and work fine. they are bloody cheap too. I have 3 in my recording box. Supports ASISO and works with all of the linux recording apps.

[http://www.clickonit.com/item/84471](http://www.clickonit.com/item/84471)

---

### Post by adarkmethod on 2007-03-20
alright, im looking into the nVidia video cards

and of course i want a better sound card, thats why i asked for suggestions, im not sure what i want and i was hoping for suggestions that others have had good luck with on Linux

---

### Post by maniacmusician on 2007-03-20
sorry, I guess I didn't see that part of your post. 

I would go over tehhaxorr's recommendation over mine; I haven't done very much recording in linux yet. the card I pointed out is very full featured, but I'm not sure as to it's support under Linux. I've heard it has good support but I have no experience with it personally.

---

### Post by adarkmethod on 2007-03-21
i'd love to get a Delta 1010 if I can find one cheap, but im looking into what others have suggested

---

### Post by adarkmethod on 2007-03-21
Alright, I'd love if people could tell me what kinds of experience they've had with any of the following Sound Cards/Interfaces using Ubuntu.. or even Windows if thats what you sued them with

E-MU 0404

M-Audio Delta 1010

E-MU 1212

please let me know what software you used them with, what kind of recording you did, how well they worked? any freezing issues, clipping too much?, weird digital skips?

---

### Post by tubasoldier on 2007-03-21
With the advent of the Creative X-FI cards the Creative Soundblaster Audigy has dropped drastically in price. It sounds great and can load soundfonts for wavetable synthesis of midi. I would definitely look into it.

---

### Post by adarkmethod on 2007-03-21
think im gonna go with the  Albatron FX5200LP V2.0 GeForce FX5200 128MB DDR AGP 4X/8X Low Profile Video Card

NVIDIA chipset, alright cache. Not like i plan on doing any video editing or anything, and its relatively cheap

---

### Post by maniacmusician on 2007-03-21
AGP cards really aren't as good as PCI-Express ones...AGP is pretty much dying out.

---

### Post by adarkmethod on 2007-03-21
well, for only about $10 more theres the ASUS EN6200TC 512/TD/256M GeForce 6200TC 256M (Effective memory 512M) GDDR2 PCI Express x16 Video Card

that looks pretty promising

---

### Post by maniacmusician on 2007-03-21
TC stands for TurboCache; which is **not** good. Turbo cache will give you a severe hit in performance. 

Go with a regluar Geforce or a Geforce *GT.

---

### Post by adarkmethod on 2007-03-21
what makes AGP bad, and if i have plenty of system memory, why do i mind TurboCache using some of it

---

### Post by mips on 2007-03-22
Because using system memory is sloooooowwwwwwwwwwwwww

---

### Post by diskotek on 2007-03-22
i'll have new ram for first, around 512 MB or 1 GB for my loosy laptop

m-audio firewire audiophile
behringer/boehringer rotary bcr 2000

would be nice and easy for me :D

---

### Post by damo21 on 2007-07-17
did anyone get the 'm-audio firewire audiophile' working in freebob?

---

### Post by theorganloft on 2007-07-18
> **adarkmethod said:**
> Alright, I'd love if people could tell me what kinds of experience they've had with any of the following Sound Cards/Interfaces using Ubuntu.. or even Windows if thats what you sued them with

E-MU 0404

M-Audio Delta 1010

E-MU 1212

please let me know what software you used them with, what kind of recording you did, how well they worked? any freezing issues, clipping too much?, weird digital skips?

I did not like the E-MU or M-audio cards on Linux. I ran into driver problems in my experience.   Go with the cards the others suggested.  I also like the ECHO MIA MIDI PCI card too.  I had good success with it.  
 I have a current system where I use a Sound Blaster Live for Live recording in a Church and use the mobo (Via) sound card for playback.  I get excellent results.  I use Audacity with K3B (CD burner) on Ubuntu Studio (Feisty) with excellent results:guitar:

---

### Post by bogr@ on 2007-07-21
I cannot get my eMu 0404 to work under Ubuntu 7.04.  So it's either buy a new card, or it's a Linux killer for me. I'm still working on it though...

---

