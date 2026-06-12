---
title: "ufw logs- port 44444"
date: 2012-01-24
forum: Security
---

### Post by Ms. Daisy on 2012-01-24
My ufw.log shows a huge amount of blocked activity to one particular IP.  I've tried to trace the IP but it times out.  I'm concerned after comparing my log to the basic security wiki (which I helped author, let's just ignore the irony of that for a minute, can we?)

What caught my interest is the volume of blocked requests (50ish in the last 2 days) and the ports used (44444).

```
 Jan 24 15:44:08 MsDaisy-Computer kernel: [ 1296.544822] [UFW BLOCK] IN= OUT=wlan0 SRC=my.IP.Add.XX DST=unknown.IP.Add LEN=60 TOS=0x00 PREC=0x00 TTL=1 ID=1088 PROTO=ICMP TYPE=8 CODE=0 ID=2913 SEQ=1   
  Jan 24 15:44:56 MsDaisy-Computer kernel: [ 1344.922839] [UFW BLOCK] IN= OUT=wlan0 SRC=my.IP.Add.XX DST=unknown.IP.Add LEN=60 TOS=0x00 PREC=0x00 TTL=1 ID=1089 PROTO=UDP SPT=47414 DPT=33434 LEN=40  
 Jan 24 15:45:21 MsDaisy-Computer kernel: [ 1369.553723] [UFW BLOCK] IN= OUT=wlan0 SRC=my.IP.Add.XX DST=unknown.IP.Add LEN=65535 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=59663 DPT=44444 LEN=65515  
 Jan 24 15:45:21 MsDaisy-Computer kernel: [ 1369.553844] [UFW BLOCK] IN= OUT=wlan0 SRC=my.IP.Add.XX DST=unknown.IP.Add LEN=65535 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=59663 DPT=44444 LEN=65515  
 Jan 24 15:45:21 MsDaisy-Computer kernel: [ 1369.553948] [UFW BLOCK] IN= OUT=wlan0 SRC=my.IP.Add.XX DST=unknown.IP.Add LEN=65535 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=59663 DPT=44444 LEN=65515  
 Jan 24 15:45:21 MsDaisy-Computer kernel: [ 1369.554050] [UFW BLOCK] IN= OUT=wlan0 SRC=my.IP.Add.XX DST=unknown.IP.Add LEN=65535 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=59663 DPT=44444 LEN=65515  
 Jan 24 15:45:21 MsDaisy-Computer kernel: [ 1369.554153] [UFW BLOCK] IN= OUT=wlan0 SRC=my.IP.Add.XX DST=unknown.IP.Add LEN=65535 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=59663 DPT=44444 LEN=65515  
 Jan 24 15:45:21 MsDaisy-Computer kernel: [ 1369.554256] [UFW BLOCK] IN= OUT=wlan0 SRC=my.IP.Add.XX DST=unknown.IP.Add LEN=65535 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=59663 DPT=44444 LEN=65515  
 Jan 24 15:45:21 MsDaisy-Computer kernel: [ 1369.554360] [UFW BLOCK] IN= OUT=wlan0 SRC=my.IP.Add.XX DST=unknown.IP.Add LEN=65535 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=59663 DPT=44444 LEN=65515  
 Jan 24 15:45:21 MsDaisy-Computer kernel: [ 1369.554464] [UFW BLOCK] IN= OUT=wlan0 SRC=my.IP.Add.XX DST=unknown.IP.Add LEN=65535 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=59663 DPT=44444 LEN=65515  
 Jan 24 15:45:21 MsDaisy-Computer kernel: [ 1369.554570] [UFW BLOCK] IN= OUT=wlan0 SRC=my.IP.Add.XX DST=unknown.IP.Add LEN=65535 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=59663 DPT=44444 LEN=65515  
 Jan 24 15:45:21 MsDaisy-Computer kernel: [ 1369.554731] [UFW BLOCK] IN= OUT=wlan0 SRC=my.IP.Add.XX DST=unknown.IP.Add LEN=65535 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=59663 DPT=44444 LEN=65515  
```Is it time to reinstall?

---

### Post by OpSecShellshock on 2012-01-24
Hmmm. Well I know that port in TCP is associated with a couple Windows trojans, but I haven't been able to find out much about it on the UDP side, unless it's something used by your router or ISP. Did you look up any information about the external IP address?

It's getting blocked, whatever it is, which of course vindicate's DT's firewall rule suggestions. 44444 is an unassigned port, so it could be anything. What's the external IP?

---

### Post by Ms. Daisy on 2012-01-24
The destination is 224.0.0.251. That's multicast, right? I'm afraid I don't really understand its use beyond that it sends a packet simultaneously to multiple locations.

I tried whois, but it doesn't return anything for that IP.  The only other thing I did with that IP was traceroute and tracepath, but both of those fail. The traceroute returns "operation not permitted" even with sudo.

I'm also interested to know why it's calling out.

---

### Post by Dangertux on 2012-01-24
Wee vindication ;-)

