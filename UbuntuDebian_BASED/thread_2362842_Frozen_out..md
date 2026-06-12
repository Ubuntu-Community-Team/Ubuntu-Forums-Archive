---
title: "Frozen out."
date: 2017-06-02
forum: Ubuntu/Debian BASED
---

### Post by twub2 on 2017-06-02
New to Linux, I am attempting to try  out Ubuntu Lite 16.04.2 LTS on an old AMD machine with a Sis Graphic card, that works well on XP.
Running from a prepared disc,  I can (eventually) reach the desktop, but on moving the mouse to the task bar, everything freezes and I am reduced to turning off the power supply.
Suggestions would be welcome, please.

---

### Post by Bucky Ball on 2017-06-02
Would suggest you try out regular Ubuntu instead or, if you're going for Lite because it uses less resources (I have no idea whether it does) then perhaps [Xubuntu]("https://xubuntu.org/getxubuntu/") or [Lubuntu]("https://help.ubuntu.com/community/Lubuntu/GetLubuntu").

Ubuntu Lite is not officially supported by Canonical or the main forum areas here. You will get better support with an official flavour. 

On an old machine like that, you might have problems and more than likely will have trying to get Ubuntu on it rather than a lighter flavour, particularly if you have a meagre amount of RAM. The SIS graphics card may only be the beginning of your issues.

---

### Post by QIII on 2017-06-02
Moved to Ubuntu/Debian BASED since this is not an official Ubuntu flavor.

---

### Post by twub2 on 2017-06-02
Thanks, both.
I think I have confused the issue. I did not realise that I am using Lubuntu 16.04.2 LTS and that this is a flavour different to Ubuntu Lite.

---

### Post by mörgæs on 2017-06-02
SIS more or less ignored GNU/Linux and they provided very limited support for the developers trying to write drivers. This means that you might need to work with some settings to get it running.

