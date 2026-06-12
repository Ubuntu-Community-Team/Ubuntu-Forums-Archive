---
title: "media server with RAID"
date: 2009-11-29
forum: Server Platforms
---

### Post by Neezer on 2009-11-29
So I have an old P4 computer with this board. An asrock p4vm800
[http://www.asrock.com/mb/overview.asp?Model=P4VM800](http://www.asrock.com/mb/overview.asp?Model=P4VM800)

It has 2 SATA I ports on it, and I think I should be able to set up a RAID 1 array with it. If I set up a raid 1 array on the motherboard with 9.04 server can I transfer the drive to a RAID controller card at a later date and still have the array working? 

I have been told that If I get a raid controller card it will work at SATA II speeds even though the onboard SATA is only SATA I.

Any input or suggestions?

---

### Post by cascade9 on 2009-11-29
That motherboard only has PCI slots, limited to 133MB/sec. I dont think you will ever get 'full SATA II' speeds from a PCI slot RAID card, 133MB/sec long way short of SATA II 3Gbit/sec. The drives will be working in SATA II mode, but your transfer rates will be limited be PCI. 

I'm not sure if you can transfer RAID arrays between controllers.

---

### Post by Neezer on 2009-11-30
Thanks for the quick reply. I was worried about that, and I was trying to find out the transfer rate for PCI. Isn't SATA I 1500 MB/sec?? So would It just be better to use my onboard SATA slots?

found an awsesome deal on some barracudas on Newegg....89.00 for a 1.5 TB drive.....getting two and using RAID 1 is the plan.

---

### Post by cascade9 on 2009-11-30
SATA I = 1500M/bit. 8 bits = 1 byte, but theres a few other things happening as well (no need to go into that here, unless you really want to). SATA I, in the end, is pretty much 150MB/sec. 

As for if you should use the VIA 8237R SATA controller...er.....maybe? Maybe not. 

> **Problem:**
Second Generation Serial ATA (SATA II) hard drives are not detected when connected to a VIA or SIS Serial ATA controller. These First Generation Serial ATA (SATA I) controllers include the following chipsets:
 
[LIST]
[*]VT8237
[*]VT8237R
[*]VT6420
[*]VT6421L
[*]SIS760
[*]SIS964
[/LIST]
 **Cause:**
Our SATA II hard drives use autospeed negotiation. This enables our SATA II drives to automatically detect the motherboard data transfer rate, making it backward compatible with SATA I data transfer rates. However, some older SATA I controllers are unable to support autospeed negotiation and cannot recognize the drive. This “drive not detected” condition occurs when a chipset is incapable of correctly negotiating the data transfer speed with a SATA II hard drive.

[http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=1337](http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=1337)

As far as I know this issue is for all SATA II hard drives on these controllers, not just western digital. 

Sorry to keep saying things I know you dont want to hear. :|

---

### Post by Neezer on 2009-11-30
So....

what are my options?? do they still sell boards that will run SATA II raid with a p4? They can't cost a lot...Also, I have a 2GB kit of DDR that is actually quite good, and I don't want to have no use for it..

I suppose I could just use two drives...one for storage/ubuntu server, and then just use the other for regular backups?

I feel like a bit of a jack@$$....I went ahead and pulled the trigger on the two drives before you mentioned the chipset problems....My own fault I guess.

So I have these two awesome drives coming anyways....might as well. make the best of it...

**EDIT:** I just read that link that you posted, and it looks like I would be able to do it with a PCI RAID card....Can I still stream music and DVD's to my PS3 at 133MB/s? doesn't sound like a huge difference in performance between 133MB/s and 150MB/s. Also looks like I could try the jumper solution to make my drive only run at SATA I speeds....

Does the fact that they are seagate drives not Western Digital have anything to do with it? or is it the chipset that has problems with all SATA II drives?

Thanks for all the help Cascade..I know you don't have to do this. I really appreciate you helping me get on the right track.

---

### Post by cascade9 on 2009-11-30
Not 100% sure if its SATA II, but I can get socket 478/945 chipset/Intel ICH7 SATA controller boards here. I had a quick look at newegg, the 2 478 boards I saw had the same VIA SATA chipset so thats no use. 

I'd you could get a PCI-SATA card. You wont get 133MB/sec sequential read from many (if any) desktop drives, and RAID1 is going to be slighty slower. Its more than enough for streaming audio/data to a PS3. 

There _should_ be jumpers on the back of the seagate 1.5TB drive..but to tell the truth my brain is melting and I cant think straight LOL (summer is just hitting, its 33c/90f and 85% puls here now. Gah.) So I cant remember where to go to check now :S 

Pic of where the jumper is anyway-
[http://www.seagate.com/images/support/en/us/cuda_sata_block.gif](http://www.seagate.com/images/support/en/us/cuda_sata_block.gif)

If you dont mind waiting, get the drives and check to see if it works. If your 'must have asap' get a PCI SATA card. 

Not a problem, I've always been a hardware guy ;) I've never been that great at software, but hardware is something I've picked up a bit of experience with.

---

### Post by Neezer on 2009-11-30
Thanks a lot! The drives should be here in a day or two. Then I'll see if it will work with the jumper in them....Well first I'll see if they just work out of the box, but that is probably not going to be the case.

I saw the same two boards on the newegg site that you were talking about....these socket 478 boards are apparently in skhort supply these days.....I wonder why...

Either way, I'll figure out a way to get them working....I'd hate to spend the money on a new board/chip/ram just to use some hard drives, but that is the breaks sometimes!!! and it would be a good excuse to get some better parts...it kind of defeats the point of using a FOSS server system like ubuntu though.

first things first is the get the drives a see if I can make them work.

Thanks again for all the help with this. I really appreciate it.

---

### Post by cascade9 on 2009-12-01
On the 478 boards beign hard to find now, that always happens. Once CPUS in whatever socket stop being produced, its only a matter of time untill the motherboards become hard, then impossible to get. Honestly I'm suprised that 478s are still around, it been ages since Intel went to LGA 775. 

You'll get the drives working. Hopefully of the on-board controller, but if I recall right the jumpers on the back of the SATA drives use the tiny (and rare) jumpers, and the drives dotn come with them. I think you c an cut down/shave a normal jumper to fit. 

Good luck ;)

---

### Post by Neezer on 2009-12-15
So I got my drives and got the jumpers in and i'm running into some problems still....I am not detecting the drives when I go into the bios...also, I think I need to generate a floppy disk for the raid setup. the only problem with this is that I don't have a floppy drive. Is it possible to do it with a USB drive instead of a floppy drive?

---

### Post by CharlesA on 2009-12-15
> **Neezer said:**
> So I got my drives and got the jumpers in and i'm running into some problems still....I am not detecting the drives when I go into the bios...also, I think I need to generate a floppy disk for the raid setup. the only problem with this is that I don't have a floppy drive. Is it possible to do it with a USB drive instead of a floppy drive?

Since the drives are on an external controller, they won't show up in the BIOS.

Why would you need to create a floppy disk? To install the drivers? Do you have a link to the linux drivers that the RAID card needs to use?

With the RAID card I use, it prompts you to hit a key combo to setup the array.

---

### Post by Neezer on 2009-12-15
> **CharlesA said:**
> Since the drives are on an external controller, they won't show up in the BIOS.

Why would you need to create a floppy disk? To install the drivers? Do you have a link to the linux drivers that the RAID card needs to use?

With the RAID card I use, it prompts you to hit a key combo to setup the array.

It is onboard RAID...the raid install process in the motherboard manual says it needs to create a floopy disk to put the SATA drivers onto the disk. It is cause the drivers are on the motherboard CD. It needs to copy them to the floppy then I can put the OS disk in and set up the raid array and load my OS.

the link to the manual for the motherboard is here:
[http://www.asrock.com/MB/manual.asp?Model=P4VM800](http://www.asrock.com/MB/manual.asp?Model=P4VM800)

it is an asrock p4vm800 board.

---

