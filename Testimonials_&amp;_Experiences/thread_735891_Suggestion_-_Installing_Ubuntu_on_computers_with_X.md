---
title: "Suggestion - Installing Ubuntu on computers with XP / VIsta"
date: 2008-03-26
forum: Testimonials &amp; Experiences
---

### Post by narraal on 2008-03-26
Hi everyone.

This topic is probably been flogged to death but......

When installing Ubunto onto a computer with Xp / Vista, surely it cannot be that hard to present a better interface for selecting where Grub is installed. The number you have to type bears little relationship (at first glance) to the name that appear during the partitioning. In addition to this, I am sure many "trial" users of Ubuntu (like me) just panic at this point because they can see one wrong character can wipe out the MBR. If you really want to attract Windows users, this has to be cleaned up. I also think that most Windows people would be much more confortable in leaving the MBR the way it is and seeing a Ubunto item added to the bottom of the Winows boot list. (ok easy(ish) for boot.in but a pain for Vista)

Before I get flamed, I am a technical director of a company that has 100,000 users and this part of Ubuntu (Linux) is just plain scary and dangerous. I know to Acronis all partitions first, and I can restore the MBR at will, but I still took a day to get it all sus'd out and working as I wanted. Ok granted, I had EXT3 / XFS paritions intermixed with NTFS partitions so that both disk drives were being used by XP/Vista and Linux to improve performance. Most users will loose data, and you've lost that customer for another 5 years. I'm lucky that I had 10 years of Sun OS, Ultirx, Iris, RS6000 and god know what else.

So, if you really want Ubunto 8 to make inroads to Windows users, hide all the grub numbers behind something friendier.

---

### Post by anantshri on 2008-03-26
thanks for pointing out this stuff, 

my suggestion in this regard will be that at grub install scree present two options 

1) use windows bootloader

2) use linux bootloaded.

for option 1 in XP, install grub at first sector of boot partition and then make its enry in boot.ini

(Please check vista options coz i didn't got hold of it yet.)

for option 2 simple install grub to mbr.


ya one more thing, if option one is selected then keep the timeout to lowest possible, also i don't think need to list all options will be necessary,

but yes atleast a time out of 1-2 sec minimum should be left so that one can work to get things back if something goes  wrong..

---

### Post by PmDematagoda on 2008-03-26
This thread has been moved to the Ubuntu Testimonials and Experiences section.

---

### Post by mmd2008 on 2008-03-26
but what if windows needs to be installed.Windows will put its mbr.
i want to install Ubuntu's on another hard disk.
so,I can from the motherboard switch between the windows hard disk and ubuntu hard disk. but I don't know how.:confused:

---

### Post by sg1 on 2008-03-26
I installed xp onto my ATA HDD and then disconnected the power supply to the HDD and then installed the LINUX to my SATA HDD so Linux couldn't see the other drive containing XP . I now have two COMPLETELY seperate OS's that I switch between by using the BOOT MENU at POST:)

---

### Post by mmd2008 on 2008-03-26
I installed ubunto 7.04  and it changed some mp3 files writing long file names when bootng to ubunto.
so, I leaved it and using only xp.
I need linux to delete xp viruses.
sometimes, I think Ubuntu cooperates with windows and can't delete some sticky files in windows.so I used [COLOR="DarkRed"]Xandros[/COLOR].

---

### Post by angry_johnnie on 2008-03-26
Ubuntu Hardy has an option to install it using Wubi.  This is done from within windows and requires no partitioning.  It  also uses Windows' boot loader.  Wubi has been around for some time now.  It's not a new thing.

And, then, there's the fact that most people never have to install an operating system.  Doing it for the first time, without proper knowledge of what one is doing, and without researching or asking for help is a foolish thing to do. 

I guess it's just a matter of looking at all the options and asking lots of questions before jumping in.

---

