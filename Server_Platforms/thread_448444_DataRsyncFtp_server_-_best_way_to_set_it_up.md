---
title: "Data/Rsync/Ftp server - best way to set it up?"
date: 2007-05-19
forum: Server Platforms
---

### Post by feenster on 2007-05-19
Hi all,
I'm going to build a data/FTP/Rsync server with Ubuntu 7.04 Server, using an Adaptec SATA RAID card (that supports RAID5, 6 etc), and a bunch of 500GB drives, how would you set it up?

I'm contemplating the best way to do it. To start with, i'll have 5x500GB drives and an Adaptec 3805 card. I was thinking of making one big RAID-6 array (leaving 2 disks for parity), giving me 1.5TB of space. I was wondering then whether to put the OS and data onto this array (instead of having a seperate disk(s) for the OS), and then formatting it with ReiserFS - i've seen it mentioned that this is a happy compromise between speed and safety with Linux.

Are there any obvious flaws in this plan? I was also contemplating putting the array into an LVM group, so in the future i could add another RAID card and 8 more drives and easily expand the space available.

Cheers,
    Matt

---

### Post by craigp84 on 2007-05-19
> Are there any obvious flaws in this plan?

Only 1, easy to fix one, everything else sounds absolutely fine. You'll find the full thing is a doddle to setup. You might want to consider a more specialised distro like [www.openfiler.com](www.openfiler.com) instead of Ubuntu for this though. Openfiler is just redhat underneath, so you can easily tack on things like a streaming media server etc if you so wish.

The problem: "Adaptec SATA RAID". Do not use the onboard (wannabe) RAID chip. Use software raid instead. The reasons for this are many-fold, but highest among those are: what happens when the card fails - you need to source an exact match (possibly even down to firmware version) to be able to recover your drives; performance - software raid will run faster for Raid 5 than any of the Adaptec Sata Raid units - to verify this, build it up under(fake)  hardware raid, then run bonnie++ the benchmarker. Then rebuild the system to use software raid, and do the same benchmarks. You may be surprised to see how much faster software raid is than these fake raid chipsets.

Don't forget to have a proper backup solution in place, raid wont save you from user error :-)

Hope this helps,

-c

---

### Post by feenster on 2007-05-20
Hi,
Thanks for the reply. Openfiler does look good, but i'm used to using Ubuntu now, so i'm happy to stick with that. I've actually been running a prototype of this system with lesser hardware for a few months now.

As for the Adaptec thing - the 3805 RAID card isn't fake RAID I think ([Adaptec 3805]("http://www.adaptec.com/en-US/products/sata_cards/value/SAS-3805/")). If so, would it really still be faster using **mdadm **to build the array rather than the hardware RAID?

Matt

---

### Post by craigp84 on 2007-05-20
> If so, would it really still be faster using mdadm to build the array rather than the hardware RAID?

There's one sure-fire way to find out! Bonnie++ is pretty easy to get going, and the couple of hours up front it takes to see which configuration is best for you could make a whole lotta difference later on in this little server's life :-)

If you do go ahead, please post your findings here!

Cheers,

-c

---

