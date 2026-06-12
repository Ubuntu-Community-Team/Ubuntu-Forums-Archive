---
title: "Kubuntu zealot wants to convert boss"
date: 2007-06-20
forum: Testimonials &amp; Experiences
---

### Post by Fallen_Demon on 2007-06-20
Hi, I started using Kubuntu after coming to uni and being thrown headfirst into the wonderful world of Linux. But I feel that this operating system is not getting the recognition it deserves at my workplace. Currently we run an incredibly slow and crash prone Windows 2003 server. I figure that if I can convince my boss to run Linux on his personal laptop, he can start to throw his weight around and get our server running on a better OS that's also free. The problem is when it crashed last time and he was complaining about it, I said "Ahh, time to move to Linux, eh?" and was met by the reply "Only 1% of the world use Linux...". Since then I've done my research and have found that it's closer to 20% of the world using a Linux box as a server. But anyway, I was wondering how I should approach it, whether I should schmooze then throw the CD at him, or give a demonstration side by side with his XP system and mine running Kubuntu Feisty with Beryl or what. Any suggestions out there?

---

### Post by Scunizi on 2007-06-20
The answer to that really depends on your relationship with the boss.  Personally if you have the the extra equipment lying around and the lattitude to do what you want with it, I'd setup a seperate server using Ubuntu Dapper 6.06 server edition.. It's stable and supported for 5 years. Consider the LAMP install.  Fiesty server is only supported for 18 mths.  

If you're new to it, it will take some effort to configure it for what you need. You might consider posting in the Server subsection of the forum the tasks and programs the current server is running or providing and see if what it does will translate across.  

If you're running windows apps directly off the server you may have to search for a linux equivelant of the program.  If it's contact management (like Act! or Goldmine) you might consider Zimbra.  It's got a slick interface and is accessable through a browser.  With the lamp install you'll be able to host you own website.  For that you could use a CMS program like Joomla.

After installing the server edition of Ubuntu you can add a desktop for the GUI.  It's your choice, gnome, kde or xfce.  

Once you get it running and configured with the services and apps you need, suggest an afterhours test or just plug it into the network and show him how to access it. Of course, if the linux server handles everything you need without seeing any difference from the perspective of the end user, you could always just unplug the existing server, plugin the new one and pretend it was a needed reboot, then let it sit and do it's job.  After a few days the boss will probably wonder why the server hasn't crashed..then you can tell him. :D  Have your resume in hand just in case though.

---

### Post by Fallen_Demon on 2007-06-21
Hmm.. That would be a learning experience... I'm still a low level employee (I moved here 6 months ago to start uni), but yeah, that would be a good idea... I'll have to check if there is good open source or at least free database program out there (we have a huge client database that would be a bit difficult to convert, which is the main sticking point I believe...)

---

### Post by Scunizi on 2007-06-21
Check out [http://www.postgresql.org/](http://www.postgresql.org/) for a free database that may support your database.  It's about as close as you're going to get to Oricle.  Also, depending on what you do with the data you can look into SugarCRM as the interface..

---

