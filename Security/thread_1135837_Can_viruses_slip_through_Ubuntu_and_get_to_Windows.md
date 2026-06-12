---
title: "Can viruses slip through Ubuntu and get to Windows?"
date: 2009-04-24
forum: Security
---

### Post by Mindrage on 2009-04-24
I just have a question about Viruses for Windows Operative Systems.

(Dual-booting Ubuntu and Windows)
If a virus is gotten inside your Ubuntu, then wait until you start windows, It would have more chance of taking over your Windows.
Does Ubuntu erase those kind of viruses, or is there any program to prevent this from happening. If it now can do it like that.

---

### Post by HermanAB on 2009-04-24
Howdy,

If you serve Email and Samba shares to Windows machines, then you can use ClamAV.  Otherwise, note that nothing *slips* anywhere in Linux.

So, if you don't serve Email, then don't worry about it.

---

### Post by Dave_Connor on 2009-04-24
With Ubuntu there are better file permissions and the first user account isn't administrator or "root" under gnu/linux terms. In order for a virus to do anything really damaging aside would need to be ran under root. So a virus has alot of trouble doing damage on linux and if there was a hole in the code. The code will be patched and recompiled as a urgent security update. With Windows there are bigger risks but running anti-virus software and having common sense of what to open and run will protect you to a certain degree.

---

### Post by brian_p on 2009-04-24
> **Mindrage said:**
> 

If a virus is gotten inside your Ubuntu, then wait until you start windows, It would have more chance of taking over your Windows.

Really? However did you get an idea like that?

> Does Ubuntu erase those kind of viruses, or is there any program to prevent this from happening. If it now can do it like that.

Considering it cannot happen the question is moot.

---

### Post by JK3mp on 2009-04-25
+1 to above posts. W/o a rather broad open sharing between them (not recommended) no.

---

### Post by halovivek on 2009-04-25
I use to test ubuntu and windows by visiting the malware sites and virus attacking sites. Windows gets more infected but ubuntu does not and one more thing. From ubuntu virus will not move to windows to affect and kill windows. It is fine. If you are using email servers and all use antivirus and antispam program for the email server in ubuntu to avoid the spamming of mails and copying,forwarding to the other locations by internet.

---

### Post by lisati on 2009-04-25
Malware is most likely to slip from Windows to Ubuntu (and vice versa) if you actually move it there yourself (email has been mentioned as one way of doing this)

A sizeable portion of malware is designed specifically for Windows: as such, it is unlikely to hurt Ubuntu, unless you're running it with Wine and have given Wine free reign over your Ubuntu installation. Of the rest of the malware, it's unlikely to hurt Ubuntu unless you do something silly.

---

### Post by bodhi.zazen on 2009-04-25
There are no known viruses that affect Ubuntu at this time. There have been "proof of concept" viruses in the past, for Linux, but Linux has long since been patched.

For info on Ubuntu Security, see the sticky at the top of there forums.

In terms of a virus, yes you can "pass through". If you download an infected file and then transfer it to Windows (by usb, email, netwrok share, etc) then you can "infect" windows.

IMO the solution is to "harden" windows and use antivirus on Windows.

---

### Post by Mindrage on 2009-04-25
> **lisati said:**
> Malware is most likely to slip from Windows to Ubuntu (and vice versa) if you actually move it there yourself (email has been mentioned as one way of doing this)

A sizeable portion of malware is designed specifically for Windows: as such, it is unlikely to hurt Ubuntu, unless you're running it with Wine and have given Wine free reign over your Ubuntu installation. Of the rest of the malware, it's unlikely to hurt Ubuntu unless you do something silly.

Yes, that was the awnser i was looking for.
Thanks alot.

---

### Post by HermanAB on 2009-04-25
Viruses do not work on WINE.  Most regular programs don't work on WINE either so a virus doesn't have much of a chance to work!

---

### Post by bodhi.zazen on 2009-04-25
> **HermanAB said:**
> Viruses do not work on WINE.  Most regular programs don't work on WINE either so a virus doesn't have much of a chance to work!

FYI, there are reports of windows viruses running in wine ...

[http://www.avertlabs.com/research/blog/index.php/2009/02/23/running-windows-malware-in-linux/](http://www.avertlabs.com/research/blog/index.php/2009/02/23/running-windows-malware-in-linux/)

[http://www.linux.com/articles/42031](http://www.linux.com/articles/42031)

---

### Post by NathanDS101 on 2009-04-25
Lol of course not

---

