---
title: "How to clone P2V into an accessible image format ?"
date: 2016-01-18
forum: Virtualisation
---

### Post by ubuserone on 2016-01-18
As a beginner on visualization , 
How to clone an OS P2V into an accessible image format which ca be mount and access certain file like an .iso or dd without any compression ? 
Which friendly or universal format as above and can be convert raw image to this 3 visualization software ?

Virtualbox 
VMware
QEMU+KVM

On understanding repeating
-How to cloning a P2V ( ubuntu and Windows ) with a cloning application ( clonezilla ) effectively 
-What is the different between (sector by sector ) and ( only sector of use block ) ?
-While cloning , Which cloning application provide guide fully support handbook ?
-Which cloning into a raw img format ( accessible or can be mount )without compression ?
-The raw img format can be easily convert to Virtual Guest (.vdi , .vdmk ) and can be booted up and run.
-If there's a bad sector on the raw img , which Virtual application can skip and still convert into virtual Guest ?
 
What I did
-I follow one of the link for virtualbox [http://www.linux.org/threads/physical-to-virtual-p2v-using-virtualbox.7248/](http://www.linux.org/threads/physical-to-virtual-p2v-using-virtualbox.7248/) but I encounter 2 problems
(Unable to mount ) and ( no boot menu ) which required a super grub.iso to search grub in the OS . Using 12.04 for testing purpose.
[http://ubuntuforums.org/showthread.php?t=2310367&p=13425064](http://ubuntuforums.org/showthread.php?t=2310367&p=13425064)

Sorry for being new on stuff like it , please suggest if I misinterpret some of the question wrongly.Thank you for the understanding :)

---

### Post by Bucky Ball on 2016-01-18
You can clone the drive with Clonezilla (among other methods). See if these give any clues:

Home site:
[http://clonezilla.org/](http://clonezilla.org/)

Create image:
[http://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/](http://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/)

Create recovery ISO:
[https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/](https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/)

Partition cloning step by step:
[http://cdonner.com/partition-cloning-with-clonezilla.htm](http://cdonner.com/partition-cloning-with-clonezilla.htm)

Create Live media (with pics):
[http://clonezilla.org/fine-print-live-doc.php?path=./clonezilla-live/doc/04_Create_Recovery_Clonezilla/01-clonezilla-boot-menu.doc#01-clonezilla-boot-menu.doc](http://clonezilla.org/fine-print-live-doc.php?path=./clonezilla-live/doc/04_Create_Recovery_Clonezilla/01-clonezilla-boot-menu.doc#01-clonezilla-boot-menu.doc)

Don't think [fsarchiver]("http://www.fsarchiver.org/Main_Page") can clone an entire disk. The [dd command]("http://www.howtogeek.com/howto/19141/clone-a-hard-drive-using-an-ubuntu-live-cd/") would work. (Be warned: read the first bit, in italics, of that article.) It copies everything, but you need to be careful you have the target right as it takes no prisoners and will erase everything before it as soon as you hit 'go'.

---

### Post by ubuserone on 2016-01-18
> **Bucky Ball said:**
> You can clone the drive with Clonezilla (among other methods). See if these give any clues:

Home site:
[http://clonezilla.org/](http://clonezilla.org/)

Create image:
[http://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/](http://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/)

Create recovery ISO:
[https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/](https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/)

Partition cloning step by step:
[http://cdonner.com/partition-cloning-with-clonezilla.htm](http://cdonner.com/partition-cloning-with-clonezilla.htm)

Create Live media (with pics):
[http://clonezilla.org/fine-print-live-doc.php?path=./clonezilla-live/doc/04_Create_Recovery_Clonezilla/01-clonezilla-boot-menu.doc#01-clonezilla-boot-menu.doc](http://clonezilla.org/fine-print-live-doc.php?path=./clonezilla-live/doc/04_Create_Recovery_Clonezilla/01-clonezilla-boot-menu.doc#01-clonezilla-boot-menu.doc)

Don't think [fsarchiver]("http://www.fsarchiver.org/Main_Page") can clone an entire disk. The dd command copies everything, but you need to be careful you have the target right as it takes no prisoners and will erase everything before it as soon as you hit 'go'.

Thank you , 
I am using clonezilla following one of the guide,  I just edit my post a minute ago .

> [COLOR=#000000]-I follow one of the link for virtualbox [/COLOR]http://www.linux.org/threads/physical-to-virtual-p2v-using-virtualbox.7248/ [COLOR=#000000]but I encounter 2 problems[/COLOR]
[COLOR=#000000](Unable to mount ) and ( no boot menu ) which required a super grub.iso to search grub in the OS . Using 12.04 for testing purpose.[/COLOR]
[http://ubuntuforums.org/showthread.php?t=2310367&p=13425064](http://ubuntuforums.org/showthread.php?t=2310367&p=13425064) 

As for clonezilla , does it had a handbook or guide because every option selected needed a full --help careful explain guide.I a wrong option hit , I may get a wrong output img which wasn't my desired img.
The clonezilla [http://clonezilla.org/clonezilla-live-doc.php](http://clonezilla.org/clonezilla-live-doc.php) doesn't explain much on my option , any more guide for it ?

I am cloning within my PC with different partition individually and not on a whole disk.Since I had 3 OS on a single hard disk which I wanted to boot as virtual individually.

I'll read the the link provided above , Thank you very much :D

---

### Post by Bucky Ball on 2016-01-18
Cloning three partitions is fairly straightforward. To clone three partitions from a disk, the information can be gleaned from my last post, but fsarchiver or dd would be the easiest. Both would use one command to clone. Create partitions on the drive you are going to clone the partitions to then dd them. Or (safer if your target drive has valuable data on other partitions) use fsarchiver.

[Here's how. ]("http://www.fsarchiver.org/QuickStart#How_to_save_filesystems_to_an_archive")

From the drive you want to clone, open a terminal and run this command:

```
sudo blkid
```

Post the output here and confirm which partitions you want to clone. See my signature and use code tags for the terminal output, please.

---

### Post by ubuserone on 2016-01-19
> **Bucky Ball said:**
> Cloning three partitions is fairly straightforward. To clone three partitions from a disk, the information can be gleaned from my last post, but fsarchiver or dd would be the easiest. Both would use one command to clone. Create partitions on the drive you are going to clone the partitions to then dd them. Or (safer if your target drive has valuable data on other partitions) use fsarchiver.

[Here's how. ]("http://www.fsarchiver.org/QuickStart#How_to_save_filesystems_to_an_archive")

From the drive you want to clone, open a terminal and run this command:

```
sudo blkid
```

Post the output here and confirm which partitions you want to clone. See my signature and use code tags for the terminal output, please.

Thank you for recommanding FSArchiver but before I start , I would like to have more understanding with FSArchiver.


-FSArchiver clone by archive or compressing files with level 1-9
-Cloning to save the filesystem with Files only


Question
-Does FSArchiver have an option not to clone using any compressing method ?
-Does cloning to save the filesystem with files only affect when if the file is readable ? 
-Can I mount on the .fsa image files after cloning to access particular files ?


The reason I asked because , there is once a did a check disk with a few bad sector on the OS.If I was to use FSArchiver , it'll skip on files with is unreadable.
As above , after I clone using FSArchiver (if it's compress), if the image .fsa having a bad sector , will I able to read/mount and restore it ? since anything with compression will have hash check and with a badblock happen , will it affect the recovery procedure ?




I downloaded SystemRescueCD as recommanded on [https://www.fsarchiver.org/Installation](https://www.fsarchiver.org/Installation)
I am testing now with a virtual guest drive to clone so the output


```

root@sysresccd /root % blkid
/dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="95f920a3-ca56-4960-9bcb-3f8b14b664cb" TYPE="ext4" PARTUUID="00011863-01"
/dev/sda2: UUID="2995CDDF50F8D16E" TYPE="ntfs" PARTUUID="00011863-02"
/dev/sda5: UUID="d9e695db-0b8f-4e57-965d-9839cb0371d5" TYPE="swap" PARTUUID="00011863-05"
/dev/sr0: UUID="2016-01-18-20-46-30-00" LABEL="sysrcd-4.7.1" TYPE="iso9660"
```


This is the first testing , I just wanted to clone sda1 to sda2 but not sda5 with swap.


To clone 
How do I mount a ntfs partition ?
```
ntfs-3g /dev/sda2 /mnt/windows
```


I plan to save on sda5, is this the correct code ?
```
fsarchiver savefs /mnt/windows/gentoo-rootfs.fsa /dev/sda1
```

---

### Post by ubuserone on 2016-01-23
What is the different between Clonezilla vs Fsarchiver ?

---

### Post by Bucky Ball on 2016-01-23
> **ubuserone said:**
> What is the different between Clonezilla vs Fsarchiver ?

In what respect? If you do a search and some research on both you'll probably find your answer. If not and there's something specific that you can't find out, let us know and we'll see if we can fill in the gaps. ;)

---

### Post by sudodus on 2016-01-23
> **ubuserone said:**
> 
QEMU+KVM

If you use QEMU+KVM (for example with virt-manager) you can use a drive on the host computer or an image (for example made with dd) directly. There is no need to make a virtual drive.
> 
-If there's a bad sector on the raw img , which Virtual application can skip and still convert into virtual Guest ?

[B][I]
dd-rescue[/I][/B] is a good tool to clone drives with some bad sectors. It can recover as much as possible (more than can be repaired by for example e2fsck) because it tries several times in a smart way.

```
sudo apt-get install gddrescue
```

The info page ```
info ddrescue
``` is well written and after reading all of it, I think you can work according to ***Example 1*** of Chapter 6 'A small tutorial with examples' to clone the whole drive. You need to modify the devices /dev/sdx and /dev/sdy where x is the drive letter for the source and y for target drive to the real devices, for example /dev/sda and /dev/sdb, and you should focus on the two first commands of the example

```
sudo ddrescue -f -n /dev/sdx /dev/sdy logfile
sudo ddrescue -d -f -r3 /dev/sdx /dev/sdy logfile
```

Run ddrescue when booted from a third drive, for example from an Ubuntu desktop persistent live system in a USB pendrive, where you have installed ddrescue, and where you can store the logfile. The logfile is very important (which is explained in the info page).

Last but not least: Bucky Ball's warning about dd applies to ddrescue too. It will do what you tell it to do without questions, even if you tell it to wipe the family pictures. So please check and double-check that the drive letters are correct!

---

### Post by ubuserone on 2016-01-25
> **Bucky Ball said:**
> In what respect? If you do a search and some research on both you'll probably find your answer. If not and there's something specific that you can't find out, let us know and we'll see if we can fill in the gaps. ;)
I did some reading on [COLOR=#000000]Fsarchiver , I posted some question on compressing level early post. Since I am a beginner , Fsarchiver is a method of cloning but on clonezilla , what are the different compare to the option [[/COLOR]Partclone (default), Partimage (optional), ntfsclone (optional), or dd to image or clone a partition. ] at clonezilla ?
> **sudodus said:**
> If you use QEMU+KVM (for example with virt-manager) you can use a drive on the host computer or an image (for example made with dd) directly. There is no need to make a virtual drive.

[B][I]
dd-rescue[/I][/B] is a good tool to clone drives with some bad sectors. It can recover as much as possible (more than can be repaired by for example e2fsck) because it tries several times in a smart way.

```
sudo apt-get install gddrescue
```

The info page ```
info ddrescue
``` is well written and after reading all of it, I think you can work according to ***Example 1*** of Chapter 6 'A small tutorial with examples' to clone the whole drive. You need to modify the devices /dev/sdx and /dev/sdy where x is the drive letter for the source and y for target drive to the real devices, for example /dev/sda and /dev/sdb, and you should focus on the two first commands of the example

```
sudo ddrescue -f -n /dev/sdx /dev/sdy logfile
sudo ddrescue -d -f -r3 /dev/sdx /dev/sdy logfile
```

Run ddrescue when booted from a third drive, for example from an Ubuntu desktop persistent live system in a USB pendrive, where you have installed ddrescue, and where you can store the logfile. The logfile is very important (which is explained in the info page).

Last but not least: Bucky Ball's warning about dd applies to ddrescue too. It will do what you tell it to do without questions, even if you tell it to wipe the family pictures. So please check and double-check that the drive letters are correct!
I follow up a guide on DD using Clonezilla [http://www.linux.org/threads/physical-to-virtual-p2v-using-virtualbox.7248/](http://www.linux.org/threads/physical-to-virtual-p2v-using-virtualbox.7248/) but I end up having only Sda without boot menu grub.I totally not knowing the command to restore it but some mention it is impossible [http://ubuntuforums.org/showthread.php?t=2310367](http://ubuntuforums.org/showthread.php?t=2310367)

---

### Post by sudodus on 2016-01-25
What is impossible? I don't understand what is the problem.

If bad sectors, you can use ddrescue instead of dd.

I think you should try until the cloning works, and then the target will be an identical copy of the source (with bootloader, partitions, file systems, directories, files and free space). Bad sectors will not be copied, if you use ddrescue, but if the original system (the source) worked, the clone (target) should also work because we can assume that the bad sectors do not affect any important data, maybe affecting only the free space.

(I have not looked into the details of the tutorial by Jarret W. Buse.)

---

### Post by ubuserone on 2016-02-24
> **sudodus said:**
> What is impossible? I don't understand what is the problem.

If bad sectors, you can use ddrescue instead of dd.

I think you should try until the cloning works, and then the target will be an identical copy of the source (with bootloader, partitions, file systems, directories, files and free space). Bad sectors will not be copied, if you use ddrescue, but if the original system (the source) worked, the clone (target) should also work because we can assume that the bad sectors do not affect any important data, maybe affecting only the free space.

(I have not looked into the details of the tutorial by Jarret W. Buse.)

There is a lot of packages during google search that list out ddrecuse , dd_recuse , gddrecuse , ddrecuse-gui .I am confuse with it.
What is the different between clonezilla dd vs ddrecuse or gddrecuse ?

Updated :
I tried with ddrecuse-gui which is much better interface [https://launchpad.net/ddrescue-gui](https://launchpad.net/ddrescue-gui).
but does it gives the best option for recovery on NTFS partition too ? and compare with gddrecuse ?

---

### Post by sudodus on 2016-02-24
***ddrescue***, that you get via the package gddrescue, has special features to try hard to read sectors that are hard to read (almost failing). It can skip bad sectors in a 'good' way to create a useful cloned image of what can be rescued for the failing drive.

I think dd_rescue is an older version that is much slower than ddrescue. I think Clonezilla dd is standard dd, with problems if there are bad sectors (or almost bad sectors).

```
sudo apt-get install gddrescue
```

The info page is good and well worth reading before you start using ddrescue

```
info ddrescue
```

---

