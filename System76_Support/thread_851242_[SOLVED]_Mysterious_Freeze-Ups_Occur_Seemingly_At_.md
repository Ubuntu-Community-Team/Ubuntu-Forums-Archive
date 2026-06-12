---
title: "[SOLVED] Mysterious Freeze-Ups Occur Seemingly At Random"
date: 2008-07-06
forum: System76 Support
---

### Post by tuebinger on 2008-07-06
Lately my laptop (Daru2 model 1221) has been freezing up seemingly at random and it's a total system lock-up.  I've tried Ctrl+alt+Esc, Ctrl+alt+F1, Ctrl+alt+Del -- none of these key combos work to get it to unfreeze.  The trackpad is non-responsive.  This seems only to happen when I'm using Firefox (I'm using 2.0.0.15), but I don't know if it's Firefox' fault or something else.  It's occurring more and more (happened twice yesterday).  All I'm left with is to push and hold down the power button for 5 seconds to restart the computer.  Is this bad for my system to restart my laptop this way?  Does anyone know what might be happening here, or what I can do to remedy the situation?  Thanks!

---

### Post by Paulr-55 on 2008-07-07
My Ratel desktop exhibited these same symptoms (total lock-ups at random) and it turned out to be an overheating video card. S76 installed a fan on it under warranty. Don't know if this is helpful, but I too suspected Firefox for a while, but it was coincidental because I spend a lot of time in the browser.

---

### Post by Nkosi on 2008-07-07
My Gazv3 laptop has the same problem. I always have Firefox loaded up, too, hmm. When I run dmesg it says my ata1 is frozen. After about 5-10 seconds, though, it unfreezes itself. But yes, it seems to be a random whenever thing that began after my first major upgrade.

---

### Post by jdb on 2008-07-07
> **tuebinger said:**
> Lately my laptop (Daru2 model 1221) has been freezing up seemingly at random and it's a total system lock-up.  I've tried Ctrl+alt+Esc, Ctrl+alt+F1, Ctrl+alt+Del -- none of these key combos work to get it to unfreeze.  The trackpad is non-responsive.  This seems only to happen when I'm using Firefox (I'm using 2.0.0.15), but I don't know if it's Firefox' fault or something else.  It's occurring more and more (happened twice yesterday).  All I'm left with is to push and hold down the power button for 5 seconds to restart the computer.  Is this bad for my system to restart my laptop this way?  Does anyone know what might be happening here, or what I can do to remedy the situation?  Thanks!

When Hardy first came out I installed the 64 bit version & had a lot of problems with firefox & flashplayer .
I then installed the 32 bit version the problems went away.
Just a thought, all the 64 bit problems may have been cleared up by now.

I don't think this is your problem, but I've noticed that when mlocate runs (daily in cron) it can really slow things down.

jdb

---

### Post by crichell on 2008-07-07
After you recover from a freeze can you use the system76 driver to create a log archive and attach it for us?

System > Administration > System76 Driver

Click the Support tab and click "Create" to create a log archive in your home folder.

Thanks

> My Gazv3 laptop has the same problem. I always have Firefox loaded up, too, hmm. When I run dmesg it says my ata1 is frozen. After about 5-10 seconds, though, it unfreezes itself. But yes, it seems to be a random whenever thing that began after my first major upgrade.

This was a problem in Fiesty with ata_piix. What version of Ubuntu are you on?

---

### Post by tuebinger on 2008-07-07
Will do.  Next time it freezes up I'll post the results.

---

### Post by tuebinger on 2008-07-07
This latest freeze occured when I was away from the computer.  Attached is the logs.tar report.

---

### Post by Nkosi on 2008-07-08
I'm currently using Ubuntu 7.10 (Gutsy Gibbon).
Of course I should have added this information, my bad -- my first time to do this.

I absolutely love Linux and what you guys are trying to do at Sys76.

---

### Post by thomasaaron on 2008-07-08
Nkosi, your problem is related to a firmware problem in your CD drive. Please contact me at support(at)system76(dot)com for the fix.

---

### Post by thomasaaron on 2008-07-08
Tuebinger,

Here is your problem...

> Jul  7 16:05:11 stephen-laptop kernel: [ 4222.367329] npviewer.bin[7877]: segfault at 00000000f5c9c030 rip 00000000f7928550 rsp 00000000fff9a7ac error 4

This post is similar...

