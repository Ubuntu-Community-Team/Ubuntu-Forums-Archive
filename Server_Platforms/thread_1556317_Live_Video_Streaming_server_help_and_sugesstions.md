---
title: "Live Video Streaming server help and sugesstions"
date: 2010-08-19
forum: Server Platforms
---

### Post by anoopch on 2010-08-19
Hi friends..

Hope you all are fine and enjoying your life..:popcorn:

I am thinking of setting-up a live streaming camera at my home. 

Scenario:
I want to see live video of a cameras fitted at my home.

Solution:

Ubuntu server is the OS possibly..

I need suggestions regarding hardware and software components required. Please give me some detailed info because i'm a novice user.:lolflag:

---

### Post by stlsaint on 2010-08-19
Google is awesome! ;)
[http://hacktivision.com/index.php/2009/06/16/setting-up-an-ubuntu-webcam-server?blog=2](http://hacktivision.com/index.php/2009/06/16/setting-up-an-ubuntu-webcam-server?blog=2)

NOTE: Ive never set this up so ensure all your data is backed up and safe as with any project you would work on!!

---

### Post by anoopch on 2010-08-20
> **stlsaint said:**
> Google is awesome! ;)
[http://hacktivision.com/index.php/2009/06/16/setting-up-an-ubuntu-webcam-server?blog=2](http://hacktivision.com/index.php/2009/06/16/setting-up-an-ubuntu-webcam-server?blog=2)

NOTE: Ive never set this up so ensure all your data is backed up and safe as with any project you would work on!!


I saw it but its not streaming.. Its capturing or clipping. It consumes more resources and is an old technology.:lolflag:

I need an arrangement similar to CCTV camera...

---

### Post by TJet1.8 on 2010-08-21
Assuming you are using the latest Ubuntu server 10.04.1, you can install ZoneMinder...which is a VERY good CCTV application.

sudo apt-get install zoneminder

The installation will install apache2 and MySQL for the ZoneMinder CCTV application.

Please note that ZoneMinder DOES NOT start working immediately once installed, you need to run a couple of commands to get the database instance into MySQL and to get the Web interface into apache.

Follow this guide:
[http://ubuntuforums.org/showthread.php?t=1535947](http://ubuntuforums.org/showthread.php?t=1535947)

Once configured, you can access Zoneminder via your new apache2 web server:
http://<your_server_ip>/zm

Zoneminder can connect to both IP camera's and camera's that use DVR cards in your PC.
 
It streams LIVE pictures via the web interface.
It can stream multiple camera's over the same web interface.
It can capture video based on motion...or continuously.

You can view your camera's over the Internet as it is a web service...after all...

I love it!!

I run it on a Nettop mini pc that has an Intel Atom 330 processor (dual-core, hyperthreading, 1.6GHz) and 2GB of RAM running Ubuntu server 10.04 x64.
My Nettop does EVERYTHING for my home network (i.e. - Print server, NAS, CIFS, SAMBA, Media server, CCTV server, Linux DDNS, DHCP, etc...)
With 3 IP camera's, CPU utilization is around 16% when NOT streaming IP camera video...and 40% when streaming all 3 camera's
The Zoneminder uses almost all of the CPU utilization listed above....the other server functions barely use 1% of the CPU.

Good luck :popcorn:

---

### Post by anoopch on 2010-08-22
[TJet1.8]("http://ubuntuforums.org/member.php?u=805048")..

Thanks a lot buddy... the article was very nice.. I will post once i implement it completely.

---

### Post by anoopch on 2010-08-22
the resource usage calculation was awesome.. It helped me to decide on the type of server that i need for setting up the streaming server..

PLanning for a c2d @ 1.5 - 2 GHz with 1 gb ram or so..

---

### Post by pattywu on 2010-10-25
Hey,

For the live streaming server, I have found a really simple and easy to manage video platform. All you need is sign up your account and create your own channel. Then, you can start streaming with your own webcam or if you have video files that you want to broadcast through the internet, you can create the playlist and upload all videos. Sounds really easy, isn't it? Go to [www.dacast.com](www.dacast.com) and you will find useful info for live streaming.

---

### Post by dani.geamanu on 2011-02-19
I want to make a website with live streaming, something like [http://www.livestream.com/](http://www.livestream.com/) , for my country! (an online television )  I do not know exactly what I need. Also if you cannot tell me everything, I can pay a developer to help me. I am a webdesigner, but I am new with this video stuff! Please help, thanks!

---

