---
title: "MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk"
date: 2010-06-26
forum: Tutorials
---

### Post by sundar_ima on 2010-06-26
The information in this thread have been moved to [https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk](https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk)

A thread for discussion of the wiki page only can be found here [http://ubuntuforums.org/showthread.php?t=2012396](http://ubuntuforums.org/showthread.php?t=2012396)

Thread closed.



**[COLOR="DarkRed"][SIZE="5"][B][CENTER][SIZE="6"]_MultiBootUSB_[/SIZE][/CENTER]**[/SIZE][/COLOR][/B]

[SIZE="3"]Download the latest windows binary/source from**[COLOR="Red"][here]("https://sourceforge.net/projects/multibootusb/files/Windows/")[/COLOR]**[/SIZE]

[SIZE="3"]Download the latest Linux script from **[COLOR="Red"][here]("https://sourceforge.net/projects/multibootusb/files/MultiBootUSB_4.7.tar.gz/download")[/COLOR]**[/SIZE]

[SIZE="4"]Send your feedback at [COLOR="Red"]**feedback.multibootusb@gmail.com**[/COLOR][/SIZE]

[COLOR="DarkRed"]**[SIZE="4"]Note:[/SIZE]**[/COLOR] [COLOR="Red"][SIZE="3"]Though this script will not format your USB drive / Pendrive it is advised to take backup of USB data before invoking the script.[/SIZE][/COLOR]

[COLOR="DarkGreen"][SIZE="4"]**_1. What is MultibootUSB_**[/SIZE][/COLOR]

	[SIZE="3"]MultibootUSB is a shell script written by A Ramesh Kumar and Sundar. Main intention of this program is to install multiple Linux distribution in to single USB disk / Flash drive / Pendrive and able to boot from it with less dependency issue. All you need is your favorite distros in iso format and FAT formatted USB disk. Read the rest to find more.[/SIZE]

[COLOR="DarkGreen"][SIZE="4"]**_2. Main Features_**[/SIZE][/COLOR]

	[SIZE="3"]Automatically detects all inserted USB derive / Pendrive and allow you to choose one.

	Uses GRUB 2 as boot manager

        It can boot hybrid iso images directly (if the distro has the support)

	Ubuntu and Ubuntu based distros like Linux mint can be booted from same pendrive.

	It uses Zenity as GUI and no commands need to be typed in the terminal (except to invoke the program/script)

	As of now this script supports 81+ distros[/SIZE]
	
[COLOR="DarkGreen"][SIZE="4"]**_2. System Requirement_**[/SIZE][/COLOR]

	[SIZE="3"]PC / Laptop which has the option to boot from USB. 

	Any latest Linux distribution with GRUB 2 as boot manager. Recommended OS is  Ubuntu 9.10 and above.

	One or more Linux ISO image(s) of your choice (Only supported by the script)
[/SIZE]
[COLOR="DarkGreen"][SIZE="4"]**_3. License_**[/SIZE][/COLOR]

	[SIZE="3"]You can redistribute this program and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or later. This program is distributed in the hope that it will be useful, but [COLOR="Red"]WITHOUT ANY WARRANTY;without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.[/COLOR] See the GNU General Public License for more details <http://www.gnu.org/licenses/>.[/SIZE]

[COLOR="DarkGreen"][SIZE="4"]**_How to use/run the script_**[/SIZE] ::[/COLOR]

	[SIZE="3"]1.	Download the script from [https://sourceforge.net/projects/multibootusb/files/](https://sourceforge.net/projects/multibootusb/files/)

	2.	Extract it to your home folder (Right click --> Extract here)

	3.	Open terminal and move to the script folder (cd MultiBootUSB)

	4.	Provide root permission (su) and type ./MultiBootUSB.sh and hit enter (for Ubuntu just type sudo ./MultiBootUSB.sh with out issuing su command)

	6.	Here after follow on screen instructions 

        7.      Screenshots can be found in doc folder for reference.[/SIZE] 

**[COLOR="DarkGreen"][SIZE="4"]_List of distributions supported_[/SIZE][/COLOR]**

[B][SIZE="3"][COLOR="Blue"]1.   Archiso Live
2.   Aptisid
3.   Austrumi
4.   AVG Rescue CD  
5.   Backtrack
6.   Bit Defender Rescue CD
7.   Bodhi Linux
8.   CD linux
9.   Chakra Linux
10. Clonezilla Live
11. CrunchBang
12. CTK Arch Live  
13. Debian
14. Deli
15. Doudolinux
16. Dream Linux
17. Dynebolic
18. Elive
19. Fedora*
20. Fuduntu
21. GeexBox
22. Goblinx
23. Gnome 3.0 - Fedora
24. Gnome 3.0 - Open SUSE
25. Gparted Live
26. GRML
27. HBCD
28. Igolaware
29. Imagine OS
30. Jolicloud
31. Kaspersky Rescue CD
32. Knoppix
34. Kubuntu*
35. Linux Mint*
36. Linux Mint - DE
37. Lubuntu
38. Manriva One
39. Me OS
40. Moon OS
41. Nimblex
42. Open SUSE
43. Ophcrack Live CD
44. Panda Rescue CD
45. Pardus
46. PCLinux OS*
47. Pentoo
48. Peppermint OS
49. PinGuy OS
50. Parted Magic
51. Pure OS
52. Puppy*
53. Rescue CD (System Rescue CD)
54. RIP Linux
55. Saline OS
56. Sabayon Linux
57. Scientific Linux
58. Sidux
59. Simply Mepis
60. SLAMPP
61. Slax
62. Slitaz
63. Stress Linux
64. Tiny Core
65. UBCD
66. Ubuntu*
67. Ubuntu Netboot*
68. Ubuntu Rescue
69. Ubuntu Ultimate Edition
70. Unity Linux
71. Vector Linux
72. Windows/NT Password / registery editor
73. Xpud
74. Xubuntu*
75. YLMF
76. Zenwalk
77. Zeven OS
78. Zorin OS
79. Salix Live
80. Free DOS
81. SAM Linux
82. Absolute Linux
83. Apodio
84. Arch Linux 32 Bit
85. Arch Bang
86. DEFT Linux
87. Express Linux
88. LDR
89. Porteus
90. Redo Backup Live CD
91. Tails
92. Mageia Linux
93. Calculate Linux
94. Vidalinux
95. MeeGO
96. Dam Small Linux
97. Elementary OS
98. Netrunner
99. Webconvergence
100.FreeBSD[/COLOR]
[/SIZE][/B]
[COLOR="Magenta"]
[SIZE="4"][SIZE="3"]**Please give your feedback, suggestions, request for new features and comments as reply.**[/SIZE][/SIZE] [/COLOR]

---

### Post by ubunterooster on 2010-06-26
woot! I was looking for a way to do this the day before yesterday and came up empty! I'll try this later! (Busy now)

---

### Post by sundar_ima on 2010-06-26
> **ubunterooster said:**
> woot! I was looking for a way to do this the day before yesterday and came up empty! I'll try this later! (Busy now)

You are welcome to try/test the script. Don't forget to leave your comment after testing...

---

### Post by C.S.Cameron on 2010-06-26
Wow, great to have an automated grub2 multiboot installer.
Does it do Puppy and NimbleX?

---

### Post by ubunterooster on 2010-06-26
The link to the site (for those who want more info): [http://multibootusb.sourceforge.net/](http://multibootusb.sourceforge.net/)

---

### Post by sundar_ima on 2010-06-27
> **C.S.Cameron said:**
> Wow, great to have an automated grub2 multiboot installer.
Does it do Puppy and NimbleX?

Yes. you can find other supported distros in the first post.

---

### Post by C.S.Cameron on 2010-06-27
sudo: ./multibootusb: command not found

---

### Post by howefield on 2010-06-27
> **C.S.Cameron said:**
> sudo: ./multibootusb: command not found

That isn't the command given in the original post.

---

### Post by C.S.Cameron on 2010-06-27
From the readme file:


> How to run the script:-
	1.	Copy the downloaded package to your home folder and extract it (Right click --> Extract here)
	2.	Move in to script folder (cd MultiBootUSB)
	3.	Type su and give your password	(For ubuntu this is not required)
	4.	Finally type ./multibootusb and hit enter (for ubuntu type **sudo ./multibootusb**)
	5.	Here after follow on screen instructions (For screenshot open (in firefox) MultiBootUSB.html from doc folder)


Also tried:

sudo ./MultiBootUSB

---

### Post by howefield on 2010-06-27
Seems to work with the non-Beta version, but not the Beta.

---

### Post by C.S.Cameron on 2010-06-27
I tried:

```
sudo ./MultiBootUSB.sh
```

And it seemed to work.
But when I tried booting it could not find file, (I had been using this flash drive as a grub2 multibooter already).

I deleted the FAT32 and casper-rw partitions and reformatted to FAT32 and tried again.

Now I am getting grub error 15???

MultibootUSB looks promising so I will keep trying.


Edit:
I think the reason I am getting boot error 15 is because nothing is being written to the flash drive.
I've tried four times and after fifteen minutes of writing each time, nothing is there.

---

### Post by sundar_ima on 2010-06-27
> **C.S.Cameron said:**
> I tried:

```
sudo ./MultiBootUSB.sh
```

And it seemed to work.
But when I tried booting it could not find file, (I had been using this flash drive as a grub2 multibooter already).

I deleted the FAT32 and casper-rw partitions and reformatted to FAT32 and tried again.

Now I am getting grub error 15???

MultibootUSB looks promising so I will keep trying.


Edit:
I think the reason I am getting boot error 15 is because nothing is being written to the flash drive.
I've tried four times and after fifteen minutes of writing each time, nothing is there.

Thank you for pointing out the mistake. I will edit my first post accordingly. Which distro are you trying to install?

---

### Post by C.S.Cameron on 2010-06-28
Part of my problem is that I am using my laptop with 10.04 but it is still using grub legacy as I have been upgrading since 8.04.
I am trying to install Ubuntu 10.04, Puppy 5, NimbleX-2008 and Tinycore.

At first it seemed to write to the disk ok but grub 2 was not installed.
Now nothing is installed.
I will try again today booting from a Live USB or CD.

Edit:
I'm impressed, really, really impressed. This seems to be working as stated. Great job! Wow!

Edit:
No luck with NimbleX so far.

---

### Post by ubunterooster on 2010-06-28
Good news: it works well. :D
Bad news: I need more flash drives :(

/me wonders if OP works for SanDisk LOL :confused:

---

### Post by sundar_ima on 2010-06-29
> **C.S.Cameron said:**
> Part of my problem is that I am using my laptop with 10.04 but it is still using grub legacy as I have been upgrading since 8.04.
I am trying to install Ubuntu 10.04, Puppy 5, NimbleX-2008 and Tinycore.

At first it seemed to write to the disk ok but grub 2 was not installed.
Now nothing is installed.
I will try again today booting from a Live USB or CD.

Edit:
I'm impressed, really, really impressed. This seems to be working as stated. Great job! Wow!

Edit:
No luck with NimbleX so far.

Good to know that it works well. Could you post the error message with the (NimbleX) version .

---

### Post by C.S.Cameron on 2010-06-29
NimbleX - 2008

> error: file not found.
error: unknown command 'kdm'.
error: you need to load the kernel first.

Press any key to continue...

I've had lots of problems manually installing NimbleX on flash drive.

---

### Post by C.S.Cameron on 2010-07-01
If I run sudo ./MultiBootUSB.sh in terminal, the terminal gets filled with a few blue and white stripes.
If I stretch the terminal a little bigger before running it, it works ok.

---

### Post by McRat on 2010-07-01
This will be really interesting when the computers and memory sticks support USB3.0.
 
It "should" be fast enough to run like a normal HDD from a few years ago. About 80mbps.
 
No need to install the O/S.

---

### Post by sundar_ima on 2010-07-02
> If I run sudo ./MultiBootUSB.sh in terminal, the terminal gets filled with a few blue and white stripes.
If I stretch the terminal a little bigger before running it, it works ok.

I too have noticed this problem. so if any one trying this script please keep your terminal in maximize mode and try.

---

### Post by confused57 on 2010-07-03
I thought I'd attempt the MultiBootUSB script, which seemed to work quite well.  I downloaded iso's of:
Clonezilla, BackTrack, Parted Magic, Knoppix Live, Lucid-Puppy, System Rescue, Slitaz, Tiny-Core, Ubuntu Rescue, Wolvix, Zenwalk Live, PC Linux OS, Peppermint Linux, and Lubuntu.

Then I ran the script(with terminal maximized), which automatically formatted the USB drive, installed grub2, and it successfully added boot entries for all of the above iso's, except Peppermint & Lubuntu.  I manually added Peppermint to the iso folder and added an entry to the /boot/grub/grub.cfg.
Peppermint booted fine, however the default language was Spanish(I think).

I'm in the process of attempting to boot each of the iso's and so far Wolvix and Backtrack have booted OK.  Knoppix will only boot into Failsafe to a root prompt, I may make a bootable cd to determine if the failure is due to my system.

Thank you for the script, makes it much easier to set up a multi-boot USB, as well as demonstrating how iso's are booted from grub2.  I noticed that for several of the live cd iso's, the contents were extracted, and others were added to the iso folder and booted directly from boot.cfg.

---

### Post by sundar_ima on 2010-07-04
Thank you for your positive feedback.

> it successfully added boot entries for all of the above iso's, except Peppermint & Lubuntu.

Yes it wont boot pepper mint and lubuntu because this support is not added in the script. you can find the list of supported distros in the first post of this thread.  

> I manually added Peppermint to the iso folder and added an entry to the /boot/grub/grub.cfg.

if you boot these distros (pepper mint and lubuntu) successfully please share us so that i will include these two distros in the script. you can share us the grub.cfg entry of these two distros.

> 
I'm in the process of attempting to boot each of the iso's and so far Wolvix and Backtrack have booted OK

I haven't tried yet for those distros. I would like to know the grub.cfg entry for these two(if you wish).

> I noticed that for several of the live cd iso's, the contents were extracted

Because these distros does not provide direst iso boot yet.

Thank you.

---

### Post by confused57 on 2010-07-04
Here is my grub.cfg:
```
set default="1"
set timeout=30
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue

menuentry "First Partition of First HDD" {
set root=(hd0,1)
chainloader +1
}

GRUB_GFXMODE=1024x768x16
insmod vbe


	menuentry "Back Track - FrameBuffer (1024x768)" {
		linux /boot/bt/vmlinuz BOOT=casper boot=casper nopersistent rw vga=0x317
		initrd /boot/bt/initrd.gz
	}

	menuentry "Back Track - FrameBuffer (800x600)" {
		linux /boot/bt/vmlinuz BOOT=casper boot=casper nopersistent rw vga=0x314
		initrd /boot/bt/initrd800.gz
	}

	menuentry "Back Track Forensics (no swap)" {
		linux /boot/bt/vmlinuz BOOT=casper boot=casper nopersistent rw vga=0x317
		initrd /boot/bt/initrdfr.gz
	}

	menuentry "Back Track - Safe Graphical Mode" {
		linux /boot/bt/vmlinuz BOOT=casper boot=casper xforcevesa rw
		initrd /boot/bt/initrd.gz
	}

	menuentry "Back Track - Persistent" {
		linux /boot/bt/vmlinuz BOOT=casper boot=casper persistent rw
		initrd /boot/bt/initrd.gz
	}

	menuentry "Back Track - Text Mode" {
		linux /boot/bt/vmlinuz BOOT=casper boot=casper nopersistent textonly rw
		initrd /boot/bt/initrd.gz
	}

	menuentry "Back Track - From RAM" {
		linux /boot/bt/vmlinuz BOOT=casper boot=casper toram nopersistent rw
		initrd /boot/bt/initrd.gz
	}



	menuentry "CD Linux" {
		linux /boot/cdlinux/bzImage quiet
		initrd /boot/cdlinux/initrd
	}


	menuentry "Clonezilla" {
		loopback loop /boot/iso/clonezilla-live-1.2.5-17-i486.iso
		linux (loop)/live/vmlinuz root=(loop)/ rootfstype=loop findiso=/boot/iso/clonezilla-live-1.2.5-17-i486.iso quickreboot utc=no    boot=live union=aufs noswap nolocales edd=on ocs_live_run="ocs-live-general" ocs_live_extra_param="" ocs_live_keymap="NONE" ocs_live_batch="no" ocs_lang="en_US.UTF-8" ocs_daemonon="ssh" ocs_numlk=on ip=frommedia nosplash
		initrd (loop)/live/initrd.img
	}

	menuentry "Clonezilla - To RAM" {
		loopback loop /boot/iso/clonezilla-live-1.2.5-17-i486.iso
		linux (loop)/live/vmlinuz root=(loop)/ rootfstype=loop findiso=/boot/iso/clonezilla-live-1.2.5-17-i486.iso quickreboot utc=no toram=filesystem.squashfs   boot=live union=aufs noswap nolocales edd=on ocs_live_run="ocs-live-general" ocs_live_extra_param="" ocs_live_keymap="NONE" ocs_live_batch="no" ocs_lang="en_US.UTF-8" ocs_daemonon="ssh" ocs_numlk=on ip=frommedia nosplash
		initrd (loop)/live/initrd.img
	}


	menuentry "Knoppix" {
		gfxpayload=1024x768
		linux /KNOPPIX6/linux ramdisk_size=100000 lang=en vt.default_utf8=0 apm=power-off vga=791 initrd=minirt.gz nomce loglevel=0 tz=localtime knoppix_dir=KNOPPIX6 BOOT_IMAGE=knoppix
		initrd /KNOPPIX6/minirt.gz
	}

	menuentry "Knoppix-Adriane" {
		gfxpayload=1024x768
		linux /KNOPPIX6/linux ramdisk_size=100000 lang=en vt.default_utf8=0 apm=power-off initrd=minirt.gz nomce loglevel=0 tz=localtime knoppix_dir=KNOPPIX adriane
		initrd /KNOPPIX6/minirt.gz
	}

	menuentry "Knoppix-Failsafe" {
		linux /KNOPPIX6/linux ramdisk_size=100000 lang=en vt.default_utf8=0 vga=normal atapicd nosound noapic nolapic noacpi pnpbios=off acpi=off nofstab noscsi nodma noapm nousb nopcmcia nofirewire noagp nomce nonetwork nodhcp xmodule=vesa initrd=minirt.gz knoppix_dir=KNOPPIX6
		initrd /KNOPPIX6/minirt.gz
	}


	menuentry "Lucid Puppy" {
		linux /boot/lupu/vmlinuz root=/dev/ram0 pmedia=usbflash loglevel=7 pkeys=us
		initrd /boot/lupu/initrd.gz
	}


	menuentry "Ubuntu" {
		loopback loop /boot/iso/ubuntu-rescue-remix-10-04.iso
		linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/iso/ubuntu-rescue-remix-10-04.iso noeject noprompt --
		initrd (loop)/casper/initrd.lz
	}


	menuentry "Parted Magic" {
		loopback loop /boot/iso/pmagic-4.11.iso
		linux (loop)/pmagic/bzImage edd=off noapic load_ramdisk=1 prompt_ramdisk=0 rw loglevel=0 max_loop=256 keymap=us iso_filename=/boot/iso/pmagic-4.11.iso
		initrd (loop)/pmagic/initramfs
	}

	menuentry "Parted Magic - Media not usable" {
		loopback loop /boot/iso/pmagic-4.11.iso
		linux (loop)/pmagic/bzImage edd=off noapic load_ramdisk=1 prompt_ramdisk=0 rw loglevel=0 livemedia noeject max_loop=256 keymap=us iso_filename=/boot/iso/pmagic-4.11.iso
		initrd (loop)/pmagic/initramfs
	}

	menuentry "Parted Magic - Low RAM" {
		loopback loop /boot/iso/pmagic-4.11.iso
		linux (loop)/pmagic/bzImage edd=off noapic load_ramdisk=1 prompt_ramdisk=0 rw lowram livemedia noeject nogpm nolvm nonfs nofstabdaemon nosmart noacpid nodmeventd nohal nosshd nosound nobluetooth loglevel=0 xvesa max_loop=256 keymap=us iso_filename=/boot/iso/pmagic-4.11.iso
		initrd (loop)/pmagic/initramfs
	}

	menuentry "Parted Magic - VESA Graphics" {
		loopback loop /boot/iso/pmagic-4.11.iso
		linux (loop)/pmagic/bzImage edd=off noapic load_ramdisk=1 prompt_ramdisk=0 rw xvesa loglevel=0 max_loop=256 keymap=us iso_filename=/boot/iso/pmagic-4.11.iso
		initrd (loop)/pmagic/initramfs
	}

	menuentry "Parted Magic - Safe Graphics" {
		loopback loop /boot/iso/pmagic-4.11.iso
		linux (loop)/pmagic/bzImage edd=off noapic load_ramdisk=1 prompt_ramdisk=0 rw vga=normal loglevel=0 max_loop=256 keymap=us iso_filename=/boot/iso/pmagic-4.11.iso
		initrd (loop)/pmagic/initramfs
	}

	menuentry "Parted Magic - Failsafe" {
		loopback loop /boot/iso/pmagic-4.11.iso
		linux (loop)/pmagic/bzImage edd=off acpi=off noapic load_ramdisk=1 prompt_ramdisk=0 rw vga=normal nolapic nopcmcia noscsi nogpm consoleboot nosmart keymap=us nosshd nosound max_loop=256 iso_filename=/boot/iso/pmagic-4.11.iso
		initrd (loop)/pmagic/initramfs
	}


	menuentry "PC Linux" {
		linux /boot/pclinux/vmlinuz livecd=livecd initrd=initrd.gz root=/dev/rd/3 acpi=on vga=788 keyb=us fstab=rw,auto
		initrd /boot/pclinux/initrd.gz
	}

	menuentry "PC Linux - From RAM" {
		linux /boot/pclinux/vmlinuz copy2ram livecd=livecd initrd=initrd.gz root=/dev/rd/3 acpi=on vga=788 keyb=us fstab=rw,auto
		initrd /boot/pclinux/initrd.gz
	}

	menuentry "PC Linux - Safe Boot" {
		linux /boot/pclinux/vmlinuz livecd=livecd root=/dev/rd/3 acpi=off vga=normal keyb=us noapic nolapic noscsi nopcmcia
		initrd /boot/pclinux/initrd.gz
	}


	menuentry "Slitaz" {
		loopback loop /boot/iso/slitaz-3.0.iso
		linux (loop)/boot/bzImage rw root=/dev/null lang=C kmap=us screen=1024x768x16 autologin
		initrd (loop)/boot/rootfs.gz
	}


	menuentry "System Rescue" {
		loopback loop /boot/iso/systemrescuecd-x86-1.5.6.iso
		linux (loop)/isolinux/rescuecd isoloop=/boot/iso/systemrescuecd-x86-1.5.6.iso rdinit=/linuxrc setkmap=us
		initrd (loop)/isolinux/initram.igz
	}

	menuentry "System Rescue - With GUI" {
		loopback loop /boot/iso/systemrescuecd-x86-1.5.6.iso
		linux (loop)/isolinux/rescuecd isoloop=/boot/iso/systemrescuecd-x86-1.5.6.iso rdinit=/linuxrc setkmap=us dostartx
		initrd (loop)/isolinux/initram.igz
	}

	menuentry "System Rescue - Files to Memory" {
		loopback loop /boot/iso/systemrescuecd-x86-1.5.6.iso
		linux (loop)/isolinux/rescuecd isoloop=/boot/iso/systemrescuecd-x86-1.5.6.iso rdinit=/linuxrc setkmap=us docache
		initrd (loop)/isolinux/initram.igz
	}

	menuentry "System Rescue - AMD 64 bit" {
		loopback loop /boot/iso/systemrescuecd-x86-1.5.6.iso
		linux (loop)/isolinux/rescue64 isoloop=/boot/iso/systemrescuecd-x86-1.5.6.iso rdinit=/linuxrc setkmap=us
		initrd (loop)/isolinux/initram.igz
	}

	menuentry "System Rescue - Alternate 32 bit" {
		loopback loop /boot/iso/systemrescuecd-x86-1.5.6.iso
		linux (loop)/isolinux/altker32 isoloop=/boot/iso/systemrescuecd-x86-1.5.6.iso rdinit=/linuxrc setkmap=us
		initrd (loop)/isolinux/initram.igz
	}

	menuentry "System Rescue - Alternate 64 bit" {
		loopback loop /boot/iso/systemrescuecd-x86-1.5.6.iso
		linux (loop)/isolinux/altker64 isoloop=/boot/iso/systemrescuecd-x86-1.5.6.iso rdinit=/linuxrc setkmap=us
		initrd (loop)/isolinux/initram.igz
	}

	menuentry "System Rescue - Memory Test" {
		loopback loop /boot/iso/systemrescuecd-x86-1.5.6.iso
		linux (loop)/bootdisk/memtestp isoloop=/boot/iso/systemrescuecd-x86-1.5.6.iso rdinit=/linuxrc setkmap=us
		initrd (loop)/bootdisk/memtestp
	}

	menuentry "System Rescue - FreeDOS" {
		loopback loop /boot/iso/systemrescuecd-x86-1.5.6.iso
		linux (loop)/isolinux/memdisk isoloop=/boot/iso/systemrescuecd-x86-1.5.6.iso rdinit=/linuxrc setkmap=us
		initrd (loop)/bootdisk/freedos.img
	}



	menuentry "Tiny Core" {
		loopback loop /boot/iso/tinycore_2.11.5.iso
		linux (loop)/boot/bzImage 
		initrd (loop)/boot/tinycore.gz
	}


	menuentry "Ubuntu Rescue" {
		loopback loop /boot/iso/ubuntu-rescue-remix-10-04.iso
		linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/iso/ubuntu-rescue-remix-10-04.iso noeject noprompt --
		initrd (loop)/casper/initrd.lz
	}


	menuentry "Wolvix GNU/Linux (login as root, password is toor)" {
		linux /boot/wolvix/vmlinuz changes=wolvixsave.xfs max_loop=255 ramdisk_size=6666 root=/dev/ram0 rw vga=791 splash=silent
		initrd /boot/wolvix/initrd.gz
	}

	menuentry "Zenwalk live" {
		linux /boot/zen/vmlinuz append max_loop=255 initrd=/boot/zen/initrd.gz init=linuxrc load_ramdisk=1 prompt_ramdisk=0 ramdisk_size=6666 root=/dev/ram0 rw vga=791 splash=silent keyb=us lang=en_US autologin
		initrd /boot/zen/initrd.gz
	}

	menuentry "Zenwalk live (Safe Graphics)" {
		linux /boot/zen/vmlinuz append max_loop=255 initrd=/boot/zen/initrd.gz init=linuxrc load_ramdisk=1 prompt_ramdisk=0 ramdisk_size=6666 root=/dev/ram0 rw vga=791 splash=silent xforcevesa keyb=us lang=en_US autologin
		initrd /boot/zen/initrd.gz
	}


        menuentry "Peppermint-One-06172010" {
loopback loop /boot/iso/Peppermint-One-06172010.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/iso/Peppermint-One-06172010.iso noprompt noeject quiet splash
initrd (loop)/casper/initrd.lz
       }

       menuentry "Lubuntu 10.04" {
loopback loop /boot/iso/lubuntu-10.04.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/iso/lubuntu-10.04.iso noprompt noeject quiet splash
initrd (loop)/casper/initrd.lz
       }
```

I was able to boot Knoppix using the first menuentry and had no problems booting lubuntu and Peppermint, which are both Ubuntu based.  I used Herman's example on his site:
[http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html#Loopback_Boot_Entry](http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html#Loopback_Boot_Entry)

I'll try to update this post with results on booting the other distro iso's.  I'm quite impressed with the results so far.

---

### Post by C.S.Cameron on 2010-07-04
Gparted works well from iso with grub2.
You can probably make the following menuentry look a bit more elegant:

```
menuentry "Gparted live" {
  insmod loopback
  insmod iso9660
  set gfxpayload=800x600x16, 800x600
  set isofile="/boot/ISOs/gparted-live-0.5.2-1.iso"
  loopback loop $isofile
  linux (loop)/live/vmlinuz boot=live union=aufs noswap noprompt ip=frommedia toram=filesystem.squashfs findiso=$isofile
  initrd (loop)/live/initrd.img
}
```

---

### Post by sundar_ima on 2010-07-07
Released beta 2.0 version. Included distros are 
Macpup (along with Lucid puppy)
AVG Rescue CD
GParted
Peppermint
Lubuntu
Fedora 
however fedora is not working at the moment.

---

### Post by sundar_ima on 2010-07-10
Oops...

Forgot to mention about the bug fix (nimblex) on beta 2 release. 

Thank you **C.S.Cameron** for your feedback and suggestion ( on GParted).
Thank you **confused57** for your suggestion on pepperment and lubuntu

We are ready to  release the new version with few more additional distros and some bug fixes :-)

---

### Post by C.S.Cameron on 2010-07-10
Thanks sundar_ima:
Will give it a try.
Great job so far.
Cork

---

### Post by MountainX on 2010-07-10
I get this error in Kubuntu 10.04

# ./MultiBootUSB.sh                                                                                                                                                                             
USB Disk [./MultiBootUSB.sh:] is not available    

                              
However, my USB disk is available. It is called "PATRIOT" and here it is:

ls /media/PATRIOT/
autorun.inf  casper  ldlinux.sys  md5sum.txt  mint4win.exe  preseed  syslinux

(Those files are all OK to delete, so I just plan on overwriting this disk.)

Why won't the script run?

---

### Post by C.S.Cameron on 2010-07-10
> **MountainX said:**
> I get this error in Kubuntu 10.04

# ./MultiBootUSB.sh                                                                                                                                                                             
USB Disk [./MultiBootUSB.sh:] is not available    

                              
However, my USB disk is available. It is called "PATRIOT" and here it is:

ls /media/PATRIOT/
autorun.inf  casper  ldlinux.sys  md5sum.txt  mint4win.exe  preseed  syslinux

(Those files are all OK to delete, so I just plan on overwriting this disk.)

Why won't the script run?


Are you giving the full path to ./MultiBootUSB.sh

---

### Post by MountainX on 2010-07-10
> **C.S.Cameron said:**
> Are you giving the full path to ./MultiBootUSB.sh

**No.** Why would I need to do more than this:
sudo -s
cd ~/Downloads/MultiBootUSB
~/Downloads/MultiBootUSB# ./MultiBootUSB.sh

---

### Post by C.S.Cameron on 2010-07-10
> No. Why would I need to do more than this:
sudo -s
cd ~/Downloads/MultiBootUSB
~/Downloads/MultiBootUSB# ./MultiBootUSB.sh

Just askin' 
Because I am installing from a laptop with grub legacy I am booting from the Live CD.
My MultiBootUSB.sh is on a flash drive so I give the path and it works.
I start with a freshly formatted FAT32 flash drive

---

### Post by MountainX on 2010-07-10
I've got a bug report:
if the path to the iso images contains a directory containing the string systemrescue, the script doesn't work properly.

Also, the GUI doesn't seem to work on kubuntu...

---

### Post by C.S.Cameron on 2010-07-10
The new gparted works for me.

NimbleX 2008 looks like it is about to work then stops at:
"Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(1,0)

When I select "First partition... " when booting I get "This is not a bootable disk. Please insert a bootable floppy and press any key to try again ..."

I've tried editing to "set root=(hd0,2), (hd=0,3), but does not help.

I will try the drive on another computer.

---

### Post by MountainX on 2010-07-10
This script is totally screwed up. Don't use it. I'm finding a ton of errors.

For example, most distros are missing the mount and mkdir commands at the point where the grub menu entries are written.

Another example that just totally screwed up: 
```

if (grep "Xubuntu" ${TEMPDIST} ) ; then

	cp ${ISO_XUBUNTU} ${USB_MOUNT}/boot/iso/

	ISO=`basename ${ISO_MINT}`

	cat <<EOF>> ${USB_MOUNT}/boot/grub/grub.cfg

	menuentry "Mint" {
		loopback loop /boot/iso/${ISO}
		linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/iso/${ISO} noeject noprompt --
		initrd (loop)/casper/initrd.lz
	}

EOF

	umount ${LIVE_MOUNT}


fi

```

way too many errors in this script

---

### Post by confused57 on 2010-07-11
> **sundar_ima said:**
> Released beta 2.0 version. Included distros are 
Macpup (along with Lucid puppy)
AVG Rescue CD
GParted
Peppermint
Lubuntu
Fedora 
however fedora is not working at the moment.
Thanks for all the work you've done on the MultiBootUSB script, I'm currently using the beta 2.0 and am in the process of trying to boot the various distro iso's I've mentioned previously.  Lucid-Puppy and the newest Gparted live cd have booted without any problems.

I realize your script is still in beta, however it has been able to accomplish what I wanted in a multi-boot usb, good job.  If it didn't work, I'd probably still be trying to manually set one up, after extensive Google and forum searches, etc.

---

### Post by C.S.Cameron on 2010-07-11
> This script is totally screwed up. Don't use it. I'm finding a ton of errors.

Most of what I have tried works for me so I will gladly use it.

> I realize your script is still in beta, however it has been able to accomplish what I wanted in a multi-boot usb, good job. If it didn't work, I'd probably still be trying to manually set one up, after extensive Google and forum searches, etc. 

I agree 100%

---

### Post by MountainX on 2010-07-11
It is worthwhile to be able to read the code in the scripts. This one has a number of obvious errors. But if you guys want to blindly use it, go ahead. You'll end up with an Xubuntu iso labeled with a menu entry of Mint along with numerous other problems (too many to count last night).

---

### Post by sundar_ima on 2010-07-11
> if the path to the iso images contains a directory containing the string systemrescue, the script doesn't work properly.
What is the error are you getting? If possible could you upload the screenshot? Generally if you use space and special characters between two words in the iso directory (including sub directories) script will not run properly. 
> Also, the GUI doesn't seem to work on kubuntu... 
Really strange to me because original script was written and tested in kubuntu. Again tested in PCLinuxOS (for GUI part only). Also i request you to explain more on the error.
> I'm finding a ton of errors.
What are those errors exactly?
> most distros are missing the mount and mkdir commands 
Not all distros are required to mount. mount and mkdir command is not required if the distro has the option to boot directly from iso. All you need is just an iso file to /boot/iso directory.
Yes i do agree that there are some mistakes and errors in the script but remember that this is still in beta version. 
and finally
> Don't use it.
Thank you for downloading and using the script. I really appreciate you for reporting those bugs and pointing out mistakes.

---

### Post by MountainX on 2010-07-11
> **sundar_ima said:**
> What is the error are you getting? If possible could you upload the screenshot? 

Thank you for downloading and using the script. I really appreciate you for reporting those bugs and pointing out mistakes.

First, the GUI never comes up for me so there is nothing to take a screen shot of. I just get a bunch of potentially dangerous and partially formed commands sent to the command line. When a script like this fails, it should not fail in a way that can cause damage to existing data. So that's a big problem with this script IMO.

Second, when looking at the code, I saw the Xubuntu/Mint mistake I already posted. 

I also tested a number of statements by pasting them individually into the command line (a slow and painful way of debugging I must say). A number of them would not execute for reasons I don't know. Sorry I cannot be of more help.

---

### Post by MountainX on 2010-07-11
another problem I already mentioned is that if the path to the iso files contains systemrescue anywhere in it, the script will copy the wrong iso. 

actually, if the paths have any of the strings the script expects in the filename of an iso file, things will go wrong.

again, that's just one example.

---

### Post by confused57 on 2010-07-11
> **MountainX said:**
> another problem I already mentioned is that if the path to the iso files contains systemrescue anywhere in it, the script will copy the wrong iso. 

actually, if the paths have any of the strings the script expects in the filename of an iso file, things will go wrong.

again, that's just one example.

I've been using Ubuntu and Linux long enough to realize running any script could be "dangerous"; therefore I ran it on a computer that I just built, just to check it out and it worked to my satisfaction.

When I initially ran the script, it wouldn't work because I had all the downloaded iso's in a directory named "isos"(creative, I know).  Once I moved all of them to the root of the partition, the script ran fine, and as mentioned, the terminal window must be full-screen.

---

### Post by C.S.Cameron on 2010-07-11
PERSISTENCE

Will MultiBootUSB be getting a persistence option?

When booting Lucid Puppy I found there was no way to make a save file.
I took a fresh lupusave.2fs from another Puppy installation and dropped it in the MultiBootUSB lupu folder. Now persistence works ok with Puppy.

Ubuntu, I knew that making an ext2 casper-rw partition and then editing the menuentry to:
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/iso/ubuntu-10.04-desktop-i386.iso noeject noprompt -- **persistent**
would give persistence.

So I took a fresh casper-rw file from an usb-creator install and dropped it into the USB root and found that also works for giving persistence.
Renaming a casper-rw file to home-rw and also dropping that into the USB root gives a separate persistent home.

Today I intend to try this persistence option with Xubuntu, Kubuntu and Mint.
I am wondering how much things will screw up If they all try using the same persistence files at the same time.

Edit:
Have tried Ubuntu and Mint with shared persistence files. Things get a little strange but mostly seem to work. The two O/S sort of start to blend together.
Probably not a good option for multiple O/S on a MultiBootUSB disk to share persistence.
Tried Kubuntu, did not want to work with the Ubuntu/Mint casper-rw file, works ok with it's own.
Xubuntu works with casper-rw but does not seem compatable with Ubuntu or Kubuntu persistence wise.

---

### Post by C.S.Cameron on 2010-07-12
As previously mentioned there are problems with the Xubuntu installer.
Heading says Mint and the xubuntu iso is not listed after iso below.

Works fine if the menuentry is fixed manually.

Tried openSUSE-11.2-KDE4-LiveCD-i686-iso and openSUSE-11.2-GNOME-LiveCD-i686-iso.
These did not work for me, am I using the correct Suse iso?

---

### Post by AceRoom on 2010-07-13
Is this the same program as found on:
[http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/](http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/)

However, that only runs on Windows. Anyway, is there any chance of getting it to work with Fedora as well?

One more thing to add:
As on the webpage, it said Linux Mint support extends only to GNOME i386 (CD to be specific). I've managed to get it working with Linux Mint x86_64 DVD (Which includes a couple of extra codecs and Java) with just a change in the file name so I suppose it can be added to the menu.lst quite easily.

---

### Post by AceRoom on 2010-07-13
One more thing as well. The current puppy linux does not work, even with a simple change in filename. Not sure what the issue is.

---

### Post by C.S.Cameron on 2010-07-13
> One more thing as well. The current puppy linux does not work, even with a simple change in filename. Not sure what the issue is. 
The Puppy iso lupu-500.iso worked fine for me except persistence needed some hacking to get working.

---

### Post by sundar_ima on 2010-07-13
Beta 3.o released. Added and Dropped some distros. List of supported distros can be found in the first post. Xubuntu - Mint problem is solved along with some more bugs...

---

### Post by sundar_ima on 2010-07-13
> Is this the same program as found on:
[http://www.pendrivelinux.com/boot-mu...multiboot-usb/](http://www.pendrivelinux.com/boot-mu...multiboot-usb/)

No.
> The current puppy linux does not work, even with a simple change in filename. Not sure what the issue is. 
What is the name you have changed? 
> is there any chance of getting it to work with Fedora as well?
Use the latest script (beta 3.0).

---

### Post by confused57 on 2010-07-13
> Beta 3.o released. Added and Dropped some distros. List of supported distros can be found in the first post. Xubuntu - Mint problem is solved along with some more bugs...
Thanks, I had the same Xubuntu problem as C.S. Cameron, using Beta 2.0.  I'll have to see which distros have been added or dropped in your first post, thanks again.  PCLinuxOS worked fine, but it stopped at shutdown with "no more processes in this init"(or something to that effect).

> The Puppy iso lupu-500.iso worked fine for me except persistence needed some hacking to get working.
I used lupu-501.iso and didn't have to perform any hacks to get persistence working.  When I shutdown Puppy, it asked if I wanted to save the session in the lupu folder on sdb1...I just needed to select the size of the persistence file.

---

### Post by C.S.Cameron on 2010-07-13
I can confirm Xubuntu is now working well. 

Still having same problem with NimbleX.

After spending considerable time downloading every OpenSuse distro I could find I see it has been dropped.

Puppy persistence is now working for me, (out of the box).

---

### Post by sundar_ima on 2010-07-15
> Still having same problem with NimbleX.

Append the initrd line as mentioned below...
```
initrd /boot/nimblex/initrd-nx08.gz
```

---

### Post by C.S.Cameron on 2010-07-15
> **sundar_ima said:**
> Append the initrd line as mentioned below...
```
initrd /boot/nimblex/initrd-nx08.gz
```

Excellent, I removed the extra ".gz" and NimbleX starts right up. (You make it look easy).

Now how about persistence?



Edit:
I'm not having much luck with NimbleX persistence, it's creating the nimblex.data file ok but does not seem to remember to boot into persistence mode. Puppy does it better. Probably need something in the menuentry to boot persistent.

---

### Post by C.S.Cameron on 2010-07-16
I revised the NimbleX menuentry as follows and now persistence works ok:


    menuentry "Nimblex Linux Persistent" {
        linux /boot/nimblex/vmlinuz-nx08 max_loop=255 init=linuxrc load_ramdisk=1 prompt_ramdisk=0 ramdisk_size=7120 root=/dev/ram0 rw vga=791 **changes=nimblex.data autoexec=xconf;kdm**
        initrd /boot/nimblex/initrd-nx08.gz
    }

---

### Post by Stan_1936 on 2010-07-16
When you run Ubuntu off a usb drive (USB 2.0) how fast is it?

I don't mean how fast is it to boot.   I mean, assume that it has fully booted.  Then you click on Open Office to open a Word document.  How fast is it in comparison to a regular hard drive install?

---

### Post by C.S.Cameron on 2010-07-16
Depends what distro you are running. Some, (Puppy, NimbleX) run totally in ram. The boot media doesn't matter.
Also flash drives come in different read and write speeds. 
Ubuntu is noticeably slower on a cheap USB 2 flash drive than a SATA drive with some applications, like Firefox.
USB 3 flash drives should be great for portable operating systems.

---

### Post by C.S.Cameron on 2010-07-22
MultiBootUSB works with the Fedora iso but I have not found a way to make the Overlay file work to provide persistence.
I would think this is just a matter of adding the right thing to the menuentry.

---

### Post by Danimoth on 2010-07-22
I am trying to run the script to burn "all" ubuntu versions on a single flash drive. By versions i mean:
- Ubuntu Desktop i386
- Ubuntu Desktop amd64
- Ubuntu Server i386
- Ubuntu Server amd64

However, when starting the script like so:
```

mark@mark-desktop:~/MultiBootUSB$ sudo ./MultiBootUSB.sh

```i get the following error message
```

USB Disk [/home/mark/MultiBootUSB/tools/whiptail/whiptail:] is not available

```I checked and the file is there. Tried redownloading just in case, still got the same error.
Also tried entering the full path in the command but the same error appears. 

:/

---

### Post by confused57 on 2010-07-22
Did you have the terminal window maximized before running the script?  I couldn't get it to run correctly, unless the window was maximized.

---

### Post by Danimoth on 2010-07-23
Tried it with maximized window, but same result.

---

### Post by C.S.Cameron on 2010-07-23
I have the MultiBootUSB script on a thumb drive so I open the thumbdrive in Nautilus and right click MultiBootUSB.sh and select Copy.
Then I open terminal and stretch the window a bit larger.
I right click in terminal and select paste.
Then I replace "file://" with "sudo".
This seems to eliminate all my typing errors.

---

### Post by Danimoth on 2010-07-23
**Bug #1:**
I am using 64-bit ubuntu and i had to download a new whiptail executable. I actually downloaded this: 
[http://archive.ubuntu.com/ubuntu/pool/main/n/newt/whiptail_0.52.10-5ubuntu1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/newt/whiptail_0.52.10-5ubuntu1_amd64.deb)

extracted and got the whiptail binary and replaced the one included in the zip.
After that it worked. 


**Bug #2:**
I proceeded to create the MultiBoot. However, it seems to me that entries with the same name are not included when you choose ISO's, so instead of getting both

- Ubuntu Desktop i386
- Ubuntu Desktop amd64

I only get one "Ubuntu" entry.
The "Ubuntu" entry corresponds to amd64. I assume the script scans the directory and finds Desktop i386, but the entry is overwritten when the amd64 ISO is found so i never get to see it. 


**Enhancement #1:**
Support for Ubuntu-Server

---

### Post by Mister.Vash on 2010-07-24
I can confirm what Danimoth said.  I'm also running the 64 Bit ubuntu and needed to replace the whiptail binary

I also have both the 32 bit and 64 bit distro iso files downloaded to the same folder and only see the selection choice for the 64 bit image when both are downloaded

---

### Post by moore.bryan on 2010-08-10
Interesting... it doesn't see any of my ISO's...

---

### Post by confused57 on 2010-08-10
> **moore.bryan said:**
> Interesting... it doesn't see any of my ISO's...
I had to move all of the iso's to the root of the partition they were located in, as I mentioned in post #40, as well as running the terminal maximized.  Might be worth a try.

---

### Post by narendraD on 2010-08-11
Very Good script fulfilling a much discussed need by a lot of people. My Hearty thanks Sundar and Ramesh.

I tried this with Slitaz, Tinycore, Austrumi and PartedMagic. All Except Austrumi booted fine. I am using the latest Austrumi 2.1.6. The ISO was not even extracted and there were error messages to that effect when the script was run. Don't know why. Naturally it did not boot. 

Any pointers on what needs to be done and if this is a problem only with this version of Austrumi and how to fix this. I am yet to try out with Puppy or Sysresc or SLAX which i like to use.

---

### Post by moore.bryan on 2010-08-11
> **confused57 said:**
> I had to move all of the iso's to the root of the partition they were located in, as I mentioned in post #40, as well as running the terminal maximized.  Might be worth a try.
Thanks for the tip... I missed that in your earlier post. No love here, though. I ended-up just installing GRUB2 to the flash drive, copying-over the ISO's, and setting my grub.cfg to loop-mount the ISO's.

---

### Post by WiReIs on 2010-09-04
Im having trouble with the terminal when entering in the command given.. 

> sudo ./MultiBootUSB.sh

i get the following error..

> USB Disk [./MultiBootUSB.sh:] is not available

i have a 16gb Verbatim micro 

can anyone help me??

---

### Post by C.S.Cameron on 2010-09-04
> **WiReIs said:**
> Im having trouble with the terminal when entering in the command given.. 



i get the following error..



i have a 16gb Verbatim micro 

can anyone help me??

Make sure you show the path to MultiBootUSB.sh.
I locate MultiBootUSB.sh in nautilus, right click it then paste in terminal, then eliminate the file/ stuff to save having to type the path and eliminate typos.

---

### Post by sundar_ima on 2010-09-08
> **WiReIs said:**
> Im having trouble with the terminal when entering in the command given.. 



i get the following error..



i have a 16gb Verbatim micro 

can anyone help me??

The script will not detect removable media (pendrive) if the label (name of the media) has  space in between words. Therefore pls check out your pendrive label and change it accordingly. Finally reply back if you could successfully use the script.

---

### Post by bluefrog on 2010-09-16
hello.

Taking ubuntu for example can we get to the "main" title as if we would boot from the cdrom to be able to use the Fx keys (or choose the menu we want) or the only is to pass some arguments in grub.cfg?

In fact, I'd like to have the ubuntu DVD if possible and then be able to choose the install.
or the ubuntu alternate edition.

So far, with the DVD I have the following error
 cannot read the linux header
 you need to load the kernel first

the USB drive is formated with ext4 so that I can put a DVD on it.

grub.cfg
menuentry "Ubuntu dvd 10.04" {
        loopback loop /boot/iso/ubuntu-10.04-dvd-i386.iso
        linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/iso/ubuntu-10.04-dvd-i386.iso noeject noprompt --
        initrd (loop)/casper/initrd.lz
}

while everything alright with

menuentry "ubuntu netbook 10.10" {
        loopback loop /boot/iso/ubuntu-10.10-beta-netbook-i386.iso
        linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/iso/ubuntu-10.10-beta-netbook-i386.iso noeject noprompt --
        initrd (loop)/casper/initrd.lz
}

---

### Post by klein de usa on 2010-09-25
hello

i installed the script, ran it on ubuntu 10.04, using two usb flash drives neither worked after the script finished it said it was done. both usb flash drives were seen by the bios, one computer and old gateway said the flash drives weren't boot-able , compaq 6715b when each was booted, booted into a grub>_ prompt (that could be bad) when both flash drives were booted on a foxcon m61pmv amd2+ motherboard it told me both flash drives were not boot-able. 

so i installed ubuntu 9.10 on a old Intel motherboard, ran the script, now both flash drives but up fine into grub menu list. ubuntu 9.10 i used was not updated at all just installed and ran. 

i also had the issue with clonezilla and ubuntu, your script only installed the amd64 versions of both, so i copied clonzilla i486 raw iso and ubuntu 10.04 i386 raw iso into /boot/isos and edited the grub config file and everything worked out fine.

great job sundar_ima thank you

---

### Post by ronniet on 2010-10-09
Sounds like an awesome script, but I'm getting a couple of errors trying to put Lucid Puppy and Tiny Core on an 8GB USB.

Here's what I'm seeing in my terminal:

> 
/usr/sbin/grub-setup: warn: Your embedding area is unusually small.  core.img won't fit in it..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.
"Puppy" "Tiny-Core"
`/tmp/temp_liveusb_root5245/live/initrd.gz' -> `/tmp/temp_liveusb_root5245/usb/boot/puppy/initrd.gz'
`/tmp/temp_liveusb_root5245/live/vmlinuz' -> `/tmp/temp_liveusb_root5245/usb/boot/puppy/vmlinuz'
`/tmp/temp_liveusb_root5245/live/lupu-511.sfs' -> `/tmp/temp_liveusb_root5245/usb/lupu-511.sfs'
"Puppy" "Tiny-Core"
Disk Synchronization in Progress ....
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              92G  3.6G   84G   5% /
none                  1.6G  352K  1.6G   1% /dev
none                  1.6G   12M  1.6G   1% /dev/shm
none                  1.6G  584K  1.6G   1% /var/run
none                  1.6G     0  1.6G   0% /var/lock
none                  1.6G     0  1.6G   0% /lib/init/rw
/dev/sda5             798G   84G  674G  12% /home
/dev/sdc1              56G   43G   11G  81% /media/DriveTwo
Start Time: 19:43:21
End Time  : 19:44:04
Installation completed remove USB disk


Looks like it finished OK, but when I boot from the USB stick it's as though it's empty.

Any ideas?...

---

### Post by beew on 2010-10-09
Have you try this? [URL="http://liveusb.info/dotclear/"]http://liveusb.info/dotclear/
[/URL]
I remember there is another thread on community cafe on creating multi boot live CD,  I never use live CDs, too slow and there is no persistence option.

---

### Post by ronniet on 2010-10-09
> **beew said:**
> Have you try this? [URL="http://liveusb.info/dotclear/"]http://liveusb.info/dotclear/
[/URL]
I remember there is another thread on community cafe on creating multi boot live CD,  I never use live CDs, too slow and there is no persistence option.

**Thanks!** I'll give that multiboot app a try, GUI = good :)

---

### Post by C.S.Cameron on 2010-10-09
> **ronniet said:**
> Sounds like an awesome script, but I'm getting a couple of errors trying to put Lucid Puppy and Tiny Core on an 8GB USB.

Here's what I'm seeing in my terminal:



Looks like it finished OK, but when I boot from the USB stick it's as though it's empty.

Any ideas?...

Are you running the script on a computer that uses grub2? It does not work on computers that use grub legacy.

---

### Post by mmck on 2010-11-04
sundar_ima thank you very much for the script. Very impressive. 
Although a beta version and some bugs ( not even worth to mention in a beta release)  I was able to work it via Compaq laptop, running Lucid  and now I have a bootable usb hdd ( 3,5" , 20 gig hdd, in an usb caddy box, which was thrown away in a drawer), 10.04 Lucid, 10.10 Maverick, did not recognise Knoppix however but not an issue. I dual booted a Lenovo ideapad netbook afterwards, with dual boot xp and Lucid in just an hour with no issues. 
I am very very impressed of the work you have done. 
By the way, I am a basic user, and a noob still looking back and forth just to create a directory through the terminal and an Ubuntu user since Intrepid.
Thanks again for the work, wow.

---

### Post by k33bz on 2010-11-06
Will this script give me an option of persistence?

---

### Post by sundar_ima on 2010-11-11
Till now no persistence option is added...

---

### Post by thebarisaxkid on 2010-11-25
sudo i-will-definitely-try-this

---

### Post by drfox on 2010-12-04
Can one add a distro after the MultibootUSB is made? Or is it necessary to wipe and run the entire script again? (BTW, great find, thank you!)

---

### Post by C.S.Cameron on 2010-12-05
If you are adding a distro who's iso boots completely from grub2 and you know the form of the menuentry there should be no problem, (such as Ubuntu).
If it is a complex install, like Puppy, it might be a problem for a non expert.
Updating distro's should not be much of a problem as you can just follow what was done previously.

---

### Post by gunit888 on 2010-12-06
I can finally run the script successfully (I wasn't maximizing my terminal window before), and the drive seems to be created successfully (there's the right structure, the ISOs are there, bootable partition, etc), but when I boot, and I select Clonezilla, I get an error about cannot find file, must load kernel first, and it dumps me back to the menu.  Any ideas what might be going wrong?

Update:  I managed to figure out the problem and get it working for Clonezilla 1.2.6-40.  Please see this post for details: [http://ubuntuforums.org/showthread.php?t=1638473](http://ubuntuforums.org/showthread.php?t=1638473)

---

### Post by Twitch6000 on 2010-12-06
This is pretty cool,but missing alot distros ..

Mandriva and Opensuse are the first to come to mind.

---

### Post by spencer3096 on 2010-12-07
I found out something very interesting about this script: if you are using Ubuntu, don't type ```
#sh ./MultiBootUSB.sh
```  I tried this about 5 times, and the interface refused to display text in the dialog boxes --  especially the one where you choose which distro to install to your stick.  The problem may be related to the fact that Ubuntu uses dash as sh instead of bash (like the Red Hat-based distros).  Using FreeBSD for a few months got me in the habit of typing 'sh ./' instead of './' before shell scripts. :rolleyes:

---

### Post by bachor on 2010-12-09
Thanks [I]sundar_ima :lol:


  I have dual boot XP with Ubuntu and Grub, tried Kubuntu 10.10 on Corsair 8GB flash with your script and it works with no problem ;-)


[/I]

---

### Post by C.S.Cameron on 2010-12-10
> **spencer3096 said:**
> I found out something very interesting about this script: if you are using Ubuntu, don't type ```
#sh ./MultiBootUSB.sh
```  I tried this about 5 times, and the interface refused to display text in the dialog boxes --  especially the one where you choose which distro to install to your stick.  The problem may be related to the fact that Ubuntu uses dash as sh instead of bash (like the Red Hat-based distros).  Using FreeBSD for a few months got me in the habit of typing 'sh ./' instead of './' before shell scripts. :rolleyes:

As mentioned previously, make terminal full screen before proceeding.

---

### Post by su_root on 2010-12-19
Thnx for this project!

Copy this to grub.cfg if problems with CloneZilla (copy clonezilla iso to iso folder)

menuentry "Clonezilla live" {
set isofile="/boot/iso/clonezilla-live-1.2.6-40-i686.iso"
loopback loop $isofile 
linux (loop)/live/vmlinuz1 boot=live live-config noswap nolocales edd=on nomodeset ocs_live_run="ocs-live-general" ocs_live_extra_param="" ocs_live_keymap="" ocs_live_batch="no" ocs_lang="" vga=788 ip=frommedia nosplash toram=filesystem.squashfs findiso=$isofile
initrd (loop)/live/initrd1.img
}

And here if someone wanna boot BitDefender:
	menuentry "BitDefender" {
		loopback loop /boot/iso/bitdefender-rescue-cd.iso
		linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/iso/bitdefender-rescue-cd.iso noeject noprompt --
		initrd (loop)/casper/initrd.gz
	}


Obviously copy bitdefender iso to iso directory.

---

### Post by su_root on 2010-12-22
And here are two different ideas/examples of getting Hirens BootCD to grub2 menu

(needs a "newer" memdisk capable of loading iso's:
[http://www.kernel.org/pub/linux/utils/boot/syslinux/](http://www.kernel.org/pub/linux/utils/boot/syslinux/)
ie extract HBCD folder from iso onto USB and put new memdisk to HBCD folder)

menuentry "Hirens BootCD (takes a while to load..)" {
	linux16 /HBCD/memdisk iso
	initrd16 /boot/iso/Hiren12.0.iso
}

menuentry "Hirens BootCD (DOS-progs)" {
	linux16 /HBCD/memdisk
	initrd16 /HBCD/boot.gz
}

---

### Post by su_root on 2010-12-22
And here is a third way of doing the same thing without purging the iso file onto USB memory:

menuentry "Hiren 12.0" {
set isofile="/boot/iso/Hiren12.0.iso"
loopback loop $isofile
		linux16 /HBCD/memdisk boot=HBCD
		initrd16 /HBCD/boot.gz
	}

---

### Post by sundar_ima on 2010-12-24
Hi all,
I was quite busy with personal work for some time. Today i have released new version of the script. New features and download links can be found on the first post. I will try to include new features and distros in future. Thank you every body for your feedback and support.

---

### Post by C.S.Cameron on 2010-12-24
Thanks for today's updates sundar_ima

If you are taking requests, how about Chromium os. It seems to be the flavour of the day.

---

### Post by sundar_ima on 2010-12-27
Released bug fix Version 1.1.


[B]@C.S.Cameron

how about Chromium os.[/B]

i will look in to it :-)

---

### Post by ineiti on 2010-12-30
Hi,

I tried to use the version 1.1, but it always says the gz-file is corrupt. So now I'm trying version 1.0...

Thanks for the work,

Linus

---

### Post by blacksunseven on 2011-01-05
I can plainly say that I've read this entire thread and followed the directions to a tee and STILL could not get this working in Ubuntu 10.10 x64. My flash drive does not have spaces. I'm sudo'ing where proper. I've got my terminal maximized. I was really hoping this would work, the script itself is beautiful but it's just too bad it doesn't work - it can't find my USB drive.

---

### Post by sundar_ima on 2011-01-06
> **blacksunseven said:**
> I can plainly say that I've read this entire thread and followed the directions to a tee and STILL could not get this working in Ubuntu 10.10 x64. My flash drive does not have spaces. I'm sudo'ing where proper. I've got my terminal maximized. I was really hoping this would work, the script itself is beautiful but it's just too bad it doesn't work - it can't find my USB drive.

Please refer the [COLOR="Red"]60th[/COLOR] post. Whiptail tool comes along with the script is 32 bit version. So please download and replace with 64 bit version of whiptail. Some how it slipped of from my mind. In the next version i try to fix this issue.

---

### Post by Sean Moran on 2011-01-06
Thank you very much Sundar.  If I'd known before of this magnificent simplicity I'd have done it yonks ago and reduced the need for USB sticks around fivefold.

At first I didn't succeed, because I'm working on sets of custom distros with custom names that the MultiBootUSB.sh script doesn't recognise, although I did try adding a few entries into the script here and there to make the formal introductions for script and mysterious .isos, but still to no avail ...

... or so I thought.  What happened was I created a USB stick with the standard /boot/grub diectory with the usual 145 files, alongside an empty /boot/iso dir.  Lo and behold if copying the three .isos straight into that /boot/iso dir and then changing the title and filenames of three parts of each corresponding menuentry in the grub.cfg file didn't do the trick in a matter of minutes!  HOORAY!

Now I have a premonition that I can overcome the problems I've been having with unetbootin-356 (in Karmic) not behaving cordially towards my custom Maverick & Natty distros by simply copying the .iso files straight onto the already working flash drive, and not have to bother with all that wasted time booting into 10.10 just for the sake of unetbootin-471.  I maybe wrong on that one yet, but it's on the way to 23:00 here so I might get some rest and try that one out in the morning.  

Thanks again for demonstrating such a smooth solution to filling up a 4Gb flash drive with a whole family of Live .isos.  I never would have guessed it was so simple.

:popcorn:

---

### Post by sundar_ima on 2011-01-07
Released bug fix version 1.2.

---

### Post by su_root on 2011-01-13
Ok, for you who have problems with the autoinstall, here a simple way to get things done manually.

1. open terminal and become root
2. fdisk -l (<= check usb device)
3. mkdir /mnt/USB_HDD && mount /dev/sdb1 /mnt/USB_HDD (sdb1 = your usb device checked with fdisk -l)
4. grub-install --force --no-floppy --root-directory=/mnt/USB /dev/sdb (where sdb is your usb device)

Now you have installed grub2 to your usb device and now you can manually create boot entrys, iso's etc to the grub list.

---

### Post by sundar_ima on 2011-01-15
Released new version 2.0 with support for lot of distros.

---

### Post by sundar_ima on 2011-01-15
The background image included in the new release is downloaded from internet (for testing purpose). some one can help me in designing new background image for the script (of-course image should have script name).

---

### Post by C.S.Cameron on 2011-01-15
I tried today's update with avg, clonezilla, gparted, kubuntu, linuxmint, systemrescuecd, tinycore, ubuntu-10.10 and tried to do the menuentry for a backup iso from remastersys by hand.
My menuentry for a backup iso from remastersys did not work.

It would be nice if MultiBootUSB did remastersys backup iso's

Edit:

The image looks pretty good but I hope this is not a sign that MultiBootUSB is on the road to becoming bloatware.

---

### Post by sundar_ima on 2011-02-25
After long gap of more than one month i am able to post in this thread. 

Check out the new release.

---

### Post by Quackers on 2011-03-06
I seem to have a problem when running the script.
It runs ok, but when I direct the script to the file where I store my .iso files (imaginatively named "isofiles") it only sees the clonezilla, kubuntu and Windows7 repair .iso files. Actually there are 3 Ubuntu .iso files in there as well that definitely work ok, as I have them booting from the system's grub menu.
Why might that be please?
Thanks.

---

### Post by Bombenbach on 2011-03-11
It would be great if you could also add FreeDos. I use it for testing my HDD's using manufacturer's tools which are unfortunately Dos only.

---

### Post by sundar_ima on 2011-03-12
> **Quackers said:**
> I seem to have a problem when running the script.
It runs ok, but when I direct the script to the file where I store my .iso files (imaginatively named "isofiles") it only sees the clonezilla, kubuntu and Windows7 repair .iso files. Actually there are 3 Ubuntu .iso files in there as well that definitely work ok, as I have them booting from the system's grub menu.
Why might that be please?
Thanks.

will update in the next release...

---

### Post by Quackers on 2011-03-12
That's good news, thanks :-)

---

### Post by kentrel on 2011-03-18
I have a 16GB pen drive and want to run several distros, a general purpose partition for moving files between computers, and I want some (or all) of it encrypted with truecrypt... 

Any idea how to do that?

---

### Post by ubunterooster on 2011-04-13
This thread needs a status update, bump, or something of the sort....

---

### Post by sundar_ima on 2011-04-13
> **ubunterooster said:**
> This thread needs a status update, bump, or something of the sort....
**[COLOR="Red"]Please read the first post.[/COLOR]**

Just released the Version 3.0. It is complete rewrite with lot of features. I have removed whiptail and added **zenity as GUI** for ease of use for newbies. I do not remember all the changes i have made but sure that you will like it and feel  the difference.

Enjoy.

---

### Post by sundar_ima on 2011-04-16
I am planing to include progress option (with auto close) during auto detection of iso files so that some indication is shown to the users. It works fine (line (950) is commented on the script) but it does not take any variable set in the function SELECT_ISO. 

Does anybody have the solution?

---

### Post by sundar_ima on 2011-04-25
Released version 3.5. Now the script supports kde based distros and uses kdialog as GUI. Script works fine on Arch Linux, Opensuse and Kubuntu (all kde based).

---

### Post by Quackers on 2011-05-02
Thanks :-) Ubuntu iso's now booting fine! (version 3 sorted those out I believe).

---

### Post by sundar_ima on 2011-05-03
Gud to know that it works for you.

---

### Post by Quackers on 2011-05-03
And gparted and clonezilla too :-)

---

### Post by sundar_ima on 2011-05-06
Released new version.

---

### Post by Quackers on 2011-05-11
When trying to use version 3.7 I'm getting this error
```
ocelot2@ocelot2-VGN-AR51SU:~/MultiBootUSB$ sudo ./MultiBootUSB.sh
./MultiBootUSB.sh: line 177: syntax error near unexpected token `fi'
./MultiBootUSB.sh: line 177: `fi'

```

---

### Post by sundar_ima on 2011-05-12
uploaded the Updated script.

---

### Post by Quackers on 2011-05-12
I'll have a go then :-) Thanks

---

### Post by sundar_ima on 2011-06-02
Version 4 is out. 
Now you can run the script on **fedora**.

---

### Post by Quackers on 2011-06-02
Aha! Many thanks :-)

---

### Post by Quackers on 2011-06-02
Oh no! It fails to boot Fedora :-(
I'm using Fedora-15-i686-Live-Desktop.iso and it loaded onto the USB without problem and a menu entry appears, on trying it I get the Fedora 15 splash screen for about 20 seconds or so, then it goes to a black screen and this appears at the top

Dropping to debug shell
sh: can't access tty; job control turned off
dracut:/#

Which I presume is the equivalent of an initramfs prompt - maybe?

Any ideas please?
Thanks.

---

### Post by Danimoth on 2011-06-03
I am trying to create a pendrive with Ubuntu Desktop/Server 32-bit and 64-bit. Some things I noticed:

1) Ubuntu Server iso 32-bit/64-bit were not recognized. Only the desktop images appear in the list.
2) When choosing to create a pendrive with Ubuntu Desktop 32-bit and 64-bit, I make sure both are checked from the list, but when the script is finished, I only see 1 iso in the pendrive, specifically the amd64 one.
3) The script asks for a password even when run with sudo. I tried running the script without sudo and/or without entering the password and there was actually no difference.

---

### Post by sundar_ima on 2011-06-04
> I am trying to create a pendrive with Ubuntu Desktop/Server 32-bit and 64-bit.

I have not included the support till now. 

> When choosing to create a pendrive with Ubuntu Desktop 32-bit and 64-bit, I make sure both are checked from the list, but when the script is finished, I only see 1 iso in the pendrive, specifically the amd64 one.

I have assigned single variable for each version. If you try with different version (ubuntu 11.10 and ubuntu 11.04 or something like that) of 32 and 64 bit then it should detect and work with out an issue. Still you can rerun the script and install ubuntu one by one. 

> The script asks for a password even when run with sudo. I tried running the script without sudo and/or without entering the password and there was actually no difference. 

Yes, because it cant bypass zenity dialog box. The thing is that now you need not open terminal to run the script. Simply double click on the script and select run in terminal option. since it provides some sort of feedback/error message, it is strongly recommended that you run the script from terminal.

---

### Post by sundar_ima on 2011-06-04
> I'm using Fedora-15-i686-Live-Desktop.iso

Did you try it in latest version(4)? Because just before release i tested it and works fine with out an issue. Did you check the iso md5sum? 
Pls post grub.conf meny entry of fedora.

---

### Post by Quackers on 2011-06-04
Yes sundar_ima, the checksum is ok. I have also installed Fedora 15 using this iso and all went well.
Here is menu entry for Fedora from grub.cfg (on the MultiBootUSB stick)
```
menuentry "Fedora-Gnome" {
		linux /boot/fedora/vmlinuz0 root=UUID=vfat live_dir=/boot/fedora rootfstype=auto ro liveimg quiet  rhgb rd_NO_LUKS rd_NO_M
		initrd /boot/fedora/initrd0.img
	}
```
The installed Fedora boots fine.
Many thanks for your time.

---

### Post by sundar_ima on 2011-06-04
**> root=UUID=vfat**
Here is the mistake. vfat is not uuid. Use "blkid" command to find out uuid of the usb disk and replace it with "vfat" then it should work fine.

---

### Post by Quackers on 2011-06-04
Ok, will do that, thanks.
How did that get there?

---

### Post by Quackers on 2011-06-04
Thank you sundar_ima, that worked perfectly :-)  Very niiiiiiiice!

Can you tell me why that edit is necessary with only the Fedora entry? Why would grub.cfg have been configured to use "root=UUID=vfat" instead of the actual UUID of the flash drive? Is that something I can avoid in the future?
Again, many thanks!

---

### Post by sundar_ima on 2011-06-04
Did you change any line of gnome.sh or kde.sh script? if not then it should work fine. I have tested it just now and works fine on my lappy. 

It is configured to use actual UUID but i dont know why it didn't pickup. 

Rerun the script and see if the same problem exists or download the new script and run the script.

---

### Post by Quackers on 2011-06-04
Lol, no I have changed nothing in any script. I wouldn't know where to start! :-)
I am quite happy that it is configured to pick up the UUID by default. It may be a fault with my system, perhaps.
I am using version 4. 
This is a very useful tool (even though I have most of my iso's booting from grub2 directly) and I'm grateful for your hard work on it.
Thanks again.

By the way, wouldn't this qualify for a place in Tips and Tutorials section of the forum?

---

### Post by sundar_ima on 2011-06-04
> By the way, wouldn't this qualify for a place in Tips and Tutorials section of the forum?

Well, you will have to tell this... :-)

---

### Post by Quackers on 2011-06-04
I'll make some enquiries on what to do :-)

---

### Post by uRock on 2011-06-04
> **sundar_ima said:**
> Well, you will have to tell this... :-)

In the future you can create a thread in Tutorials & Tips. It will not be visible until it has been looked over and approved, but once approved everyone will be able to see it.

Moved to *Tutorials & Tips*.

---

### Post by Quackers on 2011-06-04
Thank you uRock :-)
I hope people agree that the thread is better off here.

---

### Post by Danimoth on 2011-06-04
> **sundar_ima said:**
> 
Still you can rerun the script and install ubuntu one by one. 


I added 64-bit version first. Space used = 702MB
I tried adding the 32-bit version by re-running the script, but even though it seemed like the flash drive was working and the blue light blinking, the space used remained unchanged at 702MB. Furthermore, in flashdrive/boot/iso I only see one iso, the 64-bit one :/.

edit: Clarification: 64-bit/32-bit refers to Ubuntu 11.04

---

### Post by Quackers on 2011-06-04
Are you using version 4 of the MultiBootUSB script?
Is this with a Fedora iso?

---

### Post by Danimoth on 2011-06-04
Version 4.0 yes, Fedora no, I was talking about Ubuntu, I will edit for clarity :)

---

### Post by Quackers on 2011-06-04
Ah ok.
If you open the USB stick contents then open the Boot folder then open the iso folder, what's in there? One iso or two? It seems only one. If so did you use manual or automatic mode?

---

### Post by Danimoth on 2011-06-05
> **Quackers said:**
> Ah ok.
If you open the USB stick contents then open the Boot folder then open the iso folder, what's in there? One iso or two? It seems only one. If so did you use manual or automatic mode?

I tried both manual and automatic with the same result. However, I am testing a modified script sent by sundar_ima to explore the issue.

---

### Post by Quackers on 2011-06-05
Good luck then :-)

---

### Post by tetris11 on 2011-06-07
I was having huge problems getting Fedora 15 X64-Live-Desktop to boot, using other live usb applications.

The error I kept getting was:
> Trying to install Fedora 15 via a live USB made with unetbootin/usb-creator.exe. I get to the screen where it fills up the blue, then it drops into a debug shell with the message: ```
sh: can't access tty: job control turned off
```

I am pleased to report that after using your truly wonderful script, I am now typing this from within Fedora 15!

Thank you!:P:guitar:

---

### Post by sundar_ima on 2011-06-07
***@ tetris11***

Gud to know that it works for you :-)

---

### Post by sundar_ima on 2011-06-15
Released version 4.5.

---

### Post by Danimoth on 2011-06-15
> **sundar_ima said:**
> Released version 4.5.

Since this is ubuntuforums.org, I would like to point out that all versions of Ubuntu (32-bit/64-bit and desktop/server) now work perfectly and can co-exist in the same flash drive! :D

---

### Post by luisspb on 2011-06-20
Hi,

In the script Functions.sh, lines 2405 and 2447, a "}" is missing at the end of the both lines.
I've tried to install the HBCD iso and have found it.

Regards,
Luisspb.

---

### Post by beew on 2011-06-21
Haven't looked at this yet, but I have been making multiboot usbs for a while using a unity called Multisystem.

[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

website is in French but the program is in English (probably depends on where you download from)

---

### Post by sundar_ima on 2011-06-23
> **luisspb said:**
> Hi,

In the script Functions.sh, lines 2405 and 2447, a "}" is missing at the end of the both lines.
I've tried to install the HBCD iso and have found it.

Regards,
Luisspb.

Corrected in the script & will be releasing soon. Thanks for pointing out error...

---

### Post by geazzy on 2011-06-24
nice tutorial :)

---

### Post by sundar_ima on 2011-06-24
Released version 4.7. With this MultiBootUSB supports 100 distros. :)

---

### Post by Quackers on 2011-06-24
Thanks Sundar for all your hard work :-)

---

### Post by Danimoth on 2011-06-25
Awesome work :)

---

### Post by iomari on 2011-06-26
I'm using opensuse 11.4 and I use grub-legacy as my bootloader. However I have grub2 installed. Will this multiboot script work with this configuration?

---

### Post by Quackers on 2011-06-26
MultiBootUSB uses its own grub2. Yours won't affect it at all.

---

### Post by sundar_ima on 2011-06-27
> **iomari said:**
> I'm using opensuse 11.4 and I use grub-legacy as my bootloader. However I have grub2 installed. Will this multiboot script work with this configuration?

I have not tested it on Opensuse but if grub2 installed on the host system then it should work. If you find error pls post it here.

> MultiBootUSB uses its own grub2. Yours won't affect it at all.
No it does not use own grub2. It uses grub2 from host.

---

### Post by iomari on 2011-06-27
thanks

---

### Post by Quackers on 2011-06-27
I stand corrected :-) My mistake!

---

### Post by dochood on 2011-07-02
Bump, but I don't need to use truecrypt... I just want a dm-crypt encrypted system booting from a pen-drive.  I've found "Privatix", but that is a Debian version.  I want a more general approach that will work with any pen-drive, but doesn't dump the /var/log data or other frequently-changing data until the computer is shutdown.

---

### Post by Jon Anderson on 2011-09-07
Ok do I have grub 2 in ubuntu 11.04 and the explanation above tells you how to download operating systems to the flash drive, but after multiple operating systems are on the flash drive what do I do to open(or start) the specific operating system that I want to use. Am I correct when I say it will load any operating system that is a iso?Thank you.

---

### Post by Danimoth on 2011-09-08
> **Jon Anderson said:**
> Ok do I have grub 2 in ubuntu 11.04 and the explanation above tells you how to download operating systems to the flash drive, but after multiple operating systems are on the flash drive what do I do to open(or start) the specific operating system that I want to use. Am I correct when I say it will load any operating system that is a iso?Thank you.

1) When you boot from the flash drive, you will be given options which will allow you to load any operating system you have included. 

2) I don't think it will load just any OS iso. Each one needs some customization to be able to work correctly, so only the *supported* ones should work.

---

### Post by michaelangelo1267 on 2011-09-09
> **sundar_ima said:**
> [B][COLOR=DarkRed][SIZE=5][B][CENTER][SIZE=6]_MultiBootUSB_[/SIZE][/CENTER]
[/B][/SIZE][/COLOR][/B]

[SIZE=3]Download the latest script from **[COLOR=Red][here]("https://sourceforge.net/projects/multibootusb/files/MultiBootUSB_4.7.tar.gz/download")[/COLOR]**[/SIZE]

[SIZE=4]Send your feedback at [COLOR=Red]**feedback.multibootusb@gmail.com**[/COLOR][/SIZE]

[COLOR=DarkRed]**[SIZE=4]Note:[/SIZE]**[/COLOR] [COLOR=Red][SIZE=3]Though this script will not format your USB drive / Pendrive it is advised to take backup of USB data before invoking the script.[/SIZE][/COLOR]

[COLOR=DarkGreen][SIZE=4]**_1. What is MultibootUSB_**[/SIZE][/COLOR]

    [SIZE=3]MultibootUSB is a shell script written by A Ramesh Kumar and Sundar. Main intention of this program is to install multiple Linux distribution in to single USB disk / Flash drive / Pendrive and able to boot from it with less dependency issue. All you need is your favorite distros in iso format and FAT formatted USB disk. Read the rest to find more.[/SIZE]

[COLOR=DarkGreen][SIZE=4]**_2. Main Features_**[/SIZE][/COLOR]

    [SIZE=3]Automatically detects all inserted USB derive / Pendrive and allow you to choose one.

    Uses GRUB 2 as boot manager

        It can boot hybrid iso images directly (if the distro has the support)

    Ubuntu and Ubuntu based distros like Linux mint can be booted from same pendrive.

    It uses Zenity as GUI and no commands need to be typed in the terminal (except to invoke the program/script)

    As of now this script supports 81+ distros[/SIZE]
    
[COLOR=DarkGreen][SIZE=4]**_2. System Requirement_**[/SIZE][/COLOR]

    [SIZE=3]PC / Laptop which has the option to boot from USB. 

    Any latest Linux distribution with GRUB 2 as boot manager. Recommended OS is  Ubuntu 9.10 and above.

    One or more Linux ISO image(s) of your choice (Only supported by the script)
[/SIZE]
[COLOR=DarkGreen][SIZE=4]**_3. License_**[/SIZE][/COLOR]

    [SIZE=3]You can redistribute this program and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or later. This program is distributed in the hope that it will be useful, but [COLOR=Red]WITHOUT ANY WARRANTY;without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.[/COLOR] See the GNU General Public License for more details <http://www.gnu.org/licenses/>.[/SIZE]

[COLOR=DarkGreen][SIZE=4]**_How to use/run the script_**[/SIZE] ::[/COLOR]

    [SIZE=3]1.    Download the script from [https://sourceforge.net/projects/multibootusb/files/](https://sourceforge.net/projects/multibootusb/files/)

    2.    Extract it to your home folder (Right click --> Extract here)

    3.    Open terminal and move to the script folder (cd MultiBootUSB)

    4.    Provide root permission (su) and type ./MultiBootUSB.sh and hit enter (for Ubuntu just type sudo ./MultiBootUSB.sh with out issuing su command)

    6.    Here after follow on screen instructions 

        7.      Screenshots can be found in doc folder for reference.[/SIZE] 

**[COLOR=DarkGreen][SIZE=4]_List of distributions supported_[/SIZE][/COLOR]**

[B][SIZE=3][COLOR=Blue]1.   Archiso Live
2.   Aptisid
3.   Austrumi
4.   AVG Rescue CD  
5.   Backtrack
6.   Bit Defender Rescue CD
7.   Bodhi Linux
8.   CD linux
9.   Chakra Linux
10. Clonezilla Live
11. CrunchBang
12. CTK Arch Live  
13. Debian
14. Deli
15. Doudolinux
16. Dream Linux
17. Dynebolic
18. Elive
19. Fedora*
20. Fuduntu
21. GeexBox
22. Goblinx
23. Gnome 3.0 - Fedora
24. Gnome 3.0 - Open SUSE
25. Gparted Live
26. GRML
27. HBCD
28. Igolaware
29. Imagine OS
30. Jolicloud
31. Kaspersky Rescue CD
32. Knoppix
34. Kubuntu*
35. Linux Mint*
36. Linux Mint - DE
37. Lubuntu
38. Manriva One
39. Me OS
40. Moon OS
41. Nimblex
42. Open SUSE
43. Ophcrack Live CD
44. Panda Rescue CD
45. Pardus
46. PCLinux OS*
47. Pentoo
48. Peppermint OS
49. PinGuy OS
50. Parted Magic
51. Pure OS
52. Puppy*
53. Rescue CD (System Rescue CD)
54. RIP Linux
55. Saline OS
56. Sabayon Linux
57. Scientific Linux
58. Sidux
59. Simply Mepis
60. SLAMPP
61. Slax
62. Slitaz
63. Stress Linux
64. Tiny Core
65. UBCD
66. Ubuntu*
67. Ubuntu Netboot*
68. Ubuntu Rescue
69. Ubuntu Ultimate Edition
70. Unity Linux
71. Vector Linux
72. Windows/NT Password / registery editor
73. Xpud
74. Xubuntu*
75. YLMF
76. Zenwalk
77. Zeven OS
78. Zorin OS
79. Salix Live
80. Free DOS
81. SAM Linux
82. Absolute Linux
83. Apodio
84. Arch Linux 32 Bit
85. Arch Bang
86. DEFT Linux
87. Express Linux
88. LDR
89. Porteus
90. Redo Backup Live CD
91. Tails
92. Mageia Linux
93. Calculate Linux
94. Vidalinux
95. MeeGO
96. Dam Small Linux
97. Elementary OS
98. Netrunner
99. Webconvergence
100.FreeBSD[/COLOR]
[/SIZE][/B]
[COLOR=Magenta]
[SIZE=4][SIZE=3]**Please give your feedback, suggestions, request for new features and comments as reply.**[/SIZE][/SIZE] [/COLOR]

Wow this is very informative. Thank you for sharing this. I need to learn more about ubuntu. Thanks again.

_______________________________
[Michael @ pizza franchise in new jersey]("http://www.nypizzeria.com/franchise/")

---

### Post by sundar_ima on 2011-10-25
I have ported MultiBootUSB to windows (but using syslinux). Link to binary and source is [COLOR="Red"][here]("https://sourceforge.net/projects/multibootusb/files/Windows/")[/COLOR] 

[COLOR="Red"][https://sourceforge.net/projects/multibootusb/files/Windows/](https://sourceforge.net/projects/multibootusb/files/Windows/)[/COLOR]

Any suggestion is welcome. At the moment it is supporting only 22 Distros but will include more soon.

---

### Post by nooby on 2011-10-29
Wow that was impressive. 

I found something similar here **Install Ubuntu from iso using Grub4Dos**
[http://agnipulse.com/2011/08/install-ubuntu-hard-disk/]("http://agnipulse.com/2011/08/install-ubuntu-hard-disk/")

Not exactly the same but helpful never the less. 

One can use a variation of that code to "Live" boot every ubuntu distro 
and a Linux Mint that is based on Ubuntu but not any of the Debian varieties works good. Some boot some dont. 


 title lubuntu 11.10 desktop version
 find --set-root --ignore-floppies --ignore-cd /lubuntu-10.10.iso
 kernel	/lubuntu/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper iso-scan/filename=/lubuntu-10.10.iso kmap=se LANG=sv_SE.UTF-8 keymap=sv-latin1 noeject noprompt quiet splash --
 initrd	/lubuntu/casper/initrd.lz

 title Netrunner 2011 frugal iso boot of netrunner-3.2.iso 
 find --set-root --ignore-floppies --ignore-cd /netrunner-3.2.iso
 kernel	/netrunner/casper/vmlinuz rw  file=/cdrom/preseed/netrunner.seed boot=casper iso-scan/filename=/netrunner-3.2.iso noeject noprompt quiet splash --
 initrd	/netrunner/casper/initrd.lz


compare with the code he gave. My simple version worked for me. 
One need to put the casper and preseed directories on / on the hdd. 
But that hdd can be a Ms Win7 or any other of that kind. So a good 
way for a noob who have a Net book without CD and have no USB to boot from
then one can get a fast version of how all ubuntu's compare. One can add as many Ubuntu as one want only need to put them in their own directories like in my example.

---

### Post by deckoff on 2011-12-01
I dont know if the OS is the one responsible for the tool, but I will share my thoughts - My desktop will only boots usbs that are formatted to boot MS-DOS. Then the pc lists the pendrive as hard-drive and boots OK. 
If the pendrive is prepared in any other way( unetbootin, Ubuntu live usb, Multiboot, etc) the pendrive will report "boot error" or if GRUB is installed, the sisytem will declare the USB not bootable.
So, I kindly ask for Grub4DOS version of this tool or at least for a way to boot off a multibootUSB out of USB-DOS booted machine. 
The method described above me will work for ubuntu and family, but I cant figure out how to boot OpenSUSE ( have not tried with fedora and others anyway)

---

### Post by sundar_ima on 2011-12-01
Have you tried windows version of MultiBootUSB. Windows version uses Syslinux as boot manager and known for supporting FAT file system. Link is here sourceforge.net/projects/multibootusb/files/Windows/

I have tested MultiBootUSB (Linux/Windows) on many machines and did not encountered any issue with booting. 

> My desktop will only boots usbs that are formatted to boot MS-DOS

Did you format your pendrive with FAT filesystem or NTFS? I am not sure about NTFS but you should not have any issue with FAT filesystem.

Could you explain method followed in making MultiBootUSB step by step? This would help in troubleshooting and also the output of terminal (if you used MultiBootUSB (linux))

---

### Post by deckoff on 2011-12-02
> **sundar_ima said:**
> 
Did you format your pendrive with FAT filesystem or NTFS? I am not sure about NTFS but you should not have any issue with FAT filesystem.

Could you explain method followed in making MultiBootUSB step by step? This would help in troubleshooting and also the output of terminal (if you used MultiBootUSB (linux))

1) I have not tried the Windows version, i will.
2) I do think the BIOS is to blame - the same USB will work on at least 4 other different PCs without any issues. Since the usb works on all but one pc ok, I assume I do things right ;)
3) On the other hand, as I said not only multibootUSB, but Unetbootin and ubuntu Live usB creator will fail to boot.("boot error" - that is the whole error message) When I do clean install of GRUB2 on the usb, the BIOS will state the usb is not bootable (although it will then again boot OK on other PCs)
4) I would be happy to know how the boot process of this tool works, I think chainloading my multibootUSB flash with another one, using grub4dos(0.4.4) might solve my issue.
I have tried with this entries:
```

title Boot form HD0
root (hd0,0)
kernel /boot/grub/core.img
savedefault
boot

title Boot form HD1
root (hd1,0)
kernel /boot/grub/core.img
savedefault
boot 


title Boot form HD2
root (hd2,0)
kernel /boot/grub/core.img
savedefault
boot 

```
but i receive error that file is not existent( even though the drive is found).
So, more info on the method used to boot (grub, grub2, syslinux etc)

I confused this tool with MultiSystemUSB! i will try and report...

---

### Post by deckoff on 2011-12-02
1.1) OpenSUSE fails to boot when trying it from MultibootUSB.
Since Xubuntu loads OK, I presume there are some changes in latest ISO
1.2)Linux Mint 12 new iso  is not recognized as a distro
2) Creating DOS-usb which is able to execute grub4dos, and then chainloading GRUB2 off grub4dos boots this USB OK.
I use tthis entry:

```
title Boot MultiBOOT LinuxUSB
find --set-root /boot/bootme.tag
kernel /boot/grub/core.img
savedefault
boot 
```
for this to work, NON-empty (random text is OK) file, named bootme.tag, should be added in [COLOR="Red"]/boot/[/COLOR] of the [COLOR="red"]MultiBOOTUSB USB[/COLOR]. **NOT IN THE DOS USB**

---

### Post by saana on 2011-12-27
I tried latest MultiBootUSB by first creating a FAT32 partition on USB memory stick and executing MultiBootUSB.sh.  Then I selected to manually add Debian live image

[http://cdimage.debian.org/debian-cd/current-live/i386/iso-hybrid/debian-live-6.0.3-i386-standard.iso](http://cdimage.debian.org/debian-cd/current-live/i386/iso-hybrid/debian-live-6.0.3-i386-standard.iso)

to it.  Apart from a few rm error messages and cp overwrite question, installation went fine.

Then I booted my PC from the USB memory stick and chose from grub menu to install Debian Live image.  That failed with lots of "device for boot... isofrom not found /dev/disk/by-uuid/Debian/...".  The final error message was "Unable to find a medium containing a life file system".

It is so that the above mentioned Debian live image is not supported by MultiBootUSB or what was it that I did wrong?

---

### Post by s0n0fagun on 2012-02-15
Thanks for the script.  Even though I had issues, I saw what you did and made modifications. Ubuntu 11.10 works, however Linux Mint 12 and Sabayon 8 did not work.  Looking into the functions script, I noticed it is chained copy of all the allowed distributions.  After locating Linux Mint 11, copied the entries into Linux Mint 12 and it worked.  Sabayon 8 (could be my ISO is special or because it is Gnome built) placed the label in the info.txt(something *.txt) instead of the standard grub.conf.  Repeated the process of copy and paste.  Then it worked like a charm.  After the reboot though, I had duplicate entries so I had to reboot and fix the list. :-D  Now if someone can tell me how to manipulate this script to include Windows 7 iso, I would be grateful.  I read though the iso needs to be the first entry in the boot sector but who knows?  I am not good at that stuff.

By the way, why do you only support the 32bit version of Arch?  I only see the 64 and the 686.

> **saana said:**
> 
It is so that the above mentioned Debian live image is not supported by MultiBootUSB or what was it that I did wrong?

As I described, you might need to do some hackery to get it to work.  I suspect it cannot find the label in your Debian ISO so the script actually fails to copy the iso to your flash drive.  Instead you are left with an empty bootable pen drive that does not point to the iso.

---

### Post by cocoa117 on 2012-02-20
I have used the version 4.7 which is latest, and it does not show ISO image I added in the second and third time when it ask to add more images.

---

### Post by cocoa117 on 2012-02-22
I just realised the problem, it seems MultiBootUSB doesn't do well with ubuntu alternate installation CD, the linux kernel image is located in /install folder rather then /casper folder. 

In addition, the Ubuntu alternate installation CD still suffer from "Incorrect CD-ROM detected" error, even with the method of cdrom-detect/try-usb=true

Anyway to fix the above bug? Maybe I can learn to write a patch, so others can benefit from it.

---

### Post by koegs on 2012-04-23
> **cocoa117 said:**
> I just realised the problem, it seems MultiBootUSB doesn't do well with ubuntu alternate installation CD, the linux kernel image is located in /install folder rather then /casper folder. 

In addition, the Ubuntu alternate installation CD still suffer from "Incorrect CD-ROM detected" error, even with the method of cdrom-detect/try-usb=true

Anyway to fix the above bug? Maybe I can learn to write a patch, so others can benefit from it.

Any update on that topic?

I am trying to use several ISOs with manual editing of grub.cfg but still not luck with the alternate cd, all other isos are working:

```

menuentry "Xubuntu 11.10 Alternate AMD64" { 	loopback loop /iso/xubuntu-11.10-alternate-amd64.iso 	linux (loop)/install/vmlinuz cdrom-detect/try-usb=true file=/cdrom/preseed/xubuntu.seed boot=casper iso-scan/filename=/iso/xubuntu-11.10-alternate-amd64.iso noeject noprompt -- 	initrd (loop)/install/initrd.gz }

```

---

### Post by Elfy on 2012-06-29
This thread is closed. 
 
The information is now held on the community wiki at  [https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk](https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk)
 
Thank you for your thread and the work you have done in keeping it current and of use to the community. 
 
A thread for discussion of the wiki can be found at  [http://ubuntuforums.org/showthread.php?t=2012396](http://ubuntuforums.org/showthread.php?t=2012396)
 
 
Support threads regarding the wiki and it's content should be created in a suitable forum.

---

