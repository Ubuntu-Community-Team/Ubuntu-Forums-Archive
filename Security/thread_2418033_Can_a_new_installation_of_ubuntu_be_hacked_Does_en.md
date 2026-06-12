---
title: "Can a new installation of ubuntu be hacked? Does encryption provide any security?"
date: 2019-04-30
forum: Security
---

### Post by linux-user-0987 on 2019-04-30
Do you know of any good sites where people answer questions related to hacking?


  1)Is it correct that to hack a system the hacker has to find a  program with vulnerabilities and use them to access a system? So if I  just installed ubuntu, updated it and set up the firewall for web  browsing, can my system be hacked? This is assuming that all known  vulnerabilities of all the pre-installed packages have been fixed.


  2)If a hacker knows my public ip address, then is it of any use using  a vpn? Of course I can hide it from more people but what about someone  who already knows?


  3) I read that encrypting a hard disk or a single partition can  protect it from viruses and malware. Is this correct? If I have two  partitions on my hard-disk and one of them is infected and the other one  is clean and encrypted, and I access the infected one then can the  virus move to the encrypted partition?


  4) When installing ubuntu, it asks you if you want to encrypt the  home folder. How can I encrypt the whole partition? Can I encrypt a  partition without losing data? If I have ubuntu installed on an  encrypted partition, will I be asked a password during booting?
  
5) Do you think these problems can happen by due to system problems:

  
[LIST]
[*]Screen brightness reducing and computer shutting off.

[*]Audio stops playing.

[*]Amazon app starting by itself without clicking on it.
[/LIST]
  Is it normal for auth.log to contain 15-20 lines only? Does it start a new log after a reboot?
  
6) Are there any user friendly programs which tell you about unauthorized access to your ubuntu os?

---

### Post by TheFu on 2019-04-30
1) No. There are thousands of methods to hack a system don't don't require any technical expertise, just a lazy user.  "I'll watch your laptop why you visit the toilet" is a good one.

2) It depends. There are lots of different VPNs with lots of different settings. Some don't allow any inbound connections. So do.  Coming in on the public IP is outside the VPN (you didn't say it was the VPN-public-IP).  I avoid paid VPNs that reuse the same VPN-public IP.  However, my own VPN, the one I run, obviously provides the same IP when I connect.

3) Probably not, but it depends. If the partition isn't open and mounted, then all that encrypted data could still be corrupted. If someone wanted to be really nasty, they'd just overwrite the header where the encryption stuff is stored - that's less than 1KB.

4) None of the current, best-choice, versions of Ubuntu support encrypted HOMEs anymore. That has been deprecated for good reasons. If you want to encrypt a partition, then everything on that partition will be destroyed. Backup everything you don't want to lose.  Whenever using encrypted storage of any sort, it is extremely important to have excellent backups.  A tiny logical or physical error in the encrypted storage could make everything inside effectively gone.

I cannot answer the other questions.  It is best to ask 1 question per thread and have a clear, concise, relevant title, so people with specific skills might be able to answer.

---

### Post by linux-user-0987 on 2019-04-30
For the first question, what I meant was hacking without physical access.

---

### Post by DuckHook on 2019-04-30
You appear to be interested in security in general. I encourage you to research these matters on your own. A good place to start is with the sticky on these forums that I link to in my sig: Security Basics.

Please understand that the subject of security is vast. There are no quick and easy answers to the questions you are asking.

As for your question #6, think about what your question implies: if there was an easy, user-friendly way to identify **unauthorized** access, why would such access be allowed in the first place? Linux is a highly paranoid multiuser OS that restricts access and privileges by default. Any "unauthorized access" would only get past such a stringent gatekeeper by seeming to be authorized.

The only way I am aware of to find unauthorized access is to go over your logs. To this end: no, it is not normal for your auth.log to contain only 15-20 lines. Mine contains dozens of lines each day and they bridge from one day to the next, eventually packed off to gzipped storage (which can still be read with zcat or zless).

---

