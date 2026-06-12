---
title: "Booting and installing Linux OSes from hard disk"
date: 2008-10-03
forum: The Cafe
---

### Post by Anpheus on 2008-10-03
I will be succinct, the information scattered on the internet is *inconsistent*, *incomplete*, and typically *limited in utility* on how to boot a Linux 'live' environment from disk or installing Linux from disk.

Not saying it's impossible, I actually got unetbootin working for one ISO, but it's still a matter of trial and error, and it's not nearly as simple as having a CD burnt with the image on it.

What I would like is the ability to quickly and easily download an ISO and have it boot as if it were a CD. Maybe this can be accomplished with an initrd that contains Xen and can trick the liveCD into thinking it's on /dev/cdrom when it's really /dev/sdblah. It doesn't matter how it works. I want this topic to be a brainstorm of how it can currently be done, with all their imperfections, ways that we could potentially do it in the future, and how we get to the latter from the former.

Let me just quickly summarize what I would currently like to do, given my current hardware. I would like to install GRUB to a primary and secondary hard disk, and also to an external (USB-attached) external hard disk. GRUB would reference *dozens* of netboot installs. I want all of them on disk somewhere (as tiny netboot installs,) I could script the operating system (primary OS is Vista, don't kill me) to update the available netboots perhaps. I would also like a few liveCDs from different distros that I could swap in and out as I wanted to, this would let me both install and play around with different linux distros on my CD-less laptop and my desktop, and also be great for just doing quick checks when repairing other people's computers. (Or even converting them to Linux! See, I told you not to kill me after I said the V-word.) Then, I would like some DVD installs, the non-liveCD kind. OpenSUSE has one that contains a truly inspiring quantity of packages. Stuff like that.


Current issues: 
[list][*]unetbootin is unreliable on my machine. The Ubuntu 8.04.1 64-bit LiveCD drops me down to the initramfs every time. I've tried replacing quiet splash with all_generic_ide and it doesn't work. I've tried changing the partition I copied files to, and that doesn't work. I also tried FAT and NTFS filesystems. I think the problem might be that I am telling it to do a USB install and I'm specifying an internal hard drive. More on that follows:
[*]It only lets me install from *one* of my internal hard disks, the one Windows is running on. I don't like it polluting and renaming my primary hard disk with all sorts of files. Also, it makes me more worried that something could go wrong. I have more than one internal disk and about a dozen partitions, one of which I specifically created for the purpose of letting unetbootin/linux installers/liveCDs/DVDs have a sandbox with a useful filesystem. Why can't I use them?
[*]Unetbootin to external USB drives doesn't list anything unless I check "show all drives." This is slightly scary.
[*]Unetbootin to internal hard drives doesn't let me check show all drives.
[*]Unetbootin's bootloader tends to not work and I use neogrub from easyBCD to manually specify ubnkern/ubninit, the .mbr or whatever unetbootin created. This might relate to the issue above, with it looking for a USB hard disk.
[*]There's no functionality to boot ISOs without time-consuming expansion, is this something that could be implemented in a script or mounted by the initial ram image? Could that carry into greater functionality in the future, say, to boot a Vista Recovery Environment or install disk?[/list]

If you have any advice on the specific goals I'd like to push for the developer community, some comments or additions, please post them. This topic is not solely about my specific problems, but about making the process of installing Linux as easy as possible, as accessible as possible. Not just ubuntu, but every OS could benefit from the achievement of the goals above.

If this isn't the right place for this post (Installation & Upgrades) please inform a moderator.

---

### Post by cariboo on 2008-10-03
I hate to rain on your parade, but what you want to do is not possible, the closest thing to what you want to do is using vm's. Install something like VMWare Server and you can install as many different os's as your hard drive can hold.

I'm sure others will pipe up proving that there is some way to do that you want that I can't find anything about.

Jim

---

### Post by Anpheus on 2008-10-03
While you or I may not have the solution at our fingertips, that doesn't mean it's not possible.

And like I said, perhaps a Xen-enabled initial image of Linux would allow you to virtualize the hardware, making the installation think it's running off a CD-Rom. That seems to me like the 'easiest' way, even though I have absolutely no clue how to go about it. That would also probably be the most portable. If it worked, you could pretty much install anything that has a disk image. Not just Linux, but even Windows. Likewise, you could abstract the hardware any way you wanted, such as installing Windows to a USB hard drive by making it think it's a local disk. (The Windows installer adamantly refuses to be installed on non-internal/non-hotswapped storage.)

So, is this an option that someone experienced with Xen could answer? Come on, let's brainstorm. Are there ways that are potentially simpler than this? Am I leaving something out that makes this harder than I think, and by that I of course mean, harder than I think someone skilled with Xen could accomplish.

---

### Post by Anpheus on 2008-10-03
If this is not the right forum for this discussion, as evidenced by its quick departure from the front page of the forum, I would like a moderator to please correctly place it and/or inform me of who I should get in touch with to push a project like this forward. I have some ability to program myself, and I'm at least competent in Linux administration and terminology, though not nearly as much an expert as I am in Windows administration.

Thanks in advance.

---

### Post by Sef on 2008-10-03
Moved to community cafe.

---

### Post by Forrest Gumpp on 2008-10-04
Does this post by John_Spiral help?

Its opening explanation is:


" HOWTO Boot from a .iso file without needing a working CD-ROM - REALLY USEFUL!
BOOT ANY OS USING THE Gujin BOOTLOADER

Below is a faster method for installing/running any OS / LIVE-CD directly from a separate hard disc partition.

I was spurred into discovering the below method while trying to install various distros on an old Sony Vaio that didn't have a CD-ROM drive."


The UF URL is  [http://ubuntuforums.org/showthread.php?t=666267](http://ubuntuforums.org/showthread.php?t=666267)

---

### Post by Anpheus on 2008-10-04
That's close but it doesn't solve problems with unetbootin, which I'm trying to spur here, and it doesn't push us toward a more universal solution for installing without external media.

---

### Post by Anpheus on 2008-10-05
Alright, this obviously seems like the wrong place for this discussion, any advice on where to take this?

---

### Post by Riffer on 2008-10-05
What you're doing sounds very cool, its also very esoteric.  I wouldn't have a clue where to find info on this.

My one suggestions is to try the 32 bit version, rather then the 64 bit of Ubuntu.  The 64 bit version seems to be a bit buggy, that may be your problem.  

Good luck

---

### Post by Anpheus on 2008-10-05
Thanks for your honesty, the problem is, as I thought, unetbootin's silly idea of what is a local hard drive/partition and what is a USB hard drive/letter. It thinks I have one of the former and none of the latter.

If I do let it use my Windows partition, it works fine. If I use any other partition, it tends not to boot, and drops me to a command line.

There needs to be a better way.

---

### Post by Forrest Gumpp on 2008-10-05
> **Anpheus said:**
> Alright, this obviously seems like the wrong place for this discussion, any advice on where to take this?

I'm out of my depth in understanding exactly what you want, but sense that this is a subject that you may get help on from the Hermanzone, see:  [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)  It's quite an extensive site, and is mentioned in the stickies somewhere.  I'm only guessing from your relatively short posting history that you may be unaware of it.

Even if its not covered, this strikes me as the sort of thing Herman could be interested in creating a tutorial about.

---

