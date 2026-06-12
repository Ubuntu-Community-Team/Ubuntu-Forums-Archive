---
title: "Cannot make external connections"
date: 2009-05-06
forum: Server Platforms
---

### Post by MaximumFish on 2009-05-06
Hi all,

I've been running a few servers from Ubuntu Server Edition for about a year now, and while it's all been quite a pleasant experience so far I now seem to have run into a problem.

Basically I have one server that can't make any external connections. I noticed it when trying to do an 'apt-get update', when every connection attempt would timeout. Assuming it was a server issue, I tried changing to a different mirror in sources.list. Same thing. A reboot didn't fix it either.

I then tried doing the same on the other Ubuntu servers (set up to use the same mirrors) and they all worked just fine. I then tried a 'wget [www.google.com/index.html](www.google.com/index.html)', which also timed out. I tried the same for my own website and again it timed out. Finally, doing the same for an internal site hosted on one of the other Ubuntu servers returned the file without issue.

DNS lookups are working properly, all firewall settings are as they were when the system was first installed, and as far as I can tell, all network settings are accurate.

I'm at a real loss as to what's going on and I've run out of things to check. Any help would be very much appreciated!

Thanks in advance,

Max

---

### Post by brendan.lefoll on 2009-05-06
> **MaximumFish said:**
> Hi all,

I've been running a few servers from Ubuntu Server Edition for about a year now, and while it's all been quite a pleasant experience so far I now seem to have run into a problem.

Basically I have one server that can't make any external connections. I noticed it when trying to do an 'apt-get update', when every connection attempt would timeout. Assuming it was a server issue, I tried changing to a different mirror in sources.list. Same thing. A reboot didn't fix it either.

I then tried doing the same on the other Ubuntu servers (set up to use the same mirrors) and they all worked just fine. I then tried a 'wget [www.google.com/index.html](www.google.com/index.html)', which also timed out. I tried the same for my own website and again it timed out. Finally, doing the same for an internal site hosted on one of the other Ubuntu servers returned the file without issue.

DNS lookups are working properly, all firewall settings are as they were when the system was first installed, and as far as I can tell, all network settings are accurate.

I'm at a real loss as to what's going on and I've run out of things to check. Any help would be very much appreciated!

Thanks in advance,

Max


have you checked /etc/resolv.conf?

Can you get to a site that you havent been to before lets say try and ping fridu.org
if you cant, but can for example get to google.com its probably that.

---

### Post by windependence on 2009-05-07
Do you have your gateway correctly set? Try doing a traceroute on an outside site like Google and see where it stops. That's where your problem is.

-Tim

---

### Post by MaximumFish on 2009-05-07
Thanks for the responses but they're both things I've checked. This server is just console based so I'd never been to so much as Google with it, so I know DNS lookups are working. Of course the DNS server is hosted within our network.

The gateway is also set up exactly like the other Ubuntu systems that don't have a problem getting out.

I'm starting to think our Cisco firewall is blocking it for reason, but I really don't know why.

:(

---

### Post by wineman on 2009-05-07
sup dude :guitar:

dude check your firewall on your pc, i doubt your cisco router would give you issues. if you're using IPTables, the command is
```
$ iptalbes -L OUTPUT
$ iptables -L POSTROUTING
```
and check ports 53 and 80 for any DENY or REJECT or DROP commands.

also, try pinging a remote server like google, and see if there is connectivity through ICMP (port 0 + 7), and if they are allowed, then you've got a minor firewall script issue. If they are dropped, well then you might need to reboot your cisco router.

I agree with brendan.lefoll on the */etc/resolv.conf*, also check that, and check that you don't have a non-existant on incorrect gateyway setup in you */etc/network/interfaces* config file.

Good luck, i hope this helps

---

### Post by MaximumFish on 2009-05-07
OK, well we tracked it down to the Cisco firewall after all. We had a couple of NAT rules to give the box an external IP so our satellite offices could connect. When we removed that rule everything worked and I was able to install the packages I wanted, then when we recreated the rule it broke again.

Very, very strange. But at least I've got what I wanted installed.

---

### Post by windependence on 2009-05-07
Yeah, I was thinking they may have had port security on or they had your switch port on a different VLAN or something. Glad you figured that out.

-Tim

---

