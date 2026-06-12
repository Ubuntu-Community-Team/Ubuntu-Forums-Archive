---
title: "Lets Talk..Solid State Drives and Linux.."
date: 2012-04-11
forum: The Cafe
---

### Post by Bandit on 2012-04-11
I am looking for feed back from anyone who has been running any solid state drives, more so from those who are running them on Linux. 

I am upgrading my system this summer and the slowest link is my hard drives, just like everyone else. I am running 4 Western Digital Caviar BLUE drives as a Stripped Array (RAID0). Which really really helps kick up the speed (380MB/s Read, 370MB/s Write max under crystalmark with average on both around 270ish), but sacrifices data security because its not a real RAID since there is no data redundancy. So if one drive bites the dust, the whole deal has to be re-installed and any unbacked up files are gone. I been lucky so far no hick-ups. But anyway I am wanting faster speeds so I am considering purchasing SSDs. Particularly the new OCZ Vertex 4 series based on the new INDILINX controller which is supposed to be a huge improvement over the Sand Force line.

So here are my concerns. First is RAID Support. I am wanting to pair two of these up as a Stripped Array for my system. Then move my /home directory over to my Caviar drives and mirror those.
But how does Linux kernel handle garbage collection like TRIM support? Also how would one update the Firmware on these drives?
What speeds do you get as well under Linux? Also how stable are they after hours or even months of non stop use? I really would like to purchase these drives, but dont want to purchase something that is a headache. 

Comments? Suggestions?

Thanks,
Joe

---

### Post by oldfred on 2012-04-12
I recently installed a HouseBrand MicroCenter SSD and have 12.04 running on it, but still primarily boot my spinning drive. I will give you some links with info if you want to review. I am not a fan of RAID on Desktops nor RAID 0 nor RAID 1. I prefer to use extra hard drives for backup or alternate boot drive.

I configure my SSD with the full system that will boot on its own without any other drive including /home but no swap. I rarely use swap anyway with 4GB of RAM. But I only have hidden user configuration files from /home in /home and all data folders including some of the hidden folders with fair amounts of data are still on my rotating drives and linked into /home.

Not required with newer kernels
[http://disktrim.sourceforge.net/](http://disktrim.sourceforge.net/)
Typical fstab entry:
```
UUID=d65e4ad3-6315-4838-97a1-ec574cb8575f / ext4 noatime,discard,errors=remount-ro   0       1
```
Alternate to discard, call fstrim via cron  - I did not set discard right away, so I used this to houseclean.
[http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html](http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html)
fred@fred-Precise:~$ sudo fstrim -v /
/: 23267893248 bytes were trimmed

Some links are starting to get older, I like the Arch site links.
Issues with OCZ Vertex II SSD and discard option
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives) - SSD
[http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment](http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment)
[https://wiki.ubuntu.com/MagicFab/SSDchecklist](https://wiki.ubuntu.com/MagicFab/SSDchecklist)

BIOS settings (SSD but also most systems)
[http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561](http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561)

I used gpt as suggested by Arch, and configured both an efi partition as I hope to have new system in a few months and bios_grub for booting with BIOS for now.

[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)

```
fred@fred-MavericDT:~$ sudo parted /dev/sdd unit s print
[sudo] password for fred: 
Model: ATA SSD G2 series 64 (scsi)
Disk /dev/sdd: 117231408s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start      End         Size       File system  Name  Flags
 1      2048s      616447s     614400s    fat32              boot
 2      616448s    618495s     2048s                         bios_grub
 3      618496s    58925055s   58306560s  ext4         04
 4      58925056s  117229567s  58304512s  ext4         10



```

---

### Post by Paqman on 2012-04-12
> **Bandit said:**
> 
But how does Linux kernel handle garbage collection like TRIM support?

Fully supported in recent kernel versions. All you need to do is add the option "discard" to /etc/fstab.

> 
Also how would one update the Firmware on these drives?


Depends on the drive I'd imagine. I have Intel drives, they provide a tool you burn to a disk and boot from.

> What speeds do you get as well under Linux? 

Depends on the drive and the filesystem. I wouldn't expect speeds to be much different under Linux to other OS/filesystem combos. Looking back at an old thread it seems I read about 275MB/s at 0.1ms access time with no tweaking.

> 
Also how stable are they after hours or even months of non stop use?

Absolutely rock solid from both my Intel drives (X-25M and X-25V). Fit and forget.

---

### Post by Grenage on 2012-04-12
Also using SSDs, Vertex IIs on this particular machine.  You won't go back to mechanicals, the difference is borderline hilarity.

---

### Post by Bandit on 2012-04-12
Really good info everyone. I appreciate the responses. Has anyone tried TRIM under RAID0 though? Seems there is still issues in that area from what I have read off other forums.

---

### Post by Paqman on 2012-04-13
RAID0 on an SSD? Would the increase in speed be worth the reduced reliability? Not at all worth it on a desktop IMO.

---

### Post by Bandit on 2012-04-13
> **Paqman said:**
> RAID0 on an SSD? Would the increase in speed be worth the reduced reliability? Not at all worth it on a desktop IMO.

Just going to use them as my system drive, going to place my /home folder over on one of my current drives and use another to keep a daily backup. If the Stripped SSDs go down I can use reinstall the OS off a USB and with my daily backup have it up in running back to original state in a hour or two tops. I am more worried about my 60gigs worth of music I purchased over the past 15 years and/ or the 50ish gigs worth of family pictures being lost.

---

### Post by a2j on 2012-04-13
I used to have 4 drive RAID0, now I have ssd. Its not the same. With ssd I get 550MB/s.

---

### Post by haqking on 2012-04-13
I run 2 crucial M4 128GB ssd, one with windows 7 on and the other with slackware and debian

firmware is updated with a boot cd from crucial.

sound as a pound and well worth the dosh.

i get 550MB/s too

and they run all day 24/7

Peace

---

### Post by oldfred on 2012-04-13
I used to install from USB flash drives as that was faster than CD and reuseable. But I converted to using ISO directly with grub loopmounting them on flash drive. With my install to the SSD I used the ISO on my rotating hard drive. I never have seen an install go so fast, even with the limits on download speed for the updates it was extremely quick.

Hard drive:
Direct boot on hard drive - drs305:
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

---

