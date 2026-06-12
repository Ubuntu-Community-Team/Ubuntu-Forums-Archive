---
title: "Online Linux Virus Scanner"
date: 2008-05-31
forum: Security
---

### Post by VMC on 2008-05-31
I tried using google to find a Linux online virus scanner. Not a downloaded virus scanner. 

I do not want to have any antivirus scanner on my ubuntu, period. 

From time to time I would like to check my file system. I know of such things for Windows, but they are usually limited to a few files. 

They want you to download the entire program and have it always running. This is one of the reasons I left Windows.

NOTHING slows down a computer more than a antivirus scanner.

I have a dos bootable cd that has a scanner, but I don't think they cover Linux file systems.

Should I  even be concerned? I did read the sticky above, but this topic has come up several times, mainly by Windows users.

---

### Post by The Cog on 2008-05-31
I don't think you will find one. Linux's security model makes it more difficult to run invasive software like that in a browser. Online virus scanners is distinctly windows-think, and the mere possibility of it happenng in windows is part of the reason for windows virus problems.

---

### Post by Thirtysixway on 2008-05-31
You don't even need normal anti virus on Ubuntu.  That's a windows thing ;]

---

### Post by pawnrocket on 2008-05-31
Just a side note. I was curious so one day I logged onto an online virus scanner. It scanned my system and found tons of Windows Viruses. Thats odd I thought considering I haven't ran windows in almost 8 years. So I searched for the .exe's on my system. Of course there weren't any. After the scan they offered to sell me spyware and virus software. So I took a screen shot of my Linux Desktop and their website scan. Some people will do anything for a couple bucks. It was only a flash animation. 

:lolflag:

---

### Post by aysiu on 2008-05-31
Antivirus is a waste of time and resources. Antivirus on Linux even more so.

---

### Post by dakal on 2008-05-31
Generally the only purpose of Linux virus scanners is to protect Windows systems served by the Linux system (for example in the capacity of file server). Given this, online virus scanners for Linux (even if it was possible, which it is not without non-sandboxed arbitrary code being allowed to execute in a document renderer A.K.A. web browser) hardly make any sense. That is the same reason why even on Windows such services often have to be run through Internet Explorer.

As others have also said, the *nix security model (with a clear separation between user and kernel processes, user and administrator access, and generally applications and data) give viruses a much harder time to take off than on Windows.

---

### Post by VMC on 2008-05-31
I guess I was more curious about if I happened upon a dubious web site that deposited a Windows virus from my browser into my file system how would I be able to detect that?

I don't go to warez or porn sites or click on any pop-ups or unknown email . 

I know the Windows viruses would lay dormant ,but in case one got deposited how would I know. I wouldn't even know where to look. I do read my log files though.

Thanks for the replies, they were reassuring.

---

### Post by mikewhatever on 2008-05-31
Letting an online scanner check your system means a site you allow to, or one that can trick you to allow, gets access to your file system. That sounds like a huge security hole. The ability to perform such scans on Windows OS is outrageous. It gives users false sense of security when in fact the system is wide open. To better understand Ubuntu's security model, have a look --> [http://ubuntuforums.org/showthread.php?t=765421](http://ubuntuforums.org/showthread.php?t=765421).

---

### Post by marginal39 on 2012-04-25
Well, if I don't have a virus, what is it then?
For more than two weeks, all of my drives (except for my home folder) are write protected.
I was logging as root before, but after the problem I reinstalled Ubuntu and am logging as just an Admin now, same thing.
In the beginning, everything was OK, after one day, no more writing on my drives again. I wish there was an online scanner for Ubuntu ...

---

### Post by OrangeCrate on 2012-04-25
You're dancing with the dead. This thread is almost four years old. If you have a question/observation, it might be best to post a new thread, probably in the security forum.

---

### Post by rookcifer on 2012-04-25
> **dakal said:**
> As others have also said, the *nix security model (with a clear separation between user and kernel processes, user and administrator access, and generally applications and data) give viruses a much harder time to take off than on Windows.

I generally agree that AV software is next to useless.  But as we have seen with Mac OSX in recent weeks, malware doesn't necessarily have to get root to do damage, nor does it need the user to manually install it.  The Flashback trojan did not need any user interaction (the later versions didn't anyway).  All it did was attack Java running in the browser and then implant itself in the user's /home directory via a hidden file (a file is hidden if it starts with a period).  From there it downloaded another file which then executed and basically connected to a botnet.  The good news for OSX was it was simple to remove and you didn't need AV to do it.  This [guy here]("http://reviews.cnet.com/8301-13727_7-57410096-263/how-to-remove-the-flashback-malware-from-os-x/") gives a thorough overview of how it gets in and how it gets removed.

My point here is that OSX uses the same UNIX security model Linux does, so what happens on OSX should be applicable to Linux.  Indeed, I doubt it would take very many changes at all for someone to make Flashback work on Linux.  The basic structure of how OSX works and how Linux works are the same in regard to file system permissions. 

 The only question I have regarding this is if Linux (and Ubuntu in particular) will be immune due to the default [umask]("https://en.wikipedia.org/wiki/Umask") setting.  That is, every file downloaded to /home on Linux is not executable by default (it doesn't have the "x" bit sett).  I wonder is OSX enables this same behavior?  It seems to me the malware would need a way around this so it could be executed.  Does anyone know what OSX's default umask is?

That all aside, even with AV software, you wouldn't have caught this trojan in its early stages (before AV makers put it in their database).  So, AV software is no guarantee of being clean.  Never has been, never will be.  I think there are better solutions like MAC systems (Apparmor) and other sandboxing mechanisms.

---

### Post by oldos2er on 2012-04-25
Old thread closed.

"If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful."

---

### Post by aysiu on 2012-04-25
I agree with rookcifer. The problem is a lot of people think their computers are invincible or extremely vulnerable. They also think "antivirus" is the solution to all malware problems, when really "antivirus" has very little to nothing to do with stopping malware.

---

