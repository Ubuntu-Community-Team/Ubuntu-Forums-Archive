---
title: "Backup /root-partition/ &amp;&amp; Restore to New Drive"
date: 2016-02-09
forum: Ubuntu, Linux and OS Chat
---

### Post by mikodo on 2016-02-09
In the case of an internal disk failure or, before I hosed the OS. 

I want to consider backing up the  /root_partition/ now, too. I don't want to [image]("http://www.clonezilla.org/") the partition every day/week. If I was, I would use dd or other cli like [fsarchiver]("http://manpages.ubuntu.com/manpages/lucid/man8/fsarchiver.8.html"). I want to use [rsync]("http://manpages.ubuntu.com/manpages/maverick/man1/rsync.1.html") as a quick and complete backup to other nodes for, being available for accessing and syncing a new /root_partition/ to the present state of the backups. Backups with rsync are quick and easily done with one line in terminal. Its' algorithm can be used to only send the present changes to backup with the option, rsync -- delete.  Therein lies, the advantage for using rsync as, I see it.

I already have a comfortable backup scenario for backing up my data  partition to usb nodes using rsync. For, differential backups, I am  thinking of using [rdiff-backup]("http://www.nongnu.org/rdiff-backup/index.html")  in the future. I haven't got to "playing" with this yet. When I get to  using it for backups, the same principles should apply with rdiff-backup  for this guide as, it seems to have the options I use in rsync. **Then, I  could revert my system to an earlier differential, long before I hosed  it.** Thanks, TheFu.

I read in the forums that on re-install, in this case from .iso cd/dvd/usb(flash-drive),  one can choose the /root_partition/ and tell d-i/ubiquity to use the  /root_partition/ _without formatting it_. 

So, I was thinking of backing up my /root_partition/ with rsync, and in  the case of needing to reinstall, make a new /root_ partition/ and move  the data from backup to it and use that for installation and *not* format  it. 

Or, as seen below, use an .iso *live* cd/dvd/usb and use [chroot]("http://manpages.ubuntu.com/manpages/trusty/man2/chroot.2.html") to install a new Grub2 boot-loader  and [tune2fs]("http://manpages.ubuntu.com/manpages/hardy/man8/tune2fs.8.html") to find and edit the UUID's of a sync to a new /root_partition/ from backups.

One could make a 512 MiB Ext4 partition or EFI FAT32 partition on sda with the boot flag first for, use with encryption. Then, the partition for the /root_partition/. Thanks, sudodus.

Example:

```
backups: 

**sudo **rsync -av --delete /root-partition/ /media/user/partition_label

sync:

**sudo** rsync -av /media/user/partition_label/ /dev/sda1

```
- Because it is root, should I run rsync with sudo rsync?

Thanks.

---

### Post by sudodus on 2016-02-09
If you copy your root partition with ```
sudo rsync
``` with the archive option to another ext4 file system in a second drive, it will be a 'complete' backup copy. The only thing you need to add are the other partition(s), *swap* (and in your case *data*) and install the *bootloader*. See the examples in ```
man rsync
```

This means that you can also copy it back with rsync and expect it to work. As usual, you should test that it really works (with a root partition in a third drive as target).

---

### Post by mikodo on 2016-02-09
Thanks, sudodus. You "the man".

Have a great day!

---

### Post by sudodus on 2016-03-07
I saw your other thread, and looked back into this thread.

There are a couple of things, that I should add, If you do not want to restore from the backup to the original root partition, but create a system in a new drive (the case when the old drive has failed). In this case the UUIDs of the partitions will be different.

1. Match the UUID specifications in the file **/etc/fstab** (for each partition, that you use, the root and maybe home, and for swap) to the current values of your partitions as seen with for example ***sudo blkid***

2. Match UUID specifications in the file **/boot/grub/grub.cfg** for the root partition.

If you replace the previous drive, you can change the UUIDs to those of the previous drive (more convenient), but if you want to connect both drives, it can cause severe confusion, and it is better to change the UUID specifications in the files (more rebust).

