---
title: "Setting up large LVM partitions for NAS - ubuntu server 15.10"
date: 2015-12-21
forum: Server Platforms
---

### Post by warr87 on 2015-12-21
Hey,

I've started to get a lot of things in place and now want to get my NAS storage actually up and running. I wanted to install LVM so I can add other disks later on since I want to run RAID in the future. I currently have a WD Red 4TB drive and whenever I try and make a partition for that drive it wont allow me to go past 2TB. This is obviously annoying since I want to add another 4TB hdd in the future. 

*Any help? :confused::(*

I will also be running samba with this particular WD 4TB drive being mounted as "/data". My Current OS is 15.10 server edition, and is on a 120 GB SSD.

Thanks.

-Warr87

---

### Post by darkod on 2015-12-21
1. If you have not gone too far in configuring the server, I would suggest starting from scratch and installing 14.04 LTS. Always use LTS version for servers, even for home. They have 5yrs of support, while the other "normal" releases have only 9 months.

2. If the partition table you created on the disk is msdos, they have a limit of 2TB. You need to create gpt table on the disk and then you can create single partition spanning the whole disk.

---

### Post by warr87 on 2015-12-22
I've already gone pretty far with my setup, and what I have now is working (as opposed to before), so for the moment I will keep 15.10. I know the LTS versions are more stable ....

And I will do some reading and try making it a GPT table instead of msdos.

Thanks.

---

### Post by MAFoElffen on 2015-12-22
> **darkod said:**
> 1. If you have not gone too far in configuring the server, I would suggest starting from scratch and installing 14.04 LTS. Always use LTS version for servers, even for home. They have 5yrs of support, while the other "normal" releases have only 9 months.

2. If the partition table you created on the disk is msdos, they have [COLOR=#ff0000]a limit of 2TB[/COLOR]. You need to create gpt table on the disk and then you can create single partition spanning the whole disk.
Note that you also want to look at how recent the System is. On some somewhat recent, but still older systems, there was a time when the controllers would only support up to 2 TB drives. I have 3 servers that are like this. These 3 of mine will support 10 SAS/SATA 6GB/s drives, JBOD/RAID 0/1/5/6... but not recognize anything above 2 TB. I didn't find this out until I went to install a 4 TB drive in one of these, and it showed up as only 2 TB... I wasted a week thinking there must have been something I was doing wrong...

On those, I started out with a 2 TB drive as the LVM Root drive. Agreed with Darkod as 14.04 LTS... except if you are installing on a UEFI BIOS'ed system as a home server and you plan to keep it UEFI ... In that case, do as 15.10 and convert the APT cfg to update as LTS when 16.04 comes out, and is released... Just the way that newer it handles EFI = more dependable with that aspect and less work.

Just in case you ever have to do this manually, this is what you will end up with GPT partition table and partitions as:
1. bios_boot (not formatted)
2. EFI (EFI, FAT32) <-- I just started adding these and keeping them there just in case it goes to a newer system...
3. Boot (Primary,ext2,bootable)
4. LVM (lvm partition)

Note that above, if you have a legacy BIOS'ed system, the above structure will still install, and it will be prepared for others things later down the road...  
Also note that I don't like to allocate all my disk at one time. I partition and allocate my extents, as I need them, that way if I need to allocate a temp logical group for a snap shot or something else, then I can. 

Two tips-- 
- Make home it's own lv.
- Print out a copy of your layouts (partitions and your LVM structure) Keep this in a safe place in case you veer have to mount your LVM from a LiveCD. This will save a lot of time and make things easier, if you ever have to recover an LVM.

LVM is really very flexible and adaptable. After playing with it, and forcing myself to learn it, then I learned to trust it. The way you can grow and shrink volumes quickly... I am really comfortable with it now. Changing out disks is easy, except for changing out a root drive... It can be done, but is a challenge.

---

