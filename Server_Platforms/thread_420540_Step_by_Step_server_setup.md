---
title: "Step by Step server setup?"
date: 2007-04-23
forum: Server Platforms
---

### Post by irv on 2007-04-23
I am thinking about downloading the 7.04 server and was wondering if there is a step by step on how to setup in a non-graphic mode. I would like to run a Samba/HTMP  (LAMB)/FTP etc servers.  I had a server running in Graphic mode with version 6.10, and did an upgrade but something must have gone wrong with the upgrade because when the box rebooted it just hangs and will not open ports. I even tried the recovery mode and could not get into it. I had another computer available so I quickly set that one up to get back on line.
I have been using Ubuntu now since version 5.04 and know my way around the graphic desktop, but I have not  ventured in the prompt only mode. I have use the command line to do other things, and find my way around it to some degree. 
Also, is there graphic tools that can run from the prompt to help setup the server software? And is it possible to   to VNC to the server when it is running in not graphic mode?
I know I am full of questions, but I am really green at this.
Thanks for your help ahead of time!
Irv

---

### Post by r0ydster on 2007-04-23
Irv,  I have used this site to set up debian boxes as well as Ubuntu LAMP servers.

[http://www.howtoforge.com/perfect_setup_ubuntu704]("http://www.howtoforge.com/perfect_setup_ubuntu704")

Based on your question, I think this is what your looking for.

Hope this helps,

Mike

---

### Post by irv on 2007-04-24
> **r0ydster said:**
> Irv,  I have used this site to set up debian boxes as well as Ubuntu LAMP servers.

[http://www.howtoforge.com/perfect_setup_ubuntu704]("http://www.howtoforge.com/perfect_setup_ubuntu704")

Based on your question, I think this is what your looking for.

Hope this helps,

Mike Thanks for the help Mike. I am going to give this site a try.
Irv

---

### Post by ckkoba on 2007-04-26
> **irv said:**
> 
Also, is there graphic tools that can run from the prompt to help setup the server software? And is it possible to   to VNC to the server when it is running in not graphic mode?
Irv

Irv, 
There are menus for some programs which help you go through the install process, but for most server software, you'll be slogging through config files. 

I'm not entirely sure you can VNC into a CLI server, but you can always use SSH.

---

