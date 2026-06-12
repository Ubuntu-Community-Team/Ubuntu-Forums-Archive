---
title: "Server hacked, I think its used  as web proxy."
date: 2011-12-16
forum: Security
---

### Post by Lipozo on 2011-12-16
Hello,

I've noticed huge outgoing traffic from my server (Ubuntu Server 10.04, t has Apache installed, and running one website which is supposed to be only for internal use)
 From squid log files i see that is huge outgoing traffic from that server, what makes me to think that the server is used as web proxy.

Need some advice's(help) what should i check and what to do and stop that outgoing traffic from the server. 

Thanks in advance :)

---

### Post by Ms. Daisy on 2011-12-16
I'm sure one of the experts will be along shortly to help you.

In the meantime, take it off line until you can secure it.

---

### Post by haqking on 2011-12-16
So is the webserver internal then ? if so why is it external facing ?

what ports is the outgoing traffic on and to what destination ?

auth.log for any compromises ?

does it run services such as SSH or VNC or similar ?

need more info

---

### Post by HermanAB on 2011-12-16
First unplug the network cable, then look at the log files.

---

### Post by Dangertux on 2011-12-16
> **Lipozo said:**
> Hello,

I've noticed huge outgoing traffic from my server (Ubuntu Server 10.04, t has Apache installed, and running one website which is supposed to be only for internal use)
 From squid log files i see that is huge outgoing traffic from that server, what makes me to think that the server is used as web proxy.

Need some advice's(help) what should i check and what to do and stop that outgoing traffic from the server. 

Thanks in advance :)

Are you sure you aren't running squid as an open proxy? Check your ACL's and let us know.

---

### Post by Lipozo on 2011-12-17
> **haqking said:**
> So is the webserver internal then ? if so why is it external facing ?

what ports is the outgoing traffic on and to what destination ?

auth.log for any compromises ?

does it run services such as SSH or VNC or similar ?

need more info

Yes it runs SSH and VNC , i checked auth.log and nothing there also. 
only one part of the web server is visible from outside and its on port 80, and all that is routed thru firewall which is other server.

---

### Post by Lipozo on 2011-12-17
> **Dangertux said:**
> Are you sure you aren't running squid as an open proxy? Check your ACL's and let us know.


Squid runs fine, i actually blocked any kind of traffic from that server that goes outside. But the problem exists on that server, i runed live log from squid and i still see that lots of requests come from the webserver and they are deny-ed by squid.

---

### Post by Lipozo on 2011-12-19
any one got any ideas?

---

### Post by Dangertux on 2011-12-19
[LEFT]What does the traffic in the logs look like? Can you post an example, I have an idea of what's up but I can't be positive until I see the log your looking at.
[/LEFT]

---

### Post by Lipozo on 2011-12-19
> **Dangertux said:**
> [LEFT]What does the traffic in the logs look like? Can you post an example, I have an idea of what's up but I can't be positive until I see the log your looking at.
[/LEFT]

