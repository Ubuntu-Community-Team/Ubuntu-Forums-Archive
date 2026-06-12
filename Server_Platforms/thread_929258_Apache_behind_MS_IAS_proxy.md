---
title: "Apache behind MS IAS proxy"
date: 2008-09-24
forum: Server Platforms
---

### Post by Pencilpen on 2008-09-24
Hi,
I have a problem with my installation however in reading through this forum I'm not sure whether it's Apache related or PHP but I'll post here in the hope someone can steer me in the right direction.

I'm running Apache 2.2.8 on a Hardy Heron box sitting on a LAN with WWW access via an MS IAS. My website is only accessable from the LAN and that's all I want. 

However I've added rss newsfeeds to the website and so the website itself needs www access to fetch the feeds. I'm getting 407 authenfication errors from the IAS. I have set up a small proxy server on the Ubuntu box (cntlm on port 3128) which works well for Ubuntu however I'm having problem getting whatever is doing the fetching for the newsfeeds to go through cntlm.

Is it likely that Apache is the one not getting web access or is it more likely to be PHP? The website is PHP based = Joomla. 

The IAS access log entries have this information:
Dest IP: 210.50.4.217
Dest Port: 80
Proto: http
Action: Denied
Client IP : 192.168.5.5
Client Username: anonymous

or, using a different configuration:
Dest IP: 192.168.5.1
Dest Port: 8080
Proto: (blank)
Action: Failed Connection Attempt
Client IP: 192.168.5.5
Client Username: anonymous

192.168.5.5 is my Ubuntu box, 192.168.5.1 is the ISA server.

TIA
Karl

---

### Post by Pencilpen on 2008-09-29
OK, just in case anyone has this problem in the future, here was my solution:

The problem was that simplepie - the routine used by Joomla's newsfeed to get the feeds, needed to be steered to use my proxy server. I found the solution here:
[http://simplepie.org/support/viewtopic.php?id=1133](http://simplepie.org/support/viewtopic.php?id=1133)
but there was a reasonable amount of work to implement it - not for the faint-hearted. I had to make the mods as listed in this thread to my file
/home/kgnews/public_html/libraries/simplepie/simplepie.php

This mod is based on simplepie 1.0.1 however I'm using the next version so I had to do a bit of sleuth work - not too hard though. 

The end result = newsfeeds working from behind a MS ISA server Yahoo!!!  :D

---

