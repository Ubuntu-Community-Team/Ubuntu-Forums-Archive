---
title: "HowTo: Remove Ubuntu (&amp; Restore Windows)"
date: 2007-07-24
forum: Tutorials
---

### Post by anewguy on 2007-07-24
Okay, I know some people are going to have a cow because I'm posting this.  But the truth is, there are a lot of people trying Ubuntu now since it has gotten more press.  If you search the forums, you will notice there are people (A) looking to remove Ubuntu and go back to just Windows, and (B) people who have attempted to remove Ubuntu for just Windows only to blame Ubuntu when Windows doesn't boot.  It's a fact of life that people are going try this out and want to delete it, so why not give them a way to do it that is fairly easy and will hopefully leave them with a good feeling, instead of getting mad at Ubuntu because the partitions needed by grub are gone?

So......for all of you who have a dual-boot system and are looking to remove Ubuntu for now, here are some tips.    NEVER NEVER NEVER just remove the Ubuntu partitions - you won't be able to boot Windows because the information pointed to by your master boot record will be gone.  Instead, follow these easy steps:

(1) Boot you Windows installation
(2) Click on this link [[COLOR="Red"]Get Mbrfix[/COLOR]]("http://www.download.com/MbrFix/3000-2094_4-10485991.html?tag=lst-0-1")
(3) Download the program, unzip it and copy it to your root folder (I'll assume c:\)
(4) Open up the command prompt in Windows by going to start/accessories/command prompt
(5) Type:
          [COLOR="Red"]cd \[/COLOR][COLOR="Black"]     and press "Enter"[/COLOR]
         [COLOR="Red"]mbrfix /drive 0 fixmbr /yes[/COLOR][COLOR="Black"]   and press "Enter"[/COLOR]

*PLEASE NOTE*  The above assumes your boot device is device 0 - if you are not sure on this please post for help.

(6) Close the command prompt window


*PLEASE NOTE*  The following assumes you want to get rid of your Ubuntu partitions and resize you Windows partition(s) to take up that space.  If you do not wish to do so, you can stop now.

(7) Put your Ubuntu LiveCD back in the CD drive and reboot your PC so the the Ubuntu desktop comes up
[noparse](8)[/noparse] On the Ubuntu desktop, look at the top menu bar and go to applications/accessories/terminal
(9) When the terminal Window comes up type:
         [COLOR="Red"]sudo gparted[/COLOR][COLOR="Black"]   and press "Enter"[/COLOR]

     This brings up the disk manager.  You want to:

        (a) delete all non-Windows partitions
        (b) resize your Windows partition to be larger (optional - you may want to leave this alone so you can 
             come back and try Ubuntu again!:) )

(10) When you have finished deleting the Ubuntu partitions, just restart your PC, removing the CD from the 
       drive before it boots again.

If everything went correctly, your PC should just automatically boot Windows.  Note that on the first boot of Windows after you have changed the disk (especially if you resized the Windows partition), Windows may run a chkdsk - this is normal and should be ok.

[COLOR="Red"]If you have already deleted you Linux partitions and are getting grub errors, please try this as suggested by this user (thanks for the neat addition!!)[/COLOR]

 Bothered  
A Carafe of Ubuntu
   Join Date: Jun 2007
Location: United Kingdom
Beans: 136
Ubuntu 7.04 Feisty Fawn User
Windows User 

 
Re: HowTo: Remove Ubuntu (& Restore Windows) 

--------------------------------------------------------------------------------

If you delete the ubuntu partitions without running mbrfix then you can use the ubuntu LiveCD to restore the master boot record by:

1. Booting from the ubuntu LiveCD
2. Enabling universe repositories - launch System->Administation->Software Sources and check the "Community maintained Open Source software (universe)"
3. Installing the "ms-sys" package - click Applications->Accessories->Terminal and type "sudo apt-get update" and then "sudo apt-get install ms-sys".
4. Finally restore the Windows master boot record by entering the command "ms-sys -w /dev/[drive]", where [drive] is the hard disk whose Windows master boot record you want to restore. You can find out which this is by launching gparted (System->Administration->GNOME Partition Editor) and cycling through the available drives until you find your Windows partition 

-    -     -     -     -

Hope this helps, and please let me know if anyone finds any errors.  Also, for anyone using this post, "we" really hope you will come back to Ubuntu someday!  Linux, and Ubuntu, will be waiting!:)

============================

Trouble shooting:

If, after following this guide, you can not boot to Windows you may need to boot a live CD and manually delete the Ubuntu partition (making it unpartitioned space, adding it to the Windows partition, or formatting it to FAT/NTFS).  Additionally you need to be sure the MBR is set for Windows.  You will need to search the forums for more help on that.  In addition, the following Microsoft articles may be of help:


[http://support.microsoft.com/kb/247804](http://support.microsoft.com/kb/247804)

[http://support.microsoft.com/kb/314458](http://support.microsoft.com/kb/314458)

===========================
(Thanks bodhi.zazen!!!)

---

### Post by Rocket2DMn on 2007-07-24
You just gotta make sure you're using the right drive, not everybody is on drive 0.

---

### Post by andnobodyslept on 2007-07-24
Good idea, really usefull for those who forgot what the Live CD is for; as well as for those who jumped into the deep end of the pool and don't want to take the time to learn how to swim. Either way helping them leave with the feeling that the forums are helpful is a great way to bring them back.

---

### Post by anewguy on 2007-07-24
You are right, I forgot about that!! :) 

EVERYONE - when you run the mbrfix program as above, you need to substitute the "zero" after the "/drive " with the correct drive number for the boot device you want to update.

Thanks, Rocket2DMn for the correction!:)

---

### Post by Seisen on 2007-07-24
You should add this in the tutorial and tips section so it doesn't get lost on here.

---

### Post by Pablopcv on 2007-07-24
It also work for those who want to change from ubuntu to kubutu or so. I think that i'm taking this tutorial to reinstall my ubuntu...

---

### Post by LouisvilleLIP on 2007-07-24
This is a great idea.  Being able to easily remove Ubuntu will help reduce the bitter taste of defeat when new users can't figure something out.  Plus, it would be nice to know how to undo a really dumb decision so that you can restart fresh, if needed.

---

### Post by anewguy on 2007-07-25
.

---

### Post by anewguy on 2007-07-25
bump.  i see the question coming up so I wanted to bump the post up.

---

### Post by confused57 on 2007-07-25
Excellent howto...MbrFix works well for Vista, as well as XP.

Herman has listed other possible ways on his website also:

[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

### Post by acowboydave on 2007-07-26
Wouldn't super grub get you back into windows if you did mess up?

---

### Post by aysiu on 2007-07-26
The real problem, of course, is that Ubuntu gets hyped up too much, and people dive into a dual boot too quickly.

We should encourage people to start slowly:
1. Open source Windows apps
2. Ubuntu live CD
3. Ubuntu live CD
4. Ubuntu live CD
5. Maybe Wubi, if you want to play it safe
6. Maybe VMWare, if you want to play it even more safe
7. Regular dual boot if you want to make some sort of commitment
8. Remove Windows once you realize you don't need it any more

We should try, as much as possible to discourage people from jumping straight to #7.

More details [here](http://ubuntucat.wordpress.com/2007/05/25/a-home-users-successful-migration-strategy-from-windows-to-ubuntu/).

---

### Post by bodhi.zazen on 2007-07-26
> **Pablopcv said:**
> It also work for those who want to change from ubuntu to kubutu or so. I think that i'm taking this tutorial to reinstall my ubuntu...

Well, it this is what you are wanting to do :

[list=number][*]Just be aware you *can* have Ubuntu(gnome)/Kubuntu/Xubuntu all installed at the same time.[*]sudo apt-get kubuntu-desktop #For example ...[*]To remove one of these see here : > Pure gnome: [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)
	Pure KDE: [http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)
	Pure XFCE: [http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)[*]Last, if you just want to change as you suggest, just install one over the top of the other. No need to undo partitioning and/or restore the windows boot/loader[/list]

> **aysiu said:**
> The real problem, of course, is that Ubuntu gets hyped up too much, and people dive into a dual boot too quickly.

We should encourage people to start slowly:
1. Open source Windows apps
2. Ubuntu live CD
3. Ubuntu live CD
4. Ubuntu live CD
5. Maybe Wubi, if you want to play it safe
6. Maybe VMWare, if you want to play it even more safe
7. Regular dual boot if you want to make some sort of commitment
8. Remove Windows once you realize you don't need it any more

We should try, as much as possible to discourage people from jumping straight to #7.

More details [here](http://ubuntucat.wordpress.com/2007/05/25/a-home-users-successful-migration-strategy-from-windows-to-ubuntu/).

All good suggestions. For example Firefox/Thunderbird and Open Office are all available for Windows.

I would also suggest Virtualbox or qemu for virtualization.

DSL is very light but will run on windows without installing anything. 

[ftp://ftp.oss.cc.gatech.edu/pub/linux/distributions/damnsmall/current/dsl-embedded.zip](ftp://ftp.oss.cc.gatech.edu/pub/linux/distributions/damnsmall/current/dsl-embedded.zip)

Download and Extract the zip file, doubble click on the .bat file (you can rus this version in Linux as well).

> **Seisen said:**
> You should add this in the tutorial and tips section so it doesn't get lost on here.

I think moving this thread to the Tips and Tutorials section makes a lot of sense ...

anewguy: You do not need to "bump" this thread. Just link to is in other threads and others will follow ;)

---

### Post by anewguy on 2007-07-29
Thanks, Bohdi - I didn't think about the link thing!  Also, since this was intended as a tutorial for removing Ubuntu and going back to Windows, could we move the follow-on posts about things other than that to another thread?:)  Also - is there a way to edit the thread so that only my 2nd post (it's the edited version submitted for posting in tutorials and tips) shows?

Thanks again!:)

---

### Post by bodhi.zazen on 2007-07-29
> **anewguy said:**
> Thanks, Bohdi - I didn't think about the link thing!  Also, since this was intended as a tutorial for removing Ubuntu and going back to Windows, could we move the follow-on posts about things other than that to another thread?:)  Also - is there a way to edit the thread so that only my 2nd post (it's the edited version submitted for posting in tutorials and tips) shows?

Thanks again!:)

1. You can edit the thread for yourself (see the "EDIT" button at the bottom of your posts ? )

2. When you do you can "fix" you lists by either turning off smiles (Click the "Disable Smiles in text" box just below the main text box (In additional options).

OR use the list tag ...

[.list=number][*]Item 1
[*]Item2

...
[*]Last item[/list]


just remove the first "." from the first [**.**list]

See this link for information : [http://ubuntuforums.org/misc.php?do=bbcode](http://ubuntuforums.org/misc.php?do=bbcode)


3. As far as moving unrelated posts, I am not sure this is necessary ... nature of the forums that this will happen. It would take a lot of effort (and likely be fairly unpopular) to do this kind of thing (although I know how you feel ...)

EDIT: See I added this edit to my origional post ;)

At any rate, better to teach you how to maintain you own threads and posts then do the maintainence  for you (he he he .... I have my own threads to maintain ... )

---

### Post by badApples on 2007-08-01
What about when you have deleted the Ubuntu partition and can no longer get on to XP? :)

---

### Post by darksong on 2007-08-01
nice guide:popcorn:

---

### Post by Sayers on 2007-08-01
Yes, good tutorial, except my hard drive is on HDC :)

---

### Post by mshale on 2007-08-01
Hey, this guide is awesome, but i have a slightly difficult problem... i didn't find this thread before i goofed it up... here is a link to the other post:

[Description of my problem]("http://ubuntuforums.org/showthread.php?t=515274")

