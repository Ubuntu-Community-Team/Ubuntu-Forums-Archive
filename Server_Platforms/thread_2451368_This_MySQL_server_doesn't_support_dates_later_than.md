---
title: "This MySQL server doesn't support dates later than 2038"
date: 2020-10-03
forum: Server Platforms
---

### Post by Robert_Boutin on 2020-10-03
mysql server 5.7 no longer works.  From what I could find online, this error message arises on 32 bit systems.  I ran uname-a on an 18.04 VM and can confirm the result states my VM is 64 bit.  I tried to do a database dump and just recreate my VM but mysql doesn't even start.  Has anyone seen this and found a way around it, even if just enough to get mysql to limp through a database dump?  Thanks.

*Reading package lists... Done*
*Building dependency tree*
*Reading state information... Done*
*Calculating upgrade... Done*
*0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.*
*1 not fully installed or removed.*
*After this operation, 0 B of additional disk space will be used.*
*Do you want to continue? [Y/n]*
*Setting up mysql-server-5.7 (5.7.31-0ubuntu0.18.04.1) ...*
*ERROR: Unable to start MySQL server:*
*2169-10-28T04:36:55.814163Z 0 [ERROR] This MySQL server doesn't support dates later than 2038*
*Please take a look at [https://wiki.debian.org/Teams/MySQL/FAQ](https://wiki.debian.org/Teams/MySQL/FAQ) for tips on fixing common upgrade issues.*
*Once the problem is resolved, run apt-get --fix-broken install to retry.*
*dpkg: error processing package mysql-server-5.7 (--configure):*
* installed mysql-server-5.7 package post-installation script subprocess returned error exit status 139*
*Errors were encountered while processing:*
* mysql-server-5.7*
*E: Sub-process /usr/bin/dpkg returned an error code (1)*

PHP is 7.2

---

### Post by LHammonds on 2020-10-03
> This MySQL server doesn't support dates later than 2038
If your OS is 64-bit and you get that error, is it because a 32-bit version of MySQL was already installed when you tried to do an upgrade?  Or somehow a 64-bit MySQL is "downgrading" to a 32-bit in some very odd way?

Not a lot to go on here so speculation is wild.

LHammonds

---

### Post by Robert_Boutin on 2020-10-04
So might I be able to uninstall MySQL and reinstall a 64 bit version? I didn&#8217;t know there are versions specific to 32 and 64 bit.

** EDIT  I just checked mysql and it is 64 bit:

*root@crm:/etc/php# mysql --version*
[I]mysql  Ver 14.14 Distrib 5.7.31, for Linux (x86_64) using  EditLine wrapper
[/I]
Is there something else that might be causing mysql to think it is running on a 32 bit OS?

---

### Post by spjackson on 2020-10-04
> *2169-10-28T04:36:55.814163Z 0*
Is that your system time? If so, can't you set it to something more realistic?

---

### Post by LHammonds on 2020-10-04
Short answer: Stop playing around in the future or you will create a black hole and end us all!

Longer answer: There isn't a current agreed-upon solution yet at various levels: architecture, embedded systems, instruction sets, BIOS, datatypes, functions, etc.

So don't expect timestamp datatype to work yet.

As a side note, the Network Time Protocol (NTP) also uses a 32-bit integer but due to how it is configured, the similar problem will happen in year 2036.

References:
[Wikipedia](https://en.wikipedia.org/wiki/Year_2038_problem)

---

### Post by Robert_Boutin on 2020-10-04
spjackson spotted the major problem (so thank you!).  My system year was in fact set at 2169.  What is strange (I think) is I turned off synchronization and reset set my time and date manually.  Timedatectl looked fine and MySQL ran and let me update it.  But when I turned synchronization back on (*timedatectl set-ntp on*), local time and universal time both changed back to year 2169.

Having the time synchronized to the second isn't critical on this server but I'd still like the time and date to automatically update correctly so I don't have to think about it.  Is there an alternate way to automatically update the date and time?

---

### Post by rsteinmetz70112 on 2020-12-22
That's pretty weird. I've never seen anything like that, although I have seen ntp servers that don't respond. What ntp servers are you using? Perhaps one has gone rogue, or gotten trapped in a Tardis

---

