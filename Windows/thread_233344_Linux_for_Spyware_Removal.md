---
title: "Linux for Spyware Removal?"
date: 2006-08-10
forum: Windows
---

### Post by spindrift on 2006-08-10
I know ClamWin and F-Prot are available for Linux, which can be used to scan a mounted Windows partition - but how about spyware?  I know there aren't any native apps, and if there were they'd be useless for Windows, but I'm sure you could get SpySweeper/Ad-Aware/SpyBot/HiJackThis/CWShredder running under Wine (I've seen Ad-Aware do it already).

Currently BartPE/WinPE holds the crown in this department, since they're actually USING Windows files, but you know the unwritten rule of geekdom - if something can be modified to use Linux, do it!  Besides, it'd provide for more flexible solutions and less hackery just getting something to work.

So I suppose the real question is, outside Knoppix's little chntpw app, are there ways to mount registry hives from XP that would actually be effective?  The world wants to know?

---

### Post by rattlerviper on 2006-08-10
> **spindrift said:**
> I know ClamWin and F-Prot are available for Linux, which can be used to scan a mounted Windows partition - but how about spyware?  I know there aren't any native apps, and if there were they'd be useless for Windows, but I'm sure you could get SpySweeper/Ad-Aware/SpyBot/HiJackThis/CWShredder running under Wine (I've seen Ad-Aware do it already).

Currently BartPE/WinPE holds the crown in this department, since they're actually USING Windows files, but you know the unwritten rule of geekdom - if something can be modified to use Linux, do it!  Besides, it'd provide for more flexible solutions and less hackery just getting something to work.

So I suppose the real question is, outside Knoppix's little chntpw app, are there ways to mount registry hives from XP that would actually be effective?  The world wants to know?


I'm sorry, I'm lost.  Are you asking if you can have a antispyware program on your linux computer and hook it up to your windows computer and remove spyware from the windows computer?  I would think that would be no more succesful than running a antivirus on a Linux box and using it to scan a windows box.  The best you can hope for right now is finding out that indeed there is a virus on the windows machine, but being unable to do anything about it.  So in the case of spyware you would know it was there and be unable to remove it.

Or are you asking if you can run a spyware app on your wine partition.

:confused:

---

### Post by spindrift on 2006-08-10
You trying to tell me that you can't remove viruses from a Windows partition?  Full read-write support for NTFS already exists in Linux and is in use in a few liveCDs (like [LinuxDefender]("http://www.bitdefender.com/bd/site/presscenter.php?menu_id=25&n_id=58")).  And since you can most definitely remove Win32 viruses using Linux (I just tried it with f-prot and a Win32.Downloader trojan), you see it's already possible to pop a liveCD in a Windows machine, mount its partition, and scan/remove viruses without any chance of failure or infection.

My question is, how hard do you think this would be to implement for spyware?

Spyware files do exist in the form of malicious trojans and .dlls, but for the most part it lives in the registry, which is itself a big clumpy file called a "hive" that can be remotely mounted by another version of Windows and accessed.  BartPE already does it with a program called runscanner, and ERD Commander does it quite nicely, but both liveCDs boot into a Windows environment.  Currently Knoppix is the best liveCD recovery platform, in my opinion, but it would suck to have to use two different tools for cleaning an infected machine.

Obviously, it'll take some time before someone decides to make a native Linux spyware remover that's any good, but I'm wondering if the concept is already possible.  Does anyone know how to mount a Windows registry hive in Linux?  If so, it might be possible to find Windows spyware programs that can be modified to run in Wine and access the remotely mounted registry.  If this is possible, spyware can be scanned and removed from a Linux liveCD without ever booting up Windows.

Does anyone else see the possibilities here?

---

### Post by RAV TUX on 2006-08-10
> **spindrift said:**
> I know ClamWin and F-Prot are available for Linux, which can be used to scan a mounted Windows partition - but how about spyware?  I know there aren't any native apps, and if there were they'd be useless for Windows, but I'm sure you could get SpySweeper/Ad-Aware/SpyBot/HiJackThis/CWShredder running under Wine (I've seen Ad-Aware do it already).

Currently BartPE/WinPE holds the crown in this department, since they're actually USING Windows files, but you know the unwritten rule of geekdom - if something can be modified to use Linux, do it!  Besides, it'd provide for more flexible solutions and less hackery just getting something to work.

So I suppose the real question is, outside Knoppix's little chntpw app, are there ways to mount registry hives from XP that would actually be effective?  The world wants to know?

I'm not sure if it has spyware removal or even if it is still active but try this Linux Live CD, put out by Bitdefender.

 [LinuxDefender Live! CD]("http://distrowatch.com/defender")

> LinuxDefender Live! CD is a BitDefender re-mastered Knoppix distribution. It was designed to provide users of both Windows and Linux computers with virus incident rescue tools. Whether your Linux mailserver just got rootkited or your Windows gamestation just got Slammer'd, it's LinuxDefender to the rescue! Just put the bootable CD in your drive to start a turn-key Linux OS which comes packed with almost 1.5 gigabytes of utilities. This distribution contains two world premieres: the world's first ever SAMBA 3 compatible commercial antivirus and FULL NTFS write support - available using the captive NTFS write project.

---

### Post by spindrift on 2006-08-10
I kinda sorta already mentioned LinuxDefender in the second post. :P  And no, it doesn't do spyware.  Thanks though.

---

### Post by RAV TUX on 2006-08-10
also look into [BackTrack]("http://distrowatch.com/backtrack")

---

### Post by RAV TUX on 2006-08-10
> **spindrift said:**
> I kinda sorta already mentioned LinuxDefender in the second post. :P  And no, it doesn't do spyware.  Thanks though.
  My apologies I missed that.

---

### Post by matchstich on 2006-12-17
i found a fix for avast to have a gui, is there one for bitdefender

---

### Post by RAV TUX on 2006-12-17
moving to Windows forum

---

### Post by spindrift on 2007-08-03
Bump, because it's been several months and I'm still just as curious.

---

### Post by spindrift on 2007-08-03
So after looking into it a little more, it seems like the best current solution would be to use something like [RegEditPE]("http://sourceforge.net/projects/regeditpe/") in a WINE environment, then load the usual tools (Spybot, Ad-Aware, etc.) through WINE to access that registry.  There are a few registry readers/writers for Linux, but they edit the registry directly, instead of providing it to the tools to do themselves.

---

### Post by DGMurdockIII on 2008-09-04
im wondering if there is a live cd to remove spyware and viruses from windows manly other os like like mac and linux would be a plus but windows is the most important

---

### Post by spindrift on 2008-09-04
Take a look at BartPE, Reatogo and other liveCDs designed for Windows malware removal.  Try boot-land.net and 911cd.net.

---

