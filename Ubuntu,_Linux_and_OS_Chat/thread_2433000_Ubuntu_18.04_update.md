---
title: "Ubuntu 18.04 update"
date: 2019-12-12
forum: Ubuntu, Linux and OS Chat
---

### Post by P-I H on 2019-12-12
I have a desktop system with three installations
- Main installation Ubuntu 19.10 on /dev/nvme0n1
- "Back up" installation Ubuntu 18.04 LTS on /dev/sda
- "Interesting" installation Fedora 31 on /dev/sdb
I mainly use the Ubuntu 19.10 system, but now and then updates the Ubuntu 18.04 installation.
The two last two updates of Ubuntu 18.04 has included updates of grub and kernel, that required reboots.
In both these cases grub has made changes in the UEFI BIOS.
The last update made the computer unbootable and the second last update made the computer boot to Ubuntu 18.04.
As this have happened several times I'm prepared and know how to change BIOS to boot into the wanted system.
I don't know if this is related to my installation practice. As it's not possible to define where grub shall be installed during the installation, I always disconnect all drives except the installation drive.

How do you stop grub from doing unwanted changes?

---

### Post by kansasnoob on 2019-12-12
I have not found a really great way of controlling this behavior on UEFI multi-boot systems. What happens is each time grub is updated the process "remembers" how and where grub was originally installed. On older msdos/mbr systems this could be fixed using 'dpkg-reconfigure'. I'll try to explain what happens. Just remember this is CHAT, not a how to!

Lets say you have a dual boot with Windows 10 and Ubuntu 18.04, and you have grub controlling the boot process. Typically you should encounter no problem unless a Windows update goes wild. I've actually never had a problem but I've read reports from others saying Windows automatically took control of boot again. Since I've never experienced that problem I can't comment. 

I should maybe mention that I personally prefer using SuperGRUB2 to boot a Linux system and repair grub from within that system rather than just using "boot repair". I'm kind of crazy that way - like I must always be in charge rather than depending on something automated. I have had to reinstall Windows with Ubuntu already installed and in those cases I'll undoubtedly have to boot Ubuntu afterwards using SuperGRUB2 and then reinstall grub.

The first thing I do after that is run 'dpkg -l | grep grub | grep ii' to find out what exact grub package is in control - this will typically be "grub-pc" on msdos/mbr machines but on UEFI/gpt machines it'll typically be "grub-efi-amd64". So on older pre-EFI machines after seeing that grub-pc is the correct package I'd run 'sudo dpkg-reconfigure grub-pc' and then using the tab key and space bar I'd be able to select where to put grub - typically the mbr.

On pre-EFI multi-boot systems you'd use 'sudo dpkg-reconfigure grub-pc' to change which Linux system was in charge of the boot process by setting the controlling system to use the mbr but repeat the process on all other systems and set them to install grub to their own pbr (partition they're installed on). Then future updates of those "non-controlling" systems would leave the mbr alone.

UEFI is a totally different animal. Before getting into it any further I'd like to say that before messing with a UEFI system at all I always create a full backup of the existing /boot/efi partition using Gparted. I literally use a Gparted or System Rescue disc to run Gparted and copy the entire fat32 partition to a removable drive until I'm done messing around. Then, just in case I totally hose things I can replace that partition with the back-up (making sure I use the same UUID).

So on with multi-boot UEFI systems. Lets say you have a Win 10 / Ubuntu 18.04 dual boot and add 19.10. Chances are 19.10 will be in charge of booting once complete. You can certainly change that by booting 18.04 and using 'dpk-reconfigure' to put it back in charge. Remember to first check which grub package is in control. And the options offered are kind of scary! I always just accept ALL defaults. But I have to FIX this every time the secondary systems grub gets updated, either due to grub updates themselves or kernel updates.

Maybe if oldfred happens to pop in he can get both of our heads straight :)

---

### Post by oldfred on 2019-12-13
Did not know Supergrub would boot UEFI system, or is it booting it in BIOS mode? I used to use it on my old BIOS systems.
 I thought you had to use its newer rescatux version.
I use rEFInd on an old tiny flash drive that had no other use as my last resort boot method. But still have supergrub and tools as ISO that I directly boot from a grub loopmount on a flash drive.

I use my workaround to change which ESP a second UEFI install uses. And since regularly installing Ubuntu, but using 18.04 on sda as main working install, install grub to ESP on sdb. 
You also can install with ubiquity -b to not install a boot loader (have not tested recently).
       
Posted work around to manually unmount & mount correct ESP during install
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
While it then installs to ESP on sdb, it still has ESP on sda in fstab (how does it even find that?) which I have to also update. Just about required for external drives.

Before finding the work around, I use to back up ESP, but then found it really was only /EFI/ubuntu/grub.cfg and the three line configfile that needed to be restored or edited. 

