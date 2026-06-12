---
title: "Vista / Acronis HD partition resizer error"
date: 2008-12-24
forum: Windows
---

### Post by OinkOink2 on 2008-12-24
[FONT="Tahoma"]Greets to the Ubuntu community,

I have gotten myself into a pickle. I'm a novice to Ubuntu/Linux; today I aimed to install Ubuntu 8.10 on my laptop with Vista - a dual-boot.

I really want to convert over to Linux and probably was a bit to eager to install it...

Anyway this is what I have done:

[INDENT][LIST]
[*][COLOR="Navy"]Used Acronis Disk Director to RESIZE C:\ (which I know is stupid because Vista comes with the resizing/partitioning facilities as part of the OS!...)

[*]OK'd the resize, but Acronis required rebooting to begin

[*]I forgot that I had Ubuntu 8.10 already in the drive which because I already have my BIOS set to boot from CD, upon rebooting instead of executing Acronis' scheduled resizing of C:\ booted into Ubuntu instead.

[*]I realised too late and shut the laptop down by pressing the power button (bad move? quite possibly!)

[*]Turned the Pavillion back on and ejected Ubuntu - like clockwork Acronis' scheduled resizing begun.

[*]After resizing the system rebooted [definately normal]

[*]Upon rebooting, after the BIOS screen, a black empty screen followed and Vista would not load. After a few more times restarting and booting back into Vista to no Avail I got the Vista Repair Disk out.

[*]I booted into the Repair disk and repaired C:\

[*]Upon rebooting again the Windows and load bar came up -unlike previously- but now I got a bluescreen saying something along the lines of "boot into Windows and 'safely remove' any [external] devices connected to the computer" with one of those "Xc00000" error numbers. Basically the bluescreen was about not being able to "detect a device" or something. I apologise for being vague - this was a while ago now.

[*]I booted back into the Vista repair disk and continued to "repair" C:\ a further couple of times.

[*]I seemed to get somewhere because I didn't get the bluescreen anymore and Acronis came back to the final stage of its operation (at least I hope so). Now however the problem is that upon being presented with the Windows logo and load bar, Acronis precedes this with "Acronis AUTOPART" operation.

[*]After the Acronis "AUTOPART" the mouse comes on with a black screen. Usually the black screen would be the last stage in loading Vista before the LOGON screen however the logon screen never shows anymore[/COLOR].
[/LIST][/INDENT]
To be able to post this I am using Ubuntu LiveCD. Hopefully you guys will be able to shed some light onto a solution for me. Fortunately I did back up my DATA and important documents before using Acronis to resize C:\ but the problem definately seems that the Acronis AUTOPART operation is caught in a loop.

Is there any way to stop this? And get back into Vista?

I have had to force mount C:\ in Ubuntu to make sure my files are still there - which they are. Is the fact that I have had to force mount C:\ reflective of a problem?

Please help guys.

Thanks.[/FONT]

---

### Post by gettinoriginal on 2008-12-24
Well, if I understand you right, you have already partitioned your HD.  You have also mentioned that your bios are set to boot from CD first.  So:
Insert the Live CD, and turn your computer off.  Restart your computer, and you should get the live CD.  Click install.  Not sure where you will go from there, as one of the problems of the windows mindset is that the HD must be formatted to install on it.  The Live CD has a partitioning editor on it, so it would have directed you to options for partitioning.  You should be able to just tell it to install on the formatted partition that you created.   :P

---

### Post by OinkOink2 on 2008-12-24
Thanks for your reply, but there is still the fact that Vista isn't booting into Vista properly - and it's really bugging me.

I've since had a bit of luck with the things mentioned in this post: [http://www.wilderssecurity.com/showthread.php?t=199361]("http://www.wilderssecurity.com/showthread.php?t=199361") regarding a similar situation some chap found themselves in after resizing their hard drive with Acronis.

