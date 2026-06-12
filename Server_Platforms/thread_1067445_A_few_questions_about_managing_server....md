---
title: "A few questions about managing server..."
date: 2009-02-11
forum: Server Platforms
---

### Post by robmypro on 2009-02-11
I am liking Ubuntu 8.10 (desktop) so much I have decided to use it instead of Windows 2003 for our main server in our office. I do have a few questions for the resident gurus around here...

1. What is the best way to manage this server remotely? Should I use something like Webmin? 

2. I also need to setup VMware Server (don't have the correct hardware to run ESXi, unfortunately), OpenVPN, MySQL, and a bunch of other software. Can this be done without a GUI, or using Webmin? 

3. What is a good solution for backups? I have an external Maxtor drive, so I'd like to use that, if possible. I also need to backup these VM's. Any suggestions?

4. Is there a good book that might cover a lot of this stuff? Something geared towards Ubuntu Server? 

Thanks for the help guys (and gals).

Rob

---

### Post by warchief_ryan on 2009-02-12
1. SSH.

2. Yes, except im not sure with VMware i've never tried it without a GUI.

3. I always just setup cron jobs to backup stuff. You can just set it up to backup the VM at certain times.

4. Don't know, but theres always the Ubuntu community docs or the Ubuntu server irc channel.


If you dont know your way around in command line I guess Webmin would be a good option.

---

### Post by hyper_ch on 2009-02-12
1.) Learn how to manage the server through the command line. If everything else fails you should still be able to access it through ssh to the command line.

2.) Don't know how to run vmware cli-only. It's possible but I've never done it

3.) I prefer rsync and hardlinks to create incremental snapshot-style backups. However I think backing up a running vm might corrupt the backup file. I've never done that but you'd be wise to check that first.

4.) No clue about books. The information is all out there :)

---

### Post by bigbearomaha on 2009-02-12
if you are running a server, especially in business related interest, it is always best to become familiar with command line and config file editing.

AS the poster before me stated, when push comes to shove and you need to get something done, C/L familiarity will save your bacon almost every time.

However, Webmin is a perfectly good tool that can even help you learn more about the syntax of the config files and commands used to admin because that's what it does at it gut level.  if you use it as both an admin tool and a learning tool, you will be ready to go in no time at all.

 I don't use vnc stuff often myself, but if the data contained in the dir to be backed up is changing frequently, you might want to use something that makes a "snapshot" of the dir at a given point in time and do that on a persistent basis.  it's the next best thing to stopping things for a moment just to back it up.

You can use cron jobs to set up the frequency of backups you want.

Have fun, learn lots.

Big Bear

---

### Post by HermanAB on 2009-02-12
VNC is almost always the wrong solution on Linux.  You can do everything with SSH and Webmin.

Cheers,

Herman

---

### Post by etali on 2009-02-12
I've just started running an Ubuntu server, and I've found that plain old command line is actually quicker and easier than Webmin for most things.

I've left Webmin on - just in case I end up needing a browser based interface while I'm on the move, but I'm not using it much.  

I've been quite impressed with 'Linux Complete', but it's not Ubuntu specific, and there are enough differences that I find myself referring to web based tutorials quite often.

---

### Post by bigbearomaha on 2009-02-12
> **etali said:**
> I've just started running an Ubuntu server, and I've found that plain old command line is actually quicker and easier than Webmin for most things.

I've left Webmin on - just in case I end up needing a browser based interface while I'm on the move, but I'm not using it much.  

I've been quite impressed with 'Linux Complete', but it's not Ubuntu specific, and there are enough differences that I find myself referring to web based tutorials quite often.

You mean you have found "for you" that command line is easier and faster.

Which is fine.

for those for whom remembering text commands or what you had for breakfast that morning or who you are is difficult or for those whose each finger is bigger than two keys and typing quickly is not even close to happening, then perhaps other avenues like Webmin or another might help them to be more productive.

Everyone is different and has different ways of approaching Linux.  That's why it is great that there are so many alternatives and options in Linux.  


Have fun and learn lot's,

Big Bear

---

### Post by etali on 2009-02-12
Of course, each person has their own preferences - I didn't mean to imply any form of 'command line superiority' or anything.  

Perhaps I've had a bad experience with Webmin, but I started using it after having set up ftp, postfix, apache, courier, etc, and I found it incredibly annoying - it has it's own way of doing things, which isn't the same way I learned, so I'll SSH over go to edit a file (e.g. a virtual host I set up inside webmin) only to find it's either called something different, or not in the directory I expect it to be.  

I also find it very irritating to have to navigate through two or three pages to get to make a really simple change.  Webmin pages seem to take ages to load for me, even though everything else on the server loads quickly.

A cheat sheet would solve most of the 'remembering commands' issues, although I do agree with the typing problems - I'm not looking forward to SSH on my netbook, hence leaving Webmin installed!

I was offering my experiences because it sounded like the poster may be at a similar stage to me (has played with Linux in the past, making the leap to running a server...), and I thought they might want to hear my vote.

---

### Post by koenn on 2009-02-12
2-
openvpn is easy without gui, you only need to edit a few text files and run some commands
mysql without gui is also easy, if you know sql. there exist also (web) front-ends to manage and use it.

vmware server without GUI on the server is doable. You can install a gui VMware console on a desktop and connect to a (headless) server. This didn't work for me a few versions ago (probably a bug, may be fixed now), so I used a workaround : install the vmware console on the server but run it through ssh with X forwarding to my desktop.
There's also a web interface for vmware (I never tried it)
vmware also comes with a set of cli tools but I'm not familiar with those.

---

