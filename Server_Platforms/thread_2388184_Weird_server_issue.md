---
title: "Weird server issue"
date: 2018-03-29
forum: Server Platforms
---

### Post by jtaylorinvestments on 2018-03-29
Hello everyone

New to the forums and Ubuntu in general. I am a big networking guy (Cisco, Juniper, HP, etc) and am still stumped.

My business internet was cut off (got mixed up with my residential bill and forgot to pay it, whoops). Paid up a few hours after it was cut off and everything seemed fine BUT my server no longer works... http, https, FTP, SSH and mail were all working before, none working now.

The server gets the requests and responds... then retransmits and retransmits and eventually stops. I opened iptables all the way up and disabled ufw for troubleshooting sake and nothing... apache2 logs do not have anything special I don't think. DNS is good all around (web or ssh to the IP doesn't help) forward, reverse and MX.

I would rather not post my site or IP since I just told everyone it is wide open... anyone have any things I can check next? Is this an ISP issue? They claim everything is good on their end but it seems pretty coincidental that my site has been fine for months and now toast.

I appreciate any help fellas.

---

### Post by jtaylorinvestments on 2018-03-29
Also, the server on its own can get to the internet just fine. It is just responding to requests that seems to be the issue.

Also, all of the services are available to my LAN. Just external is an issue. The only thing between the server and the ISP is my wireless router which is wide open now too (and port forwarding to the server obviously).

---

### Post by wildmanne39 on 2018-03-29
*Thread moved to **Server Platforms, a more appropriate forum**.*

---

### Post by volkswagner on 2018-03-30
Do you have other computers on the LAN with your server?
Are you getting the expected public ip when you go to http:\\canyouseeme.org and are ports open according to canyouseeme?

If you don't have other machines on your business LAN you can check your external ip:
```
wget http://ipinfo.io/ip -qO -
```

Perhaps your ISP has you double NATed? Check your route to 8.8.8.8. Does it go
through private ip space, or second ip before your public ip?

---

### Post by jtaylorinvestments on 2018-04-02
I pay for the static IP and it is good to go. It is publicly routable.

My DNS records are all good too I believe. DNS resolves to the correct IP and I have my reverse DNS set up through my provider (Spectrum) and both resolve as they should. My ports are open on the Ubuntu server. In fact, the server works just fine for anyone within the LAN. My email and web work flawlessly from a local machine, just not from the internet.

I can see the traffic come in using tcpdump on the interface. I see the http request and a reply then a retransmission of the failed reply then another. I wonder if my router is jacked up or something. But the ISP cutting my service then turning it back on a few hours later coincides with my services going down.... just seems too coincidental.

---

### Post by volkswagner on 2018-04-03
You can see traffic come in on which interface (server public, server private, router WAN)?

What are results from canyouseeme port 80, 443, 25, etc?

From outside your LAN what does traceroute look like to your domain?

You can eliminate DNS as an issue by using ip address.
From inside your lan use private ip of server, if web page is
displayed, you should get the same from outside your lan
using public ip.

Are you trying your public ip from inside your lan?
Have you tried from outside your lan (use cellular), perhaps it's NAT redirection/loopback issue.

Trying another router is easy enough, no?

Do you have anything like fail2ban running?

Can you telnet in to port 80, 22, etc from outside your LAN?

---

