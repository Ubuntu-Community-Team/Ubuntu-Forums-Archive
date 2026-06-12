---
title: "How do I get back on my Windows partition?"
date: 2016-04-03
forum: Windows
---

### Post by Bobby_Pendragon on 2016-04-03
I just want my files.

I'll abbreviate all the issues that lead me to this point. Clearly did not know what I was doing and tinkered too much.

- Laptop had issues, I got the blue screen and Windows stopped booting.
- I installed Ubuntu alongside Windows to get something running, since Windows - wouldn't boot.
- Windows randomly starts booting again, and I use it, with Ubuntu... there in the background.
- Much later, another blue screen and Windows isn't booting. I'm stuck with Ubuntu. I want to get back to Windows.
- Here's where big problems settle in: I delete what I think is the Ubuntu partition using "Disks", thinking I'll be left to boot only Windows. Nope. This was a 32GB partition, where I thought only the Ubuntu OS was loaded. Never did I see or have any access to the Windows partition at this stage, it was like it wasn't there.
- Now it takes me to the grub boot-loader, with neither Windows or Ubuntu available. I've been able to somehow get Windows working just by restarting the computer randomly from Ubuntu. So I download Ubuntu again into that 32GB partition I'd previously cleared up. I had no option to boot alongside Windows, but I didn't choose the option to completely clear the hard-drive (I still chose a partition).
- This brings back Ubuntu, but I still have no clue how to boot into Windows. Stupid problem 2: I delete the Ubuntu partitions again.
- Now, I boot into GNU Grub, and can really only exit to the BIOS.

I could try to reinstall Ubuntu, to see if that gets me further along. I've tried to use a Windows recovery drive, but it suggests the drive where Windows is located is locked. OS-Installer (when I tried using it after all this said no OS's where located).

I just want to access whatever part of my drive has Windows and my files on, retrieve them, then put this laptop away. I feel like all my data should be out there, I've only tinkered with a section of the disk.

---

### Post by ajgreeny on 2016-04-03
I am a bit lost regarding your actions so far, and depending on what you actually did, you may unfortunately have deleted your Windows partitions.

However, assuming you can still boot to a live Ubuntu OS from DVD or USB, please do so and open a terminal and run command ```
sudo fdisk -l
``` which will tell us what partitions are on your machine.

Once we know that we can give you some further advice.

---

### Post by Bobby_Pendragon on 2016-04-03
Thanks for your response.

This is what was returned:

> [COLOR=#222222][FONT=arial]Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Sector size (logical/physical): 512 bytes / 4096 bytes[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]I/O size (minimum/optimal): 4096 bytes / 4096 bytes[/FONT][/COLOR]


[COLOR=#222222][FONT=arial]Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Sector size (logical/physical): 512 bytes / 4096 bytes[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]I/O size (minimum/optimal): 4096 bytes / 4096 bytes[/FONT][/COLOR]


[COLOR=#222222][FONT=arial]Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Sector size (logical/physical): 512 bytes / 4096 bytes[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]I/O size (minimum/optimal): 4096 bytes / 4096 bytes[/FONT][/COLOR]


[COLOR=#222222][FONT=arial]Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Sector size (logical/physical): 512 bytes / 4096 bytes[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]I/O size (minimum/optimal): 4096 bytes / 4096 bytes[/FONT][/COLOR]


[COLOR=#222222][FONT=arial]Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Sector size (logical/physical): 512 bytes / 4096 bytes[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]I/O size (minimum/optimal): 4096 bytes / 4096 bytes[/FONT][/COLOR]


[COLOR=#222222][FONT=arial]Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Sector size (logical/physical): 512 bytes / 4096 bytes[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]I/O size (minimum/optimal): 4096 bytes / 4096 bytes[/FONT][/COLOR]


[COLOR=#222222][FONT=arial]Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Sector size (logical/physical): 512 bytes / 4096 bytes[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]I/O size (minimum/optimal): 4096 bytes / 4096 bytes[/FONT][/COLOR]


[COLOR=#222222][FONT=arial]Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Sector size (logical/physical): 512 bytes / 4096 bytes[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]I/O size (minimum/optimal): 4096 bytes / 4096 bytes[/FONT][/COLOR]


[COLOR=#222222][FONT=arial]Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Sector size (logical/physical): 512 bytes / 4096 bytes[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]I/O size (minimum/optimal): 4096 bytes / 4096 bytes[/FONT][/COLOR]


[COLOR=#222222][FONT=arial]Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Sector size (logical/physical): 512 bytes / 4096 bytes[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]I/O size (minimum/optimal): 4096 bytes / 4096 bytes[/FONT][/COLOR]


[COLOR=#222222][FONT=arial]Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Sector size (logical/physical): 512 bytes / 4096 bytes[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]I/O size (minimum/optimal): 4096 bytes / 4096 bytes[/FONT][/COLOR]


[COLOR=#222222][FONT=arial]Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Sector size (logical/physical): 512 bytes / 4096 bytes[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]I/O size (minimum/optimal): 4096 bytes / 4096 bytes[/FONT][/COLOR]


[COLOR=#222222][FONT=arial]Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Sector size (logical/physical): 512 bytes / 4096 bytes[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]I/O size (minimum/optimal): 4096 bytes / 4096 bytes[/FONT][/COLOR]


[COLOR=#222222][FONT=arial]Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Sector size (logical/physical): 512 bytes / 4096 bytes[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]I/O size (minimum/optimal): 4096 bytes / 4096 bytes[/FONT][/COLOR]


[COLOR=#222222][FONT=arial]Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Sector size (logical/physical): 512 bytes / 4096 bytes[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]I/O size (minimum/optimal): 4096 bytes / 4096 bytes[/FONT][/COLOR]


[COLOR=#222222][FONT=arial]Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Sector size (logical/physical): 512 bytes / 4096 bytes[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]I/O size (minimum/optimal): 4096 bytes / 4096 bytes[/FONT][/COLOR]


[COLOR=#222222][FONT=arial]Disk /dev/sda: 29.8 GiB, 32017047552 bytes, 62533296 sectors[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Disklabel type: gpt[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Disk identifier: 54ECC1CC-D72C-4985-8930-[/FONT][/COLOR][COLOR=#222222][FONT=arial]E10B2DA7EDCC[/FONT][/COLOR]

[COLOR=#222222][FONT=arial]Device       Start      End  Sectors  Size Type[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]/dev/sda1     2048  1050623  1048576  512M EFI System[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]/dev/sda2  1050624 62531583 61480960 29.3G Linux filesystem[/FONT][/COLOR]

It's as though the PC has only 32 gb of space (maybe the SSD drive?). I don't know where the 500GB/1TB (can't remember) of HDD space went.

---

### Post by yancek on 2016-04-03
If you originally got the BSOD on windows, your first step should have been to go to a windows forum to try to get help to resolve the windows problem.  This isn't exactly an unusual situation with a windows computer.

Incidentally, it would be very useful if you posted which version of windows you were using.

Your first mistake was to delete the Ubuntu partition.  Your BSOD was the result of problems with your windows bootloader.  Ubuntu and the Grub bootloader do not directly boot windows systems.  They chainload which basically means Grub is told to look for boot files at a specific location on the computer, the windows partition.  Almost all the Grub boot files needed to boot or to point to this location are on the system partition, the one you deleted.

The fdisk command didn't produce anything useful.  How did you get this?  Are you using the Ubuntu installation medium?  If you are, try running:  sudo gparted and see what the output is there.

---

### Post by Bobby_Pendragon on 2016-04-03
I was using Windows 10 (the laptop was installed with Windows 8) and I got the info from the fdisk command from using Ubuntu (which is installed on the computer, all in this seemingly 32GB partition).

I got "libparted : 3.2", then in Gparted all I see is a /dev/sda1 partition with file system fat32 that is 512.00 MiB (flags say "boot,esp") and a /dev/sda2 partition with file system ext4, mount point "/" and a size of 29.32 GiB.

---

