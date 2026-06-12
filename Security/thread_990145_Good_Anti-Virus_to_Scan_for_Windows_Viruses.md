---
title: "Good Anti-Virus to Scan for Windows Viruses"
date: 2008-11-22
forum: Security
---

### Post by gerowen on 2008-11-22
I have never ran an anti-virus on my Linux system, but I'm wondering what a good "on demand" anti-virus is for Linux that is good at detecting Windows viruses so I don't spread them to my co-workers.  I don't need something that runs in the background all the time, I just want something simple that I can open up and click "Scan" on a given location.

---

### Post by SIGTERMer on 2008-11-22
try avast! (free) and disable any background activities as desired :)
although, windows viruses are pretty easy to spot, and might even be a good break form work :D

---

### Post by OrangeCrate on 2008-11-22
+1 for avast!

[http://www.avast.com/eng/download-avast-home.html](http://www.avast.com/eng/download-avast-home.html)

[http://forum.avast.com/index.php](http://forum.avast.com/index.php)

---

### Post by gerowen on 2008-11-22
Is there a GUI for it?  If not I think I'll write myself a python frontend so I can scan stuff without having to manually type all those arguments and stuff when I want to scan something.

---

### Post by OrangeCrate on 2008-11-22
[http://www.avast.com/eng/avast-for-linux-workstation.html](http://www.avast.com/eng/avast-for-linux-workstation.html)

---

### Post by gerowen on 2008-11-22
Ah found it, it didn't make a menu item for the GUI so I had to find it.  Command was:
```
avastgui
```

---

### Post by abhicho on 2008-11-22
I searched the web for a review of AVAST. One of the sites recommened it. Enclosing the url below

[http://anti-virus-software-review.toptenreviews.com/avast-review.html](http://anti-virus-software-review.toptenreviews.com/avast-review.html)

---

### Post by hyper_ch on 2008-11-24
I think I just might quote someone here:
> **RequinB4 said:**
> I think one thing that there are two things that haven't been mentioned.

First, anti-virus is not really anti-virus - it is virus-checking.  AV works (for 99.999% of the time, there are exceptions) by comparing files or parts of files to known patterns of virus interaction.  Since there have been, what, 10 known viruses that will affect a GNU/linux desktop, and none of them running in the wild, the question "should we be vigilant and not be cocky about our virus protection?" is irrelevent because until someone makes a sucessful virus for GNU/Linux there isn't much to check.

Second, there is the beleif that we should run AV to protect those we contact via the internet getting infected.  Assuming we're not talking about a mail or SAMBA server or something, let's think about this for a second - what are the possible outcomes?

1)  Linux box doesn't get a virus.  No problem.

2)  Linux box gets a virus, and doesn't transmit it.  No harm done, maybe a few wasted bytes of space.

3)  Linux box gets a virus, and transfers it to a Windows box, and the Windows box has equivalent or better anti-virus.  They don't get infected, so no harm done.

4)  Linux box gets a virus, and transfers it to a Windows box, and the Windows box doesn't have antivirus or it fails to detect.  Windows user is very sad.

So, let's examine 4.  Since the box doesn't have antivirus, and has an open connection to the internet, and (for the sake of argument) is running unsafe applications such as IE or Outlook, its security is already very low.  In fact, it's far, far, far more likely that they get the virus not from  you but from normal browsing or from ANOTHER windows box which is ACTIVELY propagating the virus.  Add the fact that the probability of 1, 2, and 3 is also MUCH higher than 4, and you begin to see my point.

So you must ask yourself - By running AV on your GNU/Linux desktop, are you protecting against the VERY unlikely, or just delaying the inevitable?

---

### Post by riff raff on 2008-11-24
I don't know about a gui, but you could try what I do; I run a root cron job every Tuesday morning to retrieve any avast updates, and then an hour later it runs avast.  Output is saved in /var/log/avast.weekly.log and I get an e-mail telling me that it ran okay and what warnings it found (if any).  If you're using avast to scan a mail server you might want to run it more often.

---

