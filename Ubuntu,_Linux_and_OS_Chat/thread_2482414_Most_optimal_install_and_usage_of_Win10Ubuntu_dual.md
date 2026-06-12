---
title: "Most optimal install and usage of Win10/Ubuntu dual boot"
date: 2022-12-30
forum: Ubuntu, Linux and OS Chat
---

### Post by smith73 on 2022-12-30
So there's a 16GB RAM laptop with Windows 10 pre-installed and I'd like to dual boot it with Ubuntu.
As I've google a bit, some recommend shrinking the main partition in Windows and
install Ubuntu on the free space. I do not use Windows often for now, but would like to
leave it for some time as a type of reserve. My main concerns are the following:

1) **Are there any drawbacks/potential risks for Ubuntu in such dual boot configuration?**
(like whether any potential defects in Windows file system may affect the booting
capacity of Ubuntu etc)

I used a Win8/Ubuntu dual boot previously on 4GB RAM and apparently Ubuntu run rather 
smoothly. But as the main SSD comes pre-partitioned by Windows and after shrinking the
main partition to get free space for Ubuntu, Windows partitions can still  be distributed 
unevenly throughout the physical SSD space: ~like some partitions in the beginning,
another partition in the end of SSD, while the free space for Ubuntu is only in the middle
of the SSD space.

2) While shrinking the main SSD in Windows, some users allocate a rounded number of GB
for Ubuntu (like e.g. 150000 MB or 150GB). [B]Can it be more optimal to enter a byte-oriented
number of MB (like - the multiples of 256 or 1024 etc) to include whole bytes?[/B]

I am planning to allocate ~750GB for Ubuntu and 250Gb for Windows, but tuning the partitoms
manually the number of megabytes may be required to enter.

3) Some tutorials recommend using Startup Disk Creator or its analog in Ubuntu Mate - 
Mate Disk Image Mounter to create  a bootable USB with Ubuntu. I used a bootable
USB with Ubuntu created by this tutorial "Make a bootable USB drive on any Linux distro [1],
using dd, wipefs, cfdisk, mkfs CLI utilities.
[B]Is it more optimal to create a bootable USB with Ubuntu via CLI tools or GUI tools ?
[/B]
[1]https://www.youtube.com/watch?v=rpGgTTFKwiU

4) Some tutorials on dual boot recommend using "Normal install" option while installing 
Ubuntu in dual boot (which performs partitioning etc automatically), others - recommend
"Something else" option where you choose partition attributes for Ubuntu manually.
It seems I used the "Normal install" option last time and "Something else" option for Ubuntu
16 didn't work. **What option is more optimal for Ubuntu - "Normal install" or "Something else"?**

5) If after some time of using the Win10/Ubuntu dual boot [B]I may want to remove Windows, or 
shrink the Windows or Ubuntu partitions to reallocate free space, can I do this without reinstalling Ubuntu[/B]?

---

### Post by oldfred on 2022-12-30
The vast majority of users dual boot Windows & Ubuntu one one drive.
Windows NTFS needs about 30% free to work well. Linux ext4 needs some extra space but not as much as Windows. And SSD should have some unused space so they can manage use.

Booting Windows may update Windows & turn on fast startup and may update UEFI. If UEFI updated, you often have to redo the settings you change to have system work.

You should always have a live installer (ubuntu) or repair disk (Windows) for current version of all installed systems. 
And you always need current backups. SSD houseclean (trim), so write is quicker. HDD just overwrite so old data still there and sometimes can be recovered. But with good backups, then no issues.

You can remove Windows & keep Ubuntu. Some move partitions which has a bit higher risk as all data has to be copied. Others use as /home or just as data partition for more data. Do not remove ESP - efi system partition which is used by both Windows & Ubuntu. 

Many use normal install. Best to shrink Windows with Windows tools so install has unallocated space. 
Using Something Else is only required if you want more than default / (root) partition. That is all a new user really needs.
If re-installing or want separate /home then you use Something Else. You can create partitions in advance with gparted or create as you install. 

Be sure to boot installer in UEFI boot mode.

More info in link in my signature below.

---

### Post by smith73 on 2023-01-05
> **oldfred said:**
> Booting Windows may update Windows & turn on fast startup and may update UEFI. If UEFI updated, you often have to redo the settings you change to have system work.

