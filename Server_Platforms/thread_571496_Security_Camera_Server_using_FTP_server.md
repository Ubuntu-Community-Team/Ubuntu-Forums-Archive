---
title: "Security Camera Server using FTP server"
date: 2007-10-09
forum: Server Platforms
---

### Post by cjblade54 on 2007-10-09
I just recently installed some sercurty cameras around the buildings of my job site.  I am currently using proftpd server on my Ubuntu box.  However, the camera has its own FTP client installed.  To make it secured, it has user name with password which are the function i want to use.  My question is, how do i create the user name and password on the sever side so the camera (FTP client) can send its image to my server (every 30 seconds).  Please help~!!

---

### Post by quietas on 2007-10-09
If they are IP based cameras like that, I'd actually take a look at Zoneminder ([http://www.zoneminder.com]("http://www.zoneminder.com")). They do web based camera recording and monitoring with full motion detection capablities. I've got it set up at work running 6 analog cameras at 5 locations.

It's easier and a lot more usable than just dumping photos or video to an FTP server.

---

