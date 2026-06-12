---
title: "a simple but probably stupid question"
date: 2011-01-03
forum: Virtualisation
---

### Post by skyzthelimit230 on 2011-01-03
i am currently performing a full migration to ubuntu but i would like to set up windows 7 as a guest OS using virtualbox. 

Would this work? I do  have a windows 7 disc from when i installed it on my computer a year ago.

would i need another product key too?

---

### Post by pbpersson on 2011-01-03
> **skyzthelimit230 said:**
> i am currently performing a full migration to ubuntu but i would like to set up windows 7 as a guest OS using virtualbox. 

Would this work? I do  have a windows 7 disc from when i installed it on my computer a year ago.

would i need another product key too?

My understanding is that IF you bought the Windows 7 CD in a retail store (and it did not come with a computer) then you can install it on another machine IF the original machine died.

When Windows 7 is activated it creates an "image" of your computer hardware and sends it up to Microsoft.  That copy of Windows "attaches" itself to that hardware and if you ever move it to another computer you have to convince Microsoft that the original hardware is gone, was destroyed in a fire, abducted by aliens, whatever.......

If you want to install a second copy of Windows 7 you would need a new CD key for the new copy.

If you install Windows 7 in a virtual session, that virtual machine would in theory become the new hardware environment.  If you read the Windows 7 license it will inform you that installing Windows in a virtual environment is strictly forbidden because Microsoft is no longer in complete control of reality at that point.

This is not by any means a stupid question.

---

### Post by 1clue on 2011-01-03
I've done this.

If it's the OS that came with the PC then it won't even install on the VM, even if you're using the same hardware.  Those images are specific down to even a serial number range of what should be the same box.  I've had to order the original OS image too, to restore the original OS for some reason.  These images Will Not Work on a VM.  Start over from scratch, get your Windows CD, install it and put both the CD and license key in your safe and bury it in the back yard.

If you bought Windows 7 from a store, not as part of a PC, then it SHOULD work.  If you bought it as an upgrade then you need not only the Windows 7 disk but the one you upgraded from as well, and legally speaking neither of those can be active on any other machine once you fire up your VM.  IMO if you're gonna do it, then buy a new license unencumbered by an upgrade requirement.  WAY less trouble when it comes time to move the VM or whatever.

I've done this in different ways.  First, you take a ghosting tool like VMware Converter and follow the directions.  VMware Converter takes the image you want, converts it to VMware and then quits.  There is at least one tool per virtualization technology.

Second, you install a fresh image on the VM and install the OS from scratch, and re-install all your software.

Now, speaking about legality and what Microsoft will do:

No matter what your license says, Microsoft WILL allow you to install on a virtual environment.  They make their own virtualization scheme, so even if they never did before they surely do now.  I did my images with VMware.  Go to any modern company with 20 or more people in it, the IT shop is using virtual machines.  Most of your web hosting sites are on virtual machines.  VMs are here and they're gonna stay awhile, and nobody knows it better than Microsoft.

Legally speaking, a virtual image is absolutely no different from hardware.  You need a separate license for every piece of software on the VM which is not tied to any software on any other machine.  That includes Linux, by the way.  It's free, but there are conditions of use that you should be aware of.

Now, say you have that virtual machine up and running.  You shut it down and then copy the image to another location, and restart the machine.  What you have now is a backup.  The VM will know where it has been run from before, and if you change directories or processors or whatever it will ask you if you moved the image or duplicated it.  Tell the truth, it's easier than trying to fake it and will ultimately end in the same result anyway, you'll need new licenses.  As long as you only run the one image, the second image does not legally count.

If you trash your running image and delete it, you can copy the backup back over to the original location and start it, and it will be a normal startup.  No questions, no glitches, you just wind up back where you were when you made the backup.  I do it all the time for software development, it's a complete operating system rollback and it's far faster than anything else you might do.

