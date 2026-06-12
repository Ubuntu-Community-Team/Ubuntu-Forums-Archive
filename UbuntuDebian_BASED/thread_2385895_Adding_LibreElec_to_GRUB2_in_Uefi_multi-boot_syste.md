---
title: "Adding LibreElec to GRUB2 in Uefi multi-boot system - Using Grub costumizer"
date: 2018-02-26
forum: Ubuntu/Debian BASED
---

### Post by xcj on 2018-02-26
Hi guys.
 

 

 My system used to have an nvme drive formated in MBR format and had a  Windows10 partition and a LibreElec Partition, to create a multiboot  menu and set LibreElec as default i just added the LibreElec to the boot  menu using EasyBCD and changed it to default and everything worked.
 

 

 Recently i decided to convert my system to UEFI/GPT, and things were not so simple.
  

 

 Now my nvme drive has Windows10 only (GPT/UEFI).
 

 I have another smaller 16GB nvme drive with LibreElec only (UEFI too)
 

 And now i have UBUNTU on a 32GB USB 3.0 drive.
  

 

 Since Easy BCD isn't much use in a UEFI system,  i decided to try EasyUefi.
 

  From EasyUefi i am able to set "one-time boot" for LibreElec and  Ubuntu, and both systems boot correctly that "one-time" and the second  reboot boots windows again.
  

 From the motherboard UEFI (what we call BIOS these days :)) i can boot all three systems.
 

 From inside Ubuntu the command "uefibootmgr" shows me the three systems available.
 

 

 But what i want is a boot menu, and set it default for LibreElec.
 

 

 I was able from the motherboard UEFI to set the UBUNTU boot loader as the default boot priority.
  

 And in the UBUNTO boot loader i have GRUB2 wich can now boot Windows 10 and Ubuntu.
 

 I installed the Grub Costumizer in UBUNTO and i already changed the label for the Windows 10 entry, and set it to default.
 

 

 All there's left to do is to add LibreElec to GRUB2.
 

 

 I tried to add it selecting the LibreElec partition in it's nvme  drive in GRUB COSTUMIZER, but i get the error "unable to set the boot  sequence - check parameters"
 

  I found some instructions to add OpenElec and LibreElec on this forum  and others, but the way to do it was much more command line based and  there are some variables that i don't know how to adjust to my system.
 

 
[INDENT]                                       
                                                Quote                          
                   
[LIST=1]
[*]menuentry "LibreELEC" { 
[*]    set root=(hd0,5) 
[*]    linux /KERNEL boot=/dev/sda5 disk=/dev/sda6 quiet 
[*]} 
[/LIST]
     
          [/INDENT]
The set root line, if the disk is listed as /dev/sda5 as the case above, is "hd0,5" , in my case i have:
 

  /dev/nvme1n1p1 ->system, vfat
 /dev/nvme1n1p2 ->storage, ext4
 

 **What do i place on the "set root" ?**
 

 [B]Also, in grub customizer, how do i add LibreElec? "Linux",  "Chainloader" , "Other" or "Script Code" ?
[/B]
  I feel i'm close, just need these two questions answered! Thanks in advance!

---

### Post by oldfred on 2018-02-26
Know nothing about grub customizer nor LibreElec.

Are all systems installed in UEFI boot mode?
Chain loader type entry would then be to ESP - efi system partition.

Have you tried?
sudo update-grub

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Often best not to have separate /boot partition with most desktops.

---

### Post by xcj on 2018-02-26
Hi olfred,

All systems are in UEFI boot mode.

sudo update-grub produced no changes

