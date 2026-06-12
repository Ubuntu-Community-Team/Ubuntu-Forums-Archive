---
title: "Trying to restore a Windows 8.1 x64 boot with boot-repair"
date: 2019-01-05
forum: Windows
---

### Post by okaghana on 2019-01-05
Hello There.

A few days ago my Laptop with Windows 8.1 64bit on it crashed and gave a 0xc000225 booting error. I tried to run the boot-repair via the windows 8 installation disk, but still couldn't fix the problem. Then I discovered [this awesome tool]("https://sourceforge.net/p/boot-repair-cd/home/Home/") on the internet. I tried to fix my non-booting laptop with it, but at first it reported that the repair was not successful. I looked in the log and discovered that when the laptop crashed it went into hibernation mode and so linux could only mount it read-only. I removed the hiberfile by mounting the HDD once manually with the --remove-hiberfile option.
After this the boot-repair gave me a "Boot successfully repaired" message, but I still wasn't able to boot and it still gave me the 0xc000225 error message.

I tried to run the boot-repair multiple times, but I always noticed, that the "MBR options" tab in the advance options was always grayed out and I couldn't change any settings, which seemed kinda strange to me, considering the fact that, as far as i know, windows uses MBR to boot.
I opened the boot-repair on my running windows 7 system (without running the boot-repair of course), and I saw that the "MBR options" tab was accessible and there were even some more options in the standard advanced-options menu where  I could change things like the un-hiding duration of the bios before booting.

You can find the output-log of the boot-repair of the laptop [here]("https://paste.ubuntu.com/p/MrY8XGxVDc/"). It says [SIZE=3] "[FONT=times new roman]The default repair of the Boot-Repair utility will not act on the MBR.[/FONT]"[/SIZE] and  [SIZE=2][SIZE=3]"[FONT=times new roman]Refusing to operate on read-write mounted device /dev/sdaX[/FONT]"[/SIZE],but I have no idea what to do about these messages.

It would very nice if you could help me with this problem.[/SIZE]

---

### Post by oldfred on 2019-01-05
If Windows 8 or 10 is pre-installed by vendor it uses the newer UEFI/gpt configuration, not the now 35 year old BIOS/MBR configuration.
With gpt partitioning there is a protective MBR, really for old MBR tools like old versions of fdisk seeing that drive has gpt partitioning. 
Usually Windows 7 was installed in the BIOS/MBR configuration, although a user can  instal to newer UEFI hardware in UEFI boot mode.

Boot-Repair is primarily for Linux systems, it can only do a very few repairs to Windows systems, due to the proprietary restrictions by Microsoft.

What brand/model system?
What video card/chip.

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the summary report ( not post full report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

But if Windows issues you probably will need your Windows repair/recovery flash drive to fix it. If Windows 8, you may be able to directly boot from UEFI (not grub) and f8 into an internal repair console to make fixes.
Grub only boots working Windows or Windows that is not hibernated.

---

### Post by okaghana on 2019-01-05
Ok.

The Laptop is a Toshiba Satellite Pro c870. You can find the specifications [here]("https://www.toshiba.ca/productdetailpage.aspx?id=2147493578").
Except that we upgraded it to Windows 8.1

By Summary I assume u mean the boot summary at the top of the full report:
[HTML]============================= Boot Info Summary: ===============================

 => Lilo is installed in the MBR of /dev/sda.
 => Syslinux MBR (5.00 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/bcd

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/Boot/bootx64.efi /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgr.efi 
                       /EFI/Microsoft/Boot/memtest.efi 
                       /EFI/toshiba/Boot/bootmgfw.efi 
                       /EFI/toshiba/Boot/bootmgr.efi 
                       /EFI/toshiba/Boot/memtest.efi

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot.ini /bootmgr /ntldr /NTDETECT.COM

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 6.03
    Boot sector info:  Syslinux looks at sector 32800 of /dev/sdb1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /EFI/BOOT/grubx64.efi /ldlinux.sys[/HTML]

If you need the rest of the report, you can find it [here]("https://paste.ubuntu.com/p/ZtjzKpr9Ym/")

---

### Post by wildmanne39 on 2019-01-05
*Thread moved to **Windows for a more appropriate fit**.*

---

### Post by oldfred on 2019-01-05
If only Windows, you really need to use Windows repair tools to fix it.
You show an old BIOS/MBR boot partition, but drive is now gpt. 
Windows only boots from gpt with UEFI and you show UEFI boot entry for Windows.

If you press f8 when booting Windows can you get into Windows internal repair console. If not the only choice is a Windows repair flash drive.

May be better to check what error message is and what those knowledgeable on Windows may say.
[https://www.google.com/search?client=ubuntu&channel=fs&q=+0xc000225&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=+0xc000225&ie=utf-8&oe=utf-8)
Windows forums:
       [http://www.tenforums.com/](http://www.tenforums.com/)
[http://www.eightforums.com/](http://www.eightforums.com/)
[http://superuser.com/](http://superuser.com/)

---