Thanks for all of your help!

---

### Post by thepopasmurf on 2007-08-09
how do you know which drive windows is in?

---

### Post by bodhi.zazen on 2007-08-09
> **thepopasmurf said:**
> how do you know which drive windows is in?

With the live CD start gparted or in a terminal enter this command :

```
sudo fdisk -l
```

The Windows partition is usually NTFS, although it may be FAT ...

For general partitioning info see here : [http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

---

### Post by samkourbeis on 2007-08-22
How do I know which partition drives are which number?
I have a boot partition which is 2 gig, a windows partition which is 60 gig, a linux swap partition which is 100 meg and a linux boot partition which is 10 gig. Does the numbering start at zero and work its way up through the drives in the order they are?
Thanks.

---

### Post by bodhi.zazen on 2007-08-22
> **samkourbeis said:**
> How do I know which partition drives are which number?
I have a boot partition which is 2 gig, a windows partition which is 60 gig, a linux swap partition which is 100 meg and a linux boot partition which is 10 gig. Does the numbering start at zero and work its way up through the drives in the order they are?
Thanks.

See if this link helps : [http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

---

### Post by GeneralHooHa on 2007-08-22
> **aysiu said:**
> 

We should encourage people to start slowly:
1. Open source Windows apps
2. Ubuntu live CD
3. Ubuntu live CD
4. Ubuntu live CD
5. Maybe Wubi, if you want to play it safe
6. Maybe VMWare, if you want to play it even more safe
7. Regular dual boot if you want to make some sort of commitment
8. Remove Windows once you realize you don't need it any more
I actually jumped straight to number 8 (on accident). Of course, now I love Ubuntu, but I really wish I became familiar with it before trying to dual boot (and failing).

---

### Post by aysiu on 2007-08-22
> **GeneralHooHa said:**
> I actually jumped straight to number 8 (on accident). Of course, now I love Ubuntu, but I really wish I became familiar with it before trying to dual boot (and failing).
That *can* be done, but I've seen too many "Oh, no! I want Windows back" threads that I think your experience should be the minority migration experience, not the standard.

---

### Post by Duck2006 on 2007-08-26
Nice post

---

### Post by jp_coll2003 on 2007-09-07
Hi all

Im a very newbie to Linux/Ubuntu.

I have Vista on one internal hard drive and Ubuntu on an external usb connected hard drive. Unfortunately I have Grub which I would love to delete so I can get rid of the external hard drive and just install Ubuntu on the internal one. Is this as simple as I think its going to be or should I expect any heart aches ?

Your comments would be appreciated.

John

---

### Post by juanbretti on 2007-09-07
Hello, I have a Windows Vista Home Premium and a** WinRE partition**: Do I have to mantain the "WinRE partition"?

Also I have a 1MiB partition from the manufacture: Toshiba that is "unallocated".

Should I keep both partitions for reinstalling Windows Vista?

Does de "Windows Vista Recovery tool (that is on the DVD)" needs the WinRE partition?

Thanks!

---

### Post by juanbretti on 2007-09-07
Another question: Do I need to **download** the MBR image to install a "clean and fresh install" of** Windows Vista**?

---

### Post by Stanley Krute on 2007-09-12
Great post.

I tried Ubuntu 6 a year ago, and gave up due to an inability to get wired andor wireless networking to Just Work.

I just gave Ubuntu 7 a spin via CD. I was happy to see that both wired and wireless networking Just Work.

So: I deleted the existing Linux partition on my hard drive, and did an install of 7.

> **anewguy said:**
>  for anyone using this post, "we" really hope you will come back to Ubuntu someday!  Linux, and Ubuntu, will be waiting!:)

This post made my coming back trivial.

Thanks to all the Ubuntans for getting that networking stuff working.

Looking forward to Ubuntu 8.

-- stan

---

### Post by EmperorMoo on 2007-09-13
Excellent guide, thank you very much.

I am a totally newbie to Ubuntu, and having this handy guide to get rid of it (I installed Ubuntu on a work laptop with only 10GB HDD space to experiment with it) was very useful and completely straight forward.

---

### Post by Bothered on 2007-09-13
If you delete the ubuntu partitions without running mbrfix then you can use the ubuntu LiveCD to restore the master boot record by:

1. Booting from the ubuntu LiveCD
2. Enabling universe repositories - launch System->Administation->Software Sources and check the "Community maintained Open Source software (universe)"
3. Installing the "ms-sys" package - click Applications->Accessories->Terminal and type "sudo apt-get update" and then "sudo apt-get install ms-sys".
4. Finally restore the Windows master boot record by entering the command "ms-sys -w /dev/[drive]", where [drive] is the hard disk whose Windows master boot record you want to restore. You can find out which this is by launching gparted (System->Administration->GNOME Partition Editor) and cycling through the available drives until you find your Windows partition.

---

### Post by bodhi.zazen on 2007-09-13
> **Bothered said:**
> If you delete the ubuntu partitions without running mbrfix then you can use the ubuntu LiveCD to restore the master boot record by:

1. Booting from the ubuntu LiveCD
2. Enabling universe repositories - launch System->Administation->Software Sources and check the "Community maintained Open Source software (universe)"
3. Installing the "ms-sys" package - click Applications->Accessories->Terminal and type "sudo apt-get update" and then "sudo apt-get install ms-sys".
4. Finally restore the Windows master boot record by entering the command "ms-sys -w /dev/[drive]", where [drive] is the hard disk whose Windows master boot record you want to restore. You can find out which this is by launching gparted (System->Administration->GNOME Partition Editor) and cycling through the available drives until you find your Windows partition.

That is very cool.

FYI you can also do this with knoppix. Boot Knoppix, open a terminal,

```
sudo install-mbr /dev/hda
```

Of course you will need to adjust if you use an alternate disk (/dev/sda1 ...)

You can list your disks with :```
sudo fsdisk -l
```

---

### Post by anewguy on 2007-09-16
> **Bothered said:**
> If you delete the ubuntu partitions without running mbrfix then you can use the ubuntu LiveCD to restore the master boot record by:

1. Booting from the ubuntu LiveCD
2. Enabling universe repositories - launch System->Administation->Software Sources and check the "Community maintained Open Source software (universe)"
3. Installing the "ms-sys" package - click Applications->Accessories->Terminal and type "sudo apt-get update" and then "sudo apt-get install ms-sys".
4. Finally restore the Windows master boot record by entering the command "ms-sys -w /dev/[drive]", where [drive] is the hard disk whose Windows master boot record you want to restore. You can find out which this is by launching gparted (System->Administration->GNOME Partition Editor) and cycling through the available drives until you find your Windows partition.


Thanks for a great addition!!!  I have copied your entire message and placed it the original post so people might find it there.  

Again, thanks for a GREAT addition!:)

---

### Post by krakas on 2007-10-20
As i cannot get my wireless to work in ubuntu, i'm dropping it in order to get more space. 

> *PLEASE NOTE* The above assumes your boot device is device 0 - if you are not sure on this please post for help.

How do i find out about this? I have searched through this thread and the forum generally, but cannot find it out. My c: is called hda1 in Gparted, so is the number 1? 

I have done the procedure outlined above, and now i'm not able to boot, only get "boot error 22". Also, the fix recommended by bothered do not work, as it says "Unable to open dev/hda1" after step 4. 

So i'm considering reinstalling ubuntu, booting to windows, and getting the mbrfix drive number right, then doing the whole process again...

Oh, and the microsoft articles didn't solve it for me either.

Anyone?

---

### Post by Duck2006 on 2007-10-20
> **Bothered said:**
> If you delete the ubuntu partitions without running mbrfix then you can use the ubuntu LiveCD to restore the master boot record by:

1. Booting from the ubuntu LiveCD
2. Enabling universe repositories - launch System->Administation->Software Sources and check the "Community maintained Open Source software (universe)"
3. Installing the "ms-sys" package - click Applications->Accessories->Terminal and type "sudo apt-get update" and then "sudo apt-get install ms-sys".
4. Finally restore the Windows master boot record by entering the command "ms-sys -w /dev/[drive]", where [drive] is the hard disk whose Windows master boot record you want to restore. You can find out which this is by launching gparted (System->Administration->GNOME Partition Editor) and cycling through the available drives until you find your Windows partition.

Thanks the more you learn the better linux becomes.

---

### Post by LifeIsShort on 2007-10-21
I think I understand most of this thread, and I do not think my problem can be resolved following these methods.

What I am looking to do is go from a full Ubuntu install, to a dual boot install on a single HDD  unfortunately I formatted the entire drive to ext3.

now I would like to have a WinXP/Ubuntu dual doot on a single HDD.

anybody know where there is an existing thread, or can post a fix/resolution here?

any help would be appreciated.

---

### Post by bodhi.zazen on 2007-10-21
> **LifeIsShort said:**
> I think I understand most of this thread, and I do not think my problem can be resolved following these methods.

What I am looking to do is go from a full Ubuntu install, to a dual boot install on a single HDD  unfortunately I formatted the entire drive to ext3.

now I would like to have a WinXP/Ubuntu dual doot on a single HDD.

anybody know where there is an existing thread, or can post a fix/resolution here?

any help would be appreciated.

Boot a live CD

1. Run gparted, resize you Ubuntu partition, and make a PRIMARY partition for windows.

2. Install windows.

3. Restore grub. 

[uwiki]RecoveringUbuntuAfterInstallingWindows[/uwiki]

Here is a how-to : 

[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)

---

### Post by LifeIsShort on 2007-10-23
Thanks for the links and the assistance!

---

### Post by JDK721 on 2007-10-29
When I do sudo gparted and bring up all the partitions in Ubuntu it doesn't let me delete them or anything.  It doesn't let me do anything to them.  Any help?

---

### Post by rsambuca on 2007-10-29
You can't work on partitions that are mounted (in use).  If you want to modify your Ubuntu partition, you will need to use the Ubuntu liveCD, or use the [gParted liveCD]("http://gparted.sourceforge.net/").

---

### Post by JDK721 on 2007-10-29
I have my LiveCD, so how do I delete my partitions with it?

I want to have just Windows XP left.  I want to get rid of Ubuntu.

I don't get how to remove the partitions if you can't do it while they're mounted.. I followed the instructions and it's not working like that.

---

### Post by traderpats on 2007-10-30
An option that we used was to install Gutsy to an external usb hard drive along with the Grub which was installed at /dev/sda.  The other internal drives are eide.   We didn't want to take any chance, (even though all data was backed up), with the xp MBR.  The only glitch was for some reason I had to enable _legacy_ usb support in the bios even though usb1&usb2 support was already enabled.  (?)

When we want to learn the ins and outs of Linux, (really good stuff btw), or tweak the system,(in preparation of a full move to Linux),  we turn on the external usb drive, then the computer, and boot right into Gutsy.  When we have to boot into xp we leave the external drive off when booting.  NOTE: The external drive can be turned on after the boot into xp if you also have a ntfs partition on the external drive that you want to access.

Anyway with this method one can simply boot into Windows and format the external drive for other uses if they feel the need.

---

### Post by diogenes2 on 2007-12-09
Hi people,
Actually, I decided to start REAL clean - new 500G disk an' all.
(Having had a prior Linux attempt couple of years ago wipe my entire Hard drive...)
I want to make a Ubuntu and/or Kubuntu total Drive and do what I did under Windows: 
I used VMWare to run Linux. I want to reverse it.
----------------------------------------
I want to use a Virtual Drive (suggestions welcome) under Linux to run Windows for the only 2 programs I can't replace in Linux. One of which needs to go out on the Net. 
 
