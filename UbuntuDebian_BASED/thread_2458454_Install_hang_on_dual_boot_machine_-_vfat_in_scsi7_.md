---
title: "Install hang on dual boot machine - vfat in scsi7 partition #2 (sdb) at /boot/efi"
date: 2021-02-24
forum: Ubuntu/Debian BASED
---

### Post by foo2bar on 2021-02-24
Hello everybody

I'm hoping someone can point me in the right direction to fix my problem. 
I have been a long time user of ubuntu and have many single and dual boot machines. I was attempting to upgrade a dual boot laptop from vanilla ubuntu 16.04 to 20.10 by **replacing** 16.04 with 20.10 **ubuntuunity **(I just don't like gnome - it's way too clunky after having used unity for ages). I know it's not a fully fledged official ubuntu version ... but I'm taking a punt here so please be kind!

As I wanted to preserve the windows10 and the linux /home partition, I chose "something else" when reaching the section on partitioning the disk.

 Before installation I had the following setup:

sda1: physical partition; ntfs; system reserved; ~500MB
sda2: physical partition; nrfs; windows os; ~30GB
sda3: extended partition containing[INDENT]sda5: logical partition; ext4; / (root partition); 18GB
[/INDENT]
[INDENT]    sda6: logical partition; linux swap
[/INDENT]
[INDENT]sda7: logical partition; ext4; /home; 93GB
[/INDENT]
 sda4: physical partition; ntfs; 69GB

I chose sda5 as the location for the new root partition (with formatting), sda6 as the new location for the swap partition and sda7 as the location for /home (no formatting). For the device location of  the boot loader I left it as the default /dev/sda. 

Clicking through onto the next page to enter the locale (UK) there as a popup stating

> "The attempt to mount a file system with type vfat in scsi7 (0,0,0) partition #2 (sdb) at /boot/efi failed."

