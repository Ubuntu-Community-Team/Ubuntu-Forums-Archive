---
title: "GRUB2 grub-install.exe, File system `fat' doesn't support embedding."
date: 2018-07-20
forum: Windows
---

### Post by boqsc on 2018-07-20
**Introductory specification:**
Operating System I'm using: Windows 10 Home x64 
GRUB2 download source I'm using: [grub-2.02-for-windows.zip]("ftp://ftp.gnu.org/gnu/grub/")


I'm issuing  an install of grub on the **MBR USB Flash drive **formatted by Windows.
```
C:\Users\boqsc\OneDrive\Stalinis kompiuteris\grub-2.02-for-windows>**grub-install.exe  --boot-directory="F:\." --target="i386-pc" "\\?\F:"**
Installing for i386-pc platform.
grub-install.exe: warning: File system `fat' doesn't support embedding.
grub-install.exe: warning: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  Ho
wever, blocklists are UNRELIABLE and their use is discouraged..
grub-install.exe: error: will not proceed with blocklists.

```

What are the steps to resolve and correctly install bootable Grub into USB flash drive using Windows operating system?

---

### Post by oldfred on 2018-07-20
Grub2 does not like to install to partitions, not enough space and then it has to use blocklists. Is f: not a partition? 
Or is flash drive gpt partitioned? If so you need a bios_grub partition. It is 1 or 2MB unformatted with bios_grub flag.

It probably is easier to create an Ubuntu live installer and install grub from that to your flash drive. Plus many here know how to do that, were almost no one has installed grub using Windows.

You need to install grub to the USB drive. Not sure how you specify that in Windows. but then parts of grub may be in the f: drive.

---

### Post by boqsc on 2018-07-20
> **oldfred said:**
> Grub2 does not like to install to partitions, not enough space and then it has to use blocklists. Is f: not a partition? 

I'm using *gdisk64.exe* (**GPT fdisk** is a disk partitioning tool, download page: [https://sourceforge.net/projects/gptfdisk/](https://sourceforge.net/projects/gptfdisk/))
```

C:\Users\boqsc\OneDrive\Stalinis kompiuteris\fdisk>gdisk64.exe
GPT fdisk (gdisk) version 1.0.3


Type device filename, or press <Enter> to exit: 1:
[B]Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present


Found valid GPT with protective MBR; using GPT.[/B]

```

The **F: **disk seems to be **GPT** partition that is **7.2GB **with **FAT **filesystem**.**
```

**Number  Start (sector)    End (sector)  Size       Code  Name**
   1            2048        15155166   7.2 GiB     0700  Microsoft basic data
```



> **oldfred said:**
> 
Or is flash drive gpt partitioned? 

This seems to be the case - it is gpt partitioned.

> **oldfred said:**
> 
If so you need a bios_grub partition. It is 1 or 2MB unformatted with bios_grub flag.


Did you mean there is only need to format it to **BIOS boot partition (type EF02) **for the partition to be considered **bios_grub** flagged?
How is the flag applied in Ubuntu/linux, what tools are used? Not sure what the flagging is.


> **oldfred said:**
> 
It probably is easier to create an Ubuntu live installer and install grub from that to your flash drive. Plus many here know how to do that, were almost no one has installed grub using Windows.

You need to install grub to the USB drive. Not sure how you specify that in Windows. but then parts of grub may be in the f: drive.

Yes, i'm sure it is easier to do this from the linux environment. 
But my goal is to do that with Windows only, that's why I need uncommon help and 
I'm not sure who can help me with that, as grub2 manuals seems to be lacking information.

---

### Post by oldfred on 2018-07-20
If using gdisk to partition flash drive then you still need a 1 or 2MB unformatted partition with code ef02 for grub to install. It can be anywhere on drive, but if using Windows best not to have it first as Windows typically only sees the first partition on flash drives.
The bios_grub flag is used by parted & gparted. 
The actual info inside the gpt partition is some very long GUID that identifies what partition is used for.

       GPT fdisk Tutorial 
[http://www.rodsbooks.com/gdisk/walkthrough.html](http://www.rodsbooks.com/gdisk/walkthrough.html)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

### Post by boqsc on 2018-07-20
> **oldfred said:**
> If using gdisk to partition flash drive then you still need a 1 or 2MB unformatted partition with code ef02 for grub to install. It can be anywhere on drive,



> **oldfred said:**
> 
 but if using Windows best not to have it first as Windows typically only sees the first partition on flash drives.


Well it is possible to set the attribute for the partition to hidden and hide the system partitions. 
If your worry is about accessing the content of non-system partitions of the USB drive. 
Then this might be a viable solution, sure not tested yet if the USB system drives boots after setting the attributes.

```