In trying to get this under way, I have a GRUB problem (apparently common) but I don't have Windows on the disk unlike the solutions seen so far.

I simply want to start over and get rid of GRUB - it won't let any install boot. Gives error message "Grub loading Stage1 5 Read error".

I have tried deleting partitions, unmounting partitions -even used a Severe deletion program that came with a SUSE103 install disk.

How can I reformat the whole drive and get rid of that Grub once and for all? AND - What is the alternative option?

Any advice more than welcome especially re a Virtual Machine to replace the very expensive - but good VMWare for Windoze?

---

### Post by Steeltwist on 2007-12-21
Stupid question but how do you find out if your boot device is 0 or whatever?

---

### Post by Geohevy on 2008-02-18
Err, say I want to delete the Ubuntu partitions and make the Windows partition larger, what should I do if  my computer (an HP dv6500 laptop) cannot use the Live CD, and cannot start XServer to go to the desktop?

I can run Ubuntu in text mode; would the sudo gparted command work from there? :confused:

And as I go, I wanna say that it's been fun. This forum is by far the most helpful I have ever seen.

---

### Post by Duck2006 on 2008-02-18
Have you tired a live cd of gparted?
It is not the ubuntu live cd.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by Bazirker on 2008-02-19
I've got a triple boot system: XP, Ubuntu i386, and Ubuntu in 64-bit.  I decided to go with 64-bit and want to wipe the 32-bit.  Will this method work?  Could I simply use gparted to clear out the i386 partition and then reinstall grub (as per [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)) to set things back up?

---

### Post by bodhi.zazen on 2008-02-20
> **Bazirker said:**
> I've got a triple boot system: XP, Ubuntu i386, and Ubuntu in 64-bit.  I decided to go with 64-bit and want to wipe the 32-bit.  Will this method work?  Could I simply use gparted to clear out the i386 partition and then reinstall grub (as per [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)) to set things back up?

That should work just fine. Start a new thread if you have problems (you may need to edit /etc/fstab).

---

### Post by Bazirker on 2008-02-23
After using gparted to remove the i386 install and resize the space to the other Ubuntu install, I didn't need to reinstall grub, although I did have to comment out the UUID for the partition I removed in /etc/fstab.

---

### Post by Tunguska on 2008-02-28
> **anewguy said:**
> *PLEASE NOTE*  The above assumes your boot device is device 0 - if you are not sure on this please post for help.


sooo, how do I figure out if my boot device is device 0 ?

also, does Mbrfix work for Windows Vista? edit: apparently it does

edit: nevermind, I found it. It was indeed drive 0, but checking never hurts. If anyone else wants to check it, but doesn't know how: In Windows go to control panel - system management - computer management - disk management. There you get an overview of your hard drive and how it's partitioned. At least that's what I think I'm looking at :)

---

### Post by Cibola on 2008-04-06
Thanks so far. Got to rebooting Ubuntu, went to Applications, Accessories, Terminal but when I type in "sudo gparted" I get --command not found. Any suggestions??

---

### Post by bodhi.zazen on 2008-04-06
> **Cibola said:**
> Thanks so far. Got to rebooting Ubuntu, went to Applications, Accessories, Terminal but when I type in "sudo gparted" I get --command not found. Any suggestions??

gparted is on the live, desktop CD. You can install it to hard drive, but you will need to boot to a live CD to manage your partitions anyways ...

Once you boot to the live Ubuntu CD, make sure the hard drive, including your windows , ubuntu, swap, and any other partitions are unmounted (you can un mount them from gparted). Then proceed ...

---

### Post by Cibola on 2008-04-07
Thanks--I am now in the gparted window but a few of the partitions are locked and I cant remove them . Also, the partition holding Windows says "unable to read the contents of this filesystem. Because of this some operations may be unavailable". This means I cant resize it. 
Any help would be appreciated.

---

### Post by Cibola on 2008-04-07
Also, the partitions thab are locked cant be unmounted.

---

### Post by bodhi.zazen on 2008-04-07
Usually the locks are due to the partitions being mounted.

Usually the problems is the wasp partition.

```
sudo swapoff /dev/sdxy
```

Change /dev/sdxy to your swap ? /dev/sda5

If that fails, try the gparted live CD

Download: [Download Gparted](http://easynews.dl.sourceforge.net/sourceforge/gparted/gparted-livecd-0.3.4-8.iso)

---

### Post by Cibola on 2008-04-07
How do I know what my swap is???

---

### Post by Rocket2DMn on 2008-04-07
From the output of
```
sudo fdisk -l
```
You will see the partition(s) with the System called "Linux swap / Solaris".  You should also be able to see it in GParted with Filesystem "linux-swap" and it has no mount point.

---

### Post by bodhi.zazen on 2008-04-07
gparted lists your partitions and will identify which one is swap.

Alternate is :```
sudo fdisk -l
```

---

### Post by Shadius on 2008-04-30
This is an awesome guide!!!!! The Ubuntu Community truly helps its users.

---

### Post by thisiam on 2008-04-30
Ok, so was going to do this to see what it does, but instead of downloading that file i was going to boot windows recovery and fixmbr->restart and delete the linux partition.
would this work aswell or am i going to mess up the whole drive and have to reinstall?

---

### Post by Fenris_rising on 2008-04-30
ive just cocked up a dual install, due to impatiance on my part, but its worked better than i hoped. i lost XP partition and hardy heron now has an 80gb drive all to its self, works lovely too. still i am downloading the gparted live disk as it may be a useful tool. great tut even a newb like me understands it.

Fenris

---

### Post by Duck2006 on 2008-04-30
> **Fenris_rising said:**
> ive just cocked up a dual install, due to impatiance on my part, but its worked better than i hoped. i lost XP partition and hardy heron now has an 80gb drive all to its self, works lovely too. still i am downloading the gparted live disk as it may be a useful tool. great tut even a newb like me understands it.

Fenris

Try parted magic.

[http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php)

---

### Post by Shadius on 2008-04-30
how do you delete the ubuntu partitions? Gparted is only seeing one partition. It just says "unallocated".

---

### Post by Shadius on 2008-04-30
> **Tunguska said:**
> sooo, how do I figure out if my boot device is device 0 ?

also, does Mbrfix work for Windows Vista? edit: apparently it does

edit: nevermind, I found it. It was indeed drive 0, but checking never hurts. If anyone else wants to check it, but doesn't know how: In Windows go to control panel - system management - computer management - disk management. There you get an overview of your hard drive and how it's partitioned. At least that's what I think I'm looking at :)
Is this for XP or Vista?

---

### Post by Shadius on 2008-04-30
Umm...getting error in command prompt. Am I supposed to execute Fixmbr after downloading it?

---

### Post by Shadius on 2008-04-30
> **anewguy said:**
> Okay, I know some people are going to have a cow because I'm posting this.  But the truth is, there are a lot of people trying Ubuntu now since it has gotten more press.  If you search the forums, you will notice there are people (A) looking to remove Ubuntu and go back to just Windows, and (B) people who have attempted to remove Ubuntu for just Windows only to blame Ubuntu when Windows doesn't boot.  It's a fact of life that people are going try this out and want to delete it, so why not give them a way to do it that is fairly easy and will hopefully leave them with a good feeling, instead of getting mad at Ubuntu because the partitions needed by grub are gone?

So......for all of you who have a dual-boot system and are looking to remove Ubuntu for now, here are some tips.    NEVER NEVER NEVER just remove the Ubuntu partitions - you won't be able to boot Windows because the information pointed to by your master boot record will be gone.  Instead, follow these easy steps:

(1) Boot you Windows installation
(2) Click on this link [[COLOR="Red"]Get Mbrfix[/COLOR]]("http://www.download.com/MbrFix/3000-2094_4-10485991.html?tag=lst-0-1")
(3) Download the program, unzip it and copy it to your root folder (I'll assume c:\)
(4) Open up the command prompt in Windows by going to start/accessories/command prompt
(5) Type:
          [COLOR="Red"]cd \[/COLOR][COLOR="Black"]     and press "Enter"[/COLOR]
         [COLOR="Red"]mbrfix /drive 0 fixmbr /yes[/COLOR][COLOR="Black"]   and press "Enter"[/COLOR]

*PLEASE NOTE*  The above assumes your boot device is device 0 - if you are not sure on this please post for help.

(6) Close the command prompt window


*PLEASE NOTE*  The following assumes you want to get rid of your Ubuntu partitions and resize you Windows partition(s) to take up that space.  If you do not wish to do so, you can stop now.

(7) Put your Ubuntu LiveCD back in the CD drive and reboot your PC so the the Ubuntu desktop comes up
[noparse](8)[/noparse] On the Ubuntu desktop, look at the top menu bar and go to applications/accessories/terminal
(9) When the terminal Window comes up type:
         [COLOR="Red"]sudo gparted[/COLOR][COLOR="Black"]   and press "Enter"[/COLOR]

     This brings up the disk manager.  You want to:

        (a) delete all non-Windows partitions
        (b) resize your Windows partition to be larger (optional - you may want to leave this alone so you can 
             come back and try Ubuntu again!:) )

(10) When you have finished deleting the Ubuntu partitions, just restart your PC, removing the CD from the 
       drive before it boots again.

If everything went correctly, your PC should just automatically boot Windows.  Note that on the first boot of Windows after you have changed the disk (especially if you resized the Windows partition), Windows may run a chkdsk - this is normal and should be ok.

[COLOR="Red"]If you have already deleted you Linux partitions and are getting grub errors, please try this as suggested by this user (thanks for the neat addition!!)[/COLOR]

 Bothered  
A Carafe of Ubuntu
   Join Date: Jun 2007
Location: United Kingdom
Beans: 136
Ubuntu 7.04 Feisty Fawn User
Windows User 

 
Re: HowTo: Remove Ubuntu (& Restore Windows) 

--------------------------------------------------------------------------------

If you delete the ubuntu partitions without running mbrfix then you can use the ubuntu LiveCD to restore the master boot record by:

1. Booting from the ubuntu LiveCD
2. Enabling universe repositories - launch System->Administation->Software Sources and check the "Community maintained Open Source software (universe)"
3. Installing the "ms-sys" package - click Applications->Accessories->Terminal and type "sudo apt-get update" and then "sudo apt-get install ms-sys".
4. Finally restore the Windows master boot record by entering the command "ms-sys -w /dev/[drive]", where [drive] is the hard disk whose Windows master boot record you want to restore. You can find out which this is by launching gparted (System->Administration->GNOME Partition Editor) and cycling through the available drives until you find your Windows partition 

-    -     -     -     -

Hope this helps, and please let me know if anyone finds any errors.  Also, for anyone using this post, "we" really hope you will come back to Ubuntu someday!  Linux, and Ubuntu, will be waiting!:)

============================

Trouble shooting:

If, after following this guide, you can not boot to Windows you may need to boot a live CD and manually delete the Ubuntu partition (making it unpartitioned space, adding it to the Windows partition, or formatting it to FAT/NTFS).  Additionally you need to be sure the MBR is set for Windows.  You will need to search the forums for more help on that.  In addition, the following Microsoft articles may be of help:


[http://support.microsoft.com/kb/247804](http://support.microsoft.com/kb/247804)

[http://support.microsoft.com/kb/314458](http://support.microsoft.com/kb/314458)

===========================
(Thanks bodhi.zazen!!!)
Confused. Am I supposed to run Fixmbr after downloading it? Command prompt doesn't recognize "fixmbr". Help?

---

### Post by Shadius on 2008-04-30
> **anewguy said:**
> Okay, I know some people are going to have a cow because I'm posting this.  But the truth is, there are a lot of people trying Ubuntu now since it has gotten more press.  If you search the forums, you will notice there are people (A) looking to remove Ubuntu and go back to just Windows, and (B) people who have attempted to remove Ubuntu for just Windows only to blame Ubuntu when Windows doesn't boot.  It's a fact of life that people are going try this out and want to delete it, so why not give them a way to do it that is fairly easy and will hopefully leave them with a good feeling, instead of getting mad at Ubuntu because the partitions needed by grub are gone?

So......for all of you who have a dual-boot system and are looking to remove Ubuntu for now, here are some tips.    NEVER NEVER NEVER just remove the Ubuntu partitions - you won't be able to boot Windows because the information pointed to by your master boot record will be gone.  Instead, follow these easy steps:

(1) Boot you Windows installation
(2) Click on this link [[COLOR="Red"]Get Mbrfix[/COLOR]]("http://www.download.com/MbrFix/3000-2094_4-10485991.html?tag=lst-0-1")
(3) Download the program, unzip it and copy it to your root folder (I'll assume c:\)
(4) Open up the command prompt in Windows by going to start/accessories/command prompt
(5) Type:
          [COLOR="Red"]cd \[/COLOR][COLOR="Black"]     and press "Enter"[/COLOR]
         [COLOR="Red"]mbrfix /drive 0 fixmbr /yes[/COLOR][COLOR="Black"]   and press "Enter"[/COLOR]

*PLEASE NOTE*  The above assumes your boot device is device 0 - if you are not sure on this please post for help.

(6) Close the command prompt window


*PLEASE NOTE*  The following assumes you want to get rid of your Ubuntu partitions and resize you Windows partition(s) to take up that space.  If you do not wish to do so, you can stop now.

(7) Put your Ubuntu LiveCD back in the CD drive and reboot your PC so the the Ubuntu desktop comes up
[noparse](8)[/noparse] On the Ubuntu desktop, look at the top menu bar and go to applications/accessories/terminal
(9) When the terminal Window comes up type:
         [COLOR="Red"]sudo gparted[/COLOR][COLOR="Black"]   and press "Enter"[/COLOR]

     This brings up the disk manager.  You want to:

        (a) delete all non-Windows partitions
        (b) resize your Windows partition to be larger (optional - you may want to leave this alone so you can 
             come back and try Ubuntu again!:) )

(10) When you have finished deleting the Ubuntu partitions, just restart your PC, removing the CD from the 
       drive before it boots again.

If everything went correctly, your PC should just automatically boot Windows.  Note that on the first boot of Windows after you have changed the disk (especially if you resized the Windows partition), Windows may run a chkdsk - this is normal and should be ok.

[COLOR="Red"]If you have already deleted you Linux partitions and are getting grub errors, please try this as suggested by this user (thanks for the neat addition!!)[/COLOR]

 Bothered  
A Carafe of Ubuntu
   Join Date: Jun 2007
Location: United Kingdom
Beans: 136
Ubuntu 7.04 Feisty Fawn User
Windows User 

 
Re: HowTo: Remove Ubuntu (& Restore Windows) 

--------------------------------------------------------------------------------

If you delete the ubuntu partitions without running mbrfix then you can use the ubuntu LiveCD to restore the master boot record by:

1. Booting from the ubuntu LiveCD
2. Enabling universe repositories - launch System->Administation->Software Sources and check the "Community maintained Open Source software (universe)"
3. Installing the "ms-sys" package - click Applications->Accessories->Terminal and type "sudo apt-get update" and then "sudo apt-get install ms-sys".
4. Finally restore the Windows master boot record by entering the command "ms-sys -w /dev/[drive]", where [drive] is the hard disk whose Windows master boot record you want to restore. You can find out which this is by launching gparted (System->Administration->GNOME Partition Editor) and cycling through the available drives until you find your Windows partition 

-    -     -     -     -

Hope this helps, and please let me know if anyone finds any errors.  Also, for anyone using this post, "we" really hope you will come back to Ubuntu someday!  Linux, and Ubuntu, will be waiting!:)

============================

Trouble shooting:

If, after following this guide, you can not boot to Windows you may need to boot a live CD and manually delete the Ubuntu partition (making it unpartitioned space, adding it to the Windows partition, or formatting it to FAT/NTFS).  Additionally you need to be sure the MBR is set for Windows.  You will need to search the forums for more help on that.  In addition, the following Microsoft articles may be of help:


[http://support.microsoft.com/kb/247804](http://support.microsoft.com/kb/247804)

[http://support.microsoft.com/kb/314458](http://support.microsoft.com/kb/314458)

===========================
(Thanks bodhi.zazen!!!)
Okay, so I did the Fixmbr thing. I did sudo gparted in Ubuntu and I get "Partition-unallocated, Filesystem-unallocated, size 37.27 GiB, and other categories, Used, Unused, Flags are empty. This is the only things that shows. I try reloading devices from Gparted and I get a crash. Help please.

This is what I'm getting in Terminal.

ubuntu@ubuntu:~$ sudo gparted
======================
libparted : 1.7.1
======================
Unable to open /dev/scd1 read-write (Read-only file system).  /dev/scd1 has been opened read-only.
Unable to open /dev/scd1 - unrecognised disk label.
Can't have overlapping partitions.

---

### Post by anewguy on 2008-05-01
> **Shadius said:**
> Okay, so I did the Fixmbr thing. I did sudo gparted in Ubuntu and I get "Partition-unallocated, Filesystem-unallocated, size 37.27 GiB, and other categories, Used, Unused, Flags are empty. This is the only things that shows. I try reloading devices from Gparted and I get a crash. Help please.

This is what I'm getting in Terminal.

ubuntu@ubuntu:~$ sudo gparted
======================
libparted : 1.7.1
======================
Unable to open /dev/scd1 read-write (Read-only file system).  /dev/scd1 has been opened read-only.
Unable to open /dev/scd1 - unrecognised disk label.
Can't have overlapping partitions.

Well, I've got to ask some questions first to try see how you got to where you are and just exactly where you are.

(1) Did you originally have a Windows partition, a Linux swap partition and a Linux "data" partition (probably ext3) on the disk when you started this process?

(2) How big is the disk?

(3) Did you follow the steps in order - did you run fixmbr before you booted the LiveCD, or did you perhaps not run fixmbr, tried the LiveCD, then went back and ran fixmbr?

(4) There are no other partitions showing in the list from gparted?  If not, and if your disk is the size of the partition showing, then I THINK you already have a "clean" disk and will now have to install Windows from scratch.

I'm a little rusty at all this because I haven't used Windows now in a LONG time, and haven't had any need to run gparted off the LiveCD for a longer time.

Please provide those answers, then if I don't get back to you right a way wait a few days or see if someone else answers.  As you noticed, it does no good to include the instructions in your reply.  Also, if you aren't getting an answer, just put the word "bump" in a reply.  A reply, even if a single character, will cause the post to jump to the top of the list.  But don't abuse bump either.  If you don't get an answer in the time frame you need, try creating your own post in the beginner's forum ask for help.  Things like this tutorial I have looked at in a long time.  You kind of write them, check them every once in a while (that might even be months in my case), and forget about them.

:)

---

### Post by Shadius on 2008-05-01
> **anewguy said:**
> Well, I've got to ask some questions first to try see how you got to where you are and just exactly where you are.

(1) Did you originally have a Windows partition, a Linux swap partition and a Linux "data" partition (probably ext3) on the disk when you started this process?

(2) How big is the disk?

(3) Did you follow the steps in order - did you run fixmbr before you booted the LiveCD, or did you perhaps not run fixmbr, tried the LiveCD, then went back and ran fixmbr?

(4) There are no other partitions showing in the list from gparted?  If not, and if your disk is the size of the partition showing, then I THINK you already have a "clean" disk and will now have to install Windows from scratch.

I'm a little rusty at all this because I haven't used Windows now in a LONG time, and haven't had any need to run gparted off the LiveCD for a longer time.

Please provide those answers, then if I don't get back to you right a way wait a few days or see if someone else answers.  As you noticed, it does no good to include the instructions in your reply.  Also, if you aren't getting an answer, just put the word "bump" in a reply.  A reply, even if a single character, will cause the post to jump to the top of the list.  But don't abuse bump either.  If you don't get an answer in the time frame you need, try creating your own post in the beginner's forum ask for help.  Things like this tutorial I have looked at in a long time.  You kind of write them, check them every once in a while (that might even be months in my case), and forget about them.

:)
bump
Answers to your question:
1) Yes, I am dual-booting Windows and Ubuntu. 
2) The disk size is 40 GB.
3) I don't think it's a clean disk. I don't have a Windows XP CD, I just have the recovery CD, and when I try to run that to Restore To Factory Settings, it just reboots.

---

### Post by anewguy on 2008-05-01
I'm starting to wonder if perhaps you have a recovery partition on your hard drive that's taking the extra 2+gb - my old laptop had one and that was about the space it took.  I'm suspecting you already have cleaned your disk, and that your recovery CD doesn't actually install Windows but just resets everything back.  A recovery partition would be used to recover Windows.  What type of PC is this?  Does the manufacturer have any help texts that same something about reloading Windows that you might be able to try?

On my old laptop, I had to make recovery CD's when the system was first brought up and was only allowed to do so once.  When you reboot your PC, does a message come up about booting from a recovery partition?

---

### Post by th00ht on 2008-08-08
What about Vista does it work in the same way?

---

### Post by anewguy on 2008-08-09
I personally I have no experience with Vista (and hope to keep it that way for as long as possible).  However, somewhere earlier in this post I think there was a reply about mbrfix saying it worked for Vista as well.  I cannot tell you if it really works or not.

---

### Post by lukjad on 2008-08-09
Thanks a lot! While I would rather juggle knives than uninstall Ubuntu to install Vista, I keep having people ask me this and I can never give them a good answer. 

BTW is the Thanks feature disabled in the Howto Section or is it just me?

Anyhow, thanks!

---

### Post by macmac666 on 2008-08-13
I am new to ubuntu and want to deinstall because I want to replace the drive it is currently residing on. How do I find out which drive my windows is on (I have 4 drives in the PC)in order to follow the instruction to use mbrfix referred to in your tutorial?
Also, when I type at the command promp, are there any spaces to be typed or is it one continuous line of typing?
mbrfix/drive0fixmbr/yes or ???

---

### Post by Duck2006 on 2008-08-13
> **macmac666 said:**
> I am new to ubuntu and want to deinstall because I want to replace the drive it is currently residing on. How do I find out which drive my windows is on (I have 4 drives in the PC)in order to follow the instruction to use mbrfix referred to in your tutorial?
Also, when I type at the command promp, are there any spaces to be typed or is it one continuous line of typing?
mbrfix/drive0fixmbr/yes or ???

To find witch drive your windoze is on, open the terminal and type

sudo fdisk -l

as for

mbrfix /drive 0 fixmbr /yes

Not sure as to this have not read the tutrorial, i would say to type it as one line.

---

### Post by hellodoggie on 2008-08-13
Thanks

This helped me alot.

> **anewguy said:**
> Okay, I know some people are going to have a cow because I'm posting this.  But the truth is, there are a lot of people trying Ubuntu now since it has gotten more press.  If you search the forums, you will notice there are people (A) looking to remove Ubuntu and go back to just Windows, and (B) people who have attempted to remove Ubuntu for just Windows only to blame Ubuntu when Windows doesn't boot.  It's a fact of life that people are going try this out and want to delete it, so why not give them a way to do it that is fairly easy and will hopefully leave them with a good feeling, instead of getting mad at Ubuntu because the partitions needed by grub are gone?