Now you light up that second image, and suddenly you have created a new virtual machine, which means every software license requirement just doubled.  If it was Windows 7, then you now need two licenses for Windows 7, MS Office, etc whatever was there.  If you said you just duplicated the image, then the MAC address of the network card changes, the serial number of the CPU, and a bunch of other stuff happens.  If you said you moved it and try to run both images on the same network, you will have duplicate MAC addresses on your ethernet, and you will spend hours trying to straighten everything out.  You'll jump through even more legal hoops, technical hoops and you'll be very sorry by the time you get both systems running.

Now, here's what you say to Microsoft:

Tell them the truth.  Seriously.

I've said I just migrated old hardware to a virtual machine (because that's what I did) and will be disposing of the old system after wiping the drive.  They handle that fine as long as you still have your license key.  They just want to know why the system changed.

I've said that I scraped off the original hardware, installed Linux with VMware and put the OS back on the same hardware.  No problem.

I've said I duplicated the system and am now running both systems.  I have this, that and the other software on it and need licenses.  No problem, but frankly they'll suggest you buy more licenses so just go to CDW or wherever to buy just the license keys.

If you're using the software exclusively for software development and testing, then get a developer license.  Windows 2008 Server is like $30 USD.  Tell the truth!  You won't get a break on Windows 7 or Microsoft Office that way though.  In this case when you duplicate the software you need not only the license key but the developer ID that you got it under, and to tell them that you understand the terms of license and that you are not violating those terms.  To get your first developer license, you need to buy at least 5 titles from Microsoft simultaneously, not all of them need to be developer licenses I think.

Look.  Microsoft's biggest problem is that people take their expensive software and duplicated it.  They would rather hear about it and make it legitimate than just let it go.  If you're trying to be legitimate they will help you do that.  If you decide you can't afford it, then apologize and hang up.

And here's why the tech people are so easygoing:  The software update will find you out anyway.  You run two copies on the same license and sooner or later software update will mention that you seem to be running an illegitimate copy of Windows, or MS Office, or SQL Server.  You will have progressively more trouble getting your stuff to work, and sooner or later the grief will outweigh the price tag of the new software anyway.


Now as an aside, if you're gonna do this then I STRONGLY recommend that you install your "base" image, then make a backup.  Then perform software updates on that base image so it's absolutely current on everything, and it boots happily with NO ERRORS in the logs.  Then make an ADDITIONAL backup of it, marked accordingly.  Then install software on it that you will most likely use if you make a second active copy.  Then make a backup of that, marked accordingly.  Finally install the stuff you want for this specific image, and make everything be perfect, and then make yet another backup.  Don't name them 1 and 2 and 3.  Make names that make sense, put a README in there or whatever it takes.

Finally, MAKE BACKUPS OF THE %##@ THING!  You PROBABLY will trash it.  You have a fairly good chance of wanting another image, if you're like me.  That goes for Windows or Linux or anything else.  This is aside of backups of the application data you need backups of.

Sorry for writing a book.

---

### Post by 1clue on 2011-01-03
Oh yeah.

If you're running Windows on the box that will be Linux, then make a complete backup of it before you start.  If you ever want to sell it the original OS is critical, especially to the garage sale crowd.

---

### Post by skyzthelimit230 on 2011-01-04
> **1clue said:**
> I've done this.

If it's the OS that came with the PC then it won't even install on the VM, even if you're using the same hardware.  Those images are specific down to even a serial number range of what should be the same box.  I've had to order the original OS image too, to restore the original OS for some reason.  These images Will Not Work on a VM.  Start over from scratch, get your Windows CD, install it and put both the CD and license key in your safe and bury it in the back yard.

If you bought Windows 7 from a store, not as part of a PC, then it SHOULD work.  If you bought it as an upgrade then you need not only the Windows 7 disk but the one you upgraded from as well, and legally speaking neither of those can be active on any other machine once you fire up your VM.  IMO if you're gonna do it, then buy a new license unencumbered by an upgrade requirement.  WAY less trouble when it comes time to move the VM or whatever.

