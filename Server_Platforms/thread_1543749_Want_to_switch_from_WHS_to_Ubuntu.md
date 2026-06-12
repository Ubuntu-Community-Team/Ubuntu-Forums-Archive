---
title: "Want to switch from WHS to Ubuntu"
date: 2010-08-01
forum: Server Platforms
---

### Post by dmorri18 on 2010-08-01
Hey everyone. I've been a faithful Windows Home Server user for almost 2 years now, and I have to say, for the most part it has done more than I expected. However, I recently had a situation where I had to restore quite a few things to my personal computer. Well, thank goodness I've been backing everything up for 2 years! Whew! Right? Wrong! Turns out, theres a known bug in WHS where your backups are not accessible. At all. None of them...gone. Kaput! So, I had 2 years of backups sitting on my WHS box, but I couldn't access any of them. Well, after re-installing WHS on my server, and re-installing my Windows XP Pro, I started backups again. They've been running for over a week now, and I decided to test them, and guess what. Can't read them. So now, I'm looking to get rid of WHS and maybe use Ubuntu. My question is, can I still use an Ubuntu box for what I use my WHS for? Here's my list of "need to haves":

Must backup all Windows computers automatically. I have 2 XP Pros, and 1 Vista. If it can do my Ubuntu Netbook as well, that would be a plus.

I have a book database using Sql Server and an .asp page that I run. I MUST have this on my server. I've spent many many hours creating this and it must be accessable! I created the site using notepad! I'm very proud of it! :p In case you're interested, you can view it here: [Clicky-click]("https://uispoh.homeserver.com/ourbooks/")

I have almost 200 movies ripped form DVD onto the server, and I have a [QNAP NP1000]("http://www.qnap.com/pro_detail_feature.asp?p_id=117") that connects to it via UPnP. Of course, I want the same functionality.

I need to be able to have file sharing over the internet. I'd like to be able to browse those folders as well as be able to upload or download to those folders.

Anything else it could do would be icing on the cake. Maybe a mail server...that would be fun to play around with.

My current server specs are:

EVGA 730i mobo with 8 SATA ports - Intel E7400 2.8 Ghz
2x 1GB Corsair DDR2 800
Corsair 650TX 650W PSU
WHS 32 bit PP3
1 WD Caviar 2 TB
2 WD Caviar 1 TB
1 Hitachi Deskstar 500 GB
1 WD Caviar 500 GB (not pooled - for WHS backups)

Let me know what you think. This WHS "bug" seems to be well known, with no work around. This is unacceptable. I can't believe that the main function of this software just doesn't work.

Thanks!

Dave

---

### Post by jbrown96 on 2010-08-01
Ubuntu will not be able to do some of it (like importing a MSSQL database) and will be much more difficult to do the rest. 

Honestly, since you have so many Windows devices, you need to stick with a Windows server. For automatically backing up those Windows boxes, you will have to write a complicated backup program; nothing like that currently exists.

---

### Post by kewlrichie on 2010-08-01
Well I don't think you should give up so quickly. As for ASP website stuff if its .NET you should checkout the Mono project [http://www.mono-project.com/Main_Page](http://www.mono-project.com/Main_Page)

MSSQL database is possible to import into MySQL depending how complicated your database is in MSSQL are. If you have custom stored proceedures you might need to rewrite that stuff. If its just a small simple database you might be able to transfer it over pretty easily. If you even have the WHS runnign now you can install MySQL for windows and see how well it plays with your wepage

Ripping DVD's 100% possible. If all you need is a windows share for your QNAP NP1000 all you will need is samba. As for backup you can just make file shares and have the windows boxes dump important files or even images to the share.

If there's another box you can install server on so you can have it side by side so you can import the SQL database while its running I think that will be easiest way to try and get the database over to mySQL

Just thinking out-loud but I would definitely give it a try


__

---

### Post by dmorri18 on 2010-08-02
I've been thinking of building a cheap temp server just so I can play around with it and see how it works. I was kind of hoping you guys were going to say "Heck ya! I do that myself!" ;)

Thanks for the replies!!

Dave

---

### Post by arrrghhh on 2010-08-02
I know it's not Ubuntu, but for automatic backups I don't think you can beat [Amahi.](http://www.amahi.org/)  IMHO, it's the "best" WHS replacement as it's fairly easy to install new things, and has a lot of great functionality built-in.

As others have said, the biggest issue you're going to run into is that ASP site with the SQL DB.  

All the other stuff, it's just finding the right piece of software that fit your needs.  For media streaming there's several solutions - uShare, MediaTomb and my personal favorite, PS3MediaServer.

---