So......for all of you who have a dual-boot system and are looking to remove Ubuntu for now, here are some tips.    NEVER NEVER NEVER just remove the Ubuntu partitions - you won't be able to boot Windows because the information pointed to by your master boot record will be gone.  Instead, follow these easy steps:

(1) Boot you Windows installation
(2) Click on this link [[COLOR="Red"]Get Mbrfix[/COLOR]]("http://www.download.com/MbrFix/3000-2094_4-10485991.html?tag=lst-0-1")
(3) Download the program, unzip it and copy it to your root folder (I'll assume c:\)
(4) Open up the command prompt in Windows by going to start/accessories/command prompt
(5) Type:
          [COLOR="Red"]cd \[/COLOR][COLOR="Black"]     and press "Enter"[/COLOR]
         [COLOR="Red"]mbrfix /drive 0 fixmbr /yes[/COLOR][COLOR="Black"]   and press "Enter"[/COLOR]

*PLEASE NOTE*  The above assumes your boot device is device 0 - if you are not sure on this please post for help.

(6) Close the command prompt window


*PLEASE NOTE*  The following assumes you want to get rid of your Ubuntu partitions and resize you Windows partition(s) to take up that space.  If you do not wish to do so, you can stop now.

(7) Put your Ubuntu LiveCD back in the CD drive and reboot your PC so the the Ubuntu desktop comes up
[noparse](8)[/noparse] On the Ubuntu desktop, look at the top menu bar and go to applications/accessories/terminal
(9) When the terminal Window comes up type:
         [COLOR="Red"]sudo gparted[/COLOR][COLOR="Black"]   and press "Enter"[/COLOR]

     This brings up the disk manager.  You want to:

        (a) delete all non-Windows partitions
        (b) resize your Windows partition to be larger (optional - you may want to leave this alone so you can 
             come back and try Ubuntu again!:) )

(10) When you have finished deleting the Ubuntu partitions, just restart your PC, removing the CD from the 
       drive before it boots again.

If everything went correctly, your PC should just automatically boot Windows.  Note that on the first boot of Windows after you have changed the disk (especially if you resized the Windows partition), Windows may run a chkdsk - this is normal and should be ok.

[COLOR="Red"]If you have already deleted you Linux partitions and are getting grub errors, please try this as suggested by this user (thanks for the neat addition!!)[/COLOR]

 Bothered  
A Carafe of Ubuntu
   Join Date: Jun 2007
Location: United Kingdom
Beans: 136
Ubuntu 7.04 Feisty Fawn User
Windows User 

 
Re: HowTo: Remove Ubuntu (& Restore Windows) 

--------------------------------------------------------------------------------

If you delete the ubuntu partitions without running mbrfix then you can use the ubuntu LiveCD to restore the master boot record by:

1. Booting from the ubuntu LiveCD
2. Enabling universe repositories - launch System->Administation->Software Sources and check the "Community maintained Open Source software (universe)"
3. Installing the "ms-sys" package - click Applications->Accessories->Terminal and type "sudo apt-get update" and then "sudo apt-get install ms-sys".
4. Finally restore the Windows master boot record by entering the command "ms-sys -w /dev/[drive]", where [drive] is the hard disk whose Windows master boot record you want to restore. You can find out which this is by launching gparted (System->Administration->GNOME Partition Editor) and cycling through the available drives until you find your Windows partition 

-    -     -     -     -

Hope this helps, and please let me know if anyone finds any errors.  Also, for anyone using this post, "we" really hope you will come back to Ubuntu someday!  Linux, and Ubuntu, will be waiting!:)

============================

Trouble shooting:

If, after following this guide, you can not boot to Windows you may need to boot a live CD and manually delete the Ubuntu partition (making it unpartitioned space, adding it to the Windows partition, or formatting it to FAT/NTFS).  Additionally you need to be sure the MBR is set for Windows.  You will need to search the forums for more help on that.  In addition, the following Microsoft articles may be of help:


