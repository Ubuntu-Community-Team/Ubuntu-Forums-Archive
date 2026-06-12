---
title: "Anyone knwo how to help me get Zenwalk to boot??"
date: 2007-03-25
forum: Slackware and derivatives
---

### Post by billdotson on 2007-03-25
I have Ubuntu on a partition on my external HDD.  The part. is sdb1.  I have another partition sdb7 (part of an extended partition) that I installed Zenwalk Linux on.  Zenwalk asked me if I wanted to install LILO and I said no, because I already had GRUB and GRUB recognized Ubuntu.
Should I just go back and tell it to install LILO or is there a way for Zenwalk to be seen by GRUB?

thank you!

---

### Post by maniacmusician on 2007-03-25
you might have to reinstall grub to get the zenwalk partition to show up, or simply add the zenwalk partition to menu.lst.

---

### Post by billdotson on 2007-03-25
how would I go about doing either??  I know that in Ubuntu there is an /etc/boot/grub/menu.lst but why would the grub menu.lst be in Ubuntu??  Is it just that I can edit it from there?

---

### Post by igknighted on 2007-03-25
> **billdotson said:**
> how would I go about doing either??

Open the file /boot/grub/menu.lst as root to edit it.  Copy all the text relating to booting your Ubuntu kernel (just one section is fine) and add it to the bottom.  You can rename it Zenwalk if you please.  Then reboot (yes, it still point to Ubuntu... but thats ok for now).

When you get to the grub menu, scroll down to the new entry and hit 'e'.  This will take you to a screen to edit the entry.  Now change the root section to what it should be (Probably (hd1,0)).  You will need to hit 'e' over the line to edit it.

Then edit the kernel line.  Delete EVERYTHING after the word kernel.  Then type in (hd1,0)/bo and then hit tab.  It should auto complete to (hd1,0)/boot/.  If it does not, then (hd1,0) is not the right partition.  You might have to experiment to find the right one.  Once you find the right one, hit tab again to give a list of files in the directory.  Start typing the kernel name in and hit tab to auto complete it.  Then hit space, and type in root=/dev/sdb1 (or the partition it is on, normal linux style).  Then add any other boot options you might need (for me I need noapic to boot).  Now hit enter to go back, the line should read something like this:
```
kernel (hd1,0)/boot/vmlinuz root=/dev/sdb1 noapic
```
but obviously with your specific info.

Now edit the initrd line.  Again, erase everything other than initrd, and use the same procedure as above to get back to the proper (hd1,0)/boot section.  Hit tab to list the files and put in the initrd file.

Now you need to take careful note of everything you wrote.  Your changes will not be saved so write it all down so you can add it to menu.lst when you boot.  You might need to remove the savedefault line ('d' takes care of this when the line is highlighted).  Once all this is done, hit 'b' to boot and you should be all set.

NOTE: If you knew all this info right away you could enter it into menu.lst right away, but this is how you set it up when you do not know.

EDIT: You are booting Ubuntu's grub (like Windows booting off of Ubuntu's grub in the typical dual boot setup).  Again, if you know all the info required you do not need to go through all the steps I laid out and can put it right into Ubuntu's menu.lst.  Zenwalk will not have a menu.lst, as slackware does not use grub to boot, only lilo.

---

### Post by billdotson on 2007-03-25
I don't understand what you mean by saying to change it to (hd1,0) because although Zenwalk is on my external drive it is the 7th partition, so shouldn't it be (hd1,6)?  I also do not know any of those extra options like noapic or any modifiers so I do not know which I would not/wouldn't need.  Do I really need to do all of that in Grub??  Isn't all I have to do is copy the kernel and ititrd lines and replace it with hd1,6 and sdb7?

So my menu.lst entry for Zenwalk would look something similar to:

Zenwalk
kernel (hd1,6)/boot/vmlinuz root=/dev/sdb7
initrd (hd1,6)/boot/vmlinuz root=/dev/sdb7

or are there other things I would have to know that I need GRUB to tell me?

Thanks.  BTW is this how I do it with any distro or BSD flavor?  Just simply add the OS and it's location and then I can boot it?