I've done this in different ways.  First, you take a ghosting tool like VMware Converter and follow the directions.  VMware Converter takes the image you want, converts it to VMware and then quits.  There is at least one tool per virtualization technology.

Second, you install a fresh image on the VM and install the OS from scratch, and re-install all your software.

Now, speaking about legality and what Microsoft will do:

No matter what your license says, Microsoft WILL allow you to install on a virtual environment.  They make their own virtualization scheme, so even if they never did before they surely do now.  I did my images with VMware.  Go to any modern company with 20 or more people in it, the IT shop is using virtual machines.  Most of your web hosting sites are on virtual machines.  VMs are here and they're gonna stay awhile, and nobody knows it better than Microsoft.

Legally speaking, a virtual image is absolutely no different from hardware.  You need a separate license for every piece of software on the VM which is not tied to any software on any other machine.  That includes Linux, by the way.  It's free, but there are conditions of use that you should be aware of.

Now, say you have that virtual machine up and running.  You shut it down and then copy the image to another location, and restart the machine.  What you have now is a backup.  The VM will know where it has been run from before, and if you change directories or processors or whatever it will ask you if you moved the image or duplicated it.  Tell the truth, it's easier than trying to fake it and will ultimately end in the same result anyway, you'll need new licenses.  As long as you only run the one image, the second image does not legally count.

If you trash your running image and delete it, you can copy the backup back over to the original location and start it, and it will be a normal startup.  No questions, no glitches, you just wind up back where you were when you made the backup.  I do it all the time for software development, it's a complete operating system rollback and it's far faster than anything else you might do.

Now you light up that second image, and suddenly you have created a new virtual machine, which means every software license requirement just doubled.  If it was Windows 7, then you now need two licenses for Windows 7, MS Office, etc whatever was there.  If you said you just duplicated the image, then the MAC address of the network card changes, the serial number of the CPU, and a bunch of other stuff happens.  If you said you moved it and try to run both images on the same network, you will have duplicate MAC addresses on your ethernet, and you will spend hours trying to straighten everything out.  You'll jump through even more legal hoops, technical hoops and you'll be very sorry by the time you get both systems running.

Now, here's what you say to Microsoft:

Tell them the truth.  Seriously.

I've said I just migrated old hardware to a virtual machine (because that's what I did) and will be disposing of the old system after wiping the drive.  They handle that fine as long as you still have your license key.  They just want to know why the system changed.

I've said that I scraped off the original hardware, installed Linux with VMware and put the OS back on the same hardware.  No problem.

I've said I duplicated the system and am now running both systems.  I have this, that and the other software on it and need licenses.  No problem, but frankly they'll suggest you buy more licenses so just go to CDW or wherever to buy just the license keys.

If you're using the software exclusively for software development and testing, then get a developer license.  Windows 2008 Server is like $30 USD.  Tell the truth!  You won't get a break on Windows 7 or Microsoft Office that way though.  In this case when you duplicate the software you need not only the license key but the developer ID that you got it under, and to tell them that you understand the terms of license and that you are not violating those terms.  To get your first developer license, you need to buy at least 5 titles from Microsoft simultaneously, not all of them need to be developer licenses I think.

Look.  Microsoft's biggest problem is that people take their expensive software and duplicated it.  They would rather hear about it and make it legitimate than just let it go.  If you're trying to be legitimate they will help you do that.  If you decide you can't afford it, then apologize and hang up.

And here's why the tech people are so easygoing:  The software update will find you out anyway.  You run two copies on the same license and sooner or later software update will mention that you seem to be running an illegitimate copy of Windows, or MS Office, or SQL Server.  You will have progressively more trouble getting your stuff to work, and sooner or later the grief will outweigh the price tag of the new software anyway.