I do not plan to connect Windows to the internet so far. I disabled the fast startup option in Windows, as was recommended by some guides on Win/Ubuntu dual boot.
Lenovo manufacturer on their pcsupport site for this ThinkPad provide drivers for manual install on Windows: there are drivers for Advanced Firmware (ThinkPad USB-C Dock Firmware, Firmware for Windows 11 (64-bit), 10 (64-bit) - ThinkPad USB-C Dock Gen 2), BIOS/UEFI  (BIOS Update (Utility & Bootable CD) for Windows 11, 10 (64-bit)).
Should I install Firmware and BIOS drivers for Windows and wouldn't this interfere with dual booting Ubuntu?

There are also storage, GPU, motherboard devices', power management, networking etc drivers. Should I install them on Windows, if I am planning to use Windows offline
mainly for Windows specific software (3d modelling etc)?

> **oldfred said:**
> Some move partitions which has a bit higher risk as all data has to be copied.
So is it possible to remove Windows and reallocate all space to Ubuntu without reinstalling Ubuntu?

---

### Post by oldfred on 2023-01-05
Many vendors make it easier to update firmware from Windows. Both UEFI & SSD.
But more & more vendors are using fwupdate with Linux. Check to see if your system is in the list.
[https://fwupd.org/](https://fwupd.org/)
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)

Drivers are all in Ubuntu, so you do not need Windows drivers for Ubuntu.

Best to use Ubuntu live installer in live mode and confirm what works or not. 

My desktop systems with standard motherboards are not  in lvs. But they have UEFI that can update directly or update from a downloaded file in a fAT32 partition. So I typically make my ESP larger, so it has room for the update file, but have used an external flash drive formatted FAT32.

---

### Post by smith73 on 2023-01-07
> **oldfred said:**
>  Check to see if your system is in the list.

Mine is ThinkPad E14 Gen2 (AMD) and devices in the list are only Gen4 [[1]("https://fwupd.org/lvfs/search?csrf_token=ImUwY2Q0YmE0YzRiNzM0ZDI4NTI4NGYzODRhNTU4NGMxOTYwMzU2ZTEi.Y7mpfQ.TH0CQ5WPwwd9SGnFRFWG1vXK84s&value=thinkpad+E14")]. Should I use it for E14 Gen2?

> **oldfred said:**
> Drivers are all in Ubuntu, so you do not need Windows drivers for Ubuntu.

I suppose Ubuntu and Windows in dual boot will share the same BIOS. So was curious whether any changes made by Windows to BIOS won't affect Ubuntu.
Or can it more optimal to install only non-BIOS specific drivers (if I plan to use Ubuntu most of the time)?

---

### Post by oldfred on 2023-01-07
Windows updates often change Windows to be first in UEFI boot order, just as a major update to grub will do.
Windows can turn fast start up back on.
And Windows updates may automatically do an UEFI firmware update. That often resets UEFI settings to defaults. My older Asus motherboard had 7 settings I changed, some required, some optional. But I kept a list and when I manually updated UEFI, I knew I had to make those changes again.
Windows may not tell you that it is also updating UEFI or what settings it is changing.
And Windows updates seem to take forever, but can be in background until you reboot and it does more updates.

---

### Post by TheFu on 2023-01-07
Why dual boot at all?  Just run one of the OSes inside a virtual machine.  This removes most of the common problems caused by dual booting.  Current hypervisors have less than 10% overhead, so VMs run very fast for everything except where direct hardware access is needed, like for games.  For almost any other purpose, besides games and video editing, a VM works excellent.

---

### Post by smith73 on 2023-01-08
> **oldfred said:**
> Windows updates often change Windows to be first in UEFI boot order, just as a major update to grub will do.
Windows can turn fast start up back on.
And Windows updates may automatically do an UEFI firmware update. That often resets UEFI settings to defaults.

Windows may not tell you that it is also updating UEFI or what settings it is changing.
And Windows updates seem to take forever, but can be in background until you reboot and it does more updates.

[B]Do you mean all that only when a Windows is connected to the Internet? So Windows can perform updates even if
the user disabled/paused the updating feature in Windows GUI?[/B]

Upon installation of Ubuntu in dual boot, I am not planning to connect Windows to the internet as long as possible,
i.e. I may be using Wi-fi/Ethernet in Ubuntu only, but have Windows in dual boot.

