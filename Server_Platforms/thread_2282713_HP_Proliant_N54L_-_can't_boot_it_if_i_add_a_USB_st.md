---
title: "HP Proliant N54L - can't boot it if i add a USB stick to it"
date: 2015-06-16
forum: Server Platforms
---

### Post by mastablasta on 2015-06-16
So I am "abusing" the internal USB plug (meant for tape) as System drive. When I was installing I had to boot live USB from it and then I installed to an externally connected USB.

Now system disk (USB) is in internal plug, but if I add an ext4 formatted USB drive (mean for system backups) to any of the outside plugs the system doesn't want to boot. Since I do not have a monitor on it it will take a while before I can see what is actually showing when it boots (I need to move the server to the desktop PC monitor) . but the funny thing is the USB stick doesn't get mounted when I plug it in (refreshing disk drives in Ajenti doesn't help).

But anyway what I can say is result of fsck check and how the disk is formatted (I sued KDE Partition manager to do both). Did I format it wrong in anyway that the system now thinks it can boot from the USB device or is searching for system files on it? because as soon as I unplug the drive and reboot it boots normally.


anyone out there using external USB plugs for additional drives on Proliant server?

---

### Post by PartisanEntity on 2015-06-16
Hi there, yes I have an external USB HDD connected to the external USB sockets on the front of the N54L that I use for backups of the internal drives.

My system disk is an internal SSD drive. I used the internal USB socket to install from a USB stick with Ubuntu on it, on to the SSD disk.

Without attaching a monitor to the server and having a look at the boot process it is hard to see what the issue is. For example it might be hanging at the grub menu and waiting for you to hit enter, it might be hanging at a later stage.

---

### Post by darkod on 2015-06-16
I had a similar issue on my HP Microserver and it was up to a setting in the BIOS. But mine is headless too so I can't check BIOS easily. Don't remember where was the setting exactly (the BIOS options are very few and limited anyway), but it was something about USB and/or booting, the default setting was Fast if I remember correctly, and you need to change it. After that it will boot ignoring the usb stick. It seems with that setting it tries always the usb first, ignoring other boot options.

I'll try to find the google search that helped me...

---

### Post by mastablasta on 2015-06-17
well I guess I need to wait until weekend when I will have time to move the box to the monitor.

I just find it odd and I though I maybe formatted in a way Linux might think the USB can boot. On normal PC's any media is usually ignored if it's not bootable. so you can set the boot order Floppy, CD, USB, hard disk. but unless Floppy, CD, or USB have anything that is bootable they would just get skipped. I guess I need monitor and check the BIOS setting.

I will also try google...

I think I found something: [http://h20566.www2.hp.com/hpsc/doc/public/display?sp4ts.oid=4194735&ac.admitted=1385638674081.876444892.199480143&docId=mmr_kc-0108973-3&docLocale=en_US](http://h20566.www2.hp.com/hpsc/doc/public/display?sp4ts.oid=4194735&ac.admitted=1385638674081.876444892.199480143&docId=mmr_kc-0108973-3&docLocale=en_US)

Does this mean if USB is enabled that besides being able to use external USB to boot I can continue to use the internal one?

edit: one thing that bothers me a bit is this:
> When Legacy USB Disabled is selected, all USB ports are enabled under a USB-aware OS, but USB is not supported during POST or RBSU. Legacy USB Disabled also disables iLO 2 virtual devices.

As I understand RBSU is meant as BIOS and POST is well POST. But the only way to add keyboard to server is via USB and I use Measy12 wireless USB keyboard/mouse to interact with it. in any case you need USB to work in BIOS as well as to trigger BIOS screen to load in POST. though USB storage is not needed in BIOS or at POST screen. 

I have a kid that likes to press things and would often unplug USB key while I work on my desktop. something about the USB sticks attracts them :-).

---

### Post by mastablasta on 2015-06-20
all i get on boot is a blinking cursor (i i boot with USB key inside the plug), and for some raason BIOS recognises the mouse/keyboard device i use (measy 12 keyboard), however it doesn't react when i press the F10, so i can't get into BIOS. it also succesfully recognises and identifies the USB drive (name and all) as well as the ones in the RAID array.

as a bonus i now also have 

```
Error: Malformed file.
Press any key to continue...

```
on boot (it then proceeds to boot normally) this looks like it's there after some latest updates.

and system talks about zombie processes running when i login, but nothing when i log in via SSH.

---

### Post by mastablasta on 2015-07-06
well I tried various BIOS settings (after borrowing a keyboard that could get into BIOS) but it doesn't look like it's a BIOS issue alone. it looks that at some point the system GRUB might be involved.

it looks like as soon as both kingstongs are in only one gets recognised by the BIOS. when I stick in the no name Chinese USB I can choose in BIOS the boot priority of the two. probably Toshiba would also provide such an options. so I guess I need to get a Toshiba or something and then set it up as secondary boot?! but why won't it work with 2 Kingstons?

By the way can I sue 64 GB FAT USB 32 to do system backups with rdiff-backup? I am guessing that not but I am not sure if backups get compressed - do they keep the file ownership and permissions?

I tried various options (removed all flags from Kingston, reformatted it as fat32) - Kingston 8GB is where the OS is installed:

[TABLE="class: grid, width: 500"]
[TR]
[TD]**Internal USB**
[/TD]
[TD]**External USB**
[/TD]
[TD]**OS Boot**
[/TD]
[/TR]
[TR]
[TD]Kingston 8GB
[/TD]
[TD]Kingston 16GB, ext4
[/TD]
[TD]no boot, blinking cursor
[/TD]
[/TR]
[TR]
[TD]Kingston 8GB
[/TD]
[TD]/
[/TD]
[TD]boot
[/TD]
[/TR]
[TR]
[TD]Kingston 8GB
[/TD]
[TD]Kingston 8GB, FAT32
[/TD]
[TD]no boot, blinking cursor
[/TD]
[/TR]
[TR]
[TD]Kingston 8GB
[/TD]
[TD]Toshiba 16GB, FAT 32
[/TD]
[TD]Toshiba boots in live session
[/TD]
[/TR]
[TR]
[TD]/
[/TD]
[TD]Kingston 8GB
[/TD]
[TD]boot
[/TD]
[/TR]
[TR]
[TD]/
[/TD]
[TD]Kingston 8GB, Toshiba 16GB
[/TD]
[TD]Toshiba boots in live session
[/TD]
[/TR]
[TR]
[TD]Kingston 8GB
[/TD]
[TD]no name Chinese 64 GB, fat32
[/TD]
[TD]boot, 64GB recognised
[/TD]
[/TR]
[TR]
[TD]Kingston 16GB, ext4
[/TD]
[TD]Kingston 8GB
[/TD]
[TD]no boot
[/TD]
[/TR]
[TR]
[TD]Kingston 8GB
[/TD]
[TD]500GB WD USB NTFS HDD
[/TD]
[TD]boot
[/TD]
[/TR]
[TR]
[TD]/
[/TD]
[TD]Kingston 8GB, no name Chinese 64 GB, fat32
[/TD]
[TD]boot, 64GB usb 
mounted
[/TD]
[/TR]
[/TABLE]

EDIT: I forgot to add one curious thing. and that is that when I booted with both USB keys and then went into BIOS. If I would pull one USB drive out and then exited BIOS no changes save it would continue until it arrived to grub at which point Grub rescue mode was displayed. quite strange indeed. which made me think that it's not completely BIOS fault.

---

### Post by mastablasta on 2015-12-17
some time a bit of money on my hands and well nothing more found out except that it will also not boot with the SanDisk inside.
when i stil it in at a working server i get the following informaiton of the new SanDisk USB key:

sudo fdisk -l says (removed the RAID array):

```


Disk /dev/sdc: 7776 MB, 7776239616 bytes
255 heads, 63 sectors/track, 945 cylinders, total 15187968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009a81f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63    15181424     7590681   83  Linux

[COLOR=#0000ff][B]Disk /dev/sdd: 16.0 GB, 16005464064 bytes
255 heads, 63 sectors/track, 1945 cylinders, total 31260672 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              32    31260671    15630320    c  W95 FAT32 (LBA)[/B][/COLOR]
```

parted -l says:
```

Model: KINGSTON DataTraveler 3.0 (scsi)
Disk /dev/sdc: 7776MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  7773MB  7773MB  primary  ext4         boot


[B][COLOR=#0000ff]Model: SanDisk Cruzer Fit (scsi)
Disk /dev/sdd: 16.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      16.4kB  16.0GB  16.0GB  primary  ext4         lba[/COLOR]
[/B]
```

any ideas?

---

### Post by sudodus on 2015-12-17
I can add my experience with middle-aged (not very old, not very new) HP computers (but no server, only a work station, some desktops and notebooks),

- They are usually good at booting USB drives made from cloned Ubuntu family iso files (made with dd or mkusb).

- They are fuzzy with USB drives with installed systems (and in general booting from grub). Sometimes it helps to add the boot flag to the boot partition, even if it *should* not be necessary with grub (and is not necessary in other computers).

So in your /dev/sdd, you could try if it helps to add a boot flag. I don't think you need the lba flag, but if you can have both flags, it is probably good.

---

### Post by mastablasta on 2015-12-17
i don't want it to boot from[B][COLOR=#0000ff] SanDisk Cruzer Fit (scsi)   
[/COLOR][/B]
The SanDisk should be just automounted and then used as "storage device". I just formated it with KDE partition manager (gparted for KDE) to ext4. didn't do any chowns or anything like that. i think what it does is that it tries to boot from SanDisk (or various other USB drives) but since there is no os on it it ends up with a blinking cursor. although it is strange as usually BIOS woudl say no OS found (or is that MBR & Grub?!).

edit: do i maybe need to use something like USBmount or udevil? to automount the other USB stick?! althoug hit is being recognised when i plug it in it is not being mounted.

---

### Post by darkod on 2015-12-17
Was this usb stick bootable before at any time? What is often forgotten is that formatting the stick does not delete the MBR boot sector. The blinking cursor is standard sign of grub being on the MBR but no grub files to continue the booting.

Trying zeroing the MBR sectors that hold the bootloader. Don't remember the exact numbers now (I think it was 442 bytes from the start, not to delete the partition table). But you have no data on the stick to lose anyway, so you can zero first 512 bytes. That will delete boot sector and partition table. Just make a new partition later and try it.

If it does have grub boot sector and USB is before HDD in the boot options, it might actually be trying to boot it.

---

### Post by mastablasta on 2015-12-18
no it's a freshly opened USB stick that just arrived in the mail. but interesting - i got an idea. what if i added grub to the other disk? and then maybe mirror them or something?

---

### Post by sudodus on 2015-12-18
I think that I don't understand your configuration - and your problem.

- Are you running the computer with one USB drive, or with more than one USB drive?
- Is it necessary to boot from USB?
- Is the problem, that you can't control which USB drive is selected by the booter?
- Is the problem booting at all from USB (in this bay meant for tape)?

---

### Post by darkod on 2015-12-18
The way I understood it, his HP Proliant Microserver is booting just fine as standard machine with internal HDDs. That works...

What he's complaining about, is that if he leaves usb stick connected and powers on, the machine doesn't boot. When it should boot from internal HDD too. He doesn't want to boot from usb.

That's why I thought the usb stick might have broken grub and is first in boot order, so the machine stops booting at the broken grub and doesn't even try the HDD MBR.

I'm not sure if I had a similar problem with my Microserver. Try looking in the bios for an option about booting from usb/removable storage and put it after HDD in the boot order. I think that helped me. However I don't recall what exactly I did, it was quite a while ago...

Or simply completely disable usb booting. When you need it you can always enable it.

---

### Post by sudodus on 2015-12-18
I see darko. Your tips are worth trying :-)

