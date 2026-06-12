---
title: "Dual boot on a HP machine using UEFI"
date: 2018-05-25
forum: Ubuntu, Linux and OS Chat
---

### Post by BarryBKS on 2018-05-25
[SIZE=3]So for those of you who are trying to install Ubuntu in a **dual boot environment**, on a **HP machine using UEFI**, please take note:[/SIZE]

If your HP machine is configured to use UEFI, it will always boot into Windows. The "OS Boot Manager" is hard coded to load the Microsoft EFI file and will always run before any other local EFI files.
This is hard coded into the HP UEFI Firmware and no mater what changes you make using efibootmgr, BCDedit or boot-repair, you cannot change it.

The only way to "cheat" this is to replace the Windows efi file with the grubx64.efi file, but leave it with the windows file name, as that is what the HP UEFI Firmware looks for.
This will work, but take note that Windows Updates may reset this file and you will lose your option to boot into Grub.

Booting the HP machine and pressing F9 will show you Ubuntu in the UEFI boot options, but the boot order settings in the BIOS (F10) will not show you Ubuntu and you cannot add it as this is a hard coded list in the BIOS.

The only way to get a correct dual boot is to install both Windows and Ubuntu on to a hard disk that is configured with the BIOS set to Legacy mode.

Under Legacy mode, Grub installs itself onto the MBR partition at the start of the hard disk, which means it is seen before either of the actual OS's. This is because the "OS Boot Manager" looks at the start of the hard disk in legacy mode.

If you are hoping to dual boot your HP machine with the pre-installed Windows, then it is unlikely that you will be able to.

It is not possible to just turn UEFI mode off and then boot your existing installation of Windows as the BIOS mode is dependent on the configuration of the hard disk. If you try to do this, you will get a blank screen or a BIOS message saying no boot loader found.

To switch form UEFI to Legacy will require a complete wipe of your hard disk, change the partition table type from GPT (UEFI) to MBR (Legacy) and then re-installing Windows. ([COLOR="#FF0000"]Doing this will destroy all your personal data as well[/COLOR]).  

I have not managed to get an answer yet from HP as to why they have built their UEFI Firmware to work in this way. I have noticed that HP forum support reps are now saying that "HP will only support the operating system that was shipped with the hardware", to avoid having to answer this issue.

Keep complaining to HP about this issue. The more complaints they get, the more likely they are to do something about it, before Legacy gets removed from their BIOS completely.

I hope this has been of help in explaining why you are unable to get Ubuntu to install in dual boot mode with your UEFI install of Windows, on your HP machine.

---

### Post by oldfred on 2018-05-25
Many with HP have installed in UEFI dual boot mode.
And BIOS/MBR is an option, but your Windows UEFI Product will not work for a new Windows install as it is in UEFI.
And yes, HP will not let you set anything other than "Windows Boot Manger" as default boot.

But there are a variety of work arounds, depending on configuration.
       Copy shimx64.efi to /EFI/Boot/bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)