First let's see more about the graphics processor. Please run ```
sudo lshw -C video
``` and post the results in CODE tags if the system is stable enough.

---

### Post by 2011spook on 2017-06-02
id  advise xubuntu or ubuntu mate for that machine

---

### Post by twub2 on 2017-06-03
Thanks.
Using XP and run, I get "windows cannot find sudo".
If it is going to be a nuisance or consume your time, I am happy to drop this but wonder if there is any flavour that would be more suitable and allow this ancient set-up to cope . Otherwise, will wait and use another machine.

---

### Post by mörgæs on 2017-06-03
> **twub2 said:**
> 
If it is going to be a nuisance or consume your time...

If that bothered me then I wouldn't have answered your thread. It's much to early to give up.

The command must be run in Lubuntu, either from an installed system of from a live boot. Maybe XP can also show detailed information about the graphics card, I don't know.

---

### Post by twub2 on 2017-06-03
OK.Thanks. 
I can't use Lubuntu, but dxdiag in XP shows Sis 760 PS Chip with 32MB memory and SiS GRV.dll driver versionn 6.14.0010.3673 if that helps.

---

### Post by mörgæs on 2017-06-03
A 760 should be possible to get working but maybe in a coarser resolution than XP. I suggest that you boot into XP, reduce the partition size in order to create 10 GB or so empty space and install Lubuntu 16.04.2 in a dual boot. If any problem appears then we take it from here.

---

### Post by twub2 on 2017-06-04
OK Reduced partition and used option from CD to "Install" Lubuntu.
Eventually got to desktop (without icons or task bar) then message "A Start process......" came up and which swiftly jumped to a black screen.
Have had to power off and revert to XP.

---

### Post by mörgæs on 2017-06-04
Are you able to boot into recovery mode?

---

### Post by twub2 on 2017-06-05
No. Only via XP Boot and then I am still in XP.
Booting without DVD does not offer a dual boot option and just boots up XP.
Booting from DVD whilst pressing esc  or left shift does not go to recovery (safe) mode, although I can get to BIOS settings.

---

### Post by mörgæs on 2017-06-06
I'm wondering if there are other difficulties than the SIS graphics card.
Please post all the hardware information you have.

---

### Post by twub2 on 2017-06-06
[B][SIZE=2]Don't laugh--it may be old, but it does all that I need!

Operating System[/SIZE][/B]		[TABLE]
[TR]
[TD="width: 48%, bgcolor: efefef, align: center"][/TD]
[TD="width: 4%"] [/TD]
		[TD="width: 48%, bgcolor: efefef, align: center"]**[SIZE=2]System Model[/SIZE]**[/TD]
[/TR]
  	[TR]
[TD="width: 48%"][SIZE=2]Windows XP Home Edition Service Pack 3 (build 2600)
Install Language: English (United States)
System Locale: English (United States)[/SIZE][/TD]
							[TD="width: 4%"] [/TD]
		[TD="width: 48%"][SIZE=2]Enclosure Type: Desktop[/SIZE]
[/TD]
[/TR]
  	[TR]
[TD="width: 48%, bgcolor: efefef, align: center"]**[SIZE=2]Processor [SUP]a[/SUP][/SIZE]**[/TD]
	[TD="width: 4%"] [/TD]
		[TD="width: 48%, bgcolor: efefef, align: center"]**[SIZE=2]Main Circuit Board [SUP]b[/SUP][/SIZE]**[/TD]
[/TR]
  	[TR]
[TD="width: 48%"][SIZE=2]1.80 gigahertz AMD Sempron
128 kilobyte primary memory cache
128 kilobyte secondary memory cache
64-bit ready
Not hyper-threaded[/SIZE][/TD]
					[TD="width: 4%"] [/TD]
		[TD="width: 48%"][SIZE=2]Board: WinFast 760GXK8MC 
Serial Number: WY3F61601711
Bus Clock: 200 megahertz
BIOS: Phoenix Technologies, LTD 6.00 PG 10/08/2005[/SIZE][/TD]
[/TR]
  	[TR]
[TD="width: 48%, bgcolor: efefef, align: center"]**[SIZE=2]Drives[/SIZE]**[/TD]
					[TD="width: 4%"] [/TD]
		[TD="width: 48%, bgcolor: efefef, align: center"]**[SIZE=2]Memory Modules [SUP]c,d[/SUP][/SIZE]**[/TD]
[/TR]
  	[TR]
[TD="width: 48%"][SIZE=2]68.56 Gigabytes Usable Hard Drive Capacity
36.36 Gigabytes Hard Drive Free Space

DVDRW IDE H16X [CD-ROM drive]
3.5" format removeable media [Floppy drive]

IC USB Storage-CFC USB Device [Hard drive] -- drive 2
IC USB Storage-MMC USB Device [Hard drive] -- drive 3
IC USB Storage-MSC USB Device [Hard drive] -- drive 4
IC USB Storage-SMC USB Device [Hard drive] -- drive 1
WDC WD800BB-55JKC0 [Hard drive] (80.03 GB) -- drive 0, s/n WD-WMAMD6039799, rev 05.01C05, [SMART]("http://www.belarc.com/smart.html") Status: Healthy[/SIZE][/TD]
				[TD="width: 4%"] [/TD]
		[TD="width: 48%"][SIZE=2]1504 Megabytes Usable Installed Memory

Slot 'A0' has 1024 MB
Slot 'A1' has 512 MB[/SIZE][/TD]
[/TR]
  	[TR]
																		[TD="width: 4%"] [/TD]
		[TD="width: 48%, bgcolor: efefef, align: center"]**[SIZE=2]Local Drive Volumes[/SIZE]**[/TD]
[/TR]
  	[TR]
																		[TD="width: 4%"] [/TD]
		[TD="width: 48%"][SIZE=2][TABLE]
 [TR]
[TD="width: 50%"][/TD]
[TD="width: 20%"][/TD]
[TD="width: 30%"][/TD]
[/TR]
  [TR]
[TD][SIZE=2]c: (NTFS on drive 0)[/SIZE][/TD]
 [TD][SIZE=2]68.56 GB[/SIZE][/TD]
 [TD][SIZE=2]36.36 GB free[/SIZE][/TD]
[/TR]
  [/TABLE]
 [/SIZE][/TD]
[/TR]
  	[TR]
																		[TD="width: 4%"] [/TD]
		[TD="width: 48%, bgcolor: efefef, align: center"]**[SIZE=2]Network Drives[/SIZE]**[/TD]
[/TR]
  	[TR]
																		[TD="width: 4%"] [/TD]
		[TD="width: 48%"][SIZE=2]*None detected*[/SIZE][/TD]
[/TR]
[/TABLE]

---

### Post by mörgæs on 2017-06-06
It's slow but not hopeless. If you want to try the hardware as-is I suggest that you experiment with the VESA approach and/or the minimal install as explained in the link in my signature. 

Another option is adding an AGP 8X graphics card from a vendor other than SIS if you can get it for free or very cheap. Not only easier to work with, also faster.

---

### Post by twub2 on 2017-06-07
OK.
Many thanks for your input.
I will see what I come across and play around when I am bored.
Best wishes.

---

### Post by mörgæs on 2017-06-07
Good luck. Please post the results from the installs when you try them.

---