---

### Post by mikodo on 2016-03-07
a

---

### Post by sudodus on 2016-03-13
You are welcome :-)

---

### Post by kevdog on 2016-03-14
I usually use dd for directly copying partitions.  You just then need to modify your /etc/fstab file since the UUIDs are going to change with the new drive.  You then need to reinstall grub most likely and let it build the initramfs all over again.  It sounds complicated -- and it is the first time.  When you're done, you'll say -- that was easy.

---

### Post by mikodo on 2016-03-14
Thanks for sharing. Nice to hear of others' positive experience of doing this. With your sharing and the hand-holding I've had so far, I think my half-baked idea is going to work..

---

### Post by mikodo on 2016-03-14
Double entry response to kevdog.

---

### Post by mikodo on 2016-06-29
It looks like I may use this soon when replacing the drive.

This should work for replacing the drive or, as mentioned earlier, replacing the full OS from earlier rdiff-backup deltas if needed, on this BIOS, MBR machine.

This needs to be done in a 'Live cd' or, with my preference, a 'Persistent Live System' from OBI/mkusb, to do backups and transfer of whole OS from backups to a new or freshly re-formatted drive.

1) Copy UUID&#8217;s of the old Root install and data partition and have saved in backups.

2) Remove old drive > install new drive.

3) Partition new drive with / partition (sda1) & data partition (sda3). 

4) Rsync / partition backups to new / partition (sda1). Rsync data partition backup to new data partition (sda3).

*Remember, these are newly made partitions, so they will have new UUID&#8217;s. Do #5.

5) Change UUID's in new drive to match old ones I saved. Use with the second command exampled here:

[http://www.sudo-juice.com/how-to-change-the-uuid-of-a-linux-partition/](http://www.sudo-juice.com/how-to-change-the-uuid-of-a-linux-partition/)

< sudo tune2fs /dev/sde5 -U <Old UUID&#8217;s >

6) Enter chroot environment. Follow the guide starting at: 6, 7 & then to 10, 11, 12, 13, 14: 