But have to change fstab mount of fstab from 0777 to defaults to allow me to edit it. After 14.04 Ubuntu changed from defaults to 0777, I presume for security. I may go back and start using 0777, but am so used to being able to easily change ESP entries, it will be a hassle. Boot-Repair also edits fstab entry for ESP. 
 
I have so many installs, every 9 months anther install or two go obsolete, but I may not yet overwrite it with a new test. I use 25GB for / so space for lots of installs. But first thing I do is turn off os-prober in grub and add my own 40_custom to boot those installs that I may still be experimenting with. When os-prober is on, it takes a long time to find & add all the installs.

---

### Post by rbmorse on 2019-12-13
If you have an EFI machine, rEFInd will keep various installed o/s all sorted and will boot a specific linux kernel directly, if asked. 

You may occasionally have to enter EFI setup to make it the default boot manager again after an update.

---

### Post by kansasnoob on 2019-12-13
> **oldfred said:**
> Did not know Supergrub would boot UEFI system, or is it booting it in BIOS mode? I used to use it on my old BIOS systems.
 I thought you had to use its newer rescatux version.
I use rEFInd on an old tiny flash drive that had no other use as my last resort boot method. But still have supergrub and tools as ISO that I directly boot from a grub loopmount on a flash drive.

I use my workaround to change which ESP a second UEFI install uses. And since regularly installing Ubuntu, but using 18.04 on sda as main working install, install grub to ESP on sdb. 
You also can install with ubiquity -b to not install a boot loader (have not tested recently).
       
Posted work around to manually unmount & mount correct ESP during install
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
While it then installs to ESP on sdb, it still has ESP on sda in fstab (how does it even find that?) which I have to also update. Just about required for external drives.

Before finding the work around, I use to back up ESP, but then found it really was only /EFI/ubuntu/grub.cfg and the three line configfile that needed to be restored or edited. 

But have to change fstab mount of fstab from 0777 to defaults to allow me to edit it. After 14.04 Ubuntu changed from defaults to 0777, I presume for security. I may go back and start using 0777, but am so used to being able to easily change ESP entries, it will be a hassle. Boot-Repair also edits fstab entry for ESP. 
 
I have so many installs, every 9 months anther install or two go obsolete, but I may not yet overwrite it with a new test. I use 25GB for / so space for lots of installs. But first thing I do is turn off os-prober in grub and add my own 40_custom to boot those installs that I may still be experimenting with. When os-prober is on, it takes a long time to find & add all the installs.

SuperGRUB2 now does provide UEFI support but must be booted in UEFI mode. Most of the puters I've fiddled with use F11 to display boot options and the UEFI boot menu will allow booting *the optical drive* in either non-efi or UEFI mode. Then, as I recall, there's an option to boot manually in the SuperGRUB2 menu after which you can select to boot using any of the preferred kernels. I've never tried booting Windows that way. Oh, the disc version I have is 2.04. I've never tried running (or even creating) a SuperGRUB2 live USB. There are a multitude of options included on the disc but I only use it to boot the preferred OS.

---

### Post by P-I H on 2019-12-14
I will install rEFInd and try it out.
See if it works on an older non EFI computer and on a computer with EFI support.
After Christmas eve I'm going to change motherboard on my main computer to an Asus ROG Strix B450-F Gaming motherboard with 2 NVme connectors. It's quite difficult to remove NVme drives from the motherboard. You stand the risk to loose the tiny screw and I really need to be able to control the boot device.

---

### Post by oldfred on 2019-12-14
Many motherboards need UEFI updates.
And check manual if two NVMe drives supported with your model.

       Asrock B450M Steel Legend - turn UEFI Secure Boot off
[https://askubuntu.com/questions/1183093/ubuntu-corrupts-bios-on-ryzen-3000-machine](https://askubuntu.com/questions/1183093/ubuntu-corrupts-bios-on-ryzen-3000-machine)
Vega GPU is built into the CPU, then the M.2_2 socket cannot be used. 
[https://ubuntuforums.org/showthread.php?t=2424099&p=13877199#post13877199](https://ubuntuforums.org/showthread.php?t=2424099&p=13877199#post13877199)
Asus B450-F Clock speeds
[https://ubuntuforums.org/showthread.php?t=2414502&p=13845363#post13845363](https://ubuntuforums.org/showthread.php?t=2414502&p=13845363#post13845363)

---

### Post by P-I H on 2019-12-15
Thanks for the information.
My testing didn't turn out as expected. The motherboard I used had a setting for EFI, but it wasn't possible to do an UEFI boot, even though I updated BIOS.
However there seems to be a way to force installation of grub to a specific drive, without the necessity to define all partitions.
In the installation you 
- Select Erase disk and install Ubuntu
- Click Back
- Select Something else
- Select the Device for boot loader installation
- Click Back
- Select Erase disk and install Ubuntu again
- Click Install Now
Tried this on a computer with sda, sdb and sdc. Installed to sdc and selected sdc as the Device for boot loader installation.
**This didn't work in a computer with uefi boot**

---

