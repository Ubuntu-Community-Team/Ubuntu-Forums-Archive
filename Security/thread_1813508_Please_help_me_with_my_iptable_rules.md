---
title: "Please help me with my iptable rules"
date: 2011-07-27
forum: Security
---

### Post by Mouse750 on 2011-07-27
I have Linux (Openwrt) running on my router with iptables and openvpn installed.

I connect to a vpn provider to help protect me and my family's privacy from evildoers.

All of the vpn servers I connect to are on port 443.

I'm trying to come up with a rule where "If" my vpn connection disconnects... I want to block myself from accidentally accessing the Internet. 

Please look at my following rule.

[[img]http://img52.imageshack.us/img52/375/screenshotzf.th.gif[/img]](http://img641.imageshack.us/img641/786/screenshotq.gif)

Rule 3 says accept wan connections to and from port 443.
Rule 4 is my "catch all" that says to drop everything else.

The problem is my rules seem ignored. As a test, I turned off the vpn and I can still access the Internet.

I don't think my rules are correct at all, in fact I'm probably way off.

I really need to get this working. Please help.

I'm trying to work with the built in gui to add, edit, and remove iptable rules however I can use regular iptable commands if need be.

Since all the vpn servers I use, connect using port 443, I was thinking that would be a good way to filter however it doesn't have to be done that way. It could done anyway you can think of.

I just want it so that if I get disconcerted from the server (which seems to happen about once a day or so), The Internet stops working, then when I notice the Internet is not working and I would just re-start the vpn service and the Internet would work again.

I know this isn't ubuntu but it is linux. I listed this thread as other os. I've tried posting over at Openwrt forums however that site doesn't have enough traffic to get replies.

Please help me?



--

---

### Post by judderwocky on 2011-07-28
> **Mouse750 said:**
> I have Linux (Openwrt) running on my router with iptables and openvpn installed.

I connect to a vpn provider to help protect me and my family's privacy from evildoers.

All of the vpn servers I connect to are on port 443.

I'm trying to come up with a rule where "If" my vpn connection disconnects... I want to block myself from accidentally accessing the Internet. 

Please look at my following rule.

[[IMG]http://img52.imageshack.us/img52/375/screenshotzf.th.gif[/IMG]]("http://img641.imageshack.us/img641/786/screenshotq.gif")

Rule 3 says accept wan connections to and from port 443.
Rule 4 is my "catch all" that says to drop everything else.

The problem is my rules seem ignored. As a test, I turned off the vpn and I can still access the Internet.

I don't think my rules are correct at all, in fact I'm probably way off.

I really need to get this working. Please help.

I'm trying to work with the built in gui to add, edit, and remove iptable rules however I can use regular iptable commands if need be.

Since all the vpn servers I use, connect using port 443, I was thinking that would be a good way to filter however it doesn't have to be done that way. It could done anyway you can think of.

I just want it so that if I get disconcerted from the server (which seems to happen about once a day or so), The Internet stops working, then I would just re-start the vpn and the Internet would work again.

I know this isn't ubuntu but it is linux. I listed this thread as other os. I've tried posting over at Openwrt forums however that site doesn't have enough traffic to get replies.

Please help me?



--


... This might be the blind leading the blind here... but doesn't the 0.0.0.0/0:* mean that it would be blocking packets targeted to your loop back ports? 

it seems like you would want to block incoming packets from the outside network which would be something like *.*.*.* 

maybe?

dunno , just a guess... 0.0.0.0 I think is basically the same as loop back, so im guessing you just need to move that asterisk around so that you are blocking all ip addresses from the local and external network...

---

### Post by Mouse750 on 2011-07-28
That is just the way it is showcased. for example 0.0.0.0/0:* just means any ip and any port. I have no control over that cosmetic aspect.

However, Here are the things I can control via the gui,

[[IMG]http://img818.imageshack.us/img818/2038/optionsf.th.gif[/IMG]](http://img818.imageshack.us/img818/2038/optionsf.gif)

If need be, can aslo ssh and add manual commands such as

iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

Any help is very appreciated.

if it helps any, here are my current (default) rules:

---

