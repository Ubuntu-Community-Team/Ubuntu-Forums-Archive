---
title: "telenet ssl reinstall problem -- failure in Maverick 10.10"
date: 2011-06-06
forum: Security
---

### Post by Mat11 on 2011-06-06
Hi i've tried to reinstall the telenet ssl package in Synaptic and got this output :-

Setting up telnetd-ssl (0.17.24+0.1-22) ...
groupadd: cannot lock /etc/gshadow; try again later.
adduser: `/usr/sbin/groupadd -g 126 telnetd-ssl' returned error code 10. Exiting.
dpkg: error processing telnetd-ssl (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 telnetd-ssl
E: Sub-process /usr/bin/dpkg returned an error code (1)
matt-laptop2@mattlaptop2-AMILO-Li-1718:~$ 

Can anyone help i've also tried using sudo in terminal 

Cheers Matt

Surely this is one thing that should not fail.

---

### Post by Mat11 on 2011-06-06
Just tried the audit :

The following packages are only half configured, probably due to problems
configuring them the first time. The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 telnetd-ssl          The telnet server with SSL encryption support

I just got far worse -- tried sudo --configure telnet--ssl and it showed it was not installed so went back to snaptic package manager and it shows clearly it is installed ???
I ran sudo dpkg --configure telnet-ssl once again and it said destination folder Operand no longer exists ???

I'm losing my patience with Ubuntu 10.10 Maverick and i know i'll have to save up for the big one which is not worth the plastic value for money wise !

---

