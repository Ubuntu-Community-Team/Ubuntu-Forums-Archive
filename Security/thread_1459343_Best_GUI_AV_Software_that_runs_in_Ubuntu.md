---
title: "Best GUI AV Software that runs in Ubuntu"
date: 2010-04-21
forum: Security
---

### Post by mattlach on 2010-04-21
Hey all,

A friend of mine asked me about trying to save a Windows install by booting up Ubuntu from an external drive, and running an AV scan on it from Ubuntu.

The next question was what a good AV software that will run in Ubuntu might be, and I had to admit I had no idea.  I never run AV in Linux.

Do you guys ahve any good suggestions?   Easy full install via APT with dependencies would be a plus, but not necessary.

Thank you very much,
Matt

---

### Post by CharlesA on 2010-04-21
I use BitDefender and it has worked without any problems. I use it to scan my Windows shares.

---

### Post by HermanAB on 2010-04-21
ClamAV is popular on Linux mail servers.  There is also ClamWin for that other obscure little OS.

---

### Post by shebaw on 2010-04-22
Even if you had a very good antivirus product and scanned the windows installation, it might not do a good job. I used to dual boot windows 7 and xp back in my windows days(lol, it's about 1 month ago), and my windows XP installation got infected by a virus since I didn't install an anti-virus program on it. I used the updated anti-virus program on windows 7 and did a scan on the windows XP partition, it removed the viruses but when I booted in windows XP, they mysteriously managed to get back.

---

### Post by CharlesA on 2010-04-22
> **shebaw said:**
> Even if you had a very good antivirus product and scanned the windows installation, it might not do a good job. I used to dual boot windows 7 and xp back in my windows days(lol, it's about 1 month ago), and my windows XP installation got infected by a virus since I didn't install an anti-virus program on it. I used the updated anti-virus program on windows 7 and did a scan on the windows XP partition, it removed the viruses but when I booted in windows XP, they mysteriously managed to get back.

System restore is lovely, isn't it?

[size=1]Which is why you turn it off, if you need to clean the install of an infection.[/size]

---

### Post by HermanAB on 2010-04-22
Hmm, System Restore is one of the first things I turn off on Windows!
(The second thing I turn off is Desktop Search)

---

### Post by sunk8 on 2010-04-22
> **mattlach said:**
> Hey all,
Do you guys ahve any good suggestions?   Easy full install via APT with dependencies would be a plus, but not necessary.
Thank you very much,
Matt

ClamAV and KlamAV are in the repos and both are good frontends for the AV...
KlamAV offers more options though...
I prefer to scan my Win Drive using KlamAV before I actually boot into it...

Check out these pages too:
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
[http://en.wikipedia.org/wiki/Linux_malware#Anti-virus_applications](http://en.wikipedia.org/wiki/Linux_malware#Anti-virus_applications)

---

### Post by Jive Turkey on 2010-04-26
I've used bitdefender for this, clamav, in my experience throws too many false positives to be very useful.  

I haven't used it yet but AVG offers a linux based live CD for scanning windows that looks promising.  I'ts also important to emphasize that even after an apparently successful virus cleaning of windows, that the machine should never be fully trusted unless you do a fresh install from trusted media.

Malwarebytes is really the only antimalware app for windows that seems to be very good at finding and removing stuff, even for stuff it cant remove it offers you some clues about how to get it out yourself.  I put it on every windows machine I use.

---

### Post by cariboo on 2010-04-26
So far I've found that MS Security Essentials works pretty good, it has found things that an up-to-date Malwarebytes has missed.

---

