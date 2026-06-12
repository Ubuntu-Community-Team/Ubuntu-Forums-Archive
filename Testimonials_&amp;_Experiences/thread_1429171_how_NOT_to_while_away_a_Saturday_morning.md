---
title: "how NOT to while away a Saturday morning"
date: 2010-03-13
forum: Testimonials &amp; Experiences
---

### Post by fritzman on 2010-03-13
I had tried Ubuntu 9.10, and didn't like it.  Besides my negative impression of the boot screen, and the grease-monkey way we have to customize the grub screen, 9.10 had this extremely annoying habit if changing the drive designation of my external usb hard drive.  On one boot, it would be listed as /dev/sddx.  On another boot, it would be designated as /dev/sdbx.  Each time, I would edit fstab and get the mount points corrected, only to have it all to do over on the next boot.
Back to 9.04.
This morning, thinking that I ought to get ready for 10.04, and that it might be best to upgrade to 9.10, and then upgrade to 10.04, I did the upgrade.
It wouldn't boot, saying there was no such partition.  I was able to edit the boot entry, and get it booted, but, I couldn't get grub edited without considerable research and plugging away at it.
Finally, I thought I had it right, did $ sudo grub-install /dev/sda , and rebooted.  Grub was gone.  The MBR was gone.  Arrrgh!
OK.  I'll use the installer dvd to rescue.  I booted to the 9.10 installer dvd, scrolled down to rescue system, and on the menu, scrolled down to repair boot loader.
Error!  Could not install boot loader!
What!!??
I tried it again.... same results.
I tried the rescue mode using the mount /dev/sda2.  
Error!  Could not mount partition!
What!!???
Mutter!  Grumble! Grumble! Mutter!
I reinstalled 9.04 on  /dev/sda2, and booted to the new 9.04 install.  From there, I edited /boot/grub/menu.lst, and booted to my backup installation, a complete and recent copy of my main installation of 9.04 before doing the upgrade.  From there, I copied my backup of the root directory to /dev/sda2, did $sudo grub-install /dev/sda  , and voila!  Back to where I started at 6:00 this morning.
Elapsed time 8 hours, 15 minutes, minus 30 minutes for a couple of smoke breaks and 15 minutes for a bowl of cereal.
Question;
When 10.04 is released, can I upgrade directly from 9.04 into 10.04?  I hope so.  9.10 is just plain knugly!
Question;
Is the boot splash for 10.04 going to be as knugly as the one for 9.10?  I hope not.
Question;
Why does it seem that virtually ALL distributions go through a period when it seems that nothing works as it ought to?  I've experienced this with Ubuntu a couple of times, including this head-ache, as well as with Fedora, which seems to have been in the 'screwed-up-mode' for 4 or 5 releases, now, Mandriva, which hasn't had a really good release, in my opinion, since 8.0, and openSUSE, which seems to suck all the time.  Forget Gentoo!  I never have actually gotten an installation of Gentoo to completely install.
OK.  Now, I have vented.
Seriously, I really like Ubuntu, especially 9.04.  And I hope to be able to continue using Ubuntu.  I just don't know if I want the heart-ache of wrestling with a release for weeks before I get it to work.

owa

---

