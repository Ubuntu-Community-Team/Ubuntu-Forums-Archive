---
title: "Booting ISO from grub"
date: 2016-08-22
forum: Ubuntu/Debian BASED
---

### Post by LastDino on 2016-08-22
Greetings everyone!

I'm trying to boot ISO from Grub and I've followed instructions from wiki and few tutorials to know what it is

So far, I've done this:
>Made a separate folder called "live" on system partition, which is dev/sda9 partition on my existing dual boot with windows 10. As a root. (My home is not separate partition)
>Copied my ISO file (which is Kali.iso) to this folder as a root.
>Opened 40_custom (in grub.d) folder in gedit as a root (using command gksu gedt /etc/grub.d/40_custom)


Now, here is what I'm not sure about

> #!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry 'Kali Linux' --class os --class gnu-linux --class gnu --class os --group group_main {
set isofile="/live/kali.iso"
insmod ext4
insmod loopback
insmod iso9660      
loopback loop (hd0,9)$isofile      
search --no-floppy --fs-uuid --set=root 657f4609-e940-4dd1-a909-30ca312126d7                            
linux (loop)/live/vmlinuz boot=live fromiso=/dev/sda1/$isofile noconfig=sudo username=root hostname=kali
initrd (loop)/live/initrd.img
}
[B]
Is this structure of the file correct?[/B]

UUID is copied from sudo bilkd for my /dev/sda9 partition, which is default for my existing Linux operating system in this dual boot
exact output
> /dev/sda1: LABEL="WINRE_DRV" UUID="B4EC0243EC01FFFA" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="41ac2c07-59fd-4d9e-8929-85b0815035b8"
/dev/sda2: LABEL="SYSTEM_DRV" UUID="AE04-8F6E" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="14cacb72-b6d0-4507-bf95-1c79e5273884"
/dev/sda3: LABEL="LRS_ESP" UUID="DE07-DDC0" TYPE="vfat" PARTLABEL="Basic data partition" PARTUUID="195a7877-a47e-48ec-8461-5495a30fff87"
/dev/sda5: LABEL="Windows8_OS" UUID="06C00B4EC00B4401" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="9ff9655b-8a49-4616-912f-8db52eadfe06"
/dev/sda6: LABEL="New Volume" UUID="7C2A29002A28B8D2" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="93372d34-5976-4e43-8887-bca3cfcf4405"
/dev/sda7: LABEL="New Volume" UUID="2C0C42F30C42B81A" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="0b5897db-b7f9-4552-a6bd-f38c3fad9d25"
/dev/sda8: LABEL="New Volume" UUID="74B053D1B0539906" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="8d7566bf-bbda-4fd2-b38e-624e18cc6fa7"
/dev/sda9: UUID="657f4609-e940-4dd1-a909-30ca312126d7" TYPE="ext4" PARTLABEL="Basic data partition" PARTUUID="d552ae66-3c05-4493-84ac-18e638304dbb"
/dev/sda10: LABEL="PBR_DRV" UUID="48500DF4500DE990" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="0d987a36-3c5f-4cd2-97c4-cd83736ebeaa"
/dev/sda11: UUID="9b00fd59-fad0-425c-8c70-60bd77a268b7" TYPE="swap" PARTUUID="0bec978e-97c6-475d-be65-2f79b810edef"
/dev/sda4: PARTLABEL="Microsoft reserved partition" PARTUUID="8f6cbae8-6d37-46bc-bce2-2ba3adf7dcdd"


I'm not sure if I'm doing this right and don't have resources atm to do repair work if I brick something. So, please anyone who has knowledge of what this is, please help.

---

### Post by oldfred on 2016-08-22
I found getting path correct as one of the larger issues in configuring loopmounts. 
And I often have to open ISO to see internal path & boot options normally used.

Found this, but older version.