That is multicast traffic, as such traceroute will fail (it's a reserved IP). It's unlikely that it is malicious in nature. It is also not a distinct indicator that your system is compromised. 

Do you use cable Internet service?

---

### Post by Ms. Daisy on 2012-01-24
yup.
What can I read to understand this?

---

### Post by OpSecShellshock on 2012-01-24
That's definitely a multicast IP. I'm suspecting some kind of media playing application is involved, but not sure how to confirm that. Do you have any of those running?

---

### Post by Dangertux on 2012-01-24
It's trying to talk to your modem rather... It's trying to respond to what your modem is saying.

---

### Post by Ms. Daisy on 2012-01-24
> **OpSecShellshock said:**
> That's definitely a multicast IP. I'm suspecting some kind of media playing application is involved, but not sure how to confirm that. Do you have any of those running?
I do not have anything other than firefox, log file viewer, and ruby running. 

[QUOTE=Dangertux] It's trying to talk to your modem rather... It's trying to respond to what your modem is saying. 	[/QUOTE]
My modem... you mean my cable modem? Not the router?

---

### Post by Dangertux on 2012-01-24
Yep the modem. See multicast is used in this case to discover devices on the network that are "alive".  

So it will pass through the router (and likely be forwarded)

---

### Post by Ms. Daisy on 2012-01-24
It also used these ports: ```
SPT=33764 DPT=33434
SPT=52674 DPT=44444
SPT=60251 DPT=44444
SPT=5353 DPT=5353
```

OK. So the modem wants to know what devices are connected. It's checking  all the devices continuously throughout the day?  So this is something that takes up a lot  of log space but is otherwise innocuous?

---

### Post by OpSecShellshock on 2012-01-24
OK, now I'm confused. If this is an indication of response traffic being blocked, how is the incoming discovery request getting through in the first place? Also, from the look of the log events, the blocked traffic is going out over a high port, which in a lot of cases signifies that the request is originating from the local machine by some process that's running. That said, the whole zeroconf/multicast thing makes no sense to me no matter how much documentation I read.

---

### Post by Dangertux on 2012-01-24
Icmp and igmp multicast do not create stateful connections so thinking about it in those terms makes it more confusing

---

### Post by Ms. Daisy on 2012-01-24
[QUOTE=OpSecShellshock]That said, the whole zeroconf/multicast thing makes no sense to me no matter how much documentation I read. 	[/QUOTE]
Don't take this the wrong way, but that makes me SO happy to read! I'm confused, but that's not surprising. To see that much more experienced people are confused, well... it gives me hope :)

So is this something that I should allow in my ufw settings? Seems like I should allow my computer to talk to the modem.

---

### Post by Dangertux on 2012-01-24
It's not strictly necessary it's a biproduct of how cable modems work, and the traffic would be filtered by your modem anyway. Else someone in your neighborhood would be able to wiresharl everything you do ;-)

---

