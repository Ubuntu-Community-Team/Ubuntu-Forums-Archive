---
title: "UEFI Secure Boot Off (booting Windows &amp; Linux)"
date: 2016-12-31
forum: Windows
---

### Post by kc_2 on 2016-12-31
Windows 10 Pro on M2 SSD, Ubuntu Server on SATA SSD.

Both are working fine now, except the mouse in linux.

Only going to use fluxbox, but mouse is being buggy.

Installed video card driver to fix it, but it is asking me to turn UEFI Secure Boot off.

I had some issues getting both systems to work before, it may have involved that setting.

Will Windows still boot if I turn secure boot off?

I need to get the mouse fully functioning in Linux.

---

### Post by oldfred on 2016-12-31
Windows should still work.

UEFI with secure boot requires that all boot files be secure. A driver that is integrated into the kernel then must be secure but that process is not. At least for now.

       [http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/](http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/)
 the whole UEFI thing is more about control than security

---

### Post by kc_2 on 2017-01-01
> **oldfred said:**
> Windows should still work.

UEFI with secure boot requires that all boot files be secure. A driver that is integrated into the kernel then must be secure but that process is not. At least for now.

       [http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/](http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/)
 the whole UEFI thing is more about control than security

IcheckedtheUEFI/BIOSsettingstoseeifIcouldmanuallydisableit,itdidn'thavetheoption.

Edit -

Okay so this forum software disallows use of spaces unless there's a character at the end.

I checked the UEFI/BIOS settings to see if I could manually disable it, it didn't have the option.

d

---

### Post by oldfred on 2017-01-01
Unless you have one of those crippled tablet type Windows 8 or 10 systems using 32 bit UEFI, Microsoft has required the vendors to offer users the option to turn off Secure Boot.

What brand/model system?

Some like Acer hide settings behind a UEFI password. 
Some have needed UEFI updates.

---

### Post by kc_2 on 2017-01-01
> **oldfred said:**
> Unless you have one of those crippled tablet type Windows 8 or 10 systems using 32 bit UEFI, Microsoft has required the vendors to offer users the option to turn off Secure Boot.

What brand/model system?

Some like Acer hide settings behind a UEFI password. 
Some have needed UEFI updates.