Command (? for help): x


Expert command (? for help): a
Partition number (1-2): 1
Known attributes are:
0: system partition
1: hide from EFI
2: legacy BIOS bootable
60: read-only
62: hidden
63: do not automount


Attribute value is 0000000000000000. Set fields are:
  No fields set

```


> **oldfred said:**
> 
The bios_grub flag is used by parted & gparted. 
The actual info inside the gpt partition is some very long GUID that identifies what partition is used for.

GPT fdisk Tutorial 
[http://www.rodsbooks.com/gdisk/walkthrough.html](http://www.rodsbooks.com/gdisk/walkthrough.html)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

### Post by oldfred on 2018-07-20
What are you planning on booting from flash drive?
Once grub is installed, you have to create your own grub.cfg for it to boot.

I once created a Windows 7 repair flash drive. But it took so little space on larger flash drive, I installed grub to it, added boot entries to boot the Windows repair install and then added ISO and had grub loopmount those. Then on one flash drive I had a Windows repair tool  & several Linux repair ISO or installs.

---

### Post by boqsc on 2018-07-20
> **oldfred said:**
> What are you planning on booting from flash drive?


I'm interested in booting Ubuntu. 
The whole plan is about making Ubuntu persistent USB drive from Windows operating system and learning/studying how some parts work.

> **oldfred said:**
> 
Once grub is installed, you have to create your own grub.cfg for it to boot.

This is horrible experience for me as **grub-2.02-for-windows (**[ftp://ftp.gnu.org/gnu/grub/](ftp://ftp.gnu.org/gnu/grub/)**)** or any previous version associated with grub2, has no **grub-mkconfig.exe **included and only mysterious **grub-mkconfig_lib **script which is written in **Bash **and couldn't be ran in Windows environment, this might be a mistake from the developers of grub2 as I haven't seen any auto-generation of  **grub.cfg** or **menu.lst **after installation with target of **i386-efi** which is always successful and without an error.

I'm wondering if **grub.cfg** or **menu.lst** are always made by script (grub-mkconfig) in linux, or is it uncommon practice used by beginners studying grub, 
and if the non-existant** grub-mkconfig.exe** that is nothing more than - supposingly simple compiled script, is even needed.



> **oldfred said:**
> 
I once created a Windows 7 repair flash drive. But it took so little space on larger flash drive, I installed grub to it, added boot entries to boot the Windows repair install and then added ISO and had grub loopmount those. Then on one flash drive I had a Windows repair tool  & several Linux repair ISO or installs.

---

### Post by oldfred on 2018-07-20
Ignore anything related to menu.lst unless experimenting with the very old grub4dos which is based on grub legacy which used menu.lst.
Grub2 used grub.cfg.
But grub has os-prober to find other installs and add to grub, but grub has to first be installed.
When just installing grub, you have to manually create grub.cfg.

If your system is UEFI:
       If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formated flash & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)
[https://help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb)

Normal way to create live installer. Persistent is an option.
       Most find this works:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb) 
            Persistent  install
[https://help.ubuntu.com/community/mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

---

### Post by boqsc on 2018-07-21
> C:\Users\boqsc\OneDrive\Stalinis kompiuteris\grub-2.02-for-windows>grub-install.exe  --boot-directory="F:\." --target="**i**
**386-pc**" "\\?\F:" --force
How can I know that was a successfull operation, what are the steps to test it?
I can't trust the output of **grub-install.exe **

---

### Post by oldfred on 2018-07-21
In BIOS you can try to boot. But unless you have created a grub.cfg you will get grub>.

You can run this report from Ubuntu live installer, but do not know how from Windows.

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

