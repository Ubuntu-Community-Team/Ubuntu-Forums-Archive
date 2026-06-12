---
title: "Ubuntu 14.04 server lvm on raid 1, no boot from raid"
date: 2015-09-17
forum: Server Platforms
---

### Post by Kevin_Damstra on 2015-09-17
Hey guys,

Just wondering, I currently use the following setup;

- 64Gb ssd, Ubuntu 14.04 server
- 2 Tb, mediafiles, movies and music 
- 2x 4 Tb in Raid 1, pictures, videos, other important files

No I've read a lot about the advantages of LVM, read some articles and tried to find a how-to that fits my situation here.
I tried following [http://blogging.dragon.org.uk/installing-ubuntu-14-04-on-raid-1-and-lvm/](http://blogging.dragon.org.uk/installing-ubuntu-14-04-on-raid-1-and-lvm/) but i have a question.
This guy boots from his raid setup, in my case this is not neccesary. So how do i devide my raid setup, do i still require a boot section?

3 sections; /boot/, /root/, /swap/

I tried to setup my raid device with just the /root/ and /swap/ sections, install ubuntu on the ssd and booted the system, no luck. I used a USB stick with a clean install of 14.04 server, all the disks can be formatted.

So the question is, how do i get the same setup as described before, but using lvm? Do i just use LVM on the 4Tb disks?, the 2Tb disk is just a dump and i dont want to integrate the ssd since its speed.

Thanx!

---

### Post by darkod on 2015-09-17
Sorry, but I didn't understand on which disk are you actually planning to install ubuntu. The SSD? In that case, you don't even need root md device on the 4TB disks. You need a big partition on them for data only, if the OS will be on another disk.

---

### Post by Kevin_Damstra on 2015-09-18
Darko,

I will use the ssd for ubuntu, so the two 4Tb disks are for data only.

The last time i tried to setup LVM on raid 1 with the two disks i had two partitions;

1# Raid 1; /root/
2# Raid 1; /swap/

Then when i tried to boot the system, it couldnt, i ended up with an unbootable system. So i just use the ssd, flag it as bootable and all the other disks stay /usr/ or /data/?

Ill try again and show some pics of the configuration.

---

### Post by darkod on 2015-09-18
Yes, install ubuntu on the ssd and have the raid1 md device mounted as /data for example. You can create the raid during install and the mount point. Just make sure not to mix it up. The / partition goes to the ssd.

If you want, you can try again installing only using the 2x4TB disks. Using the ssd for ubuntu server might be little bit of waste. I am not sure it benefits from the ssd speed.

---

### Post by Kevin_Damstra on 2015-09-20
Well, i tried various options, can't get it to work.

Latest setup; (also see attachement)
[http://pasteboard.co/MmA0R6R.jpg](http://pasteboard.co/MmA0R6R.jpg)

ssd (120Gb); 
- sdd1, 110Gb, B, ext4, /
- sdd2, 10Gb, swap 

hdd1 (4Tb);
- sdf1, 4Tb, K, raid

hdd2 (4Tb);
-sdg1, 4Tb, K, raid

LVM VG vg0, LV lv_archive - 4,0 Tb Linux device-mapper, (unallocated space 20Gb)
Raid1 device #0 - 4,0 Tb Software Raid device

I also tried to reinstall grub to /dev/sdd1 but this ends in a fatal error; "exit 1"

I'm kinda stuck at the moment here...

---

### Post by Kevin_Damstra on 2015-09-20
Alright, tried a different setup;

[COLOR=#000000]ssd (120Gb); [/COLOR]
[COLOR=#000000]- sdd1, 10Gb, B, ext4, /boot
[/COLOR]- sdd2, 100Gb, ext4, /
[COLOR=#000000]- sdd2, 10Gb, swap [/COLOR]

[COLOR=#000000]hdd1 (4Tb);[/COLOR]
[COLOR=#000000]- sdf1, 4Tb, K, raid[/COLOR]

[COLOR=#000000]hdd2 (4Tb);[/COLOR]
[COLOR=#000000]-sdg1, 4Tb, K, raid[/COLOR]

[COLOR=#000000]LVM VG vg0, LV lv_archive - 4,0 Tb Linux device-mapper, ext4, /usr (unallocated space 20Gb)[/COLOR]
[COLOR=#000000]Raid1 device #0 - 4,0 Tb Software Raid device

So with even a /boot section with seperate /root section it doesnt boot yet...
[/COLOR]

---

### Post by darkod on 2015-09-20
First, grub never goes to a partition. And /dev/sdd1 is a partition. It goes to the MBR of a disk, which is always /dev/sdX format, never /dev/sdXY. No number in it.

Second, what I see is that you are using usb stick to install from I guess. The stick is /dev/sda so if the installer puts grub only there, without the stick the machine will not boot even though all is installed good.

Also, your attached image does not show any mount point or filesystem for lv_archive. Did you set it up to be used or not yet? I am just asking, this is not needed for the system to boot, because your / is on the ssd.

You don't need separate boot, that's not your problem here. The grub bootloader install location might be the problem.

Which disk is the machine booting from in bios? I see sdd, sdf and sdg but nothing about sda,sdb,sdc? Why do your disks start from sdd?

---

