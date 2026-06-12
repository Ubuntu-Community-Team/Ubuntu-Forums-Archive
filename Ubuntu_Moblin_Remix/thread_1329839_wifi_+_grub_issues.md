---
title: "wifi + grub issues"
date: 2009-11-17
forum: Ubuntu Moblin Remix
---

### Post by denis6902 on 2009-11-17
**Grub:**

After installing ubuntu NBR i get a weird error which never happened before, only when i select my WIN7 partition to load.

I used gparted live disk, delete both linux and swap partitions, applied, created new ones, installed NBR finely! no problems,

but if i choose win7 at grub start, i get that grubDos error (RED BACKGROUND), then if i press ESC i have lots of options on how to start windows. I always go with the one which says (default) 1st option on the list, and it boots win7 just fine.

Can i fix this? Has anyone seen this before?


**Wifi:**
**Hardware:**
**Motherboard:** Zotac Mini-ITX N330 ION

**Wireless Devices Tested:**
Atheros AR928X Wireless Network Adapter **(Mini PCIE)**
Atheros AR5007UG Wireless Network Adapter **(USB)**

I tried using the stock wireless **(Mini PCIE) **and somehow i keep loosing my wifi. I made sure i went to check my router settings, and its all good. **They work fine on WIN7** being used solely or both ENABLE. No dropped connections, no errors, no nothing and STRONG signal 3-4 bars, mostly on 4 bars.

I tried using the second one only**(USB)**, DISABLING the PCIE and still the same issues which appeared before. Back to windows7, fine as usual no issues, 4-5 bars, mostly 4bars.

I tried using both of them ENABLE, and same issues again. Keep loosing the wifi!
When it connects, i have STRONG signal for less then a min, then i see the bars getting smaller until i reach the point i dont have wifi (All this happens between **1-2 min max**) which is quite fast.

It all seems to be something missing in the drivers initial pack i think. 

sudo apt-get update **DONE**
sudo apt-get upgrade **DONE**

Does anyone knows how to fix this bug? Do i need to install some sort of backport drivers for it to function better? Can this be fixable? 

Best Regards and Thanks in advance to all,

denis6902

---

### Post by denis6902 on 2009-11-18
no one? i cannot believe i am the only one getting this :(

---

### Post by denis6902 on 2009-11-19
i have no idea whats going on with this grub or grub2, just being a PITA!!!

I Even manage to loose everything today, not even linux was booting anymore, thanks god **SUPERGRUB DISK** helped to get the linux working at least!

As soon as the pc is booting i get GRUB saying press ESC to options:
linux
linux recovery
win7
memtest

From there linux, and recovery run fine. But if i choose win7 i get:
**ERROR 12 - Invalid Device Requested&#8206;**

I am afraid that if i use Gpated live cd to delete swap and linux partition and install it again it wont solve my problem. It seems that there is something wrong with the lines for the Windows initialization. [B]

What do i do?[/B]
[B]Can someone Help me out Please!?
Should i just format everything?

***no peeps for this silly grub2, very confusing and difficult to use! [-X
[/B]previous versions of ubuntu were way easier to use with the old simple grub
its way to complicated for beginners like myself. ](*,)


Terminal:
$ **sudo fdisk -l:**
```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00001e6e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         261     2096451   82  Linux swap / Solaris
/dev/sda2             262        3133    23069340   83  Linux
/dev/sda3            3134       16187   104856255    7  HPFS/NTFS
/dev/sda4           16188      121601   846737955    5  Extended
/dev/sda5           16188      121601   846737923+   7  HPFS/NTFS

```Terminal:
**$ gksu gedit /boot/grub/menu.lst**

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        8

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=3379f60d-7a05-4747-865d-fb55be2ca6ad ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3379f60d-7a05-4747-865d-fb55be2ca6ad

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.10
uuid        3379f60d-7a05-4747-865d-fb55be2ca6ad
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=3379f60d-7a05-4747-865d-fb55be2ca6ad ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, (recovery mode)
uuid        3379f60d-7a05-4747-865d-fb55be2ca6ad
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=3379f60d-7a05-4747-865d-fb55be2ca6ad ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Windows 7 Ultimate Loader
rootnoverify    (hd0,3)
makeactive
chainloader        +1
boot

title        Ubuntu 9.10, memtest86+
uuid        3379f60d-7a05-4747-865d-fb55be2ca6ad
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by denis6902 on 2009-11-19
What a hell!

Ok, i managed to rescue my windows back, and i am indeed happy because most of my work is here on win7 partition. I am not fully happy as the fix removes grub from mbr, therefore the pc will boot automatically in WINDOWS, [B]NO GRUB.

Intructions:[/B]

**1-**
```
Restart your PC with WIN7 dvd/cd in
```**2-**
```
Press a key to boot from cd
```**3-**
```
Windows will ask you language and keyboard config, please preceed with that
```**4-**
**ATTENTION:** 
```
Do not reintall the whole OS, at the bottom of this section you will see REPAIR WINDOWS, somethig like that

```**5- **
```
Go to COMMAND PROMPT

```**6-**
**Please enter this on the Command Prompt:**
```
**bootrec.exe /fixboot**
```you will/probably see sucessfull

**and this one also**
```
**bootrec.exe /fixmbr**
```you will/probably see sucessfull

**7-**
```
 Close Command Prompt
```**8-**
```
 Reboot your PC without the CD/DVD from the device!
```**9-**
```
 YES!!! WINDOWS IS BACK without loosing files or having to reinstall everything from scratch!
```**10-**
```
 Give me beeeeeeeeeeeeeeeeeeeens!
```

Now, i really would like to have the linux back to be fully happy! 
However i really dont want to have GRUB2 (grub-pc), its way to complicated and annoying!

How should i get my linux back without having **grub2** and without loosing my win7 partition again?
[B]
SUPERGRUB DISK?[/B]
**UBUNTU LIVE CD?**

What would be the best way to have the old, good and stable **GRUB **with my partitions booting properly?

---

### Post by Orkun Sensebat on 2009-12-29
Seems like a corrupt installation.

I myself am considering to buy one of these boxes and i read (admittedly only some) reviews of people that installed 9.10 with xbmc and reported 100% functionality. No one ever reported major problems.

I would recommend for you to wipe out the hard disk and start again with a fresh install. Just install - if needed - Windows first, should not take more than 2 partitions. then ubuntu - you have 2 alternatives: direct installation and live cd, if one does not work, use the other. these are 2 more partitions.

ubuntu can read ntfs perfectly, if you really need win on a regular basis, make one of the win partitions huge and ntfs.

there is really no reason at all not to install ubuntu again under these circumstances - if you don't want to or can't because of a lack of backup possibilities - you could just use any linux live cd (like linux), start it and then simply install grub again on mbr. I would try to use the setup installer and skip steps, if that is not supported, use google instead. but you can install grub only from any live cd (use newest ubuntu though, it implemented a major grub update).

i only recommend these two scenarios: if you want to only use windows, kill everything from mbr using repair utilities and only use windows boot loaders.
if you want to use both, always install windows first and then let grub handle the rest (using a simple and clean ubuntu installation).


It would be nice, if you would keep me posted on the zotac mag's support as I want to buy one tomorrow. I just found out it should use a AR928x for WIFI. Anyhow, xbmc VDPAU full hd 1080p at low cpu was reported by plenty of users working without any configuration or whatsoever. All this for 240 euros.

---

