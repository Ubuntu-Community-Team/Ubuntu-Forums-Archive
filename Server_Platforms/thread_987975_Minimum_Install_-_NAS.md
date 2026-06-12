---
title: "Minimum Install - NAS"
date: 2008-11-20
forum: Server Platforms
---

### Post by schander on 2008-11-20
Hi, I'm looking at setting up a NAS box The PC that it's going to go on is a Compaq d530, p4 2.8GHz, 1gb nic, 1280 Ram and 2 x 750GB drives, hopefully in raid 1. 
Have been looking at using freenas as the OS and booting from a compact flash on ide. Then i saw that Ubuntu has a server version that has a minimum install, but it take up 500+mb with on the Samba File server installed, compared to the 32mb for freenas. 
Is there a really small version of ubuntu server?, like the boot only version of freebsd (33mb), which freenas is based on.

The setup would be 2 hd mirrored with the OS on a usb drive/compact flash on ide. Also if I was to install Ubuntu to a usb thumb drive how could i avoid killing it by moving the areas that constantly written to off the usb drive. Also what would be the betst way to handle swap space, i'd rather not have it on the mirrored hd's.

Can anyone help?

Thanks
Satpal

---

### Post by threetimes on 2008-11-20
I'd get a 3rd drive, for the system only, put the swap space and the 500mb system there, and you have no problems with a dead usb drive or mirrored swap.
 
But if you don't have a 3rd drive, you can at least solve the usb drive problem by using it as a live cd. Then nothing will be written to it.

---

### Post by Krupski on 2008-11-20
> **schander said:**
> Hi, I'm looking at setting up a NAS box The PC that it's going to go on is a Compaq d530, p4 2.8GHz, 1gb nic, 1280 Ram and 2 x 750GB drives, hopefully in raid 1. 
Have been looking at using freenas as the OS and booting from a compact flash on ide. Then i saw that Ubuntu has a server version that has a minimum install, but it take up 500+mb with on the Samba File server installed, compared to the 32mb for freenas. 
Is there a really small version of ubuntu server?, like the boot only version of freebsd (33mb), which freenas is based on.

I have a couple home NAS file servers. They both run Ubuntu Server 64 bit off of 4 GB compact flash cards installed into CF-to-IDE adapters plugged right into the motherboard.

2 GB is for Linux, the other 2 GB is for swap.

Works like a charm.

Why not just use Ubuntu server and a 4 GB CF card? They are so inexpensive now there's no point in going smaller.

BTW, if you are referring to the "Server Minimal Install" procedure that's posted in the "How-To Forge", you will find that, although it works, it's missing a LOT of necessary apps and you will just end up doing an install from a Server disk anyway.

-- Roger

---

### Post by schander on 2008-11-21
> **Krupski said:**
> I have a couple home NAS file servers. They both run Ubuntu Server 64 bit off of 4 GB compact flash cards installed into CF-to-IDE adapters plugged right into the motherboard.

2 GB is for Linux, the other 2 GB is for swap.

Works like a charm.

Why not just use Ubuntu server and a 4 GB CF card? They are so inexpensive now there's no point in going smaller.

BTW, if you are referring to the "Server Minimal Install" procedure that's posted in the "How-To Forge", you will find that, although it works, it's missing a LOT of necessary apps and you will just end up doing an install from a Server disk anyway.

-- Roger
Thanks for your reply Roger. 
I have a some questions:
[LIST]
[*]Do you have a full install? I don't mind installing stuff that i actually want running as it will keep the box responsive, it's only p4.
[*]What do you use fo admin of the NAS box (ebox, webmin)?
[*]What speed is your compact flash card? 
[*]How long have you been running it from the cf card?
[*]Have a backup of your OS?
[/LIST]
Have you thought about mounting /tmp on a ram disk to avoiding the constant I/O to the cf card, as mentioned here:
[http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/822001690931]("http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/822001690931")
Interestingly the talk about running the server without swap. This is what i'm running at the moment:
```
schander@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              16G  742M   14G   6% /
tmpfs                 628M     0  628M   0% /lib/init/rw
varrun                628M  284K  628M   1% /var/run
varlock               628M     0  628M   0% /var/lock
udev                  628M  2.7M  625M   1% /dev
tmpfs                 628M     0  628M   0% /dev/shm
/home/schander/.Private
                       16G  742M   14G   6% /home/schander/Private
schander@ubuntu:~$ free
             total       used       free     shared    buffers     cached
Mem:       1285020     163384    1121636          0      13832     106520
-/+ buffers/cache:      43032    1241988
Swap:       746980          0     746980
```
Using only a 160mb of memory out of 1280mb that i have, so even if put the swap on the cf card i doubt it will used.
Just using an old 17gb disk for testing until I get my cf card.