[https://help.ubuntu.com/community/Grub2/Installing#via_ChRoot](https://help.ubuntu.com/community/Grub2/Installing#via_ChRoot)

To see what this means:

< for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt$i; done >

 [https://ubuntuforums.org/showthread.php?t=2330080](https://ubuntuforums.org/showthread.php?t=2330080)

.......................................

**For New Computer** >  UEFI > test for backup/return of the  (pre-partitioned) > 1GiB EFI System Partition (ESP; /boot/efi) on  different drive connected, singularly.  

Replace the newly made partition GUID's  for / and the data partitions to, the old ones copied.

For the new Computer, Rod Smith's explanation sounds hopeful I can copy  over the ESP && / files > then install Grub2 &&  update-grub and expect it to work. Particularly when, I would be  reinstalling the bootloader to "let it build the initramfs all over  again" anyway. 

"Re-installing another OS's boot loader should also work ..." [https://askubuntu.com/questions/666602/location-of-grub-on-gpt-partition](https://askubuntu.com/questions/666602/location-of-grub-on-gpt-partition)


Thank you, for all the advice everyone.


Notes

For dd one should use <sudo -i> . See link below.


Further reading

[https://help.ubuntu.com/community/OBI](https://help.ubuntu.com/community/OBI)

[URL="https://help.ubuntu.com/community/mkusb"]https://help.ubuntu.com/community/mkusb

[/URL][https://help.ubuntu.com/community/mkusb#Persistent_live_systems](https://help.ubuntu.com/community/mkusb#Persistent_live_systems)

                         [http://xubuntu.org/news/booting-the-xubuntu-usb-image-from-a-cd/](http://xubuntu.org/news/booting-the-xubuntu-usb-image-from-a-cd/)

[https://rc.fas.harvard.edu/resources/documentation/linux/rdiff-backup/](https://rc.fas.harvard.edu/resources/documentation/linux/rdiff-backup/)

[http://askubuntu.com/questions/491082/steps-to-create-dd-image-file-from-usb-and-restore-image-to-a-different-usb](http://askubuntu.com/questions/491082/steps-to-create-dd-image-file-from-usb-and-restore-image-to-a-different-usb)

[https://wiki.archlinux.org/index.php/disk_cloning#Using_dd](https://wiki.archlinux.org/index.php/disk_cloning#Using_dd)[URL="https://help.ubuntu.com/community/Grub2/Installing#via_ChRoot"]

[/URL][https://wiki.archlinux.org/index.php/Master_Boot_Record](https://wiki.archlinux.org/index.php/Master_Boot_Record)
[URL="https://wiki.archlinux.org/index.php/Master_Boot_Record#Backup_and_restoration"]
[/URL][URL="https://wiki.archlinux.org/index.php/Master_Boot_Record#Backup_and_restoration"]https://wiki.archlinux.org/index.php/Master_Boot_Record#Backup_and_restoration

[/URL][https://superuser.com/questions/111152/whats-the-proper-way-to-prepare-chroot-to-recover-a-broken-linux-installation](https://superuser.com/questions/111152/whats-the-proper-way-to-prepare-chroot-to-recover-a-broken-linux-installation)

---

### Post by Habitual on 2016-06-29
> **kevdog said:**
> I usually use dd for directly copying partitions.
What ^ said ;)
[https://wiki.archlinux.org/index.php/disk_cloning](https://wiki.archlinux.org/index.php/disk_cloning) is Good Stuff, Maynard.

---

### Post by mikodo on 2016-06-29
> **Habitual said:**
> What ^ said ;)
[https://wiki.archlinux.org/index.php/disk_cloning](https://wiki.archlinux.org/index.php/disk_cloning) is Good Stuff, Maynard.

Thank you, for your advice. 

May I ask you a couple newb questions? 

1. Why use dd instead of rsync? What are the advantages of that?

2. Would dd cloning of a partition (make image) be more effective in bringing my DE "configurations" in my Xubuntu install's root partition with my /home in it, to my new drive than a sync would with rsync? 

Like what the [Xfce Settings Daemon]("http://docs.xfce.org/xfce/xfce4-settings/xfsettingsd") stores of [xconf]("http://docs.xfce.org/xfce/xfconf/start") settings and configurations.

---

### Post by sudodus on 2016-06-30
There are many alternatives that can be used in linux.

I think there are different opinions about methods for {cloning, copying, backing up, porting} a system in general and about dd in particular.

Try more than one method and stay with the method that works best for you :-)

---

### Post by mikodo on 2016-07-03
> **sudodus said:**
> 

I think there are different opinions about methods for {cloning, copying, backing up, porting} a system in general **and about dd in particular.**

+1

I have much to learn about dd. :)

Another thing in my New Projects folder.

I think it would be interesting to see how long it would take to make a drive backup.img from one faster 256 GiB SSD to another identical one.

And, what value there is (if there is any) in the backup.img over using the syncing as I plan to use for starters. See, I have much to learn ...

[http://askubuntu.com/questions/491082/steps-to-create-dd-image-file-from-usb-and-restore-image-to-a-different-usb](http://askubuntu.com/questions/491082/steps-to-create-dd-image-file-from-usb-and-restore-image-to-a-different-usb)

[URL="http://askubuntu.com/questions/338300/how-to-backup-data-from-usb-drive-using-dd-or-dd-rescue-in-ubuntu#"]
[/URL]

---

### Post by sudodus on 2016-07-03
The theoretical SATA III speed is 6 Gb/s, so with dd and similar cloning tools you need

256 * 2^30 * 8 / (6 * 10^9) / 60 min =  6 min.

But a more realistic SSD speed might be 200 MB/s, so

256 * 2^30 / (200 * 10^6 ) / 60 minutes = 23 min.

A realistic USB pendrive speed is 20 MB/s = 230 min (almost 4 hours).

But usually you have a lot of free space, and methods that copy only the used space (files, directory structure etc) are much more efficient, for example rsync, Clonezilla and various backup tools.

---

### Post by mikodo on 2016-07-03
> **sudodus said:**
>  - what you said - 

Thank you.

So, I am not "too far off the mark" with backing up using dd copy and rsync.

For backup to my safety-deposit box, maybe there is value in using the backup.img to swap out drives with. I dunno yet though. It's a pain in the rear, and the data partition is never current. That's why I want to use [TarSnap]("https://www.tarsnap.com/") for my data/Documents partition. But, life keeps getting in the way with all I want to learn and do. My penance for being so hedonistic as a young man. Ex-wives cost money.

Interesting tidbits about Colin Percival. He went to University here in Canada at the age of 13. Got a degree in Mathematics and then went on to Cambridge University and finished at 21 years of age with a PhD. in Computer Science with thesis in (cryptography I believe). Then, was the security officer for a number of years for FreeBSD until he had to relinquish that post to, devote more time to TarSnap management.

I am sure your math would be correct and it does provide the answer to time for me. My education, does not allow any understanding of what the heck you wrote there though. :)

---

### Post by sudodus on 2016-07-03
> **mikodo said:**
> ...
I am sure your math would be correct and it does provide the answer to time for me. My education, does not allow any understanding of what the heck you wrote there though. :)

Use the simple formula ***Time = Size / TransferRate***

The difficult part is to estimate the transfer rate of the cloning operation.

```

256 *   2^30    *     8         / (6 * 10^9) / 60 min       =  6 min.
256   Gibibytes   bits/byte   /  6  Gbits/s  / to-minutes

256 *   2^30      / (200 * 10^6 ) / 60 minutes = 23 min.
256   Gibibytes   /  200 MB/s      /  to-minutes
```

2^30 alias 2³&#8304; alias 1024 * 1024 * 1024, definition of Gibibyte (base 2) = 1073741824 ~ 1.07 GB (base 10)

You can use the command line tool ***bc*** for such calculations

```
[COLOR="#0000FF"]sudo apt-get install bc[/COLOR]

$ [COLOR="#0000FF"]bc[/COLOR]
bc 1.06.95
Copyright 1991-1994, 1997, 1998, 2000, 2004, 2006 Free Software Foundation, Inc.
This is free software with ABSOLUTELY NO WARRANTY.
For details type `warranty'. 

[COLOR="#0000FF"]1024 * 1024 * 1024[/COLOR]
1073741824
[COLOR="#0000FF"]2^30[/COLOR]
1073741824

[COLOR="#0000FF"]scale=1[/COLOR]  # number of decimals

[COLOR="#0000FF"]256 *   2^30    *     8         / (6 * 10^9) / 60[/COLOR]
6.1
[COLOR="#0000FF"]256 *   2^30      / (200 * 10^6 ) / 60[/COLOR]
22.9
[COLOR="#0000FF"]256 *   2^30      / (20 * 10^6 ) / 60[/COLOR]
229.0
[COLOR="#0000FF"]256 *   2^30      / (20 * 10^6 ) / 60 / 60[/COLOR]  # hours 
3.8
```

---

### Post by mikodo on 2016-07-04
Thank you, for explanation sudodus.

I'll look at later. 

I just screwed up my MBR Grub2 entries and couldn't boot into Xubuntu 16.04 or Ubuntu 16.04. I could boot into Xubuntu 14.04.1 though. I read the U. Community wiki on boot repair, went into the live cd for Xubuntu 16.04 and downloaded Boot Repair in the live cd. Expunged the Grub2 entries and re-installed them. Rebooted and saw in the Grub menu entries the partitions for Xubuntu 16.04 && Ubuntu 16.04 and I think Ubuntu 14.04. I am back presently in Xubuntu 16.04 which, I want as my main install going forward now. I ran sudo update-grub in this install just now. It seems to have the other OS I mentioned.

Interesting thing though. If I read correctly, Boot Repair seemed to install the boot loader to sda1. ???? Maybe I had like that before, I dunno.

I am going to do the reboots now. I saved the pastebucket address if I have questions.

Here we go.

---

### Post by sudodus on 2016-07-04
Yes, Boot Repair is a good tool :-)

---

### Post by mikodo on 2016-07-04
> **sudodus said:**
> Yes, Boot Repair is a good tool :-)

Okay. All good so far. I am booting into all 3 distros.

Fixed my wife's screw up with her dvd player commands.

Downloaded the boot-info script:

[http://paste2.org/sBxj2B39](http://paste2.org/sBxj2B39)

I haven't read it yet. Does it say that it actually attached Grub2 to sda1 though?

I'm going to look now.

---

### Post by mikodo on 2016-07-04
I am not sure what this means. But, it is working at least. I am going to save that boot entry on my computer. Who knows how long it is up there. Oh the heck with that. It's huge.

> Recommended repair     The default repair of the Boot-Repair utility will purge (in order to fix legacy files) and reinstall the grub2 of sda1 into the MBR of sda.
     Additional repair will be performed: unhide-bootmenu-10s

grub-install --version
     grub-install (GRUB) 2.02~beta2-9ubuntu1.8,grub-install (GRUB) 2.
  
    Reinstall the GRUB of sda1 into the MBR of sda
     Installing for i386-pc platform.
     Installation finished. No error reported.
     grub-install /dev/sda: exit code of grub-install /dev/sda:0

I ran it from Xubuntu 16.04 as I said earlier. I hope it  means something significant that it has *boot attached to it (sda3). I want to keep that one.

> Drive: sda _____________________________________________________________________
     Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
     Units: sectors of 1 * 512 = 512 bytes
     Sector size (logical/physical): 512 bytes / 4096 bytes
     I/O size (minimum/optimal): 4096 bytes / 4096 bytes
     Disklabel type: dos
  
    Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
  
    /dev/sda1               2,048    49,999,871    49,997,824  83 Linux
     /dev/sda2          54,194,176   263,909,375   209,715,200  83 Linux
     /dev/sda3    *    268,103,680   320,532,479    52,428,800  83 Linux
     /dev/sda4         324,726,784   976,773,119   652,046,336   5 Extended
     /dev/sda5         324,728,832   377,157,631    52,428,800  83 Linux
     /dev/sda6         381,351,936   433,780,735    52,428,800  83 Linux

---

### Post by sudodus on 2016-07-04
> ```
 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub. It also embeds following components:
```


This means that Grub is installed into the head of /dev/sda (sector 1 is the head, it is not partition 1).

---

### Post by mikodo on 2016-07-04
Thank you, sudodus! It was fun to see how you did the math. And, for the confirmation that the MBR with Grub2 is installed on the first sector of /dev/sda.

It was unnerving to mess up my Grub2 like that. But, it did show me Boot Repair. I learned how to use it and save its' boot info script record of Grub2, so as to be able to ask for help if needed. I learned how to use it to completely remove the Grub2 entries in the MBR and replace them.

 I assume Boot Repair rewrote Grub2 in the MBR of the boot sector of sda (446 bytes of 512 bytes total) & (with 64 bytes for the partition table & 2 bytes for the magic number) and edited the /etc/default/grub and/or the scripts in /etc/grub/.d/ to load and build the /boot/grub/grub.cfg in the root partitions. If one already has the UUID/GUID changed over in the new root's etc/fstab, maybe Boot Repair could be used to rebuild the bootloader file in in the /etc/default/grub and rewrite the new UUID specifications in /boot/grub/grub.cfg and be able to boot into the new system. I dunno exactly how Boot Repair works and, I really don't need to know anything other than it works and maybe one could use it, if need be, to deal with the MBR. 

So it seems, Boot Repair may be a gui tool I can use, if I have to.

---

