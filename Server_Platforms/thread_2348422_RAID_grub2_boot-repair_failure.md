---
title: "RAID grub2 boot-repair failure"
date: 2017-01-03
forum: Server Platforms
---

### Post by kdrees on 2017-01-03
After a failed upgrade from ubuntu 14.04 to 16.04, my system no longer boots. I believe I fixed the operating system by purging old kernel files from /boot using chroot from a live cd and completing the upgrade. However, when booting the system, the grub rescue prompt appears after the message "invalid arch-independent ELF magic". I tried the boot-repair process, but I get the same error. Here is a link to my bootinfo file:

[URL="http://paste2.org/sDjVHa0d"]http://paste2.org/sDjVHa0d
[/URL]

---

### Post by oldfred on 2017-01-03
You show mixed UEFI & BIOS.
And the ELF error is usually related to booting in UEFI with BIOS install or vice-versa. That error would only be from old files from previous install in other boot mode.

Current install does not show mounting of ESP - efi system partition, so it looks like a BIOS boot is current configuration. If you want to convert to UEFI, Boot-Repair can do that if booted in UEFI mode and using advanced options to totally uninstall/reinstall grub. That uninstalls grub-pc(BIOS) and installs grub-efi-amd64(UEFI).

Boot-Repair mentions Secure boot may be on. If so you cannot boot in BIOS mode as that is not secure. You also are not showing signed kernels, so even in UEFI boot mode you have to have secure boot off in UEFI.

You also show grub installed to sda2 partition boot sector. System cannot boot from a partition boot sector unless you have another boot loader. And grub2 does not recommend use of partition boot sectors as it does not really fit. Always install grub to a drive like sda, not a partition like sda2.

If you want UEFI. How you boot install media from UEFI is then how it installs.
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by korab on 2017-01-03
I had the same problem (kernel panic) grub2 error or  better call it ''crash'' i relaised that instead of installing the 32 bit version i acidentally installed 64 bit and caused me the grub2 error and kernel panic

---

### Post by kdrees on 2017-01-04
Thanks for the help!

oldfred:
With the info at [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI), I determined that:
* ubuntu isn't booting in EFI mode
* I have grub-pc installed, not grub-efi
* my live cd isn't booting in EFI mode
* my firmware (American Megatrends version 3201) can't switch the boot mode to EFI, or toggle secure boot.

I don't want to install windows into a partition or anything else that would require EFI. The system booted with BIOS before my ubuntu upgrade problem. I just want to get it to boot properly again.

I did confirm that my ubuntu 16.04 installation is functional. I'm able to chroot to its partition and use it.