### Post by emiller12345 on 2012-01-25
everything that I've read about ports 11111 22222 33333 44444 and 55555 is that they are common trojan ports (easy to find). you may consider port scanning your own network to see if any device is on there that shouldn't be. Make a record of all MAC addresses and verify them with the labels that are actually on the outside of the products (if their listed). Also make sure that your router doesn't have a feature enabled like 'Multicast pass-through'.  That would probably let anyone on the net send you multicast packets.

---

### Post by Ms. Daisy on 2012-01-25
> **Dangertux said:**
> Icmp and igmp multicast do not create stateful connections so thinking about it in those terms makes it more confusing
I've been googling ICMP, IGMP, multicasting, zeroconf, and modems.  I'm guessing that the modem is sending ping-like packets to the network using ICMP (BTW my other computer shows the same ufw logs, so it was receiving the same messages). But I'm not really getting anything about modems.

Do you know of any links that would explain how modems use multicasting?


@ emiller12345- I checked, there are no extra devices on the network. I checked the router & it has no Multicast pass-through setting.

---

### Post by Dangertux on 2012-01-25
Somewhat technical but here you go

[http://www.cisco.com/en/US/technologies/tk648/tk828/technologies_case_study0900aecd802e2ce2.html](http://www.cisco.com/en/US/technologies/tk648/tk828/technologies_case_study0900aecd802e2ce2.html)

---

### Post by Ms. Daisy on 2012-01-25
@Dangertux- thanks for the link. I'll read that tonight.

> **OpSecShellshock said:**
> OK, now I'm confused. If this is an indication of response traffic being blocked, how is the incoming discovery request getting through in the first place? 
I suppose I'm beating a dead horse here, but I still don't understand this part either.  It would make more sense to me to see blocks both in- and out-bound.  I think this is a firewall question.

So the modem sent MsDaisy-computer a bunch of packets. They all came through the firewall.  MsDaisy-computer created response packets and tried to send them back to the modem, but the firewall blocked the responses. 

I'm using the firewall settings from this [thread]("http://ubuntuforums.org/showthread.php?t=1876124"). The settings are to deny all traffic except the specifically allowed traffic.  So are the multicast packets coming in to MsDaisy-computer through a port I allowed, but then MsDaisy-Computer is responding on a different port? AFAIK, multicasting uses ports 264, 639, & 5353.  Those are all blocked in & out. So how'd they get in?

BLARGH! I am in the land of confusion...

---

### Post by Ms. Daisy on 2012-01-25
> **Dangertux said:**
> Yep the modem. See multicast is used in this case to discover devices on the network that are "alive".  

So it will pass through the router (and likely be** forwarded**)

What do you mean by "forwarded?" Do you mean sent along? or port forwarded?

---

### Post by Dangertux on 2012-01-25
> **Ms. Daisy said:**
> What do you mean by "forwarded?" Do you mean sent along? or port forwarded?

This is where it can get confusing quickly, let's take a look at the logs step by step and see what's going on.

This will be even harder because you blocked the dst/src ip but I will do the best with what you have provided. I'm willing to bet they aren't ALL the 224.0.0.251 (which by the way is multicast DNS)

```

24 15:44:08 MsDaisy-Computer kernel: [ 1296.544822] [UFW BLOCK] IN= OUT=wlan0 SRC=my.IP.Add.XX DST=unknown.IP.Add LEN=60 TOS=0x00 PREC=0x00 TTL=1 ID=1088 PROTO=ICMP TYPE=8 CODE=0 ID=2913 SEQ=1   

```Important things to note about this block are.

- PROTO = ICMP (this is an ICMP echo request, noted by the TYPE = 8) it was blocked by your firewall (this is pretty standard). This request was PROBABLY from your router or modem, the failure of this request LIKELY spawned the spurious requests afterwards.

```

  Jan 24 15:44:56 MsDaisy-Computer kernel: [ 1344.922839] [UFW BLOCK] IN= OUT=wlan0 SRC=my.IP.Add.XX DST=unknown.IP.Add LEN=60 TOS=0x00 PREC=0x00 TTL=1 ID=1089 PROTO=UDP SPT=47414 DPT=33434 LEN=40  

```This is UDP, and isn't very specific, if it's going to mDNS, it's likely just a zeroconf query.

```

 Jan 24 15:45:21 MsDaisy-Computer kernel: [ 1369.553723] [UFW BLOCK] IN= OUT=wlan0 SRC=my.IP.Add.XX DST=unknown.IP.Add LEN=65535 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=59663 DPT=44444 LEN=65515  
 Jan 24 15:45:21 MsDaisy-Computer kernel: [ 1369.553844] [UFW BLOCK] IN= OUT=wlan0 SRC=my.IP.Add.XX DST=unknown.IP.Add LEN=65535 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=59663 DPT=44444 LEN=65515  
 Jan 24 15:45:21 MsDaisy-Computer kernel: [ 1369.553948] [UFW BLOCK] IN= OUT=wlan0 SRC=my.IP.Add.XX DST=unknown.IP.Add LEN=65535 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=59663 DPT=44444 LEN=65515  
 Jan 24 15:45:21 MsDaisy-Computer kernel: [ 1369.554050] [UFW BLOCK] IN= OUT=wlan0 SRC=my.IP.Add.XX DST=unknown.IP.Add LEN=65535 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=59663 DPT=44444 LEN=65515  
 Jan 24 15:45:21 MsDaisy-Computer kernel: [ 1369.554153] [UFW BLOCK] IN= OUT=wlan0 SRC=my.IP.Add.XX DST=unknown.IP.Add LEN=65535 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=59663 DPT=44444 LEN=65515  
 Jan 24 15:45:21 MsDaisy-Computer kernel: [ 1369.554256] [UFW BLOCK] IN= OUT=wlan0 SRC=my.IP.Add.XX DST=unknown.IP.Add LEN=65535 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=59663 DPT=44444 LEN=65515  
 Jan 24 15:45:21 MsDaisy-Computer kernel: [ 1369.554360] [UFW BLOCK] IN= OUT=wlan0 SRC=my.IP.Add.XX DST=unknown.IP.Add LEN=65535 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=59663 DPT=44444 LEN=65515  
 Jan 24 15:45:21 MsDaisy-Computer kernel: [ 1369.554464] [UFW BLOCK] IN= OUT=wlan0 SRC=my.IP.Add.XX DST=unknown.IP.Add LEN=65535 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=59663 DPT=44444 LEN=65515  
 Jan 24 15:45:21 MsDaisy-Computer kernel: [ 1369.554570] [UFW BLOCK] IN= OUT=wlan0 SRC=my.IP.Add.XX DST=unknown.IP.Add LEN=65535 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=59663 DPT=44444 LEN=65515  
 Jan 24 15:45:21 MsDaisy-Computer kernel: [ 1369.554731] [UFW BLOCK] IN= OUT=wlan0 SRC=my.IP.Add.XX DST=unknown.IP.Add LEN=65535 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=59663 DPT=44444 LEN=65515

```These give away their origin without me even knowing the full packet details. 

As far as forwarded, with broadcast/multicast traffic it's not so much a forwarding thing as a passing through thing.

My guess here is these are either responses to or replies to an mDNS membership request. If you'd like to verify it, I went ahead and did a quick capture on a packet that I believe to have a similar purpose. There is a screen shot from wireshark below for your comparison, to queue the responses necessary I simple restarted the avahi-daemon service

```

sudo service avahi-daemon restart

```You should get a sequence of about 14 packets (similar to what you are seeing here) verify that your firewall logs are indicating the same, and that the packet contents is  similar to what will be posted. 

In any case this really is nothing to worry about. BTW UDP is stateless, so speaking in terms of creating a connection (is rather arbitrary in this case).

Hope this helps.

Note : the destination and source port change can be considered rather trivial in this case due to the nature of mdns multipathing and the layout of a network vastly changing the creating of membership requests. That being said, compare the packet contents, to make sure it is in fact what we are observing.

---

### Post by Ms. Daisy on 2012-01-26
Thank you, Dangertux.  You went way above & beyond helping me to understand (just like you do for nearly every thread in which you post).

---

