---
title: "Questions about server administration"
date: 2009-07-13
forum: Server Platforms
---

### Post by jdakhayman on 2009-07-13
Greets all,

	I have just recently become a member of the Linux community and have spent copious amounts of time on How-to Forges forums and how-to guides, along with the ubuntu forums and the how-to's there also and many other sites. I have installed, screwed up and reinstalled numerous times to learn, and followed many of the how-tos listed on the how-to forge website to learn what can be done using linux. I started from scratch and have learned everything that I do know from the very generous and helpful Linux community. 
	
	With that said, I have gotten two servers up and running, for the most part doing the things I need/want them to do. I have one machine that does nothing but act as my mail server for multiple domains. Its the how-to Virtual Users And Domains With Postfix, Courier, MySQL And SquirrelMail (Ubuntu 9.04) on how-to forge website. My second machine is running a LAMP setup with just apache/php/perl/mysql/phpmyadmin etc. And it holds the websites that I need to be served up. 

	Everything works well and I do not have to many problems. My questions are these, and I hope that they are not to obstinate:

	What are the basic system/network/server administrative duties that I should be preforming to ensure that all systems are healthy and running . 

	I prefer to use cli to do my administration. Is this a secure,efficient, and a normal way of administration?

	I want to ensure that I'm looking at the proper log files in the proper way. I look at (mail.log,mail.err,etc) sys.log, apache's error file for the respective site. What others? And I use vim to view the files. Is that standard practice? 

	I monitor system resources using the top command, and check my disk space for my data-disks using the df -l command? Are there better ways or am I on track.

	If possible would someone who regularly maintains and administers multiple servers be willing to outline or summarize what there “morning routine” is? How you would start your day off in your roll as a network/system/server administrator? 

	I appreciate all the time and effort of the community at large and all those who so put in some much effort and time helping others.


Thank you and good day.

jdakhayman

---

### Post by koenn on 2009-07-13
my morning routine, workwise, is to ask my colleagues "everything still working ?", and if they nod yes, it's ok. 

what you probably should do is make backups and check them : check the backup routines run, check that something is actually written on the tapes, check that you can restore data from the tapes (or whatever medium you use), check that you can not only restore files, but actually restore a database, an application, ...

Then,you'll want to automate things. Cheking for free disk space etc is all good fun, but what you really want is that the server sends you mail when the available diskspace gets below a predefined number, or when the used space suddenly spikes. 


You'll also want to get mail if other stuff goes wrong (temperatures, fain failures, disk failures, ...)
Then, of course, how you're going to be notified if your mail server goes down ? So you find and implement a solution for that as well.

figuring out what info you need to collect and when to start worrying is one thing, getting that info in an automated way is another. That should keep you busy for a while. 

You should also know what parts of your infrastructure are absolutely indispensable, and how you're going to deal with that. This depends on the business, but you need to know, and have a plan in case something fails. The plan me require that you have set up things in a certain way. So you set them up that way in advance.

Say, your DNS server is down so nobody is doing anything anymore. Do you have a plan ? Or the server with the websites suddenly dies. How fast can you have a server + all web sites up again ? Is that time acceptable to the owners of those sites ?  Do you have a plan and all info you need to set it up again, or is it going to be your best effort from what you remember from the first time + lots of trial and error all over again ? 

Also, you know you're going to decommission those servers sooner or later. start thinking about ways to migrate to new hardware, and set up your current servers so that this migration becomes easier. Also, document how they're set up. It helps. 

Start tracking resource usage (memory, CPU, disk space) so that when you're going to run out of disk space or your server can't deal with the load anymore, you see it coming in advance, and respond before it becomes an urgent problem, or at least plan for it. This means you don't just check occasionally, but check and record regularly, to see where the trends are going (and how fast)

Figure out how you're going to deal with software upgrades and updates. Can you afford to just run apt-get upgrade and hope nothing goes wrong ?

---