@ mastablasta, more tips: - would it be an option to use a second SATA or an eSATA drive instead of USB? What about other USB ports (not the one in the bay meant for tape)?

---

### Post by mastablasta on 2015-12-19
> **sudodus said:**
> I think that I don't understand your configuration - and your problem.

- Are you running the computer with one USB drive, or with more than one USB drive?
- Is it necessary to boot from USB?
- Is the problem, that you can't control which USB drive is selected by the booter?
- Is the problem booting at all from USB (in this bay meant for tape)?

had a medical emergency so wasn't much online...

Currently i am booting from internal USB (which is ment for tape).

the OS is on USB, the data is on RAID1 hard disk array.

So 
/ is on USB

/data is RAID1 (software - mdadm)
/swap is RAID1 (software - mdadm)


the internal USDB boots fine but as soon as i add an external one it looks like it is trying to boot from that. even if i add two USB drive on external plugs (one with OS an done with nothing on it - even fat32 formated) it still give a blinking cursor. however if i add a USB hard disk to external plug it would all boot just fine.

so the setup is - OS installed on USB, that is then backed up weekly or maybe monthly is enough as well to another USB. data is on hard drives. in case the OS goes bad i can reinstall it. it already happened and the setup porved good. i just had to replace the USB disk (cheap) and restore the backup. the problem is before i was making backup of OS manually (unplug USB, create image plug it back in) now i want to do it automatically.

