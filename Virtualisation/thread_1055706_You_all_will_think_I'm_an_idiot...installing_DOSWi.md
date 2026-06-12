---
title: "You all will think I'm an idiot...installing DOS/Win95 in VirtualBox"
date: 2009-01-31
forum: Virtualisation
---

### Post by dbsoundman on 2009-01-31
OK, I know, I'm a complete idiot. But I CANNOT figure out how to get DOS 5.0, 6.0, or Windows 95 to install in Virtualbox! I have ISO or IMG files for each OS. I can load the image just fine in VirtualBox; my problem is actually installing the OS. It loads up, and I get an A:> prompt. I tried doing things like running "Setup", it doesn't exist. I check the directory, and there IS no setup file. The only thing remotely close is autoexec.bat, but that does nothing either. What step am I missing here? I know the images are fine, as I downloaded them from multiple sites and they're all the same. Help a noob out here.

Thanks,
Dan

---

### Post by HotShotDJ on 2009-01-31
for DOS at the A:> prompt, I BELIEVE you need to type```
sys c:
copy command.com c:\
```then copy the rest of the files over in order to get a bootable drive.  I don't know about Windows 95.  I never installed it or used it in my life.

---

### Post by dbsoundman on 2009-01-31
Thanks a lot! Now, it seems my problem is I can't seem to mount a c: drive. I do have a virtual disk specified as the primary IDE drive for this system, but I don't know exactly how I should get that going in the virtual machine. Doing sys c: produces a fail message: "Invalid Media type".

Can you all tell that I was in 3rd grade when Windows 95 came out? haha

-Dan

---

### Post by lykwydchykyn on 2009-01-31
It's been a loooooooong time since I've setup windows 95, but it's not the walk-in-the-park that setting up a modern OS is.  If memory serves, some versions of the win95 cd were not even bootable, you had to boot do a DOS floppy first and start the setup from the floppy.  You also had to use fdisk to make the partition, then reboot, then format, then start the installer.

I may be thinking of 3.1, though; it's been years.  Surely theres a howto out there?

EDIT: here's a tutorial: [http://www.pcguide.com/proc/sw/w95inst-c.html](http://www.pcguide.com/proc/sw/w95inst-c.html)  Note the part in the "preparations/warnings" section about partitioning and formatting beforehand.  

One thing about this; once you're done, you'll never again be tempted to think that Linux is hard to install.

---

### Post by HotShotDJ on 2009-01-31
> **dbsoundman said:**
> Can you all tell that I was in 3rd grade when Windows 95 came out?When I was in 3rd grade, the very first Unix from Bell Laboratories had just escaped into the wild. :)

