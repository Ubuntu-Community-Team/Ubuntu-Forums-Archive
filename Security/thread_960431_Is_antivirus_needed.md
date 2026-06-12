---
title: "Is antivirus needed ?"
date: 2008-10-27
forum: Security
---

### Post by wildman4god on 2008-10-27
I know this may seem like a dumb question, but I'll ask anyway. When I was going through the add/remove programs in ubuntu I saw an anti virus application. My question is why? it was my understanding that there were no viruses for linux (or macs). Should I install this program or not waste my time with it?

---

### Post by DGortze380 on 2008-10-27
> **wildman4god said:**
> I know this may seem like a dumb question, but I'll ask anyway. When I was going through the add/remove programs in ubuntu I saw an anti virus application. My question is why? it was my understanding that there were no viruses for linux (or macs). Should I install this program or not waste my time with it?

Not true.

There are no virus as widespread as those targeted at Windows machines, but it's one of those 'never say never' things.

Best virus protection is being smart about what sites you visit and what you download. I use ClamAV for extra protection along with strict iptables rules.

---

### Post by phowells on 2008-10-27
There is nothing special about Linux that would prevent a virus attack.  Viruses are complex programs that are designed to exploit security flaws in a specific OS.  It requires a lot of skill and effort to write a virus so people write viruses for OSs where they can have the greatest impact and visibility.  Since the MicroSoft OSs have the largest and the least skilled user base it is the best place to target.  Since the Linux user base is many magnitudes smaller and far more technically savvy it makes for a poor target for viruses.

---

### Post by wildman4god on 2008-10-27
Thanks for clearing that up for me.

---

### Post by SeanHodges on 2008-10-27
Some info here:

[http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses)

Most people I know don't use anti virus software on their Linux desktops, and as long as you are making regular backups of your vital data (which you should always do regardless of security measures and chosen O/S), this should be fine.

If you are in the habit of forwarding emails/files to Windows users, however, it's a good idea to install an anti-virus to scan them so you don't accidentally infect your friends/co-workers.

---

### Post by cariboo on 2008-10-27
I see nobody has mentioned that clamav only scans for windows viruses. There is no need for a virus scanner in Linux as the only way a virus can be installed is if you do it as root. So really the biggest virus problem in Linux is the one between the back of the chair and the keybaord. :)

Jim

---

### Post by koenn on 2008-10-27
> **cariboo907 said:**
> I see nobody has mentioned that clamav only scans for windows viruses. There is no need for a virus scanner in Linux as the only way a virus can be installed is if you do it as root. So really the biggest virus problem in Linux is the one between the back of the chair and the keybaord. :)

Jim
... and the only reasonable use of clamav is
* to desinfect a windows PC or a disk from a a Windows PC
* on a Linux machine that transfers files to Windows PC's, to catch viruses before they reach the Windows PC's

---

### Post by porteclefs on 2008-10-27
when surfing the web, you come into contact and have relations with many anonymous partners. be smart, use protection.

---

### Post by bodhi.zazen on 2008-10-27
Thread moved and re-titled.

First there are tons of threads on these forums asking this question ;)

Second please use a more descriptive title.

Third, take the time to learn the basics of Linux (Ubuntu) security :twisted:

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

[[all variants] Intrusion Detection - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=919472")

---

### Post by brian_p on 2008-10-27
> **wildman4god said:**
> I know this may seem like a dumb question, but I'll ask anyway. When I was going through the add/remove programs in ubuntu I saw an anti virus application. My question is why?

It scans for Windows malware.

> it was my understanding that there were no viruses for linux (or macs).

Your understanding is correct,

> Should I install this program or not waste my time with it?

Unless you have some reason to protect a Windows machine you would be wasting your time to install it.

---

### Post by nubdora on 2008-10-27
> **brian_p said:**
> 


Your understanding is correct,


?

There are viruses written for linux and unix, but there are not as many active in the wild as there are for windows.

---

### Post by koenn on 2008-10-27
> **nubdora said:**
> ?

There are viruses written for linux and unix, but there are not as many active in the wild as there are for windows.
you should read a bit before posting.

> **bodhi.zazen said:**
> Thread moved and re-titled.
First there are tons of threads on these forums asking this question ;)
(...)
Third, take the time to learn the basics of Linux (Ubuntu) security :twisted:

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

