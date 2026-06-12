---
title: "RAID recommendations"
date: 2011-04-07
forum: Server Platforms
---

### Post by Sam_Williams on 2011-04-07
Hi,

I'm just setting up a reconditioned dell poweredge 2650 as a home office server, and am wondering what the best RAID (hardware) configuration would be. It's my first time setting up anything more complex than a desktop, and I am a little confused about the interaction between the hardware raid controller, grub and the LVM - can anyone point me towards a good howto on this subject?

Before the box was wiped, it was set up as a RAID 5 array of 5x 137GB drives giving around 548GB storage. Windows and user data apparently co-existed happily in this configuration.

However, having done a little research and reading some (admittedly older) posts, I am concerned that grub may not boot linux from a RAID 5 array. Will I need to exclude one of the drives when setting up the raid array so that I end up with a four disk RAID 5 (411GB) and a separate drive to hold the OS? It would seem a bit of a waste if less than half of the single disk was used for the OS and some swap space.

As far as I can work out the hw raid controller will only form an array from entire disks (not from identical size partitions on each drive), and only gives options for Raid 0, 1 & 5. I could ignore the hw controller and use linux software raid instead, which seems more flexible, but at the cost of greater overhead.

I do wedding photography for friends and family, and the box will be used mostly as a file server to hold photos. Each wedding generates about 16-20GB of photos, so I would like to end up with the configuration which gives me the greatest amount of resilient storage. I currently keep the photos on my desktop and backup to multiple USB drives, which is a pretty slow process! I've also had a number of USB drives fail, which causes me some concern. 

Any thoughts or opinions on the best set-up for my needs are welcome! 

Sam

---

### Post by CharlesA on 2011-04-07
I always have the OS on a separate drive from the RAID array. I've only done a setup like that, so I don't know how well/how badly it would work if you installed the OS to the array.

In my case, I've got 3 x 2TB drives in a RAID-5 array, with a 500GB drive for the OS. Everything works perfectly. :)

Also, I've run into some problems with USB drives, but for the most part the ones that have failed, failed within a couple days to a week of being bought. I use USB drives for backing up my array.

EDIT: That being said, I backup documents from the array to an external daily, and backup everything monthly to two other drives, so if one goes down, I have another copy of the data if I need to go back.

---

### Post by Sam_Williams on 2011-04-07
> **CharlesA said:**
> I always have the OS on a separate drive from the RAID array.

I must admit this seems to be the most common set-up and I suspect  there is a good reason for that.

I guess the crux of my query is whether the hw raid controller hides the complexity of the array and presents itself as a single device to grub? If it does, then grub itself would not have to work out how to read the stripes to load the OS... you would think that the hw controller would do this transparently.

Sam

---

### Post by CharlesA on 2011-04-07
It should show as a single device. That's how mine is seen.

---

### Post by Vegan on 2011-04-07
I recommend hardware RAID with a real controller.

Software RAID is no protection at all.

---

### Post by rubylaser on 2011-04-07
With hardware controllers, I typically put my OS on the RAID array to take advantage of the parity offered by the array. That 2650 probably has a PERC RAID (I would guess a 3/DI) card in it. Ubuntu will just see that as one hard drive, and boot from it with no problem.  I personally would just leave the existing RAID5 setup, and install Ubuntu.  Just make sure you still do backups, because RAID is not a backup :)

Vegan,  Sam_Williams already said he's using a hardware solution, and this...

> Software RAID is no protection at all.

is both wrong and misleading.

---

### Post by disabledaccount on 2011-04-08
> **Vegan said:**
> Software RAID is no protection at all.
> **rubylaser said:**
> Vegan,  Sam_Williams already said he's using a hardware solution, and this...
is both wrong and misleading.

I've just realised what's the point - Vegan is notoriously criticising Windows software raid (it's clear that he knows nothing about Linux raid.) Yes, windows have soft-raid too - built of logical volumes - but it's crap, it don't have even fraction of md functionality, flexibility  and reliability.
So above statement should sound like this:
> Windows software RAID is no protection at all.
 :) :) :)

---

### Post by rubylaser on 2011-04-08
You're probably right.  It seemed like a shot at software RAID (with no factual backup) when the OP wasn't even considering it as an option anyways.

---

