---
title: "Getting a Out of Range error on monitor after fresh install of server"
date: 2012-04-06
forum: Server Platforms
---

### Post by MagnaFX on 2012-04-06
Hi there, new to ubuntu server, Had an older HP Proliant Gen3 computer laying around decided to give it a try, installation went perfect, however when the install finished and the system rebooted into the OS, I am not able to see anything on my monitor, Monitor is telling me that the signal is out of range. Any suggestions to get rid of this? :confused:

---

### Post by lisati on 2012-04-06
Are you able to see the grub menu? If so there are a couple of tweaks that might be of help if you are able to log into recovery mode. 

/me rushes off to look.

---

### Post by lisati on 2012-04-06
The "fix" in post 7 of [this thread]("http://ubuntuforums.org/showthread.php?t=1777759") helped me get started with a solution when I had a similar problem on my server.

---

### Post by MagnaFX on 2012-04-06
Unfortunately no, The last thing that I am able to see is my boot manager loading the hard drive, then a fd0:Error (No floppy disk loaded into the drive I am assuming) then I get the error on the monitor.

---

### Post by MagnaFX on 2012-04-06
This is interesting, after being able to load recovery mode, I am not able to execute a shell on /dev/sda1 . Inorder to be able to load a shell i have to go through the /dev/Server-1(the name of the installation)/root/ I am really new to linux, but know a few basic things from running it on a netbook. I am able to get into the root using sudo /bin/bash, however, it is saying that gedit is not installed. I ran aptitude (apt) and installed it but gedit will not run due to "Cannot open display:" then i am thrown back into my root@Server-1:/#  grrrr is there any inline text editor in this shell?

---

### Post by whiskers751 on 2012-04-07
Err..... nano?

---