Now as an aside, if you're gonna do this then I STRONGLY recommend that you install your "base" image, then make a backup.  Then perform software updates on that base image so it's absolutely current on everything, and it boots happily with NO ERRORS in the logs.  Then make an ADDITIONAL backup of it, marked accordingly.  Then install software on it that you will most likely use if you make a second active copy.  Then make a backup of that, marked accordingly.  Finally install the stuff you want for this specific image, and make everything be perfect, and then make yet another backup.  Don't name them 1 and 2 and 3.  Make names that make sense, put a README in there or whatever it takes.

Finally, MAKE BACKUPS OF THE %##@ THING!  You PROBABLY will trash it.  You have a fairly good chance of wanting another image, if you're like me.  That goes for Windows or Linux or anything else.  This is aside of backups of the application data you need backups of.

Sorry for writing a book.


wow, very comprehensive! :D

So, let me just get one thing cleared up: lets say I have a windows 7 partition now of about 120gigs (I know I will have to shrink the partition at some point).

And I create a backup image of that partition using Macrium reflect. Than, I do the total wipe of my HDD and install Ubuntu, than set up my windows 7 VM, and than I try to restore from that image. Are you saying that won't work unless I convert that image with VMWare converter? 

I appreciate the stress you put on the legal issues as it cleared up some other stuff for me. I will be contacting MS just prior to my taking the plunge.

Edit: I am using a windows 7 OEM installation disc I bought from the store

---

### Post by 1clue on 2011-01-04
> **skyzthelimit230 said:**
> wow, very comprehensive! :D

So, let me just get one thing cleared up: lets say I have a windows 7 partition now of about 120gigs (I know I will have to shrink the partition at some point).

And I create a backup image of that partition using Macrium reflect. Than, I do the total wipe of my HDD and install Ubuntu, than set up my windows 7 VM, and than I try to restore from that image. Are you saying that won't work unless I convert that image with VMWare converter? 

I appreciate the stress you put on the legal issues as it cleared up some other stuff for me. I will be contacting MS just prior to my taking the plunge.

Edit: I am using a windows 7 OEM installation disc I bought from the store

Chances are you will have driver issues if you do that.  The VMware image uses virtualized VMware hardware.  Your video card will not be the same, your network card will not be the same, your keyboard, mouse, whatever will not be the same.  The converter takes care of that.  AFAIK the same thing happens with most other virtualization systems.

Make your backup, you will want it in case you decide the whole thing was a mistake and want to restore back to the exact thing you had before.

Then run the converter and make your new image.  I think Microsoft won't really know what you're talking about until you are staring at the license key screen.  I never considered contacting them before, though, so maybe it would work your way.

---

### Post by skyzthelimit230 on 2011-01-04
I think if I convert the partition image into the virtual partition image using Macrium's tools than the drivers should carry over too as the drivers are installed within the C:\ Drive. I don't foresee drivers being an issue in this case if I use the image and import all the data into VirtualBox. Still, who knows what issues I'll run into....I've never used VirtualBox, but the only issues I really see being a problem are the actual virtualization hiccups.

At any rate, hopefully I wont have nasty surprises. I'm still in the process of looking over Macrium's tutorials and the like. They actually have a tutorialfor just this sort of thing which surprised me pleasantly:

[http://www.macrium.com/KB/KnowledgebaseArticle50005.aspx](http://www.macrium.com/KB/KnowledgebaseArticle50005.aspx)

---

### Post by 1clue on 2011-01-04
My point is that the virtual machine will probably not use the same drivers.  VMware at least doesn't expose the raw hardware, it is a driver on top of your native driver.  They only emulate one of anything, and it's a VMware driver.  You might  have an NVidia video card, but that driver won't work on the VM because the VM sees virtual hardware.  It's a VMware video card, if you're using VMware.  Yes, I know you're not but I suspect it's much the same for virtualbox.

---

