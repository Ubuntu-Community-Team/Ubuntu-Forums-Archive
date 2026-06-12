---
title: "Question about apache log and a connection"
date: 2010-06-24
forum: Security
---

### Post by Cyked on 2010-06-24
Here is basically what I am seeing in my apache logs (I alerted slightly to remove the IP and the actual file names).  This is the ONLY lines that were logged from this IP (which is in Oslo).  I see the GET /favicon.ico all the time, typically from bots.  I don't typically see the GET /files/.  Directory browsing is turned off, so you get a 'forbidden' error for most all directories anyway, including the /.temp dir.

```

[23/Jun/2010:20:25:17 -0700] "GET /files/ HTTP/1.1" 403 179 "-" "Opera/9.80 (iPhone; Opera Mini/5.0.0198/18.794; U; en) Presto/2.4.15"
[23/Jun/2010:20:25:17 -0700] "GET /favicon.ico HTTP/1.1" 404 183 "http://mysite.com/files/" "Opera/9.80 (iPhone; Opera Mini/5.0.0198/18.794; U; en) Presto/2.4.15"
[23/Jun/2010:20:25:47 -0700] "GET /.temp/file.txt HTTP/1.1" 401 290 "-" "Opera/9.80 (iPhone; Opera Mini/5.0.0198/18.794; U; en) Presto/2.4.15"
[23/Jun/2010:20:26:07 -0700] "GET /.temp/file.txt HTTP/1.1" 401 290 "-" "Opera/9.80 (iPhone; Opera Mini/5.0.0198/18.794; U; en) Presto/2.4.15"
<login ID> [23/Jun/2010:20:26:07 -0700] "GET /.temp/file.txt HTTP/1.1" 200 14382 "-" "Opera/9.80 (iPhone; Opera Mini/5.0.0198/18.794; U; en) Presto/2.4.15"

```