[http://support.microsoft.com/kb/247804](http://support.microsoft.com/kb/247804)

[http://support.microsoft.com/kb/314458](http://support.microsoft.com/kb/314458)

===========================
(Thanks bodhi.zazen!!!)

---

### Post by killchaos6669 on 2008-08-24
yeek, windows is so gross. I don't know why anyone would want that virus on their machine.

---

### Post by Luci4 on 2008-08-25
Hi,
I would like to delete my ubuntu, mainly because my laptop just cannot handle it and I really do not want to spend hours on end trying to figure out how to make linux work on my pc. I've tried it before, and it kept freezing up, now I'm just tired of it.
I'll come back to linux once I have a new computer!

But anyways, my question is, I just did the fixmbr thing and now I would like to remove my ubuntu completely but I do not have a live cd and I'm not in the position to obtain one either.
I do have partition magic which allows me to delete ubuntu and resize.
Now that I already fixed mbr, is it safe to delete ubuntu this way? Or will I then still get grub errors???

Thanks for the help!

---

### Post by xthajesta on 2008-10-23
Ok I am trying to delete Ubuntu and restore my laptop back to Windows Vista. My laptops been going crazy since I installed Ubuntu. I have tried the Mbrfix thing tons of times but get the error Message Function Failed. Error 5: Access is denied. I am running a Acer Aspire 5630 laptop. I my drive is 0. I have windows and ubuntu dual partioned. I also have the windows recovery partioned. The laptop came this way I don't have a single cd for Ubuntu, Windows, or anything else.

---

### Post by kris07LX on 2008-11-10
umm how do i install  mbrfix?

---

### Post by rsambuca on 2008-11-10
> **kris07LX said:**
> umm how do i install  mbrfix?

Instructions and link are in post #1 of this thread.

---

### Post by cloroxmartini on 2008-11-21
How do I know if my boot device is set to device 0?  Because I already unzipped mbrfix and ran the command prompt lines.

---

### Post by bengreer on 2008-12-31
> **anewguy said:**
> Okay, I know some people are going to have a cow because I'm posting this.  But the truth is, there are a lot of people trying Ubuntu now since it has gotten more press.  If you search the forums, you will notice there are people (A) looking to remove Ubuntu and go back to just Windows, and (B) people who have attempted to remove Ubuntu for just Windows only to blame Ubuntu when Windows doesn't boot.  It's a fact of life that people are going try this out and want to delete it, so why not give them a way to do it that is fairly easy and will hopefully leave them with a good feeling, instead of getting mad at Ubuntu because the partitions needed by grub are gone?

So......for all of you who have a dual-boot system and are looking to remove Ubuntu for now, here are some tips.    NEVER NEVER NEVER just remove the Ubuntu partitions - you won't be able to boot Windows because the information pointed to by your master boot record will be gone.  Instead, follow these easy steps:

(1) Boot you Windows installation
(2) Click on this link [[COLOR="Red"]Get Mbrfix[/COLOR]]("http://www.download.com/MbrFix/3000-2094_4-10485991.html?tag=lst-0-1")
(3) Download the program, unzip it and copy it to your root folder (I'll assume c:\)
(4) Open up the command prompt in Windows by going to start/accessories/command prompt
(5) Type:
          [COLOR="Red"]cd \[/COLOR][COLOR="Black"]     and press "Enter"[/COLOR]
         [COLOR="Red"]mbrfix /drive 0 fixmbr /yes[/COLOR][COLOR="Black"]   and press "Enter"[/COLOR]

*PLEASE NOTE*  The above assumes your boot device is device 0 - if you are not sure on this please post for help.

(6) Close the command prompt window


*PLEASE NOTE*  The following assumes you want to get rid of your Ubuntu partitions and resize you Windows partition(s) to take up that space.  If you do not wish to do so, you can stop now.

(7) Put your Ubuntu LiveCD back in the CD drive and reboot your PC so the the Ubuntu desktop comes up
[noparse](8)[/noparse] On the Ubuntu desktop, look at the top menu bar and go to applications/accessories/terminal
(9) When the terminal Window comes up type:
         [COLOR="Red"]sudo gparted[/COLOR][COLOR="Black"]   and press "Enter"[/COLOR]

     This brings up the disk manager.  You want to:

        (a) delete all non-Windows partitions
        (b) resize your Windows partition to be larger (optional - you may want to leave this alone so you can 
             come back and try Ubuntu again!:) )

(10) When you have finished deleting the Ubuntu partitions, just restart your PC, removing the CD from the 
       drive before it boots again.

If everything went correctly, your PC should just automatically boot Windows.  Note that on the first boot of Windows after you have changed the disk (especially if you resized the Windows partition), Windows may run a chkdsk - this is normal and should be ok.

[COLOR="Red"]If you have already deleted you Linux partitions and are getting grub errors, please try this as suggested by this user (thanks for the neat addition!!)[/COLOR]

 Bothered  
A Carafe of Ubuntu
   Join Date: Jun 2007
Location: United Kingdom
Beans: 136
Ubuntu 7.04 Feisty Fawn User
Windows User 

 
Re: HowTo: Remove Ubuntu (& Restore Windows) 

--------------------------------------------------------------------------------

If you delete the ubuntu partitions without running mbrfix then you can use the ubuntu LiveCD to restore the master boot record by:

1. Booting from the ubuntu LiveCD
2. Enabling universe repositories - launch System->Administation->Software Sources and check the "Community maintained Open Source software (universe)"
3. Installing the "ms-sys" package - click Applications->Accessories->Terminal and type "sudo apt-get update" and then "sudo apt-get install ms-sys".
4. Finally restore the Windows master boot record by entering the command "ms-sys -w /dev/[drive]", where [drive] is the hard disk whose Windows master boot record you want to restore. You can find out which this is by launching gparted (System->Administration->GNOME Partition Editor) and cycling through the available drives until you find your Windows partition 

-    -     -     -     -

Hope this helps, and please let me know if anyone finds any errors.  Also, for anyone using this post, "we" really hope you will come back to Ubuntu someday!  Linux, and Ubuntu, will be waiting!:)

============================

Trouble shooting:

If, after following this guide, you can not boot to Windows you may need to boot a live CD and manually delete the Ubuntu partition (making it unpartitioned space, adding it to the Windows partition, or formatting it to FAT/NTFS).  Additionally you need to be sure the MBR is set for Windows.  You will need to search the forums for more help on that.  In addition, the following Microsoft articles may be of help:


[http://support.microsoft.com/kb/247804](http://support.microsoft.com/kb/247804)

[http://support.microsoft.com/kb/314458](http://support.microsoft.com/kb/314458)

===========================
(Thanks bodhi.zazen!!!)




After I type in:

```
sudo apt-get update
```

I get this:
```

Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Translation-en_US
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Translation-en_US
Hit http://archive.ubuntu.com hardy Release.gpg                                
Ign http://archive.ubuntu.com hardy/main Translation-en_US                
Hit http://security.ubuntu.com hardy-security Release.gpg
Ign http://security.ubuntu.com hardy-security/main Translation-en_US
Ign http://archive.ubuntu.com hardy/restricted Translation-en_US
Ign http://archive.ubuntu.com hardy/universe Translation-en_US
Hit http://archive.ubuntu.com hardy-updates Release.gpg
Ign http://archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com hardy-updates/universe Translation-en_US
Hit http://archive.ubuntu.com hardy Release    
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Hit http://security.ubuntu.com hardy-security Release
Hit http://archive.ubuntu.com hardy-updates Release
Hit http://security.ubuntu.com hardy-security/main Packages         
Hit http://archive.ubuntu.com hardy/main Packages
Hit http://archive.ubuntu.com hardy/restricted Packages
Hit http://archive.ubuntu.com hardy/universe Packages
Hit http://archive.ubuntu.com hardy/main Sources
Hit http://archive.ubuntu.com hardy/restricted Sources
Hit http://security.ubuntu.com hardy-security/restricted Packages
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/main Sources
Hit http://archive.ubuntu.com hardy/universe Sources
Hit http://archive.ubuntu.com hardy-updates/main Packages
Hit http://archive.ubuntu.com hardy-updates/restricted Packages
Hit http://archive.ubuntu.com hardy-updates/universe Packages
Hit http://archive.ubuntu.com hardy-updates/main Sources
Hit http://security.ubuntu.com hardy-security/restricted Sources
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://archive.ubuntu.com hardy-updates/restricted Sources
Hit http://archive.ubuntu.com hardy-updates/universe Sources
Reading package lists... Done
```

Then, I type: 

```
sudo apt-get install ms-sys
```

I get:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ms-sys
```

It is not working, what do I do?

---

### Post by bodhi.zazen on 2009-01-01
I am not sure if this package is maintained

[http://packages.ubuntu.com/search?keywords=ms-sys&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=ms-sys&searchon=names&suite=all&section=all)

You could try downloading the .deb and see if it works, or try the Knoppix CD.

---

### Post by caljohnsmith on 2009-01-01
It seems "ms-sys" is no longer available in the Ubuntu repositories, but fortunately there are a number of alternative solutions. Instead of using ms-sys, you can install a Windows equivalent MBR by doing the following:
```
sudo apt-get install lilo
sudo lilo -M  /dev/[COLOR="Blue"]sdX[/COLOR] mbr
```
And replace sdX with the drive you want to install a Windows equivalent MBR to. The first install command may not be necessary if you run the lilo command from a recent Ubuntu Live CD, because at least the Intrepid Live CD has lilo installed by default (I'm not sure about prior versions though). How about giving the above commands a shot and let me know how it goes.

---

### Post by creek23 on 2009-01-01
> **HowTo: Remove Ubuntu (& Restore Windows)**

I say, you should have used Wubi instead. :P

And since you didn't, just read the [guide from the first post]("http://ubuntuforums.org/showthread.php?t=508927"). ;)

---

### Post by Luci4 on 2009-01-06
Does anyone know how to get lost HD space back???
I uninstalled ubuntu according to this post, but then in my computer, my HD wasn't 60, but 40. The 20 that used to be for ubuntu is now unrecognised. However, when I check partition magic, it does say 60... weird... 
I want my space back! can anybody help?

---

### Post by El_Belgicano on 2009-01-06
> **Luci4 said:**
> Does anyone know how to get lost HD space back???
I uninstalled ubuntu according to this post, but then in my computer, my HD wasn't 60, but 40. The 20 that used to be for ubuntu is now unrecognised. However, when I check partition magic, it does say 60... weird... 
I want my space back! can anybody help?

Use Gparted from a liveCD, select free space, format to FAT32 or NTFS, reboot.
The most "to-the-point" method I can come up with...

Thomas

---

### Post by mgist007 on 2009-02-12
I have tried the ms-sys but it keeps telling me that it cannot find the package.  I have checked the box and did the get update.  Is there something missing?

Thanks

---

### Post by fiona-conn on 2009-04-21
ms-sys does not appear to exist.

Nor can I delete my Linux partitions in GParted because it asks me to unmount volumes higher than 5, but it will not let me delete /dev/sda6 (the swap file). 

Any help?

---

### Post by bodhi.zazen on 2009-04-21
ms-sys : [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=ms-sys&searchon=name&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=ms-sys&searchon=name&subword=1&version=all&release=all)

For your partitions you need to manage them from a live CD. Unmount ALL your partitns from gparted first.

Then unmount your swap ```
sudo swpaoff -a
```

If you can not find ms-sys, use your windows install CD and / or try Knopix and/ or re-install Ubuntu with a separate small boot partition, then delete the ubuntu partition and keep the small boot partition (with the grub files, you can delete the linux kernels).

---

### Post by Duck2006 on 2009-04-21
> **fiona-conn said:**
> ms-sys does not appear to exist.

Nor can I delete my Linux partitions in GParted because it asks me to unmount volumes higher than 5, but it will not let me delete /dev/sda6 (the swap file). 

Any help?

Are you trying to do this from with in ubuntu?
You may find it easy to use the live CD of Gparted.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Or parted magic.

[http://partedmagic.com/](http://partedmagic.com/)

To redo your partitions.

---

### Post by JoeinSandy on 2009-06-02
I have read all the posts in this thread, but I don't think my exact issue has been addressed. 

I didn't install Ubuntu--just ran it from the Live CD. My wireless card isn't supported, so I shut down and rebooted Windows. 

The only problem was that the registry (?) appears to be virgin. All my apps are there, but documents, settings, bookmarks, all the personalizations are gone. 

Do I need to follow the original procedure when Ubuntu wasn't installed? Did it create a Linux partition anyway? Is my data gone? (I have a backup, but restoring is a pain.)

Thanks!
-j

---

### Post by bodhi.zazen on 2009-06-02
> **JoeinSandy said:**
> I have read all the posts in this thread, but I don't think my exact issue has been addressed. 

I didn't install Ubuntu--just ran it from the Live CD. My wireless card isn't supported, so I shut down and rebooted Windows. 

The only problem was that the registry (?) appears to be virgin. All my apps are there, but documents, settings, bookmarks, all the personalizations are gone. 

Do I need to follow the original procedure when Ubuntu wasn't installed? Did it create a Linux partition anyway? Is my data gone? (I have a backup, but restoring is a pain.)

Thanks!
-j

Running Ubuntu from a live CD, without installation, should not affect your hard drive. That is the whole point of running the live CD.

---

### Post by goosemontana on 2009-09-09
i need to remove ubuntu because of some problems but i dont know my boot device number. can someone help me?

---

### Post by bodhi.zazen on 2009-09-09
> **goosemontana said:**
> i need to remove ubuntu because of some problems but i dont know my boot device number. can someone help me?

Either post a screenshot of gparted or the output of:

```
sudo fdisk -l
```

See also : [HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018&highlight=partitioning")

---

### Post by markuspxpx on 2009-09-28
Amazing post, but I have a error right that I cant install the package...

[FONT=courier new][/FONT]

ubuntu@ubuntu:~$ sudo apt-get install ms-sys
Reading Package Lists... Ready      
Reading state information... Ready 
E: Could not find the package ms-sys


can someone help me ?

---

### Post by bodhi.zazen on 2009-09-28
It was removed from the reposs due to liscensing.

[http://ms-sys.sourceforge.net/#Download](http://ms-sys.sourceforge.net/#Download)

---

### Post by markuspxpx on 2009-09-28
ahh... thank you a lot !

but, I don't know how to install this package , can you help me what I need to do to install it ?

---

### Post by bodhi.zazen on 2009-09-28
> **markuspxpx said:**
> ahh... thank you a lot !

but, I don't know how to install this package , can you help me what I need to do to install it ?

There are detailed instructions in the README which are also posted here :

[http://ms-sys.sourceforge.net/](http://ms-sys.sourceforge.net/)

You will need to install build-essential

```
sudo apt-get install build-essential
```

Then extract the archive and proceed with make and then make install.

You can also look at other options suggested in this thread.

---

### Post by markuspxpx on 2009-09-28
Its so good to be true... 

here I am with this error on ms-sys installation.

root@ubuntu:/home/ubuntu/ms-sys-2.1.3# ms-sys --mbr /dev/sda1
/dev/sda1 seems to be a disk partition device,
use the switch -f to force writing of a master boot record

root@ubuntu:/home/ubuntu/ms-sys-2.1.3# ms-sys -f /dev/sda1
/dev/sda1 has an x86 boot sector,
it is an unknown boot record

---

### Post by oboedad55 on 2009-09-28
> **JoeinSandy said:**
> I have read all the posts in this thread, but I don't think my exact issue has been addressed. 

I didn't install Ubuntu--just ran it from the Live CD. My wireless card isn't supported, so I shut down and rebooted Windows. 

The only problem was that the registry (?) appears to be virgin. All my apps are there, but documents, settings, bookmarks, all the personalizations are gone. 

Do I need to follow the original procedure when Ubuntu wasn't installed? Did it create a Linux partition anyway? Is my data gone? (I have a backup, but restoring is a pain.)

Thanks!
-j

Did you defrag your hard drive before installing  Ubuntu? I made that mistake exactly once to learn my lesson. Not doing so hosed the partition I resized. Just a thought.

---

### Post by bodhi.zazen on 2009-09-28
> **markuspxpx said:**
> Its so good to be true... 

here I am with this error on ms-sys installation.

root@ubuntu:/home/ubuntu/ms-sys-2.1.3# ms-sys --mbr /dev/sda1
/dev/sda1 seems to be a disk partition device,
use the switch -f to force writing of a master boot record

root@ubuntu:/home/ubuntu/ms-sys-2.1.3# ms-sys -f /dev/sda1
/dev/sda1 has an x86 boot sector,
it is an unknown boot record

You sure you want /dev/sda1 and not /dev/sda ?

sda is the entire HD and my guess is you want to re-write the MBR on the hard drive and not sda1 (the first partition).

---

### Post by markuspxpx on 2009-09-28
Still trying... and crying too.

---

### Post by markuspxpx on 2009-09-29
First I want to tank you bodh.zazen for ur AMAZING patience to help me with this problem for a noob like me, better, windows user :(

I hope we can solve this, but if u can`t I will get a Windows Vista Ultimate SP2 DVD and fix this with bootrec.exe /fixboot or what I really don`t want, format this WinShit.
Like I said , I hope we can fix this to this post can be for others users with same problem.

Thank you a lot.


> 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3bf9da22

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       22947   184321746    7  HPFS/NTFS
/dev/sda2           22948       60800   304054222+   f  W95 Ext'd (LBA)
/dev/sda5           22948       60800   304054191    7  HPFS/NTFS
I tryied with just ` dev/sda ` and 
> 

root@ubuntu:/home/ubuntu/ms-sys-2.1.3# ms-sys --mbr /dev/sda
Windows 2000/XP/2003 master boot record successfully written to /dev/sda

I restarted the pc but doesnt work, still appear just WIN XP boot option but the HD with xp wasn`t plugged, just the HD 500gb with Vista 64 partition and Files partition

---

### Post by bodhi.zazen on 2009-09-29
I am sorry, I have not worked with windows much in several years.

Try these links :

[http://robert.penz.name/221/mini-howto-restore-windows-mbrbootloader-with-linux/](http://robert.penz.name/221/mini-howto-restore-windows-mbrbootloader-with-linux/)

[http://www.ehow.com/how_5089290_restore-windows-xp-bootloader.html](http://www.ehow.com/how_5089290_restore-windows-xp-bootloader.html)

---

### Post by markuspxpx on 2009-09-30
> **bodhi.zazen said:**
> I am sorry, I have not worked with windows much in several years.

Try these links :

[http://robert.penz.name/221/mini-howto-restore-windows-mbrbootloader-with-linux/](http://robert.penz.name/221/mini-howto-restore-windows-mbrbootloader-with-linux/)

[http://www.ehow.com/how_5089290_restore-windows-xp-bootloader.html](http://www.ehow.com/how_5089290_restore-windows-xp-bootloader.html)


[B]Thank you dude !

Finally my Windows Vista are working again .....

;D
[/B]

---

### Post by agoodliffe on 2009-11-01
Hello all,
Here is the question regarding removing Ubuntu 9.10 and restoring my Windows XP. 
I am relatively new to Ubuntu. A friend who knows it well back i n the day installed it in a dual boot on my Windows XP.
Now I decided to upgrade to Xubuntu 9.10. However by following the steps I screwed up the GRUB. Now when I turn on the computer the screen is black with GRUB in the top left hand corner.

Here are the steps that I followed
I downloaded the iso image, put it on a CD and installed the Live CD. In the partition area is the same for what I had before
Windows NTFS - /dev/sda1
Ubuntu 9.10 ext4 /dev/sda5
Shared drive fat32 /dev/sda2
swap /dev/sda4

What I think is that I screwed up the GRUB and MBR for WIndows. I would like to have access to my WIndows drive again - make a recovery CD (which I don't have :( and then start from scratch.
Any ideas??? I have downloaded the SuperGrub application but it has not been of any help and am unable to get internet access with my WIndows/Ubuntu machine so unable to download packages to the Ubuntu.
Any ideas on how to get back into my WIndows environment and disinstall Ubuntu and start from scratch - indeed from the shallow end;)
Thanks again for your help.

---

### Post by seshomaru samma on 2009-11-01
one thing you could try is to install ubuntu again
when ubuntu  installs properly you should have access to both windows and ubuntu.

---

### Post by agoodliffe on 2009-11-01
Thanks for the advice,
I just did that but on the Grub page when I try to access Windows it goes blank and then goes right back to the Grub page.
However I can access Xubuntu with no problems which is nice. 
But please if you have any suggestions on how to get back to my Windows partition. I really think it is a problem with the Grub but don't really know how it works. I have tried Supergrub but even that won't start my windows.

---

### Post by seshomaru samma on 2009-11-01
agoodlife,
i suggest you start a new thread about
include your setup 
your grub file
and the output of the terminal command 
```
sudo fdisk -l
```

---

### Post by sabertooth81 on 2009-11-15
i have  windows on drive  c:

and  a folder named ubuntu of 10 gb on d :  drive...

plzzz helppp  how to unistall ubuntu...

---

### Post by 34Dell17 on 2010-01-21
> **Rocket2DMn said:**
> You just gotta make sure you're using the right drive, not everybody is on drive 0.

Would I select the windows drive or the main ubuntu drive. Also, my computer has an OEM recovery/system drive will it be affected.

---

### Post by THORium234 on 2010-02-20
> **anewguy said:**
> *PLEASE NOTE*  The above assumes your boot device is device 0 - if you are not sure on this please post for help.

How do I check this?

---

### Post by A2JC4life on 2010-03-01
Thanks!  I still want to try out Ubuntu, but at the moment my HDD is simply too small (for my files, not for Ubuntu) and I need to remove that partition to regain that space as a short-term solution.  This will be very helpful. :)

---

### Post by dagdeniz on 2010-03-21
Thanks, used this guide more than one time; I'm trying to get into Linux and tried many systems during the last two weeks

If I got it right, the mbrfix application disables grub and reactivates windows' bootloader (ntldr?). That means, again if I got it right, if you do not want to get rid of Linux entirely, you do not need the mbrfix. 
So, what if I've windows plus two linux distros? Do I have to make any changes in the grub.cfg file in order to remove one of the distros or is it safe to directly format the partition? 

(in fact I want to remove debian and try another os beside windowsXP and Kubuntu)

---

### Post by Bucky Ball on 2010-03-21
Check which partition you are about to erase, erase and remove that partition's entry from your grub so the machine is not looking and stalling on that partition when you boot.

---

### Post by emooney on 2010-07-08
I got MbrFix.exe to finally work on my Vista machine. When I executed 'MbrFix.exe /drive 0 fixmbr /vista /yes', I was getting the following error message; "Error 5: access is denied".

What I had to do was in Explorer, right click on MbrFix.exe and under the Compatibility tab, I selected "Run this program as an administrator". Then I selected "Show settings for all users" and selected "Run this program as an administrator" again. Hit apply and OK and ran the file again in DOS and it worked. 

I now don't see the GRUB screen every time I reboot my system. YAY!!

---

### Post by the8thstar on 2010-07-08
Instead of having to fiddle with Windows you can always reinstall the Windows bootloader from within Ubuntu with the following commands:

> sudo apt-get install lilo && sudo lilo -M /dev/sda mbr

That should get things cleared up for you. CAREFUL though because from there on yu won't be able to access your Ubuntu partition anymore. You'll need a liveCD to access and erase your Ubuntu partition with this:

> sudo gparted

---

### Post by mjsh401 on 2010-08-17
> **anewguy said:**
> Okay, I know some people are going to have a cow because I'm posting this.  But the truth is, there are a lot of people trying Ubuntu now since it has gotten more press.  If you search the forums, you will notice there are people (A) looking to remove Ubuntu and go back to just Windows, and (B) people who have attempted to remove Ubuntu for just Windows only to blame Ubuntu when Windows doesn't boot.  It's a fact of life that people are going try this out and want to delete it, so why not give them a way to do it that is fairly easy and will hopefully leave them with a good feeling, instead of getting mad at Ubuntu because the partitions needed by grub are gone?

So......for all of you who have a dual-boot system and are looking to remove Ubuntu for now, here are some tips.    NEVER NEVER NEVER just remove the Ubuntu partitions - you won't be able to boot Windows because the information pointed to by your master boot record will be gone.  Instead, follow these easy steps:

(1) Boot you Windows installation
(2) Click on this link [[COLOR="Red"]Get Mbrfix[/COLOR]]("http://www.download.com/MbrFix/3000-2094_4-10485991.html?tag=lst-0-1")
(3) Download the program, unzip it and copy it to your root folder (I'll assume c:\)
(4) Open up the command prompt in Windows by going to start/accessories/command prompt
(5) Type:
          [COLOR="Red"]cd \[/COLOR][COLOR="Black"]     and press "Enter"[/COLOR]
         [COLOR="Red"]mbrfix /drive 0 fixmbr /yes[/COLOR][COLOR="Black"]   and press "Enter"[/COLOR]

*PLEASE NOTE*  The above assumes your boot device is device 0 - if you are not sure on this please post for help.

(6) Close the command prompt window


*PLEASE NOTE*  The following assumes you want to get rid of your Ubuntu partitions and resize you Windows partition(s) to take up that space.  If you do not wish to do so, you can stop now.

(7) Put your Ubuntu LiveCD back in the CD drive and reboot your PC so the the Ubuntu desktop comes up
[noparse](8)[/noparse] On the Ubuntu desktop, look at the top menu bar and go to applications/accessories/terminal
(9) When the terminal Window comes up type:
         [COLOR="Red"]sudo gparted[/COLOR][COLOR="Black"]   and press "Enter"[/COLOR]

     This brings up the disk manager.  You want to:

        (a) delete all non-Windows partitions
        (b) resize your Windows partition to be larger (optional - you may want to leave this alone so you can 
             come back and try Ubuntu again!:) )

(10) When you have finished deleting the Ubuntu partitions, just restart your PC, removing the CD from the 
       drive before it boots again.

If everything went correctly, your PC should just automatically boot Windows.  Note that on the first boot of Windows after you have changed the disk (especially if you resized the Windows partition), Windows may run a chkdsk - this is normal and should be ok.

[COLOR="Red"]If you have already deleted you Linux partitions and are getting grub errors, please try this as suggested by this user (thanks for the neat addition!!)[/COLOR]

 Bothered  
A Carafe of Ubuntu
   Join Date: Jun 2007
Location: United Kingdom
Beans: 136
Ubuntu 7.04 Feisty Fawn User
Windows User 

 
Re: HowTo: Remove Ubuntu (& Restore Windows) 

--------------------------------------------------------------------------------

If you delete the ubuntu partitions without running mbrfix then you can use the ubuntu LiveCD to restore the master boot record by:

1. Booting from the ubuntu LiveCD
2. Enabling universe repositories - launch System->Administation->Software Sources and check the "Community maintained Open Source software (universe)"
3. Installing the "ms-sys" package - click Applications->Accessories->Terminal and type "sudo apt-get update" and then "sudo apt-get install ms-sys".
4. Finally restore the Windows master boot record by entering the command "ms-sys -w /dev/[drive]", where [drive] is the hard disk whose Windows master boot record you want to restore. You can find out which this is by launching gparted (System->Administration->GNOME Partition Editor) and cycling through the available drives until you find your Windows partition 

-    -     -     -     -

Hope this helps, and please let me know if anyone finds any errors.  Also, for anyone using this post, "we" really hope you will come back to Ubuntu someday!  Linux, and Ubuntu, will be waiting!:)

============================

Trouble shooting:

If, after following this guide, you can not boot to Windows you may need to boot a live CD and manually delete the Ubuntu partition (making it unpartitioned space, adding it to the Windows partition, or formatting it to FAT/NTFS).  Additionally you need to be sure the MBR is set for Windows.  You will need to search the forums for more help on that.  In addition, the following Microsoft articles may be of help:


[http://support.microsoft.com/kb/247804](http://support.microsoft.com/kb/247804)

[http://support.microsoft.com/kb/314458](http://support.microsoft.com/kb/314458)

===========================
(Thanks bodhi.zazen!!!)
I don't know what is my boot device number.
What can I do?

---

### Post by bodhi.zazen on 2010-08-17
> **mjsh401 said:**
> I don't know what is my boot device number.
What can I do?

In Ubuntu, run ```
fdisk -l
```

That will list your partitions, windows is the ntfs partition.

See also :

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018&highlight=partitioning")

---

### Post by Kobus on 2010-12-07
This is what I did to remove Ubuntu and restore to original Windows only configuration.

I had a Netbook with dual boot Win7 with Ubuntu 10.04. I had to clean-up the machine and return to employer.

- Copied /boot folder from Win7 DVD onto USB memory stick. (No optical drive on netbook)
- Boot into Windows. (Nothing removed yet)
- Insert memory stick with Windows /boot folder.
- Right click on bootsect.exe, select properties.
- Under the Compatibility tab select Run this program as an administrator. (initially got access denied message)
- Then follow the instructions here (steps 7-9): [http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

After restarting the machine, I used Windows Disk Management to remove Linux partition and reclaim space for Windows partition.
- Right click Computer. Select Manage.
- Select Storage, Disk Management.
- Change partitions as required.
- Restart

Machine is now restored to Windows only :-(

But, don't despair... new machine will also get Ubuntu installed!!  :-D

---

### Post by jaronron10 on 2010-12-29
Although this does not help if someone (ie: me) who compleatly erased there netbook hard disk to install Ubuntu. Im not really sure how I would stick a MS-Windows install cd in this thing anyway!!! No cdrom drive!?!* lol

Good thing there are forums full of people who are helping me on my way to a happy Ubuntu user!!

Thanks All

---

### Post by Razor338 on 2010-12-29
thanks dude!

---

### Post by warlock43 on 2011-02-09
For the quoted step below...can i have some help with finding my drive number? PLEASE ?!



"(5) Type:
cd \ and press "Enter"
mbrfix /drive 0 fixmbr /yes and press "Enter"

*PLEASE NOTE* The above assumes your boot device is device 0 - if you are not sure on this please post for help."

[http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)

---

### Post by charndt on 2011-03-19
Thanks.  That worked great.  With Vista I could use the Vista partition manager to reallocate the space.

---

### Post by rahulchavan34 on 2011-04-13
[I]--------------------------------------------------------------------------------

If you delete the ubuntu partitions without running mbrfix then you can  use the ubuntu LiveCD to restore the master boot record by:[/I] [I]

1. Booting from the ubuntu LiveCD[/I] [I]
2. Enabling universe repositories - launch  System->Administation->Software Sources and check the "Community  maintained Open Source software (universe)"
3. Installing the "ms-sys" package - click  Applications->Accessories->Terminal and type "sudo apt-get update"  and then "sudo apt-get install ms-sys".
4. Finally restore the Windows master boot record by entering the  command "ms-sys -w /dev/[drive]", where [drive] is the hard disk whose  Windows master boot record you want to restore. You can find out which  this is by launching gparted (System->Administration->GNOME  Partition Editor) and cycling through the available drives until you  find your Windows partition 

-    -     -     -     -[/I] [I]

Hope this helps, and please let me know if anyone finds any errors.   Also, for anyone using this post, "we" really hope you will come back to  Ubuntu someday!  Linux, and Ubuntu, will be waiting![/I] [I]:smile:

============================[/I] [I]

Trouble shooting:[/I] [I]

If, after following this guide, you can not boot to Windows you may need  to boot a live CD and manually delete the Ubuntu partition (making it  unpartitioned space, adding it to the Windows partition, or formatting  it to FAT/NTFS).  Additionally you need to be sure the MBR is set for  Windows.  You will need to search the forums for more help on that.  In  addition, the following Microsoft articles may be of help:[/I] [I]


[http://support.microsoft.com/kb/247804](http://support.microsoft.com/kb/247804)[/I]   [I]

[http://support.microsoft.com/kb/314458](http://support.microsoft.com/kb/314458)[/I]  [I]

===========================
[/I]**hi, i did the same thing what is said above but i get an error message i.e when i type _sudo_** _**apt-get install ms-sys**_  [B]it says E: couldn't find package ms-sys...
help need pls... ive just deleted the ubuntu partition and now vista doesnt boot up...
[/B]

---

### Post by chaucolai on 2011-07-15
Hi,
I'm using MBRFix to fix my MBR on my netbook. However, I keep getting "Function failed. Error 5: Access is Denied".
[IMG]http://i52.tinypic.com/2q8vdpc.png[/IMG]

I'm running Windows 7 Starter on a HP Mini (god only knows what it is.. a low end one) and trying to remove UNR/UNE (only because Word doesn't run on it and when you're taking notes solely on a netbook, you need the Quick Styles Gallery!).
Can anybody help?

---

### Post by daranth on 2011-08-04
i was following the first steps of the instructions, and when i inserted the linux ubuntu disk, it wouldnt load anything apart from boot into first hard drive, which then came up with the error "ntldr missing" ?

---

### Post by slavinzing56 on 2011-08-05
This is a great idea.  Being able to easily remove Ubuntu will help  reduce the bitter taste of defeat when new users can't figure something  out.  Plus, it would be nice to know how to undo a really dumb decision  so that you can restart fresh, if needed.

---

### Post by Duck2006 on 2011-08-05
> **chaucolai said:**
> Hi,
I'm using MBRFix to fix my MBR on my netbook. However, I keep getting "Function failed. Error 5: Access is Denied".
[IMG]http://i52.tinypic.com/2q8vdpc.png[/IMG]

I'm running Windows 7 Starter on a HP Mini (god only knows what it is.. a low end one) and trying to remove UNR/UNE (only because Word doesn't run on it and when you're taking notes solely on a netbook, you need the Quick Styles Gallery!).
Can anybody help?

Did you try just.
C:\>fixmbr

---

### Post by cathalcummins on 2011-08-10
-----------------
EDIT
-----------------

Apologies, I misread the very first thread. I thought "start your windows installation..." referred to the XPCD...

---

### Post by YannBuntu on 2011-08-11
A new version of OS-Uninstaller has arrived ! :guitar:

--> [https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)

[[img]http://pix.toile-libre.org/upload/img/1313035409.png[/img]](http://pix.toile-libre.org/?img=1313035409.png)

Enjoy :)

---

### Post by cathalcummins on 2011-08-14
Great tutorial -- worked for me. I was using XP professional and Ubuntu 11.04, XP installed first.

One suggestion (probably has been made already): to find out which number drive your Windows disk is, just click the drive's properties when you're on Windows. Might be handy to put this info in the sticky.

---

### Post by cdoebbler on 2011-09-02
I am using Ubuntu 11.04 on a HP Compaq 7100 Minitower. I have Windows 7 loaded and tried to load Ubuntu...apparently twice. No my computer does not boot from harddisk. Does boot from Ubuntu 11.04 CD Rom and provided internet access, but not from Windows 7 boot disk. Any help welcomed. Below is result of Boot Info Script:

>                   Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 2036. But according to the info from fdisk, 
                       sda6 starts at sector 60088320.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda3/Wubi: _____________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048     4,194,303     4,192,256   7 NTFS / exFAT / HPFS
/dev/sda2           4,196,350    94,283,775    90,087,426   f W95 Extended (LBA)
/dev/sda5           4,196,352    60,086,283    55,889,932   7 NTFS / exFAT / HPFS
/dev/sda6          60,088,320    94,281,727    34,193,408   7 NTFS / exFAT / HPFS
/dev/sda3          94,285,485 1,937,487,194 1,843,201,710   7 NTFS / exFAT / HPFS
/dev/sda4       1,937,494,016 1,953,520,064    16,026,049   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        CE0ABBB70ABB9AC3                       ntfs       SYSTEM
/dev/sda3        01CB70914703A0A0                       ntfs       OS
/dev/sda4        147227167226FC5C                       ntfs       HP_RECOVERY
/dev/sda5        8A84F82F84F81EFF                       ntfs       New Volume
/dev/sda6        68467CCA467C9B10                       ntfs       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


========================= sda6/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 0
ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sda6: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          0
            ?? = ??             syslinux/vesamenu.c32                          1

============== sda6: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3/Wubi

00000000  30 30 30 30 30 30 30 30  30 30 30 30 30 30 30 30  |0000000000000000|
*
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde sdf sdg 

=============================== StdErr Messages: ===============================

ERROR: asr: seeking device "/dev/sdb" to 18446744073709551104
ERROR: ddf1: seeking device "/dev/sdb" to 18446744073709551104
ERROR: ddf1: seeking device "/dev/sdb" to 18446744073709420032
ERROR: hpt37x: seeking device "/dev/sdb" to 4608
ERROR: hpt45x: seeking device "/dev/sdb" to 18446744073709545984
ERROR: isw: seeking device "/dev/sdb" to 18446744073709550592
ERROR: isw: seeking device "/dev/sdb" to 18446744073709551104
ERROR: isw: seeking device "/dev/sdb" to 18446744073708468736
ERROR: jmicron: seeking device "/dev/sdb" to 18446744073709551104
ERROR: lsi: seeking device "/dev/sdb" to 18446744073709551104
ERROR: nvidia: seeking device "/dev/sdb" to 18446744073709550592
ERROR: sil: seeking device "/dev/sdb" to 18446744073709551104
ERROR: via: seeking device "/dev/sdb" to 18446744073709551104
ERROR: asr: seeking device "/dev/sdb" to 18446744073709551104
ERROR: ddf1: seeking device "/dev/sdb" to 18446744073709551104
ERROR: ddf1: seeking device "/dev/sdb" to 18446744073709420032
ERROR: hpt37x: seeking device "/dev/sdb" to 4608
ERROR: hpt45x: seeking device "/dev/sdb" to 18446744073709545984
ERROR: isw: seeking device "/dev/sdb" to 18446744073709550592
ERROR: isw: seeking device "/dev/sdb" to 18446744073709551104
ERROR: isw: seeking device "/dev/sdb" to 18446744073708468736
ERROR: jmicron: seeking device "/dev/sdb" to 18446744073709551104
ERROR: lsi: seeking device "/dev/sdb" to 18446744073709551104
ERROR: nvidia: seeking device "/dev/sdb" to 18446744073709550592
ERROR: sil: seeking device "/dev/sdb" to 18446744073709551104
ERROR: via: seeking device "/dev/sdb" to 18446744073709551104


---

### Post by jrschrock on 2011-09-04
This seems like a good thread in which to pose this scenario: I'm not absolutely to the point where I'm ready to go back to Windows, but it's getting increasingly difficult for me to justify continued use of Ubuntu. I'm pretty sure I'm going on 6 months of using it, too, so unless I'm completely oblivious, I don't feel like I'm giving up right away. Here are some reasons why..

-My income is nearly 100% based around use of my computer- IM, link-building, etc. I need to use a toolbar developed by my employer to build links (has to be Firefox browser) and I've never been able to successfully install it, so I've got to use my roommate's laptop to work.

-I use Skype very frequently to communicate with my daughter. However, my internal mic has never worked since installing Ubuntu. Again, using others' PCs for this.

-I've never been able to sync my iPod nor my phone to my laptop since installing Ubuntu. These were both very intuitive, trouble-free procedures with Windows. So, you guessed it- roomie's laptop.

The increase in performance Ubuntu provides barely noticeable. Yeah, the software is free, but I'm rarely impressed by it. Especially with digital audio workstation/production type programs. Certainly not media players. Here's the thing-it is very, very easy to get expensive software for nothing. I'm not saying it's right, but I'm also not saying my moral compass points due north. 

Yes, I've done as much research as I've felt worth doing to remedy the aforementioned issues, but obviously have not found solutions, as the issues still exist.

So, remind me again why Linux/Ubuntu OS is so highly touted as the end-all/beat-all OS by its legion of adoring fans. I'm missing something here. Oh yeah, convenience and performance......

Any suggestions would be appreciated and with any luck, more useful than those that I've received thus far.

---

### Post by jrschrock on 2011-09-04
> **slavinzing56 said:**
> This is a great idea.  Being able to easily remove Ubuntu will help  reduce the bitter taste of defeat when new users can't figure something  out.  Plus, it would be nice to know how to undo a really dumb decision  so that you can restart fresh, if needed.

It's quotes like these that make me think maybe, just maybe, I'm missing out on something incredible. Nonetheless, I remain skeptical. Hah, skeptical is underlined as being misspelled, but is certainly is not, and the suggested correct spelling is 'sceptical'. This is just one of many examples of incorrect spell-checks I've come across. 

Time to back up the horn-tooting, Ubuntu Universe........(Ubuntu is also marked as being misspelled, lol...jeez)

---

### Post by JCMB1 on 2011-11-16
Actually, it's not a bitter taste of defeat.

I installed 11.10 and found that most of the software I wanted to run didn't run on that system. I had to "recreate" the gnome system, but still find 11.10 user hostile when it is compared to previous versions of Ubuntu.

But, I spent an evening trying to get 11.10 to do what I want to do and will use it for a while before I give up and install 10.04.

And the Live CD won't give you a taste of what software is available and how installed programmes will function (or not--as the case may be).

An OS should allow you to use your computer.  Otherwise, it's just windows.

---

### Post by anewguy on 2012-03-01
Please remember this thread isn't about what you like/don't like about Ubuntu or problems you are having accomplishing your tasks in Ubuntu.  It is purely for the purpose of wanting to (or perhaps already have and are stuck) remove Ubuntu and going back to Windows.

---

### Post by szdhsn on 2012-06-06
Please tell me how to know my MBR device? I am using windows 7 & ubuntu 12.04LTS.

---

### Post by soumoks on 2012-06-06
guys also try this amazing piece of sw called easyBCD for windows
,here is the link:
[http://neosmart.net/EasyBCD/](http://neosmart.net/EasyBCD/)
its a free piece of sw btw,scroll down to the bottom of the page and click on register,it should give u the download link..
this sw is for restoring the mbr,u will have to remove the ubuntu partitions manually..
hope i helped someone..

---

### Post by YannBuntu on 2012-06-06
> **szdhsn said:**
> Please tell me how to know my MBR device? I am using windows 7 & ubuntu 12.04LTS.

If you remove Ubuntu via [https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller) (from a live-CD), you won't need to know it. The Ubuntu system partition will be formated, and the MBR will be automatically restored, so that your PC will directly boot on Windows.

---