Boot-Repair should automatically do copy file with 'use standard EFI file':
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
Sony, HP & others workarounds:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
Boot-Repair should automatically do copy file with 'use standard EFI file':
[http://askubuntu.com/questions/582073/dual-boot-but-only-windows-boots/582114#582114](http://askubuntu.com/questions/582073/dual-boot-but-only-windows-boots/582114#582114) 
    
       HP UEFI boot order change with efibootmgr does not stick, but change in HP's UEFI does work
[https://ubuntuforums.org/showthread.php?t=2390309](https://ubuntuforums.org/showthread.php?t=2390309)
HP 11m reinstall Windows & dual boot with Ubuntu 16.04
[https://ubuntuforums.org/showthread.php?t=2389104](https://ubuntuforums.org/showthread.php?t=2389104)
Probook G4 470 Ubuntu works fine with UEFI and secure boot. 
[https://ubuntuforums.org/showthread.php?t=2381663](https://ubuntuforums.org/showthread.php?t=2381663) 
    
Boot-Repair now copies shimx64.efi to /EFI/Boot/bootx64.efi to use as fallback or hard drive boot entry. One of the more often used work arounds.
Before Boot-Repair did copy, many manually copied files.
       Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)
HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

---

### Post by james.mc on 2019-01-23
It looks like HP was listening because they cleaned up dual booting using UEFI. On January 11, 2019, I received my new 17” HP Envy laptop with Windows 10 Home edition. Until then, my workaday computer was a 2007 HP Media Centre laptop running a quint-boot Ubuntu 10.04 with Windows XP, Vista, 7 and 10. Researching how things have changed, particularly with UEFI and HP, I was dreading having to figure out how to make the dual boot work on my new laptop. However, it couldn’t have been easier.

I used Rufus to create a live USB of Ubuntu 18.04.1; I used Windows disk management to create 32MB of free space on my hard drive; I used the Ubuntu installer to create a 2MB logical swap partition and a 30MB Ext4 logical partition for Ubuntu and to also assign the “Windows Boot Manager” partition to the “Device for boot loader installation” for the Ubuntu partition; and then installed Ubuntu.

Now when I startup, my laptop will still boot normally into Windows 10. To boot Ubuntu, I tap the F9 key once every second, to reach the boot option menu. There the Ubuntu OS boot manager (UEFI) is displayed as an option. I press the down arrow to highlight it and press enter. Next the GRUB menu appears and I hit enter to start Ubuntu. Unbelievable! Thank you HP.

---

### Post by mastablasta on 2019-01-24
probably it also depends on the model. 
UEFI is running the booting so that would mean that grub reboot is not an option, right? when booting windows it will never reach grub, correct?

---

### Post by yetimon_64 on 2019-01-24
> **james.mc said:**
> ... However, it couldn&#8217;t have been easier.....

> **mastablasta said:**
> probably it also depends on the model...

I think it does depend on the model. It seems the HP Envy 17 model is different to the reports of problems with doing dual boots on other HP devices.

I set this HP Envy 17 up as a dual boot with win 8 a couple of years ago and didn't seem to hit any problems requiring renaming boot files or anything of the like. I managed to install trusty in a dual boot with win 8 and even got the grub bootloader to work without any hitches for both my Linux and Windows installations. Windows updates never touched the bootloader I installed and the machine didn't have the Windows only bootloader requirement with Win 8 (though Win 10 may be a bit stricter, I don't know for sure about that). I have my hard drive as a GPT drive and I use UEFI booting and didn't hit any snags when setting it all up. Since going Linux only on this machine I've even turned off the secure boot option in the settings and it still runs fine.

In the time since I've set it up I have even removed Windows altogether and now dual boot multiple Linux installs using the grub bootloader and it still runs smoothly.

@james.mc, It seems, like me, you have been lucky enough to snag a good HP model for dual booting on. Though it is not because of any recent changes by HP, it has been like that here for the last couple of years.

---

### Post by james.mc on 2019-01-26
My HP Envy model no. is bw0011nr.

@mastablasta: When booting Windows it never reaches GRUB which I like because it's quicker than reaching GRUB first and then selecting Windows, which is how my older laptop functioned. But now when I want to boot Ubuntu, there's extra steps, but I get there.

---

### Post by mastablasta on 2019-01-28
ok though so. well i setup Kubuntu in MBR with old BIOS on old PC. windows XP stayed on it's separate disk so i can boot it directly from BIOS boot menu. it will be used mostly for old games. anyway Kubuntu boots in 30-45 seconds, windows takes 10 minutes to boot (firewall and antivirus take a loooong time to load). anyway i setup an icon in linux that uses grub to reboot to windows once. so when kids want to play some windows games they would just double click the icon and wait for windows to load. after they are done, they just have to reboot and they are back to linux. 

the reasons for this extra effort are:
1.  ease of use in dual boot.
2. nvidia throws primary display on living room TV instead of on VGA output where the monitor is. so system needs to first boot before i can see what is going on. it does the same in windows and it does it even if you unplug the tv form the GPU card. weird. i mean why output on something that doesn't have any monitor connected to it.

---

### Post by james.mc on 2019-01-30
@mastablasta: From pushing the start button until the desktop appears, Windows boots in 15 seconds (including entering my user login password) and Ubuntu boots in 23 seconds (including repeated pressing of F9 and selecting Ubuntu in the boot manager and then in GRUB).

---

### Post by mastablasta on 2019-01-30
must be using SSD, maybe even fastboot. i can't get win 10 on work PC to boot that fast (HDD, laptop with an i3 CPU). i think it takes at least a minute and then some to load all the extra stuff we have to have installed.

my home PC is a single core from 2003 with a hard disk. so yeah, it takes a while to load all the extra stuff :)

the win7 pc has an issue if you are not using it for a while it would run the anti malware scan which takes up all CPU so that one too nowadays takes 8 minutes to boot sometimes. but to be fair although newer CPU the power is quite similar to the old one. still both are more than fine for an old game or two and for schoolwork and office stuff.

---

### Post by jeremy31 on 2019-01-30
I have a new HP Laptop 15-bs1xx running dual boot with Win 10 in UEFI and all I had to do was go into UEFI settings and change the OS boot option from Windows to Ubuntu.  Now that I cloned the install on to a SSD it even boots Win 10 in about 15 seconds

---

