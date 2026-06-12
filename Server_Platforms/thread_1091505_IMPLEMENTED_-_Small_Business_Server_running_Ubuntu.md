---
title: "IMPLEMENTED - Small Business Server running Ubuntu 8.10"
date: 2009-03-09
forum: Server Platforms
---

### Post by mitanc on 2009-03-09
I have recently setup a new server in our office because of an ugly crash which happened about a week ago.  The old system was running Windows Small Business Server but after the annoyances I have had, I chose to put in Ubuntu Linux Server 8.10.  While this was no easy task, and in fact a bit stressful at times, but I have successfully installed Ubuntu as our new server for the office.  I was attracted to the Ubuntu OS because of the following features:

1.  Acts as our office’s Domain Controller running Open LDAP to authenticate users to the server
2.  File sharing with permissions using SAMBA which also authenticates over Open LDAP
3.  Printer sharing and spooling using CUPS
4. Snapshot and Backup system using rsync and cron and rsnapshot
5. VPN / SSH access using Hamachi

Now most people will say I can do all of this in Windows, I agree, but there is something about total control over my system.  If there is a problem, in Linux I CAN find a solution usually using a HOW-TO or scowering the forums.  Even though I live in Asia where the “price” of Windows is not really an issue, when problems come up with Microsoft you need to throw money at the solution whether it be hiring a professional, buying more software / hardware, or actually paying MS to help you fix it.

All in all I am really happy with the way the server has been running.  Accessing the file system has been a lot snappier (but that could also be the better hardware) and I am totally loving the backup system I have running.  I am using a program called [rsnapshot]("http://rsnapshot.org") which will take all of the companies shared data files and back them up incrementally using an incredible program called rsync.  Every night it will take a snapshot of the data folder and store them somewhere on the backup partition.  After a week it will take a weekly snapshot and then again begin with the 7 days prior to that so if I need to ever revert to an old version of a file, we have nearly a months supply to choose from.

I will slowly implement some more features such as a mail server and the like, but I had to get the main things running first.  

All the clients are still windows machine because the staff feel mostly comfortable using it, but I have downloaded windows search on each of the clients which allows the staff to search through all of the data shares.  What I would really like to do is implement a search on the Ubuntu server which the clients could search via a web interface.  Of course the web interface would have to allow the clients to open the files they find using hyperlinks.  Anyone have any idea how to implement something like this?

---

