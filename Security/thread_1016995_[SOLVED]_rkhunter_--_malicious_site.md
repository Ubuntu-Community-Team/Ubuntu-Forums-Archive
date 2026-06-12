---
title: "[SOLVED] rkhunter -- malicious site"
date: 2008-12-20
forum: Security
---

### Post by utnubuuser on 2008-12-20
Hello -- I recently visited a site that caused a pop-up on my computer, and also caused Firefox to close.

I've installed rkhunter to check for rootkits, and the only warnings produced were for hide, which is part of the installation when you install rkhunter, and a warning for /dev.  Nothing more was specified, so I'm wondering if a default Ubuntu 8.10 installation would contain something to produce a warning on /dev?

The other bit of information is that the site's pop-up was for spyware software.  Unfortunately I immediately quit Firefox and cleared the cache.  I'll see if I can re-locate the site.

I'm guessing it was nothing, but the fact that it caused Firefox to close worried me.

This is the link the site re-directs to: WARNING - THIS SITE STARTS A SCAN OF YOUR COMPUTER UPON ENTERING:
[http://proantivirusscan.com/2009/1/en/_freescan.php?nu=880135](http://proantivirusscan.com/2009/1/en/_freescan.php?nu=880135)
And this is the original Google search result link:  
[http://madison-apartments.com/qolyo/nxurm/recessed/recessed.htm](http://madison-apartments.com/qolyo/nxurm/recessed/recessed.htm)

The original search was for "installing recessed european hinges", the link was found on the second page with the heading:> recessed - female dog recessed vulva - purchase recessed can thermal
installing new recessed lighting promotional code yahoo recessed lighting recessed drink holders installing recessed hinges recessed beds ...

I suppose the heading should've been a clue...

---

### Post by slowth5 on 2008-12-20
Hi utnubuuser, I just ran rkhunter and it also gave me a /dev warning. When I viewed the rkhunter.log file, the suspicious file was related to pulseaudio.  This same file appeared when I scanned a fresh 8.10 install, so I don't think it's an issue.  I would suggest you research your situation though, because I can't say with absolute certainty that it's not an issue for you .

I'd say the likelihood you are infected is rather low, but please understand I'd rather not visit the site to verify this.  I certainly don't want to discourage you from exercising due diligence, but the fact is most malware is directed towards Windows.  Nevertheless, run chkrootkit and clamav if you feel it necessary.

Firefox vulnerabilities certainly exist, so you might want to look into AppArmor.  bodhi.zazen wrote an excellent guide that should enable you to tightly lock down Firefox.  

[http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)

---

### Post by utnubuuser on 2008-12-20
Hi sloth5 --  thanks for checking that.  I'm not going to pursue it, I mostly just wondered about the /dev folder  warning.   I was fairly sure the warning was normal,  --better safe than sorry.

Again, thanks a bunch.  And a Merry Christmas!

---

### Post by Zip247 on 2008-12-20
if you dont want this warning for the /dev/shm/pulse-shm-###### you can whitelist it in the /etc/rkhunter.conf by finding this section

```
#
# Allow the specified files to be present in the /dev directory and not
# regarded as a suspicious file.  One file per line (use multiple
# ALLOWDEVFILE lines), wildcards accepted.

```

and adding this
```

ALLOWDEVFILE=/dev/shm/pulse-shm-*

```

hope this helps

wdecker

---

### Post by cariboo on 2008-12-20
This same web site has been discussed many time here. It doesn't do anything to Linux. If you happen to hit this site while using Windows and you installed Antivirus 2009, you've got some work ahead of you. :)

Jim

---

### Post by utnubuuser on 2008-12-21
Thanks.  -- and merry Christmas.

---

### Post by Firestem4 on 2008-12-22
> **cariboo907 said:**
> This same web site has been discussed many time here. It doesn't do anything to Linux. If you happen to hit this site while using Windows and you installed Antivirus 2009, you've got some work ahead of you. :)

Jim

Hey. I was just looking through this security because I was bored but curious about some security features of Linux. I'm a windows user but I am currently working on migrating to Ubuntu. (or maybe Kubuntu...i havent decided which GUI i like more). 

In any case I noticed what you said about AntiVirus 2009 and i actually was infected with that on my laptop. In my stupidity, I downloaded a file that normally I would have known it was a virus, but I downloaded it anyways. I'm a A+ Certified tech for Windows so I know my way around a computer. (Mind you i have absolutely no programming knowledge. one reason I want to learn linux is how to program - Security is a passion of mine.)

Its actually quite easy to get rid of it. I bombarded my comp (Vista) with some of my anti-virus programs and did a manual search for related files. Found it and deleted in no time, And fater that did a restore to a backup before i got infected. Alls fine now.

---

### Post by Norm24 on 2008-12-27
I recently ran rkhunter and came up with the same warning.Other than the fact that I ran rkhunter I would've never known about the file.

Is it something that is safe to simply delete?

---

### Post by cariboo on 2008-12-27
On a default installation rkhunter comes up with several false positives that can be safely ignored. When using rkhunter you should update it regualrly by using the **--propupd** option. I ran the update before scanning and it didn't find any false positives.

Jim

---

