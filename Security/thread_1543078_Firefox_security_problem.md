---
title: "Firefox security problem?"
date: 2010-07-31
forum: Security
---

### Post by jellybaby on 2010-07-31
Hi all,


thought I'd better post this.

PROBLEM:
I was just searching for info on parallel ports and got a result leading to "getsmartservices.net". Firefox (3.6.8 ) immediately disappeared (I found out a few seconds later it was minimized) and was paralyzed underneath a popup saying I had to install anti-virus software. This popup could not be clicked away, and was constantly on top. I tried to kill from the kill icon on my panel, but that didn't work, so I went to System/Administration/System Watcher (sorry, I'm translating from German, that's probably not right, I just can't remember what it is in English, system monitor, maybe) and I killed Firefox from there. When I restarted Firefox, it very politely restored my windows, so I had the same problem. Luckily, after 2 starts, I got the " Well, this is embarrassing" screen and I could disable the page.

QUESTION:
Is this finally a security problem for Ubuntu? Do I have to worry about something that may have been lodged in my user account? "ShieldsUp" tests show my PC is 100% secure, in stealth mode, but I've never experienced anything like this in Linux before. I've tried Suse, Mandrake, Knoppix, and have been with Ubuntu since 5.04


I'd be grateful for any feedback.
Regards

---

### Post by FuturePilot on 2010-07-31
It's fake. It's just an animation and popup that tries to scare you into buying fake anti-virus software that is actually a virus itself.

---

### Post by Rubi1200 on 2010-07-31
From time to time posts appear on the forums from people who have come across similar ''problems.'' In most cases, these are scripts aimed at Windows users. As long as you do not do anything silly (which you did not), the best thing to do is close Firefox and when you restart go to Tools > Clear Private Data and clear all the cookies and browser history. The problem should then be dealt with.
 
You should also consider installing NoScript (available from the Mozilla addons site).

---

### Post by CharlesA on 2010-07-31
Adblock+ works too. :)

---

### Post by jellybaby on 2010-07-31
Thanks for the replies.
I already use Adblock. I would not worry so much only the fact that my kill-icon was rendered useless which means it's a pretty well-programmed script. I tried it again, and this time I tried just to shutdown. There was a different popup saying I can not shutdown without installing the anti-virus. The Ubuntu dialogue for shutdown was delayed about 10 seconds. That is also very unusual. Has anyone tried to reach the site?
Have to go now. I'll be back in the morning (08:00 GMT)

---

### Post by wacky_sung on 2010-07-31
As what you mention, this type of malware can only affect Window OS.By the way, did you dual boot Ubuntu togather with Window OS.If so, very much likely your Window OS has caused this issue from such a malware infection.

---

### Post by FuturePilot on 2010-07-31
> **wacky_sung said:**
> By the way, did you dual boot Ubuntu togather with Window OS.If so, very much likely your Window OS has caused this issue from such a malware infection.

That's impossible. Windows cannot interact with your Linux install.

---

### Post by Giant Speck on 2010-07-31
> **wacky_sung said:**
> As what you mention, this type of malware can only affect Window OS.By the way, did you dual boot Ubuntu togather with Window OS.If so, very much likely your Window OS has caused this issue from such a malware infection.

That's hilariously wrong.

There's really nothing that the Windows partition can do to the Ubuntu partition other than deleting it, which would require Windows to currently be running and for the user to grant the process administrative rights.  And even if the Windows partition is infected, it would most likely be infected with something that can only affect Windows.

To the OP:  It's nothing more than an advertisement designed to fool you into thinking you need their specific malware protection, when the application you would be downloading from them *is* malware.

---

### Post by wacky_sung on 2010-08-01
> **Giant Speck said:**
> That's hilariously wrong.

There's really nothing that the Windows partition can do to the Ubuntu partition other than deleting it, which would require Windows to currently be running and for the user to grant the process administrative rights.  And even if the Windows partition is infected, it would most likely be infected with something that can only affect Windows.

To the OP:  It's nothing more than an advertisement designed to fool you into thinking you need their specific malware protection, when the application you would be downloading from them *is* malware.

I think you do not get my point.I fully agreed that the window partition can never get impact to Ubuntu partition.It is not just a advertisement designed to fool you into thinking that you need their specific malware protection but the software itself is a rouge/fake antivirus which is actually a malware.

Down here explained it better.
[http://en.wikipedia.org/wiki/Rogue_security_software](http://en.wikipedia.org/wiki/Rogue_security_software)

---

### Post by wacky_sung on 2010-08-01
In additional, see below for the latest news.

[http://www.theregister.co.uk/2010/07/30/firefox_update_scareware_ruse/](http://www.theregister.co.uk/2010/07/30/firefox_update_scareware_ruse/)

Beside that, it is targeted for Window OS user.

[http://www.f-secure.com/weblog/archives/00001997.html](http://www.f-secure.com/weblog/archives/00001997.html)

---

### Post by jellybaby on 2010-08-01
Hi,

wacky_sung, I do dual-boot with Win 98SE, but I don't access the internet from Win. Even if a Win-virus managed to see Ubuntu, I don't think it could do damage to ext4 from a fat32. *But*, from everything I've read over the years, one should never underestimate the abilities of these programmers.
Thanks again for all the feedback. By the way, did anyone check out the site? The actual address was [http://getsmartservices.net/ufegf/uwmh.php?fa=545933](http://getsmartservices.net/ufegf/uwmh.php?fa=545933). Under getsmartservices.net and [www.getsmartservices.net](www.getsmartservices.net), nothing actually happens.

jellybaby

---

### Post by wacky_sung on 2010-08-01
> **jellybaby said:**
> Hi,

wacky_sung, I do dual-boot with Win 98SE, but I don't access the internet from Win. Even if a Win-virus managed to see Ubuntu, I don't think it could do damage to ext4 from a fat32. *But*, from everything I've read over the years, one should never underestimate the abilities of these programmers.
Thanks again for all the feedback. By the way, did anyone check out the site? The actual address was [http://getsmartservices.net/ufegf/uwmh.php?fa=545933](http://getsmartservices.net/ufegf/uwmh.php?fa=545933). Under getsmartservices.net and [www.getsmartservices.net](www.getsmartservices.net), nothing actually happens.

jellybaby
I just visited the site the provided and it does not cause any impact to me.

FYI i do not use any addon for firefox such as Noscript, Adblock , etc.

---

