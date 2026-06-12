---
title: "New WWW server setup"
date: 2011-03-06
forum: Server Platforms
---

### Post by rwcramer on 2011-03-06
Hi,
I am an experienced computer user with programming experience from about 40 years ago.  I am new to Ubuntu and lynux.  I have a P4 box that I have loaded with Ubuntu Server 10.10.  I an access the default page from my local network but not from the outside.  I have read a lot of documentation and tried several things with no success.  I have set up a vhost website which also works locally.  What I need to do is set up a server box that I can link to from our church web page to make available video files of our services.  It could be as simple as an ftp transfer or as complex as a streaming server, with the latter being preferred.  I have a dyndns.org name set up to us and I can ping that name from the outside, but I can't get to either the FTP server or the WWW server from outside.  I have opened up all the necessary ports on my router to the server IP address.  By default the httpd.conf file is blank.  My isp is charter cable.  What I need is some help configuring the server to work with the outside world.  What am I missing.  As I am new to this I need detailed entries to the conf files and which files need to be modified or added.
Thanks for any help
Ralph

---

### Post by volkswagner on 2011-03-06
First you need to verify the port is open and not blocked by your isp.

From inside you LAN, navigate to canyouseeme.org.

Check port 80 to see if it is open.

---

### Post by rwcramer on 2011-03-06
Thanks for the info.  I am running my virtual server on port 8010 and I can see port 8010 on canyouseeme.org.  I am waiting to see if my son can connect now.  I did have to make a change to my router, as I had it using port 8080.  Looks like I will also have to change the ftp server to use a nonstandard port also. My ISP seems to be blocking ports 80 and 21
Ralph

---

### Post by sergio-bobillier on 2011-03-06
Default configuration files for Apache are ready to work out of the box to allow your site to be accessed from the outside as soon as you install Apache you get your default domain (the one that says "It works") working. So it must be something on your router or your ISP.

Here are some troubleshooting tips:

**[SIZE=3]1.[/SIZE]**
Call your ISP provider to see if they block the 80 port (a lot of ISPs do this, mine does). If that is the case you will need to use an alternative port, for example port 2000. When accessing the we page you will need to do something like this:

```
http://mydomain.dyndns.com:2000
```

Then you'll need to modify the Virtual Host configuration to tell Apache to listen in that port, like so:

```
<VirtualHost *:2000>
```

**[SIZE=3]2.[/SIZE]**
Check the port forwarding in your router to make sure it is forwarding HTTP requests to the desired machine. A good practice when forwarding ports in a router is to give the target machine a static IP so it wont change unexpectedly.

Use a port scan site to make sure the port 80 is reachable from outside.

---

### Post by rwcramer on 2011-03-06
Thanks to all for the help.  Looks like I have the http server working now.  My ISP seems to be blocking ports 80 and 21.  I think I can get the FTP portion working ok, I just need to set it up to use a different port also.  I thought it should all work out of the box, didn't realize the ISP would block ports.  Does anyone know if it is possible to stream video files as it comes out of the box, or is there any add on that will allow you to stream video?
Thanks,
Ralph

---

### Post by Rakeshvijayan on 2011-03-07
> **rwcramer said:**
> Hi,
I am an experienced computer user with programming experience from about 40 years ago.  I am new to Ubuntu and lynux.  I have a P4 box that I have loaded with Ubuntu Server 10.10.  I an access the default page from my local network but not from the outside.  I have read a lot of documentation and tried several things with no success.  I have set up a vhost website which also works locally.  What I need to do is set up a server box that I can link to from our church web page to make available video files of our services.  It could be as simple as an ftp transfer or as complex as a streaming server, with the latter being preferred.  I have a dyndns.org name set up to us and I can ping that name from the outside, but I can't get to either the FTP server or the WWW server from outside.  I have opened up all the necessary ports on my router to the server IP address.  By default the httpd.conf file is blank.  My isp is charter cable.  What I need is some help configuring the server to work with the outside world.  What am I missing.  As I am new to this I need detailed entries to the conf files and which files need to be modified or added.
Thanks for any help
Ralph


You are great beacuse you can do this enough .I was fail on crating websever on my ubuntu.If you have mind to share what you had do with your web configuration 
will help me and others...please share your experience

---

### Post by SeijiSensei on 2011-03-07
> **rwcramer said:**
> Does anyone know if it is possible to stream video files as it comes out of the box, or is there any add on that will allow you to stream video?

This might sound crazy, but I'd recommend that your church open a YouTube account and put the videos there.  Uploading videos to YT is quite easy, and you won't have to deal with the bandwidth requrements streaming demands.

---

### Post by bsntech on 2011-03-07
The only trouble with YouTube is that they typically limit uploads to only 10 minutes.  All uploads that I have made are limited to that - and if it goes over, the upload fails.

Brian S.
BsnTech Networks
[http://www.bsntech.com]("http://www.bsntech.com/services-provided/web-site-design.html")

---

### Post by SeijiSensei on 2011-03-07
That's true, Brian, but I think the OP's options are pretty limited.

Even with a least-common-denominator solution like XviD at 360p or 480p resolution in the AVI or Flash container, an hour of decent quality video will probably run something like 200-300 MB.  Using the x264 encoder would help some, but still not make a dramatic difference.  (Support for decoding using the H.264 codec is also a bit iffy on older systems.)  Serving files this size on a consumer-level connection, using the always much more limited upstream bandwidth, will saturate the line pretty quickly.  Particularly if this is intended as a quasi "real-time" service for shut-ins and the like where you'd expect to have a number of simultaneous connections on Sundays.

I just don't think streaming is going to work off a P4 box connected to a residential Charter account (ignoring for the moment the issues about violating Charter's terms-of-service).  At a minimum, I'd look for a hosted solution like a virtual server with access to a big pipe and niceties like backup power.

---

### Post by bsntech on 2011-03-07
Agreed.  I always post my videos on YouTube - just for the fact that it is less bandwidth from my systems.

---