i need to check if it can boot from e-sata. otherwsie a cheaper version would porbably still be to just get an external USB hard drive since they do not seem to interfere with the boot process. a 120GB SSD (kingston) costs about 50 EUR here. a 500 GB external USB HDD cost 50 EUR.:o both cost way more than 16 GB USB which i got for 5,50 EUR :D

maybe it's just me just being cheap again...

---

### Post by darkod on 2015-12-19
Ah, ok. So I didn't understand it correctly... If you are booting from usb stick I can see how the boot process is confused by adding another stick. Even if it has no bootloader on it.

I wouldn't expect usb sticks boot to work as with HDDs, where it tries all internal HDDs in a row until it finds a bootloader to boot.

Besides, how many sticks you need in the machine? :) Plug the second one after the boot and that's it. This issue happens only on boot right? You don't reboot servers that often, even home servers... So is it really such a big issue?

---

### Post by sudodus on 2015-12-19
I wish you get well soon :-)

Is the second USB drive there in order to receive the backup of the operating system? Or some other reason? I would say '+1' to darko's suggestion to plug it in after booting.

My experience is that some UEFI/BIOS systems, for example on IBMs and Lenovos, can manage more than one USB drive, but many UEFI/BIOS systems cannot, they just grab the first USB drive they find. If that is the case in your computer, it will be hard to control which USB drive to boot from. Maybe the reason why a USB HDD does not interfere is that it is slower to get powered up (needs to get the disk spinning etc), so your USB boot drive is found first.

