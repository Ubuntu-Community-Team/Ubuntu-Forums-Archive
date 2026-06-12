---
title: "Ubuntu sudo versus windows 7 user account control"
date: 2010-01-06
forum: Security
---

### Post by dogdo on 2010-01-06
Hi

Is windows 7 UAC basically a user/system control system like sudo?

---

### Post by cdenley on 2010-01-06
> **dogdo said:**
> Hi

Is windows 7 UAC basically a user/system control system like sudo?

This probably isn't the best place to ask how Windows 7 works. I've hardly touched vista. I haven't even seen Windows 7.

---

### Post by Project PWNED on 2010-01-06
Sudo's equivalent in Windows is sorta like when you have a guest account on Windows, you hold Shift and right click on an installer to install a program, then you get the "Run As..." part on the very top of the menu.

There's no real equivalent for UAC on Linux, because UAC is for people running as administrator (or "root" on Linux) all the time and accidentally run something that could potentially change/damage the system. UAC says "HEY, are you sure you want to do this".

Most people click Allow on UAC, regardless if it's a file installer, virus, malware, etc. It's just a false sense of security for people. Soon, you'll have UAC style popups on websites to trick people into "allowing" installation of malware.

---

### Post by running_rabbit07 on 2010-01-06
I would say no, because you don't have to enter a password on WIndows to allow a program to install or change settings.

---

### Post by gradinaruvasile on 2010-01-06
In theory, at lest. In practice, there are some rumours that just doesnt work that well. 
I think the biggest problem is the user mentality - they throw security just because they dont want to be interrupted. AFAIK Vista UAC was bugging Windows users so in 7 it was remade but it seems that the lower bugging ratio is the result of toned down security. But dont take my word for it.

I installed Windows 7 on a laptop and joined a domain with it. 
I dont know how single user UAC works, but here i had to give USER (administrator) AND PASSWORD to make changes to the OS every time. Its true i didnt fiddle with it much to change settings etc.
Probably single user UAC is password only, or maybe click only as i have seen it in Vista (that i used maybe once).

---

### Post by sliketymo on 2010-01-06
Single user mode(IMHO)would be to turn off UAC,and pay attention to what you are doing.

---

### Post by bodhi.zazen on 2010-01-06
> **cdenley said:**
> this probably isn't the best place to ask how windows 7 works. I've hardly touched vista. I haven't even seen windows 7.

+1

---

### Post by rookcifer on 2010-01-07
The funny thing about UAC is that, according to [Mark Russinovich]("http://technet.microsoft.com/en-us/magazine/2009.07.uac.aspx") (a major Windows developer), it is *not* a security boundary.  Yes, I know that sounds a bit odd, but that's what he and others keep reiterating.  If you think about it, it makes sense: UAC is worthless if malware is already on the system and it does nothing to stop spoofing or phishing of admin credentials by fake pop-ups (this can be avoided if one turns on the "secure desktop" mode, but it is not enabled by default).  The main purpose of UAC is to nag developers into creating their software to run in a limited account.

When comparing the Linux superuser and regular users to the Windows "admin" and limited users, it isn't a 1:1 comparison because there are other variables with how the OS kernel handles various data.  I am not a Windows expert, but I have read that the Windows "limited account" is less secure than the UNIX account because it still allows access to certain admin owned dll's. Moreover, most windows services run with admin privileges, whereas on Linux, most daemons run within their own user account.

---