[[all variants] Intrusion Detection - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=919472")

---

### Post by nubdora on 2008-10-27
> **koenn said:**
> you should read a bit before posting.

Thank you, but I can read fine. When I see something wrong I tend to point it out. Thank you for pointing me in the direction of system compromise, but I use ubuntu for non-sensitive and non-personal data reasons.

---

### Post by DGortze380 on 2008-10-27
> **koenn said:**
> you should read a bit before posting.

Ok.. not to start is pi$$ing match, but if you really believe that there are no viruses, anywhere, that could infect a linux system, you have a very naive and limited understanding of how computers (and the people that use them) work.

There certainly are viruses for linux. They are few and far between, and generally not a consideration for the average desktop user, but they certainly do exist.

---

### Post by brian_p on 2008-10-28
> **DGortze380 said:**
> 

There certainly are viruses for linux. They are few and far between, and generally not a consideration for the average desktop user, but they certainly do exist.

I bet you're using the word 'virus' in a very general sense to mean 'something bad'. The concept of a virus includes the ability for the code to spread unaided from machine to machine. Viruses for linux do not exist. Trojans and worms do.

---

### Post by hyper_ch on 2008-10-28
there are no known linux viruses out in the wild. Decide for yourself if you need antivirus.

---

### Post by rosv on 2008-10-28
I use anti virus software on my Linux box because most of my friends use windows. As posted earlier, Linux anti virus software can (probably) only find windows viruses. Therefore, if you use a scanner on your Linux box and you find a contaminated file send to you by a friend, you can tell them update their anti virus application. 

Call it solidarity or rationality, I can't decide for myself.

---

### Post by Georgia boy on 2008-10-28
So, the Anti-virus that is for Linux is actually checking for stuff that is for Windows? Then if something did show up it would be on the emails that is being sent from a Windows user and it might be one that you would be forwarding on to another Windows user from your Linux OS. What about the trojans or worms? How do you take care of them?
Thanks
Tom

---

### Post by bodhi.zazen on 2008-10-28
> **Georgia boy said:**
> So, the Anti-virus that is for Linux is actually checking for stuff that is for Windows? Then if something did show up it would be on the emails that is being sent from a Windows user and it might be one that you would be forwarding on to another Windows user from your Linux OS. What about the trojans or worms? How do you take care of them?
Thanks
Tom

Linux security is different from windows.

See : 

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

[[all variants] Intrusion Detection - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=919472")

---

### Post by koenn on 2008-10-28
> **DGortze380 said:**
> Ok.. not to start is pi$$ing match, but if you really believe that there are no viruses, anywhere, that could infect a linux system, you have a very naive and limited understanding of how computers (and the people that use them) work.

There certainly are viruses for linux. They are few and far between, and generally not a consideration for the average desktop user, but they certainly do exist.

OK, not to continue the pissing contest that you did not want to start, but
a/
you should read posts in the context of the thread.
The question was "I saw an anti virus application.  Should I install this program or not waste my time with it?". Given that anti-virus programs on linux check for Windows viruses, any discussion about the likelihood of "Linux viruses" or the necessity to install such AV to protect against linux viruses is off-topic, moot, and borderline nonsense.

b/yes, there are viruses and worms for Linux. They are known and documented. They are remedied not by detection and deletion by AV software as is common on Window systems, but because the vulnerabilities that they rely on to propagate or deliver their payload get patched. 

b bis/ technically, it's possible to create viruses, worms, and the likes that run on Linux, but in order to propagate they'll require access to files, processes, ... where a user has no or unsufficient access to. If a new virus would exploit a new loophole, the hole would get plugged and you'd get the update delivered to you as soon as its ready through your software update mechanism. 

c/ there are other threats to Linux (say, browser exploits, social engineered malicious code execution, stack overflows, ...) but these are beyound the scope if this discussion because they wouldn't get detected by (signutare and heuristics based) virus detection and removal programs anyway, if such programs would scan for linux viruses to begin with, which they don't. 

Given my limited and naive understanding of computers, that's all for now. If you see any flaws in my reasoning, feel free to point them out.

---

### Post by DGortze380 on 2008-10-28
> **koenn said:**
> 
b/yes, there are viruses and worms for Linux. 

That's all I was trying to point out. I'm not a fan of 
'partially correct' or plain incorrect statements like 'there are no virus that can effect linux'. While it does not answer to OP's question directly, it is relevant to correct statements like these for those referring to the thread in the future.

---

### Post by koenn on 2008-10-28
> **DGortze380 said:**
> That's all I was trying to point out. I'm not a fan of 
'partially correct' or plain incorrect statements like 'there are no virus that can effect linux'. While it does not answer to OP's question directly, it is relevant to correct statements like these for those referring to the thread in the future.

Fair enough, 
but one could claim just as well that all of those "linux viruses do exist !" & "but it *is* possible to create viruses for linux !" replies to a thread  that asks about the sense or nonsense of installing  AV software on Linux, are equally "partially correct" or seriously misleading, as they could wrongfully give the impression that installing such AV to protect against said linux viruses actually would do any good. 

Basically, the OP's question was adequately dealt with in posts 5 & 6 & 7, with bodhi's pointer to the security sticking providing some background and elaboration.

---

### Post by brian_p on 2008-10-28
> **DGortze380 said:**
> That's all I was trying to point out. I'm not a fan of 'partially correct' or plain incorrect statements like 'there are no virus that can effect linux'. While it does not answer to OP's question directly, it is relevant to correct statements like these for those referring to the thread in the future.

As part of the correction procedure future readers of this thread might appreciate being given the name of one virus which affects Linux. Some indication of how it spreads from machine to machine without root assistance would go a long way to convincing people that the existence of a Linux virus should be taken seriously.

---

### Post by bodhi.zazen on 2008-10-28
> **brian_p said:**
> As part of the correction procedure future readers of this thread might appreciate being given the name of one virus which affects Linux. Some indication of how it spreads from machine to machine without root assistance would go a long way to convincing people that the existence of a Linux virus should be taken seriously.


/me hands brian DVL

[http://www.damnvulnerablelinux.org/](http://www.damnvulnerablelinux.org/)

---

### Post by brian_p on 2008-10-29
> **bodhi.zazen said:**
> /me hands brian DVL

[http://www.damnvulnerablelinux.org/](http://www.damnvulnerablelinux.org/)

Appreciated, but DVL has a much wider scope than the simple request I made and for which there is as yet no answer. Maybe the only response open to 'Linux viruses exist' believers lies is this little story:

[http://www.xanga.com/uncle_philip/646458237/item.html](http://www.xanga.com/uncle_philip/646458237/item.html)

---