[https://pcpartpicker.com/user/KCmetro/saved/R3wcf7](https://pcpartpicker.com/user/KCmetro/saved/R3wcf7)

That's [Asus Z170-PRO ATX LGA1151 Motherboard]("https://pcpartpicker.com/product/LsX2FT/asus-motherboard-z170pro")

I googled it and found this
[http://www.technorms.com/45538/disable-enable-secure-boot-asus-motherboard-uefi-bios-utility](http://www.technorms.com/45538/disable-enable-secure-boot-asus-motherboard-uefi-bios-utility)

So I might try backing up those keys, deleting them (in effect "disabling" secure boot), and doing it a 2nd time just to make it go through, and will see how things go from there.

---

### Post by oldfred on 2017-01-01
Do not mess with the keys.

But Secure boot is called "Windows" or "Other". Detail is that if installing Windows 7 in UEFI mode you have to use "Other" as Windows 7 does not support secure boot.

---

### Post by kc_2 on 2017-01-03
> **oldfred said:**
> Do not mess with the keys.

But Secure boot is called "Windows" or "Other". Detail is that if installing Windows 7 in UEFI mode you have to use "Other" as Windows 7 does not support secure boot.

Thanks for the updated info. I'm running Window 10 pro, not sure if that makes a difference.

M2 SSD = Windows 10 Pro
SATA SSD = Ubuntu Server 16.10
SATA HDD x2 = RAID 1 storage

I took pictures of my uefi/bios setup with the same screens you provided screenshots of, but the pictures have not yet uploaded, so I'll just summarize the highlights of the current settings, or at least the ones that are from the same pages/screens that you posted:

boot menu
[LIST]
[*]boot\secure boot
[LIST]
[*]secure boot state = enabled
[*]platform key (pk) state = loaded
[*]os type = windows uefi mode (not currently set to "other os")
[*]key management
[/LIST]

[*]boot\csm
[LIST]
[*]launch csm = enabled
[*]boot device control = uefi and legacy oprom
[*]boot from network devices = legacy only
[*]boot from storage devices = uefi driver first
[*]boot from pci-e devices = uefi driver first
[/LIST]
[/LIST]
advanced menu
[LIST]
[*]advanced\pch storage configuration
[LIST]
[*]hyper kit mode = disabled
[*]sata controllers = enabled
[*]sata mode selection = raid
[*]smart self test = on
[*]m2 pcie storage raid support = disabled
[*]sata express pcie storage raid support = disabled
[*]pciex16_3 pcie storage raid support = disabled
[*]aggressive lpm support = enabled
[*](then below that is a list of all sata drive bays, I have 3 (1 SSD, 2 HDDs) and they're enabled)
[/LIST]
[/LIST]

---

### Post by oldfred on 2017-01-03
With my Asus Z97, I could only get it to boot in UEFI mode with UEFI only for USB. If Windows is UEFI, you do not want any Legacy/CSM settings. 
Best to have Secure boot off.

CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode      

You need to have drives in AHCI. Not sure how to do RAID with two drives not RAID. Ubuntu Desktop does not yet fully support RAID. If using FakeRAID, you may need to install using Server version.
 [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
dmraid was replaced by mdadm for handling FakeRAID in Ubuntu 14.04.
15.04 or later now uses mdadm to support intel fakeraids 
User who installed fakeRAID
How to install Ubuntu 14.04 in software fakeraid RAID 1 with Intel Z87 chipset mobo controller
[http://ubuntuforums.org/showthread.php?t=2229126](http://ubuntuforums.org/showthread.php?t=2229126) 

I turned off network boot as I was not going to ever use that.
I also turned off fast boot in UEFI.
If Windows 10 you need Windows fast start up off which is always on hibernation.

---

### Post by kc_2 on 2017-01-03
> **oldfred said:**
> With my Asus Z97, I could only get it to boot in UEFI mode with UEFI only for USB. If Windows is UEFI, you do not want any Legacy/CSM settings. 
Best to have Secure boot off.

CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode      

You need to have drives in AHCI. Not sure how to do RAID with two drives not RAID. Ubuntu Desktop does not yet fully support RAID. If using FakeRAID, you may need to install using Server version.
 [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
dmraid was replaced by mdadm for handling FakeRAID in Ubuntu 14.04.
15.04 or later now uses mdadm to support intel fakeraids 
User who installed fakeRAID
How to install Ubuntu 14.04 in software fakeraid RAID 1 with Intel Z87 chipset mobo controller
[http://ubuntuforums.org/showthread.php?t=2229126](http://ubuntuforums.org/showthread.php?t=2229126) 

I turned off network boot as I was not going to ever use that.
I also turned off fast boot in UEFI.
If Windows 10 you need Windows fast start up off which is always on hibernation.

Everything's working with the current settings, I'll have to take note of them in case anything breaks / stops working after changing them.

I am unable to set the motherboard to AHCI, it has to be RAID. I'm not using fakeraid / dmraid / mdadm / softraid, just the motherboard's raid. If I change the setting to AHCI then the drives won't work in combination with the windows drive, linux drive, and 2 extra drives that use the raid, while both windows and linux access that raid.

Some of the motherboard settings I can disable, like network boot, there's no point in having that on.

What do you mean by fast start up needing to be off and always on hibernation? I've read that once everything's set up it's good/okay to turn fast start on (from motherboard settings).

When I initially tried installing the nvidia driver, during the process it asked me if it could turn off secure boot. I might just go through the steps again, only this time let it actually turn secure boot off instead of me going into the uefi/bios settings and manually turning it off. I just hope that I'll be able to revert those changes if it ends up making it impossible to boot to windows and/or linux.

Part of this is also that I'm running SSDs. I can't remember exactly what it was, but something with the uefi/bios setup was a bit stubborn specifically because of the combination of hardware, features, and OSs.

Anyway, here goes nothing, hopefully the installer that disables secure boot won't break anything.

Edit -

Update, so I let the app that wanted to disable secure boot do its thing, and I am still able to boot into windows and linux.

Now, however, I'm unable to get xorg/gui to load at all in linux. I tried startx, startfluxbox, dpkg-reconfigure xorg, and no luck. When trying to load X it says cannot connect to it and it "passes display to null".

Also, the font size is about 2 to 3 times bigger now that I installed nividia-367 (also tried 370, no apparent difference, some searching found that 375 doesn't work with gtx 1070 video cards, recommending 367 or 370).

So the main thing now is getting X window interface to actually load again, then hopefully have a working mouse, then get that huge font size back down to the nice crisp, clean font that it used to be.

Here's what I did:

sudo apt-get purge nvidia-* xorg fluxbox
(wanted to start fresh)

sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
sudo apt-get install --no-install-recommends nvidia-367
reboot
sudo apt-get install xorg fluxbox
startx
(didn't load)
startfluxbox
(same, also tried the full paths from their bin directories)

Edit again -

This is the message:

[FONT=sans-serif]Error: Couldn't connect to XServer passing null display[/FONT]

(I'm googling it, hopefully will find something.)

Another edit -

One step forward, a couple steps back.

Mouse is working fine now, but...

I ran this as root:

Xorg :1 -configure
cp /root/xorg.conf/new /etc/X11/xorg.conf

I tried startx as normal user, it wouldn't load.

I tried startx as root, and it wouldn't load.

Then I replaced :1 with :0.

Still didn't work as normal user.

But now fluxbox successfully loads, but only when logged into root.

When I exit fluxbox, it displays the prompt again, but nothing that I would type would show up on screen, although I can still send commands.

So at this point it looks like I have the necessary driver, the mouse is working, I just need to configure the other things to work.

Next up, gotta figure out how to:

* Set it so normal user can startx
* Fix the issue of "invisible typing" after exiting X
* Change the non-GUI font back to the smaller font size

---

### Post by oldfred on 2017-01-03
There are two totally different settings. 

UEFI has fast boot. That assumes everything is the same configuration, no hardware changes. It skips all hardware checks and immediately boots. But that is so fast you do not have time to press the key to get into UEFI. It assumes you can get into UEFI from Windows, but when Windows breaks, you can have major issues. I set mine to 3 sec delay, just to have time to press a key.

Windows has fast start up. That is just hibernation. Windows does not really boot faster, but enables hibernation to make users think they have improved boot time. But all NTFS partitions are in effect permanently mounted. The Linux NTFS driver will not open hibernated NTFS partitions as read/write to prevent damage.
 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html) 


BIOS RAID is FakeRAID.

Have you totally purged the older nVidia driver before installing a new driver. Otherwise you have conflicts.
[http://www.phoronix.com/scan.php?page=article&item=nvidia-gtx-1070&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia-gtx-1070&num=1)
I thought the issues with nVidia were with the dual video/optimus video systems on laptops. And they need the newer xorg-xserver 1.1.

---

### Post by kc_2 on 2017-01-04
> **oldfred said:**
> There are two totally different settings. 

UEFI has fast boot. That assumes everything is the same configuration, no hardware changes. It skips all hardware checks and immediately boots. But that is so fast you do not have time to press the key to get into UEFI. It assumes you can get into UEFI from Windows, but when Windows breaks, you can have major issues. I set mine to 3 sec delay, just to have time to press a key.

Windows has fast start up. That is just hibernation. Windows does not really boot faster, but enables hibernation to make users think they have improved boot time. But all NTFS partitions are in effect permanently mounted. The Linux NTFS driver will not open hibernated NTFS partitions as read/write to prevent damage.
 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html) 


BIOS RAID is FakeRAID.

Have you totally purged the older nVidia driver before installing a new driver. Otherwise you have conflicts.
[http://www.phoronix.com/scan.php?page=article&item=nvidia-gtx-1070&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia-gtx-1070&num=1)
I thought the issues with nVidia were with the dual video/optimus video systems on laptops. And they need the newer xorg-xserver 1.1.

I have a couple or few seconds on boot to get into setup.

Whenever I use the windows side of the computer and if I know I will again later, I just put it to sleep. Otherwise, once I have the linux side set up, I'm going to leave it booted up most of or all the time. Once I get the basic issues resolved (with the mouse issue now leading to general GUI & CLI issues), I'll be able to finally dig into the server setup. Will also use the linux side of the computer for personal computer purposes, will run either lxd+gui or a vm for that, while running lxd containers for server purposes.

Anyway, getting back to point, I did a purge of nvidia before installing the new driver.

[COLOR=#000000]sudo apt-get purge nvidia-* xorg fluxbox[/COLOR]

I've done some googling on the current issues (1. normal user cannot startx, 2. invisible typing outside the GUI, 3. large font outside the GUI), but haven't had a chance to try anything yet.

---

### Post by oldfred on 2017-01-04
I had large fonts, oversize screen until I installed a nVidia driver, but that was several versions ago. I was able to right click on screen, get to System Settings and install driver from there.
 My nVidia card was newer then and now that same card just works even with the open source drivers.

---

### Post by kc_2 on 2017-01-05
> **oldfred said:**
> I had large fonts, oversize screen until I installed a nVidia driver, but that was several versions ago. I was able to right click on screen, get to System Settings and install driver from there.
 My nVidia card was newer then and now that same card just works even with the open source drivers.

Sorry, I meant I get the large fonts from the CLI before loading GUI. When first booting computer, before running startx. That font used to be smaller, until adding the nvidia driver. Maybe I can install an open source driver instead. Unless CLI and GUI are using different video drivers.

---

### Post by oldfred on 2017-01-05
That may be grub settings.
Grub tries to use the gfxmode of system. But you can force it to match your size screen or whatever video driver supports.

       Details on settings in /etc/default/grub
 info -f grub -n 'Simple configuration'
> `GRUB_GFXMODE'

  Set the resolution used on the `gfxterm' graphical terminal.  Note
 that you can only use modes which your graphics card supports via
 VESA BIOS Extensions (VBE), so for example native LCD panel
 resolutions may not be available.  The default is `auto', which
 tries to select a preferred resolution.  *Note gfxmode::. 
     From a grub command line to see available settings pressing <c> & escape to get back to menu
vbeinfo 

Then once booted change mode.

 sudo nano /etc/default/grub 
      
 sudo update-grub 
    


   #GRUB_GFXMODE=640x480
GRUB_GFXMODE=1366x768 or whatever your monitor is or what vbeinfo when booting at grub menu said works.

---

