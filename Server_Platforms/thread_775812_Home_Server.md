---
title: "Home Server"
date: 2008-04-30
forum: Server Platforms
---

### Post by MotherMayI on 2008-04-30
Over the next few days I am looking to set up a home server for me and my house mates. What I'm aiming for this to be able to do is:
- Be a simple file server.
- HTTP + mail server if possible, but not entirely necessary.
- FTP server.
- Some form of remote control.
- Remotely download torrents.

The computer I have set aside for this is an old Mac G3, with 256mb RAM. Would that be sufficient for my needs? Obviously the HDD's will need upgrading, as I think it currently only has an 8gb disk, but I can't see that being much of an issue - I'm sure I'll have some old IDE HDD's sitting around somewhere.

Thanks.

---

### Post by tamoneya on 2008-04-30
seems fine to me especially if you isntall the server edition instead of the desktop edition.  The loads shouldn't be to heavy so even on your limited hardware ubuntu should be fine.

---

### Post by MotherMayI on 2008-04-30
I thought that, but then read:

[http://www.linux.com/forums/topic/1061](http://www.linux.com/forums/topic/1061)

Are you sure that it will be capable?

---

### Post by tamoneya on 2008-04-30
if you dont run a gui you should be alright.  You are planning on using it as a server and not having a heavy load so i think it will work.

---

### Post by Dr Small on 2008-04-30
Setup Apache (Web Server), Postfix (Mailserver), Courierpop3 (POP3 Server), gProFTP (FTP Server. Note, FTP is insecure.), Openssh-server (For remote control).

---

### Post by MotherMayI on 2008-04-30
With just these services running, and no running (although I will probably keep one installed), the G3 will be ok?

---

### Post by daschl on 2008-04-30
well it really depens on what you and your friends do with it.. if "your friends" are 100 people and you use it as a corporate server where your files will be accessed every minute it may be not enough, but for "home access" it will be alright.. 

the best method for home use is: just try it. ubuntu is free so you dont have to pay for it and then get in trouble when you realize that it isnt working correctly.. if you find out that your system is running out of memory / or disk space / or cpu you can then upgrade the needed part later, you will not have to reinstall ubuntu again.

hth

---

### Post by Brazen on 2008-04-30
I run Ubuntu 6.06 Server as a Samba file server on a computer with 32mb of RAM and it works just fine.  Downloading torrents through your server is what is going eat up your RAM though.

I use torrentflux-b4rt on Ubuntu 6.06 Server and it pushes the limit with 392mb of RAM. This is with no gui or anything else extra on top of the base OS load except for Apache w/php which is required by torrentflux.  It also requires a MySQL database, but that is running on another computer.

---

### Post by MotherMayI on 2008-04-30
I had no idea that torrentflux would be so RAM intensive. I'm also going to have to run MySQL from the same box, so I assume im going to run in to serious memory problems?..

---

### Post by fiatguy85 on 2008-05-01
I just set up something similar the other day on a 500MHz P3 w/ 256MB RAM.  I'm running apache, mysql, and torrentflux.  It works ok, definitely eats up all of the memory, and torrentflux takes up most of the cpu too.  I'm running a variant called [UbuntuLite]("http://ubuntulite.tuxfamily.org/").  It's designed for older hardware.  I installed the command line version of it, and then openssh-server must be installed off the cd to access it remotely.

---

### Post by MotherMayI on 2008-05-01
Well, in the end I got myself an AMD2000 and 256mb RAM for the same price - So I think I'll be fine.

Just got to wack some massive HDD's in it now and get busy..

Thanks for your advice guys, and I'll look in to UbuntuLite.. Although with an AMD2000, I doubt ill have any problems.

---

### Post by exaviorn on 2008-05-01
This might be a bit of-topic but i would say that it would be easy to do what you want to do (I have done something similar:))I would say that the hardest thing would be setting up a mail server :lolflag: but it is still not that hard (I had my mail server set up in a day)

---

### Post by MotherMayI on 2008-05-02
Well, heres hoping.

I also plan on making some kind of web interface for my house mates to easily use and so on. To be honest, I'm not too bothered about the difficulty of the project as I am doing it, in many ways, to advance my understanding of Linux as much as I am for a practical purpose.

---

### Post by fiatguy85 on 2008-05-02
That's a good philosophy, I enjoy doing the same.  After tweaking some settings real quick, I have gotten memory usage down to under 160MB on my server, so it is running great.  I slimmed down apache and mysql's memory usage, so what you were envisioning seems pretty easily accomplished, even on the old hardware.

---

