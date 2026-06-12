---
title: "Ip tables help"
date: 2013-11-03
forum: Security
---

### Post by chaos_efphect on 2013-11-03
So I hope this would be the appropriate section if not would a MOD please move and accept my apologizes.

I have been fiddling around with a new ubuntu/debian dhcp server and internet gateway and had a few questions about Ip tables i seek help with. I was following the following [tutorial]("http://qcktech.blogspot.com/2012_08_01_archive.html") with a great deal of success. Now there is a few rules that was suggested to add to ip tables that i was not totally sure about but claim to help secure the box. Could someone with more skill or knowledge please explain a little more about the reason behind it? I have attempted to research on my own with little success.

[PHP]sudo iptables -A INPUT -s 192.168.0.0/24 -i eth0 -j DROP
sudo iptables -A INPUT -s 10.0.0.0/8 -i eth0 -j DROP
sudo iptables -A INPUT -s 172.16.0.0/12 -i eth0 -j DROP
sudo iptables -A INPUT -s 224.0.0.0/4 -i eth0 -j DROP
sudo iptables -A INPUT -s 240.0.0.0/5 -i eth0 -j DROP
sudo iptables -A INPUT -s 127.0.0.0/8 -i eth0 -j DROP[/PHP]

I understand the 127.0.0.0 would be a loop back address but what benefit would i have to block it? what benefit do I have blocking the other ip ranges? I also have a copy of the ip table used in my dd wrt router and attempted a stare and compare but was only left with more questions. any help is greatly appreciated.

---

### Post by Doug S on 2013-11-03
Assuming eth0 is your external interface, then those are non-routable addresses under RFC1918 (addresses reserved for private networks) and a few others. They should be DROPPED because it should not be possible for such packets to arrive at your public IP address. Also, it wouldn't be possible for you to reply to them anyhow as the return path can not possibly be known. You should have something similar on your outgoing and forward chains to prevent sending out packets from addresses reserved for private networks. Most ISPs will just drop such packets upstream, but Verizon will actually suspend your service for sending out packets with a reserved source address (or so I have heard from a couple of sources).
By the way, I have those exact same rules, but with logging added, in my iptables rule set.

Edit: I do not have this line anywhere: [COLOR=#000000][COLOR=#0000BB]sudo iptables [/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]A INPUT [/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]s 127.0.0.0[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]8 [/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]i eth0 [/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]j DROP[/COLOR][/COLOR] and I do not recall ever seeing such an incoming packet. Curious if I should add such a check. I forgot to mention that my DSL modem spews 10.X.X.X packets and my ISP does also. I DROP them.

---

### Post by chaos_efphect on 2013-11-03
Thank you for the fast response Doug s.

That is kind of what i figured since they all where various private ips but would it really be needed to have a rule block them both on eth0(wan connection) and on eth1(lan connection)? since they are private ips i did not think they would even be routed to eth0 to begin with? Does anyone have any suggestions for a good list of Iptable rules to use on a dhcp server that connects directly to the internet?

---

### Post by Doug S on 2013-11-03
> **chaos_efphect said:**
> ... since they are private ips i did not think they would even be routed to eth0 to begin with? Does anyone have any suggestions for a good list of Iptable rules to use on a dhcp server that connects directly to the internet?Yes, but the return address can be forged. For Iptables [this]("http://bodhizazen.net/Tutorials/iptables/") is referred to often, and I like it. I'll PM you in a moment with a link to my iptables, as a text file (I have posted the link in these forums a few times, but I'll do it via PM this time).

---

