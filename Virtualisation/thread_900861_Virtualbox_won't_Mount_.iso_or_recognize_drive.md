---
title: "Virtualbox won't Mount .iso or recognize drive"
date: 2008-08-25
forum: Virtualisation
---

### Post by dirtydata on 2008-08-25
First off, thank you for taking the time to look at this post.

I'm trying to install a copy of Windows XP using Virtualbox (as you could have guessed from the title).  I have been running into some an error reading "FATAL: Could not read from the boot medium! System halted."

[IMG]http://img411.imageshack.us/my.php?image=screenshotwindowsxprunnwj6.png[/IMG]

Here are some of my settings:

[IMG]http://img509.imageshack.us/img509/6179/screenshotsunxvmvirtualeq2.png[/IMG]

[IMG]http://img524.imageshack.us/img524/232/screenshotwindowsxpsettkz1.png[/IMG]

[IMG]http://img505.imageshack.us/img505/8738/screenshotwindowsxpsettsd4.png[/IMG]

I've got a real Windows XP disc but when this is in the drive, Virtualbox doesn't recognize it.

I'm basically always online and up for giving any information upon request.  I'm relatively new to Ubuntu but I'm not knew to Unix.

Thank you in advance!

Have a great day/night!

-DirtyData

---

### Post by tuxxy on 2008-08-25
Weird, if it did previously work maybe you should check the permissions of the virtual hard disks 

They are usually located here,

**/home/username/.VirtualBox/Machines**

make yourself the current user owner of all the files and retry virtual

---

### Post by dirtydata on 2008-08-25
> **tuxxy said:**
> Weird, if it did previously work maybe you should check the permissions of the virtual hard disks 

They are usually located here,

**/home/username/.VirtualBox/Machines**

make yourself the current user owner of all the files and retry virtual

Below is a screenshot of my current vboxusers permissions.

[IMG]http://img207.imageshack.us/img207/5624/screenshotgroupvboxusernz5.png[/IMG]

-DirtyData

---

### Post by dirtydata on 2008-08-25
I've installed vmware workstation and player.

I'm getting the same error with vmware player not recognizing my cd drive.  Here are the messages I'm getting.

[IMG]http://img83.imageshack.us/img83/3701/screenshotwindowsxpproftg6.png[/IMG]

[IMG]http://img300.imageshack.us/img300/3583/screenshotvmplayerba8.png[/IMG]

-DirtyData

---

### Post by Living2007 on 2008-08-25
Do you have any virtual CD programs running. Cause my VMware doesn't pickup my Windows CD's (when it is in my real drive) if Daemon Tools is running without a Windows CD)

---

### Post by dirtydata on 2008-08-25
> **Living2007 said:**
> Do you have any virtual CD programs running. Cause my VMware doesn't pickup my Windows CD's (when it is in my real drive) if Daemon Tools is running without a Windows CD)

I don't have any virtual drives on that I know of.  I've never set one up on this computer. 

When I put the windows cd in I get errors and when I mount an image file using gmount I get errors.

[IMG]http://img84.imageshack.us/img84/4097/screenshotgmountisosa2.png[/IMG]

-DirtyData

---

### Post by dirtydata on 2008-08-26
I am just guessing here but the issue I'm having might have something to do with the fact that I mount my cdrom drive it is directing to /dev/scd0 and not /media/cdrom0.  This is pictured in the original post.

Anyone have any other ideas on how this is or isn't related to my issue?

-DirtyData

---

### Post by drulinx on 2008-11-12
Ok guys so I'm no expert but I've been running LINUX for quite some time now and am very familiar with Virtualbox.  The easiest way to solve these problems is to follow this guide [http://lifehacker.com/367714/run-windows-apps-seamlessly-inside-linux](http://lifehacker.com/367714/run-windows-apps-seamlessly-inside-linux) which I always refer to when setting up a new VM.  On a side note lifehacker.com is an excellent source for linux tips and just awesome in general.  Hope this helps someone, I know it worked like a champ for me.

---

### Post by killer_d76 on 2008-11-12
it can be a cause of badly scratched CD or if you have it in .iso image, i would suggest you to redo it and see if that should work.. try running a different .iso image and see if you get the same error.

---

