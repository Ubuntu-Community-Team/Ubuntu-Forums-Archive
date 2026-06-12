---
title: "grub2 add windows 10 to menu?"
date: 2017-04-09
forum: Windows
---

### Post by Jan_Johansson on 2017-04-09
ASUS ROG G551VW  with UEFI GPT partitioning and factory installed windows 10 64bit.  XUbuntu 16.04 installed secondary on sda5.
Installation of XUbuntu went fine and when boot grub comes up - but:

Windows 10 boot menu is wrong and boots to  windows recovery instead of going to windows desktop. 

I need help editing grub and correct the windows 10 grub entry, can you guys help me on that, working windows 10 entry will go long way with instructions on how to implement it?

Ubuntu 16.04 boots just fine.

 Please don't refer to boot-repair, it does not work with 16.xx. When running it, it will  give you commands to paste into terminal and these commands are  depreceated so they will fail, then boot-repair can't continue and you  can only chose discard which will remove grub totally from the system  and delete most files needed to repair or re-install grub - it's a  nightmare I had to deal with yesterday - trying to manually re-install  grub running from live media fails because boot-repair removed the  needed files including grub-install, grub-common, grub-pc,  /etc/default/grub /boot/grub/grub.cfg, 40_custom and so on. Supergrub2  disc saved me and re-installed grub but only partially -  /etc/default/grub /boot/grub/grub.cfg, 40_custom is still missing. So I  got /etc/default/grub from my own pc and it seem to  be the same.  Point being, don't use boot-repair with 16.xx.

grub customizer indicating missing files
[https://www.dropbox.com/s/p0hiheko4uwc39b/IMG_20170408_213421.jpg?dl=0 ]("https://www.dropbox.com/s/p0hiheko4uwc39b/IMG_20170408_213421.jpg?dl=0")

grub windows 10 not working entry
[URL="https://www.dropbox.com/s/iu94zgtd04zdffw/IMG_20170408_215354.jpg?dl=0"]https://www.dropbox.com/s/iu94zgtd04zdffw/IMG_20170408_215354.jpg?dl=0
[/URL]
Current partition table
[URL="https://www.dropbox.com/s/52wpanh4mcpu8w0/IMG_20170408_215846.jpg?dl=0"]https://www.dropbox.com/s/52wpanh4mcpu8w0/IMG_20170408_215846.jpg?dl=0
[/URL][URL="https://www.dropbox.com/s/52wpanh4mcpu8w0/IMG_20170408_215846.jpg?dl=0"]
[/URL]

---

### Post by oldfred on 2017-04-09
Do not know Grub Customizer. It does create its own grub files, replacing the standard files.

Boot-Repair would only reinstall grub boot stanza or fully delete & reinstall all of grub in advanced options.
But it is grub's own os-prober that is run with every update or manually with that finds other systems to boot:
sudo update-grub

But we need to see lots of details and easiest just to run the Summary report from Boot-Repair as that has almost all the info we normally need.

 May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by Jan_Johansson on 2017-04-10
Hi Oldfred, I'm sorry but I'm not going to mess around with boot-repair again until the errors and bugs are corrected, i already filed case with the developer.

What I like to do is:

1. manually edit Grub to fix the Windows 10 entry. just need some guidance on how to do that since never done it on grub2, only grub legacy menu.lst.

Please don't send me to other sites to read, i wasted allot of time already reading and reading and reading and none of the options have made me being able to fix this yet.


2. How to re-install grub-update, grub-install, without messing with the system as it is now - because windows 10 is the only not working, Xubuntu boot just fine.


Anyone who has a similair system _**please**_ post their working windows 10 grub2 entry here, so I can modify it and use on my friends laptop.

Jan

---

### Post by oldfred on 2017-04-11
My fear is that it is Grub Customizer, not Boot-Repair.
Customizer seems to be good for minor edits to grub, but for major changes writes its own versions of grubs boot files.

Boot-Repair really is only running standard commands using a gui to make it easier for those users who do not like terminal commands. Plus it combines many commands together.

All you should every need for working system is:
sudo update-grub

But grub only boots working Windows. And that means Windows cannot be hibernated (fast start up off) or needing chkdsk. 
When grub does not see or let you boot Windows then you have to directly boot with f10 or f12 whatever is UEFI direct boot.

This entry works on my Dell. It has my UUIDs and my ESP is sda1. Created by grub2's os-prober.

```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows Boot Manager (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-efi-68E4-107D' {
    insmod part_gpt
    insmod fat
    set root='hd0,gpt1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  68E4-107D
    else
      search --no-floppy --fs-uuid --set=root 68E4-107D
    fi
    chainloader /EFI/Microsoft/Boot/bootmgfw.efi
}

```

---