---

### Post by igknighted on 2007-03-25
> **billdotson said:**
> I don't understand what you mean by saying to change it to (hd1,0) because although Zenwalk is on my external drive it is the 7th partition, so shouldn't it be (hd1,6)?  I also do not know any of those extra options like noapic or any modifiers so I do not know which I would not/wouldn't need.  Do I really need to do all of that in Grub??  Isn't all I have to do is copy the kernel and ititrd lines and replace it with hd1,6 and sdb7?

So my menu.lst entry for Zenwalk would look something similar to:

Zenwalk
kernel (hd1,6)/boot/vmlinuz root=/dev/sdb7
initrd (hd1,6)/boot/vmlinuz root=/dev/sdb7

or are there other things I would have to know that I need GRUB to tell me?

Thanks.  BTW is this how I do it with any distro or BSD flavor?  Just simply add the OS and it's location and then I can boot it?

Well, yeah, I was just using a generic example where it was on the first partition... You would need to plug in your specific partitions.

I can't promise that your BSD would work the same way, but its a good bet that it would.

Try this:
```
title Zenwalk
kernel (hd1,6)/boot/vmlinuz root=/dev/sdb7
initrd (hd1,6)/boot/initrd
boot
```
The file names might not be the same as vmlinuz and initrd, as those are generic.  But if you erase the vmlinuz part and hit tab it will give you options. One will say either kernel-2.6.XX blah blah blah, or there might be a vmlinuz.  Dunno.  The intird is a different file.  It will probably "initrd.img" or some other file extension, but will say something about initrd in the file name.  You can mount the zenwalk partition in Ubuntu and look in the /boot folder for the proper filenames.

---

### Post by billdotson on 2007-03-25
ok so I added this to my list:

title Zenwalk Linux
root (hd0,2)   (I did hd0 because Ubuntu has hd0 which is odd since the external drive is hd1)
kernel root= (hd06,6)/boot/vmlinuz-2.6.20
boot

there is no initrd.img in there the only thing there is is initrd.splash, so I didn't include the initrd line.  There is another initrd but I didn't include that either because it wasn't an initrd.img.  When I tried to boot from that it ran through a bunch of lines of text and then said cannot find or access (I can't remember) root device 'sdb7' or unknown block (0,0)

I also tried it with root (hd0,6) but I got a kernel panic error.

I also tried:

title Zenwalk Linux
root (hd0,6)   
kernel /boot/vmlinuz-2.6.20
boot

and I got a kernel panic error or something like error 17 cannot mount root partition.. or maybe that was the first Zenwalk section up at the top, actually I think it is.  I think I got the cannot access root device line and then it said kernel panic on the other two.

I think the issue lies in that the partition I installed it to is a logical partition inside an extended partition.  The extended partition is /sdb3/ so I tried the (hd0,2) but that didn't work.  The extended partition that Zenwalk is on is sdb7.

Thanks

---

### Post by igknighted on 2007-03-25
You need the initrd file.  Use the .splash.  There is no standard extension for these files, so as long as initrd is in the name its probably it.  Also, root does not point to Ubuntu's root.  Sure ubuntu has the config files, but as far as grub is concerned Ubuntu is another OS it can boot and nothing more.  There shouldn't be references to the Ubuntu drive in the grub config file.  leave the root line as "root (hd1,6)".

---

### Post by billdotson on 2007-03-25
wait but if Ubuntu is hd0 wouldn't anything else on the drive be hd0??  Ubuntu is on (hd0,0) so if I did (hd0,2) how would I be referencing to Ubuntu?

---

### Post by igknighted on 2007-03-25
now you've confused me... from what I see in your setup try this:

title Zenwalk Linux
root (hd0,6)
kernel (hd0,6)/boot/vmlinuz-2.6.20 root=/dev/sdb7
boot

and if that doesnt work:

title Zenwalk Linux
root (hd0,6)
kernel (hd0,6)/boot/vmlinuz-2.6.20 root=/dev/sdb7
initrd (hd0,6)/boot/initrd.splash
boot

