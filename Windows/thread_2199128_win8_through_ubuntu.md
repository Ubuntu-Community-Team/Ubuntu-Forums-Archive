---
title: "win8 through ubuntu"
date: 2014-01-12
forum: Windows
---

### Post by lizpy66 on 2014-01-12
So I had win8 built into my laptop when I got it, all was good until literally christmas morning when Windows 8 literally locked itself out, I plan on fixing it eventually but how do I check if I still have it through Ubuntu or boot up? I'm not tech savvy if I'm honest. I got Ubuntu when Win8 messed up, like it a lot actually but just want Win8 for games( I know of WINE but it would be easier on WIN) and itunes since nothing else tends to work here so far. Besides that I will keep Ubuntu but just want Win8 for games and itunes. If it helps Win8 messed up at a blue screen and said something about srt trail, can't remember much. I just need to know if Windows 8 is even still on my computer because I think when I installed Ubuntu 13.10 I accidentelly installed over it, if that's so then it's not a big deal I'll get 7 from an old computer I have here I think.


P.S. on a UEFI system

---

### Post by tfrue on 2014-01-12
Computer's that come pre-installed with Win 8 have secure boot, UEFI, and use a GPT partition. So to install Ubuntu you generally have to disable secure boot, and manually partition the HDD in Windows.

I would either boot into Ubuntu or live boot it, but install boot-repair and see if that will help with Windows. It's very possible that you have a corrupt file system, or a bad sector, or a plethora of problems, or maybe not. But I would boot into Ubuntu, again, and see if you can access that Windows partition from Ubuntu using the file manager, back up your files, then troubleshoot Windows or just wipe the HDD, re-install Windows, partition the drive, and re-install Ubuntu.

Chris

---

### Post by oldfred on 2014-01-12
This will show lots of details of your system.
 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

If you install a Windows 7, you have to have a new license as the current one is for the vendor version of Windows 8 and is stored in the UEFI NVRAM. Windows 7 default install also is BIOS, so you have to convert drive from gpt to MBR(msdos). Windows 7 can be installed in UEFI mode only from flash drive with some slight modifications.

---

### Post by UltimateCat on 2014-01-14
To find out if Win's is still on your computer you can use Ubuntu or a Live Ubuntu CD and run this command as 'root'
[B]fdisk -l  (small letter L)

You should be able to see all partitions on your computer-
[/B]

---

### Post by lizpy66 on 2014-01-15
thanks :) did this and was able to see but I don't understand what most of it means. It said dev/sda  util fdisk doesn't support GPT. Use GNU Parted. also said some vg root error thing for ubuntu

---

### Post by tfrue on 2014-01-15
Could you post the output of the command? You will need to use a different disk partitioning tool since fdisk supports BIOS/MBR partitions only. Gdisk, and parted both support the use of UEFI/GPT partitions so to view the GPT on your disk, use those. I think you will have to download gdisk, but parted might be installed. To download gdisk, type:
```
sudo apt-get install gdisk
```
Let it install, then the syntax is:
```
sudo gdisk /dev/sda
```
If it ask if you want to use GPT or MBR, use GPT so type 2.
Then would you post the output of each command, please:
```
p (This will print the partitions on the disk.)
i
1 ("i" will show detailed info on a partition, 1 selects which partition to use. Copy the info after typing 1)
i
2 (Post this output.)
i
3 (Post if applicable.)

```

Thanks,
Chris

---

### Post by UltimateCat on 2014-01-18
> **lizpy66 said:**
> thanks :) did this and was able to see but I don't understand what most of it means. It said dev/sda  util fdisk doesn't support GPT. Use GNU Parted. also said some vg root error thing for ubuntu

Your Welcome-

Try what [**[COLOR=#000000]tfrue[/COLOR]**]("http://ubuntuforums.org/member.php?u=1865338") posted for you.
That will help-:D

I didn't realize you needed GPT partitioning- Sorry

[B]parted -l is another command you can use to look at partitions.

```
dev/sda is just the first partition on the first hard disk drive on your system.

```
[/B]Most likely dev/sda1 is your first Windows partition

---

### Post by lizpy66 on 2014-01-18
sorry for the late reply, was busy. I just tried this but got a different layout then what you mentioned. I think there is a new version. I went to detailed partition list and it said Partition number (1-3): , so I typed in 1-3 and it gave something about sectors

sorry, I'm not computer savvy, at least not on ubuntu. Thanks for the help you've given :)

---

### Post by tfrue on 2014-01-18
It's asking which partition do you want to use (1-3), so I would type 1 to see partition 1.

I recommend doing what oldfred posted:
> This will show lots of details of your system.
 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

If you install a Windows 7, you have to have a new license as the  current one is for the vendor version of Windows 8 and is stored in the  UEFI NVRAM. Windows 7 default install also is BIOS, so you have to  convert drive from gpt to MBR(msdos). Windows 7 can be installed in UEFI  mode only from flash drive with some slight modifications.

This will help us, help you!

Chris

---

