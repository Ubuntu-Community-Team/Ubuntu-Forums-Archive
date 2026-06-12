---
title: "Linux really needs an antirvirus???"
date: 2007-08-26
forum: Server Platforms
---

### Post by arashiko28 on 2007-08-26
I use Ubuntu 7.04 and since in the university there is a large quantity of viruses spreading from pendrive to computer everytime we swap information, security has come an important matter. There are from trojans, worms, really harmful viruses that turn the screen green (not blue, the recognized fatal error that windows throws, but green) being the only solution for the unexperted to loose all their data and fresh install a copy of their windows.
When I had windows I used the Panda Titanium antivirus. Have 2 years using it and it's great, after an incident with norton and a virus  that costed me 26 GB of music, all my work, pictures and a 40 years old family video that was reediting for burning on DVD, I installed panda and oh! surprise, in the installation found the virus and eliminated it, while norton said there was none. But this is not the point. The point is that after using panda, I became the pendrive cleaner or something like that, when they gave data or I gave it them, quickly checked the pendrive. And still do it, now using linux, since I can see and delete the file, then delete it from the thrash of the pendrive, and then from the computer. But do I need to install an antivirus for linux? For my own safety?:confused::confused::confused:

---

### Post by emrextreme on 2007-08-26
Nay, i don't think so. Unless you wouldn't install apps from own repos but other sources, you won't need a anti-sthg. software but firewall indeed.

---

### Post by Steveway on 2007-08-26
Simply no.
You can install one to check for windowsviruses to protect others but you don't need one for your Linuxsystem.

---

### Post by insane_alien on 2007-08-26
since, your sharing files with windows computers and there appears to be a rampant infestation of viruses, perhaps you should install clamav, its the best AV in linux. this is not for your security(linux will not be affected, however, viruses may lie dormant on your machine and you could transfer an apparently clean file to a windows user where the virus could wreak havoc.

---

### Post by hessiess on 2007-08-26
becose of the way linux is disighned, it would haft to ask you for the password to be able to do anything, a/v is useless

---

### Post by Dark Star on 2007-08-26
No No No No .. .Plz do not ask this question :p Not at all .. Open Source is free from VISTA ;)

---

### Post by Johnsie on 2007-08-26
Lol, no operating system is completely invulnerable. It makes sense to have an anti-virus in case something ever does crop up that affects Linux users. Having no anti-virus on Linux is like having less lifeboats on the Titanic. People banged on about how the Titanic was unsinkable and look what happened, the boat sank and they didn't have enough lifeboats to save them from the disaster.  No operating system is unsinkable and no operating system is fully secure. Linux has vulnerabilities and that was shown recently when hackers hacked the local Ubuntu servers and used them to attack other computers. That may not have been a virus but it showed that there are potential security holes in Ubuntu that CAN and will be exploited if people get the chance. So yes, I think it's wise to have an anti-virus. If you don't and something does happen then it's your loss.

---

### Post by insane_alien on 2007-08-26
> **Johnsie said:**
> Lol, no operating system is completely invulnerable. It makes sense to have an anti-virus in case something ever does crop up that affects Linux users. Having no anti-virus on Linux is like having less lifeboats on the Titanic.

yeah, but if the titanic was linux and the water a virus the captain himself would have had to tear the gash. if he didn't, maybe only a toilet would get flooded though thats still a 1:100 chance.

> No operating system is unsinkable and no operating system is fully secure. Linux has vulnerabilities and that was shown recently when hackers hacked the local Ubuntu servers and used them to attack other computers. That may not have been a virus but it showed that there are potential security holes in Ubuntu that CAN and will be exploited if people get the chance. So yes, I think it's wise to have an anti-virus. If you don't and something does happen then it's your loss.

the ubuntu version was out of date, no longer supported. 

but i do agree, an antivirus in a linux system regularly interacting with a windows system(file transfers and such) should have some degree of protection.

---

### Post by K.Mandla on 2007-08-26
You can get antivirus programs, but most of them are intended for machines that handle Windows files and pass them through to Windows computers.

I've never used an antivirus program on a Linux machine, and probably never will.

---

### Post by p_quarles on 2007-08-26
> **Johnsie said:**
> No operating system is unsinkable and no operating system is fully secure. Linux has vulnerabilities and that was shown recently when hackers hacked the local Ubuntu servers and used them to attack other computers. That may not have been a virus but it showed that there are potential security holes in Ubuntu that CAN and will be exploited if people get the chance. So yes, I think it's wise to have an anti-virus. If you don't and something does happen then it's your loss.
You are correct that no operating system is "unsinkable." But viruses are, as of now, a Windows problem. If you really think that installing an AV scanner on a Linux system will help with security, you're just missing the point. 

Look: ClamAV will find plenty of little scripts in your e-mail folder. Since there are no known Linux viruses in the wild, though, it will not find anything that could pose a threat to your system. It can't scan for things no one knows about.

ClamAV, on the other hand, will do absolutely nothing to prevent the following:
-buffer overrun attacks
-SQL injection attacks
-brute force attacks
-exploits involving insecure protocols such as telnet, ftp, wep, or http browsing
-social engineering

No, Linux is far from bulletproof. Focusing on viruses, though, is a complete distraction from any serious attempt at improving security.

---

### Post by CPUDave on 2007-08-26
The real point is that there are almost no viruses written for Linux.
The nature of Linux OS interferes with the installation of viruses.
An anti-virus will only work for viruses that are already known to exist.

Viruses for Linux are not impossible, just improbable.

---

### Post by euler_fan on 2007-08-27
Have you seen/read [this]("http://ubuntuforums.org/showthread.php?t=510812") yet?

AV is only one part of defense in depth--and a part as a desktop Linux user that is far from your primary concern.

There are some unofficial phishing signatures for ClamAV [here]("http://www.sanesecurity.co.uk/clamav/usage.htm") if you care to try that sort of thing.

---

### Post by euler_fan on 2007-08-27
I'm also going to suggest that a good place to start if you want to have a couple of tools running is to (1) use firestarter to configure your IPTables firewall. Not too hard, their tutorial on their website if very good. (2) run OSSEC-HIDS and set up the email alerts. People will say you don't need a firewall, but that issue is much more controversial than not needing AV. OSSEC-HIDS is designed to help you keep track of the 10000 things going on with your machine and let you know about the more important ones.

If you still want AV, go ahead. It's your machine, your piece of mind, your time and effort.

For the record, unless you are running some kind of server software, then all your ports should be closed by default. I like to run the IPTables firewall as a catchall and monitoring tool--just in case and so I can keep and eye on things.

---