[http://ubuntuforums.org/showthread.php?t=647961](http://ubuntuforums.org/showthread.php?t=647961)

It looks to me like Flash is causing the problem.

We're not really seeing this issue at large, though. How did you install Flash on your computer?

---

### Post by tuebinger on 2008-07-08
I first tried to install it using the method on the Adobe download page ([http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)) but it wasn't working, Then you told me to try:  sudo apt-get install flashplugin-nonfree   in this post: [http://ubuntuforums.org/showthread.php?t=827658](http://ubuntuforums.org/showthread.php?t=827658)

Could my first attempt to manually download the flash plugin be causing the problem?

---

### Post by thomasaaron on 2008-07-09
Could be.

We can try to delete anything remaining from the original adobe install and then re-installing flash.

Please post the output of...

ls .mozilla

Also, is there any relationship between having Gmail open and the freezing?

---

### Post by tuebinger on 2008-07-09
Here is the output of ls .mozilla:

stephen@stephen-laptop:~$ ls .mozilla
extensions  firefox
stephen@stephen-laptop:~$ 

I don't  leave Gmail open -- I usually close it after checking my mail.  I do leave my eBay page open to keep track of my listings.

---

### Post by thomasaaron on 2008-07-09
There's a pretty good chance this is the pulseaudio bug that causes problems with flash. It's also been reported as being problematic with gmail and other websites. Try this...

sudo apt-get remove libflashsupport

...and see if the freezing occurs.

---

### Post by tuebinger on 2008-07-09
I tired sudo apt-get remove libflashsupport and apparently it isn't there.  Here's the ouput:

stephen@stephen-laptop:~$ sudo apt-get remove libflashsupport
[sudo] password for stephen:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libflashsupport
stephen@stephen-laptop:~$ 

Must be something else?

---

### Post by thomasaaron on 2008-07-09
Try installing it.

sudo apt-get install libflashsupport

---

### Post by tuebinger on 2008-07-09
It didn't install, either.

stephen@stephen-laptop:~$ sudo apt-get install libflashsupport
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libflashsupport
stephen@stephen-laptop:~$

---

### Post by tuebinger on 2008-07-15
Well, I've been using Opera for the last 5 days and haven't had a problem with a complete system lock-up during that time.  I don't know if this has anything to do with the flash problem or not, because Opera uses flash too.  Maybe it handles flash better??  I don't know.  I'm just happy it's not freezing everyday now!

---

### Post by Nkosi on 2008-07-16
My Gazv3 Gutsy 32-bit laptop runs rock solid stable now and its speed has doubled, at least. Your firmware fix is good!

---

### Post by tuebinger on 2008-07-26
I think I can safely mark this thread as solved, since I have since reinstalled 7.10 again and installed flash using:

sudo apt-get install flashplugin-nonfree

So far so good.  No system freezes. Very stable, even with Firefox and GMail open. I think I was right about it being something to do with the way I tried to install flash originally. It's working, I believe, because I used the apt-get command, as you had originally suggested,  instead of the method described on the Adobe website. 

Now if I could only learn to stop messing with my system...   ](*,)

---

### Post by darkknight045 on 2008-07-28
> Now if I could only learn to stop messing with my system...  

Come now, why would you be using Linux if you weren't going to mess with your system? :)

---

### Post by tuebinger on 2008-07-28
> **darkknight045 said:**
> Come now, why would you be using Linux if you weren't going to mess with your system? :)

Come to think of it, I *do* have this seemingly uncontrollable urge to to mess with the system!!  It must be some strange Linux-user's affliction...

---

### Post by thomasaaron on 2008-07-28
Yes, it's called "fiddle-itis." I have it too. ](*,)

But then, I'm *paid* to have fiddle-itis. What's YOUR excuse? :lolflag:

---

### Post by tuebinger on 2008-07-28
> **thomasaaron said:**
> Yes, it's called "fiddle-itis." I have it too. ](*,)

But then, I'm *paid* to have fiddle-itis. What's YOUR excuse? :lolflag:

 That must be it, I have "fiddle-itis."  I have no excuse, though :( I think I'm a hopeless masochist when it comes to Linux...:biggrin:

---

### Post by steveneddy on 2008-07-29
I grew tired of fiddling when I desired reliability and stability over the cool factor.

---

### Post by jdb on 2008-07-30
> **steveneddy said:**
> I grew tired of fiddling when I desired reliability and stability over the cool factor.

I've got one bootable partition for reliability & stability and many for fiddle-itis.

It's a lot more fun to smoke a partition when you have another to boot to. :popcorn:


jdb

---

### Post by walkeraj on 2008-07-30
> **jdb said:**
> I've got one bootable partition for reliability & stability and many for fiddle-itis.

It's a lot more fun to smoke a partition when you have another to boot to. 

jdb

Of course, a lot of my knowledge has also come from the necessity of learning how to restore the installation I just borked to hell and back.  Just recently, I did something stupid to a headless BSD box, and ended up with just a keyboard.  Nothing like blind-typing regexes into vim with only beeps to guide you.

Oh and, in case you're wondering, I take no pride from that. :)

---