---

### Post by mastablasta on 2015-12-22
> **darkod said:**
> Ah, ok. So I didn't understand it correctly... If you are booting from usb stick I can see how the boot process is confused by adding another stick. Even if it has no bootloader on it.

I wouldn't expect usb sticks boot to work as with HDDs, where it tries all internal HDDs in a row until it finds a bootloader to boot.

Besides, how many sticks you need in the machine? :) Plug the second one after the boot and that's it. This issue happens only on boot right? You don't reboot servers that often, even home servers... So is it really such a big issue?

i wanted to have two for starters. there is room for 6 USB devices in external USB sockets :O well i also do some other updates that occasionally need a reboot. i see now what the problme is. the HDD is recognised as HDD but USB flash drive doesn't get probed that way. would it help if it was premounted?

> **sudodus said:**
> I wish you get well soon :-)

Is the second USB drive there in order to receive the backup of the operating system? Or some other reason? I would say '+1' to darko's suggestion to plug it in after booting.

My experience is that some UEFI/BIOS systems, for example on IBMs and Lenovos, can manage more than one USB drive, but many UEFI/BIOS systems cannot, they just grab the first USB drive they find. If that is the case in your computer, it will be hard to control which USB drive to boot from. Maybe the reason why a USB HDD does not interfere is that it is slower to get powered up (needs to get the disk spinning etc), so your USB boot drive is found first.

well i need to get some ultrasound first, then we'll see. hopefully it can be resolved without operation.
 
anyway, yes i wanted to use the second USB as a backup. occasionally it seem the server does require a reboot, so then it would get stuck i guess. at leats if i did it remotelly.

so it looks like the BIOS doens't probe the USB drives first, the boot from the one with bootloader, but instead just attempts to boot from one of them. And then if there is no OS on it it is just stuck. that's interesting... i think i need another option, but in the mean time i just might have to plug/unplug one drive. or look into getting an external hard disk. though the one i tried had NTFS. i don't know how it would act if i added ext3 on it.

---

### Post by whatwasthat on 2015-12-27
> **darkod said:**
> Was this usb stick bootable before at any time? What is often forgotten is that formatting the stick does not delete the MBR boot sector. The blinking cursor is standard sign of grub being on the MBR but no grub files to continue the booting.

Trying zeroing the MBR sectors that hold the bootloader. Don't remember the exact numbers now (I think it was 442 bytes from the start, not to delete the partition table). But you have no data on the stick to lose anyway, so you can zero first 512 bytes. That will delete boot sector and partition table. Just make a new partition later and try it.

If it does have grub boot sector and USB is before HDD in the boot options, it might actually be trying to boot it.

Thanks for this tip - it was exactly the problem.
I used Minitool Partition magic to over write the MBR record, and re-created the Ubuntu install USB disk again (after reformating the drive again) and it worked :)
Thanks for the tip

---

