---
title: "http server issues"
date: 2008-06-13
forum: Server Platforms
---

### Post by fadetoblack82 on 2008-06-13
hi, i'm having problems with image loading times on my ubuntu box. im running lightthpd, and when i try to load an image off the server it downloads extremely slow, like its dial up - even worse. however, when i access it from another computer within the lan or locally (ie [http://192.168.0.3/image.jpg](http://192.168.0.3/image.jpg) or [http://127.0.0.1/image.jpg](http://127.0.0.1/image.jpg)) it works perfectly. ive also tried apache 2 and i had the exact same problem. ive never had this issue before, so im not sure what the problem could be. any ideas?

---

### Post by windependence on 2008-06-14
So the problem is only when accessing it from an outside IP (outside of your network)?

-Tim

---

### Post by fadetoblack82 on 2008-06-14
> **windependence said:**
> So the problem is only when accessing it from an outside IP (outside of your network)?

-Tim

yes, apparently it's only from outside

edit: sorry, what i meant was: when i access it using the external ip, only then it's slow. even if i access it from a computer in the lan but using the external ip, then the problem occurs.

---

### Post by windependence on 2008-06-14
> **fadetoblack82 said:**
> yes, apparently it's only from outside

Do a traceroute from the oustide and see where the delay is. If you are not sure how to do that from another PC, you can go to dnsstuff.com and they have a tool for it there.

-Tim

---

### Post by fadetoblack82 on 2008-06-14
> **windependence said:**
> Do a traceroute from the oustide and see where the delay is. If you are not sure how to do that from another PC, you can go to dnsstuff.com and they have a tool for it there.

-Tim

i did a traceroute, but im still not sure what the problem is. the analysis at the bottom said:

Analysis:
Number of hops: 19
Last hop responding to ICMP: 19, UDP: 18, TCP: 0.
The destination appears to block unwanted UDP packets.
There appears to be a firewall at 74.53.59.130 (hop 1) that blocks unwanted TCP packets.

74.53.59.130 is some server in texas
$ whois 74.53.59.130

OrgName:    ThePlanet.com Internet Services, Inc.
OrgID:      TPCM
Address:    315 Capitol
Address:    Suite 205
City:       Houston
StateProv:  TX
PostalCode: 77002
Country:    US

---

### Post by windependence on 2008-06-14
Can you post the full output from the traceroute?

-Tim

---

### Post by fadetoblack82 on 2008-06-14
> **windependence said:**
> Can you post the full output from the traceroute?

-Tim

[http://private.dnsstuff.com/tools/tracert.ch?domain=***.homeip.net](http://private.dnsstuff.com/tools/tracert.ch?domain=***.homeip.net)

ill pm you what *** is

---

### Post by windependence on 2008-06-14
Well, I traced it from here and it has considerable lag after it gets to NY. I am in Phoenix, and all the other hops are acceptable. Are you serving directly on port 80 or do you have a redirect? Some of the hops after NY are really long.

-Tim

---

### Post by fadetoblack82 on 2008-06-14
yeah i noticed that too. the servers producing the lag seem to be ISP servers. yes, im serving directly off port 80. i have a standard netgear router which forwards port 80 to my linux machine

edit: im not sure why i initially said there was a problem with image loading times only. its definitely any file, and its not a http problem. scp is also slow from the outside.

---

### Post by windependence on 2008-06-14
> **fadetoblack82 said:**
> yeah i noticed that too. the servers producing the lag seem to be ISP servers. yes, im serving directly off port 80. i have a standard netgear router which forwards port 80 to my linux machine

edit: im not sure why i initially said there was a problem with image loading times only. its definitely any file, and its not a http problem. scp is also slow from the outside.

I don't think it's your problem, I think it's your ISP. have you done a speed test lately?

[http://www.speakeasy.net/speedtest/](http://www.speakeasy.net/speedtest/)

-Tim

---

### Post by fadetoblack82 on 2008-06-14
i just did one on [http://www.speedtest.net/](http://www.speedtest.net/).

it seemed to be alright.. 10mbps down, 500kbps up. but i did it from the other computer on my network. currently i can only ssh into the linux machine. is there some command line speed test or something? got the same results on the speakeasy site

---

### Post by windependence on 2008-06-14
Hmmm... it sounds like somewhere along the line, your ISP is doing something funny with your packets. The bottleneck could also be your router but I kinda doubt it. At this point I know for sure it's not on your server, but what outside your network is causing this I am not sure about. Let me think a bit on this one.

Kind of a long shot but make sure your host files on each machine have aliases for all the other machines in your network. This will speed up lookup time a bit if it's an internal DNS problem. Also, make sure your server has some fast DNS servers listed. You can try 208.67.222.222, and 208.67.220.220 for the secondary DNS. These are OpenDNS servers and they have a huge cache and should be able to resolve things faster for you.

-Tim

---

### Post by fadetoblack82 on 2008-06-14
sure. im just gonna confirm that by installing an ssh or http server on my other machine and see what happens. most probably will get the same results since it seems to be ISP related like you said.

---

### Post by windependence on 2008-06-14
> **fadetoblack82 said:**
> sure. im just gonna confirm that by installing an ssh or http server on my other machine and see what happens. most probably will get the same results since it seems to be ISP related like you said.

Yeah, I had more than 10 hops with over 120ms delay. There is a full second right there. It doesn't sound like much but that is for every request, every image, every page and it adds up to many seconds quickly. You may want to call them to find out what's going on.

-Tim

---

### Post by fadetoblack82 on 2008-06-14
yea i guess i'll give them a call. just to confirm, i did have the same problems on the other machine so it definitely has something to do with my internet connection.

thanks for all the help

---

### Post by MJN on 2008-06-14
> **windependence said:**
> Yeah, I had more than 10 hops with over 120ms delay. There is a full second right there. 

It sounds like you might be misunderstanding the output of traceroute - the timings are from source to each hop, not inter-hop delays. Hence, end-to-end latency is not a sum of each hop timing.

Also bear in mind that traceroute is measuring latency, however what you really want to be measuring is throughput as even with high latency you can still have high throughput, particularly with large TCP window sizes.

Of course, if the OP posted their IP/domain we could all check from our various locations. If this is an Internet facing public server why hide it?

Could your ISP be 'server unfriendly' and throttling common outbound services?

Mathew

---

