---
title: "how to install a camera in zoneminder"
date: 2013-08-05
forum: Server Platforms
---

### Post by rob8 on 2013-08-05
I have anran model c754r hd h.264 compatible cameras but i can get them to work with zoneminder. How do i add the cameras. I installed the h.264 pack.

I believe my problem is finding the correct remote host path. They are ip cameras working on the network. I have the ip address and port i also have rtsp on. Any ideas?  I have a server just for this job that hosts my media. I would like to add this to its job roll.

---

### Post by wyliecoyoteuk on 2013-08-05
Often, if you log in to the web interface for the camera, hovering over the links for various parts (e.g. display image), the actual link URL will be shown at the bottom of the screen.
you may need to include a username and password in the hostname link e.g. ```
user:password@<ipaddressofcamera>
``` and the path e.g. /videostream.cgi?rate=0

---

### Post by rob8 on 2013-08-06
I logged in to the camera and all I could get for links was the ip address/longin but nothing when going over the video or playing with settings. I was very hopeful but nothing. Any other ideas?

---

### Post by wyliecoyoteuk on 2013-08-06
Well, short of googling the camera or the zoneminder forums to see if anybody else knows the correct url, no, sorry.

---

### Post by wyliecoyoteuk on 2013-08-06
Well, short of googling the camera or the zoneminder forums to see if anybody else knows the correct url, no, sorry.
It looks like it is an Amovision clone

AM-N9C754R

---

### Post by rob8 on 2013-08-07
> **wyliecoyoteuk said:**
> Well, short of googling the camera or the zoneminder forums to see if anybody else knows the correct url, no, sorry.
It looks like it is an Amovision clone

AM-N9C754R

Could not find anyone who has installed these. I am guessing my cameras use activex and that wont work with zm I have read.

---

### Post by wyliecoyoteuk on 2013-08-07
Even if it uses ActiveX, it may also offer a java connection many do.
If you can connect to it with an Android phone, it can be used with Zoneminder, but you may need to use the mobile url.
The Amovision version supports VLC.

---

### Post by wyliecoyoteuk on 2013-08-07
This link may help.
[http://www.ispyconnect.com/man.aspx?n=ANRAN](http://www.ispyconnect.com/man.aspx?n=ANRAN)

---

### Post by rob8 on 2013-08-07
I will look into that thanks. My cameras do work with my Android phone so I will look at this new way. Thanks

---

### Post by tduncklee on 2013-09-23
rob8,

I managed to get an Anran VGB101-IP working with ZoneMinder. I've added it to the ZoneMinder Hardware Wiki. Maybe it will work for your camera. I found it best to use VLC to test the url with first. This camera requires ActiveX and I have it working with ZM.
[http://www.zoneminder.com/wiki/index.php/Hardware_Compatibility_List#Network_Cameras](http://www.zoneminder.com/wiki/index.php/Hardware_Compatibility_List#Network_Cameras)

---

