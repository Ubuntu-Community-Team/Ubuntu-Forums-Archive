---
title: "Installing 13.04 in an SD card"
date: 2013-01-28
forum: Ubuntu Development Version
---

### Post by nomenkultur on 2013-01-28
I had to wipe my hard drive and lost my u13.04 install...
 
I would like to continue using u13 but this time as an "exterior" operating system.
 
In order to do this, what is the best option?
 
Is it at all possible to run a normal install and point the installer to an SD card instead of the laptop's hard drive?
 
 How much space does a normal install require?
 
 I wanted to avoid unetbootin and live sessions so I could actually install stuff and define my passwords.

---

### Post by dino99 on 2013-01-28
you need to select "something else" from the installer dialog box, to select installation onto the sd card (if the bios can boot on sd indeed), and allow enough space:

use gparted or partedmagic to create 3 partitions:
- / : root, bootable, ext4, ~ 12 Gb (take note of its name: /dev/sd? , will be asked when installing the  iso.
- swap : about 2 Gb (4 Gb if suspend/hibernate will be used)
- /home : ext3 or ext4 format, unlimited space to store your data and settings

note: of course, swap & /home partitions can be on hdd/ssd instead of the small sd card.

---

### Post by nomenkultur on 2013-01-28
yes, I wanted to have the entire system in the SD and not to touch the hard drive but that kills it :( 
 
 I have a bunch of sd cards but none of them is 16G...
 
 I guess unetbootin with persistence will probably be the best I can do

---

### Post by mlentink on 2013-01-28
You do not need 16GB, 8GB is ample. Neither do you need to make a separate /home partition. It is entirely feasible to install ubuntu on a 8GB SD card. Just use "Do something else" at partition time in the installer, and do not forget to install GRUB to the SD-card, if you want to be able to install another OS on the harddisk and use that with the SD-card detached.

---

### Post by ronacc on 2013-01-28
if your box will boot off of an sd card (my eeepc will ) you can get a full install on an 8 gb card , either partition it 6gb/ and 2gb /home or the whole 8gb as / with no seperate /home no swap in either case, you won't have much room for "extras" but it will work .

---

### Post by dino99 on 2013-01-28
8 Gb, well its possible indeed, even less if you only install what is stricly needed.

But i suppose that installing ubuntu without apps is quite useless: so having some free space to be able to upgrade, get some packages in cache, and some required dynamic space dedicated to /temp for breathing is a good idea  .

Otherwise dont forget  to purge the cache and clean the system to avoid the nice "out of space" error  :)

---

### Post by jerrylamos on 2013-01-28
> **nomenkultur said:**
> I had to wipe my hard drive and lost my u13.04 install...
 
I would like to continue using u13 but this time as an "exterior" operating system.
 
In order to do this, what is the best option?
 
Is it at all possible to run a normal install and point the installer to an SD card instead of the laptop's hard drive?
 
 How much space does a normal install require?
 
 I wanted to avoid unetbootin and live sessions so I could actually install stuff and define my passwords.
Best you can do is an external hard drive connected to USB port if your pc will boot off usb.

Amazon sells USB cases for a hd for $10 or so.  They have versions for both SATA and IDE.  I had left over 2.5" lap top drives.  These can be ordered from Amazon or Tiger Direct or at your local computer store that sells used hard drives.  Simply insert hard drive into case and connect to USB port.

I do O.K. with a little 40 GB hard drive connected via USB, two partitions of 8GB for Ubuntu current one and next one to try, a 1 GB swap (hardly used), and another partition for archiving stuff.

Works fine on two of my three test pc's.  Other one Acer 5253 wide screen notebook has bugs in USB.  It will boot and run fine but is very cranky about installing to the USB hard drive.

My experience in running to USB pen drives is s-l-o-w.  I suspect the same with SD card, but having said that I've a little $35 Raspberry Pi computer which runs off SD card O.K.  I'd suggest 8GB anyway.  Amazon etc. sells 16 GB and more.  Maybe I'll try it, I've got an unused 8 GB right here.

Do note SD is a flash memory, and after a certain number of writes it fails.  Reading lots of times is O.K.

---

### Post by cariboo on 2013-01-28
I had Lubuntu installed on an 8GiB micro sd card, that I ran for a while, aside from it seeming to take longer to boot than from the hard drive, it worked quite well.

---

