---
title: "Gufx firewall sufficiency"
date: 2015-05-28
forum: Security
---

### Post by papakota on 2015-05-28
Hello! 
I'm pretty new to the world of Linux. Right now I use Ubuntu  Desktop 14.04 Later down the road I plan to install LAMP to try to run a  web server. 
Generally speaking, I prefer GUI (as most people, I  guess), though I have no problem with CLI (remember myself in 1990 with  MS-DOS). 
As a regular user I don't think I really need a firewall in  Ubuntu. Sticking to installation defaults is fine by me. But as an  admin of a web server, I would think that I'm gonna need something  beyond the Desktop ed. defaults security-wise. I'm aware of IPtables, of  course. But to me it seems a little bit too much to learn, too steep of  a learning curve right now. Then there's ufw. 
And a GUI front-end  of it, which is Gufw. Here opinions vary. Some say, I must learn  IPtables, others think that Gufw does its job fine. 
So what I'm asking here is not just an OPINION, but also **a reasoning behind it**. Real life example maybe etc. 
Thank you.

---

### Post by patrikmellq on 2015-05-28
If you are going to run a server - then i would recommend Tripwire.
It does not prevent intrusion - but it will show if you had one intrusion and it will show how the intrusion was made changing files on your system.
The person who make the intrusion can not crack your Tripwire - because the Tripwire databas is on removable media.

Tripwire sign every existing file on your operating system with one algorithm or uniq key and save it into a database.
So each file have a uniq id.
Then you save this database on removable USB stick.

Then if some one (including your self) change any thing on the system - Tripwire will notice this change.
So lets assume you have not touch you system and some one add a root-kit with your system.
Then when you check the system you will see that some critical and sensetive root files have been changed.

So i say again - it does not prevent intrusion - but it show if you had one intrusion.
My self think its to much work running Tripwire with a desktop computer - as after each update i have to update Tripwire database and before that check a Tripwire Report - but if i would run a server i would make sure i install Tripwire.

Here is a SOLVED COMPLETE INSTALLATION OF TRIPWIRE WITH REMOVABLE MEDIA
[http://ubuntuforums.org/showthread.php?t=2233278&highlight=TRIPWIRE](http://ubuntuforums.org/showthread.php?t=2233278&highlight=TRIPWIRE)

CHeers

---

### Post by cariboo on 2015-05-28
You may want to have a look at the Useful Links on Servers, [System Administration, and Security thread]("http://ubuntuforums.org/showthread.php?t=1046738") on the server section of the forum.

---

### Post by papakota on 2015-05-28
Thanks for your replies!

---