While doing this repair, I had created a FAT32 EFI system partition with a boot flag using GParted. This was based upon "well, it can't hurt" partitioning advice in the GPTfdisk tutorial ([http://www.rodsbooks.com/gdisk/advice.html](http://www.rodsbooks.com/gdisk/advice.html)). Maybe that was the problem. Unfortunately, deleting it and running boot-repair didn't fix it.

I did see in the ubuntu UEFI article that turning off QuickBoot might help. I was able to do this in my BIOS, but after running boot-repair, it still wouldn't boot.

I was able to fix the problem with grub2 being installed in the boot record of my ubuntu partition. I must have inadvertently installed it there during one of the many purge/reinstalls I've done. I used dd to clear the boot record:

sudo dd if=/dev/sda2 of=/home/sda2_boot_backup.bin bs=512 count=1
sudo dd if=/dev/zero of=/dev/sda2 bs=512 count=1

Unfortunately, the system still wouldn't reboot after another boot-repair.

korab:
I have a 64 bit system and am running a 64 bit ubuntu. apt-get is automatically installing grub for i386. I didn't see a 64 bit version of grub in the repository. That shouldn't be a problem though, right? A 64 bit os can run a 32 bit app, right?

The current bis is at [http://paste2.org/j8vY5WnK](http://paste2.org/j8vY5WnK). If you have any other suggestions, please let me know. Thank you!

---

### Post by LostFarmer on 2017-01-04
> However, when booting the system, the grub rescue prompt appears after the message "invalid arch-independent ELF magic". is that still the error message ?

---

### Post by oldfred on 2017-01-04
Is it really a 9TB drive? Or is something else wrong.

You only need bios_grub to be 1 or 2MB, and I always have used both the ESP - efi system partition and bios_grub on every install. But I do not have any  very large drives.

A few motherboards had to see a boot flag even if you were not using it and grub does not use it. I think there were several posts where Rod Smith suggested adding the fat32 with boot flag on gpt drives and similar on MBR(msdos) drives. I know some Intel motherboards had that type of issue.
I might keep the ESP, even if not used & booting in BIOS mode.
What motherboard?

A while back when 2TB was large, there were issues with both grub and BIOS that would not work with larger drives.

You might try a smaller / (root) partition and use rest of drive as /home or /mnt/data or both.

---

### Post by kdrees on 2017-01-05
Yes, the error I'm getting is still "invalid arch-independent ELF magic".

---

### Post by kdrees on 2017-01-05
Also, the hard drive is a hardware RAID of 4 2.2 TB hard drives.

---

### Post by oldfred on 2017-01-05
I do not know RAID.
Moving to Server sub-forum where those who may know RAID can help.

But what motherboard?
May be better to have bios_grub right after ESP on drives. 
What type of RAID, FakeRAID (BIOS type), Hardware RAID (Brand?) or Linux Software(mdadm)?

---

### Post by darkod on 2017-01-05
While you were in the chroot, did you try reinstalling grub to /dev/sda?

And how are you sure you fixed the broken installation? You just ran apt-get upgrade in the chroot?

You might need to update the initramfs in the chroot also. I think it should be something like:
```
update-initramfs -u
```

NOTE: I assume you are inside the chroot above, so I did not include sudo in front of the command. Otherwise it needs sudo, but not when you are running it as root.

---

### Post by LostFarmer on 2017-01-05
[https://lists.gnu.org/archive/html/help-grub/2011-08/msg00008.html](https://lists.gnu.org/archive/html/help-grub/2011-08/msg00008.html)

"This generally means that the version of grub being loaded from the
mbr + embedded area at boot does not match the version whose files are
in /boot/grub/."

I do not know how raid drives work , but could the 'boot-repair' be installing the updated grub to the wrong hdd ?

I did have a look at grubx64.efi and it does have "invalid arch-independent ELF magic" in its code.

---

### Post by darkod on 2017-01-06
Personally I wouldn't run automatic boot-repair on servers where you are not sure which exact steps it will perform. I have respect for the script and its creator, but often servers have specific setups too, and not all can be properly detected and acted upon...

That is why I asked if you tried reinstalling grub from the chroot? It would go something like:
Remove it (purge):
```
apt-get purge grub-pc grub-common grub
```

Install it, create new config and install it on the MBR of sda, just in case update initramfs too:
```
apt-get install grub-pc
grub-mkconfig
grub-install /dev/sda
update-grub
update-initramfs -u
```

Reboot and see how it went...

---

### Post by kdrees on 2017-01-10
Oldfred, here is my motherboard info:

# dmidecode 3.0
Getting SMBIOS data from sysfs.
SMBIOS 2.6 present.

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
    Manufacturer: ASUSTeK Computer INC.
    Product Name: KGP(M)E-D16
    Version: Rev 1.xxG
    Serial Number: 130410287300047
    Asset Tag: To Be Filled By O.E.M.
    Features:
        Board is a hosting board
        Board is replaceable
    Location In Chassis: To Be Filled By O.E.M.
    Chassis Handle: 0x0003
    Type: Motherboard
    Contained Object Handles: 0

I checked the raid situtation and determined it to be a hardware raid, but I don't remember the details. I'll confirm this tomorrow.

I'll put the ESP partition back on the drive first, followed by the bios-grub partition, like I had it set up when I started the thread.

Darko:

I have tried reinstalling grub using the kernel on my hard drive with chroot rather than the live cd. I didn't receive any error messages, which I think means the ubuntu installation is working, but it still wouldn't boot. I did not do "update-initramfs," and will give that a try.

---

### Post by darkod on 2017-01-11
Now you lost me. What do you mean by "using the kernel on my HDD with chroot"?

You said grub does not work which means boot does not work, right? In such cases usually you boot the system with desktop live cd or system rescue cd or similar... Then once into the live environment, you use chroot to go into the server installation and from that point on you are working as if the server is booted, you are working inside the server.

For comparison, if you don't do chroot, running update-initramfs or similar commands will actually run them into the live environment, not in the server installation. So they would not help.

Since you already said you know how to chroot, this is why I suggested from chroot (so, from inside the server installation) to purge all grub and try reinstalling it.

---

### Post by kdrees on 2017-01-13
> **darkod said:**
> Now you lost me. What do you mean by "using the kernel on my HDD with chroot"?


Sorry about my bad terminology Darko. My system does not boot. I've been using a live cd to boot, and can use chroot to use the server ubuntu installation.

I reinstalled grub and ran update-initramfs as you suggested in chroot. Here are the commands I used, starting with a terminal in a live cd session...

```

sudo mount /dev/sda2 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /dev/pts /mnt/dev/pts 
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt

apt-get install grub-pc
grub-mkconfig
grub-install /dev/sda
update-grub
update-initramfs -u

```

Unfortunately, it didn't boot. I got the same "invalid arch-independent ELF magic" error.

---

### Post by kdrees on 2017-01-13
> **oldfred said:**
> 
What type of RAID, FakeRAID (BIOS type), Hardware RAID (Brand?) or Linux Software(mdadm)?


A 3ware SATA RAID controller 9740-4i is listed when the system begins booting, so I think we're dealing with a hardware RAID.

---

### Post by oldfred on 2017-01-13
I though hardware RAID looked just like any install as hardware handled everything. 
Or you reinstall of grub should have worked to reinstall to MBR or sda.
Are you booting from sda?
Do you have any other system partitions like /boot? Those also must be mounted when chrooting.

---

### Post by darkod on 2017-01-13
I see you didn't run the purge like I suggested. That might help actually remove any wrong grub installs. I think running boot repair might have actually messed things up if it confused between uefi boot and legacy boot and vice-versa.

PS. Let me explain little better... I think you might have a mismatch of legacy grub vs uefi grub maybe as a result of manually creating/deleting the ESP partition and running boot repair or trying to reinstall grub manually. Seeing the ESP (or the lack of), it might have tried to install wrong grub.

So what I would suggest is to recreate the original disk layout. If you had ESP partiiton, create it again if it's missing now. If you didn't have one, delete any ESP partition you created manually during the troubleshooting.

After that is done, use the above commands to first purge all grub packages (the main ones anyway), and then reinstall them. This reinstall will hopefully get things right if the ESP partition state is as it was originally (existing or not).

As for the raid, it looks normal I guess. You have HW raid and hence it is showing single /dev/sda disk (the raid array presented as single disk to the OS). Right?

---

### Post by oldfred on 2017-01-13
There are a few systems (Intel motherboards for one) that want to see a boot flag or they do not let you even start to boot. Does not matter whether UEFI or BIOS or MBR or gpt. 
And we saw a BIOS install on gpt partitioned drive where we had to add a boot flag. With BIOS boot flag can be on any partition or if Windows any primary partition. 
But with gpt the boot flag must only be on the FAT32 formatted partition that becomes the ESP - efi system partition. In one install we created a tiny FAT32 partition added boot flag just to make motherboard/BIOS happy, but still installed in BIOS mode using bios_grub partition. FAT32 was not used.

I typically add both the ESP & bios_grub to all new drives, even larger flash drives. But only one or the other is normally used. 
But gives me the chance to change boot mode later if desired to test different boot mode.

---

### Post by kdrees on 2017-01-25
> **oldfred said:**
> I though hardware RAID looked just like any install as hardware handled everything.
That was my understanding. I included the RAID info in case it wasn't that straightforward.
> **oldfred said:**
> Are you booting from sda?
yes
> **oldfred said:**
>  Do you have any other system partitions like /boot? 
No, the whole installation is in one partition.

---

### Post by kdrees on 2017-01-25
> **darkod said:**
> I see you didn't run the purge like I suggested.
I had, but neglected to include that command. 

I removed the ESP and ran the commands again:

```


sudo mount /dev/sda2 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /dev/pts /mnt/dev/pts 
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt

apt-get purge grub-pc grub-common grub

apt-get install grub-pc
grub-mkconfig
grub-install /dev/sda
update-grub 
update-initramfs -u
```
Unfortunately, I got the same results: "invalid arch-independent ELF magic" and a grub rescue prompt.
> **darkod said:**
> You have HW raid and hence it is showing single /dev/sda disk (the raid array presented as single disk to the OS). Right?
Right.

---

### Post by darkod on 2017-01-25
I have no more ideas, sorry. You seem to be doing the correct steps to purge and reinstall grub. Whether that is enough in your HW configuration I can't be sure. Maybe oldfred has more ideas, especially since I still think uefi is the cuprit here.

Are you 100% the upgade was completed correctly after the initial problems? Looks like it might not have been...

---

### Post by oldfred on 2017-01-25
Just to confirm where you are at.  Not sure if this will show anything or not.
Are you booting in BIOS/CSM/Legacy mode from UEFI/BIOS?
I do not know RAID, but know grub, BIOS & UEFI.

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by kdrees on 2017-01-30
> **darkod said:**
> Are you 100% the upgade was completed correctly after the initial problems? Looks like it might not have been...
I was, but now I'm not! I had used chroot to mount linux from the hard drive, and then sudo apt-get update & upgrade to repair the operating system. The output indicated that the os had been successfully upgraded, but the booting problem persisted.

---

### Post by kdrees on 2017-01-30
> **oldfred said:**
> Are you booting in BIOS/CSM/Legacy mode from UEFI/BIOS?
I do not know RAID, but know grub, BIOS & UEFI.

       Post the link to the Create BootInfo summary report.
The BootInfo summary from the start of the thread is at [http://paste2.org/j8vY5WnK](http://paste2.org/j8vY5WnK). I think the relevant section is here:

[LIST=|INDENT=1]
[*][FONT=inherit][COLOR=#666666][FONT=inherit]===================[/FONT][/COLOR] UEFI/Legacy mode:[/FONT]
[*][FONT=inherit]This live-session is not in EFI-mode.[/FONT]
[*][FONT=inherit]SecureBoot maybe enabled.[/FONT]
[*]
[*]
[*][FONT=inherit][COLOR=#666666][FONT=inherit]===================[/FONT][/COLOR] PARTITIONS [FONT=inherit]&[/FONT] DISKS:[/FONT]
[*][FONT=inherit]sda2    : sda,    not-sepboot,    grubenv-ok    grub2,    signed grub-pc ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda2.[/FONT]
[*][FONT=inherit]sda1    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.[/FONT]
[*]
[*][FONT=inherit]sda    : GPT,    BIOS_boot,    has-no-EFIpart,     not-usb,    has-os,    [COLOR=#666666][FONT=inherit]2048[/FONT][/COLOR] sectors * [COLOR=#666666][FONT=inherit]512[/FONT][/COLOR] [COLOR=#19177C][FONT=inherit]bytes[/FONT][/COLOR][/FONT]
[/LIST]

So I think I'm booting in BIOS mode from BIOS. 

I can get a more recent BootInfo summary if you think it might help. Meanwhile, I'm moving data files from sda2 to a new partition in preparation for wiping sda2 and reinstalling linux.

---

### Post by oldfred on 2017-01-30
You cannot have UEFI secure boot on, and boot in BIOS mode. They are incompatible.
Make sure Secure Boot is off and boot in legacy mode.

Your bios_grub is unusually large. Not an issue, but it is sized more like a FAT32 ESP - efi system partition.
The bios_grub only needs to be 1 or 2MB and unformatted. 
I usually configure all gpt drives with both the ESP & bios_grub, but normally install & boot one way or the other. And now I only use gpt.

---

