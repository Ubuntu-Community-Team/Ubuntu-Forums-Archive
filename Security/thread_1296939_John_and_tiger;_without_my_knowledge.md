---
title: "John and tiger; without my knowledge"
date: 2009-10-21
forum: Security
---

### Post by Zenmij on 2009-10-21
I'm a bit of a noob at ubuntu and wondered if anyone would be able to help.

I got conky running a while back, in it I have the code for showing up the running processes.

For a while I had been noticing an increase in CPU usage around 1am, and when I glanced at conky, there was a process called deb_checkmd5sums running and hogging the CPU.

At first I tried to kill it using the system monitor, changed the My Processes to All Processes and there were huge instances of deb_checkmd5sums running.

I dug around on the internet and found a reference to something called tiger. So opened up Synaptic and it was installed. 

I never installed tiger myself on this system to my knowledge.

I also found a job in cron.d called john. I found references to this also, and obviously checked synaptic and completely removed it.

My questions: Where these installed as part of a dodgy .deb package I might have installed? And what else can I do to make sure there is nothing else like this on my PC?

I also have firestarter running now with only a few apps allowed to contact the net.

I guess you only make a mistake like this once...  

Thanks v much in advance..

---

### Post by QLee on 2009-10-21
Description of tiger:

Report system security vulnerabilities
TIGER, or the 'tiger' scripts, is a set of Bourne shell
scripts, C programs and data files which are used to perform
a security audit of UNIX systems.  TIGER has one primary goal:
report ways 'root' can be compromised.

Debian's TIGER incorporates new checks primarily oriented towards
Debian distribution including: md5sums checks of installed files,
location of files not belonging to packages, check of security
advisories and analysis of local listening processes.

---

### Post by diesch on 2009-10-21
tiger is suggested by harden-tools and checksecurity. Did you install one of them?
john is recommended by tiger

---

