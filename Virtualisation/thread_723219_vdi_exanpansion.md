---
title: "vdi exanpansion"
date: 2008-03-13
forum: Virtualisation
---

### Post by gjj391 on 2008-03-13
Running XP through virtualbox on my gutsy... I set it up up to have a dynamically expanding vdi.

While im xp its always freaking out saying theres is no more diskspace?

kinda confused.....

---

### Post by Hero of Time on 2008-03-16
There are a two things that could go wrong here. Either you don't have enough space on your physical hard drive left for the vdi to grow, or the vdi reached its limit you set when creating the virtual hard disk image.
Even though you set it to dynamically expand, it means that the vdi file will use as much disk space as the data in it uses. If you use 2 GB of data in the vdi file, the vdi will take about 2 GB (a bit more for extra info). However, if you set the size of the vdi to be limited to 10 GB, and the data in the virtual machine wants to use 10.2 GB, it can't because the 'hard drive' is full.

---

### Post by gjj391 on 2008-03-16
i gotcha.... I still have plenty of room.

Can you resize the vdi with out lossing everything on it?

---

### Post by Jose Catre-Vandis on 2008-03-16
No you cannot resize a vdi in VirtualBox. You have to create a new virtual hard drive of the size you want, attach it to your vm, then copy an image of your existing hard drive using gparted or similar, then switch hard drive priorities and boot up :)

---

### Post by lkraemer on 2009-01-17
Correction on the above post stating a VDI can NOT be expanded.

Yes, you can expand a VDI and here is a guide that works.

1.  Download Clonezilla.
2.  Download Gparted.  (I didn't use the latest of either)
    (There is a Clonezilla/Gparted LiveCD too, but I didn't use it.)
    [http://gpartedclonz.tuxfamily.org/](http://gpartedclonz.tuxfamily.org/)
3.  You currently have the existing VDI that is FULL OR NEEDS
    to be resized/expanded.  Most likely it is attached to your
    IDE Primary Master Slot.  
4.  Create a new RAW (unpartitioned) VDI and size it as needed,
    and attach it to IDE Primary Slave Slot.  (This will contain
    a copy of your original VDI in #3 above when you are finished.)
5.  Make sure that the CD/DVD has a check mark so it is a BOOT device
    and that it's order is set before the Hard Drive.
6.  In VirtualBox click on CD/DVD ROM and check MOUNT, then ISO
    Image file, and browse to the CLONEZILLA.ISO you just downloaded.
    (This will become your BOOT Device when you click START.)
7.  Click START and Clonezilla will start running.  (Even though you
    will be copying a PARTITION (VDI) use the DISK to DISK function and
    make sure they are listed as VirtualBox partitions.
    Use the Spacebar to select SOURCE, then DESTINATION.  
    UNSELECT the -g-auto (write grub) and then SELECT the
    -e Resize Filesystem to fit size in Target Partition.
    (Newer versions use -r Resize Filesystem to fit size in Target....)
    When you are asked "Do you want to clone the Bootloader?"
    answer YES.  Sit back and relax while your VDI is cloned.
8.  If for some reason the -e (now -r) option doesn't work correctly,
    you can always load gparted (as #5 above) and manually
    resize the partition (VDI).
9.  When you are finished, reset the IDE Primary Master to the
    newly resized VDI. Change the CD/DVD ROM back to what it was
    previously, and change your BIOS BOOT order as required.
10. Click START to run the new resized VDI.  If you are running XP,
    check your C:\ drive to make sure it was resized.

lkraemer

---

### Post by Mgiacchetti on 2009-04-03
umm... that isnt "resizing" a vdi, that is cloning a vdi to a larger vdi.

Totally different, but it solves the problem.

---

### Post by musikgoat on 2009-05-30
Thanks to lkraemer's instructions, I was able to grow my windows 7 vdi from 10GB to 20GB.  

I deviated from his instructions in that I only used clonezilla and instructed it to grow the partition, but when I booted into Windows 7 I had to use the Disk Manager to grow the partition to its full size.

It worked flawlessly and now I have lots 'o space to work with!

---

### Post by zevans on 2009-06-10
> **Mgiacchetti said:**
> umm... that isnt "resizing" a vdi, that is cloning a vdi to a larger vdi.

Totally different, but it solves the problem.

Well, indeed - does this mean you know how to resize it using only VirtualBox and guest OS tools?

---

### Post by muteXe on 2009-06-10
Yeah i made that mistake.  It's amazing to think a new install of xp is about 11-12Gb.  I restarted and allowed my disk to be 20Gb.

---

### Post by przemoc on 2009-10-21
> **zevans said:**
> [QUOTE=Mgiacchetti;7005812]umm... that isnt "resizing" a vdi, that is cloning a vdi to a larger vdi.

Totally different, but it solves the problem.Well, indeed - does this mean you know how to resize it using only VirtualBox and guest OS tools?[/QUOTE]

VirtualBox doesn't have such feature, but my program called **vidma** - Virtual Disks Manipulator has it. It supports in-place resizing, but because this tool is in alpha stage, you should always backup your image before expanding or shrinking it, or just give the name of output file in command line (then input file won't be modified). USE AT YOUR OWN RISK! NO WARRANTY!

Download page: [vidma]("http://wiki.przemoc.net/projects/start#vidma")
VB Forum topic: [vidma - Virtual Disks Manipulator (tool for resizing VDI) ]("http://tinyurl.com/vbix-vidma")

---

### Post by KamakazieX on 2010-04-22
has anyone tried #dd if=\dev\sda{1} of=\dev\sdb{1} and resizing with gparted? just throwing an idea out in the air. As long as the target drive is larger it should work?

---

