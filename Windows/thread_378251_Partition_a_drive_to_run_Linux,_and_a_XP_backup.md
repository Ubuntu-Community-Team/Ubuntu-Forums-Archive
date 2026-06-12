---
title: "Partition a drive to run Linux, and a XP backup"
date: 2007-03-07
forum: Windows
---

### Post by Support the 2nd on 2007-03-07
I have a 200gig SATA drive that I want to setup with 2 partitions.  One for Ubuntu, and the other for a backup of my first drive (XP).

Whats the best way to do this?  I know if I just right click the drive Windows will format it as NTFS right?  I can't have that I don't think.

---

### Post by wickstopher on 2007-03-07
The Ubuntu liveCD comes with gparted, which is a great graphical partition editing tool.  Boot the liveCD, and once you get into ubuntu there will be an "Install" icon on the desktop.  Go through the motions, and when you get to the partitioning phase, select "manually edit partition table."  From there, you should be able to shrink your Windows partition and create new root and swap partitions in the ext3 file format for Ubuntu.  After the installation of Ubuntu, you should get a Grub menu presenting you with the option to boot into either Ubuntu or Windows XP.  Post here if you have any problems with this, and good luck!

---

### Post by Support the 2nd on 2007-03-07
Thanks.  I will try that.

But just to be clear, will I get a boot selection all the time?  I really would rather just let it boot to XP from my PATA drive for the time being and hit F11 when I want to use Ubuntu off the SATA.  (Most things I do are still XP for the time being)

---

### Post by wickstopher on 2007-03-07
yes, you will get a boot selection every time.  i'm not sure how to change that.  once you figure out ubuntu, you won't be wanting to use XP so much, so it's not a big deal.  ;)  i still have both operating systems on my computer, but only use xp for very specific tasks (if only there were music notation software on par with finale or sibelius for linux....*sigh*)..  ubuntu, however,  is my day to day baby, and it only gets better from here.

---