Pastebin from boor-repair:
[http://paste.ubuntu.com/p/sTzByKrr7m/](http://paste.ubuntu.com/p/sTzByKrr7m/)

The 4TB NTFS is just data.
The 500Mb NTFS (2 part) is just from past experiments, will be wiped and reporpused.
The 16GB USB is where UBUNTU is installed
The 14GB nvme is where LibreElec is installed (the one missing from GRUB)
The 250 nvme is where i have windows installed, and also where the Ubunto bootloader runs.

Many thanks!

---

### Post by oldfred on 2018-02-26
See line 522
>  Windows is hibernated, refused to mount. 
But not sure if an issue or not. Script finds the required unformatted partitions and thinks they should be NTFS and then says it is an error. (not really script, but Linux commands it is running).
If not hibernated, then grub in Ubuntu would add a chain entry to Windows.

Report also uses bootinfoscript, which has not been updated to include all the details on NVMe devices. So top part of report does not show the NVMe drives.

Your sda, sdb & sdc all say this:

> GUID Partition Table detected, but does not seem to be used.


If using UEFI, better to eventually convert all drives to gpt. I started back with BIOS system in 2010 to use gpt. And soon started to convert all new or reformatted drives to gpt. And then when Windows 8 came out requiring UEFI/gpt, I added both bios_grub for BIOS boot on then current system and ESP - efi system partition for future UEFI boot. Actually bought new drives for new UEFI system, but still add both partitions to all new drives.

Can you mount /dev/nvme1np1 and /dev/nvme1np2
p1 should be ESP. And have folder for LibreElec and/or grub. Post contents of folder & grub.
And p2 should be LibreElec. Post its /etc/fstab.

If you had Windows drive connected when installing LibreElec, then it probably would have used the ESP on /dev/nvme0np1.
Ubuntu's UEFI grub only installs to first drive. But some other distributions do let you install to other ESPs on other drives.

If you want to chain load, you can in effect copy Windows UEFI boot entry, which should be similar to these. If UUID, then it must the UUID of ESP with Windows boot folder.

```
 menuentry "Windows bootmgfw.efi UEFI" {
  search --file --no-floppy --set=root /efi/Microsoft/Boot/bootmgfw.efi
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
} 

   menuentry "Windows bootmgfw.efi " {
search --fs-uuid --no-floppy --set=root 18FE-69D8
chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
} 


```

---

### Post by xcj on 2018-02-26
Here are the contents of both partitions mounted in ubunto:

**Contents of partition 1:**

xcj@Sofagamer:~/nvme1n1p1$ ls -l
total 219716
drwxr-xr-x 3 root root      4096 fev 23 01:25 EFI
-rwxr-xr-x 1 root root  12054800 fev 23 01:25 KERNEL
-r-xr-xr-x 1 root root    122308 fev 23 01:25 ldlinux.c32
-r-xr-xr-x 1 root root     69632 fev 23 01:25 ldlinux.sys
-rwxr-xr-x 1 root root       105 fev 23 01:25 syslinux.cfg
-rwxr-xr-x 1 root root 212729856 fev 23 01:25 SYSTEM

xcj@Sofagamer:~/nvme1n1p1$ cd EFI/
xcj@Sofagamer:~/nvme1n1p1/EFI$ ls
BOOT
xcj@Sofagamer:~/nvme1n1p1/EFI$ cd BOOT/
xcj@Sofagamer:~/nvme1n1p1/EFI/BOOT$ ls
bootx64.efi  ldlinux.e64  syslinux.cfg

xcj@Sofagamer:~/nvme1n1p1/EFI/BOOT$ more syslinux.cfg 
DEFAULT linux
PROMPT 0
 
LABEL linux
 KERNEL /KERNEL
 APPEND boot=LABEL=System disk=LABEL=Storage  quiet

**Contents of partition 2:**

xcj@Sofagamer:~/nvme1n1p2$ ls -l
total 40
drwxr-xr-x 2 root root  4096 fev 23 01:26 backup
drwx------ 2 root root 16384 fev 23 01:25 lost+found
drwxr-xr-x 2 root root  4096 fev 23 01:26 music
drwxr-xr-x 2 root root  4096 fev 23 01:26 pictures
drwxr-xr-x 2 root root  4096 fev 23 01:26 screenshots
drwxr-xr-x 2 root root  4096 fev 23 01:26 tvshows
drwxr-xr-x 2 root root  4096 fev 23 01:26 videos

---

### Post by xcj on 2018-02-26
Offred, first of all for the help!

Just want to be sure you understand what i am trying to do.

Windows and Ubunto are working just fine, i can select either one from GRUB's boot menu, just want to add LibreElec to the boot menu but not sure on how to do it.

LibreElec does not use grub , it's a lightweight linux + KODI distro to run KODI as an appliance and have all system related configurations done from it's user interface, it has no option to install alongside with windows like ubunto does.

I have no issues with any drive, and do not plan to install other systems on them, if i did i would probably convert to GPT.

Also, i am able to boot all three systems from the UEFI (Motherboard "bios"), i just want LibreElec on GRUB.

Many thanks!

---

### Post by oldfred on 2018-02-27
I did read somewhere that syslinux had updates to use UEFI boot.
The Ubuntu installer uses syslinux for BIOS boot and grub for UEFI boot on same installer.

I do not know syslinux well.
It looks like it uses the standard hard drive or fallback entry. That is /EFI/Boot/bootx64.efi.
Then it has moved kernel into ESP partition and its configuration boots from those paths/files.
Your original entry may have worked with something using /dev/nvme1n1p1     where ESP is and paths to /KERNEL.
But I would have to experiment to convert syslinux paths & parameters to grub versions.

But you can chain load to the ESP with LibreElec and still then use syslinux to boot.
Check what its UUID is and paste into entry below in 40_custom.
       sudo blkid -c /dev/null -o list
lsblk -o NAME,LABEL,PARTLABEL,SIZE,UUID,MOUNTPOINT 

       Example to boot to fallback, update xxxx-xxxx with correct UUID:
```
menuentry "LibreElec UEFI" {
search --fs-uuid --no-floppy --set=root xxxx-xxxx
chainloader (${root})/EFI/Boot/bootx64.efi 
} 
```

sudo -H gedit /etc/grub.d/40_custom
or
sudo nano -B /etc/grub.d/40_custom
Then do:
sudo update-grub 

If this works (of course it is going to work .... or maybe not) please post back your entry.
I have a long list of working grub boot stanzas and will add it to the list.

---

### Post by xcj on 2018-02-27
Hey oldfred,

It appears to be a sintax error, but i don't see where, also i correct the path "Boot" with "BOOT", didn't do the "lsblk -o NAME,LABEL,PARTLABEL,SIZE,UUID,MOUNTPOINT" command, since i did not understand the purpose or how to fill in all the variables.
[B]
output of "sudo blkid -c /dev/null -o list"[/B]

device               fs_type   label      mount point              UUID
-------------------------------------------------------------------------------------------------------
/dev/nvme1n1                              (not mounted)            
/dev/nvme1n1p1       vfat      System     (not mounted)            5A8F-6D7A
/dev/nvme1n1p2       ext4      Storage    (not mounted)            283a7f25-4cb4-43ec-bbce-9852804b1bbe
/dev/nvme0n1                              (in use)                 
/dev/nvme0n1p1       ntfs      Recovery   (not mounted)            E0AA8372AA8343CE
/dev/nvme0n1p2       vfat                 /boot/efi                6E83-C363
/dev/nvme0n1p3                            (not mounted)            
/dev/nvme0n1p4       ntfs                 (not mounted)            400A846C0A846130
/dev/sda1                                 (not mounted)            
/dev/sda2            ntfs      Games Landing (not mounted)         7016A5A616A56DB2
/dev/sdb1            ntfs                 (not mounted)            760A351E0A34DCB5
/dev/sdb2            ntfs      New Volume (not mounted)            785261DE5261A19C
/dev/sdc1            ext4                 /                        262b805d-e90a-401b-a99e-36131a20015e

**grub 40_custom:**

xcj@Sofagamer:/etc/grub.d$ more 40_custom
menuentry "LibreElec UEFI" {
search --fs-uuid --no-floppy --set=root 5A8F-6D7A
chainloader (${root})/EFI/BOOT/bootx64.efi
}

**update grub error that indicates the sintax error:**

xcj@Sofagamer:/etc/grub.d$ sudo update-grub
Generating grub configuration file ...
using custom appearance settings
Found background image: /home/xcj/Downloads/Digital-Polygon-Wallpaper-1920x1080.jpg
Found linux image: /boot/vmlinuz-4.13.0-36-generic
Found initrd image: /boot/initrd.img-4.13.0-36-generic
Found linux image: /boot/vmlinuz-4.13.0-21-generic
Found initrd image: /boot/initrd.img-4.13.0-21-generic
/etc/grub.d/40_custom: 1: /etc/grub.d/40_custom: menuentry: not found
/etc/grub.d/40_custom: 2: /etc/grub.d/40_custom: search: not found
/etc/grub.d/40_custom: 3: /etc/grub.d/40_custom: Syntax error: word unexpected (expecting ")")

---

### Post by oldfred on 2018-02-27
Did you erase the default lines at beginning of 40_custom. Those are required.

Your more command should have also shown this:

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

```

I also have this as I just wanted to see differences in grub2 with Fedora to Ubuntu's grub2.
But I also have a lot of other entries also. And this is booting Fedora's grub in an ESP on sdb, not the standard one on sda, so should be very similar to yours.

```
menuentry "Fedora UEFI" {
  search --file --no-floppy --set=root F496-1330
  chainloader (${root})/efi/fedora/grub.cfg
}

```

---

### Post by xcj on 2018-02-27
It worked!! 

So the sintax error was the default-lines in 40_custom that were missing!
I already changed it in grub customizer to be the default boot.
Project complete! 

I know i have only been talking to you since yesterday, but i can say without any hesitation: You da Man! :P

---

### Post by oldfred on 2018-02-27
Glad you got it working.  :)

---

