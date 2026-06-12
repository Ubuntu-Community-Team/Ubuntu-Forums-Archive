---
title: "Help With Infected WinVista"
date: 2009-12-16
forum: The Cafe
---

### Post by ftabor on 2009-12-16
I have a friend with a Windows Vista box that, due to her propensity to click on, download, and log into any and every thing she comes across, has a box that is thoroughly rooted, owned, and otherwise terminally infected.

Other than using the restore disk, ( she didn't create one before it got "sick",) what is the best plan using a Live Ubuntu CD to try to clean it up?  What AV or combination would be the best to use and at least preserve her data?

I'm posting to this forum because it really isn't an Ubuntu security problem.  If it needs to be moved to another forum, I would appreciate that also.

Thanks in advance for any suggestions/help.

---

### Post by n0glu3 on 2009-12-16
Can you boot into Vista?

---

### Post by dragos240 on 2009-12-16
Crap. Man, that sucks. I was infected with vista too. That is one awful virus.

---

### Post by ftabor on 2009-12-16
Her system or mine?  Hers, no.  It has crashed.

---

### Post by n0glu3 on 2009-12-16
> **dragos240 said:**
> Crap. Man, that sucks. I was infected with vista too. That is one awful virus.

:rolleyes:

---

### Post by tom66 on 2009-12-16
Boot from Ubuntu LiveCD, mount NTFS drive, copy data onto a USB stick or USB hard drive or another internal hard drive, reboot. Then reinstall.

There is virtually no way for you to remove that kind of infection other than a reinstall. It's probably tightly embedded itself into the operating system.

---

### Post by n0glu3 on 2009-12-16
> **ftabor said:**
> Her system or mine?  Hers, no.  It has crashed.

What happens exactly?

---

### Post by ftabor on 2009-12-16
There's nothing to reinstall with.  She didn't make the recovery disks.  Copying the data will probably bring virii with it.

I was hoping that I could use ClamAV or AVG for Ubuntu and mount the drive and try to disinfect it.

---

### Post by n0glu3 on 2009-12-16
Doh. Ok, boot up a LiveCD. mount the Vista drive and delete everything in the C:/Windows/Prefetch folder. Then boot Vista into safe mode and uninstall every program you can.

---

### Post by dragos240 on 2009-12-16
You could mount the drive, copy the data, and scan the data. That's what I'd do.

---

### Post by ftabor on 2009-12-16
> **n0glu3 said:**
> What happens exactly?

I'm not sure.  She would be your typical luser, "It won't boot! Something flashes across the screen and then nothing happens."  

I haven't been there to look at it yet.  But she has been complaining of slowness, browsing is sluggish, constant modem activity, popups, etc. I asked her about virus protection and she said, "Huh?"  She made noises about taking it to the Geek Squad, and I may just let her, except my ego won't let me.

---

### Post by MooPi on 2009-12-16
Wait before you start any destructive procedures, what is the make and type of computer. There may be a restore partition available.

---

### Post by ftabor on 2009-12-16
> **n0glu3 said:**
> Doh. Ok, boot up a LiveCD. mount the Vista drive and delete everything in the C:/Windows/Prefetch folder. Then boot Vista into safe mode and uninstall every program you can.

I'll give that a try, as well as trying to scan drive.  Thanks.

---

### Post by n0glu3 on 2009-12-16
> **ftabor said:**
> I'm not sure.  She would be your typical luser, "It won't boot! Something flashes across the screen and then nothing happens."  

I haven't been there to look at it yet.  But she has been complaining of slowness, browsing is sluggish, constant modem activity, popups, etc. I asked her about virus protection and she said, "Huh?"  She made noises about taking it to the Geek Squad, and I may just let her, except my ego won't let me.

Are you experienced with removing Windows viruses? It doesn't sound like you are.

---

### Post by ftabor on 2009-12-16
> **MooPi said:**
> Wait before you start any destructive procedures, what is the make and type of computer. There may be a restore partition available.

Yes, I'm sure there is a restore partition there, but I don't know if I can create a restore disk while everything else is infected.  I'm not sure what she has.  As I said, luser.

---

### Post by ftabor on 2009-12-16
> **n0glu3 said:**
> Are you experienced with removing Windows viruses? It doesn't sound like you are.

Yes, I ran Windows up until about a year ago.  Most aren't too bad.  I'd say she probably has more problems with Trojans than virii, but I need to get down there and take a look.  It's a half days travel.

---

### Post by n0glu3 on 2009-12-16
> **ftabor said:**
> Yes, I ran Windows up until about a year ago.  Most aren't too bad.  I'd say she probably has more problems with Trojans than virii, but I need to get down there and take a look.  It's a half days travel.

Lol ok. You may also want to remove everything from %TEMP% too. Also, make sure if you can that you limit the startup programs to Microsoft ones only.

---

### Post by NoaHall on 2009-12-16
> **n0glu3 said:**
> Lol ok. You may also want to remove everything from %TEMP% too. Also, make sure if you can that you limit the startup programs to Microsoft ones only.

F8 on start-up, select safe mode, type in "msconfig", go to services tab, tick "hide all microsoft serivces", click disable all, go to startup tab, disable all, click apply, restart normally.

---

### Post by ftabor on 2009-12-16
> **n0glu3 said:**
> Lol ok. You may also want to remove everything from %TEMP% too. Also, make sure if you can that you limit the startup programs to Microsoft ones only.

That's usually the first thing I do when I can get my hands on a system.  There is way too much stuff running on startup.

---

### Post by ftabor on 2009-12-16
> **NoaHall said:**
> F8 on start-up, select safe mode, type in "msconfig", go to services tab, tick "hide all microsoft serivces", click disable all, go to startup tab, disable all, click apply, restart normally.

That's provided I can get it to boot at all.

---

### Post by MooPi on 2009-12-16
Every brand of computer has a Function key to boot to restore. Look up the make and model and research which key to use at start up.

---

### Post by n0glu3 on 2009-12-16
Have you thought about a remote connection into her machine?

---

### Post by cariboo on 2009-12-16
I'd suggest backing up any important data, and then use the restore partition, to make it just like new again. From the way it sounds that's about all you can do, unless you are charging her to clean things up.

Free only gets the quickest and easiest fix.

---

### Post by MooPi on 2009-12-16
Remote is a moot point if it won't boot

---

### Post by n0glu3 on 2009-12-16
> **MooPi said:**
> Remote is a moot point if it won't boot

He said himself he wasn't certain of what she meant by that.

---

### Post by ftabor on 2009-12-16
> **n0glu3 said:**
> Have you thought about a remote connection into her machine?

Without her being able to boot the machine, I don't think I can get in. I'm not that familiar with Remote connections.  I tried that several times with my own stuff when I ran Windows and never had much success with it.

---

### Post by User3k on 2009-12-16
After you get things cleaned up for her, you might want to get her to install these things if she is running Windows. You probably already know about them or at least some of them. I have used many of these for years when I use to use Windows and I still recommend them for all the Windows users I know.

AVG Free
ZoneAlarm Free
Ccleaner
Spybot

For browsers, add-ons - 
Ad-Block
Flash Block
noscript


Or you can get her to just use Linux and get rid of four out of the seven above, lol.

---

### Post by n0glu3 on 2009-12-16
> **ftabor said:**
> Without her being able to boot the machine, I don't think I can get in. I'm not that familiar with Remote connections.  I tried that several times with my own stuff when I ran Windows and never had much success with it.

Well if you can just help her enough over the phone to get it to boot, then you may well be able to remote connect.

---

### Post by ftabor on 2009-12-16
> **cariboo907 said:**
> I'd suggest backing up any important data, and then use the restore partition, to make it just like new again. From the way it sounds that's about all you can do, unless you are charging her to clean things up.

Free only gets the quickest and easiest fix.

Well, I'm hoping it won't be exactly free, but that's a thread best pursued in another venue. :-&

---

### Post by ftabor on 2009-12-16
You guys are getting ahead of me, but I'm going to try a combination of everything to get it working again.  Thanks for the suggestions and the help.

I'd love to convert her to Linux, but I doubt that will happen in the near future.  I'm going to leave her a laptop with 9.10 on it and Open Office for her business travels and maybe I can change her mind.

---

### Post by n0glu3 on 2009-12-16
Good luck.

---

### Post by Exodist on 2009-12-16
> **ftabor said:**
> I have a friend with a Windows Vista box that, due to her propensity to click on, download, and log into any and every thing she comes across, has a box that is thoroughly rooted, owned, and otherwise terminally infected.

Other than using the restore disk, ( she didn't create one before it got "sick",) what is the best plan using a Live Ubuntu CD to try to clean it up?  What AV or combination would be the best to use and at least preserve her data?

I'm posting to this forum because it really isn't an Ubuntu security problem.  If it needs to be moved to another forum, I would appreciate that also. Not really sure but you may be able to get one from MS alternative media for $9.95.

Thanks in advance for any suggestions/help.


Just completely reinstall Vista from disc. If she doesnt have one call the PC manufactor and get them to send you one. May take up to 10 days to arrive.

Then just make sure she has all her updates, Windows Defenseless is turned on and a good AV program like Avast is installed. 

Thats about all you can do. Nothing can help an idiot that impulsively clicks on everything.

---

### Post by User3k on 2009-12-16
Let us know how it turns out.

---

### Post by alexfish on 2009-12-16
> **ftabor said:**
> I have a friend with a Windows Vista box that, due to her propensity to click on, download, and log into any and every thing she comes across, has a box that is thoroughly rooted, owned, and otherwise terminally infected.

Other than using the restore disk, ( she didn't create one before it got "sick",) what is the best plan using a Live Ubuntu CD to try to clean it up?  What AV or combination would be the best to use and at least preserve her data?

I'm posting to this forum because it really isn't an Ubuntu security problem.  If it needs to be moved to another forum, I would appreciate that also.

Thanks in advance for any suggestions/help.


Ubuntu not a problem

 But a headache for vista

   it's a problem of their own making:guitar:

 also things get slowed down with this:lolflag:

---

### Post by lisati on 2009-12-16
Maybe a comibination of the ideas so far will be the way to go: using an Ubuntu LiveCD to clean up, scan and backup what you can, then using the restore partition to do a fresh install (assuming the partition isn't messed up), and then making a restore disk a.s.a.p.

---

### Post by munky99999 on 2009-12-16
> **ftabor said:**
>  what is the best plan using a Live Ubuntu CD to try to clean it up?  

Use only part of the disk while installing ubuntu.

---

### Post by baddog144 on 2009-12-16
I read the thread title as "Help, infected with WinVista"
I wouldn't have been surprised.

---

### Post by Chame_Wizard on 2009-12-16
Mount the HDD on your *buntu desktop to check on infections.:popcorn:

---

### Post by gletob on 2009-12-16
One another note, Hello there my fellow Virginian.  

I agree with the idea of booting the livecd and deleting the prefetch folder & Temp files.

---

### Post by alexfish on 2009-12-16
> **User3k said:**
> Let us know how it turns out.

Up Side Down And Inside Out Here We Go Again   :guitar:

When They Made That Song They Must Must Have Used MicroSoft:confused:

Name The Year And The Group\\:D/

---

### Post by alexfish on 2009-12-17
> **ftabor said:**
> I'm not sure.  She would be your typical luser, "It won't boot! Something flashes across the screen and then nothing happens."  

I haven't been there to look at it yet.  But she has been complaining of slowness, browsing is sluggish, constant modem activity, popups, etc. I asked her about virus protection and she said, "Huh?"  She made noises about taking it to the Geek Squad, and I may just let her, except my ego won't let me. Found a CURE  
				* 					 						[Last edited by alexfish]("http://ubuntuforums.org/posthistory.php?p=8513125");*

---

### Post by ftabor on 2009-12-20
I never could reproduce her boot errors.  I booted the system on an Ubuntu Live CD, mounted her drive, then scanned with ClamAV and AVG.  Took a couple of hours but they cleaned a lot of stuff out.

I also isolated the data she needed and put it on a USB stick and scanned it with AVG in my VirtualBox Windows, it was clean.

I did mount the recovery partition and scanned it and it was clean, so I managed to boot her box to the recovery partition and formatted and reinstalled her OS.  I did all this with the Network connection removed so there was no possibility of any thing hidden calling home.

The next thing was to uninstall Norton and install AVG and scan everything.  Second was to make a set of recovery disks for the next go 'round.  Then scanned the USB stick again before transferring the data back and got everything back up and running.  Only took about 4 hours.  So I'm ready for the next time which I'm sure will occur despite anti-virus/spyware protection and attempts at education.  

So, again, thanks for the suggestions and ideas.

---