I was operating under the assumption that you had formated your virtual disk already.  Use the following commands INSTEAD of the ones I gave you -- again, its been a very long time since I've dealt with DOS.... so no guaranties -- ```
format c: /s
copy *.* c:\
```

---

### Post by dbsoundman on 2009-01-31
OK, I'm working on DOS 5.0 right now, I have the files copied to the C drive, and it's all formatted and all that. Wnat next?

-Dan

---

### Post by HotShotDJ on 2009-01-31
> **dbsoundman said:**
> OK, I'm working on DOS 5.0 right now, I have the files copied to the C drive, and it's all formatted and all that. Wnat next?

-DanInstall all that DOS software that has been sitting around with nothing to do since you were in 3rd grade. :)

Why did you install it?  What do you WANT to do with it?

---

### Post by dbsoundman on 2009-01-31
I want to install it just so I can play with it, and partially because I can. I'm pretty good at accumulating lots of useless skills. I actually eventually want to get an old computer and turn it into a DOS gaming system (don't laugh too hard). So, I figured I might as well get familiar with HOW I do it.

-Dan

---

### Post by HotShotDJ on 2009-01-31
> **dbsoundman said:**
> I want to install it just so I can play with it, and partially because I can. I'm pretty good at accumulating lots of useless skills. I actually eventually want to get an old computer and turn it into a DOS gaming system (don't laugh too hard). So, I figured I might as well get familiar with HOW I do it.Well... I guess you can start here: [http://www.dosgames.com/](http://www.dosgames.com/)

You'll have to put them on a DOS formatted floppy drive and then mount the floppy in your virtual machine, because I know of no way to get the files to your virtualized DOS system... I'm pretty sure that Shared drives won't work right, because that type of networking wasn't around in the days of DOS.

---

### Post by dbsoundman on 2009-01-31
Ook, I get it now. I was thinking there was some sort of setup procedure beyond copying the files to the local drive. Now I'm on to Windows 95...

-Dan

---

### Post by HotShotDJ on 2009-01-31
> **dbsoundman said:**
> Ook, I get it now. I was thinking there was some sort of setup procedure beyond copying the files to the local drive.OH... you expected some kind of fancy set up routine for DOS?  Nope... back in the day, you made the disk bootable, copied the files, and you were done.

---

### Post by lykwydchykyn on 2009-01-31
> **HotShotDJ said:**
> OH... you expected some kind of fancy set up routine for DOS?  Nope... back in the day, you made the disk bootable, copied the files, and you were done.

Well, almost done... until you wanted a mouse, audio card, or CD ROM device working.  Then it was time to start hacking autoexec.bat and config.sys.

I don't know much about DOS networking, but I seem to remember surfing gopherspace back in my college days with a little help from kermit and a null modem.  

Seems like there's more to DOS than just command.com; IIRC MS DOS 6 was several diskettes, and there were some graphical shells available (I had one before switching to norton commander).  I mean, yeah, you only need like 3 files and a sys c:, but if you really want to experience early 90's computing there's a lot more to it.

---

### Post by HotShotDJ on 2009-01-31
> **lykwydchykyn said:**
> Well, almost done... until you wanted a mouse, audio card, or CD ROM device working.  Then it was time to start hacking autoexec.bat and config.sys.

I don't know much about DOS networking, but I seem to remember surfing gopherspace back in my college days with a little help from kermit and a null modem.Yes... all that stuff was extra.  Nothing was standardized and each device had its own set of software that you had to install to get them to work.  I also remember having to actually purchase software so that I could use my modem (300 baud, put the telephone handset into the rubber boots).  *sigh*  I'm getting all nostalgic now. **wipes eyes**

---

### Post by seachnasaigh on 2009-02-01
Yes, DOS was fun ... it used to be that getting sound to work was what separated the pros from the noobs. 

I'm not sure that "DOS networking" is a phrase you can actually use. 

Warning: DOS doesn't have any sort of modern memory optimisation or partitioning inherent to it. If you start a DOS program, it grabs all of the memory available on the system to run unless you specifically tell it not to in some sort of .ini file. If you're running multiple DOS-based VM's you might find some memory utilisation problems as you go along. YMMV.

Most DOS games, programs, etc. will run in Windows versions up to XP with varying results. They run in a "DOS box" (Windows: WOWEXEC) but you hafta watch out for the warning above, and sometimes edit the file "default.pif" to get them to run right. There's a nice little utility out there called "tamedos.exe" that gives the DOS box a memory ceiling for any individual program. Worth looking into.

Cheers!

---

### Post by niteshifter on 2009-02-02
> **seachnasaigh said:**
> 

I'm not sure that "DOS networking" is a phrase you can actually use. 



Yep, it can be used - just not in polite company :)

I remember setting up dear old DOS to use TCP/IP networking. Needed DOS Extenders installation (Phar Lap / IBM, etc). Extended vs Expanded Memory ... hacking config.sys til your fingers bleed.

I miss it about as much as I'd miss a french kiss from a rattlesnake.

My only worse memory from those days was trying to get AIX installed on a IBM PS 2 machine - dozens and dozens of (expletive deleted) floppies. A mis-step (and there were many) required starting over - from Disk #1.

---

### Post by lykwydchykyn on 2009-02-02
Hey don't forget about IPX/SPX.  We still use netware servers here at work that run on a DOS kernel.

---

### Post by Ng Oon-Ee on 2009-02-03
To the OP, if you're concerned with DOS gaming, DOSBOX is terrific, I've been playing X-Com Apocalypse on it.

---

### Post by glotz on 2009-02-03
You might be interested in [http://www.freedos.org/](http://www.freedos.org/)

---

