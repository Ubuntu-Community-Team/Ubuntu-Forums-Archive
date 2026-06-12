---
title: "Having a problem getting Shoutcast server to run using terminal"
date: 2007-03-09
forum: Server Platforms
---

### Post by Joe89 on 2007-03-09
Ok, here's the deal:

I go to a tech center through school and one of my classes there requires us (my peers) to do several projects over a 45-day period.  We're here for 2 hours a day and everyone has to do certain projects over a limited timeframe.  The project I'm on right now is setting up a SHOUTcast server using Ubuntu.  I have never touched this OS until a few days ago.  I'm working with 3 other students on this project (it's an individual project, but we're helping each other out) right now and we all seem to be stuck on this little problem we're having save for one person who hasnt been here in a couple of days.  We've asked for help in class, but no one seems to know what to do.  So here I am, asking you guys out here what my problem may be.  Ok, onto the problem.  So our project requires us to use the terminal to get things set up.  We have an 18-page document with instructions on how to do this, but its not working now.  The tar.gz file we downloaded had a folder in it with 4 other files plus 1 mp3 as a sample mp3 to use for setting it up.  The folder is called "**shoutcast-1-9-2-linux-glibc**" (should help you tell what I'm dealing with here).  We put the folder in the etc directory and we were instructed to put the sample mp3 into the content directory (which I had to make myself) which is in **opt/SHOUTcast/content**.  I am running as the root user by the way and I have permissions set too.  According to the document, we should be able to start the server by typing such in the terminal:
**# /etc/init.d/shoutcast start** but when I go to do this, I get this message, [B]root@xxxx-desktop:/etc/init.d# shoutcast start
bash: shoutcast: command not found[/B]

We've tried using the **sudo** command too and a couple of other methods, but nothing seems to work.  Anyone know what I may be doing wrong or missing something?  I've tried to run the server using the gui, but it doesnt run, so we're stuck here and we've got like 2 or 3 days to finish this and we cant even get the bloody thing to run.

Thanks in advance for any advice you may have

~Joe

---

### Post by Aberrix on 2007-03-09
Generally you dont want to run shoutcast as root as that can be really bad. so we create a shoutcast user:

1.) Login to root
2.) adduser shoutcast
3.) passwd shoutcast

Now it will ask for a new password set this and remember it.

Now login as the new shoutcast user.

Installing shoutcast:

Lets take shoutcast from nullsoft:

wget [http://www.shoutcast.com/downloads/s…-glibc6.tar.gz](http://www.shoutcast.com/downloads/s…-glibc6.tar.gz)

extract shoutcast:

tar -zxvf shoutcast-1-9-2-linux-glibc6.tar.gz

rm -rf shoutcast-1-9-2-linux-glibc6.tar.gz
mv shoutcast-1-9-2-linux-glibc6 shoutcast
cd shoutcast

How to configure shoutcast?

your going to want to edit the shoutcast configuration.

pico sc_serv.conf
or
nano sc_serv.conf

MaxUser
Password
PortBase

uncomment AdminPassword and set an admin password.

Now at this point you can go threw the settings and change them to what you want or you can save and start shoutcast and it will work perfectly.

to save crtl+x

How do i start shoutcast?

./sc_serv sc_serv.conf 

(from [link]("http://blog.webhosting.uk.com/category/streaming-media/"))

---

### Post by Joe89 on 2007-03-09
Thank you very much for such a swift response.  Unfortunately I dont have time to do all of that, but I'll do it on Monday (as I'm leaving here in 10 minutes and I have to fill out a weekly paper still) but I'll do ASAP when I return here and replay back with any problems I run into.

---

### Post by Aberrix on 2007-03-09
> **Joe89 said:**
> Thank you very much for such a swift response.  Unfortunately I dont have time to do all of that, but I'll do it on Monday (as I'm leaving here in 10 minutes and I have to fill out a weekly paper still) but I'll do ASAP when I return here and replay back with any problems I run into.

I guess this was the main point, make sure you have it all properly configured then

```
./sc_serv sc_serv.conf
```

---

### Post by spelingchampeon on 2007-03-11
I hope I dont mess anyone up with this... or that I missed something... but I use Streamtuner to listen to Shoutcast music channels. Check Synaptics for it.... if not, it is available online (install Streamripper for recording). The only requirement you may need for Streamtuner is XMMS music player....
.

