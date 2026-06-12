---
title: "Why is Linux a secure design?"
date: 2007-02-15
forum: The Cafe
---

### Post by FaceorKneecaps on 2007-02-15
I have tried to google it but without any luck. I wonder what it is about the Linux design that makes it secure. I guess it has to do with access as user and root, and how the file system is set up, but I dont understand how it works. Anyone have some good links about this?

---

### Post by highneko on 2007-02-15
My guess would be because almost everything's open-source. Groups of users maintain packages which probably have md5sums or something. With windows you would have no idea what you're getting, and to get something done you would have to find a binary file from the internet. Users aren't admin by default. That's all I can think of, some of that may be incorrect.

---

### Post by M$LOL on 2007-02-15
Wouldn't it also be because it is based on the architecturally superior Unix, as opposed to the fatally flawed Windows one?

Also, programs are easier to create in Windows, way more people use it, it's easier to spread malware to, and way simpler to hack, so hackers go for Windows first.

---

### Post by AndyCooll on 2007-02-15
Well, for starters it has been built with security in mind as part of the structure (and not as a bolt on). And the most obvious case is differentiating between user privileges and administrator, and by default actions don't have adminstrative privileges.

:cool:

---

### Post by PriceChild on 2007-02-15
Linux is built as a multi-user OS.

Its built to have lots of users, with different access levels. Normal users can't access files that aren't personally theres. That includes system files.

Next, the way open source development works, everyone gets to read the code. Millions of people are constantly improving software and closing security holes. You can't exactly add dodgy code in without someone else seeing.

Pricey

---

### Post by macogw on 2007-02-15
Along with what PriceChild said, I recently heard a guy from Novell say that he just saw that XP has "switch user" and mulitple people can stay logged on.  That wasn't in Win 9x, but, if I remember correctly, back when Linus started on Linux, he showed someone "it looks like DOS" "yeah and?" "multiple people can log on" "woah" (i think that was in Just For Fun, but it could be from Levy's "Hackers").

---

### Post by Choad on 2007-02-15
built in firewall, no root access by default, open source, modular design.

---

### Post by aysiu on 2007-02-15
This doesn't address your question directly, but it answers parts:
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by beercz on 2007-02-15
[http://www.theregister.co.uk/security/security_report_windows_vs_linux/](http://www.theregister.co.uk/security/security_report_windows_vs_linux/)

---

### Post by koenn on 2007-02-15
when you say "secure by design" you talk about security measures that are build into the os itself, by choice of the programmer(s).
The side effects of open source - e.g. everyone can see the code so malicious code or security holes would get detected -  are not really design decisions, although they contribute to the security. Same goes for the 'more people use windows, so it's a more interesting target' : might be true - but has nothing to do with the _design_ of the OS. 

most of the 'secure design' has indeed to do with the multi-user aspect : 
there's a strict separation between root (sysadmin) and users. users have only acces to their home directory - therefore it's hard for crackers or viruses to access or harm the system  

applications and services usually run with a normal user account - that limits their access to the os and the file system, just as it does for human users. Security flaws in applications do not compromise the entire operating system, as would be the case on some systems where services run as "SYSTEM" or "Administrator' - accounts with unlimited privilegues. 

on multi-user systems, a crash of a program that one user is using should not make the entire system, or even just any of the applications used by other users, crash as well. Thus the separation of users goes further than just the file system. This also helps to prevent intruders or malicious code to do much harm.

The encryprion techniques for eg password lists are quite strong, so hard to break them. Most applications that require remote access, use secure techniques by default (private tunnels, encryption, PKI, ...)

user management is quite straightforward - the access controll for file access is easy to implement and can also be used to manage access to executable files so it's quite easy to give a user access to exactly those things he needs and nothing else. (You don't need to give a user 'administrator' rights or apply very loose settings just to make things work) Security breaches through user accounts and the rights assigned to it, are therefore less likely

Less to do with the design itself but with the 'designers' - the programmers : most people who program for Linux, are used to multi-user, networked systems, and are aware of the consequences - which will be reflected not only in the design of their programs, but also it the default configurations. EG Squid proxy server : not only does it allow to configure access to it in a great many ways - it (at least the packages I've seen so far) also installs with "all access denied" by default.

---

### Post by Dunrobin on 2007-02-15
> **PriceChild said:**
> Linux is built as a multi-user OS.
Just for clarification, Windows has been multi-user since at least Windows 2000.  (I don't remember if that god awful "Windows ME" was or not.)

---

### Post by aysiu on 2007-02-15
> **Dunrobin said:**
> Just for clarification, Windows has been multi-user since at least Windows 2000.  (I don't remember if that god awful "Windows ME" was or not.)
But Windows is not currently (and this may be different in Vista--I'm not sure) built in a practical way to have you operate mainly as a regular user and then temporarily shift up to a more privileged user for **all** tasks.

For example, there is no equivalent (without serious hacking of the registry) to *gksudo nautilus* or *kdesu konqueror* for Explorer. Only some Control Panel items can be Shift-Right-Clicked to **Run As...**. And when the Windows Updates are run using **Run As...**, not all the updates successfully install.

There are also still [many programs designed for Windows that assume you're running as administrator and will not function properly if you are not administrator](http://www.pluralsite.com/wiki/default.aspx/Keith/HallOfShame.html).

So, yes, you can create users in Windows with different levels of privilege, but it's not at all convenient to administer the computer when you're not logged in as administrator.

Read more here:
[http://psychocats.net/ubuntu/security#versuswindows](http://psychocats.net/ubuntu/security#versuswindows)

---

### Post by koenn on 2007-02-15
multi-user as in "multiple users run applications on the same machine, simultanuously ?

besides, the point is that Linux has always been multi-user, and therefore is designed differently (and more secure) than Windows, wich was designed as a stand-alone single user system but had networking and multi-user features added to it afterwards - the functionality may be there, the secure design is not.

edit:
aysiu was faster -
this post is in reply to
> Just for clarification, Windows has been multi-user since at least Windows 2000.

---

### Post by boredandblogging.com on 2007-02-16
Read something the other day that if you try installing something on Vista, the install process actually takes administrator rights. 

Here is post about ithttp://blogs.zdnet.com/security/?p=29.

From a Microsoft guy:[INDENT]Russinovich pegged it as a tradeoff between application compatibility and ease of use, explaining the weakness as a "design choice."

[/INDENT]Microsoft decided a long time ago that market share (ease of use) is much important than security.

---

### Post by M$LOL on 2007-02-16
> **Dunrobin said:**
> (I don't remember if that god awful "Windows ME" was or not.)

See my avatar.:lolflag:

---