---

### Post by billdotson on 2007-03-25
I have tried what I have tried and what you have suggested every time except for the time I had the line root (hd0,2) I get these lines at the bottom of the text:

RAMDISK: Couldn't find valid RAM disk image starting at 0
Replacing swsusp
Suspend2: Resume2 parameter is empty.
Suspending will be disabled.
VFS: Cannot open root device "sdb7" or unknown-block(0,0)
Please append a correct "root=" boot option
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

Dangit!!!

Maybe it needs to be (hd1,6) because I have my internal drive plugged in right now.  When I installed GRUB and Ubuntu I did not.

---

### Post by igknighted on 2007-03-25
> **billdotson said:**
> I have tried what I have tried and what you have suggested every time except for the time I had the line root (hd0,2) I get these lines at the bottom of the text:

RAMDISK: Couldn't find valid RAM disk image starting at 0
Replacing swsusp
Suspend2: Resume2 parameter is empty.
Suspending will be disabled.
VFS: Cannot open root device "sdb7" or unknown-block(0,0)
Please append a correct "root=" boot option
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

Dangit!!!

Maybe it needs to be (hd1,6) because I have my internal drive plugged in right now.  When I installed GRUB and Ubuntu I did not.

Well, it is finding the kernel so the partition # is right.  Do you remember what file system you used for Zenwalk?  If you used XFS you might not be able to boot with grub... apparently grub and xfs dont play nice.  I have seen that error message before.  The first time I installed Gentoo I got that, because when I compiled the kernel I had neglected to include support for something.  I think it might have been drivers for my sata... perhaps you have the same issue.  The kernel for Zenwalk might not be compiled with support for booting via a USB drive.

---

### Post by billdotson on 2007-03-25
hmm interesting.  Well that kindof stinks I really wanted to try Zenwalk.  I installed Zenwalk on an ext3 filesystem, not an XFS.

---

### Post by igknighted on 2007-03-25
One more thought... what if you tried sda7 or sdc7 or something?  In Ubuntu run "sudo fdisk -l" to find what the exact partition name is, then try that (replace root=/dev/sdb7 with root=/dev/<partition_from_fdisk>)

---

### Post by bonzodog on 2007-03-26
Grub has a funny way of reading drives. 

sda = 0. sdb =1. 

Partition 7 of sdb would be (1,6).

try that combination for the Zenwalk boot.

When you partition a drive, the first partition is always 0, and counts up from there as far as grub is concerned.

---

### Post by billdotson on 2007-03-26
bonzodog.. thank you I will try that.  I know that GRUB sees the drives as 0,1 if there are two drives but I thought that I should have the root be (hd0,6) because when I looked at the entries for Ubuntu the root for Ubuntu was (hd0,0) but the odd thing is that Ubuntu is on my external drive.. which would be recognized by GRUB as hd1 wouldn't it?  Maybe it has to do with the fact that I unplugged my internal HDD when I installed Ubuntu and GRUB..?

I am confused because I know that the root should be hd1, but why then is Ubuntu hd0 is if it on the external drive just like Zenwalk?

---

### Post by bonzodog on 2007-03-26
yeah, it might be that you unplugged the internal HDD, so the external HDD became the first logical one, making it sda. Why it's now sdb, but still boots as 0,0 is strange. 
that shouldn't be possible.

Are you sure that Ubuntu see's it's own root on /dev/sdb?

if so, does that mean that windows is on /dev/sda on the internal drive?

Where is grub installed?

on the external drive or the internal drive.

Logically, it should always be on /dev/sda.

---

### Post by dam2 on 2007-08-20
I found this information, I'm late but it might be usefull :

[http://support.zenwalk.org/index.php/topic,9843.0.html](http://support.zenwalk.org/index.php/topic,9843.0.html)
the useful part :

[HTML] I boot with Grub. This is what i have:

title      ZENWALK
root      (hd0,2)
kernel      /boot/vmlinuz root=/dev/sda3
initrd      /boot/initrd.splash
savedefault
boot

ZW is on partiton 3[/HTML]

---