This is squid report, and the list goes on.....

	ACCESSED SITE	CONNECT	BYTES	%BYTES	IN-CACHE-OUT	ELAPSED TIME	MILISEC	%TIME
	[www.google.com](www.google.com)	22.05K	1.24G	27.52%	0.00%	100.00%	23:08:14	83,294,641	0.38%
	search.yahoo.com	6.25K	209.12M	4.62%	0.00%	100.00%	02:22:00	8,520,255	0.04%
	images.google.com	3.61K	109.47M	2.42%	0.00%	100.00%	03:08:43	11,323,344	0.05%
	[www.bing.com](www.bing.com)	2.48K	92.63M	2.05%	0.00%	100.00%	00:33:12	1,992,136	0.01%
	[www.baidu.com](www.baidu.com)	10.87K	90.80M	2.01%	0.02%	99.98%	03:44:29	13,469,159	0.06%
	fayazi-vahid.blogfa.com	1.41K	69.42M	1.53%	0.00%	100.00%	01:03:05	3,785,973	0.02%
	sk.archive.ubuntu.com	83	60.20M	1.33%	13.46%	86.54%	07:00:28	25,228,800	0.12%
	[www.qdjimo.com](www.qdjimo.com)	1.84K	59.70M	1.32%	0.00%	100.00%	01:44:08	6,248,249	0.03%
	[www.hardware.com.br](www.hardware.com.br)	2.77K	54.08M	1.20%	0.00%	100.00%	00:29:16	1,756,774	0.01%
	hentaiforumz.com	2.88K	48.46M	1.07%	0.00%	100.00%	00:15:12	912,089	0.00%
	twitter.com	1.72K	43.45M	0.96%	0.00%	100.00%	00:52:29	3,149,594	0.01%
	[www.google.ru](www.google.ru)	730	36.08M	0.80%	0.00%	100.00%	00:35:44	2,144,835	0.01%
	[www.ticketmaster.com](www.ticketmaster.com)	186	35.03M	0.77%	0.00%	100.00%	00:54:39	3,279,502	0.02%
	[www.zazzle.com](www.zazzle.com)	335	29.18M	0.64%	0.00%	100.00%	00:45:48	2,748,804	0.01%
	bamasportsforum.com	281	25.24M	0.56%	0.65%	99.35%	01:51:15	6,675,070	0.03%
	hpcgi3.nifty.com	1.82K	24.45M	0.54%	0.00%	100.00%	00:40:45	2,445,526	0.01%
	globalvoicesonline.org	212	21.78M	0.48%	42.26%	57.74%	00:23:57	1,437,255	0.01%
	[www.megaupload.com](www.megaupload.com)	1.79K	18.00M	0.40%	0.00%	100.00%	00:47:35	2,855,859	0.01%
	[www.yahoo.com](www.yahoo.com)	132	17.32M	0.38%	0.00%	100.00%	01:12:11	4,331,524	0.02%
	hpcgi1.nifty.com	1.02K	17.27M	0.38%	0.00%	100.00%	00:25:09	1,509,861	0.01%
	[www.denic.de](www.denic.de)	3.24K	16.98M	0.38%	0.00%	100.00%	00:16:30	990,099	0.00%
	[www.alexa.com](www.alexa.com)	130	15.48M	0.34%	0.00%	100.00%	00:11:10	670,143	0.00%
	ams-teardrop4.cdn.maases.com	1	14.91M	0.33%	0.00%	100.00%	00:50:00	3,000,664	0.01%
	[www.jimotuangou.com](www.jimotuangou.com)	14.31K	14.49M	0.32%	0.00%	100.00%	3517:25:00	12,662,700,985	58.09%

---

### Post by lisati on 2011-12-19
Random thought: squid is a proxy system.

---

### Post by Dangertux on 2011-12-20
Yeah are you utilizing squid as a caching proxy? Because it looks like you are.. Unless those aren't sites you visit.

Though... I would wager that would be your traffic check /var/log/squid/access.log for more information.


Hope this helps.

---

### Post by Lipozo on 2011-12-23
> **Dangertux said:**
> Yeah are you utilizing squid as a caching proxy? Because it looks like you are.. Unless those aren't sites you visit.

Though... I would wager that would be your traffic check /var/log/squid/access.log for more information.


Hope this helps.

Problem isn't with squid, squid server is totally different server.
Those log of visited sites are from the web-server which i mention i starting post :)

---

### Post by sourchier on 2011-12-25
Did you configure your acl security as described here?
[https://help.ubuntu.com/community/Squid]("https://help.ubuntu.com/community/Squid")

Did you secure bind as described here?

[http://jazzymarketing.com/main/lc/0904/open-resolver-securing-bind-server]("http://jazzymarketing.com/main/lc/0904/open-resolver-securing-bind-server")

Are you running ufw to control access to your servers? You need to check these things and then report back. Thanks.

---

### Post by Lipozo on 2012-01-03
Problem isn't in squid, i am asking help for the web server which is totally different server.

---

### Post by Drenriza on 2012-01-03
If your internal server is being used for external use. And it isn't suppose to be reachable to the WAN except on port 80. Setup a ACL on your network / server (that is in the line before your internal server) and create a ACL that defines the following.

Block any traffic (except port 80) from external port which is going to internal server.
You can do this by creating a ACL that states. Example is from Cisco router, so tweek it to your need.

allow tcp 80 from external-ip to internal-server
a invisible deny all will deny all other traffic from external interface to internal server. Which is what you want?

Personally i would purchase a Cisco (e-bay) router if i was you, and control the network flow like this, directly in the router. I do not and wont understand, why you would ever control ACL,s and security features on a server and not on the network infrastructure. That is leading the traffic from source to destination. Which also free server resources.

My 2 cents.

---