Thanks
Satpal

---

### Post by threetimes on 2008-11-21
> **schander said:**
> Do you have a full install? I don't mind installing stuff that i actually want running as it will keep the box responsive, it's only p4.
> **schander said:**
> p4 2.8GHz, 1280 Ram
That's more than way enough, I run a full server on a p3 600MHz with 256 mb ram. (Almost) no swap used.> **schander said:**
> What do you use fo admin of the NAS box (ebox, webmin)?Just use SSH, if you want it web-based, I'd reccomend [Ajaxterm]("http://antony.lesuisse.org/software/ajaxterm/").
> **schander said:**
> Have a backup of your OS?
If you want to be safe, back your system up to a second CF, and if one fails, restart the server from your other card.



> **schander said:**
> 
Interestingly the talk about running the server without swap. This is what i'm running at the moment:
[..code..]
Using only a 160mb of memory out of 1280mb that i have, so even if put the swap on the cf card i doubt it will used.

Cool, huh? My output:
```
peter@peter-server:~$ df -h                                                     
Filesystem            Size  Used Avail Use% Mounted on                          
/dev/sda1              74G  1,3G   69G   2% /                                   
varrun                125M   96K  125M   1% /var/run                            
varlock               125M     0  125M   0% /var/lock                           
udev                  125M   32K  125M   1% /dev                                
devshm                125M     0  125M   0% /dev/shm                            
peter@peter-server:~$ free -m                                                   
             total       used       free     shared    buffers     cached       
Mem:           249        194         54          0         23         74       
-/+ buffers/cache:         96        153                                        
Swap:          729          6        722
```
> **schander said:**
> 
Just using an old 17gb disk for testing until I get my cf card.
You could keep it like this, if you don't need a backup. I use a 80gb drive from my desktop as only storage.

---

### Post by schander on 2008-11-21
> **threetimes said:**
> 
If you want to be safe, back your system up to a second CF, and if one fails, restart the server from your other card.
Thats an idea :)

> **threetimes said:**
> 
Just use SSH, if you want it web-based, I'd reccomend Ajaxterm.
I will check it out.

> **threetimes said:**
> 
You could keep it like this, if you don't need a backup. I use a 80gb drive from my desktop as only storage.
I would be the only problem is that it would mean maxing out the the case, which is a custom compaq sff, also the unit only has a 150w power supply. There could also be a problem air flow as I notice that my 750gb samsung was running warmer than I would expected

Thanks
Satpal

---

### Post by Krupski on 2008-11-22
> **schander said:**
> Thanks for your reply Roger. 
I have a some questions:
[LIST]
[*]Do you have a full install? I don't mind installing stuff that i actually want running as it will keep the box responsive, it's only p4.
[*]What do you use fo admin of the NAS box (ebox, webmin)?
[*]What speed is your compact flash card? 
[*]How long have you been running it from the cf card?
[*]Have a backup of your OS?
[/LIST]
Have you thought about mounting /tmp on a ram disk to avoiding the constant I/O to the cf card, as mentioned here:


(1) Yes I did a full Ubuntu 8.10 Server 64 bit install to a 2GB partition on the CF card. Currently (with all updates installed, plus a few utilities and "build-essential" [c compiler]), 927 MB of the 2GB is used. I have a little over 1 GB free. The other 2GB partition is for swap (which is hardly ever used).

(1a) Having things installed does not mean they use CPU power. They are just AVAILABLE. My box is not in any way loaded down by extra apps being installed. Here's output from TOP (did it just now):

```

top - 12:50:54 up 3 days, 16:02,  1 user,  load average: 0.00, 0.00, 0.00
Tasks:  82 total,   1 running,  81 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.0%us,  0.0%sy,  0.0%ni, 99.8%id,  0.2%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   8105332k total,  1247028k used,  6858304k free,    56680k buffers
Swap:  1951856k total,        0k used,  1951856k free,  1069976k cached

```

The machine is barely awake!  :)

(2) I use SSH server in the box and Bitvise Tunnelier SSH/SFTP client in remote Windows machines. I've got port 22 forwarded through my router for SSH.

(3) The CF card is 266X (40 MB/s) (A Sandisk card).

(edit to add): Here's what I use to plug the CF card into the motherboard IDE connector: [LINK]("http://www.addonics.com/products/flash_memory_reader/adebidecf.asp")