I've manually downloaded in Ubuntu the basic Win drivers provided by Lenovo manufacturer on the device support page,
and the Advances Firmware, BIOS/UEFI drivers are not marked as critical, but recommended only. The critical drivers are:
1) Graphics Processing Units (GPU) and Server-AI Accelerators; 2) Motherboard Devices (core chipset, onboard video, PCIe switches
-AMD IO driver); 3) Mouse, Touchpad, Keyboard and Pen; 4) Networking: LAN (Ethernet); 5) Software and Utilities - Hotkey 
Features Integration. **So would it be more or less safe to install these basic drivers ****provided by the manufacturer **[B]
offline in Windows?

[/B]So I may install these drivers in Windows offline, then install Ubuntu in dual boot and won't connect Windows to the internet.
**Thus Windows shouldn't be able to update GRUB and **[B]UEFI boot order while not connected to the internet or 
while only Ubuntu is connected to the internet?[/B]

 Currently I've paused updates in Windows for 35 days, but I am a bit horrified: Windows writes: "When you reach the pause limit
(i.e. after 35 days), your device will need to get new updates before you can pause again".

Currently I've disabled wi-fi in BIOS and the ThinkPad device is in airplane mode. But its BIOS has a mouse pointer and froze once I was
in BIOS and tried to use the mouse pointer (have never seen anything similar in ~5-7 BIOS'es I've ever seen).

---

### Post by oldfred on 2023-01-08
Windows really wants to be on-line.
And for Windows & Windows security updates you do have to be on line to get those.
I have had no issues using Windows on line other than I hate its update process. But I do it rarely as I do not regularly boot Windows, so it takes a long time. 

I prefer to monitor updates in both Windows & Ubuntu, rather than go off and do something else. Then if something is not working I can maybe tell if an update is related. But Windows does not really tell me much where with Ubuntu I can see every file it is updating when I do it manually in terminal.

---

### Post by smith73 on 2023-01-08
> **TheFu said:**
> Why dual boot at all?  Just run one of the OSes inside a virtual machine.  This removes most of the common problems caused by dual booting.  Current hypervisors have less than 10% overhead, so VMs run very fast for everything except where direct hardware access is needed, like for games.  For almost any other purpose, besides games and video editing, a VM works excellent.

Well, I was searching for a reliable laptop (for learning CS/programming, CADs etc) without Windows from local vendors and it was sort of a hell as there are very few of them, so I've found sort of a good Cristmas deal on hardware but with Windows. So it is already installed, and despite some of its crappy features it is, well, some software, the whole OS actually, so it seems sort of a pitiful to erase it (at least for now).

During the last ~dozen of years I used Ubuntu successfully enough, but needed Windows on bare metal only to use a driver for an old Epson scanner and to repair NTFS on an USB drive. Windows VM guest on Ubuntu didin't recognize the scanner via USB port. If I solve these 2 issues for Ubuntu, I wouldn't pay so much attention to Windows stuff currently and would use Windows on VM for other Windows apps. Though as this Thinkpad has 14" display, it would also be useful to try to make a Windows VM guest 100% full screen, as even VM Guest Additions still preserve a ~5mm minimal display frame with VM controls.

---

### Post by smith73 on 2023-01-08
> **oldfred said:**
> I prefer to monitor updates in both Windows & Ubuntu, rather than go off and do something else. Then if something is not working I can maybe tell if an update is related. But Windows does not really tell me much where with Ubuntu I can see every file it is updating when I do it manually in terminal.

As far as I have navigated through the Windows 10 Settings, in the Updates section there are such options as ~Show Installed Updates and ~Uninstall Updates. Isn't this enough?

I also noticed that it requires sign-in into Microsoft account to use Office tools, so won't be able to use them without the Internet, or, well, install a cracked version.
I'd really love to run an AI tool ChatGPT (which can already write Linux kernels, React apps, html etc) in Windows for all these issues.

How do you see every file Ubuntu is updating when in terminal? Isn't *sudo apt-get update* enough?

---

### Post by oldfred on 2023-01-08
I use sudo apt update.
And if in a script which I use that both housecleans, updates & shows me how full all my partitions are, use apt-get.
Someone posted that apt for for terminal & apt-get for scripts. Although it seems either works.

