---
title: "Howto help USB boot drives"
date: 2013-12-31
forum: Tutorials
---

### Post by sudodus on 2013-12-31
[SIZE=4]Content of the posts
[/SIZE]
1. A tool that helps boot some computers from [other] USB boot drives - Chainloader - (This first post, no link needed)

2. [Check download and clone image in Windows]("http://ubuntuforums.org/showthread.php?t=2196858&p=12888237#post12888237")

3. [Chainloading with the 40_custom method when you have linux and grub installed]("http://ubuntuforums.org/showthread.php?t=2A196858&p=12892978#post12892978")

4-5. [Add a pendrive to grub simply by inserting the pendrive and doing 'sudo update-grub']("http://ubuntuforums.org/showthread.php?t=2196858&p=12893689#post12893689")

6. [Pendrive speed test]("http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085")

7. [Pendrive ability to boot]("http://ubuntuforums.org/showthread.php?t=2196858&p=12907221#post12907221")

8. [Pendrive lifetime]("http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297")

9. [Repair the partition table and file system of a pendrive](http://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986)

13. [Checking the iso file and the boot drive - detailed tips](http://ubuntuforums.org/showthread.php?t=2196858&p=13511608#post13511608)

14. [Restore a USB boot drive](https://ubuntuforums.org/showthread.php?t=2196858&p=13543602#post13543602)

[HR][/HR]
[SIZE=4]A tool that helps boot some computers from [other] USB boot drives - Chainloader[/SIZE]

What is new, why this tutorial, when I have already written [Howto make USB boot drives]("http://ubuntuforums.org/showthread.php?t=1958073")? Isn't it enough to be able to use ***mkusb*** or the other tools?

It can be hard to boot some computers with some USB pendrives. New and fast USB 3 pendrives are nice when booted, but can be unwilling to boot from the built in menu of some computers. This is described at the following links

[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)
[https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB](https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB)

I have found, that

- the same USB pendrive can boot with one operating system, but not another one, in some computers, while it boots happily in other computers with almost any operating system,

- the Ubuntu 13.04 based grub2 bootloader is 'a good booter' in many computers (it is used in the original [One Button Installer]("http://ubuntuforums.org/showthread.php?t=2172971")),

- many USB pendrives boot when selected from the grub menu, even if they will not boot from the built in menu of some computers.

So I made a small ***chainloader***, that

- is willing to boot and

- is able to chainload to other pendrives or other mass storage devices.

When this chainloader is installed into a pendrive, that is good for booting (but maybe slow), we have a tool to help [other] USB boot drives.
[SIZE=4]
Comparison with Plop[/SIZE]

Maybe you have used or heard of [Plop]("http://www.plop.at/en/bootmanagers.html"), a tool to boot from one device (typically a CD or floppy drive) and help booting another drive, typically a USB drive. That tool is useful for old computers. The ***chainloader*** is useful for middle-aged computers, for example computers without a CD/DVD drive, where it can be hard to boot from a USB drive, and when you want to run from a fast USB 3 drive that is unwilling to boot.

[SIZE=4]UEFI[/SIZE]

New computers are often delivered with another operating system that is locked into UEFI, which makes things complicated. This chainloader is not running in UEFI mode. Use other tools and methods, for example according to the following links

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

[SIZE=4]
Pendrives that are good for booting[/SIZE]

The following pendrives were tested by [Pendrivelinux]("http://www.pendrivelinux.com/recommended-usb-flash-drives/") a few years ago. At least some of them are still available in the market (and I do *not* mean the second hand market)

SanDisk – Cruzer Micro 128M-2G
RIDATA – Ritek Mini Spin 128M-2G
OCZ – Rally2 (Old Style) 128M-2G
OCZ – Mini Kart 128M-1-2G
PQI – PQI i810 1-2G
PNY – Attache 1-2G

I have SanDisk – Cruzer Micro 4 GB and 16 GB, and they are also good booters.

I have ***SanDisk – Cruzer Blade 4 GB ***(I bought a 10-pack). They are good booters and quite cheap (at least in Sweden) and I can recommend them for the ***chainloader***.

[SIZE=4]USB 3 pendrives[/SIZE]

The [Kingston DataTraveler Ultimate G2 16GB]("http://usb.userbenchmark.com/Kingston-DataTraveler-Ultimate-USB-30-16GB/Rating/1271") USB 3 pendrive is tested and recommended as a good booter by [http://usb.userbenchmark.com/](http://usb.userbenchmark.com/) but it can be hard to find in the market today.

I have [Sandisk Extreme USB 3.0 16GB and 32GB]("http://usb.userbenchmark.com/SanDisk-Extreme-USB-30-32GB/Rating/1466") and they are very fast and give good value for the money. I have also a Transcend [JetFlash 700 USB 3.0 32GB]("http://usb.userbenchmark.com/Transcend-JetFlash-700-USB-30-32GB/Rating/1276"). It is not very fast compared to Sandisk Extreme but definitely faster than standard USB 2 pendrives and a good booter, that I have tested for a long time. I use it for the One Button Installer; there is space enough for many tarballs. ***Sandisk Cruzer Blade 4 GB ***is cheap and slow, and a reliable booter, that has only failed once for me during years.

Tests of speed and ability to boot are described in posts #6 and #7 (in this thread).

[SIZE=4]The Chainloader software[/SIZE]

A compressed image file of the chainloader software is available at the following links

[http://phillw.net/isos/linux-tools/](http://phillw.net/isos/linux-tools/)
[https://drive.google.com/folderview?id=0B46yhFQuJvfPbjNIMERBaFJiSjA&usp=sharing](https://drive.google.com/folderview?id=0B46yhFQuJvfPbjNIMERBaFJiSjA&usp=sharing)

```
-rw-r--r-- 1 root root 24426712 dec 31 23:41 chainloader-101MB_13.04.img.xz
```

The corresponding md5sum is

```
8d41e2873511e08c05a1ddc3c061d230  chainloader-101MB_13.04.img.xz
```

and it can be installed with the following command (if ***mkusb*** is in the same directory)

```
sudo bash mkusb chainloader-101MB_13.04.img.xz
```

***mkusb*** helps you write to the correct target device (your pendrive). The ***chainloader*** expands from 24MB to 101MB. You can use a small pendrive (if it is a good booter).

The file [FONT=courier new]**grub.cfg**[/FONT] looks like this (and you can modify it if you wish)

```

set timeout=20
set default=1

#echo listing available drives (hdX) and partitions (hdX,msdosY) 
#ls
#echo -n "Press ESC to continue to the menu "
#sleep -v -i ${timeout}

menuentry "Boot (chainload) first drive (on hd0) usually internal, maybe not now" {
        insmod part_msdos
        insmod fat
        set root='(hd0)'
        chainloader +1
}
menuentry "Boot (chainload) drive (on hd1)" {
        insmod part_msdos
        insmod fat
        set root='(hd1)'
        drivemap -s (hd0) ${root}
        chainloader +1
}
menuentry "Boot (chainload) drive (on hd2)" {
        insmod part_msdos
        insmod fat
        set root='(hd2)'
        drivemap -s (hd0) ${root}
        chainloader +1
}
menuentry "Boot (chainload) drive (on hd3)" {
        insmod part_msdos
        insmod fat
        set root='(hd3)'
        drivemap -s (hd0) ${root}
        chainloader +1
}
menuentry "Boot (chainload) drive (on hd4), edit if necessary: set root='(hd5)' ..." {
        insmod part_msdos
        insmod fat
        set root='(hd4)'
        drivemap -s (hd0) ${root}
        chainloader +1
}
menuentry "List available drives (hdX) and partitions (hdX,Y)" {
    ls
    echo -n "Press ESC to continue to the menu "
    sleep -v -i 20
}
menuentry "Long list drives (hdX) and partitions (hdX,Y)" {
    ls -l
    echo -n "Press ESC to continue to the menu "
    sleep -v -i 20
}
menuentry "Long list drive 1 (hd1) and partition 1 (hd1,1), edit if necessary" {
    ls -l (hd1,1)
    echo -n "Press ESC to continue to the menu "
    sleep -v -i 20
}

```

[SIZE=4]Chainloading with the 40_custom method when you have linux and grub installed[/SIZE]

In the particular case, that you have linux and grub installed there is also the **40_custom**  method, ***and it is better than using a USB chainloader***. As already described, some pendrives boot from grub even if they won't boot from the  computer's own (bios/uefi) USB boot menu entry. See the a detailed description in post #3.

---

### Post by sudodus on 2014-01-01
[SIZE=4]Check download and clone image in Windows[/SIZE]

First download the ***chainloader ***and **md5sums.txt** from this [link(1)]("http://phillw.net/isos/linux-tools/") or [link(2)]("https://drive.google.com/folderview?id=0B46yhFQuJvfPbjNIMERBaFJiSjA&usp=sharing").

 Then download the following help programs  

[http://www.md5summer.org](http://www.md5summer.org) 
[http://www.7-zip.org](http://www.7-zip.org) 
[http://sourceforge.net/projects/win32diskimager](http://sourceforge.net/projects/win32diskimager) 

Check that the download was successful with **md5summer** according to the file **md5sums.txt**.

Next extract the image file with **7-zip**

from ***chainloader-101MB_13.04.img.xz*** to ***chainloader-101MB_13.04.img***

Then prepare to write the extracted image file (without the ending xz) with **win32diskimager** according to the picture. Win32diskimager looks for **img** files.  Don't mind that the picture is borrowed from another project and contains another file name.

[COLOR=#ff0000]***WARNING***: Double-check that the target device is the correct one (in the window of **win32diskimager**) before you start writing! [/COLOR]Otherwise you might overwrite and destroy important data.[COLOR=#ff0000]
[/COLOR]
[IMG]https://help.ubuntu.com/community/grub-n-iso?action=AttachFile&do=get&target=win32diskimager2.jpg[/IMG]

Using **win32diskimager **is described with screenshots in the following link [https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

---

### Post by sudodus on 2014-01-06
[SIZE=4]Chainloading with the 40_custom method when you have linux and grub installed[/SIZE]

In the particular case, that you have linux and grub installed there is also the **40_custom**  method, ***and it is better than using a USB chainloader***.  As already described, some pendrives boot from grub even if they won't  boot from the  computer's own (bios/uefi) USB boot menu entry. See the  following link  for a background about grub [Scripts: /etc/grub.d/]("https://help.ubuntu.com/community/Grub2/Setup#Scripts:_.2BAC8-etc.2BAC8-grub.d.2BAC8-") 

Edit the file

```
sudo nano /etc/grub.d/40_custom
```

Add the following text to the file **40_custom** (notice that it is important to keep the first lines, that come with the file) 

```
menuentry "External drive (on hd1) if no eSATA drive connected. edit if necessary" {
        insmod part_msdos
        insmod fat
        set root='(hd1)'
        drivemap -s (hd0) ${root}
        chainloader +1
}
```

and run the command

```
sudo update-grub
```

Then  you will get a grub menu option to boot from a second drive (hd1),   which could be a USB pendrive. If another drive is hd1, you can edit  the  line to (hd2) etc. 
If there is no grub menu, press the **left shift key** during boot, and it should appear.

---

### Post by C.S.Cameron on 2014-01-06
The truly lazy should be able to add a pendrive to grub, without going to 40_custom, simply by inserting the pendrive and doing:
```

sudo update-grub
```

---

### Post by sudodus on 2014-01-07
Yes, I agree that it is a very convenient method, and should be enough in many cases, but I think it will be specific for that particular pendrive and its current operating system.

---

### Post by sudodus on 2014-01-22
[SIZE=4]Pendrive speed test[/SIZE]

I made this speed test because I make installers that use cloning with dd and expansion of compressed tarballs. So the test measures the speed of those particular operations. See also the general speed tests at this [link to USB 3.0 Flash Drive Speed Tests]("http://usb.userbenchmark.com/")

The focus of this test was on 8 GB drives, because I make 8 GB images for the One Button Installer, but there are also some 4, 16, 32 GB pendrives, that I know after years of usage.

When using USB pendrives, you often notice that they are slow compared to internal disks. There are big differences between fast and slow pendrives, and it makes a big difference, when you use them as general mass storage devices, but the difference seems to be even bigger, when you boot an operating system, that is installed in the pendrive.

USB 3 is much faster than USB 2. The flash hardware is often limiting the read and write speed below the limits of the USB system. USB 3 pendrives are often but not always made with faster hardware than standard USB 2 pendrives. This makes it worthwhile to use USB 3 pendrives in USB 2 ports, so USB drives can be useful also with old computers without USB 3.

Reading and writing single or few big files can be fairly fast with USB pendrives, but the time to start and stop writing is often much longer in pendrives compared to hard disk drives and SSDs. It makes many pendrives very slow when writing many small files, like when you install an operating system or backup a file system or directory tree. This is why I included a test expanding a tarball with many small files. It is actually installing the text version of the One Button Installer, writing 68417 files with the total data amount 1.2 GB. The average file size is 17.7 kB (10-base). The complete result of the test is shown in attached files, and includes reading and writing single big files with dd.
[SIZE=4]
Write small files MB/s
[/SIZE]***in USB 2 port***
```

18.989    SanDisk Extreme (scsi) / new 32 GB
17.855    SanDisk Extreme (scsi) / new 16 GB - undersized
 5.224    Kanguru SS3 (scsi) / 16 GB - undersized
 4.673    SanDisk Extreme (scsi) / old 32 GB - damaged
 3.797    Kanguru FlashBlu (scsi) / 8GB USB 2, write-protect switch
 3.313    JetFlash Transcend 32GB (scsi) / 'new 700' good booter - undersized
 2.953    JetFlash Transcend 16GB (scsi) / 'old 700' USB 3 &#8211; undersized
 2.769    JetFlash Transcend 4GB (scsi) / old with green rim
 2.731    Kingston DT Ultimate G3 (scsi) / 32GB USB 3 - undersized
 2.629    SanDisk Ultra (scsi) / 8 GB USB 2
 2.561    Kingston DataTraveler 3.0 (scsi) / 100 G3 8GB - undersized
 2.446    SanDisk Cruzer Blade (scsi) / 4 GB, USB 2, good booter
 2.257    JetFlash Transcend 8GB (scsi) / 760 USB 3 - undersized
 2.091    JetFlash Transcend 8GB (scsi) - 500 USB 2
 1.923    UFD 2.0 Silicon-Power8G (scsi) / Ultima U01
 1.680    Verbatim STORE N GO (scsi) / 8GB - undersized
 1.427    Corsair Voyager (scsi) / 8GB USB 2 'Flash Voyager'
 1.294    Kingston DataTraveler 2.0 (scsi) / 101 G2 8GB - undersized

```
***in USB 3 port***
```

32.333    TOSHIBA External USB 3.0 (scsi) / HDD 320 GB
23.926    SanDisk Extreme (scsi) / 16 GB - undersized 15693664256 bytes
23.006    SanDisk Extreme (scsi) / 32 GB
 8.365    Kanguru SS3 (scsi) / 16 GB - undersized
 4.747    JetFlash Transcend 32GB (scsi) / 'new 700' good booter - undersized 31608274944 bytes
 4.069    Kanguru FlashBlu (scsi) / 8GB USB 2, write protect switch
 3.987    Kingston DT Ultimate G3 (scsi) / 32GB USB3 - undersized 31440502784 bytes
 2.795    JetFlash Transcend 16GB (scsi) / 'old 700' USB 3 - undersized 15812526080 bytes
 2.658    Kingston DataTraveler 3.0 (scsi) / 100 G3 8GB undersized 7803174912 bytes
 2.583    JetFlash Transcend 8GB (scsi) / 760 USB 3 -undersized 7902068736 bytes
 2.187    SanDisk Cruzer Blade (scsi) / 4GB, USB 2, good booter

```

[SIZE=4]Read 2 GB file with random content (cloning with dd) [SIZE=4] MB/s[/SIZE]
[/SIZE]***in USB 2 port***
```

36.1    SanDisk Extreme (scsi) / old 32 GB, damaged works only in USB 2
36.1    SanDisk Extreme (scsi) / new 32 GB
36      JetFlash Transcend 16GB (scsi) / 'old 700' USB 3 &#8211; undersized
36      SanDisk Extreme (scsi) / new 16 GB - undersized
35.9    Kingston DataTraveler 3.0 (scsi) / 100 G3 8GB - undersized
35.9    JetFlash Transcend 32GB (scsi) / 'new 700' good booter - undersized
35.3    Kanguru SS3 (scsi) / 16 GB - undersized
32.8    Kingston DT Ultimate G3 (scsi) / 32GB USB 3 - undersized
30.4    JetFlash Transcend 8GB (scsi) / 760 USB 3 - undersized
29.2    Kanguru FlashBlu (scsi) / 8GB USB 2, write-protect switch
22.2    SanDisk Cruzer Blade (scsi) / 4 GB, USB 2, good booter
21.9    SanDisk Ultra (scsi) / 8 GB USB 2
21.3    JetFlash Transcend 8GB (scsi) - 500 USB 2
20.5    Kingston DataTraveler 2.0 (scsi) / 101 G2 8GB - undersized
20.2    Corsair Voyager (scsi) / 8GB USB 2 'Flash Voyager'
17.9    Verbatim STORE N GO (scsi) / 8GB - undersized
15.1    UFD 2.0 Silicon-Power8G (scsi) / Ultima U01
14.9    JetFlash Transcend 4GB (scsi) / old with green rim

```
***in USB 3 port***
```

104      SanDisk Extreme (scsi) / 16 GB - undersized 15693664256 bytes
 74.6    Kanguru SS3 (scsi) / 16 GB - undersized
 64.1    TOSHIBA External USB 3.0 (scsi) / HDD 320 GB
 60.1    JetFlash Transcend 32GB (scsi) / 'new 700' good booter - undersized 31608274944 bytes
 59      Kingston DT Ultimate G3 (scsi) / 32GB USB3 - undersized 31440502784 bytes
 51.6    JetFlash Transcend 16GB (scsi) / 'old 700' USB 3 - undersized 15812526080 bytes
 49.3    JetFlash Transcend 8GB (scsi) / 760 USB 3 -undersized 7902068736 bytes
 38.9    Kingston DataTraveler 3.0 (scsi) / 100 G3 8GB undersized 7803174912 bytes
 37.8    SanDisk Extreme (scsi) / 32 GB
 28.7    Kanguru FlashBlu (scsi) / 8GB USB 2, write protect switch
 20.3    SanDisk Cruzer Blade (scsi) / 4GB, USB 2, good booter

```
[SIZE=4]Write 2 GB file with random content (cloning with dd)[/SIZE] [SIZE=4] MB/s[/SIZE]
***in USB 2 port***
```

29.5    SanDisk Extreme (scsi) / new 32 GB
27.5    SanDisk Extreme (scsi) / new 16 GB - undersized
26.9    SanDisk Extreme (scsi) / old 32 GB default (finished with tar)
20.9    JetFlash Transcend 16GB (scsi) / 'old 700' USB 3 &#8211; undersized
17.4    Kingston DT Ultimate G3 (scsi) / 32GB USB 3 - undersized
16.9    SanDisk Extreme (scsi) / old 32 GB full test finished with dd
16.3    Kanguru SS3 (scsi) / 16 GB - undersized
13.9    JetFlash Transcend 32GB (scsi) / 'new 700' good booter - undersized
10.9    Kanguru FlashBlu (scsi) / 8GB USB 2, write-protect switch
 7.8    SanDisk Ultra (scsi) / 8 GB USB 2
 7.2    JetFlash Transcend 4GB (scsi) / old with green rim
 7.1    UFD 2.0 Silicon-Power8G (scsi) / Ultima U01
 5.9    JetFlash Transcend 8GB (scsi) / 760 USB 3 - undersized
 5.9    JetFlash Transcend 8GB (scsi) - 500 USB 2
 5.1    Kingston DataTraveler 3.0 (scsi) / 100 G3 8GB - undersized
 4.9    Corsair Voyager (scsi) / 8GB USB 2 'Flash Voyager'
 4.7    SanDisk Cruzer Blade (scsi) / 4 GB, USB 2, good booter
 4.1    Verbatim STORE N GO (scsi) / 8GB - undersized
 3.2    Kingston DataTraveler 2.0 (scsi) / 101 G2 8GB - undersized

```
***in USB 3 port***
```

88      TOSHIBA External USB 3.0 (scsi) / HDD 320 GB
44.1    SanDisk Extreme (scsi) / 16 GB - undersized 15693664256 bytes
43.6    SanDisk Extreme (scsi) / 32 GB
30.0    Kanguru SS3 (scsi) / 16 GB - undersized
25.9    Kingston DT Ultimate G3 (scsi) / 32GB USB3 - undersized 31440502784 bytes
20.8    JetFlash Transcend 16GB (scsi) / 'old 700' USB 3 - undersized 15812526080 bytes
20.5    JetFlash Transcend 32GB (scsi) / 'new 700' good booter - undersized 31608274944 bytes
10.5    Kanguru FlashBlu (scsi) / 8GB USB 2, write protect switch
 5.7    JetFlash Transcend 8GB (scsi) / 760 USB 3 -undersized 7902068736 bytes
 5.4    Kingston DataTraveler 3.0 (scsi) / 100 G3 8GB undersized 7803174912 bytes
 4.7    SanDisk Cruzer Blade (scsi) / 4GB, USB 2, good booter


```

[SIZE=4]Comments[/SIZE]

***Sandisk Extreme*** is much faster (approximately 3 times faster than the second best, ***Kanguru SS3***, and 5 times faster than the third best, ***Jetflash Transcend 700***) writing 'many small files' compared to the other tested pendrives, but not as fast as a USB 3 HDD. ***Kanguru FlashBlu*** was fastest writing 'many  small files' among the 8 GB pendrives, even though it is a USB 2 device  and competed with some USB 3 devices.

***There are several pendrives that read single big files with high speed***, so if that is what you need, there are many good candidates. Writing speed of single big files differs more than reading, but the results are more even than writing 'many small files', and the ranking is somewhat different. See also the attached files.

[SIZE=4]Disclaimer[/SIZE]

This is a fairly simple speed test without statistical validation. The pendrives were bought as a regular consumer from a web store, and in most cases a single specimen of each model was tested. Make your own test, if you need reliable results for your particular application.

-o-

***Edit***: There was a request from the Lubuntu mailing lists to upload the scripts and input files to perform this test (or a similar one), so they are uploaded now. See this link

[http://phillw.net/isos/linux-tools/usb-speed-test/](http://phillw.net/isos/linux-tools/usb-speed-test/)

---

### Post by sudodus on 2014-01-22
[SIZE=4]Pendrive ability to boot[/SIZE]

If you want to use a USB pendrive to boot computers, it is important that it is a good booter. Most pendrives (that are not damaged) can boot most computers, but some of them have problems. The USB hardware and firmware on the motherboard might have problems with the pendrive. You can say that some pendrives do not cooperate with some computers.

I made this bootability test because I make installers and help programs and script for installers. The focus of this test was on 8 GB drives, because I make 8 GB images  for the One ButtonInstaller, but there are also some 4, 16, 32 GB  pendrives, that I know after years of usage.

***Booting from a computer's built in boot menu***

This is a survey of the ability to boot from a computer's built in boot menu. Several pendrives were tested in some different computers. It is far from a complete or statistically validated test, but I hope it can help to select a pendrive when it is important to boot from it. At least it will show some aspects that you should consider before deciding what to buy.

It may be possible to boot via the Chainloader, even if the computer cannot boot the pendrive and it's system from the built in boot menu.
[SIZE=4]
0. The pendrives are listed in alphabetical order.[/SIZE]

The focus was on 8 GB drives, because I make 8 GB images for the One ButtonInstaller, but there are also some 4, 16, 32 GB pendrives, that I know after years of usage.

Corsair Flash Voyager 8 GB, USB 2
Kanguru Flashblu2 8GB, USB 2
Kingston DT 100 G3 USB 3, 8 GB
Kingston DT 101 G2 USB 2, 8 GB
Kingston DT Ultimate G3 USB 3, 32 GB
Sandisk Cruzer Blade USB 2, 4 GB
Sandisk Cruzer Ultra USB 2, 8 GB
Sandisk Extreme (USB 3), 16, 32 GB
Transcend Jetflash 500 USB 2, 8 GB
Transcend Jetflash 700 USB 3, 16, 32 GB
Transcend Jetflash 760 USB 3, 8 GB
Verbatim Micro 8 GB, USB 2

[SIZE=4]1. All tested pendrives can boot the following computers[/SIZE]

Toshiba Satellite Pro C850, Toshiba Satellite Pro A300, Asus (motherboard) M2N-VM DVI, Dell Dimension 4600, IBM Thinkpad T42

[SIZE=4]2. HP Elitebook 8560p boot problems - typical of 'middle-aged to newer' HP professional class laptops[/SIZE]

With an exception for an 'old 32 GB' Sandisk Extreme (USB3), all pendrives booted in a similar way (but at very different speed). Booting from cloned iso files and Unetbootin systems works. Booting from grub2 works with the version of grub that comes with Ubuntu 14.04 LTS, when the **boot flag** is added to the partition.

The following comment might explain why I have considered Sandisk Extreme a poor booter:

- A Sandisk Extreme 'old 32 GB' (USB3) can boot the chainloader but not the built in OBI. This pendrive works well in most situations in USB 2 ports, but after an (electronic?) damage, it is extremely slow in USB 3 ports. This pendrive has 'always' been a poor booter, even before the damage. Maybe it was a bad specimen from the beginning. Newer Sandisk Extreme pendrives show as good booting ability as Transcend 700.

[SIZE=4]3. IBM Thinkpad T42 boot problems[/SIZE]

Corsair Flash Voyager 8GB USB 2 seemed to work (the LED was flashing) but it never finished the booting (after 'Loading initial ramdisk ...'). After 'hard reset' and cold boot (power off and waiting a minute) it booted correctly.

Transcend Jetflash 500 8GB USB 2 was not recognized by the BIOS, so it could not be selected. It failed several times. It was recognized by the BIOS when connected via a USB hub, and then it could boot.

The other pendrives work properly (but of course, this IBM has a Pentium M CPU, so it cannot boot iso files with PAE kernels). See this link

[https://help.ubuntu.com/community/Lubuntu-fake-PAE](https://help.ubuntu.com/community/Lubuntu-fake-PAE)

[SIZE=4]4. Compaq Presario 5640 boot problems[/SIZE]

This computer is very old, has a Pentium II CPU with 400 MHz and 192 MB RAM. ***It can boot from USB via Plop***, but there are problems with some USB pendrives and systems on them.
[I][B]
The following pendrives can boot[/B][/I] the 'OBI version 2.2 text' based on Ubuntu mini-iso 13.10. I used nomodeset to get it running. There are some error outputs, but nevertheless booting continues and succeeds with most of the tested pendrives.

Corsair Flash Voyager 8 GB, USB 2
Kanguru Flashblu2 8GB, USB 2
Kingston DT 100 G3 USB 3, 8 GB
Kingston DT Ultimate G3 USB 3, 32 GB
Sandisk Extreme 'new 32 GB' (USB 3)
Transcend Jetflash 500 USB 2, 8 GB
Transcend Jetflash 700 USB 3, 16 GB
Transcend Jetflash 760 USB 3, 8 GB
Verbatim Micro 8 GB, USB 2

***The following pendrives do not work because they are not found*** after the Plop bootloader transfers control to the USB system.

Kingston DT 101 G2 USB 2, 8 GB
Sandisk Cruzer Blade USB 2, 4 GB (which has worked 'everywhere' before)
Sandisk Cruzer Ultra USB 2, 8 GB

The OBI version 2.2 booted via the USB chainloader did not work. Probably chainloading twice {Plop - USB chainloader - final system} will lose track of some important data.

***Test of extra pendrives (for this very old computer)***

A **Transcend Jetflash 520S 32 GB, USB 2** 'very small pendrive with metal casing' boots with Xubuntu Precise installed. An **old Sandisk Cruzer Micro 4GB**  with Ubuntu Boot Repair could boot too. An **old Sandisk Cruzer Micro 16 GB**  with OBI version 2.1 based on Lubuntu 13.10 booted, but the system did  not want to run properly. The pendrive itself worked.

[SIZE=4]Comments[/SIZE]

Most pendrives in this test are good booters. Some of them fail to boot some computer. The computers are very different in age and type, but it is hard to draw any definite conclusions about computers not tested as well as pendrives not tested. You should also notice, that in some cases the operating system (at least the bootloader) makes a difference. This was the case with the HP laptop.

So get a fast pendrive unless the price is too high! You can also choose between  one fast USB 3 pendrive and use it as a temporary device (flash the iso file, image file or data set when you need it), or several standard USB 2 pendrives, which you dedicate to different systems or data sets. I can buy ten Sandisk Cruzer Blades (4GB) for about the same price as two Sandisk Extreme 16 GB or one Sandisk Extreme 32 GB. Jetflash Transcend 700 and Kingston DT Ultimate G3 USB 3, 32 GB, are also good choices, somewhat cheaper and slower than Sandisk Extreme.

[SIZE=4]Disclaimer[/SIZE]

This is a fairly simple boot test without statistical validation. The  pendrives were bought as a regular consumer from a web store, and in  most cases a single specimen of each model was tested. Make your own  test, if you need reliable results for your particular application. You should also notice that this test does not evaluate the lifetime or sensitivity to damage of the pendrives.

---

### Post by sudodus on 2015-01-02
[SIZE=4]Pendrive lifetime[/SIZE]

***Memory cards and USB pendrives have the same kind of hardware inside, so this post is relevant to memory cards too.***

USB pendrives have a rather bad reputation concerning lifetime, but there is evidence that they have improved, and can last quite long nowadays, at least when managed in a good way.

> "The reports of my death have been greatly exaggerated."
Mark[COLOR="#0000CD"]us B[/COLOR] Twain 

Summing the information up a couple of years ago:If  you don’t physically ruin your drive,  you have about ***1,500 connections*** and about ***10,000 write cycles*** for each memory cell before  you can expect the USB pendrive or flash card to fail. This is typical for ***MLC*** flash memory cells. ***SLC flash memory lasts ten times longer*** and is used in solid state drives (SSD) and *it seems also* in some expensive pendrives. Probably the average has improved now, but we can expect differences depending on the manufacturing process.

The market is changing. Search the internet for ***pendrive slc***. I found that the 'MX-ES Series USB3.0 pendrive' utilizes SLC NAND according to the manufacturer, and also 'Winkom USB-3.0 Pendrive SLC DDR flash'. Recently (in 2015) I found a USB 3 pendrive with built-in trim and S.M.A.R.T commands. It is still way too expensive, but soon such pendrives will probably be common and cheap. [See this link](http://www.kingston.com/datasheets/DTWS_us.pdf).

[COLOR=#0000cd]***When old pendrives get slower*** (typically reduce the writing speed to half), I ***wipe the whole device*** with[/COLOR] [mkusb]("https://help.ubuntu.com/community/mkusb#Wipe_the_whole_device") [COLOR=#0000cd](overwrite with zeros). That way I have recovered the original (or near original) write speed.[/COLOR] I think it is a way to relieve the internal management of the memory cells (connecting logical cells with physical cells, maybe by releasing cells that have been written to seldom because they have been storing data). But don't do it too often, because of the wear.

***When a pendrive or memory card is read-only***
[LIST]
[*]On some pendrives and on many memory cards there is a small mechanical switch for write protection, that can toggle between read/write and read-only. You might have set it read-only without intention.
[*]Reboot the computer and try again to wipe the first megabyte with [mkusb](https://help.ubuntu.com/community/mkusb/wipe).
[*]Disconnect other USB devices. Sometimes USB devices can disturb the function for each other.
[*]Try other USB ports and another computer.
[*]Try another operating system (Windows, MacOS) in another computer.
[*]If you still cannot wipe the first megabyte of the drive, and the drive is read-only, it is 'gridlocked', and the next stage is that it will be completely 'bricked'.[/LIST]

Repair methods are described in the next post, #9, [Repair the partition table and file system of a pendrive](http://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986)

-o-

[This link to a post by DuckHook in the Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=2178075&p=12805426#post12805426") describes how a flash drive works, and how it can fail, first getting read-only 'gridlocked', then totally 'bricked'.
 
The following link describes different hardware problems and what can be done to repair a USB stick/pendrive/flash drive [http://www.wikihow.com/Repair-a-USB-Flash-Drive](http://www.wikihow.com/Repair-a-USB-Flash-Drive). Look for the tips and warnings! 

The next link describes in detail how flash memory works and wears.

[http://www.storage-switzerland.com/articles/Entries/2012/3/6_Why_Flash_Wears_Out_and_How_to_Make_it_Last_Longer.html](http://www.storage-switzerland.com/articles/Entries/2012/3/6_Why_Flash_Wears_Out_and_How_to_Make_it_Last_Longer.html)

Apparently writing to a vfat drive with this "sync" option can ruin it. The following link is ten years old, but who knows if it can still work like that.

[http://readlist.com/lists/vger.kerne...22/111748.html]("http://readlist.com/lists/vger.kernel.org/linux-kernel/22/111748.html")

The following links are shorter, but may add some information

[http://www.flashbay.co.uk/blog/usb-life-expectancy](http://www.flashbay.co.uk/blog/usb-life-expectancy)

[http://www.zdnet.com/article/usb-drive-life-fact-or-fiction/](http://www.zdnet.com/article/usb-drive-life-fact-or-fiction/)

[http://www.dallasnews.com/business/technology/20120802-whats-the-life-expectancy-of-a-flash-drive.ece](http://www.dallasnews.com/business/technology/20120802-whats-the-life-expectancy-of-a-flash-drive.ece)[URL="http://www.storage-switzerland.com/articles/Entries/2012/3/6_Why_Flash_Wears_Out_and_How_to_Make_it_Last_Longer.html"]
[/URL]
[http://getusb.info/what-is-the-life-cycle-of-a-usb-flash-drive](http://getusb.info/what-is-the-life-cycle-of-a-usb-flash-drive)
[URL="http://www.storage-switzerland.com/articles/Entries/2012/3/6_Why_Flash_Wears_Out_and_How_to_Make_it_Last_Longer.html"]
[/URL]

---

### Post by sudodus on 2015-12-21
[SIZE=5]Repair the partition table and file system of a pendrive[/SIZE]

[size=4]Restore the original speed[/size]

[COLOR=#0000cd]***When old pendrives get slower*** (typically reduce the writing speed to half), I ***wipe the whole device*** with[/COLOR] [mkusb]("https://help.ubuntu.com/community/mkusb/wipe#Wipe_the_whole_device") [COLOR=#0000cd](overwrite with zeros). That way I have recovered the original (or near original) write speed.[/COLOR] I think it is a way to relieve the internal management of the memory cells (connecting logical cells with physical cells, maybe by releasing cells that have been written to seldom because they have been storing data). But don't do it too often, because of the wear.

[size=4]Repair file systems[/size]

Often when a pendrive does not work, it is not bricked, but the file system or partition table is damaged. This can be repaired with the same kind of tools as are used for hard disk drives.

***Repair Windows file systems (FAT and NTFS) with Windows tools***

```
chkdsk /f X:
``` or if you suspect bad sectors, ```
chkdsk /r X:
``` where X: is the drive letter (volume letter) for the target partition as seen from Windows.

Another problem of Windows file systems is ***fragmentation***. After a while they might need defragmentation. But it means a lot of writing, and I would suggest a method that creates less writing on the pendrive:

- Copy the content of the pendrive to another drive, backup. Do not clone, instead you should copy the directory structure with the files.
- Format the drive alias create a new file system (or, only if it has become very slow, wipe the whole device).
- Restore alias copy back the content from the backup.

If you have no Windows system and cannot borrow a Windows computer you can try to repair a FAT file system with ***dosfsck***, that comes with the package dosfstools,

```
sudo apt-get install dosfstools
```

```
sudo dosfsck -a /dev/sdxy
```

where x is the drive letter and y is the partition number, for example **/dev/sdb1** for the first partition in drive b. See ```
man dosfsck
``` for more details.

Sometimes this 'least destructive method' of the option -a is not enough, and you need the option -r to 'interactively repair the filesystem'.

```
sudo dosfsck -r /dev/sdxy
```

This -r option was necessary when I had provoked a damaged file system by unplugging while a big iso file was copied (to a pendrive with a FAT32 file system).

***Repair linux file systems with linux tools***

```
sudo e2fsck -f /dev/sdxy
``` or if you suspect bad blocks ```
sudo e2fsck -cfk /dev/sdxy
``` where x is the drive letter and y is the partition number, for example **/dev/sdb1** for the first partition in drive b. See ```
man e2fsck
``` for more details.

[SIZE=4]Advanced repair of a partition table, file system and/or recovery of files[/SIZE]

If you still have problems, you can use other methods for repair or recovery of the files, that are more powerful but also more risky. If the data are valuable it is a very good idea to ***make a cloned copy*** to a card or pendrive of at least the same size, and try to repair the file system and/or recover files from the cloned copy.

Particularly if you suspect bad sectors (a hardware damage on the drive), it is a good idea to clone with ***ddrescue***.

Install ddrescue ```
sudo apt-get install gddrescue
``` learn about it at the info page ```
info ddrescue
``` and follow one of the examples.

Otherwise (no bad sectors), it might be a good idea to clone with ***mkusb-dus***, because it is safer, 'wraps a safety belt around dd'.

```
dus /dev/sdx
```

where x is the drive letter of the source drive (and you use a menu to select the target drive (to become the cloned copy).

Notice that you should ***[COLOR="#cc0000"]not[/COLOR] use Clonezilla*** in these cases, because you want to clone also parts of the drive which might not be marked as containing file data. (Otherwise Clonezilla is a good tool.)

***Testdisk and PhotoRec***

Learn how to get and how to use ***testdisk*** and ***photorec*** from the instructions at [https://www.cgsecurity.org/](https://www.cgsecurity.org/)

If you need more detailed help, you are welcome to ***start an own thread*** here at the Ubuntu Forums, for example in the [hardware](http://ubuntuforums.org/forumdisplay.php?f=332) or [general help](http://ubuntuforums.org/forumdisplay.php?f=331) subforums.

[size=4]Refresh the partition table and file system(s) - the wipe menu in mkusb[/size]

When a USB drive is recognized as a mass storage device, /dev/sdx, by for example ```
sudo lsblk -fm
``` the following method can often make a failing drive available to use again, even if the file system could not be repaired. Wipe means that the previous partition table and file systems will be overwritten with zeros, so do not expect to recover data afterwards.

***Wipe [only] the first megabyte*** to prepare for a fresh partition table without any remaining and confusing data [with mkusb according to this link]("https://help.ubuntu.com/community/mkusb/wipe"). If you wish you can make a partition table and file system too from the wipe menu. Afterwards you can use ***gparted*** to create or modify a partition table with partitions and file systems. See the attached screenshot files. mkusb version 12 alias ***mkusb-dus*** is easier to use than the previous versions of mkusb.

If it is not possible to wipe the first megabyte of the drive, and the drive is read-only, it is 'gridlocked', and the next stage is that it will be completely 'bricked'. See [Post #8. Pendrive lifetime](http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297)

[SIZE=4]Attempts to repair the pendrive's hardware[/SIZE]

The following link describes different hardware problems and what can be done to repair a USB stick/pendrive/flash drive [http://www.wikihow.com/Repair-a-USB-Flash-Drive](http://www.wikihow.com/Repair-a-USB-Flash-Drive). Look for the tips and warnings!

---

### Post by QDR06VV9 on 2015-12-21
This as you have already pointed out 
> [I]**The following pendrives do not work because they are not found** after the Plop bootloader transfers control to the USB system.
Sandisk Cruzer Blade USB 2, 4 GB (which has worked 'everywhere' before)
Sandisk Cruzer Ultra USB 2, 8 GB[/I]
Is the only problems I have encountered..
What else do need me to test sudodus??
Kind Regards

---

### Post by sudodus on 2015-12-22
> **runrickus said:**
> This as you have already pointed out 
> [I]**The following pendrives do not work because they are not found** after the Plop bootloader transfers control to the USB system.
Sandisk Cruzer Blade USB 2, 4 GB (which has worked 'everywhere' before)
Sandisk Cruzer Ultra USB 2, 8 GB[/I]
Is the only problems I have encountered..
What else do need me to test sudodus??
Kind Regards

1. If you have a pendrive that is much slower than when it was new, you can wipe the whole device, and after that check if it is fast again. But don't do it on a good pendrive, that would only cause unnecessary wear of the memory cells.

2. If you have a pendrive with a bad FAT16 or FAT32 file system, you can try to repair it with the linux tool *dosfsck*. I'm not sure how much it can do compared to the Windows tool *chkdsk*.

*. Otherwise I don't know right now, but I'll come back and ask (hoping that you will have time to test when that happens).

---

### Post by QDR06VV9 on 2015-12-22
> [COLOR=#000000](hoping that you will have time to test when that happens).[/COLOR]
I will make the time..
I have bought a couple of SanDisk Cruzer U 16 Gigs, Real Cheap and they are just waiting for you..:D
Thanks sudodus

---

### Post by sudodus on 2016-06-30
[SIZE=4]Checking the iso file and the boot drive - detailed tips[/SIZE]

There are two ways to check the md5sum.

[SIZE=3]1. Check the whole iso file with md5sum versus the listed value[/SIZE]

at [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes), for example

```
$ [COLOR="#0000FF"]md5sum ubuntu-16.04-desktop-amd64.iso[/COLOR]
c94d54942a2954cf852884d656224186  ubuntu-16.04-desktop-amd64.iso
```

or if you have the md5sum in a file with a line, where the file name is following the md5sum (usually separated by two spaces like the output above)

```
$ [COLOR="#0000FF"]md5sum -c ubuntu-16.04-desktop-amd64.iso.md5[/COLOR]
ubuntu-16.04-desktop-amd64.iso: OK
```

[SIZE=3]2. Check the packages in the install drive with the boot menu option 'Check the disk for defects'[/SIZE]

[SIZE=3]Discussion[/SIZE]

If there is a checksum error, it depends very much *where* it is. Some program package might be damaged, that you are not using (at least not during the first few days). But if the checksum is bad, there is often a big damage, and you will not be able to create a working boot drive from the iso file.

***1. iso files***

Most bad iso files are caused by bad internet connections. The quality of internet connections is improving over time, and bad downloads are less common nowadays compared to a few years ago. One failure is that the connection failed before the whole file was downloaded. So the file is too small. Using a ***torrent*** is reliable because it checks the md5sum automatically. The same holds for ***zsync*** which is available at the [Ubuntu QA testing tracker](http://iso.qa.ubuntu.com).

***2. Check the disk for defects***

*2.1. Optical disks*

I think most failures at 'Check the disk for defects' (when the iso file was good) are caused by bad burning, for example a failing optical drive or too high burning speed. It is a good idea to burn at the lowest possible speed. I have good experience of ***k3b***, that can be installed in any flavour of Ubuntu (not only Kubuntu).

See the following link for more details, [BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

*2.2 USB pendrives*

Flashing the iso file to a USB pendrive is very reliable with ***cloning*** tools, but can fail with tools that depend on interpreting the internal structure of the iso file, if the tool is not up to date with the particular linux system in the iso file. If a USB pendrive is bad (physically bad with damaged sectors of memory cells), it will usually be read-only or dead, rather than accept writing but not store the data correctly.

See the following link for more details, [Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by sudodus on 2016-09-12
[SIZE=4]Restore a USB boot drive[/SIZE]

You may want to re-use the USB pendrive as a standard storage drive (after installing Ubuntu). If the boot drive was cloned from the iso file (with mkusb or the Ubuntu Startup Disk Creator alias usb-creator-gtk version 0.3), there is a read-only iso9660 file system, and you must restore the drive. The standard is an MSDOS partition table (MBR) and a partition with the FAT32 file system.

1. You can format the USB pendrive completely (including MBR) using ***gparted*** in Ubuntu or Disk Management in Windows. This works in most cases.

2. Otherwise you can use ***mkusb*** and ***mkusb-nox***, which have built-in features to wipe the first megabyte, create a new partition table and file system.

It is easy to use mkusb-nox in a terminal window (but you must install it, which is described in both links below).

```
sudo mkusb-nox restore
```

[hr][/hr]
See the following links (and links from them),

[Postrequisites - restore the USB stick](https://help.ubuntu.com/community/Installation/FromUSBStick#Postrequisites_-_restore_the_USB_stick)

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

---

### Post by slickymaster on 2017-11-04
Reopened per OP request

---

