---
title: "How to set up a backups on Ubuntu Server 10.04 (32bit)"
date: 2011-09-11
forum: Server Platforms
---

### Post by &#1052;&#1086;&#1093;&#1085;&#1072;&#1090;&#1099;&#1081; on 2011-09-11
Hello!
I have a HDD1(320Gb) for system and 2 HDDs (1TB) for user data. I will backup my system using SimpleBackup utility and place backups on first partition of first terabyte HDD. On second partition i will place file share with data. I will copy the content of first terabyte HDD to second and synchronize it. And i have some questions and need some advice:
1. Can i backup my system better than via SimpleBackup?
2. How can i mirror the data from one terabyte HDD to another?
My first solution was to create software raid1. But this is the risk to lose data when system is crashing. I've also found a ghost4linux utility but i have no experience of using it.
Thanks!

---

### Post by gmiller-1977 on 2011-09-11
Hi there,
 
I'm not sure I completely understand what you are trying to do, so, let me see if I understand your question by restating it.
 
You have a 320GB HDD, that boots your system
You have a 1TB HDD that holds user data
You have a second 1TB HDD that you want to have for backups of the 1TB HDD
 
If you are looking to have a true backup, ie, live data copied to a non live location on a schedule (perhaps, nightly?), your best bet is to simply create a copy or rsync script and add it to cron.
 
If the data on your 1TB HDD is small enough, you may consider having multiple copies of the data copied to the other 1TB HDD.  Perhaps week1, week2, week3, etc - or nightly, Monday - Friday.
 
If this is what you are looking for make sure you take that other 1TB HDD out of the server enclosure, and put it in an external chasis, especially if this is for a business or production environment.  Drives that are internal that are used for backups can be damaged by the power supply in the system, corrupted by a failing controller, etc.
 
Your other suggestion, RAID1, gives server *uptime* in the event of a drive failure, but is not a backup - and should not be used in replacement of one.  RAID1 as you may know allows you to have mirrored data on 2 drives, but, if a file is deleted, it is removed from both drives.
 
Going back to "backup software" - I have to admit, I'm a big believer in just having data "available" when you need to restore it.  I always use external media (RDX, external HDD, etc) that allows me to read the contents/directory structure no matter what system I plug it into.  This way, if your linux server hardware ever failed, you could easily move the data to another server temporarily.
 
I hope this answers your question.

---

### Post by &#1052;&#1086;&#1093;&#1085;&#1072;&#1090;&#1099;&#1081; on 2011-09-22
Sorry for delay with answer.
Thanks! Your post is a good help for me. I've created script, based on 'rsync' and set it on cron. It works and fully satisfies me. Thanks again!

---

