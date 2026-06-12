---
title: "Security"
date: 2008-09-29
forum: Security
---

### Post by ursulet1984 on 2008-09-29
Because i'm new i have a question ! Thoes the free o.s. need antivirus and firewall protection or anykind of security ?
Thank you !

---

### Post by enaelis on 2008-09-29
I am a beginner also, but from what the documentation says, it sounds like security programs such as anti virus and spy ware are pointless on all Linux distro's. However I do seem to remember a mention of rootkits... look it up!

---

### Post by cdenley on 2008-09-29
> **ursulet1984 said:**
> Because i'm new i have a question ! Thoes the free o.s. need antivirus and firewall protection or anykind of security ?
Thank you !

If you're asking whether you need anti-virus or a firewall on a typical ubuntu desktop configuration, then the answer is no. If you're paranoid, you do have some options as far as security tools go. I think the most important thing you could do is to simply follow good security practices.
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by hyper_ch on 2008-09-29
Generally there's no need for antivirus
Generally there's no need to modifiy the existing firewall (which lets pass everything)

Rationale: For linux there are hardly any viruses and none in the wild. However if you operate a fileserver or email server you may want to protect Windows clients from catching the malware or from forwarding viruses as attachments to friends. I, however, think that each one has to take care themselves of it. I think the probability that someone gets infect because of something I send is really small. It's must more likely that they will get infected by something from someone else.

The firewall on windows has two purposes: Check what gets in and check what gets out (there's a lot of programs on windows that phone home). The home-phoning is no problem on linux if you stick to trusted software (from the repos). And generally no need to check whats get in. You might - however - want to block certain countries or restrict access to certain services only to a few ipaddresses. But as long as you don't run servers/services (e.g. apache, openssh-server, ....) there's no real point worrying about taht.

---

### Post by uberdonkey5 on 2008-09-30
one of the main reasons I swapped to ubuntu was the increased speed from not running virus protection software. I have asked this question myself on the forums, and there is good consensus that its safe. It is the design of linux itself that enables the security, however be aware that you can damage your system yourself very easily within the terminal if you do not know what you are doing (people suggesting that you use dangerous commands within the terminal, esp. those using 'rm' inappropriately I believe are the main type of 'virus' on linux). There is such an antivirus industry now with microsoft it wouldn't suprise me that it would be politically unacceptable now to make the OS very safe.

---

### Post by stmurray on 2008-10-01
It is all a tradeoff.  I am a relatively paranoid type (years of computer security incident response does that to you), but I don't run AV on my Ubuntu workstation, because 
1) The risk of linux malware (virus/trojan/adware/worm) is low at this time 
2) Signature-based malware detection is getting less and less effective as virus writers find new ways to pack virus executables
3) I am very careful about what executable content can get on my machine:  
[INDENT]  1) I keep all software updated and I only download software from trusted locations (If there is something I want to try, but don't trust, I run it in a VM with no network-- virtual or otherwise-- connected, until I have some assurance of the software).  
  2) I run NoScript on firefox (In my opinion, the most important security software to have in today's environment)
  3) I run a firewall on it
  4) I Never run peer-to-peer file sharing software. [/INDENT] 

I have a Ubuntu server that I run as my own version of a universal threat management (UTM) device-- it has Shorewall, DansGuardian, privoxy, snort, etc.  I do have Clam-AV installed on that, as it is at a higher risk-- it can be accessed from the Internet (ssh), and any performance hit is acceptable.  

I also make sure to backup all data.   That is the first line of defense against almost all problems-- disk crashes, theft of the computer, malware, stupid admin mistakes (me being the admin ), etc

---

