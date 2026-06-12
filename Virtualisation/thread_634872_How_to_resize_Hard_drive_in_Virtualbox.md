---
title: "How to resize Hard drive in Virtualbox"
date: 2007-12-08
forum: Virtualisation
---

### Post by oneadvent on 2007-12-08
How do I make my virtual Hard disk bigger?

It is very new, but I do not want to reinstall because then I might have to call microsoft for activation, and that is annoying.

So back to my question. I did try to use gparted like other threads have suggested, but it doesn't allow me to make it any bigger.

Thanks,

Joshua

---

### Post by viking777 on 2007-12-08
You read the help files which say:

> The VDI files reside on the host system and are seen by the guest systems as hard disks of a certain geometry. When creating an image, its size has to be specified which determines this fixed geometry. It is therefore not possible to change the size of the virtual hard disk later.

---

### Post by oneadvent on 2007-12-08
well that is stupid, given the very nature of virtual disks

---

### Post by shafin on 2007-12-08
Threr is a workaround..I hope it'll work for you.

1.Create a bigger virtual disk.
2.Boot your VM with the ubuntu LiveCD and the two vms as primary and secondary HDD.
3.Mount the disks.
4.Copy everything from the small disk to the bigger new disk.

Good luck...no try booting from the new disk,if you succeed, delete the old one.

---

### Post by shafin on 2007-12-08
And for shrinking,try this out:

[http://forums.virtualbox.org/viewtopic.php?t=2507&start=0&postdays=0&postorder=asc&highlight=](http://forums.virtualbox.org/viewtopic.php?t=2507&start=0&postdays=0&postorder=asc&highlight=)

---

### Post by oneadvent on 2007-12-08
Hey that is a really good idea. I will have to try that later on. I ended up making another partition, and then using that to install programs on. This is my first round with Virtualization. I suppose it isn't the first time I run into problems.

---

### Post by oneadvent on 2007-12-09
Okay. I tried to copy the windoze partition and it did not work.

It did copy the files, but some of the "hidden" folders were not hidden and it did not boot.

Should I have changed the drive to have the boot flag?

What about the hidden folders/files that are now showing up?

Thanks for any help!

---

### Post by oneadvent on 2007-12-10
As an update, yes it needs to have the boot flag.

I do not know what was the deal with the flags, I just did a reinstall and copied things over.

Thanks for the help all.

---

### Post by glymph on 2009-02-22
Using [self-image]("http://selfimage.excelcia.org/") you can copy the disk, then a disk management utility such as diskpart or Partition Magic, expand the drive to fill the available space. There are further details on the [virtualbox forum]("http://forums.virtualbox.org/viewtopic.php?t=1878"), but the diskpart method doesn't appear to work for recentl (XP servicepack 3) XP installations.

---

### Post by FirstByté on 2009-07-08
**Just a quick note on how I was able to RESIZE my fixed Virtual [2.5GB to 10GB] WinXP Hard drive in VirtualBox.**:p

First, you may need to grab the Acronis CD or [*ISO image like I did in my case.... dint wanna burn a new CD just to do this ;)*]

*    Then stop the Virtualbox if you haven't stopped it.
*    [CREATE A NEW LARGER HARD DISK] I just tricked Virtualbox by creating a new OS, whereupon I created a 10GB dynamic harddisk on my freer host hard disk this time. [*Sorry I dint know a better way to do this.*] Next you would add the harddisk as a slave hard disk under the previous OS... not the new one just created
*    Load the Acronis CD and make sure the VirtualBox boots up into the CD. Virtualbox has the 'boot from CD 1st' order checked by default
*    I dropped straight to the Clone 'Hard drive option' and miraculously the new 10GB HDD showed up and i chose it as my destination HDD
*    Once cloned... all you need do is set the new HDD as the primary and either forget about the old HDD or just keep it:guitar:
*    Never under forget to plan ahead before you create HDD in future and choose the 'Dynamic' option :popcorn:

Happy Virutalizing!!

---

### Post by franjo101 on 2009-07-09
Hi to all!
I have read the thread, and have a question.
I do have dinamic HDD in my VirtualBox, how to enlarge one of those?

---