From man apt page:
> [FONT=monospace][COLOR=#000000]apt - command-line interface[/COLOR]
[/FONT]

But apt-get's man page is similar.

---

### Post by smith73 on 2023-01-08
> **oldfred said:**
> Windows really wants to be on-line.
And for Windows & Windows security updates you do have to be on line to get those.
I have had no issues using Windows on line other than I hate its update process. But I do it rarely as I do not regularly boot Windows, so it takes a long time. 

I prefer to monitor updates in both Windows & Ubuntu, rather than go off and do something else. Then if something is not working I can maybe tell if an update is related. But Windows does not really tell me much where with Ubuntu I can see every file it is updating when I do it manually in terminal.

So you don't know whether Windows 10 can mess with automatic BIOS updates while wi-fi is enabled even after erasing Windows and installing Ubuntu?
Doesn't mouse cursor integration in BIOS on this ThinkPad show some potential BIOS vulnerabilities?

---

### Post by oldfred on 2023-01-08
If Windows not installed, then it cannot update UEFI.
But some systems only easily update UEFI from Windows and often UEFI update required for security reasons. 

Linux now has UEFI update, but vendors have to add to the database. And some are only now adding new systems.
[https://fwupd.org/vendorlist](https://fwupd.org/vendorlist) & 
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)

I recently bought a Dell since it was one of the first to be in fwupdate.

---

### Post by smith73 on 2023-01-10
So I've installed offline only the basic critical non-BIOS drivers for Windows 10, which don't require a restart. But for 2 critical drivers (touchpad and ssd) it was going to update firmware and need a restart, so I didn't install them do far. I am going to run MemTest86 for RAM in Windows and maybe  some Cinebench testing for hardware status, hope it won't affect the hardware (SSD at least) without some of the drivers.

So if Windows 10 will be in dual boot with Ubuntu 22.04 and if I install device firmware/BIOS drivers for Windows, Windows will use this firmware only while being installed and running?
Ubuntu installed in dual boot will probably install its own firmware/BIOS drivers, and will use them while running with Windows firmware installed being inactive?
If after some time I'll remove Windows completely and use Ubuntu only in single boot, so the previously installed Windows device firmware/BIOS drivers may still remain installed/active or can also be removed?

---

### Post by oldfred on 2023-01-10
Firmware is installed to the hardware. So UEFI firmware & SSD firmware as used by both systems. And you generally need those updates.

Drivers are system independent. Microsoft & vendors write drivers for their hardware. Very new systems often have a new driver or two that the Linux kernel & any Linux distribution has not developed, yet.

Some companies like Dell have newer drivers. But the do release then for use in Linux. But still if very new Dell, it may take 6 months or a year before everything is included in Linux Kernel & drivers in distributions.

---

### Post by smith73 on 2023-01-11
Someone "Explaining computers" on the internet mentioned regarding  Ubuntu 22.04, which I am going to install in dual boot so far (Ubuntu  Mate), that it has GRUB bootloader 2.06, which may not be set to probe  other operating systems. [Here]("https://askubuntu.com/questions/1404259/getting-grub-menu-to-work-on-dual-boot-ubuntu-22-04-windows-11-currently-boots")  there are some options to change GRUB to see other OSes by modifying  grub config file, but it seems a bit inconsequential to release GRUB  with an option to not see other OSes.

---

### Post by smith73 on 2023-01-11
> **oldfred said:**
> 
Some companies like Dell have newer drivers. But the do release then for use in Linux. But still if very new Dell, it may take 6 months or a year before everything is included in Linux Kernel & drivers in distributions.

I didn't choose Dell due to feeble top casing, absence of battery charging via USB-C and high pulse width modulation of the display (per a review on laptopmedia).

Open-source etc should pay more attention to writing drivers etc or speeding this up with a generative AI tool like ChatGPT and others. It can be trained 90% on code and documentation + the unique methodology. And many users probably have perfectly working old/unused computers to donate compute power in a distributed way for training.

---

### Post by oldfred on 2023-01-11
First thing I do is turn off os-prober.
With 2.06, they want it off for security reasons. It has to open and check every partition for an operating system. 

I have a lot of partitions and some old installs that I do not want in grub menu anyway. So I just copy the boot stanzas I want into 40_custom, so the just get added to grub menu. Much faster and easy once you know how.

---

