---
title: "Simple Networking Questions From A Noob"
date: 2006-01-29
forum: Server Platforms
---

### Post by Pangloth on 2006-01-29
Hello everyone.

Let me first say that I sincerely apologize if this is not the right place to ask these questions! If I should take them somewhere else, let me know.

Anyway, onto and forward. I'm running a server install of Ubuntu, no X, GNOME, nothing. I have installed an FTP server (vsftpd), SSH server (OpenSSH), and a web server (Apache2).

The servers are configured (more or less) and working (more or less) satisfactory. I'm rather happy with them, too.

Here's my question: how can I see what is going on with the servers and their connections? Let me elaborate.

Assume the daemons are up and running. Let's say I am interested in the FTP server (vsftpd). Is there any way (without a GUI) to find out if a user is logged on, and if they are, what's their IP address and other info? I used to run Bulletproof FTP Server on WinXP and it had a wonderful little window that told you who's on, what they are doing, their IP, bandwidth taken, etc. Is there any way on the console (whether a specific vsftpd command or not) to do something even remotely similar? I'm most interested to know how many (if any) users are on (and which users), where from, and possibly what they are doing. The vsftpd documentation was not helpful at all.

Also, anything similar for SSH sessions? Or am I stuck with using "who" and "ps" to find out? And if I am stuck like that, is there a way to see if they are transferring files over SSH, and perhaps which one(s), and what speeds? What about their IP?

And lastly (for now, I think I'll be spending some time on the forums... le sigh), is there a way to see total bandwidth load at a given time? Kind of like you can do in Windows through the Task Manager -> Networking.

Oh yeah, I have tried the vsftpd and OpenSSH documentation, websites, etc., but I could not find anything relevant. And... I don't mean to seem ungrateful, but... if you just tell me to use netstat and/or tcpdump or the like... well, I tried, but they are not very helpful for what I want to know! Or I don't know how to make them do what I need.

I just want to know what is going on with my server!

Thanks a lot!

PS. For the Horde!

---

### Post by gruepig on 2006-01-29
Basic information is in the logs (/var/log/*) -- poke around (in particular auth.log, messages, syslog, daemon.log, apache2/*).  You can also run 'last' to see who has logged in (and when and from where).  There are a number of programs that will handle log analysis for you.  (webalizer seems to be common for reading apache logs and serving up a web page with a summary.)

You may be able to increases logging for the services you are running.  Also, if you really want to enable logging for networking you could use the logging feature of iptables (firewall).

As for capturing the current state, try 'ps auwwwx', 'who', 'top', 'lsof -i', and 'netstat -ap'.

For network traffic, there are a lot of tools.  Yes, tcpdump is one of them.  Try 'tcpdump -n dst port ftp', for example.  For a summary, 'iptraf' is pretty self-explanatory.  You could also try 'ntop'; I think there's both a command line version as well as a daemon that generates web pages.

Enjoy.

---

### Post by andrija1989 on 2006-01-29
Hey i am a noob with linux ubuntu... and i was just wonderign how do i download and install programs i tried to install java but,.. i couldent installit for some reason.. can soem one please help me :P txs

---

### Post by Iowan on 2006-01-29
[QUOTE=andrija1989]Hey i am a noob with linux ubuntu... and i was just wonderign how do i download and install programs i tried to install java but,.. i couldent installit for some reason.. can soem one please help me :P txs[/QUOTE]I might suggest you start your own thread.  I'm also quite new with Ubuntu, but I used aptitude to load software from the CD and apt-get to update/upgrade stuff.

---