### Post by Jackzor on 2010-03-13
[http://ubuntuforums.org/forumdisplay.php?f=103](http://ubuntuforums.org/forumdisplay.php?f=103)

---

### Post by fritzman on 2010-03-13
I take it by your response that you think this should have been posted in the 'testimonials' section.  You're right.  It probably should have been posted there.
However, could you or someone answer the question of whether an upgrade to 9.10 will be necessary prior to upgrading to 10.04?
Another question might be, is it absolutely necessary to use grub2 instead of grub?  Grub works, and is easily edited to your liking.  Grub2 works, but is NOT easily edited, and seems to be a bit quirky.
owa

---

### Post by howefield on 2010-03-13
> **fritzman said:**
> However, could you or someone answer the question of whether an upgrade to 9.10 will be necessary prior to upgrading to 10.04?

You will need to go to 9.10, then 10.04.

You can go from LTS to LTS, eg 8.04 to 10.04, but other than that, you need to go sequentially.

Not sure about using grub instead of grub2, but there are a few boot managers you can use, you are not limited to any form of grub.

---

### Post by wojox on 2010-03-13
Yes you would have to upgrade to 9.10 to install 10.04. I went with a fresh install of 9.10 so get the benefits of ext4 and Grub2.

---

### Post by fritzman on 2010-03-13
Thanks for the responses.  I guess I'll have to suffer through a brief experience with 9.10, then, to get to 10.04, at which time, I just might switch to LTS for the stability.
I'll just hold off going to 9.10 till after 10.04 is released.
I love Linux, and will never go back to MS.  I first jumped to Linux with Fedora Core 1, and never looked back.  I really like the improvements made in the past couple of years to Ubuntu, and I would like to stay with it.
The only reason I went to grub2 is that doing so was strongly recommended and encouraged, as grub2 was the way of the future.  Personally, I liked grub just as it was, but I balked at ext4 too, but eventually moved to it.  Stubborn in my old age, I guess.
Again, thanks to both of you for your responses.
owa

---

### Post by howefield on 2010-03-13
> **fritzman said:**
> Thanks for the responses.  I guess I'll have to suffer through a brief experience with 9.10, then, to get to 10.04, at which time, I just might switch to LTS for the stability.

Of course, the other way of doing it is to clean install with 10.04.

I am running Lucid Lynx Alpha 3 on my main machine, (appears very stable and all my stuff is well protected through multiple backups and a disk image).

But when 10.04 is released, I'll clean install it to a hard disk partitioned into 4 /, /home, /swap and /Data. When future releases comes along I'll dual boot with 10.04 until the next LTS.

Lucid is shaping up to be a very fine release, one that I'd be happy to keep till the next LTS.

---

### Post by raymondh on 2010-03-13
> **howefield said:**
> 

Lucid is shaping up to be a very fine release, one that I'd be happy to keep till the next LTS.

Same here.  Will do a clean install and keep Lucid till the next LTS.  Currently set-up with root, /home, swap.  Data on another hd which also contains a second OS.

Best,

Raymond

---

### Post by fritzman on 2010-03-13
While we were away for a few minutes, I uninstalled grub2, et al, reinstalled grub, and rebooted.... all is well
I agree that clean installs are really the best way to go.  Although I was impressed at how relatively smooth the upgrade process seemed to be going from 9.04 to 9.10, I was annoyed that it arbitrarily uninstalled xscreensaver and gramps.
My experience has always been that a clean install tends to be much more stable than upgrades.
I'm curious about 9.10 changing the device nomenclature for the usb drive just with a reboot.  I don't want my desktop cluttered with the cute little partition mount icons, so I handle mounting of removable drives via fstab.  But, when the os arbitrarily renames the device simply with a reboot, that tore it for me.  9.10 had to go.
I'm looking forward to giving Lucid Lynx a run when it's released.
My layout is /dev/sda1 = swap, /dev/sda2 = /, /dev/sda5 = /home and a nearly identical layout for the usb drive, /dev/sdd1 = swap, /dev/sdd2 = /, /dev/sdd3 = home, and /dev/sdd4 = critical data backup storage.  I have a little cron script that backs up / on sda to / on sdd, and backs up /home on sda to /home on sdd weekly.  
Thanks, guys.
owa

---

### Post by TutAmongUs on 2010-03-13
> **fritzman said:**
>  Snippage...
Seriously, I really like Ubuntu, especially 9.04.  And I hope to be able to continue using Ubuntu.  I just don't know if I want the heart-ache of wrestling with a release for weeks before I get it to work.

owa


  Well, to halt that need...

 At the very least, get yourself a duplicate for that hard drive, and clone it or mirror it before fooling with these releases.  Probably a good idea anyway.  They are a dirt cheap investment that yields a full back-up.  Don't be like a lost dude that won't look at a map (the female critique) ;)   Dive right into that full back-up realm!

  I did not lose any data as a result of my 'incident', but I need to point at grub on the partition the OS is on and retain MY boot loader on the MBR as the pointing code and everything about the MBR as well. As in NEVER touch it.  It is not required.

 I hope they listen.

---

### Post by fritzman on 2010-03-13
I have a little cron script that backs up / on sda to / on sdd, and backs up /home on sda to /home on sdd weekly. 

So, that back-up ritual has saved me many times.  How the MBR got borked remains a mystery, and why the rescue program on the install dvd doesn't work is problematic.  
And, why 9.10 changes the device nomenclature is also mysterious.
But..... A clean install of 10.04, when it is released, will be the next project.  I hope it is as good as you folks have touted it to be.
Thanks for the input.
owa

---

### Post by Sef on 2010-03-13
> I take it by your response that you think this should have been posted  in the 'testimonials' section.  You're right.  It probably should have  been posted there.

Agreed, so moved.

---

### Post by louieb on 2010-03-13
lol - this old man did not care for v9,10 - got rid of it and have has been using 10.04 alpha since Dec. (Dual boot my laptop with 9.04) Think your going to like it. 10.04 alpha still has a few bugs - but its only got to where it would not boot at all just once - not bad for an alpha stage. 

I am in the clean install camp - when the final comes out I'll do a clean install over the alpha version.

---

