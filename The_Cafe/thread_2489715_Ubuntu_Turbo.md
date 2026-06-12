---
title: "Ubuntu Turbo"
date: 2023-08-08
forum: The Cafe
---

### Post by xinuzi on 2023-08-08
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292573&stc=1[/IMG]

Space, the Final Frontier... ;-P

Don't ask for further details but some settings that still seem to give extra punch to Ubuntu:

(Any text editor will do, here geany)

To check before/after a few things in cli:

```
cat /proc/sys/vm/swappiness
cat /proc/sys/vm/vfs_cache_pressure
```

Adaptations of these things in file **/etc/sysctl.conf,**
to be opened in your favorite text editor:

```
sudo geany /etc/sysctl.conf
```

Add at the bottom:

```
# Optimize Swap (was: 60) 
vm.swappiness=10

# Optimize Cache (was: 100)
vm.vfs_cache_pressure=50
```

Save.
Close file.
Effect after reboot.

(*Update: it's maybe advised to just do the swappiness setting only.*) 

Personal choice, but on an 8 Gib ram machine I usually set swappiness to 10, on a 4 Gib ram pc to 5.

Actually I was looking for sth to speed up my video conversions and lazy USB3 FAT32 transfers...

In case of the latter, I read this on wiki.debian.org:

"Add the 'noatime' (or the default 'relatime') mount option in /etc/fstab, to disable (or significantly reduce) disk writes whenever a file is read.
This improves filesystem read performance for both SSDs and HDDs."

Things to try!

Bye-bye & cheers :-)

---

### Post by lammert-nijhof on 2023-08-08
I agree with your remark about the time option for fstab, that can speed up your system.  I disagree with the paging advice, it depends completely on your work load and configuration. 
You try to keep the memory pages with code and data longer in memory. However the pages that are swapped out are the least recently used pages, that are the pages that were used during program start up or those that deal with exceptions. Keeping those pages in memory has no advantage, it just spoils your memory. Changing these values is only advantageous, if the main loop of the program needs all physical memory. The advantage will be mainly noticeable with a classical HDD. 

I have a 16GB; a nvme SSD (3400/2300MB/s) and the 2nd slowest Ryzen (Ryzen 3 2200G). I run Virtualbox VMs and I did not change anything in those swapping parameters and my VMs swaps a lot.  I only have to take care, that the Hosts swap file does not exceed too much the 2 GB swap partition on the nvme-SSD. As long as the pages stay within the 2 GB nvme-swap partition, the system and the VMs runs fine and if the 2 GB swap partition is used, I have 2GB more main memory available for an additional Ubuntu VM :)  So I love it, that unused parts of my programs and VMs are swapped out :)

---

### Post by xinuzi on 2023-08-09
Interesting points you make.

These things depend on personal choice.

I like the speed increase after the swappiness change.
Although the general speed of the system was already very good.

Less sure of the effectiveness of the 'vm vfs cache pressure' reduction.
Commented aka blocked it for the moment.

The extra mount option, I leave it as-is.
The system is usually configured the best way possible by default.

Wiped & reformatted the FAT32 USB3 sticks to NTFS with gparted.
Increadible speed increase.
100% transfer = 100% transfer. Full Stop. Not actually 100%+muchtiiiiimeaaaaafter.
They sell those larger USB3 sticks most often with FAT32 pre-installed (also better compatible with Mac, so I've heard).
Thereafter customers get disappointed about the unexpected poor transfer speeds, not having a clue.
FAT32 doesn't belong on those USB3 sticks. NTFS does.
If FAT32 vs NTFS is already 'an issue' concerning compatibility, ext4 would, alas, be an even bigger issue.

Other important advantages (on linux) of NTFS (on external disks):

- Bash opens directly when clicking a(n) (executable) shell script from the external usb-disk. On FAT32 you have to open the terminal and then 'bash file.sh'.
- Most actions can be done immediately on the external usb-disk at speeds comparable to those of a hard drive. So, e.g. if you want to transcode a video, or videos in a 'for i in' loop, probably from a bash script calling ffmpeg, you don't have to copy those videos to your hard drive first. Sufficient converting speeds.

I'll format FAT32 on usb sticks that need to be very compatible (and don't often need file transfers), like those used on the car radio-usb (haven't checked if ntfs would work on that - probably not).
Bigger sticks, bigger, regular file transfers, still compatible with Windows: NTFS.

Cheerio.

---