---

### Post by Joe89 on 2007-03-12
Ok, got it to run to a degree.  How do I put the password in?

*******************************************************************************
** SHOUTcast Distributed Network Audio Server
** Copyright (C) 1998-2000 Nullsoft, Inc.  All Rights Reserved.
** Use "sc_serv filename.ini" to specify an ini file.
*******************************************************************************

Event log:
<03/11/07@10:24:25> [SHOUTcast] DNAS/Linux v1.9.2 (Nov 25 2002) starting up...
<03/11/07@10:24:25> [main] pid: 5542
<03/11/07@10:24:25> [main] loaded config from sc_serv.conf
<03/11/07@10:24:25> [main] initializing (usermax:10 portbase:8000)...
<03/11/07@10:24:25> [main] No ban file found (sc_serv.ban)
<03/11/07@10:24:25> [main] No rip file found (sc_serv.rip)
<03/11/07@10:24:25> [main] opening source socket
<03/11/07@10:24:25> [main] source thread starting
<03/11/07@10:24:25> [main] opening client socket
<03/11/07@10:24:25> [main] Client Stream thread [0] starting
<03/11/07@10:24:25> [main] client main thread starting
<03/11/07@10:24:25> [source] listening for connection on port 8001
<03/11/07@10:34:06> [source] invalid password from GET /content/sample.pls HTTP/1.1 127.0.0.1

---

### Post by Aberrix on 2007-03-12
> **Joe89 said:**
> How do I put the password in?

did you specifiy it in 'sc_serv.conf' ?

---

### Post by Joe89 on 2007-03-13
I put an admin password in and server pass too.  But how do I use it to get it to work?

---

### Post by daemon_82 on 2007-03-13
Well the password that you have specified in sc_trans.conf must be exactly the same as the one you specified in your sc_serv.conf file, in the password field (not admin pass). That is, the password in the following part:

sc_serv.conf
```
; Password.  While SHOUTcast never asks a listener for a password, a 
; password is required to broadcast through the server, and to perform
; administration via the web interface to this server.  This server should
; consist of only letters and numbers, and is the same server your broadcaster
; will need to enter in the SHOUTcast Source Plug-in for Winamp.  THIS VALUE
; CANNOT BE BLANK.
Password=[COLOR="Red"]your_pass[/COLOR]
```

sc_trans.conf
```
; Password is the password on the sc_serv you're sending to.
Password=[COLOR="Red"]your_pass[/COLOR]
```

---

### Post by Joe89 on 2007-03-13
Where can I find **sc_trans.conf**?  It certainly isnt it the shoutcast folder where **sc_serv.conf** is.

---

### Post by daemon_82 on 2007-03-13
Oh, I hadn't see that you use streamtuner. What I use to broadcast is the shoutcast server and shoutcast DSP Plugin for MacOSX, Linux and FreeBSD (you can find it [here](http://www.shoutcast.com/download/broadcast.phtml#posixdownload) if you want). The configuration file is in it. You download it, extract it in a directory and run it with ./sc_trans_linux sc_trans.conf There are also instructions how to create a playlist.

Anyway, for streamtuner I think what you have to do is to define in your streamtuner configuration exactly the same password with the one in your sc_serv.conf file in password section (again not admin password). But as I don't use streamtuner that's only a guess.

---

### Post by Joe89 on 2007-03-14
Daemon, do me a favor please and read my first post.

---

### Post by Joe89 on 2007-03-16
Can someone **please** help me out here?  I'm no expert at using this OS, so I have no bloody idea what I'm doing the majority of the time.  I just need to get though with the password.  That's it.  Just tell me what to do (using shoutcast & the terminal) and I can be on my way.

Thank you in advance.

---

### Post by andlinux21 on 2007-03-24
There are two files you need to download from the shoutcast website.  I havent read all of the previous posts but if you followed the instructions from the shoutcast site you should have it at least installed.  One folder has the sc_serv in it and the other has the sc_trans_linux.
i open up two xterms one for the ./sc_serv and the other for the ./sc_trans_linux.  It should work if you did everything else ok.

---

