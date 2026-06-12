---
title: "i really need help with GRUB.. &quot;multi-install-sata&quot;"
date: 2016-06-07
forum: Windows
---

### Post by konstrukt777 on 2016-06-07
Hi folks,

i really need your help. ive been since 1 week now, registered to 4 forums... no one could help ..
i will explain the situation in the shortest way :
i often repair systems, laptop etc for friends.. now i need a faster better workflow
lets say - i want to do it that way..

i run a windows 10 x64 machine with 4 hard drives.
1 of these hdds is a 160gb sata drive. 
its actually partitioned this way :

```

X:  NTFS, primary, 20gb, active.      << i put an extracted windows 10 iso there
Y:  NTFS, primary, 20gb                  << i put an extracted windows 8 iso there
Z:  NTFS, primary, 20gb                  << i put an extracted windows 7 iso there
```

i used 

```
cmd.exe as admin
X:
cd \boot
bootsect.exe /nt60 X: /force
``` 
(this made partition X bootable)

now i can put this internal sata drive into any pc and INSTALL windows 10 from it... to any other installed mediums on that pc.


fine.

the problem :

i need a bootmenue/bootloader like this :

1.) ..install windows 10  (background bootloader operations : boot hd0,partition1 ((drive X)
2.) ..install windows 8   (background bootloader operations : boot hd0,partition2 ((drive X)
3.) ..install windows 7   (background bootloader operations : boot hd0,partition3 ((drive X)

i thought, GRUB4DOS would easily be able to do this ?

can anyone send me the correct menu.lst or code snippet, what it would look like ?
i dont know, HOW to install grub4dos onto that internal HDD :(
im really messed up at this point, dont know how to handle this :/

UPDATE :  just needs MBR... maybe UEFI later..

thanks so much

Kon

---

### Post by yancek on 2016-06-07
Format each of the three partitions ntfs, done?
Copy the windows extracted iso to each specific partition, done?

My understanding is that Grub4Dos uses the same type menu and parameters as Grub Legacy which it was originally based so the entry below should work in your menu.lst or grub.conf file.  You would change the title line as appropriate and the root line to point to the correct drive partition.  That X, Y, Z stuff isn't going to do anything.  Are you familiar with Linux/Grub naming conventions?  My experience is that it is not necessary to have each partition marked as active/bootable but if you have problems, that would be the first thing I would change.

> title install win10
root (hd0,1)
chainloader /bootmgr

Details on booting a windows extracted installation iso from Grub2 are at the link below.  It also works with Grub Legacy and should then work with Grub4dos.

[http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html)

---

### Post by konstrukt777 on 2016-06-08
> **yancek said:**
> Format each of the three partitions ntfs, done?
Copy the windows extracted iso to each specific partition, done?

My understanding is that Grub4Dos uses the same type menu and parameters as Grub Legacy which it was originally based so the entry below should work in your menu.lst or grub.conf file.  You would change the title line as appropriate and the root line to point to the correct drive partition.  That X, Y, Z stuff isn't going to do anything.  Are you familiar with Linux/Grub naming conventions?  My experience is that it is not necessary to have each partition marked as active/bootable but if you have problems, that would be the first thing I would change.



Details on booting a windows extracted installation iso from Grub2 are at the link below.  It also works with Grub Legacy and should then work with Grub4dos.

[http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html)


is it possible , to set more than 1 active partition on 1 HDD ?? (i didnt know this..)
but this would not be needed. i thought the bios only scans "active" partitions for bootloaders?
and so 1 bootloader on that first partition on 1 hdd should work fine ?

so i guess for booting also UEFI, i should do it so :

partition 1 x: 20gb FAT32, active primary     windows 10 + grub4dos files
partition 2 y: 20gb NTFS, primary     windows 8
partition 3 z: 20gb NTFS, primary     windows 7


thanks for your help i will take a look for that link... cannot find something useful in german *argh*

WOULD THIS WORK ?
```

title install win10
root (hd0,1)
chainloader /bootmgr

title install win8
root (hd0,2)
chainloader /bootmgr


title install win7
root (hd0,3)
chainloader /bootmgr
```

---

### Post by oldfred on 2016-06-08
I have not tried multi-booting Windows.

But did install Windows repair ISO to flash drive, then installed grub2 into same partition so it booted with grub2 and used a grub2 boot stanza to boot Windows.
I then added Ubuntu ISO, gparted ISO and what else fit on that flash drive to make a repair flash drive. The only issue with grub & Windows was Windows has to have its BCD in /boot and grub installs to /Boot. Windows does not care as it is not case sensitive, but Linux tools are case sensitive and Windows will not work with  duplicate folders. So just have to make sure only one /boot or /Boot, but not both.

You can only have one primary NTFS partition with boot flag (active in Windows) per device. And if UEFI the ESP is the partition with the boot flag, but not the same as in BIOS. Normally Windows uses BCD to add additional boots to one Windows booting from primary NTFS with boot flag.

If after the install, you can move boot flag and run repairs. In some cases you may be able to copy bootmgr & /Boot/BCD, but if versions differences then still may need repairs.
 To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html](http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html)
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
[http://www.multibooters.com/](http://www.multibooters.com/)
[http://www.multibooters.co.uk/articles/windows_seven.html](http://www.multibooters.co.uk/articles/windows_seven.html)
More tech info - BIOS boot process & some UEFI
[http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/windows-nt-6-boot-process.html](http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/windows-nt-6-boot-process.html)

---

### Post by yancek on 2016-06-08
> is it possible , to set more than 1 active partition on 1 HDD ?? (i didnt know this..)

I don't think so.  What I meant was that if the first partition install booted and installed and you then tried the second and it failed to change the active/bootable manually.  I doubt this is necessary.  

> but this would not be needed. i thought the bios only scans "active" partitions for bootloaders?

Windows is the only OS I am aware of that needs a partition to be marked active/bootable in order to boot.  Never been needed with Linux.  I guess some system boards BIOS need it but I don't really know about that.

 > and so 1 bootloader on that first partition on 1 hdd should work fine ?

If I understand what you are doing correctly, you have the extracted iso files of the three different windows on separate partition and with Grub4Dos on the first partition, I would expect it to work if you can get the entries correct.  I put a windows 7 recovery system on one partition and an extracted win 10 iso on a second partition and was able to boot both with a similar method.  

The entries you posted might work.  I used this method on a flash drive which was seen as the first drive (hd0) so I'm not sure how that will work.  If you have the external usb drive set to first boot priority when you use it, it probably will.  Only way to find out is to test it.  

The link I posted above is in regard to doing this using Grub2 which is very different than Grub Legacy and Grub4Dos so if you are using Grub4Dos, some of the suggestions such as menu entries will not work.

---

