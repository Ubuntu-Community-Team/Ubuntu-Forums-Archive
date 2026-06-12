---
title: "Erasing 56 SCSI Hard Drives with Gutsy?"
date: 2008-02-18
forum: Server Platforms
---

### Post by JohnnyXmas on 2008-02-18
Hello!

I just built something interesting, and need some tips on getting it to do what I need it to:

I have 4 Compaq StorageWorks SCSI Arrays connected to a Compaq Proliant DL580 G2 server using SymBIOS  Logic 22910 Ultra2 LVD  HBA's.  Each array can hold and address up to 14 drives. The server is running a Win2K AS \ Ubuntu Gutsy Dual-Boot.

the purpose of this setup is to provide fast mass drive testing and erasure. I need to be able to load it up with drives, test them for SMART failures and bad sectors, then perform a one-pass erasure.

Can you guys provide me with a walkthrough on how to perform these tasks with this equipment?

I have been using Ubuntu for a few years now as a Desktop \ Laptop OS, so I am very familiar with it, along with the locations and functions of the major configuration files and such. I have just never had to deal with this particular situation (of course), so a lengthy step-by-step is not necessary, just a geenral rundown of the quickest way to perform these tasks. 

Thanks!!

---

### Post by HermanAB on 2008-02-18
Hmm, unfortunately Google proved statistically that SMART doesn't actually work.

However, that being said, here is an erase utility for you:
[http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml](http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml)

Cheers,

Herman

---

### Post by JohnnyXmas on 2008-02-18
Tanks, but it doesn't really address my needs.

I'm WELL aware of the SMART issue, but we're contractually obligated to do it by our client, and far be it from me to turn away easy money. 

As far as the utility, it's not really necessary. I can seriously get away with a standard 1-pass "format" of the drive. No secure erasure is needed. 

What I do need, is instructions on how to rescan the SCSI busses each time I swap drives out, so I don't have to constantly reboot the machine.  Furthermore, I need a quick way to tell it to wipe all the drives on said busses (except for the primary one, which holds the OS), without having to fdisk and mount every single one, every single time.  Right now I'm doing it under Solaris 10 on a Sun V480, whose "format" command at least provides a menu system, but it's still REALLY tedious.

This is going to be a permanent situation, with hundreds of drives per month going through it, so you can imagine how insanely tedious it would be to do that manually.

Also, should this be in the "Server" section? It's not running a server OS, nor isthe machine serving anything, but I dunno.

---

