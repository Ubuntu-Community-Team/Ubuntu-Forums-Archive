---
title: "Mac OSX and Ubuntu Security"
date: 2011-05-30
forum: Security
---

### Post by mr-woof on 2011-05-30
Morning all,

over the last couple of days, I've been reading the articles about this new malware that is targeting OSX and it's got me wondering. One of the articles, just incase you've been living in a cave all week :)

[http://www.theregister.co.uk/2011/05/26/mac_malware_game_changer/](http://www.theregister.co.uk/2011/05/26/mac_malware_game_changer/)

How different is the mac OSX security model compared to Ubuntu?

The main reason I'm asking, is we see a lot in these great forums questions along the lines of "I'm new to Linux, what protection do I need?" "Do I need a virus scanner?" and generally the answers are "no malware for Linux, you don't need anything etc etc"

Are we setting ourselves up for a fall? Are we too confident that we can't/won't get infected by anything, that many of us don't install virus scanners, use firewalls etc?

If as we all hope, that Ubuntu and Linux in general becomes more popular, surely the bad guys will try and target Linux? 

Hope that makes sense, I've just woke up :)

---

### Post by donato roque on 2011-05-30
Review your ubuntu security. [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by Lars Noodén on 2011-05-30
> **mr-woof said:**
> How different is the mac OSX security model compared to Ubuntu?



The Mac articles are mostly scare mongering and perhaps based on an agenda.  Much of it seems centered around a trojan.  Nothing significant has changed in recent months.  

As for there being no malware for linux yet, I disagree.  It's called Flash and has been out for a while.  People install it and give over control of their systems, including all input devices.  In most cases Flash is only a wrapper around a movie or animation...

That said, security is not a separate process from regular software engineering.  Rather it is the result of good design.  If you design software carefully, it will be more secure.

---

### Post by spynappels on 2011-05-30
The Mac thing was a social engineering issue, i.e. the user had to allow the offending malware to run/install iirc.

No OS can protect against the PBKAC.










(problem between keyboard and chair)

---

### Post by Thewhistlingwind on 2011-05-30
Trojans can thrive on any platform. The Linux and Mac security structures are similar.

Theres no outstanding drive by vulnerabilities for Linux, and I'm pretty sure theres none for Mac either. The most vulnerable part of the current generation of Unix systems used by home users is the web browser.

---

### Post by aysiu on 2011-05-30
Even if a new malware threat suddenly appeared, having so-called "antivirus" installed would not protect you.

But, yes, as others have stated, this is a trojan, and trojans can thrive on any software platform, because they exploit the gullibility of the user and not any software vulnerability.

---

### Post by Larkspur on 2011-05-30
> **aysiu said:**
> Even if a new malware threat suddenly appeared, having so-called "antivirus" installed would not protect you.

That's not strictly true, is it? (Non-linux) AV do a bit of heuristic scanning, so have a chance of catching new threats, unless the malware is using new methods.  Some warning is better than none. Then again, the disadvantages are false positives.

As for the OPs question, in the event of malware attacks, there may be a large initial infection since reports of malware will be initially dismissed (for good reason - since there's nothing at the moment).  Once more and more people start reporting infection, it'll be taken seriously, and then resolving it should be quick (depending on what it is): if it's a rogue PPA, Launchpad will shut it down, if it's a vulnerability, Ubuntu will push out an update.  Also, news of the risk will be disseminated quickly through places like this forum or Askubuntu and so on.  Look how quickly the deleting theme was jumped upon today.  

And, thinking about it, Canonical has a huge vested interest in keeping Ubuntu malware-free: Apple and Windows know they can take their time since they've got the OEM contracts, they've got their OSs as standard on hardware.  If Ubuntu gets a reputation for vulnerability then there's no more Ubuntu.

---

### Post by aysiu on 2011-05-30
> **Larkspur said:**
> (Non-linux) AV do a bit of heuristic scanning, so have a chance of catching new threats, unless the malware is using new methods.  Some warning is better than none. Then again, the disadvantages are false positives. Exactly. In other words, as far as I'm concerned, not effective. What I have found is that most users get unreasonably paranoid because of those false positives and start deleting otherwise innocuous or actually system-critical files for fear they are malware. Better to just use your own common sense judgment than to rely on so-called "antivirus."

---