I have renamed **[COLOR="Blue"]AutoPartNt.exe[/COLOR]** and **[COLOR="Blue"]AutoPartNt.let[/COLOR]** to **[COLOR="Blue"]AutoPartNt.exe.OLD[/COLOR]** and[COLOR="Blue"]** AutoPartNt.let.OLD**[/COLOR] and this has had the *welcomed* effect of not getting the 'Acronis AUTOPART' operation which I believed to be continuously in loop, however my logon screen just wont load up!

I think the solution definately lies in this thread. 

I've tried searching for the following registry key that the chap in that above post was recommended to correct by navigating over to C:\WINDOWS\System\System32 and running "regdt32.exe" by using Wine. Unfortunately I cannot find the reg key: **[COLOR="Indigo"]HKEY_LOCAL_MACHINE\system\currentcontrolset\control\session manager[/COLOR]**and therefore can not find the value for the **BootExecute** entry which after following the recommended correction, was the solution for the fellow in that post.

Hence I'm still at a loose end. [LIST]
[*]Does anyone have a solution? 
[*]And how come I can't run "msconfig" to check the boot perameters and start up entries for Vista through Wine? 
[*]Also, why is Wine unable to view that reg key assuming it would be there - I get the impression I'm unable to see every registry entry?

--Note, I really would like to correct Vista before installing Ubuntu! 

Thank you.
[/LIST]

---

### Post by gettinoriginal on 2008-12-24
I'm not proficient enough to understand what you may have done, but it sure sounds like you have corrupted or negated your "grub".  I have never used Acronis, when I dual booted, I just inserted the Live CD and went from there without problem.  So therefore, i will back out and hope someone with more knowledge of your problem will come along.  Good luck :P

---

### Post by OinkOink2 on 2008-12-24
No prroblem, your helpful intentions are much appreciated anyway.

However, I've an UPDATE:

I couldn't find the registry key [see above] and the subsequent value for key entry "BootExecute" so I've experimented a little - I've _made_ one.

I'll post the results up shortly - will it solve the problem or wont it?...exciting stuff...

---

### Post by vandorjw on 2008-12-24
Since you made a backup of your Data already, isn't the quickest path of action to reformat your drive, and when creating the vista partitions, create one for Ubuntu right away also.

Then, install ubuntu.

------------------------------------------------------------------
So far what you have told us, is that you are now able to boot into Vista. First thing I would do is unistall your partitioning program. (Its not needed anyways.)

If your registry is borked, run the one care live tool safety scanner, (uncheck scan for viruses and all other useless things, and only let it scan and fix registry problems.)

Good luck.

-CC7gir

---

### Post by ugm6hr on 2008-12-25
Moved to Windows forum.

This issue requires Vista / Acronis knowledge - hopefully users will be able to help here.

---

### Post by tsali on 2008-12-25
I've btdt

The partition resize damaged your Vista install. You will have to clean re-install. You may be able to retrieve user data from the drive with a live CD if you're lucky.

If you want a solid dual boot system, re-install Vista (on the ENTIRE hard disk), install all updates, run defrag, THEN use the WUBI installer to install Ubuntu.

Works wonderfully.

Maybe someone smarter than me can tell you another way, but I don't know of one.

Put Acronis away. You'll do more damage with it than it's worth.

---

### Post by OinkOink2 on 2008-12-25
Well in response to my update, it didn't work.

Thanks for the help anyway guys. Fortunately I've got the backup discs and I'll just do the above.

---

### Post by OinkOink2 on 2008-12-25
> **OinkOink2 said:**
> Well in response to my update, it didn't work.

Thanks for the help anyway guys. Fortunately I've got the backup discs and I'll just do the above.

EDIT - Tsali, do you think I should FORMAT C:\ with Ubuntu's GParted first, and then clean reinstall from my recovery discs?

Thanks

---

### Post by tsali on 2008-12-25
> **OinkOink2 said:**
> EDIT - Tsali, do you think I should FORMAT C:\ with Ubuntu's GParted first, and then clean reinstall from my recovery discs?

Thanks

Only if you have trouble installing from your restore disks.

Your restore disks will do a clean format of the entire drive. Doesn't matter what's one there to start with.

---

