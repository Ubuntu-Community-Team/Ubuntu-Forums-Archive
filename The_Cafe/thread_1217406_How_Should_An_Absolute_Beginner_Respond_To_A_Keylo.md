---
title: "How Should An Absolute Beginner Respond To A Keylogger?"
date: 2009-07-19
forum: The Cafe
---

### Post by LewRockwell on 2009-07-19
How Should An Absolute Beginner Respond To A Keylogger?

Someone recently asked what steps are worthwhile regarding physical keyloggers on machines at work and software keyloggers on "gifted for business" laptops that are taken home.

How and when can they initiate a lawsuit?

.

---

### Post by SuperSonic4 on 2009-07-19
Usually when they discover it if they did not sign an agreement saying they could

---

### Post by oOarthurOo on 2009-07-19
Depending on what Country you are in, businesses allowed to monitor everything you do on the computer. 

Common sense says you have no reasonable expectation of privacy while using a business machine.

I would confirm with IT that it is their keylogger and not a malicious attack. After that, just get to work and stop checking facebook. :)

---

### Post by ramnarayan on 2009-07-19
Ok stupid question,

do key loggers work on linux

and how does one figure out that they are on ?? (on Linux i mean)

---

### Post by oOarthurOo on 2009-07-19
A hardware keylogger works regardless of the os. You can find them by physically inspecting the system, assuming you know what to look for. As for software, it would be trivial to write a script that is launched at boot to record all keystrokes. Chown it to root only and restrict the ability of users to see root processes and there is no way to detect whether a keylogger is running.

---

### Post by ramnarayan on 2009-07-19
i have rkhunter and chkrootkit installed would that help

Am curious about keylogging software, no one has access to my machine, so it should be safe but am wondering how it could be put on ??

I know from wincedows experience (years back) that there are shareware apps available to install such stuff and as also to find such stuff. But i don't think it should be so simple to put it up on Linux boxes

---

### Post by oOarthurOo on 2009-07-19
You're right about that. You'd need administator access. I'm speaking about business owned machines running linux. The administrator could easily do this without user knowledge (assuming they do not also have admin rights). On your machine, I wouldn't worry one little bit. Unless you have ssh enabled and an easy password and allow root to login remotely and... a bunch of other really dumb stuff not enabled by default. You'd have to take a number of steps to weaken your machine enough to let someone hack in and install a software keylogger. :D

---

### Post by t0p on 2009-07-19
The OP was talking about a keylogger that has been installed on an employer's laptop, *by* the employer.

When it comes to *your* machine, the only realistic time a keylogger could be installed on a linux-running computer would be when an attacker has physical access to the computer.

---

### Post by cariboo on 2009-07-19
lkl is available [here]("http://sourceforge.net/projects/lkl/"), it used to be in the repositories, but [Ubuntu package search]("http://packages.ubuntu.com/") seems to be down right now.

---

### Post by ramnarayan on 2009-07-19
> **oOarthurOo said:**
>  You'd have to take a number of steps to weaken your machine enough to let someone hack in and install a software keylogger. :D

Ah, thats what i like about Linux , it takes an effort to allow stupid stuff to happen, not like some of the $$ os's out there ;-)

---

### Post by ramnarayan on 2009-07-19
> **cariboo907 said:**
> lkl is available [here]("http://sourceforge.net/projects/lkl/"), it used to be in the repositories, but [Ubuntu package search]("http://packages.ubuntu.com/") seems to be down right now.

your right, its still there 

Ok seriously why would anyone like to keylog - if not for some devious evil reason ??

---

### Post by oOarthurOo on 2009-07-19
Business might like to know if you are stealing proprietary info. Parents might like to know what their 6 year old is doing online. You might want to keep a record of your actions for legal or reference purposes. I dunno... seems like there are many legitimate reasons to want to log keystrokes.

---