I added the file.txt to /.temp just that day (idk, maybe around 14:00:00 on the 23rd.  My question is how in the crap did someone find just this one file, and DIDN'T get the other two txt files in that folder?  The 3rd and 4th entries are failures since the directory is PW protected, and then the 5th and last entry they get the file with the correct ID and PW.  I'm just using authtype basic and the user ID and PW is nothing crazy.

Thoughts?



Also, I'm seeing these in auth log.  I do use SSH and tunnel sometimes through FF.

```
sshd[24433]: error: connect_to xxx.xxx.xxx.xxx port 15871: failed.
```

I'm not putting 2 and 2 together here, racking my brain trying to figure this out.  This has something to do with the open ssh connection because the 24433 is the PID.

---

### Post by cdenley on 2010-06-24
Browsers often attempt to download /favicon.ico to display the little icon you often see next to the URL in the browser. That looks like somebody using an iPhone (although this can easily be spoofed) attempted and failed to browse to /files/, at which point the browser also attempted to retrieve an icon. Thirty seconds later they navigate directly to /.temp/file.txt (no referer), apparently enter an incorrect login on the first try, then a correct one on the second try.

How did you "add" that file?

---

### Post by anomie on 2010-06-24
[QUOTE=Cyked]I added the file.txt to /.temp just that day (idk, maybe around 14:00:00 on the 23rd.  My question is how in the crap did someone find just this one file, and DIDN'T get the other two txt files in that folder?[/quote]

Similar to the previous poster, I would be curious to know how you uploaded file.txt. If you did it clear text (i.e. over ftp), then someone could have easily determined where you put it. 

I'm presuming you have triple-checked that Options -Indexes is working for that directory. 

[QUOTE=Cyked]I'm just using authtype basic and the user ID and PW is nothing crazy.[/quote]

Sounds like it's time to switch to HTTP digest authentication, and beef up your password requirements a bit. 

[QUOTE=Cyked]```
sshd[24433]: error: connect_to xxx.xxx.xxx.xxx port 15871: failed.
```

I'm not putting 2 and 2 together here, racking my brain trying to figure this out.  This has something to do with the open ssh connection because the 24433 is the PID.[/QUOTE]

Whole other topic (unrelated to the first). Possibly AllowTcpForwarding is on, and someone's up to no good? 

[ BTW, Arrogant Bastard Ale == good. ]

---

### Post by Cyked on 2010-06-24
So figured out the first part.  The opera mini browser on iphone uses some sort of... something.  Proxy?  Redirect?  It was ME that accessed the file from home, totally slipped my mind.  The source IPs I see from when using opera are 64.255.180.xxx, 64.255.164.xxx (obviously not internal IPs).  I'm curious why they do this.

Still sort lost on the second thing with the sshd[24433]: error: connect_to xxx.xxx.xxx.xxx port 15871: failed. messages I'm seeing in the auth log.  I get that its something over the tunnel I've opened from my laptop, but not getting that something is being logged because I did X.

---

### Post by cdenley on 2010-06-24
> **Cyked said:**
> So figured out the first part.  The opera mini browser on iphone uses some sort of... something.  Proxy?  Redirect?  It was ME that accessed the file from home, totally slipped my mind.  The source IPs I see from when using opera are 64.255.180.xxx, 64.255.164.xxx (obviously not internal IPs).  I'm curious why they do this.

Still sort lost on the second thing with the sshd[24433]: error: connect_to xxx.xxx.xxx.xxx port 15871: failed. messages I'm seeing in the auth log.  I get that its something over the tunnel I've opened from my laptop, but not getting that something is being logged because I did X.

Well, I believe the opera browser for mobile devices is so fast because it proxies the connection, then delivers a compressed image of the page to the user. When you zoom in, it downloads a more detailed image. This limits the data which must be transferred over your phone's data network, since that is usually a bottleneck.

What are you tunneling through your SSH server? Are you using it as a proxy? Do you know the IP it is attempting to connect to? Was that your session?

---

### Post by Cyked on 2010-06-24
> **cdenley said:**
> Well, I believe the opera browser for mobile devices is so fast because it proxies the connection, then delivers a compressed image of the page to the user. When you zoom in, it downloads a more detailed image. This limits the data which must be transferred over your phone's data network, since that is usually a bottleneck.

Makes sense, I didn't really consider that.

> **cdenley said:**
> 
What are you tunneling through your SSH server? Are you using it as a proxy? Do you know the IP it is attempting to connect to? Was that your session?

For the second thing?  Well, one of the IPs is 67.15.245.6 (siteground hosting/ThePlanet.com Internet Services, Inc.) hosting for a forum I visit.  The one that is throwing me:

```
sshd[24433]: error: connect_to 192.168.42.42 port 80: failed.
```

.42 is not my subnet, and is not the subnet o the computer I am connecting with.  In the end I think that I am just over thinking this.  Obviously these are connections coming across on the tunnel.

To answer your other question.  I'm tunneling Firefox through it mostly and sometimes Trillian for IM.

---

### Post by FuturePilot on 2010-06-24
> **cdenley said:**
> Well, I believe the opera browser for mobile devices is so fast because it proxies the connection, then delivers a compressed image of the page to the user. When you zoom in, it downloads a more detailed image. This limits the data which must be transferred over your phone's data network, since that is usually a bottleneck.

Yes that is correct. Opera Mini proxies everything through one of their servers which strips unnecessary junk from web pages and compresses images to decrease loading times and to save bandwidth.

---

### Post by anomie on 2010-06-24
[QUOTE=Cyked]The one that is throwing me:

```
sshd[24433]: error: connect_to 192.168.42.42 port 80: failed.
```

.42 is not my subnet, and is not the subnet o the computer I am connecting with.[/QUOTE]

192.168/16 is on RFC 1918 [private network](http://en.wikipedia.org/wiki/Private_network) space. Odd indeed.

---

### Post by yeleek on 2010-06-25
Given 192.168/16 can't be routed over the internet, what about a local connection?  Whats the LAN look like?  And do you have iptables logging, that giving anything up?

---

### Post by Cyked on 2010-06-25
> **yeleek said:**
> Given 192.168/16 can't be routed over the internet, what about a local connection?  Whats the LAN look like?  And do you have iptables logging, that giving anything up?

Nothing in iptables that would catch it.  I'm pretty much just logging and dropping traffic from obvious bots and brute force type stuff.

You mean the local connection from the source machine I'm on?  Class B, its not 192.168/16.

No idea what it was, but it was something going over the SSH tunnel and was coming from the browser. Its really the only thing I run through it.

---

### Post by yeleek on 2010-06-25
'You mean the local connection from the source machine I'm on? Class B, its not 192.168/16.'

No i mean to the server itself i.e. is the external connection natted but the internal network a 192.168/16 meaning the connection didn't come from the internet but within the office or data centre?

---

### Post by Cyked on 2010-06-25
Yeah, not sure.  I don't think so.  At home the server is behind two routers running Tomato, both same subnet.  The first.... dude you're avatar is really starting to freak me out lol...

anywho.  the first is wired to an ATT uverse RG which does pretty much nothing other than have a coax cable connected to it.. It passes my internet IP directly to the first router.  Then the server and an XP machine are wired to the other router in another room, which is bridged back to the first router.

---

### Post by yeleek on 2010-06-28
LOL - can't beat blackadder.

TBH will be interested to hear if you find out, only thing I can think of is 192.168 is local to the device itself somehow.

---

