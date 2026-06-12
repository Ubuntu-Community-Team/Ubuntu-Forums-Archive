---
title: "RAID Grub not installed on right partition"
date: 2020-04-23
forum: Server Platforms
---

### Post by kari0ca on 2020-04-23
Problem:
After windows 10 reinstall i used my usual kubuntu usb drive (USB A) to reinstall grub, but i don't know why it seems that the config files of grub went to the USB A.
After that, i've created another usb drive with kubuntu (USB B) to reinstall grub correctly, hoping that would save the grub on the disk (SSD), but it didn't happened. when my system boots without the USB A, the cursor keeps blinking and no grub menu is displayed.

Things that i have tried:
Boot with USB B and do the following
```
sudo mount /dev/sda4 /mntfor i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt$i; done
sudo chroot /mnt
sudo grub-install /dev/sda
update-grub
```

The result is:
```
# grub-installInstalling for i386-pc platform.
Installation finished. No error reported.


# update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.3.0-46-generic
Found initrd image: /boot/initrd.img-5.3.0-46-generic
Found linux image: /boot/vmlinuz-5.3.0-45-generic
Found initrd image: /boot/initrd.img-5.3.0-45-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 10 on /dev/sda1
done
```

My SSD config:
```
Device     Boot     Start       End   Sectors  Size Id Type/dev/sda1  *         2048   1126399   1124352  549M  7 HPFS/NTFS/exFAT
/dev/sda2         1126400 728758259 727631860  347G  7 HPFS/NTFS/exFAT
/dev/sda3       728758272 729845759   1087488  531M 27 Hidden NTFS WinRE
/dev/sda4       729849856 937701375 207851520 99,1G 83 Linux
```

In my opinion, when i tried to install grub on the second time, it should write grub and its config files on the SDA, right?
Is it possible that windows blocked the boot partition? or have locked something to prevent the grub to write the files correctly?

---

### Post by yancek on 2020-04-23
The USB A with Kubuntu, is that an actual, full install on an external usb drive or is it a 'live' system?
Is USB B a 'live' Kubuntu?  The output you posted for your SSD shows 3 windows partitions and one Linux.  Is that the install of Kubuntu?

If you boot with USB B, you need to first ascertain what it see itself as because if it is a 'live' install, it will probably be /dev/sda.  Use df -h or fdisk to get this info when booted to the 'live; Kubuntu before proceeding.

---

### Post by oldfred on 2020-04-23
Default installs of grub whether BIOS or UEFI go into first drive, unless you specify otherwise. 
And with Ubiquity installer, grub only goes into first drive, no matter what you specify.

May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by kari0ca on 2020-04-24
> **yancek said:**
> The USB A with Kubuntu, is that an actual, full install on an external usb drive or is it a 'live' system?
Is USB B a 'live' Kubuntu? The output you posted for your SSD shows 3 windows partitions and one Linux. Is that the install of Kubuntu?


If you boot with USB B, you need to first ascertain what it see itself as because if it is a 'live' install, it will probably be /dev/sda. Use df -h or fdisk to get this info when booted to the 'live; Kubuntu before proceeding.
USB A and USB B are live systems that i used to install my system (kubuntu)


the result of the command 
```

# df -h on my system, booted using the SSD with the USB A to boot
Sist. Arq.                   Tam. Usado Disp. Uso% Montado em
udev                         3,9G     0  3,9G   0% /dev
tmpfs                        794M  1,6M  793M   1% /run
/dev/sda4                     98G   70G   23G  76% /
tmpfs                        3,9G   87M  3,8G   3% /dev/shm
tmpfs                        5,0M  4,0K  5,0M   1% /run/lock
tmpfs                        3,9G     0  3,9G   0% /sys/fs/cgroup
/dev/loop0                    55M   55M     0 100% /snap/core18/1705
/dev/loop1                   102M  102M     0 100% /snap/p7zip-desktop/220
/dev/loop2                   106M  106M     0 100% /snap/audacity/648
/dev/loop3                    79M   79M     0 100% /snap/audacity/645
/dev/loop4                    63M   63M     0 100% /snap/gtk-common-themes/1506
/dev/loop6                   256K  256K     0 100% /snap/gtk2-common-themes/9
/dev/loop5                    28M   28M     0 100% /snap/snapd/6953
/dev/loop7                    28M   28M     0 100% /snap/snapd/7264
/dev/loop8                    55M   55M     0 100% /snap/gtk-common-themes/1502
/dev/loop9                    94M   94M     0 100% /snap/core/8935
/dev/sda2                    347G  126G  222G  37% /windows
/dev/mapper/pdc_ccjcdigaib3   65G   52M   62G   1% /store_lin
/dev/mapper/pdc_ccjcdigaib2  430G   89G  342G  21% /store_win
/dev/mapper/pdc_ccjcdigaib1  1,4T  1,1T  296G  79% /tralha
tmpfs                        794M   12K  794M   1% /run/user/1000
```


