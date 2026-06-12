---
title: "auto scan, mount and fstab?"
date: 2008-08-15
forum: The Cafe
---

### Post by bone2006 on 2008-08-15
I spend 99% of mine time on Linux box, but at work I'm forced to use a windows machine.   Somethings on the windows machine is just soo much easier I have to admit.

Recently I had to create a new partition using the non-destructive partition software gparted. Well funny thing is that I needed a fat32 partition to be shared between the two systems.

After the partition was created I went into windows right clicked on the container and clicked format.  It's done.............. I can if I want change the drive letter to another letter.............but it's done.

I rebooted into linux and wondered why isn't it so easy for Linux?  Why can't the average user just come to Linux if it's really not that easy.

I couldn't remember which partition I wanted to mount, so I had to type in cfdisk, ok...........it's sda3

then I go to mount

mount -t fat32 /dev/sda3 /mnt/sharedfolder

hum..............not working.............. oh wait it's supposed to be vfat

ok
mount -t vfat /dev/sda3 /mnt/sharedfolder

then I went into fstab..........I can't remember how to modifiy fstab to be honest...........googled.  At the end I did it.

I'm thinking wow I know a lot of people who consider themselves computer savy and I'd imagine it would take them probably a day to figure out something that really should have some gui applications.

Why isn't there any applications to automate this process?  If there is why isn't part of ubuntu's standard package.  I mean we see when we put a usb device we are at least blessed that it's automatically mounted and configured...........................but that's it when it comes to anything automatic.

It's not that I'd want a tool that takes up resources waiting for a new partition, but would be nice to open up a tool, it shows the the only partition that's not mounted like say it does in gparted and then ask where I want it to mount and if I want it to mount each time.  Maybe who has permission to use the partition.

If there's a tool like this that automates everything, what is it?  Why isn't it part of ubuntu's basic install?

---

### Post by FuturePilot on 2008-08-15
idk usually those kind of things get automounted. At least for me they do. I've never had to mess with fstab to get a partition to automount.

---

### Post by bone2006 on 2008-08-17
Hum.............they have never mounted for me.....ever.  You are probably thinking USB device?

I don't think I've experienced a partition that I created from the same system be automounted, if so I didn't realize this was added to the new ubuntu release

---

