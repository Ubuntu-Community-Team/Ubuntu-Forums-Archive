---
title: "fun with XP"
date: 2007-06-28
forum: Windows
---

### Post by loserboy on 2007-06-28
My friend has a problem with his xp machine but it's been a long time since Ive messed with windows and I've forgotten how to fix it, hoping maybe you guys could help.

The power went off while he was running it, and now when you try to boot it shows safe mode options but but restarts after you choose an option and it tries to boot.

heres the fun part. The guy has no windows disk, whoever built it for him didn't give him one. Now if I use one of my windows disk to do the repair function will it work on his comp even though it's a different disk?
I don't recall do you have to enter the key even on a repair?

---

### Post by vexorian on 2007-06-28
you don't need a key to enter to repair console. You will need his administrator password though and chances are he didn't set it.

---

### Post by loserboy on 2007-06-28
I don't thik he set one, but he's about 80 years old and doesnt remember

---

### Post by marklid on 2007-06-28
Try sticking a Windows XP CD n the drive, boot the machine from the CD, go to the recovery console and at the command line type

chkdsk c: /f /r

Sounds like the file syste is corrupt - the above command should fix it, but be warned it can take a good couple of hours....

Let me know if it works ;)

---

### Post by DrEmpire on 2007-06-28
try disabling Automatically Restart if you can, tho i think if possible make new boot disks either with floppy or a cd r then you could use the recovery program and you dont need the key for it

---

### Post by umattu on 2007-06-28
It depends, is your disc an actual install disc or is it a repair disc. Alot of PC manufacturers ship their PC's with windows recovery discs that will ONLY re-install the system to its original state. These discs are model specific, if you try using them on a differant PC they will seem to work, until it is too late to go back. If it is an install disc from MS than you should be ok. 



Now are you saying that the machine actually RESTARTS (as in goes back to bios then POST)?

---

### Post by loserboy on 2007-06-28
@marklid - you sure that chkdsk c: /f /r isn't a full format?

@Drempire - this boot menu doesnt offer that option

@umattu - I have multiple OEM discs, and the computer was a custom build it looks like, so theres no restore disc

what I'm trying to figure out now though is if I can use the repair with my OEM disc on his comp without needing his old key, or needing to use my key

---

### Post by FuturePilot on 2007-06-29
No chkdsk c: /f /r does not format anything. The /f tells it to fix any errors it finds and the /r locates bad sectors and recovers readable information.

---

### Post by marklid on 2007-06-29
Well FuturePilot has explained chkdsk already :)
Any XP install CD (i.e. not manufacturersr recovery CD) should work.

Always handy to have is Ultimate Boot CD for Windows (see [www.ubcd4win.com](www.ubcd4win.com)) which includes chkdsk along with tonnes of other stuff.

---

### Post by DrEmpire on 2007-06-29
i think u should just use some kind of a boot disk like someones else windows cd or just download the boot disk it fits on 6 floppys i think  can be slow but you can recover from that or copy to boot files to flash drive or cd then you be able to do what you need to do,  one more thing i had a problem like it, did you give it enuff time once it took my pc like 5 mins from splash screen to getting into windows

---

### Post by smoker on 2007-06-29
hi, 
if your friend doesn't know his xp key, then he can slave the drive to another computer, and run 'Magical Jelly Bean', and point the app to look in the windows folder of the slave drive (his drive), and it will find the key, then you can copy it and keep it safe.
[http://www.magicaljellybean.com/keyfinder.shtml](http://www.magicaljellybean.com/keyfinder.shtml)

if he gets xp up and running, then use 'belarc advisor' which will list a profile of his pc, and also includes the installed windows key. he can keep a log file for future ref.
[http://www.belarc.com/free_download.html](http://www.belarc.com/free_download.html)

---

### Post by marklid on 2007-06-29
lots of replies LOL save yourself a lot of time and try my advice first, if it does the job (and I think it will) you will save yourself a lot of time.Any XP install disc will work, no key :KS

---

### Post by myoungf1 on 2007-06-29
> **loserboy said:**
> @marklid - you sure that chkdsk c: /f /r isn't a full format?

@Drempire - this boot menu doesnt offer that option

@umattu - I have multiple OEM discs, and the computer was a custom build it looks like, so theres no restore disc

what I'm trying to figure out now though is if I can use the repair with my OEM disc on his comp without needing his old key, or needing to use my key


Check this site out for usuage of chkdsk and fixmbr.  Also as stated any winxp disk can be used to boot up the repair module it doesn't matter about the key.

[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

### Post by loserboy on 2007-07-02
cool, will do. 
thanks for all the info, I used to be able to do this stuff on my own, but it seems I was so happy to get away from windows that I quickly forgot everything.

---

### Post by FuturePilot on 2007-07-02
Don't worry. Sometimes I feel like I'm loosing my Windows knowledge because I've been using Ubuntu as my primary OS, except for a few things on Windows.

---