### Post by Support the 2nd on 2007-03-07
Ok so right now I am in Ubuntu.  But I went to install and I am slightly confused about this partitioning thing.  First it asks me to "unallocate" some space.  Then the next one says I need two partitions for a */* root and a 256 meg space thing.  There are two areas fior my two HD's, but I don't get what I am supposed to do.  The last thing I want is to screw up my main IDE hard drive right now.

I plan on getting Ubuntu:Studio when that comes out if I like this one a lot.  I want something for home recording but everything I have used on XP has just irritated me.  Sonar has too much stuff.  I want something will less features, but not a nuetered LE version.

---

### Post by M_the_C on 2007-03-07
Firstly, the '/' or root partition is for all of the OS data and applications, the second smaller partition should be the linux swap partition.  Technically you don't need this but it is highly recommended, so create both on your second hard disk.

As for your first hard disk, I'm not sure, but I think you have to install GRUB on whichever hard disk is the master (in this case you XP disk) this should not need to affect your current XP partition.  

So, don't touch the XP partition on your XP disk, just re-partition your second disk.  

As for choosing which OS is started, have a look at [this.]("https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS")

---

### Post by Support the 2nd on 2007-03-07
> **M_the_C said:**
> Firstly, the '/' or root partition is for all of the OS data and applications, the second smaller partition should be the linux swap partition.  Technically you don't need this but it is highly recommended, so create both on your second hard disk.]

So I need to make 4 partitions on my drive?  And where do I do this at?  Can I do it in Windows first?

---

### Post by Support the 2nd on 2007-03-07
Okay so I just let the installer deal with everything and I set the one partition it asked me to make at 70 gigs.  Now here is the thing....

When I boot, rather than booting into XP from my PATA (which my BIOS is set to boot from first), it asks to boot from a couple Ubuntu options or XP...if I do nothing it goes to Ubuntu.

Then.....

If I choose XP, when it boots it says it needs to do a disk check on the Ubuntu drive unless I press a key.

---

### Post by Malac on 2007-03-07
Unfortunately you have over written the MBR of your XP (first)drive with GRUB
If you can decide which hard drive is the boot device from the bios then you need to boot your windows cd and use recovery console to run commands "fixboot" and "fixmbr" this should set up XP's boot loader to work from Hard Disk One.

Then boot the Ubuntu CD:
[System->Administration->Gnome Partition Editor]
Will take you to the partitioner.
To start over I would wipe Hard Disk Two, so long as there is nothing on there that you want, and start again with formatting the drive. I'd setup one partition for Ubuntu "/" to use. (If you're feeling adventurous set up a /home partition too.)
Then another which is the same size as your XP system or adequate to do your backup to.
Then if you have enough space setup a small fat32 area for easy transfer of files between the two OS.
Finally setup a swap partition which is 1.5 time the size of your RAM
It may be worth writing out the order you did them in and the rough size in MB so you can id them later.

Fire up the installer.
This time on one of the installer prompts you are asked where you want to install GRUB/Bootloader choose Hard Drive Two. I can't remember exactly which page or when in the process it asks you so look out for it.
Choose these partitions as where to install.
First for /
Fourth for /swap
You are probably best formatting the fat32 and backup partitions in Windows.

Let the installer do its thing then reboot this time it should have left your Windows boot menu alone and should only boot into the Ubuntu menu if you choose that disk from the bios menu.

Hope this helps.

---

### Post by Support the 2nd on 2007-03-07
> **Malac said:**
> Unfortunately you have over written the MBR of your XP (first)drive with GRUB
If you can decide which hard drive is the boot device from the bios then you need to boot your windows cd and use recovery console to run commands "fixboot" and "fixmbr" this should set up XP's boot loader to work from Hard Disk One.

Awesome.  It works perfect now.  Thanks.


> Then boot the Ubuntu CD:
[System->Administration->Gnome Partition Editor]
Will take you to the partitioner.
To start over I would wipe Hard Disk Two, so long as there is nothing on there that you want, and start again with formatting the drive. I'd setup one partition for Ubuntu "/" to use. (If you're feeling adventurous set up a /home partition too.)
Then another which is the same size as your XP system or adequate to do your backup to.
Then if you have enough space setup a small fat32 area for easy transfer of files between the two OS.
Finally setup a swap partition which is 1.5 time the size of your RAM
It may be worth writing out the order you did them in and the rough size in MB so you can id them later.

Fire up the installer.
This time on one of the installer prompts you are asked where you want to install GRUB/Bootloader choose Hard Drive Two. I can't remember exactly which page or when in the process it asks you so look out for it.
Choose these partitions as where to install.
First for /
Fourth for /swap
You are probably best formatting the fat32 and backup partitions in Windows.

Well I can no longer see the HD in XP.  I booted from the CD and went into Partition Editor, and I think I started to erase two of the 4 sections, but two 2.90G partitions were locked.  I didn't see anything in the menus to erase everything.

---

### Post by Malac on 2007-03-07
> **Support the 2nd said:**
> Awesome.  It works perfect now.  Thanks.
You're Welcome.
> **Support the 2nd said:**
> Well I can no longer see the HD in XP.  I booted from the CD and went into Partition Editor, and I think I started to erase two of the 4 sections, but two 2.90G partitions were locked.  I didn't see anything in the menus to erase everything.
In Partition Editor highlight each partition and right-click on it.
Choose Delete from the menu (you may have to unmount it first) and when finished marking the partitions for deletion click Apply on the Edit menu.
To be honest you could just do any resizing at this stage and choose to just assign the partitions you already have during Ubuntu Install and remember to choose /dev/ of the 200GB Hard Disk Two to install GRUB onto.

If you are more comfortable setting up partitions and formatting from within Windows do it from there but leave the proposed Ubuntu ones un-formatted.

Your partitions should look something like this:
/dev/xdx1     Ubuntu Root               mounted to  /
/dev/xdx2     Windows Backup       you can mount this later.
/dev/xdx3     Fat32 Sharing Area    mounted to /media/<whatever-you-want>
/dev/xdx4     linux-swap                 mounted to /swap

If you want to let me know of the proposed sizes you want for the partitions, I could block up some screenshots of what the install steps should look like.

---

### Post by Support the 2nd on 2007-03-07
I really botched this all up.  :( 

I need to get a removeable backup drive.  I was gonna disconnect my main HD but I got lazy......

I used XP's install disk to partition the other HD, but I decided to have it format it too on the one partition.  I forgot that it was gonna auto install afterwards, so it installs XP onto the partition.  So I wait for it to finish the first section, then I restart and boot back into XP's install disk to trash it and just leave it as a raw partition.  I go to reboot and there are now two XP systems to choose from on the boot screen, but the second doesn't work and the first goes as far as "Windows is starting up..."  THe computer freezes there.

:-({|= [-o< ](*,) ](*,) ](*,)

I used the XP disk to then use that section for fixing an install (not the recovery console), but all that did was basically reinstall everything from the looks of it, but the booting is still two choices with one not working and the other freezing.

Now I have the second HD with 5 partitions though.  Hopefully the other one didn't erase everything on me and I will some day be able to get into it somehow to at least copy some stuff.

I am gonna go have a few beers I think and maybe be back in a while.

---

### Post by Support the 2nd on 2007-03-07
> **Malac said:**
> You're Welcome.

In Partition Editor highlight each partition and right-click on it.
Choose Delete from the menu (you may have to unmount it first) and when finished marking the partitions for deletion click Apply on the Edit menu.
To be honest you could just do any resizing at this stage and choose to just assign the partitions you already have during Ubuntu Install and remember to choose /dev/ of the 200GB Hard Disk Two to install GRUB onto.

If you are more comfortable setting up partitions and formatting from within Windows do it from there but leave the proposed Ubuntu ones un-formatted.

Your partitions should look something like this:
/dev/xdx1     Ubuntu Root               mounted to  /
/dev/xdx2     Windows Backup       you can mount this later.
/dev/xdx3     Fat32 Sharing Area    mounted to /media/<whatever-you-want>
/dev/xdx4     linux-swap                 mounted to /swap

If you want to let me know of the proposed sizes you want for the partitions, I could block up some screenshots of what the install steps should look like.

Its a 200 gig drive, so about 189 available.

I was thinking 80 for a back up section, 2.5 for theroot, 2 for the swap, 60 for media/os/personal files/whatever linux calls it, and then the rest as whatever....maybe another XP area.

I think I lost everything on XP.  I am basically gonna instill Ubuntu then deal with my botched XP disk later.

---

### Post by Malac on 2007-03-07
> **Support the 2nd said:**
> Its a 200 gig drive, so about 189 available.

I was thinking 80 for a back up section, 2.5 for theroot, 2 for the swap, 60 for media/os/personal files/whatever linux calls it, and then the rest as whatever....maybe another XP area.

I think I lost everything on XP.  I am basically gonna instill Ubuntu then deal with my botched XP disk later.
Okay, you may be able to save the original XP install if you repeat the previous Repair Install from the XP CD (not the Recovery Console one).
After the license agreement it asks you which XP installation you wish to repair.
Choose your original XP and proceed with that one.
You will have to run Windows Update and you will lose any "customisation" you may have done to XP but all your data and programs should still be there.
I have done this before and the only programs that didn't seem to like it was some Norton Stuff which needed a re-install and PC-cillin AV which needed a re-install too. Other than those two my data and other programs worked as before and it was an easy job to re-do my customisations.

---

### Post by Support the 2nd on 2007-03-07
> **Malac said:**
> Okay, you may be able to save the original XP install if you repeat the previous Repair Install from the XP CD (not the Recovery Console one).
After the license agreement it asks you which XP installation you wish to repair.
Choose your original XP and proceed with that one.
You will have to run Windows Update and you will lose any "customisation" you may have done to XP but all your data and programs should still be there.
I have done this before and the only programs that didn't seem to like it was some Norton Stuff which needed a re-install and PC-cillin AV which needed a re-install too. Other than those two my data and other programs worked as before and it was an easy job to re-do my customisations.


I ran the Repair Install part.  I guess I could run it again.  But when the computer would boot it would give me two of the same choice to boot, and the one that worked would only take me to the "starting Windows now..." screen.  Then it just froze there.

I am running Ubuntu off the second HD right now.  I never got an option on where to install GRUB, or the /dev/ or whatever that was.  So when I restarted it booted to Ubuntu.  I partitioned 3 seconds.  I left the 80gig partition from the xp deal on there, so there are 4 things now I guess plus a chunk of blank.

This whole Linux thing is pissing me off to no end.  I can't even figure out how to install Thunderbird.  This was gonna be one thing to be a second OS, now that its all I have I don't like it.

---

### Post by Malac on 2007-03-08
> **Support the 2nd said:**
> I ran the Repair Install part.  I guess I could run it again.  But when the computer would boot it would give me two of the same choice to boot, and the one that worked would only take me to the "starting Windows now..." screen.  Then it just froze there.

I am running Ubuntu off the second HD right now.  I never got an option on where to install GRUB, or the /dev/ or whatever that was.  So when I restarted it booted to Ubuntu.  I partitioned 3 seconds.  I left the 80gig partition from the xp deal on there, so there are 4 things now I guess plus a chunk of blank.

This whole Linux thing is pissing me off to no end.  I can't even figure out how to install Thunderbird.  This was gonna be one thing to be a second OS, now that its all I have I don't like it.
I admit if you've only used Windows before Linux takes a bit of getting used to but the people here on the forums try to help when they can.
To install stuff just go to [System->Administration->Synaptic Package Manager]
This will list all the packages available to install, thunderbird is in there as mozilla-thunderbird I think.
You can search from within Synaptic for thunderbird and it should find that.
You may need to enable repositories. To do this:
From inside Synaptic go to Settings->Repositories and you will see a window like this:[ATTACH]26884[/ATTACH]
I'd recommend ticking all but the Source checkbox and un-check the CD if it's in there.

I would try the repair install again from the XP CD from scratch as this should sort out your XP problem.

---

### Post by Support the 2nd on 2007-03-08
Thanks.  Mine looked a bit different because I installed 6.06 since it was the maintained one.

I still don't quit grasp installing stuff.  I just see 20 different thunderbird things, none really rin a bell as installers.  But how do I use Firefox 2.0?  I DL'd it, and click on everything inside the package, and one of them opened 2.0 on me.  But I don't see it in that Synaptic thing.

---

### Post by Malac on 2007-03-08
> **Support the 2nd said:**
> Thanks.  Mine looked a bit different because I installed 6.06 since it was the maintained one.

I still don't quit grasp installing stuff.  I just see 20 different thunderbird things, none really rin a bell as installers.  But how do I use Firefox 2.0?  I DL'd it, and click on everything inside the package, and one of them opened 2.0 on me.  But I don't see it in that Synaptic thing.

Synaptic is a "frontend" to a database of available applications held on various servers. They are in the .deb (Debian) format which means they are easy to install and should comply to certain standards such as where the "executable" file is placed and where the menu item is placed etc.
The mozilla-firefox in Synaptic (6.06 Dapper version) is I think 1.5 Max.
You won't see other programs installed by any other method in Synaptic except those installed using GDebi, apt-get or aptitude.

Here's a guide to installing Firefox. I haven't checked it out so sorry if it is not what you are after.
[http://www.ubuntuforums.org/showthread.php?t=330386](http://www.ubuntuforums.org/showthread.php?t=330386)
If it isn't try searching the forums for "install firefox"

---

### Post by Support the 2nd on 2007-03-08
Thanks for the link, I will not be installing it right now though.  It looks a little confusing so I think I need to install something else first few times.  As it stands, the Firefox I am using is my only lifeline to figuring out what I just jumped into.  :)  If I screw it up, I can't ask questions here.

---

