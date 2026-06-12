---
title: "Godaddy Ubuntu 16.04 Server &quot;This Site Can’t Be Reached&quot;"
date: 2021-02-07
forum: Server Platforms
---

### Post by gaspower on 2021-02-07
Hello,
I am very new to Ubuntu. I have a server on godaddy that I can manage, and they just recently performed a update and right after I received (This site can’t be reached). This happened last time when they did a update and I had to to hire someone to correct the issue and now can not get ahold of them. They always say nothing they update will change anything, but it is very strange two times in a row when they update, I can not access the site on the server. I want to learn how to fix this issue as it may happen more in the future. I can ping the server and I can SSH into it. Can I please get some guidance on what to look for that may cause this issue and some instructions on how to possibly fix it. 

I do appreciate any help. Thank you JR

---

### Post by TheFu on 2021-02-07
If ssh works, it likely is NOT a network problem.  Probably a issue with
[LIST]
[*]reverse proxy
[*]firewall
[*]web server
[/LIST]


What do the log files say? always check the logs first.

Each of those could be running different programs, and different expertise is needed to troubleshoot each. Basically, you'll need to at least determine which program is being used first to get the help.  That is basic admin stuff.  

Hope you realize that support for 16.04 ends in 2 months. Time to move to 20.04.  The upgrade processes haven't been clean for any of my servers. Some failed to boot post-upgrade. All had some huge problem. I have just 1 system remaining on 16.04. Think I'll do a fresh install of 20.04, mirgrate the data over and intall the specific software that server exists to run. It will be faster than a 3 hr upgrade to a broken system, that is certain.

If you need guidance on commands and other background, [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is a hassle-free book.  Until you can look at the logs and provide the config files for the different subsytems, we are sorta stuck.

---

### Post by gaspower on 2021-02-08
Hello,
Thank you for the reply. I will check on you suggestions today and check back. It is really appreciated.

JR

---

### Post by slickymaster on 2021-02-08
*Thread moved to **Server Platforms**.*

---

### Post by gaspower on 2021-02-08
Hello,
Can you please let me know which log files I need to view. I can access all the log files, but is it the system log we need to view for  possibly the error. Thank you

---

### Post by TheFu on 2021-02-08
> **gaspower said:**
> Hello,
Can you please let me know which log files I need to view. I can access all the log files, but is it the system log we need to view for  possibly the error. Thank you

Check them all. Use grep/egrep when you don't know where to look.  Probably don't need to look at any that are compressed.

---

### Post by LHammonds on 2021-02-08
Also, if the web pages / server was configured to use IP addresses, that could cause it to break when the IP changes.

---

### Post by ActionParsnip on 2021-02-08
Have you submitted a ticket to GoDaddy?

---

### Post by gaspower on 2021-02-24
Hello,
I did contact Godaddy, but completely useless. I am trying to access the log files now. Thank you

---

### Post by gaspower on 2021-02-24
Looks like the firewall was the issue. Thank you for all the advice.

---

