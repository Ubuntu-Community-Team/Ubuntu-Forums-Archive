---
title: "ClamAv found 4 viruses? are they real?"
date: 2008-05-01
forum: Security
---

### Post by iwannamarrymiju on 2008-05-01
clamav found 4 viruses..........but only 3 appear in the quarantine window.

they are:

cache.VIRUS
gdm
gdm.VIRUS

are they real?

I have a lamp/mail/postgreysql server installation.

---

### Post by nidoo on 2008-05-02
I had the same problem as you.

Here is the link to my post and solution.

[http://ubuntuforums.org/showthread.php?t=778659&highlight=gdm.virus]("http://ubuntuforums.org/showthread.php?t=778659&highlight=gdm.virus")

---

### Post by iwannamarrymiju on 2008-05-03
> **nidoo said:**
> I had the same problem as you.

Here is the link to my post and solution.

[http://ubuntuforums.org/showthread.php?t=778659&highlight=gdm.virus]("http://ubuntuforums.org/showthread.php?t=778659&highlight=gdm.virus")

:confused:

so should I presume these are false positives? I thought gdm was necessary for my fluxbox gui.........

---

### Post by nidoo on 2008-05-06
Definitely false positives, I also got the same results on a vanilla install. Whether it's something about the Gnome Display Manager or Clamav I don't know but I'm kind of surprised I couldn't really find information on this immediately. I'm so used to now just doing a quick search and getting an answer. Been a while since I had to play the troubleshooter.

---

### Post by mattress on 2008-05-08
> **iwannamarrymiju said:**
> :confused:

so should I presume these are false positives? I thought gdm was necessary for my fluxbox gui.........


Sorry to go a little OT here but I thought this might help. You don't need GDM for Fluxbox. Personally I would use something like Slim if I wanted a "lighter" system. I believe it's in the repo's somewhere...

GDM is one of many graphical login managers, but none of them are completely necessary. They just make life easier when logging into the system.

HTH

-m

---

### Post by nidoo on 2008-05-08
> **mattress said:**
> 
GDM is one of many graphical login managers, but none of them are completely necessary. They just make life easier when logging into the system.

HTH

-m

Oh I agree but for me it's necessary to have. The wife can handle GDM and one thing I learned early on with sharing the same computer with multiple accounts is make it simple make it universal. If I start changing things when it comes to how she's done things in the past I'm just asking for trouble.:lolflag:

---

### Post by ThorstenS on 2008-05-16
Hi
You can upload potential malware to [http://www.virustotal.com](http://www.virustotal.com).

This page will scan the file with several AV scanners and return the results.

---

### Post by iwannamarrymiju on 2008-05-21
> **ThorstenS said:**
> Hi
You can upload potential malware to [http://www.virustotal.com](http://www.virustotal.com).

This page will scan the file with several AV scanners and return the results.

how do I upload them?I don't see any feature to do that with clamtk.

---

### Post by ThorstenS on 2008-05-24
You have to identify the files on your computer and upload these files using the web interface of the service.
You should do this prior to deleting the files or quarantining them (some anti virus software offers to quarantine the malware)

---

### Post by HermanAB on 2008-05-24
Well, unless you are serving email to Windows users, you need not run a virus scanner on Linux.  It is just a waste of time really.

Cheers,

Herman

---

