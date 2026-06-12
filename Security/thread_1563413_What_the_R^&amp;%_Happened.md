---
title: "What the R^&amp;% Happened?"
date: 2010-08-29
forum: Security
---

### Post by needhelppeeps on 2010-08-29
I moved some video files to a fedora samba server and when I opened one tonight my screen went black and my hard disk went nuts. I saw something about caught unattended installation right before my system rebooted.

I found this under auth.log
Aug 29 02:59:39 polkitd(authority=local): Registered Authentication Agent for session /org/freedesktop/ConsoleKit/Session2 (system bus name :1.30 [/$

Did my system just crap out or ?

---

### Post by wacky_sung on 2010-08-29
May be you have a bad sector in your hard disk or hard disk crashed.

---

### Post by Rubi1200 on 2010-08-29
Just out of curiosity, what graphics card do you have installed?

```
lspci | grep VGA
```

---

### Post by needhelppeeps on 2010-08-29
VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200

I opened the file since without a repeat... it just worried me that it said unattended installation caught and that entry in my auth.log that I had not seen before. 

I set the samba server to only accept connections from my ip and my shh on the fedora server requires a key+password. I don't think I have any services that should open ports on my ubuntu machine.

---

### Post by Rubi1200 on 2010-08-29
You should continue to keep an eye on the logs, but it is quite likely this was a one-time incident.

The message about > unattended installation is normal and nothing to worry about there.

---

### Post by cariboo on 2010-08-29
What version are you using, as there is a bug in policykit for maverick (10.10).

---

