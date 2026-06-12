---
title: "Grub2 broken after LVM changes"
date: 2012-10-08
forum: Server Platforms
---

### Post by hozzaconners on 2012-10-08
I wanted to use my server initially to try different Linux variants. Over the last year or so I've been through the following process:

1. Install Fedora 16 root on root
2. Create LVM
3. Install Fed 16 /home and /swap on LVM partitions
4. Write Grub2
5. Install Ubuntu Server 11.10, along with a number of other Linux OS's, on LVM partitions.
6. Update Grub2 which shows all OS's in an Ubuntu styled Grub2 loader
7. With each install, install / on one partition, /home on one partition, /swap on one partition (ie 3x partitions per install)
8. Upgrade Ubuntu Server to 12.04, done loads of tinkering, get it running nicely, been an idiot and not backed up config/data/OS files

It's all been working well, and I found I was using 12.04 to do everything, so last night I decided to get rid of the other OS's and stick with 12.04. I went through the following process:

1. From 12.04, remove LVM partitions from other OS's
2. Remove Fed 16 /home and / partitions
3. Attempt to remove Fed 16 /swap - I get an error message saying it's in use
4. Reboot machine
5. Get message saying "error unknown file system" "Grub Rescue>"

OK, so it's broken. Found various instructions on internet and have now done the following:

1. Boot from Live CD
2. mount /dev/sda1 /mnt/
3. grub-install --root-directory=/mnt /dev/sda
4. Reboot
This boots into a "GNU GRUB version 1.99-12ubuntu5" screen with a grub command prompt. I am now at a loss as to how I can boot to 12.04.
5. Boot to Live CD
6. Partitions appear. Try to copy / and /home data off for storage, but after sitting for lots of time nothing has copied across, just seems to be sitting there

Ideally I'd like to get Grub running so that I can boot into 12.04 and copy data off before reformatting drive and starting again. If this is not possible I'd like to boot into LiveCD and copy data off, so that I can start from scratch.

I'm asking myself the same questions as you..."Why has this idiot done it this way" and "What kind of a doughnut doesn't back up his important files?!"

Any help gratefully received!

---

### Post by darkod on 2012-10-08
Why would you use the standard instructions to mount sda1 as your root partition when you are using LVM?

If your root partition is inside the LVM it's not sda1 any more, right?

I assume you are trying to repair grub using ubuntu desktop live cd. Boot into live mode, open terminal, install lvm2 (it's not in the desktop version by default), activate the LVM, and then mount your root LV and install grub2 on the MBR of /dev/sda. Something like:
```
sudo apt-get install lvm2
sudo vgchange -ay #(note down the 12.04 root like /dev/mapper/VGname/LVname)
sudo mount /dev/mapper/VGname/LVname /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

i think that should work, I don't think you need to adjust anything else.

---

### Post by hozzaconners on 2012-10-08
Thanks for the reply darkod.

What you're saying makes perfect sense...the reason I'd done it that way was because I couldn't figure out how to point to the LVM root.

So I tried the solution you gave me, and on reboot it's given me a "GNU GRUB version 1.99-21ubuntu3.1" screen with a grub prompt. No nice menu pops up allowing me to boot to the OS.

Any ideas where I go from here?

Thanks!

---

### Post by darkod on 2012-10-08
Are you sure you actually have grub2 and all config files present in ubuntu?

On the other hand, it might not have worked because of the LVM, I have never tried to reinstall grub2 to the MBR for LVM system.

You might need to use the full chroot procedure so you can run things as if within the LVM installation.

---

### Post by hozzaconners on 2013-02-04
As a quick FYI as I close this thread, I spent hours on this and couldn't find the right solution, so ended up reformating, reinstalling and starting from scratch.

---