### Post by franjo101 on 2009-07-10
Or if that isn't posible (and I think it isn't, because I have read that somewhere) plesae tell me how did You boot from CD. I men, I can boot from CD (I have Hiren's 9.6) but when the computer gets to loading CD drivers.......nothing, computer freezes.
What should I do to solve this?
It's Ubuntu Jaunty host, and Vista ultimate guest in VirtualBox.

Don't bother.... I used Acronis on his own, not on Hiren's CD, and I succeeded

---

### Post by jens-mct on 2009-07-11
i also recommend you add the larger new seconddrive en then use a boot .iso to copy the entire drive to the new one (for example, norton ghost or clonezilla (free))

if your pc won't boot because of a missing mbr see [http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true)

---

### Post by lunatico on 2009-08-06
I just did this to resize my disk and it works a treat!
[http://www.modhul.com/2008/10/21/re-sizing-a-virtualbox-virtual-disk-image-file/](http://www.modhul.com/2008/10/21/re-sizing-a-virtualbox-virtual-disk-image-file/)

---

### Post by blumojo on 2009-08-23
Instead of using Acronis;

I cloned the partition with the Clonezilla ISO:
[http://clonezilla.org/](http://clonezilla.org/)

then I resized the partition with the GParted Live ISO:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by carlitos.10040 on 2009-10-16
> **lunatico said:**
> I just did this to resize my disk and it works a treat!
[http://www.modhul.com/2008/10/21/re-sizing-a-virtualbox-virtual-disk-image-file/](http://www.modhul.com/2008/10/21/re-sizing-a-virtualbox-virtual-disk-image-file/)

Roger that!!! 
This link did it for me.
Thanks for sharing.

---

### Post by 1longtime on 2010-02-13
> **blumojo said:**
> Instead of using Acronis;

I cloned the partition with the Clonezilla ISO:
[http://clonezilla.org/](http://clonezilla.org/)

then I resized the partition with the GParted Live ISO:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Same here.  That Acronis "register for a trial version" stuff didn't interest me.  A couple of things I noticed:

1) I kept getting "error bitmap free" messages/failure with Clonezilla until I put the source and target disks on different IDE channels (one on Primary, the other on Secondary).

**IF the guest OS is Ubuntu, read #2:

2) Using Gparted to resize the too-small Primary partition required moving the Extended partition (which is automatically created during an Ubuntu default installation).  It's not obvious how to do this, since Gparted did not give me the option to move it around ("disk space before partition" and "after partition" buttons were disabled).  I realized why: the primary can't grow because the Extended partition is creating a boundary on the Primary's right side.  So you need to move the Extended, which is tricky, to the right (toward the end of the disk).

To move the Extended partition, FIRST grow the Extended partition (I used the maximum space remaining on the disk).  Then move the Logical partition INSIDE of the extended partition to the far right (toward the end of the Extended partition).  You should now have options to change the disk space before/after the logical partition, the buttons will no longer be greyed out after you increase the size of the Extended partition.  Then you can change the disk space options before/after the Extended partition, so you can shrink it and shift it to the right (toward the end of the disk).

Go back to the Primary partition, you should have created lots of free space (to the right) for the Primary to grow.

---

### Post by lahmanwokard on 2010-03-02
I just tried this with a windows 7 vm. It worked very well but the boot loader freaked a little bit on the first boot of the “new” drive. I loaded an image of the win 7 install and ran a repair and viola! It worked perfectly.

---

### Post by jonley on 2010-05-27
Easiest way to do this is with clonezilla. First create the new hdd in virtualbox and add it as a secondary hdd to the vm. Mount clonezilla iso and boot from it. Select disk to disk copy and let it run. Then delete the old hdd. Very fast.

---

### Post by relapse on 2010-07-12
> **jonley said:**
> Easiest way to do this is with clonezilla. First create the new hdd in virtualbox and add it as a secondary hdd to the vm. Mount clonezilla iso and boot from it. Select disk to disk copy and let it run. Then delete the old hdd. Very fast.

This worked for me without a hitch. As a final step you need to use gparted. Download and mount the gparted iso and choose to boot from it. Once you're in the GUI, choose to resize the partition so that it takes up all the unused space and that's it.

---

### Post by WernerB on 2011-09-13
> **viking777 said:**
> You read the help files which say:

That is a bit out of date.

see:

VBoxManage modifyhd

---

### Post by nothingspecial on 2011-09-13
> **WernerB said:**
> That is a bit out of date.



Yes it is.

---

