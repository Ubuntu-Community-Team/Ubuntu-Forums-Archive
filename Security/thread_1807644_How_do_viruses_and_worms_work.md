---
title: "How do viruses and worms work?"
date: 2011-07-19
forum: Security
---

### Post by stamatiou on 2011-07-19
How do viruses and worms work? How do they infect files? And finally how can a virus attach its self to a program?

---

### Post by uRock on 2011-07-19
For the most part they do not work in Linux. All of the known Linux viruses have been block by software patches.

---

### Post by stamatiou on 2011-07-19
> **uRock said:**
> For the most part they do not work in Linux. All of the known Linux viruses have been block by software patches.
What are software patches?

---

### Post by haqking on 2011-07-19
> **stamatiou said:**
> How do viruses and worms work? How do they infect files? And finally how can a virus attach its self to a program?


they work well in WINDOWS ;-)

[http://support.microsoft.com/kb/129972](http://support.microsoft.com/kb/129972)

[http://www.howstuffworks.com/virus.htm](http://www.howstuffworks.com/virus.htm)

[http://www.net-security.org/news.php?id=4451](http://www.net-security.org/news.php?id=4451)

[http://www.ehow.com/how-does_4673103_computer-viruses-work.html](http://www.ehow.com/how-does_4673103_computer-viruses-work.html)

[http://en.wikipedia.org/wiki/Computer_virus](http://en.wikipedia.org/wiki/Computer_virus)

[http://www.microsoft.com/security/pc-security/virus-whatis.aspx](http://www.microsoft.com/security/pc-security/virus-whatis.aspx)

**In Linux:**

[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)
[http://www.linux.com/learn/tutorials/284124-myth-busting-is-linux-immune-to-viruses](http://www.linux.com/learn/tutorials/284124-myth-busting-is-linux-immune-to-viruses)
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

---

### Post by haqking on 2011-07-19
> **stamatiou said:**
> What are software patches?

fixes that prevent previously known bugs and vulnerabilites being exploited.

Look up Patch Tuesday if you have ever used a Windows system.

Viruses and such are not really an issue in the *nix world

---

### Post by uRock on 2011-07-19
> **stamatiou said:**
> What are software patches?

Please tell me this isn't for a school homework project.

---

### Post by stamatiou on 2011-07-19
> **uRock said:**
> Please tell me this isn't for a school homework project.
I wish we were doing such things in school but here in Greece we are far away from early computer education :(

---

### Post by haqking on 2011-07-19
> **stamatiou said:**
> I wish we were doing such things in school but here in Greece we are far away from early computer education :(


answers to all your virus related questions are linked and answered above.

enjoy

---

### Post by stamatiou on 2011-07-19
> **haqking said:**
> answers to all your virus related questions are linked and answered above.

enjoy
Ok thanks!

---

### Post by Chayak on 2011-07-19
> **stamatiou said:**
> How do viruses and worms work? How do they infect files? And finally how can a virus attach its self to a program?

I can pretty much go on quite a while on the topic since my job is malware analysis.  Yeah it sounds cool but it's actually more like staring at x86 assembly code in IDA Pro for 8 hours a day and writing reports.

If you're interested in malware research a good start would be to read The Art of Computer Virus Research and Defense by Peter Szor.  It covers the history and gives a good overview.  If you want something more in depth than that then you're going to have to learn x86 assembly language as the vast majority of the good books on the topic are targeted at reverse engineering.

---

### Post by amiacamal on 2011-07-22
@Chayak, now you sound like someone i should be talking too :P 
I'm the guy who ppl give their laptops to when they get all crappy, and "virus'd". In general its more a defrag and delete stuff they never use, but on 2 or three occcasions (ironically all from the same guy) I have seen actual viruses. I'd quite like to know as much as my friends seem to assume i know, and will try to find that Szor book in the college library (before I try other sources). Where would you advise after that? :)

---

### Post by haqking on 2011-07-22
> **amiacamal said:**
> @Chayak, now you sound like someone i should be talking too :P 
I'm the guy who ppl give their laptops to when they get all crappy, and "virus'd". In general its more a defrag and delete stuff they never use, but on 2 or three occcasions (ironically all from the same guy) I have seen actual viruses. I'd quite like to know as much as my friends seem to assume i know, and will try to find that Szor book in the college library (before I try other sources). Where would you advise after that? :)


[http://www.amazon.com/Art-Computer-Virus-Research-Defense/dp/0321304543/ref=sr_1_1?ie=UTF8&qid=1311334369&sr=8-1](http://www.amazon.com/Art-Computer-Virus-Research-Defense/dp/0321304543/ref=sr_1_1?ie=UTF8&qid=1311334369&sr=8-1)

---

### Post by amiacamal on 2011-07-22
Perfect :) If it's not in the library amazon will do  :)

---

### Post by Chayak on 2011-07-22
It's the ones you don't see that are the problem.  There are some very advanced rootkits that dig in so deep in the system that it's almost impossible to detect.  There are a couple I've seen that also have their own network stack that bypasses the OS.

Anti-virus only detects what it has signatures for and there is a lot of malware that they don't have signatures for.  In addition when a malware author finds that his creation is being detected they'll alter it to change the signature.

My general response to a rootkit in a windows box is to never trust it afterwards, wipe the drive completely and reinstall.

I've actually got images for frequent offenders.  I'll boot their system with a live CD, copy their personal files over, and then boot it off the network and select their named image to install.  I check their files and then copy them back over to the machine.  They get a fresh system with all their files and it's minimal work on my part.

---

### Post by mikewhatever on 2011-07-22
Viruses don't work, they are parasites.
:P

---

### Post by Thewhistlingwind on 2011-07-22
> **Chayak said:**
> 

My general response to a rootkit in a windows box is to never trust it afterwards, wipe the drive completely and reinstall.

ANYTHING that's given read/write privileges (To any sector on the drive.) to an untrusted entity is no longer trustworthy.

You'd think people would think of this while pondering those viruses that seem to be "Unkillable.".

---

