---
title: "Repair Vista Boot Loader"
date: 2008-06-14
forum: Tutorials
---

### Post by tturrisi on 2008-06-14
If dual booting Windows & Linux, and also use GRUB, if you remove the Linux partition(s) you probably can no longer boot Windows.  While this is very easy to fix if the Windows operating system is XP or earlier, it is a bit more complicated (but still easy to do) in Windows Vista.

More often than not, when removing Linux partitions in a dual boot Vista-Linux environment, or when using GPARTED to resize partitions, Vista can no longer boot.

Windows Vista uses a different boot loader than earlier versions of Windows.  Fortunately the Vista bootable DVD contains a utility for repairing the MBR and boot sections of the hard drive.  To repair the Vista bootloader:  [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

However, the utility mail fail on any action and give an error message of **"Element not Found"**.  This is because resizing the Vista partition(s) or Linux partition(s) changes the disk's file allocation table and the Vista partition may get marked as "inactive".  The same holds true when removing or resizing Linux partitions.  A boot partition MUST be marked as "active" to be bootable.

The remedy for **"Element not Found"** is this:

1.Put the Windows Vista installation disc in the disc drive, and then start the computer.
2.Press a key when you are prompted.
3.Select a language, a time, a currency, a keyboard or an input method, and then click Next.
4.Click Repair your computer.
5.Click the operating system that you want to repair, and then click Next. (if no Vista operating system is listed, click Next anyway)
6.In the System Recovery Options dialog box, click Command Prompt.

Next:

At the command prompt, type **diskpart**.
This will get you to the DiskPart prompt, which allows you to use a variety of hard disk partitioning and formatting tools similar to FDISK in older versions of Windows.

At the DiskPart prompt, type **select disk #** where the # sign is the number of the hard disk drive with Vista installed on it. If your Vista drive is the only hard drive in your computer, it is Disk 0.

Select the partition by typing **select partition #** where the # sign is the partition that has Vista installed on it.

Type **active and press ENTER**. The Vista partition is now active. Finally, type 'exit' to close DiskPart. Reboot the computer using the Vista dvd and follow steps 1-6 above.  You can now repair the Vista boot:

Fix the Master Boot Record: (commands)

[b]bootrec /fixmbr
bootrec /rebuildbcd
bootrec /fixboot[/b]

You should now be able to boot Vista.  Then start over again and install Linux!

---

### Post by monkeyface766 on 2008-11-13
What if I don't have a vista cd: it came pre-installed.

Is there a way to activate the vista partition from Ubuntu?

---

### Post by MockY on 2009-01-07
I wonder the same. 
My friends laptop refuses to boot due to broken boot loader. This is however a single OS setup and it has never been a dual boot setup, so Grub or Lilo has never been installed on it. He did not bring his Vista disk with him and it just went bad while visiting.

So I wonder if I can repair the bootloader with Ubuntu Live Disc or replace it with Grub.

---

### Post by rotary12 on 2009-01-07
> **monkeyface766 said:**
> What if I don't have a vista cd: it came pre-installed.

Is there a way to activate the vista partition from Ubuntu?

you can download a vista boot cd.
google Bootmdr is mising

---

### Post by ashsmith on 2009-01-08
> **monkeyface766 said:**
> What if I don't have a vista cd: it came pre-installed.

Is there a way to activate the vista partition from Ubuntu?

I am thinking about this one as well.. Good question!

And if it's downloadable, is it free? if not, how much?

---

### Post by lifereversal on 2009-05-22
you should state the commands 

"list disk"

"list partition"

---

### Post by Daniel Balster on 2009-08-07
The above steps will fail if you're working with "dynamic disks".

- diskpart: marking as "active" says "invalid operation"
- bootrec: /rebuildbcd reports "not possible"

If someone runs into that problems:

diskpart> list disk
diskpart> select disk #    <- enter correct number from listing

diskpart> convert basic    <- convert disk back to basic

diskpart> list partition
diskpart> select partition # <- enter correct number from listing
diskpart> active

---

### Post by gunnar123 on 2009-10-13
Thanks Tturrisi, this helped me recover my Home Vista Basic partition
(first one on disk) after I removed my Ubuntu stuff on a laptop,
essentially repairing the boot record.
Using the automatic start repair command on the Vista DVD simply did a checkdisk and
did not attempt to restore the boot stuff. But your hints helped me do it.
The command "bootrec /rebuildbcd" indicated 0 installations detected but
the repair worked anyway. Some hints continue to help people long after they were posted.

---

### Post by paulkearney on 2009-12-03
Hi All,
 
Many thanks for all your help here. My problem wasn't a Ubuntu/linux related one, but thought I'd post up my findings for anyone that experienced similar...
 
I was upgrading the hdd on a Sony Vaio laptop running Vista. 
 
Ghosted the original disk off and ghosted back to new disk.
 
Disk wouldn't boot to O/S - kept wanting to start the Vaio recovery partition.
 
Downloaded Hiren's boot CD and used MBRWizard to set the O/S partition as active. Still came up with missing O/S on boot.
 
Downloaded Vista Recovery CD, booted off it as above and selected repair and command prompt. Ran three bootrec commands (identical to gunnar where is said 0 installations detected).
 
Rebooted and O/S started up!
 
Thanks again to all posters for advice.
 
Paul

---

### Post by Karim_ on 2010-05-24
You can easily get a Windows Vista Recovery Disk by following the white rabbit... Er... I mean link. Scroll down a bit, now choose your version and download the ISO image. This is NeoSmart Technologies version not an official Microsoft disk and it's only 120mb  [[COLOR="Blue"]http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/[/COLOR]]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/")

It has all the recovery functions like in the original Vista DVD disk, yet, something feels missing, yes, there is something missing, it's the full installation of vista. Don't click that option something terrible might happen

---

### Post by defaria on 2010-05-27
No matter what I do the bootrec /fixboot keeps saying that Element is not found. Note this is a VM copy of my physical machine. I've set the partition active time and time again but it still says "Element not found". 

Help!

---

### Post by arscek on 2010-06-16
Thanks so much, this solved my problem.

---

### Post by chinoto on 2010-09-05
The Windows partition on my laptop started to act up about half a year ago and restart at the screen with the Windows logo and progress bar, I used the Startup Repair thing for awhile, it stopped working so I used your guide. Somehow it breaks itself after every shutdown. Recently I decided to wipe my harddrive so I could reorganize the partitions and install the 64bit version of Windows. Guess what, same exact problem.

Since it manages to get to the "Windows is pretending to load" screen, am I correct in assuming that I don't need to do "bootrec /fixmbr" or "bootrec /fixboot"? I tried "bootrec /rebuildbcd" by itself recently and that seemed to work, but maybe it wasn't broken that time. If so that might help narrow things down.

---

### Post by shegra on 2012-02-14
Alright, i have tried to boot my windows vista disk but it ignores me and when i looked to see if my computer even knew it had a disk in it, it shows nothing. i checked the disk drive but it says not suported. i need to get ubuntu off my computer and i need to get windows back on it. Help Please!

[IMG]http://api.photoshop.com/v1.0/accounts/1dd78d2034b642488666900a28f3d621/assets/5ea08e9101464d619dbee859a876264c/renditions/1024.jpg?md=1329205371000[/IMG]

---