[IMG]http://www.shopaddonics.com/mmSHOPADDONICS/Images/adebide2cf.jpg[/IMG]



(4) Been running for about 9 months straight so far.

(5) Yes... I use DD to make a complete 4GB image of my CF card that is stored on my RAID drive which I then later copy to a Windows machine. I use the backup in case I make a change on the server and mess it up. It's easy to pull out the card, image the "last known good" back to the CF card, pop it back in and reboot. 

It takes all of 5 minutes to recover from a boo-boo.

I also do an immediate backup just before I do something that I'm not sure of... just in case!


(6) Yes, I have thought of flash wearout problems... but considering the write cycle life of current flash memory and the amount the card actually gets written to (as well as the card's own wear leveling algorithms), it will be decades before the card wears out. By then, we will all be using radically different machines and my file server will be in a landfill somewhere!  :lolflag:

Note also that if you really care about flash wearout, you can use the dual CF adapter shown above and put in TWO cards... one CF card and one Hitachi "Microdrive" (a 1 inch CF2 hard drive!). Then put your swap, tmp, var, etc... on the hard drive.


Any other questions... feel free to ask!

-- Roger

---

### Post by windependence on 2008-11-22
Of course YMMV but IMHO FreeNAS is smaller, more reliable, and more simple. I'm also not sure if Ubuntu has software to handle block level devices such as iSCSI. I have several FreeNAS boxes some set up as NFS boxes and some as iSCSI. The cool thing is even though I have 512 memory, I could run them on as little as 256 for iSCSI and less than that for anything else. 

I'm not in any way saying Ubuntu isn't a great setup for a NAS box, just that in my experience BSD is much more solid. Of course, my NAS boxes are targets for many VMware machines and are live production servers. For home use it might be overkill.

Roger, Can you post exactly what model card that is? I wanty to see what they cost me through ditribution. Looks like a great idea!

-Tim

---

### Post by windependence on 2008-11-22
Sorry Roger, missed the link to the card in your post, THANKS!

-Tim

---

### Post by Krupski on 2008-11-22
> **windependence said:**
> Roger, Can you post exactly what model card that is? I wanty to see what they cost me through ditribution. Looks like a great idea!

-Tim

Which card? The compact flash card, or the CF-to-IDE adapter?

---

### Post by windependence on 2008-11-22
> **Krupski said:**
> Which card? The compact flash card, or the CF-to-IDE adapter?

I was looking for the CF to IDE card but I missed your link. I have my boxes running off a small partition on the MB but they run in embedded mode meaning they are immediately loaded to RAM and use a RAMdisk to run the NAS. It's just as fast as the CF card except for boot.

-Tim

---

### Post by Krupski on 2008-11-22
> **windependence said:**
> Sorry Roger, missed the link to the card in your post, THANKS!

-Tim

Oops... Yes the CF to IDE adapter card is made by Addonics. They have two different models... a single and a dual. The dual one populated with 2 cards acts as a master and slave IDE drive.

There are several other brands of adapter cards, but I've found the Addonics cards to be the best quality. I also like their other adapter cards. They are VERY useful especially for adding new SATA hard drives to an old IDE only machine, or for allowing a customer to use their old IDE hard drives with a newer SATA motherboard.

One thing that you may be interested in is that the Addonics card needs 5 volts which is normally supplied by (the included) adapter cable which connects to a 4 pin hard drive power connector and Y's off to a 4 pin connector and a 2 pin connector for the CF adapter.

What I did (for neatness) was to take the power cable for the CF adapter and attach the wires to a 10 pin socket header (click [**[COLOR="Red"]LINK[/COLOR]**]("http://home.roadrunner.com/~krupski/images/adapter.jpg") for a picture).

This allows me to plug into an unused USB header on the motherboard and get my 5 volts without using a big, clunky adapter cable.

A mass produced molded version of that cable might be a nice idea if you're going to be doing this stuff in quantity... ?

-- Roger

---

### Post by Krupski on 2008-11-22
> **windependence said:**
> I was looking for the CF to IDE card but I missed your link. I have my boxes running off a small partition on the MB but they run in embedded mode meaning they are immediately loaded to RAM and use a RAMdisk to run the NAS. It's just as fast as the CF card except for boot.

-Tim

Do you think I could, at boot time, copy my whole Linux partition into a ram drive and then CHROOT to it?

Would a simple CHROOT move ALL accesses (like /tmp and /proc, etc...) to the ram drive?

I'm not sure WHY I would want to do this (since I'm not concerned about flash write cycle life), but it would be a fun learning experience.

Thanks!

-- Roger

---