I carried on regardless and it just sat there for ages doing nothing in particular. Having a read around, it seems others had a similar problem ages ago (2012) whereby attempting to preserve /home by choosing to not format it was a problem (something about a race condition /home not being unounted in time). I tried the work around (don't target /home in the installation and add in after the installation). That didn't work either.

I then chose to delete sda5, sda6, sda7 and then recreate them. That didn't work either. I then deleted sda5, sda6, sda7 but only recreated sda5 and sda6 - still no good.

I have tried mounting all ntfs partitions on sda manually using disks and gparted - they mount successfully.

The strange thing is that the message refers to "partition #2 (sdb)". sdb is the usb stick and partition 2 is the efi boot partition - all created from the iso I had to write the iso using dd as startupdisk creator didn't recognise it).

This is the state of the machine at the moment.

ubuntu@ubuntu:~$ blkid | grep sda
/dev/sda1: LABEL="System Reserved" BLOCK_SIZE="512" UUID="D464179864177D04" TYPE="ntfs" PARTUUID="7bb10d49-01"
/dev/sda2: LABEL="Windows OS" BLOCK_SIZE="512" UUID="6C96350C9634D7F2" TYPE="ntfs" PARTUUID="7bb10d49-02"
/dev/sda4: LABEL="Shared" BLOCK_SIZE="512" UUID="6DCF9AAF59C48098" TYPE="ntfs" PARTUUID="7bb10d49-04"
/dev/sda5: UUID="a95baff6-3c41-47c4-8ef9-06dbcdc15e1a" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="7bb10d49-05"
/dev/sda6: UUID="c2ce3c09-4d65-41f8-839d-43ee599028a3" TYPE="swap" PARTUUID="7bb10d49-06"
ubuntu@ubuntu:~$ blkid | grep sdb
/dev/sdb2: SEC_TYPE="msdos" UUID="6FFF-D6F6" BLOCK_SIZE="512" TYPE="vfat" PARTLABEL="EFI boot partition" PARTUUID="a8da6173-d491-4958-b4c2-6e7bc09402b0"
/dev/sdb3: BLOCK_SIZE="2048" LABEL="ISOIMAGE" TYPE="hfsplus" PARTLABEL="HFSPLUS" PARTUUID="a8da6173-d491-4958-b4c3-6e7bc09402b0"
/dev/sdb5: LABEL="writable" UUID="37896b39-5cf2-4551-a619-7a64cc170e4a" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="36ae7aa9-a693-b84a-9f7c-a758c7f40dd7"

Ideas anyone? (apart from go and ask the ubuntuunity team)

Thanks

---

### Post by tea for one on 2021-02-25
It looks like you have booted the Ubuntu Unity installer in UEFI mode but you do not have an EFI partition.

Possibly the Ubuntu Unity installer is different to the Ubuntu installer?
Which Windows version in your dual boot?
Why do you have extended partitions (sda4 to sda6)?

Windows 10 requires UEFI mode with GPT, which allows more than 4 primary partitions.

I would suggest that you back up all your personal data and re-install both systems using UEFI mode and GPT.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Have you also opened a thread here [https://www.foss.ubuntuunity.org/forums/discussion/46/installation-problem-on-dual-boot-machine?](https://www.foss.ubuntuunity.org/forums/discussion/46/installation-problem-on-dual-boot-machine?)

---

### Post by howefield on 2021-02-25
Thread moved to the "*Ubuntu/Debian BASED*" forum for a better fit.

---

### Post by foo2bar on 2021-02-25
> **tea for one said:**
> It looks like you have booted the Ubuntu Unity installer in UEFI mode but you do not have an EFI partition.

Possibly the Ubuntu Unity installer is different to the Ubuntu installer?
Which Windows version in your dual boot?
Why do you have extended partitions (sda4 to sda6)?

Windows 10 requires UEFI mode with GPT, which allows more than 4 primary partitions.

I would suggest that you back up all your personal data and re-install both systems using UEFI mode and GPT.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Have you also opened a thread here [https://www.foss.ubuntuunity.org/forums/discussion/46/installation-problem-on-dual-boot-machine?](https://www.foss.ubuntuunity.org/forums/discussion/46/installation-problem-on-dual-boot-machine?)

I don't think I have changed the way that I boot the machine - or rather - I haven't gone into the bios and changed anything. Before I started installation, both windows10 and ubuntu booted fine. I just chose which one I wanted to launch at the grub screen.
The machine boots (or rather it did before it broke) into windows10 or ubuntu 16.04.

I just used the iso from [http://linux.darkpenguin.net/distros/ubuntu-unity/20.10/](http://linux.darkpenguin.net/distros/ubuntu-unity/20.10/) which you get to from [https://ubuntuunity.org/download/](https://ubuntuunity.org/download/) and flashed a 4GB usb stick using dd. I did check the md5 hash and it matched the iso.

I can't remember why I used extended partitions - it was such a long time ago that I worked on this machine so I can't remember the rationale - apart from probably because I wanted more than 4 partitions to segment the linux installation. Maybe at the time I didn't realise that GPT didn't limit the number of partitions to 4.

Ideally I would do the backup ... but i'm a bit worried now that I won't be able to restore windows10. I recall that this machine had windows10 as a result of the free upgrade from windows7 to windows10 - so there are no discs etc.

Regarding the duplicate thread - yes - I opened that there not knowing whether the two communities would "talk" to each other so thought I would increase my chance of getting a reply.

gparted does report that the partition table is of type msdos rather than GPT. I've checked the BIOS and UEFI boot support has been disabled - so that matches up with the partition table type being MSDOS.

I've got several machines which are all partitioned in the same way and in which both windows10 and ubuntu co-exist happily.

---

### Post by foo2bar on 2021-02-25
Just thinking about your first response

> It looks like you have booted the Ubuntu Unity installer in UEFI mode but you do not have an EFI partition.


Are you saying that the USB stick with ununtuunity (sdb) has been booted as if it's in UEFI mode? I don't see how that is possible given that the BIOS has UEFI mode disabled.
Just had a look at gparted again and sda1 has the boot flag set. All things point to sda being in legacy/BIOS mode - not UEFI.

Do different devices get booted using different schemes? e.g. SDD/hard drives are booted as BIOS/legacy mode but external USBs are booted as UEFI mode?
I did follow the link [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) and it showed the different screens that would show in the boot sequence highlighting the difference between legacy vs UEFI mode. When the USB stick boots, it looks like the screen for UEFI booting.

---

### Post by oldfred on 2021-02-25
If Windows is in BIOS boot mode on MBR drive, you need to install Ubuntu in BIOS boot mode.
But Microsoft has required vendors to install in UEFI mode to gpt drives since 2012.
But upgrades from Windows 7 were usually still BIOS/MBR.

There was some issue with 20.10 where it always wants an ESP - efi system partition.
I might try 20.04 since it is LTS and you do not need newest kernel & drivers for your older hardware.
Or just add a tiny FAT32 partition with esp flag, to make installer happy.

---

### Post by tea for one on 2021-02-25
Legacy bios mode is not ideal for Windows 10 and i still suggest that you back up and install both Windows and Ubuntu Unity in UEFI mode with GPT.

You can download a copy of Windows 10 direct from Microsoft and I would hope that your existing activation key will be OK.
If Windows is your priority, then you should check with Microsoft and/or a Windows forum about activating a Windows 10 installation with a Windows 7 key.

---

### Post by foo2bar on 2021-02-25
Activation key?
I foolishly just went ahead with the installation (thinking it would be fine) without booting into windows to get the product/installation key. I'll not make that mistake again.

---

### Post by foo2bar on 2021-02-25
> **oldfred said:**
> If Windows is in BIOS boot mode on MBR drive, you need to install Ubuntu in BIOS boot mode.
But Microsoft has required vendors to install in UEFI mode to gpt drives since 2012.
But upgrades from Windows 7 were usually still BIOS/MBR.

There was some issue with 20.10 where it always wants an ESP - efi system partition.
I might try 20.04 since it is LTS and you do not need newest kernel & drivers for your older hardware.
Or just add a tiny FAT32 partition with esp flag, to make installer happy.

Just to rule out whether it is a quirk with ubuntuunity's installer versus regular ubuntu, I am going to try the installation with just ubuntu 20.10 and see if that coughs with the same problem.

If I was going to do the last suggestion 

> Or just add a tiny FAT32 partition with esp flag, to make installer happy, could that partition be anywhere?

---

### Post by foo2bar on 2021-02-25
I have just flashed a USB stick with ubuntu 20.10.
On boot I did get a message saying "1 error was found" whilst checking the files. I carried on anyway (!), partitioned the disk as I wanted (sda5=/,  sda6=swap, sda7=/home) and was able to progress to the page where you select your locale without any error. To all intents and purposes, the installation was fine until I got the following error:

> Executing 'grub-install /dev/sda' failed.
This is a fatal error.

I was so pleased that it had managed to progress without throwing up the  previous error (which made me conclude there is a difference between  ubuntu's and ubuntuunity's installer) but success was short lived.

I had a look at syslog which reports the following just before the error:

> ubuntu grub-installer: info: architecture: amd64/efi
...
ubuntu ubiquity: volume group "sda" not found
ubuntu ubiquity: cannot process volume group sda
...
ubuntu grub-installer: info: identified partition label for /dev/sda5: msdos
ubuntu grub-installer: info: installing rub on '/dev/sda'
...
ubuntu grub-installer: info: Running chroot /target grub-install --force --target x86_64-efi "/dev/sda"
ubuntu grub-installer: info: Installing for x86_64-efi platform
ubuntu grub-installer: grub-install: error: cannot copy  '/usr/lib/grub/x86_64-efi-wigned/grubx64.efi.signed' to  '/boot/efi/EFI/ubuntu/grubx64.efi': No space left on device
ubuntu grub-installer: error: Running 'grub-install --force --target x86_64-efi "/dev/sda"' failed


I have no idea what's going on here - because the BIOS is in legacy mode  and sda is MSDOS not GPT - so why on earth is it trying to install  grubx64.efi?

And which partition is it targeting for /boot/efi/EFI/ubuntu/grubx64.efi? sda1 (the windows reserved partition) or sda5 which is **meant** to be /?

---

### Post by rbmorse on 2021-02-25
You can get the Windows activation key that's in use from within the running Windows session.  I forget the specific steps, but I do know it's possible.  A Google or DDG search should provide in short order.

[https://answers.microsoft.com/en-us/windows/forum/windows_10-win_licensing/extracting-product-key-for-windows-10/738e9e25-d13f-4e86-a8ed-c3d57a72e6fe](https://answers.microsoft.com/en-us/windows/forum/windows_10-win_licensing/extracting-product-key-for-windows-10/738e9e25-d13f-4e86-a8ed-c3d57a72e6fe)  might help.

---

### Post by foo2bar on 2021-02-25
> **rbmorse said:**
> You can get the Windows activation key that's in use from within the running Windows session.  I forget the specific steps, but I do know it's possible.  A Google or DDG search should provide in short order.

[https://answers.microsoft.com/en-us/windows/forum/windows_10-win_licensing/extracting-product-key-for-windows-10/738e9e25-d13f-4e86-a8ed-c3d57a72e6fe](https://answers.microsoft.com/en-us/windows/forum/windows_10-win_licensing/extracting-product-key-for-windows-10/738e9e25-d13f-4e86-a8ed-c3d57a72e6fe)  might help.

This machine is one of those that was upgraded from windows7/8 to windows10 for free around 2016. I've just been talking with m$ online and apparently, it's not possible to reinstall windows10 onto this machine using the original windows7/8 product keys! I'd have to buy a new licence!! And like hell I'm going to do that!

I'm convinced the person I was speaking with didn't know their gluteus maximus from their oleocranon.

On the plus side, even though ubuntu carped during installation, grub was restored and I was able to boot into windows. However, I wasn't able to boot into ubuntu 20.10. Can't remember the message. I've made the mistake to booting into windows and it's applying updates going back to 2016 ... It's going to be long while before I can try booting into ubuntu again.

---

### Post by oldfred on 2021-02-25
How you boot install media is then how it installs or repairs.

Some tools that create installer like Rufus create either a BIOS/MBR installer only or a UEFI/gpt installer only. Other tools create an installer that can be used for either UEFI or BIOS installs.
And each time you boot an installer or repair flash drive whether Ubuntu or Windows you have to choose "UEFI:flash" or "flash".
 The flash entry then is the BIOS boot and "flash" is usually the name or label of the flash drive.

If a BIOS only system, then you have no options, and have to have a BIOS bootable flash drive for it to work. You can use gpt with BIOS boot if drive is Ubuntu only. (I have since 2010 and still have it on a mostly retired 2006 laptop.)

The entry in UEFI/BIOS is only for the default boot of your installer internal systems.

Windows requires gpt for UEFI boot. Ubuntu will let you install in UEFI boot mode to an old MBR(msdos) partitioned drive, but probably should not. You cannot have Windows in BIOS boot on same drive as UEFI boot of Ubuntu. You can have different boot modes if on separate drives, but then can only dual boot from UEFI boot menu, not from grub menu.

If you use gpt, you have to a FAT32 formatted partition with esp/boot flags for UEFI. All installs put boot files into separate folders in the ESP. 
If you use gpt with BIOS boot of Ubuntu, you have to have a tiny 1 or 2MB unformatted partition with the bios_grub flag.

I did see one user who managed to get BIOS Windows and Ubuntu UEFI to work on one drive. I think he was able to put esp flag on ESP and boot flag on Windows boot partition. But many systems would not allow that.

---

### Post by foo2bar on 2021-02-26
Thank you for you rather comprehensive reply. I've yet to take it in.

In  essence, are you saying that whatever the bios records as the boot mode  (UEFI or legacy/BIOS), that only applies to tthe bios has seen the GPT  USB drive, ignored the he hdd/ssd on the machine? Things like USB sticks  could be booted as UEFI if they were formatted as such?

blkid on the installation media (a USB drive) reports:
/dev/sdc1:  UUID="2020-10-22-14-30-30-00" LABEL="Ubuntu 20.10 amd64" TYPE="iso9660"  PARTLABEL="ISO9660" PARTUUID="7ee1ffac-4072-46b8-885f-a7ea3f9c70cf"
/dev/sdc2:  SEC_TYPE="msdos" LABEL="ESP" UUID="F366-AE33" TYPE="vfat"  PARTLABEL="Appended2" PARTUUID="7ee1ffac-4072-46b8-885c-a7ea3f9c70cf"
/dev/sdc4:  LABEL="writable" UUID="e0b6feca-4108-478a-b899-aa451a67c425"  TYPE="ext4" PARTUUID="6222bb34-475d-d141-8e45-e30a25ba80d9"

(sdc3 is a 300kb gap which does not appear in blkid)

gparted states the USB drive has a GPT partition table and sdc2 has **boot** and **esp** flags.

I  used ubuntu's StartupDiskCreator to write ubuntu 20.10 to the USB  drive. So, if I'm understanding you correctly, the StarupDiskCreator  created a GPT partitioned USB drive. When inserted into my laptop, the  BIOS ignored its own internal settings (i.e. boot in legacy mode) and  having seen the boot flag on sdc2 (which also had the esp flag), booted  using UEFI. Therefore the installation also expects the destination for  the installation to also boot in UEFI?

Thing is .. this machine  has been working in dual boot, non-UEFI mode for years. Has something  changed in the installer/StartupDiskCreator since 2016 (which was the last installation on  the machine)?

---

### Post by oldfred on 2021-02-26
If you have the hybrid configured flash drive, it is the way you choose to boot it.

The settings in UEFI apply to all internal drives, so if HDD is an internal drive then UEFI settings of UEFI or Legacy will apply. But if HDD is an external drive those settings will not apply if you directly boot that drive. If you boot grub on another drive in UEFI mode then the boot of HDD will match how you booted system.

You cannot switch boot modes once you start booting.

---

### Post by foo2bar on 2021-02-26
When ubuntu's StartupDiskCreator is used to write create an installation USB disk, how does it decide which scheme to use? Can I force it to create a non-UEFI scheme?

---

### Post by oldfred on 2021-02-26
The Ubuntu ISO is configured for both UEFI or BIOS boot.

Rufus creates either UEFI or BIOS only versions. You can try that if desired.

But it should just be a choice in UEFI one time boot menu, UEFI or BIOS boot.

---

### Post by foo2bar on 2021-02-26
BTW, any idea why when installing ubuntu 20.10 I get the following message

> ubuntu grub-installer: info: Running chroot /target grub-install --force --target x86_64-efi "/dev/sda"
ubuntu grub-installer: info: Installing for x86_64-efi platform
ubuntu grub-installer: grub-install: error: **cannot copy      '/usr/lib/grub/x86_64-efi-wigned/grubx64.efi.signed' to      '/boot/efi/EFI/ubuntu/grubx64.efi': No space left on device**
ubuntu grub-installer: error: Running 'grub-install --force --target x86_64-efi "/dev/sda"' failed

The only partition on either the internal drive (sda) or the    installation USB drive (sdb) which has no/very little space left is the second    partition on the installation USB drive (sdb2) which happens to be the boot    partition (size 4.86MB, used 4.86MB)

Is this a side effect of the conflict between the machine's internal    drive being formatted as MBR/non-UEFI and the installation media being    booted as UEFI? Or have I just picked a USB stick which is too small    (4GB).

---

### Post by oldfred on 2021-02-26
You booted Ubuntu live installer in UEFI boot mode.

And Ubuntu's Ubiquity only installs grub's UEFI boot files into ESP - efi system partition on first drive seen. Usually sda or first NVMe drive.
If you want BIOS install you have to boot installer in BIOS mode. And in BIOS mode, using Something Else the combo box at bottom of partitioning screen works (does not work with UEFI) and you can choose which drive, sda, sdb etc to install grub2's boot loader into, but do not choose a partition.

You can tell which choice you made in UEFI one time boot menu by looking at first screen.
Shows live installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen 20.10 uses grub for both
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by foo2bar on 2021-02-26
Hello again - and thank you for all your help so far - much appreciated.

The screen I get when booting from the USB installation drive is the black one i.e. UEFI boot - not the purple one! When it booted up, there is no "choice" I can make to decide to boot in UEFI or non-UEFI.

I'll have a look at the BIOS to see if there is anything I can change - when I looked yesterday the UEFI boot setting was off ...

Thanks

UPDATE:
The **BOOT MENU** in the BIOS has the setting **UEFI BOOT SUPPORT** = **DISABLED**.

---

### Post by tea for one on 2021-02-26
When you have booted into a live Ubuntu session, you can double check whether you are in UEFI mode or Legacy mode.

Open a terminal and enter:-
```
[ -d /sys/firmware/efi ] && echo "UEFI mode" || echo "Legacy mode"
```

---

### Post by oldfred on 2021-02-26
Again the UEFI boot mode is only for your installed system.
How you boot install media is how it installs.

Every brand UEFI is different, but screen shot shows two entries for Toshiba flash drive. One clearly UEFI and one not.
My UEFI is somewhat similar as it shows two entries, also, but is a totally different brand UEFI and different source for live installer.

---