And the result of the command using the USB B to boot (live mode)```

# df -h 
Filesystem                   Size  Used Avail Use% Mounted on
udev                         3.9G     0  3.9G   0% /dev
tmpfs                        794M  1.5M  793M   1% /run
/dev/sdf1                    3.8G  2.2G  1.6G  58% /cdrom
/dev/loop0                   1.7G  1.7G     0 100% /rofs
/cow                         3.9G  179M  3.8G   5% /
tmpfs                        3.9G   29M  3.9G   1% /dev/shm
tmpfs                        5.0M  8.0K  5.0M   1% /run/lock
tmpfs                        3.9G     0  3.9G   0% /sys/fs/cgroup
tmpfs                        3.9G  4.0K  3.9G   1% /tmp
tmpfs                        794M   12K  794M   1% /run/user/999
/dev/mapper/pdc_ccjcdigaib1  1.4T  1.1T  296G  79% /media/kubuntu/Tralha

```



> **oldfred said:**
> Default installs of grub whether BIOS or UEFI go into first drive, unless you specify otherwise. 
And with Ubiquity installer, grub only goes into first drive, no matter what you specify.

May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)
I've done the repair process with the boot-repair and the boot went to the USB B.
the log is in this link: [https://paste.ubuntu.com/p/73kPvZKyZP/](https://paste.ubuntu.com/p/73kPvZKyZP/)
I will try later use the advance options

---

### Post by oldfred on 2020-04-24
With multiple drives you should not ever use Boot-Repair's auto-fix.
It will want to install grub into every drive and when you have multiple drives you typically only want grub in one drive.
You need to use advanced options and choose install & drive.

I find if I reboot with a flash drive installed, it normally becomes sda and every other drive changes one letter. And default install of grub is usually sda. With two flash drives not sure then what it does, I have avoided doing that.

---

### Post by kari0ca on 2020-04-27
> **oldfred said:**
> With multiple drives you should not ever use Boot-Repair's auto-fix.
It will want to install grub into every drive and when you have multiple drives you typically only want grub in one drive.
You need to use advanced options and choose install & drive.

I find if I reboot with a flash drive installed, it normally becomes sda and every other drive changes one letter. And default install of grub is usually sda. With two flash drives not sure then what it does, I have avoided doing that.
I've installed grub with Boot-Repair and have set some advance options, with no success.
Here goes some screens

My Hard Disks
[IMG]http://www.upl.co/uploads/gparted11587989103.png[/IMG]

Boot-Repair
[IMG]http://www.upl.co/uploads/BootRepair11587989137.png[/IMG]

Boot-Repair
[IMG]http://www.upl.co/uploads/BootRepair21587989169.png[/IMG]
I don't know why the grub and its config files aren't writen into SDA, wich is my systems SSD.
Any help on that?

---

### Post by oldfred on 2020-04-27
Please attach screenshots. If large photo reduce size also.
You can easily attach screenshots with forum's advanced editor and paperclip icon.

It looks like it should have installed grub correctly to sda.
Post link to summary report from Boot-Repair.

---

### Post by kari0ca on 2020-04-27
> **oldfred said:**
> Please attach screenshots. If large photo reduce size also.
You can easily attach screenshots with forum's advanced editor and paperclip icon.

It looks like it should have installed grub correctly to sda.
Post link to summary report from Boot-Repair.
Here is the link from the log of my last attempt, the one pointing to the SDA disk, wich appeared the other partitions from my system
[https://paste.ubuntu.com/p/RQmVR2SQGY/](https://paste.ubuntu.com/p/RQmVR2SQGY/)

---

### Post by oldfred on 2020-04-27
I do not know RAID.
Moving to the server sub-forum where those who know RAID may be able to help.
You have Promise hardware RAID but different sizes of drives.
It is showing some sort of gpt error. But I have seen a user try to fix gpt with either LVM or RAID and have further issues. So do not know details.

---

### Post by darkod on 2020-04-27
1. Are you using legacy boot or EFI boot?
2. From ubuntu/kubuntu live mode, and assuming the ssd is sda, post the output of:
```
sudo parted /dev/sda unit MiB print
```

---

### Post by kari0ca on 2020-04-28
> **darkod said:**
> 1. Are you using legacy boot or EFI boot?
2. From ubuntu/kubuntu live mode, and assuming the ssd is sda, post the output of:
```
sudo parted /dev/sda unit MiB print
```

This is from my running system, wich i used the USB A to boot, but the system is running from my SSD
```
[FONT=monospace][COLOR=#000000]sudo parted /dev/sda unit MiB print[/COLOR]
[sudo] senha para higor:  
Modelo: ATA SanDisk SSD PLUS (scsi)
Disco /dev/sda: 457863MiB
Tamanho do setor (lógico/físico): 512B/512B
Tabela de Partição: msdos
Opções de disco:  

Número  Início     Fim        Tamanho    Tipo     Sistema de arquivos  Opções
 1      1,00MiB    550MiB     549MiB     primary  ntfs
 2      550MiB     355839MiB  355289MiB  primary  ntfs
 3      355839MiB  356370MiB  531MiB     primary  ntfs                 diag
 4      356372MiB  457862MiB  101490MiB  primary  ext4                 boot[/FONT]
```

I'm working now, later i will boot from USB B and do the same

---

### Post by darkod on 2020-04-28
It doesn't look like you are using EFI boot. You have no ESP partition.

I don't see any major issues, except that you are using msdos table on the disk and you already have 4 primary partitions. You can't create any more partitions.

Make sure you boot the usb stick in legacy mode (not EFI) and then make sure which letter does the stick have and which letter does the ssd have.

You don't even need full chroot.

Lets assume the ssd is sda and we know your ubuntu root partition is sda4. To install grub to the MBR from live mode simply do:
```
sudo grub-install --root-directory=/dev/sda4 /dev/sda
```

That command tells it to install to the MBR of /dev/sda and that the root is /dev/sda4.

If in live mode your ssd becomes sdb simply modify the command.

After that reboot without the stick connected and see if it worked.

---

### Post by kari0ca on 2020-04-28
> **darkod said:**
> It doesn't look like you are using EFI boot. You have no ESP partition.

I don't see any major issues, except that you are using msdos table on the disk and you already have 4 primary partitions. You can't create any more partitions.

Make sure you boot the usb stick in legacy mode (not EFI) and then make sure which letter does the stick have and which letter does the ssd have.

You don't even need full chroot.

Lets assume the ssd is sda and we know your ubuntu root partition is sda4. To install grub to the MBR from live mode simply do:
```
sudo grub-install --root-directory=/dev/sda4 /dev/sda
```

That command tells it to install to the MBR of /dev/sda and that the root is /dev/sda4.

If in live mode your ssd becomes sdb simply modify the command.

After that reboot without the stick connected and see if it worked.

Unfortunately i`m getting this error doing the previous command:
```
root@kubuntu:/# sudo grub-install --root-directory=/dev/sda4 /dev/sda
Installing for i386-pc platform.
grub-install: error: failed to get canonical path of `/dev/sda4/boot/grub'.
```

---

### Post by oldfred on 2020-04-28
Try this, I think you have to mount partition first for BIOS version of grub.

sudo mount /dev/sda4 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sda

---

### Post by darkod on 2020-04-29
> **oldfred said:**
> Try this, I think you have to mount partition first for BIOS version of grub.

sudo mount /dev/sda4 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sda


Correct. I haven't done this command in so long that I forgot about the middle step where you have to mount the root partition. :)

If that also doesn't work I would suggest full chroot and to completely reinstall grub. We can give you the steps later.

---

### Post by kari0ca on 2020-04-29
After trying that yesterday i've tried mounting the root on /mnt, but no success.
Today i've booted from USB live kubuntu and seems that it fails to write to MBR...

I think that i will clear all partitions from this SSD and install all from scratch, windows 10 and then kubuntu

---

### Post by darkod on 2020-04-30
If you can't mount sda4 at /mnt then you might have bigger problems, not just grub-install to sda. You should be able to correctly mount the partition from live mode at any time.

If you wanna go with full reinstall and you don't mind doing it, then go ahead. Troubleshooting this will take more time and there is no guarantee of success, we don't know what the issue is yet.

---

### Post by kari0ca on 2020-04-30
> **darkod said:**
> If you can't mount sda4 at /mnt then you might have bigger problems, not just grub-install to sda. You should be able to correctly mount the partition from live mode at any time.

If you wanna go with full reinstall and you don't mind doing it, then go ahead. Troubleshooting this will take more time and there is no guarantee of success, we don't know what the issue is yet.
Sorry my mistake, when i said that i had no success mounting root on /mnt, wasn't that i meant. i did mount the /dev/sda4 on /mnt and did reinstalled grub, but seems that can't write to mbr.

---

### Post by darkod on 2020-04-30
There is the option of windows preventing you maybe. I haven't done dual boot in long time, and especially not with newest Win10 (if that's what you have).

It can't be rules out that some windows "protective app" is preventing you write to the MBR.

---

### Post by oldfred on 2020-04-30
What brand system or motherboard?

Some UEFI or BIOS have settings or Bitlocker in Windows, users have posted these:
BIOS settings to disable "Boot Sector Virus Protection" or called Security or locked down Boot sector, Bitlocker
 bios had a setting for "Fixed disk boot sector" and it was set at "Write Protect"
If your boot drive has RAID meta-data on it, Desktop installer does not like it. Not sure how server install then works.

---

