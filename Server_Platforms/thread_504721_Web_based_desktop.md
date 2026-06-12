---
title: "Web based desktop"
date: 2007-07-19
forum: Server Platforms
---

### Post by t_ras on 2007-07-19
Is there any web based  ([HTTP://port](HTTP://port) 80) for linux? so I connect to my comp through browser?
thanks

---

### Post by reckless2k2 on 2007-07-19
umm...do you mean like how you run remote desktop through port 80 on xp? if so, there is rdesktop in ubuntu. i believe it is in the admin menu how you can set it up but you need vnc on the client like tightvnc executable. you have to specify the terminal as well like pick 1 instead of 0.

---

### Post by t_ras on 2007-07-19
I tried it once, but filed to configure thr VNC client for port 80 :(

---

### Post by reckless2k2 on 2007-07-19
well vnc typically run off 5900 or around that range stock. you'd have to run a vnc client on the windows side to connect to rdesktop on the ubuntu side. i'm not sure if we are on the same page or if this is what you're even tryign to do. i was aksing if you are looking for a remote desktop solution in linux. if that was the port 80 issue or why.

---

### Post by t_ras on 2007-07-20
I tried VNC from the wincomp before, but 
1)didn't find out how to configure the VNC client for port 80.
2) I have webserver also on my comp, and though I have 2 NICs with different addresses I failed to configure ISPconfig/HTTPd to use one and VNC to use the other
For the reasons above I though maybe there is maybe an "otu of the box" solution for this...
thanks any way

---

### Post by Motoxrdude on 2007-07-20
I am pretty sure you can't use port 80 for vnc. Why not use it's default port?

---

### Post by t_ras on 2007-07-21
Because I'm a consultant and many times I have to connect from my customers networks, which are mostly behind a firewall...

---

### Post by agurk on 2007-07-21
Have a look at [Webmin](http://www.webmin.com), perhaps it'll suit your needs, there is a demo available. It can be extended with various plugins.

---

### Post by az on 2007-07-21
> **t_ras said:**
> I tried VNC from the wincomp before, but 
1)didn't find out how to configure the VNC client for port 80.
2) I have webserver also on my comp, and though I have 2 NICs with different addresses I failed to configure ISPconfig/HTTPd to use one and VNC to use the other
For the reasons above I though maybe there is maybe an "otu of the box" solution for this...
thanks any way

sudo gconf-editor

Select Apps - Desktop - remote-access  and then edit the alternative-port key.

But, no, two things cannot use the same port.

> **t_ras said:**
> Because I'm a consultant and many times I have to connect from my customers networks, which are mostly behind a firewall...

Can't you route port 80 to another port on your computer.

---

### Post by lawentzel on 2007-07-24
I don't know of a router or a firewall that doesn't allow you to provide access to specific ports if you know about it in advance.  Another option to look into is [http://www.logmein.com](http://www.logmein.com) it is a remote access program that appears to be JAVA based.  If you go with the free version you have complete access to the computer.  If you need to copy files to it or from it, you then have to get creative.  I just open up a browser, and log into my person email address, and upload or download the files that way.  Other then that...  Port 80 is reserved for HTML.  IE websites.

---

