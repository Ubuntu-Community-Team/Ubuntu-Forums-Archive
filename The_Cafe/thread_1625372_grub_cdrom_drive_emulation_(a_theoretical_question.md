---
title: "grub cdrom drive emulation (a theoretical question)"
date: 2010-11-19
forum: The Cafe
---

### Post by jadeddragoon on 2010-11-19
Ok, first I'll apologise for making such a post my first post.  I also apologise for putting this here... I looked but could not find a place more suitable.  Let me make up for it by giving you guys a basic idea of who I am and what my knowledge set is.

I am a professional computer repair tech.  No... not like the minimum wage workers at geeks squad.  A real computer tech.  I run my own business catering to local businesses... giving them service equivalent to a one-man in-house IT department without the overhead and need to justify the constant cost of wages for an actual in-house IT department.  Of course I charge a premium for such service.

I also do computer work for home users, as well as tutoring... so I am good with the human element of the computer world as well (something that is far too rare in this industry).

Something many do not understand about a computer technician is that we are not going to have the same in-depth knowledge of, for example, software programming that a programmer will... or of web development that a web designer would... but that we will have a wide... some what superficial... knowledge of a great many different segments of the IT industry.  More importantly we understand the connections between them... something that specialists often lack.

Think of me as a general practice doctor compared to a cancer specialist or a surgeon.

The reason I put that out there is I want to make it clear what I do and don;t know.... and to point out that bringing together separate concepts into a coherent whole is my thing.

And on that note... I have a question...

Why has no one developed a method of emulating cdrom drives pre-kernel load?

Grub2 (and many other boot loaders) offer the option to chainload an iso file... but only under very limited circumstances.  Grub, for example, can boot some iso images... but only those containing a specific kind of live-cd.  Other bootloaders seem to be able to chainload any iso... but if the iso latter tries to figure out the cdrom drive that it is booting from (as those same live-cds do) it hits a brick wall and can no longer continue.

The solution then... would be to emulate a piix4 ide controller with a generic dvdrom drive attached as primary master.  This is exactly what VirtualBox does and since the OSE version is open source the code to do so should already be available.

The trick... in so far as I know... is that calls to the bios by any kernel loading after that point would have to be intercepted and the correct info from the bios plus the simulated controller and drive passed to the kernel.  Now... I don't know if that is possible... but... older machines (back in the days of windows 95 and 98 ) often used BIOSes that could not properly identify a drive larger than 8gb.  Maxtor (and others) developed a work around where a modified bootloader was installed the mbr that intercepted calls by kernels loading after that point to the bios and gave the correct geometry for the hard drive... instead of the incorrect geometry that would have been provided by the bios.  Could the same be done here?

It sees that if these two tricks were put together it would then be possible to "mount" and boot any iso file as if it was an actual cd.  Imagine a USB pendrive with grub and a long list of iso files containing diagnostic tools and all your windows cds/dvds... linux live-cds... etc....  This would be tremendously useful to me in my computer work.

Now opensource is all about the "if your know what to do and see something that needs to be done do it yourself" mentality... but I am no coder.  I've played around with perl, C, Tcl, and many other programming/scripting languages... but I am no where near the skill set needed for production environment grade code.

So I'm hoping this will get the attention of some one who is and maybe lead to a new module being incorporated in grub2 for this purpose.

Or maybe I'm completely unaware of intricacies that make this impossible... can't know if you don't ask... right?

---

### Post by oldfred on 2010-11-19
I have a 4GB Flash with many Linux repairCDs and my Ubuntu for installing. All boot directly with grub2. I also have another that I installed the windows repair CD from neosmart and copied it to a flash drive, installed grub2 and boot windows and several ISOs. Some ISO that are not directly bootable just need to have the kernel & initrd installed to boot the ISO which I have done with puppy.

I think the MultiBootUSB script automates what I did manually. (In some cases I have cheated and checked the script to see how he did it to understand what to do manually).

 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)

MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
multicd.sh - combine Linux ISOS into one
[http://ubuntuforums.org/showthread.php?t=1071869](http://ubuntuforums.org/showthread.php?t=1071869)

older MultiBoot USB with Grub2 (boot directly from iso files)
Is full script, I only used some commands
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)

---

### Post by czr114 on 2010-11-19
This seems somewhat kludgey for the given goal. How many live CDs are you dealing with, and can they be merged? The open source stuff should be able to share one live environment. How many proprietary environments are involved?

---

