---
title: "more security"
date: 2016-02-07
forum: Security
---

### Post by Jim_Dodds on 2016-02-07
I'm currently using clamtk for antivirus. I just want to know if there is more software out there to use for more security. Like a antikeylogger and for malware?

---

### Post by oldos2er on 2016-02-07
Moved to Security.

Have you read the stickies [here]("http://ubuntuforums.org/forumdisplay.php?f=338")?

---

### Post by HermanAB on 2016-02-07
First of all, Linux is not Windows, so relax and enjoy your new system.  You probably have nothing to worry about.

All Linux and BSD distributions are secure out of the box.  They can become insecure if you install a service without knowing what you are doing.  Experimenting is part of learning though.

To see what is going on, learn how to use tcpdump and how to view the system log files.

---

### Post by patrikmellq on 2016-02-07
The answear is like a coin flip 50/50 ...

Some say that a updated system with Ubuntu running UFW firewall by default is ok and secure.
Also have the home network behind a router.

But when i post that i can relax having Logwatch and Tripwire running on my Ubuntu system, they say i can never relax and that security measurments is on going jorney that never ends.
Logwatch is a software that monitor your system actions and create log files and send them to your email account every day.

Tripwire is a Intrusion Detection System, that means that Tripwire program sign all your files with a uniq key number, then if some one modife or change any file on your system, Tripwire will notice.
And is very hard for a hacker/cracker to make a intrusion and hide it from you, as you would running the Tripwire database on removable medium, for example floppy or USB stick, so there is no acces to Tripwire core system.
But Tripwire has not been developing or updated for many years, so i would recommend Another Intrusion Detection System with the name "Afick"

I have made a complete Logwatch Howto which you can find on this forum, just search for it.
I also made a complete Tripwire Howto which you can find on this forum, just search for it.

Both is up to date working guides.
If you install both, then you will learn much following the steps.

My opinion is that NO Ubuntu system for home use should run with out IDS where you install the database on removable medium.
This don't prevent intrusion, if it happens, but it will make you aware of it has happen.

Cheers

---

### Post by pfeiffep on 2016-02-07
> **Jim_Dodds said:**
> I'm currently using clamtk for antivirus. I just want to know if there is more software out there to use for more security. Like a antikeylogger and for malware?The best security is provided by an educated consumer. The best software is an excellent filter placed strictly between the keyboard and end user enabled by a generous sprinkling of education.

---

### Post by sabina2 on 2016-02-16
Same thoughts. It depends of our own learning curse. It is easy to feel that it can be endless. For me, security or cyber-security are the most interesting parts of computing, even if I do not spend so much time to learn more. Actually, it is not my job, just a hobby.

---

### Post by Habitual on 2016-02-16
clamtk or clamav doesn't clean, only move or removes "infected" files.
so why use it?

I don't use A/V and in 15 years, I've never seen a Linux Virus on a Linux system.

---

