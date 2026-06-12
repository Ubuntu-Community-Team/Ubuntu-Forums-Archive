---
title: "Systemback - Software to make an image of your installed OS"
date: 2014-07-15
forum: The Cafe
---

### Post by tea for one on 2014-07-15
I came across this software via this website [http://www.unixmen.com/systemback-restore-linux-system-previous-state/](http://www.unixmen.com/systemback-restore-linux-system-previous-state/) and I thought that I would investigate further.

In the past, I used Remastersys but I know that it is in the process of being released by another developer soon.
Anyway, I followed the instructions on the Unixmen site and installed Systemback via the PPA.

I have successfully created a system image and converted it to an ISO (total size 1.3GB)
The ISO image was put on a USB stick using the Start Up Disk Creator in Ubuntu
The USB stick booted OK but I was _surprised_ to have to log in using my original User name and Password.
Systemback is still present on the live system and you can use it to install the live OS.
I had a spare drive, so I tried the installer and so far so good. I am writing this post from the new installation.

I haven't tested the new installation thoroughly yet, but the important things like wifi, ethernet, sound and video all seem OK.
By the way, I did not include user data in my image only the operating system (14.04 including Unity & Gnome Shell)

There are many posts in the Ubuntu forums for imaging apps and I hope that a few other users will give it a test drive to see if it is suitable.

The developer has a launchpad account [https://launchpad.net/systemback](https://launchpad.net/systemback)

---

### Post by mooreted on 2014-07-15
That sounds pretty nice. I will have to check it out.

---

### Post by rv_happy on 2014-07-29
Sounds interesting. In the past I have also used remastersys and mklivecd (on pclinuxos). Right now i have found the Retracta tools to be the best current option but I'll definitely give this a try sometime. Does it compress the livecd image do you know?

---

### Post by pretty_whistle on 2014-07-30
That sounds great so I installed it.  I can't run it because it's asking for a password and wont accept my root password.  What the......... ?

Too bad.

---

### Post by tea for one on 2014-07-30
> **rv_happy said:**
> Does it compress the livecd image do you know?

Yes, it does compress the live image.

When I did a test, the live image was 1.3GB and the installed OS is around 6.0GB.


Kind regards

---

### Post by tea for one on 2014-07-30
> **pretty_whistle said:**
> That sounds great so I installed it.  I can't run it because it's asking for a password and wont accept my root password.  What the......... ?

Too bad.

I do not have a root password only a user password which allows elevated privileges. By this, I mean the password that you enter after sudo.......

My user password allowed me to use the software.

Are we talking about the same password?

You may wish to direct your question to the developer's launchpad page, where there are other questions & answers about this application.

Best wishes

---

### Post by SurfaceUnits on 2014-07-30
Remastersys is still the best. Install it, launch it, click Dist and in a short while you will have your compressed, bootable iso using the ubuntu default Live session user account. Many options for finetuning your output. Grub boot menu background image, live cd grub background image, file name, session name, and more.

---

### Post by rv_happy on 2014-07-30
But Remastersys is no longer developed and as I understand each new Ubuntu version breaks Remastersys (I am happy to be corrected). BlackLab Linux took the code and redeveloped it for their own purposes but have since taken it down from their public site.I couldn't get a bootable image off it anyway (though I was probably doing something wrong).

---

### Post by rv_happy on 2014-07-30
> **tea for one said:**
> Yes, it does compress the live image.

When I did a test, the live image was 1.3GB and the installed OS is around 6.0GB.


Kind regards Thanks, sounds good. I'll definitely be testing it soon :)

---

### Post by SuperFreak on 2014-07-30
I recall with Remasterys there was a limitation on back up size is this the case with Systemback? I have been using ReDo for a backup of all system partitions (EFI and Root) and Home

EDIT:Tried it  and used it to create Restore Point. Be advised that on my system the restore point was nearly 10 GB and that is a lot on an SSD. So I changed the directory I was using for my Restore Point to my HD

---

### Post by SurfaceUnits on 2014-07-30
> **rv_happy said:**
> But Remastersys is no longer developed and as I understand each new Ubuntu version breaks Remastersys (I am happy to be corrected). BlackLab Linux took the code and redeveloped it for their own purposes but have since taken it down from their public site.I couldn't get a bootable image off it anyway (though I was probably doing something wrong).

Remastersys is working fine on 14.04. The only issue I ever had was when resolv.conf was changed to a symbolic link, 12.04-12.10, but it was quickly resolved.
Remastersys is not proprietary in that it combines standard ubuntu utilities/applets into a useful program.

---

### Post by SuperFreak on 2014-07-30
Well I have tried Systemback for Restore Points and also LIVEUSB and it works very well. It has overcome Remastersys limitations on space and works with larger volumes on USB Live. I booted up a live USB and it worked exceedingly well;even symlinks to my other hard drives not backed up remained intact and functional. Wallpaper, programs, DE etc all intact. It even booted up to the last pages on firefox I was at.Gave a donation to the devs as this is valuable GNU software, While I created Restore Points sucessfully I did not try restoring my sysytem from them. Works much better than REDO for Ubuntu but on the other hand REDO will back up my entire Dual Boot (both OSs)I donn't think this will do that

---

### Post by Redalien0304 on 2014-10-22
Where is Systemback Tmp folder at? have cannot find it. for when it does backups & creating a sblive or Iso format? Than for any info in Advance. Thanks

---

### Post by tea for one on 2014-10-22
> **Redalien0304 said:**
> Where is Systemback Tmp folder at? have cannot find it. for when it does backups & creating a sblive or Iso format? Than for any info in Advance. Thanks

When you open the application, the storage directory location appears in the top right corner.

I use the the default location ...../home

Kind regards

---

### Post by Redalien0304 on 2014-10-22
ok Thanks i found it in with Nemo File Manger in File System/Home/Sustemback not in as i Understood it from Systemback. Thanks

---

### Post by xmbwd on 2014-12-03
I've been using Systemback as an alternative to Remastersys.  I can create a LiveCD .iso, copy it to a USB (using Multisystem, which is AWESOME), and boot from it.  Does anyone know if it is possible to install that Live system to the computer that I booted into from the USB?  I'd like to be able to make my .iso into a mini-distribution.

---

### Post by tea for one on 2014-12-04
> **xmbwd said:**
> I've been using Systemback as an alternative to Remastersys.  I can create a LiveCD .iso, copy it to a USB (using Multisystem, which is AWESOME), and boot from it.  Does anyone know if it is possible to install that Live system to the computer that I booted into from the USB?  I'd like to be able to make my .iso into a mini-distribution.

Yes indeed, you can install your iso.

Systemback > System Install (On the right hand side)

Experiment on a free partition and let us know the outcome.

---

### Post by xmbwd on 2014-12-04
So I got it to install from the live system using Systemback.  The sequence seems to be that you (1) set the mount point (I selected "/"); (2) set the file system (I selected "ext4"); and then (3) click the little, green, back-ward facing arrow to "Change Partition Settings."  This allowed me to run and complete the System Install.  

**However**, the newly installed system **_did not_** show up in my GRUB2 at startup, *so I could not boot to it*.  In the Disks application, the partition with the new install shows up as "SB@," whereas my other, bootable partitions show up as "Filesystem."   And I can mount it and see what looks to be a Linux system.  But again, I can't startup from it or see it in GRUB2.

  Is there some additional step that I need to take?  Or did I mess up by setting the mount point to "/"?  

Alternatively, is there a way to install the Live system from the running USB as you would when you create a Live ISO USB from the default installer?  That is, is there a way to get the "Install Ubuntu" application on the Systemback ISO?

---

### Post by tea for one on 2014-12-05
> **xmbwd said:**
> So I got it to install from the live system using Systemback.  The sequence seems to be that you (1) set the mount point (I selected "/"); (2) set the file system (I selected "ext4"); and then (3) click the little, green, back-ward facing arrow to "Change Partition Settings."  This allowed me to run and complete the System Install.  

**However**, the newly installed system **_did not_** show up in my GRUB2 at startup, *so I could not boot to it*.  In the Disks application, the partition with the new install shows up as "SB@," whereas my other, bootable partitions show up as "Filesystem."   And I can mount it and see what looks to be a Linux system.  But again, I can't startup from it or see it in GRUB2.

  Is there some additional step that I need to take?  Or did I mess up by setting the mount point to "/"?  

Alternatively, is there a way to install the Live system from the running USB as you would when you create a Live ISO USB from the default installer?  That is, is there a way to get the "Install Ubuntu" application on the Systemback ISO?

If you have installed your Systemback OS in a multiboot situation, can you probe and update grub from one of your other systems? You may be able to detect your recent installation.

Alternatively, you can try this:-

Return to the Ubuntu system you wish to back up
Download and install ubiquity (Live CD installer) via synaptic
Download and install GParted (partition manager)
Create a Systemback back up
Convert the back up to an iso.
Create a live USB/DVD using Start Up Disk Creator (Ubuntu's own utility)
Try and install using ubiquity

When I experiment with this type of installation software, I remove my daily hard drive and use an old redundant drive as a destination so that I don't lose anything important.
Be careful and take backups before experimenting.


Best wishes

---

### Post by mastablasta on 2014-12-05
> **SuperFreak said:**
> .... While I created Restore Points sucessfully I did not try restoring my sysytem from them. 

well that is the other important part - to be able to restore.
1 more week and then I will have time to test it in virtualbox first of course.

---

### Post by flaymond on 2014-12-05
Well, for me...I just use options from Xfburn software or Brasero to create image data from the extracted iso files in the USB. Then, it will create a new iso file (just like downloaded from Ubuntu) back. I don't know if it's worked to reinstall using the recreated and reused  iso file to install Ubuntu. Anyone had tried this? Maybe, I'm make a mistake in this. :(

---

### Post by xmbwd on 2014-12-06
I was able to install the Systemback .iso and (almost) boot from it after running "sudo update-grub" from another, working partition!!  Unfortunately, the boot failed about 3/4 through with a /boot/efi error. 

 Not sure what that is about.  I'm going to try another route to install the .iso on the USB and post back.

---

### Post by xmbwd on 2014-12-06
Thanks for the suggestion below.  I created the bootable .iso from "Startup Disk Creator," but how do I "[COLOR=#b22222]install using ubiquity[/COLOR]" after I boot from the USB with the .iso?  I can't find that option in Startup Disk Creator.  Thanks. 


> **tea for one said:**
> If you have installed your Systemback OS in a multiboot situation, can you probe and update grub from one of your other systems? You may be able to detect your recent installation.

Alternatively, you can try this:-

Return to the Ubuntu system you wish to back up
Download and install ubiquity (Live CD installer) via synaptic
Download and install GParted (partition manager)
Create a Systemback back up
Convert the back up to an iso.
Create a live USB/DVD using Start Up Disk Creator (Ubuntu's own utility)
Try and [COLOR=#b22222]**install using ubiquity**[/COLOR]

When I experiment with this type of installation software, I remove my daily hard drive and use an old redundant drive as a destination so that I don't lose anything important.
Be careful and take backups before experimenting.


Best wishes

---

### Post by tea for one on 2014-12-06
> **xmbwd said:**
> Thanks for the suggestion below.  I created the bootable .iso from "Startup Disk Creator," but how do I "[COLOR=#b22222]install using ubiquity[/COLOR]" after I boot from the USB with the .iso?  I can't find that option in Startup Disk Creator.  Thanks.

Ubiquity is not an option in Startup Disk Creator.

Ubiquity is the Ubuntu installer which is included when you first install Ubuntu. After Ubuntu is installed, I'm pretty sure that Ubiquity, Gparted and some other packages are removed because they have become redundant.

I was hoping that, if you had Ubiquity in your remastered ISO, the installer would help you in a similar fashion to a first- time installation of Ubuntu.

With regard to your previous question, regrettably (or fortunately), I have no experience of EFI so I cannot offer any more assistance.

You may wish to post a question on the developer's launchpad page about installing in a multi-boot system together with EFI partitions.

---

### Post by xmbwd on 2014-12-06
I installed Ubiquity and re-did the Systemback live .iso.  I then installed it on a USB using Systemback and Multisystem (two different attempts).  While I can boot from the USB using the created .iso, it throws a lot of system errors related to the Terminal -- which is weird.  Worse, when I attempt to install the Live system from Ubiquity, it hangs at the map where you choose your location.  And while Systemback says it successfully completes the installation, the partition where I put it won't boot out of Grub. The latest error I get is "partition does not exist" "alloc magic is broken."  

I've spent the day with this and I'm at a loss for what I'm f'ing up.  It all seems pretty straightforward.  Aaaarggh!

> **tea for one said:**
> Ubiquity is not an option in Startup Disk Creator.

Ubiquity is the Ubuntu installer which is included when you first install Ubuntu. After Ubuntu is installed, I'm pretty sure that Ubiquity, Gparted and some other packages are removed because they have become redundant.

I was hoping that, if you had Ubiquity in your remastered ISO, the installer would help you in a similar fashion to a first- time installation of Ubuntu.

With regard to your previous question, regrettably (or fortunately), I have no experience of EFI so I cannot offer any more assistance.

You may wish to post a question on the developer's launchpad page about installing in a multi-boot system together with EFI partitions.

---

### Post by xmbwd on 2014-12-16
The Systemback developer fixed this issue and instructed me how to remedy parts that were my fault.  [Here]("https://answers.launchpad.net/systemback/+question/258754") is the thread.

---

### Post by rijnsma on 2015-03-03
The best thing I found for producing 'live-media' this far is 'systemback'. 
Get the right version. Learn with care how it works. 
And it does simply and perfect what is needed.
It does more than making live-media. It can even make restorepoints and copy a system to 
another partition.

I think all who are interested to save their system also this way were waiting for this one.. :D

See for example:
[http://launchpad.net/systemback](http://launchpad.net/systemback)
[http://sourceforge.net/projects/systemback/](http://sourceforge.net/projects/systemback/)

---

### Post by charito on 2015-08-10
I managed to use the iso created by systemback and installed it with no problems,i took the iso back to windows and used rufus,it booted no problem and installed with a different gui,i guess systemback,it was hard to do but i did it and it worked good, just one app gave me problems and that was popcorntime

---

