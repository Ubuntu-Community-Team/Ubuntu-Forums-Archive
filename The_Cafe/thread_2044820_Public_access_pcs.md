---
title: "Public access pcs"
date: 2012-08-20
forum: The Cafe
---

### Post by primozcas on 2012-08-20
Hello,
I have 10 days to prepare cca 20 computers for our local community/youth centre. Its surpsrising how little you have to know to be "the linux guy" and get in over your head :)
Machines are of course from different sources, but most will run Ubuntu 12, the rest will be on Lubuntu. They will mostly be used as public access pcs and occasionaly as classroom. We want to set them up so guests will have maximum possible options like installing extra programs, but when user is logged off, everything gets deleted and the system is restored. 
Can I get some input from you guys? I thought about deleting guestuser at shutdown and create new one, but that will not delete installed programs? 
We also need remote desktop access of "collaborative" kind, so guest sees what remote admin is doing (remote help during class). Suggestions?

---

### Post by Lars Noodén on 2012-08-20
If you're doing a kiosk, then there are some good instructions here:

[http://www.alandmoore.com/blog/2011/11/05/creating-a-kiosk-with-linux-and-x11-2011-edition/](http://www.alandmoore.com/blog/2011/11/05/creating-a-kiosk-with-linux-and-x11-2011-edition/)

Otherwise, about installing programs, you'll need to used [dpkg](http://manpages.ubuntu.com/manpages/precise/en/man1/dpkg.1.html) with the option --get-selections to make a list of what is and isn't installed on your base system.  Then on each boot or shutdown make a diff with what the current state is and then uninstall and purge what is extra.

---

### Post by ivanvodisek on 2012-08-20
Cheers!

Did U gave a though to some disk imaging program?

Like a hidden image partition that periodically overwrites the one used for all the fun stuff?

---

### Post by primozcas on 2012-08-20
Thanks for replies.
Ivan: That was my first idea, but we have no budget for something like Norton Ghost or Acronis, DriveImage XML is free but windows only, do you have any other suggestions?
Lars: if a kiosk is meant a machine with only browser, than no, these pcs need more functionality.
If I go the dpkg --get-selections way and also recreate guest user, is there anything else to consider? I like this idea because it would mean the machines will always be updated...

---

### Post by primozcas on 2012-08-22
Wrong thread?

---

### Post by Lightstar on 2012-08-22
I think making a custom live-cd is the way to go.  I have no doubt you can "burn' the iso to hard drive (like we do with usb sticks / memory cards).  So whenever someone shuts down the pc, all their stuff is deleted.  The next person comes to a fresh OS.

You'd have to customize it to make sure most of what they need will be there.  Also look up how to skip the tryout screen where it asks "Do you want to 1) Try Ubuntu or 2) Install Ubuntu ?"

[Remastersys ]("http://www.remastersys.com/") is well known for live-cds.  But there might be more options out there.

---

### Post by Petro Dawg on 2012-08-22
> We also need remote desktop access of "collaborative" kind, so guest  sees what remote admin is doing (remote help during class). Suggestions?Team Viewer works well as a remote access, but your use may be considered "commercial use".  To do everything "ethically" you may need get permission from Team Viewer developer  to use their free version in your situation.  Since it is a community/youth center, they may be willing to "donate" the software.

Also found [this]("http://forums.debian.net/viewtopic.php?f=16&t=49345") about enabling boot TORAM in a Debian distro, not sure if it works in Ubuntu though.  I assume you would have to edit the boot options to allow only booting to RAM in your case.

---

### Post by Pinoy Tux on 2012-08-22
> **primozcas said:**
> ...guests will have maximum possible options like installing extra programs
I think it's ill-advised to grant admin privileges to guests.  They can potentially hose the installation.  Better to create two users -- an administrator and a regular user.  Auto-login to the regular user account by default.

> **primozcas said:**
> ...when user is logged off, everything gets deleted and the system is restored.
You could adapt the technique used in [this thread]("http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Deepfreeze_for_Linux").  The user account automatically gets restored upon boot-up.  It all boils down to using the rm and tar commands to effectively wipe out and restore the regular user account in its pristine condition.

-----

+1 on Remastersys.

Set up a single machine and customize it to whatever is required and use Remastersys' Backup mode in making your remaster.  Deploy the remastered version on your other machines.  All of them will have a consistent look as you don't have to go through customizing each machine to match the original one.  It's a great timesaver when it comes to multiple deployments.

---

### Post by Lars Noodén on 2012-08-22
> **Pinoy Tux said:**
> 

+1 on Remastersys.

Set up a single machine and customize it to whatever is required and use Remastersys' Backup mode in making your remaster.  Deploy the remastered version on your other machines.  All of them will have a consistent look as you don't have to go through customizing each machine to match the original one.  It's a great timesaver when it comes to multiple deployments.

Instead of rm plus tar, you could do it all with [rsync](http://manpages.ubuntu.com/manpages/precise/en/man1/rsync.1.html).  It is faster since it only deals with the differences and can be set to erase extraneous files using the --delete option.

The CD/DVD idea is interesting.  You don't even need to burn the DVD, it can be booted straight from Grub:
[http://manpages.ubuntu.com/manpages/precise/en/man1/rsync.1.html](http://manpages.ubuntu.com/manpages/precise/en/man1/rsync.1.html)

[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)

---

### Post by Lightstar on 2012-08-23
> **Lars Noodén said:**
> 

The CD/DVD idea is interesting.  You don't even need to burn the DVD, it can be booted straight from Grub:
[http://manpages.ubuntu.com/manpages/precise/en/man1/rsync.1.html](http://manpages.ubuntu.com/manpages/precise/en/man1/rsync.1.html)

[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)

I didn't know that!
Grub booting the .iso from hdd... that's awesome.
I'm gonna have to play with it.
Thanks for pointing it out!

---

### Post by primozcas on 2012-08-27
Thanks everyone for info, greatly appreciated :)

---

