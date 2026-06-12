---
title: "I changed fstab now can't boot"
date: 2010-06-12
forum: Server Platforms
---

### Post by danoli on 2010-06-12
I am new to linux and setup an ubuntu 10.04 server for samba sharing. The initial 80gb disk was too small so I added a pc sata card, install a 1tb drive and powered on. All went well so I modified the fstab file to auto mount the drive (I got it working on the command line first). After the change, I rebooted and now it pauses with an error along the lines

fstab line 14 bad code...

I can't remember the error exactly but the problem is that I cannot boot to get in and edit it?

I tried the slax live cd but can't figure out how to mount the right disk/volume to get to the fstab file to fix it?

I would really appreciate some help, ta.

---

### Post by terry_gardener on 2010-06-12
i dont know about the slax live cd, but if you boot from the ubuntu live cd it will list all the drives in places and you just need to click on it and then find the fstab. 

hope this helps

---

### Post by danoli on 2010-06-12
Is this part of the desktop version cd?

---

### Post by terry_gardener on 2010-06-12
yes desktop live cd

---

### Post by danoli on 2010-06-12
It looks like the fstab file is almost empty, does the system keep a previous copy?

---

### Post by danoli on 2010-06-12
Actually, I was looking at the fstab for the live cd....

The actual disk that contains the one I want to edit only has a folder called 'grub' and another called 'lost & found' plus a few files in the root of the disk?

---

### Post by terry_gardener on 2010-06-12
are you sure you have clicked on the 80gb drive as i guess that is where you installed it.

it sounds like you have clicked on the 1tb drive by mistake easily done. 

if you have clicked on the correct drive and it only has grub, root and lost&found folder then os will need a reinstall as it is missing most of the files needed.

---

### Post by danoli on 2010-06-12
Hmm, I am pretty sure I clicked the correct disk but I will double check tomorrow as I have left the office for the day.  If the files are gone, is there any way to discover what went wrong othe than a coincidental disk failure, although I'd guess that would take the whole drive out?

All I did was add an entry to the fstab file using vi and I think the problem is that I left a blank line at the end :(

---

### Post by danoli on 2010-06-14
I have just double checked and it is the 80gb drive.

I am getting the following errors (below) which would indicate that it is trying to read an fstab file as it is failing on line 14 but there is nothing in the 80gb disk?


warning: bad format on line 14 fstab
/dev/sdc1 was not cleanly unmounted, check forced
mountall: mount /storage/disk1 [624] terminated with status 32
/dev/sdc1 211/124496 files 3.3% non contiguous 
mountall fsck /boot [319] terminated with status 1

---

