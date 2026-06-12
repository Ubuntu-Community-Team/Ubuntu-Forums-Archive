---
title: "Ubuntu, Bacula, iSCSI, Dell, processors, and backup"
date: 2009-12-30
forum: Server Platforms
---

### Post by mrcoulson on 2009-12-30
Mods, feel free to relocate this thread if I've put it in the wrong place.

We're in the market for a new enterprise backup solution here at work.  My coworker is looking at Ubuntu and Bacula, but he has some questions.  I'm here to see if I can get some insight from the brains around here.

First, does anyone have any experience backing up servers and workstations with Ubuntu and Bacula?  How does it do with SQL Server?  I read it has no built-in support, but there are lots of community-provided scripts for such a thing.  That's important because of our numerous SQL Server databases.

Second, will Bacula on Ubuntu support iSCSI well?

Third, can we get away with a single dual-core or quad-core processor for this system?

Fourth, what exactly does it mean if the Dell server we're going to get is not listed as supporting Ubuntu?

Do you have any other advice to share?  This is our first enterprise-wide foray into open source technology, so we really want to make sure it goes well and doesn't leave the bosses with a poor impression of open source.

Thanks!

Jeremy

---

### Post by pmla on 2009-12-30
Hi Jeremy,

Seems we are looking for the same thing, but unfortunately the news are not good.
I've been trying to get a stable network backup solution for months Bacula included.
Basically have a dell 2950 (quad core) with a scsi vault running ubuntu 9.10 server. And want to network backup 2x win 2003 server (32 and 64b) 2x win 2008 64b and 2 ubuntu servers 9.10 (32 and 64b). Also 

My opinion is that a single quad or dual core are enough for small medium size lans, if you actually arrange a good schedule for the backups, everything is always limited to lan speed.

The best solution would be zamanda they have easy clients and a great server GUI, but it's just too expensive.

So I have been trying and testing Bacula without much sucess.
Problems I have found with bacula working in Ubuntu.

**All GUI's suck big time :)**
- bweb (web based GUI) as many issues with perl and apache. Needs a lot of lines, all directory locations are different. Did not find a good how-to to make this run properly in ubuntu. basically I got to the stage that the web page was responding but all the cgi-bin locations where broken... Given up on this.
- Bat installed from repository can be used in localhost or remotely. The repository version is alpha so 50% of feactures do not work and it keeps losing connection to bacula director.
-webmin as a bacula module that just does not work keeps on showing the director deamon as Down when it's up and running. After a while it's main page just gets stuck saying that the bconsole can not connect to director due to password missmatch?!?!?! when the passwords are correct. Some buttons are missing from the frontend (like run backup now and a few more) )Friends from webmin, I love you guys and use webmin a lot, but please remove bacula from your "working modules".

**Clients to backup**
- they are not smart detecting the main server and importing settings. Therefore each client needs to be individually configured with 5 to 10 lines. Multiply that for let's say 20 clients :)

**Bacula**
Hummm  what to say about bacula?!?! Maybe that it never worked 100% for me, almost impossible to make it run with error messages in the logs. Does not work out of the box. Takes forever to deploy if you can actually manage to do it without an IT department helping :) or maybe dedicating 1 or 2 months of you life to make it run :)
Maybe the hardest software I have ever tested... 3 daemons *-dir, *-sd, *-fd... yes it makes sense in someone head?
Many times the deamon director crashes when communicating with a client or with a remote BAT.
Always error messages.
No stable, working 100% managing GUI.
Bunch of *.conf files (-dir, -fd, -sd, bconsole, tray,)(3 client conf files per client)(1 conf file for bweb),(1 conf file for each BAT). When I say a bunch I really mean a BUNCH.
Password paranoia, you have to set a bunch of passwords, 1 for each deamon, 1 per client, etc. again, a bunch means a BUNCH to much.
General security paranoia when it comes to ip's in the deamon config files... ps, all default address=localhost for the deamons do not work. Use the box nic static lan Ip.

Conclusion, **I support everything that bacula stands for "GPL" and "FOSS", and all the people working there to make it happen**. But personally I do not recommend Bacula except if you want to invest some serious brain cells and time to it. 

**After killing the geeks of entire IT departments, :) Bacula "It comes by night and sucks the vital essence from your computers.":lolflag:**

---