[https://forums.kali.org/showthread.php?1025-Grub2-Loop-Boot-Solution](https://forums.kali.org/showthread.php?1025-Grub2-Loop-Boot-Solution)

You have at least this wrong:
fromiso=[COLOR=#ff0000]/dev/sda1[/COLOR]/$isofile

I would expect that to be sda9.

And you have mounted at /live, but internally in ISO it looks like the kernels are in a /live folder. Those are not the same, so do not get those paths confused.

---

### Post by sudodus on 2016-08-22
Have a look at the following link - scroll down to find a paragraph about Kali.

[https://wiki.archlinux.org/index.php/Multiboot_USB_drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive)

> Kali Linux

    Initramfs framework: initramfs-tools (cmdline: RFD)
    Live framework: Debian Live (cmdline: [21])
    Init system: sysvinit (cmdline: RFD)

```
menuentry "[loopback]kali-linux-1.0.7-amd64" {
	set isofile='/boot/iso/kali-linux-1.0.7-amd64.iso'
	loopback loop $isofile
	linux (loop)/live/vmlinuz boot=live findiso=$isofile noconfig=sudo username=root hostname=kali
	initrd (loop)/live/initrd.img
}
```

---

### Post by yancek on 2016-08-22
The two entries below both worked for me with Kali.  In the example below, the Kali iso file is in the root of partition sda11 so you will have to change that.  Your entry is pointing to the Kali iso under a sub-directory named live which could work if that is where the iso file is.  You need the exact name of the iso and put a set root line in for the partition on which the Kali iso is.

> menuentry "Kali Linux-2.0" {
    set root='hd0,msdos11'
    iso="/kali-linux-2.0-i386.iso"
    bootoptions="findiso=$iso boot=live noconfig=sudo username=root hostname=kali quiet splash"
    search --set -f $iso
    loopback loop $iso
    linux (loop)/live/vmlinuz $bootoptions
    initrd (loop)/live/initrd.img
}


menuentry "kali-linux-2.0" {
    set root='hd0,msdos11'
    set isofile='/kali-linux-2.0-i386.iso'
    loopback loop $isofile
    linux (loop)/live/vmlinuz boot=live findiso=$isofile noconfig=sudo username=root hostname=kali
    initrd (loop)/live/initrd.img
}

---

### Post by howefield on 2016-08-22
Moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by LastDino on 2016-08-22
> **oldfred said:**
> I found getting path correct as one of the larger issues in configuring loopmounts. 
And I often have to open ISO to see internal path & boot options normally used.

Found this, but older version.

[https://forums.kali.org/showthread.php?1025-Grub2-Loop-Boot-Solution](https://forums.kali.org/showthread.php?1025-Grub2-Loop-Boot-Solution)

You have at least this wrong:
fromiso=[COLOR=#ff0000]/dev/sda1[/COLOR]/$isofile

I would expect that to be sda9.

And you have mounted at /live, but internally in ISO it looks like the kernels are in a /live folder. Those are not the same, so do not get those paths confused.

> **sudodus said:**
> Have a look at the following link - scroll down to find a paragraph about Kali.

[https://wiki.archlinux.org/index.php/Multiboot_USB_drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive)

> **yancek said:**
> The two entries below both worked for me with Kali.  In the example below, the Kali iso file is in the root of partition sda11 so you will have to change that.  Your entry is pointing to the Kali iso under a sub-directory named live which could work if that is where the iso file is.  You need the exact name of the iso and put a set root line in for the partition on which the Kali iso is.

Thank you guys. Now I'm able to boot from ISO directly. And as pointed out, path was the issue. 

> menuentry "Kali Linux" {
set root='hd0,msdos9'
iso="/live/kali.iso"
bootoptions="findiso=$iso boot=live noconfig=sudo username=root hostname=kali quiet splash"
search --set -f $iso
loopback loop $iso
linux (loop)/live/vmlinuz $bootoptions
initrd (loop)/live/initrd.img
}

This is what worked, thank you again.

I've couple of questions now,

[LIST=1]
[*]Is there any way to make this a persistent boot?
[*]I read somewhere that it is possible to make multi-boot USB from grub as well, so assuming I've couple of ISO's loaded on Grub, what would I've to do for that?
[/LIST]

And for some reason this post is not visible on latest posts, so I'm making one more post.

---

### Post by sudodus on 2016-08-23
'Persistent live' is managed in different ways by different linux distros.

In Ubuntu, flavours of Ubuntu and re-spins, that have not changed much of the boot system, you can simply provide a partition with the label **casper-rw** and an ext file system. In addition to that, you must add the boot option **persistent**.

I don't know if that will work with Kali, you can try, or you can browse the internet for tips, or if you are lucky, someone who knows will read this and reply with a solution.

-o-

The following link shows what can work with Ubuntu and Debian,

[mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)
[One pendrive for all PC (Intel/AMD) computers - single-boot dual-boot multi-boot](https://ubuntuforums.org/showthread.php?t=2259682)

---

### Post by LastDino on 2016-08-23
> **sudodus said:**
> 'Persistent live' is managed in different ways by different linux distros.

In Ubuntu, flavours of Ubuntu and re-spins, that have not changed much of the boot system, you can simply provide a partition with the label **casper-rw** and an ext file system. In addition to that, you must add the boot option **persistent**.

I don't know if that will work with Kali, you can try, or you can browse the internet for tips, or if you are lucky, someone who knows will read this and reply with a solution.

-o-

The following link shows what can work with Ubuntu and Debian,

[mkusb/persistent]("https://help.ubuntu.com/community/mkusb/persistent")
[One pendrive for all PC (Intel/AMD) computers - single-boot dual-boot multi-boot]("https://ubuntuforums.org/showthread.php?t=2259682")

Thank you! 
I'll try and see where it goes.

Since the original problem is solved, I'll mark the thread as solved. And make new one if I face problem with the persistent boot or multiboot usb.  

You guys are awesome!

---

### Post by sudodus on 2016-08-23
Thanks for sharing your solution and good luck with the new tasks :-)

If you start a new thread, please post a link to it here (in a new reply).

---

### Post by LastDino on 2016-08-23
> **sudodus said:**
> Thanks for sharing your solution and good luck with the new tasks :-)

If you start a new thread, please post a link to it here (in a new reply).

Yes, I'll.

One more thing for lost souls like me, although you could figure this from the documentation 
[https://help.ubuntu.com/community/Grub2/ISOBoot#Menuentry_Details](https://help.ubuntu.com/community/Grub2/ISOBoot#Menuentry_Details)
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples) 

But to make life easy, if anyone wants to boot Ubuntu 16.04 ISO ( x64) from grub, here is what works for me

> 
menuentry 'Ubuntu 16.04' {
set isofile="/live/ubuntu16.04.iso"
loopback loop (hd0,9)$isofile
linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}


Assuming:
1. Like me you're saving the ISO in "live" folder in root (which was created by me), if not change the path according to that
2. You've renamed the ISO image or used exact name in 2nd line where you set isofile
3. You're using correct partition number and using same in 3rd line. For me it was my root which was on /dev/sda9 

After updating and saving this in 40_custom, don't forget to run
> sudo update-grub

Then you should be good to go on next power up.

---

### Post by oldfred on 2016-08-23
You can add as many ISO as you have space for, and then loopmount entries for grub.

But once you get beyond one or two I find it easier to make 40_custom a configfile grub entry that refers to another grub or grub style boot file. I always forget to run the sudo update-grub when I edit the 40_custom. With configfile, 40_custom never changes, but you edit a file in the folder you have for ISO.

With two drives I put an ISO folder on each drive so I can slightly more easily install from one drive to another drive.

```
menuentry 'Live ISOs on SSD' {
configfile (hd0,5)/livecdimage.cfg
} 

menuentry 'Live ISOs on HDD (boot on SSD)' {
configfile (hd1,6)/livecdimage.cfg
} 

```

```
# livecdimage.cfg
# Add this to 40_custom to load this file:
# menuentry 'Live ISOs on SSD' {
# configfile (hd1,6)/livecdimage.cfg
#} 
# Add iso names to livecdimage.cfg
#for i in `ls *.iso`;do echo "# "$i>>livecdimage.cfg; done;


set cmdpath=(hd1,gpt6)
set config_file=(hd1,gpt6)/livecdimage.cfg
set root=(hd1,gpt6)/livecdimage.cfg

menuentry "Ubuntu 16.04 xenial Daily amd64" {
    set isofile="/xenial-desktop-amd64.iso"
    insmod part_gpt
    loopback loop (hd1,6)$isofile 
    linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile
    initrd (loop)/casper/initrd.lz
}

```

But with my current system, even plugging in flash drive changes device order in grub and I have to edit (hd1,gpt6) to another drive when booting in all places as I boot grub then configfile.

---

### Post by yancek on 2016-08-23
An explanation of creating a persistent partition for Kali is at the link below.  It is in reference to using a flash drive but there is not reason you could not do the same by creating another partition on your hard drive for the exclusive use of Kali.  There are two options, with or without encryption.  Personally, I'd just use a flash drive and create persistence.  That's pretty easy to do and with the flash drive (as well as a DVD), you will have a number of options to boot available which you don't when booting the iso directly.  The boot option you have now will not be persistent and even if you create a persistent partition as explained below, you would need to modify your grub.cfg entry.  You can do that by loop mounting the Kali iso and going to the isolinux/live.cfg and taking a look at the entries for persistent boot and modifying it to fit Grub2  

[http://docs.kali.org/downloading/kali-linux-live-usb-persistence](http://docs.kali.org/downloading/kali-linux-live-usb-persistence)

---

### Post by LastDino on 2016-08-25
> **oldfred said:**
> You can add as many ISO as you have space for, and then loopmount entries for grub.

But once you get beyond one or two I find it easier to make 40_custom a configfile grub entry that refers to another grub or grub style boot file. I always forget to run the sudo update-grub when I edit the 40_custom. With configfile, 40_custom never changes, but you edit a file in the folder you have for ISO.

With two drives I put an ISO folder on each drive so I can slightly more easily install from one drive to another drive.

```
menuentry 'Live ISOs on SSD' {
configfile (hd0,5)/livecdimage.cfg
} 

menuentry 'Live ISOs on HDD (boot on SSD)' {
configfile (hd1,6)/livecdimage.cfg
} 

```

```
# livecdimage.cfg
# Add this to 40_custom to load this file:
# menuentry 'Live ISOs on SSD' {
# configfile (hd1,6)/livecdimage.cfg
#} 
# Add iso names to livecdimage.cfg
#for i in `ls *.iso`;do echo "# "$i>>livecdimage.cfg; done;


set cmdpath=(hd1,gpt6)
set config_file=(hd1,gpt6)/livecdimage.cfg
set root=(hd1,gpt6)/livecdimage.cfg

menuentry "Ubuntu 16.04 xenial Daily amd64" {
    set isofile="/xenial-desktop-amd64.iso"
    insmod part_gpt
    loopback loop (hd1,6)$isofile 
    linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile
    initrd (loop)/casper/initrd.lz
}

```

But with my current system, even plugging in flash drive changes device order in grub and I have to edit (hd1,gpt6) to another drive when booting in all places as I boot grub then configfile.

This is actually pretty handy, like you I have tendency to forget running sudo update-grub and then have to power up the machine again to run the command. Also, makes life easier by not having to tinker with the 40_costume directly again and again. 

Thank you!

> **yancek said:**
> An explanation of creating a persistent partition for Kali is at the link below.  It is in reference to using a flash drive but there is not reason you could not do the same by creating another partition on your hard drive for the exclusive use of Kali.  There are two options, with or without encryption.  Personally, I'd just use a flash drive and create persistence.  That's pretty easy to do and with the flash drive (as well as a DVD), you will have a number of options to boot available which you don't when booting the iso directly.  The boot option you have now will not be persistent and even if you create a persistent partition as explained below, you would need to modify your grub.cfg entry.  You can do that by loop mounting the Kali iso and going to the isolinux/live.cfg and taking a look at the entries for persistent boot and modifying it to fit Grub2  

[http://docs.kali.org/downloading/kali-linux-live-usb-persistence](http://docs.kali.org/downloading/kali-linux-live-usb-persistence)

Right now it is little difficult to create extra partition as I've my HD loaded, so I'll try with USB. 

Thank you ones again for sharing valuable knowledge   O:)

---

### Post by C.S.Cameron on 2016-08-25
There is this page on Kali persistence:

[http://docs.kali.org/downloading/kali-linux-live-usb-persistence](http://docs.kali.org/downloading/kali-linux-live-usb-persistence)

For iso/grub2 boot I usually modify the grub.cfg file to get persistence.

Oops, did not notice there was a page 2.

---

