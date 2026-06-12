---
title: "What could affect this behavior ?"
date: 2016-01-21
forum: Server Platforms
---

### Post by soamz on 2016-01-21
Im a host at speedtest.net and it works pretty well.
We have UBUNTU SERVER INSTALLED. 

But I have felt a weird thing with it. 
Normally, everytime I do a speedtest at other cities, who hosts are locally located, the ping starts almost instantly. 
But in my host, the ping test almost takes like 40 seconds to start even. 

What is affecting this lag ?
Any idea ?

Network Design :
Core Router Microtik CCR1009 > Connected to Microtik CRS125 > Speedtest host server is Dell 2950 and its connected to a port of CRS125. 

What do you think could be responsible for the lag ?

See the video to believe :

[https://youtu.be/d-wp9OBuQQI](https://youtu.be/d-wp9OBuQQI)

See my active connections and iptraf screenshot too.
I dont think there is any problem with load or whatsoever. 

Just need to figure out the lag.[ATTACH=CONFIG]266872[/ATTACH][ATTACH=CONFIG]266873[/ATTACH]

---

### Post by nerdtron on 2016-01-21
Ping takes a long time to start? How about trying to dig/nslookup a domain. For example: nslookup [www.ubuntuforums.org](www.ubuntuforums.org)

If the nslookup also takes a long time, then you may need to look into the dns servers on the ubuntu config. Either the DNS servers are not what you intended to be, or that the connection between Ubuntu and the DNS server is problematic.

---

### Post by soamz on 2016-01-21
> **nerdtron said:**
> Ping takes a long time to start? How about trying to dig/nslookup a domain. For example: nslookup [www.ubuntuforums.org]("http://www.ubuntuforums.org")

If the nslookup also takes a long time, then you may need to look into the dns servers on the ubuntu config. Either the DNS servers are not what you intended to be, or that the connection between Ubuntu and the DNS server is problematic.


[FONT=Menlo]jetplex@jetplex:~$ nslookup [www.ubuntuforums.org](www.ubuntuforums.org)[/FONT]
[FONT=Menlo]Server:		8.8.8.8[/FONT]
[FONT=Menlo]Address:	8.8.8.8#53[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]Non-authoritative answer:[/FONT]
[FONT=Menlo]Name:	[www.ubuntuforums.org](www.ubuntuforums.org)[/FONT]
[FONT=Menlo]Address: 91.189.94.12[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]jetplex@jetplex:~$[/FONT]

---

### Post by matt_symes on 2016-02-01
Hi

> **soamz said:**
> Anyone who can help ?

You didn't really address Nerdtron's question.

Did the nslookup command take a while to return ?

Kind regards

---

### Post by soamz on 2016-02-01
> **matt_symes said:**
> Hi



You didn't really address Nerdtron's question.

Did the nslookup command take a while to return ?

Kind regards


It was almost instant. 
May be 1-2 seconds.

---

### Post by matt_symes on 2016-02-01
Hi

Have you contacted your hosting provider to ask them for help ?

You haven't supplied much background information about your setup, so you may be unlikely to get much useful help. That may explain the dearth of answers.

Kind regards

---

### Post by soamz on 2016-02-02
Hosting provider for which thing ?

---

### Post by matt_symes on 2016-02-02
Hi

> **soamz said:**
> Hosting provider for which thing ?

> Im a host at speedtest.net and it works pretty well.

Maybe i misunderstood that last quote from post #1.

Kind regards

---

### Post by MAFoElffen on 2016-02-02
This is just what I do in those circumstances...

Ping to target location and another know location (usually another location I know about that I what to make a test comparison to.) The OP has done that.

Use nslookup in interactive mode query name servers for information about various hosts and domains ... and to print a list of hosts in the target domain. That way I also have the lookup and reverse lookup information.

use traceroute to a target location and a comparable known location.

I've save the output from these over time, to places I need to deal with. I've done this enough from "my location," that I have an idea of the default routes from my region... and what average results should be. I have baselines of data for what is normal ... and when some "other than default" hops are occurring. My ISP has a note in my account file, for their technical support to forward me directly to their network engineers, where I tell them where there might be a problem...

The key in that is "*I have a baseline.*" I can get most of the data to see and compare, from those three basic utilities. Between those 3: Is there a problem? Check DNS,  DNS timings and gather info to go on. Id where the problem may lie.

A long lag for the first ping, then subsequent faster pings, may indicate:
 - Usual reason is lag with DNS name resolution, which members asked to try, but didn't mention why.
 - A default hop between routers being down, so along the way it has work out an alternate route. Once the connection is made, then subsequent's follow that same route. Remember that the internet basically is just a series of routers, with hops set in paths to get between them...

---

### Post by soamz on 2016-02-04
Can this be a reason ?

For example, my server IP is 123.456.789.001 and im in India. 

But speedtest needs 2 domain names like,
abc.domain.com
abc1.domain.com


So, I created two A records in my dedicated server in USA, which has my domains and websites. 
And I simply pointed speed.mydomain.com and speed1.mydomain.com to 123.456.789.001. 


So, can this be a reason that, every ping request goes to USA and then resolves to my IP and then it starts the start ?

Shall I get a new domain and setup inside this 123.456.789.001 server itself ?
So, instead of A record pointing, the domain and IP both will be india, and it can start instant ?

Can this be a reason or solution ?

---

### Post by soamz on 2016-02-11
Okay, may be I did not explain better. 
I will explain again. 
Im from India. 


I have 2 servers. 
1 is based in USA (LiquidWeb Hosting)
2nd is based in India (my in house dell server with public IP)




So, lets say my dedicated server in USA has this domain, [www.abc.com]("http://www.abc.com")


And my server IP is India, is 111.111.111.111


Now speedtest requirements was this : 


> DNS
Two URLs from two distinct hostnames, which point to the same IP address.
Example URL 1: [http://sp1.domain.com/speedtest/upload.php](http://sp1.domain.com/speedtest/upload.php) - 201.12.28.12


Example URL 2: [http://sp2.domain.com/speedtest/upload.php](http://sp2.domain.com/speedtest/upload.php) - 201.12.28.12




Note: Having two URLs from different hostnames allows us to open twice as many HTTP threads in older web browsers, which can help overcome protocol overhead when testing over HTTP. 




So, what I did was, 
I went inside my USA server and created 2 A records for,
speedtest1.abc.com
speedtest2.abc.com and pointed them to my India server public IP. 




I guess, thats what is doing the lag.

---

