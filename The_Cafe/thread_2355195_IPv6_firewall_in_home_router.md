---
title: "IPv6 firewall in home router?"
date: 2017-03-10
forum: The Cafe
---

### Post by The Cog on 2017-03-10
I keep reading comments from people saying that they don't want IPv6, and that IPv4 is better because they are protected from the internet by NAT. In my opinion, they should all have a stateful firewall, and block incoming connections by default.

So I was wondering - do home routers with IPv6 support provided by ISPs have any firewalling enabled by default? For those people whose ISPs are not stuck in the stone age (I'm with Virgin Media), do the routers they provide have firewalls with IPv6 incoming blocked by default?

---

### Post by ajgreeny on 2017-03-10
My router shows me this which I assume means it is disabled
> IPv6 Address 	N/A
IPv6 Prefix 	::/0

---

### Post by The Cog on 2017-03-12
Bump. 
Nobody here gets IPv6 from their ISP? BT Infinity frinstance?

---

### Post by kevdog on 2017-03-12
How would you check -- I have a Comcast modem which was put in bridge mode.  I believe all traffic is passed to by router behind the modem.  I believe I'm assigned an IPv4 address but what would be best way to check?

---

### Post by The Cog on 2017-03-13
Hi Kevdog,

If the modem is in bridge mode, then all the IP processing will be being done by the router behind it. It is there that I would expect to find IPv4 NAT being done, or IPv6 firewalling. The router should be manageable (usually by a web browser). I am interested in whether the default config of such routers provided by ISPs has IPv6 firewalling enabled. I guess the only way to find out is to log onto the router and look at its IPv6 configuration settings, the same as you would if you wanted to configure IPv4 forwarding. If your output from **ifconfig** or **ip a**  only has link scope IP addresses, or your router has no IPv6 configuration settings then I guess your ISP doesn't provide IPv6 internet access. From the lack of responses in this thread so far, I guess IPv6 support is less common than I thought. I read that BT claim 100% IPv6 avasilability now: [http://www.ispreview.co.uk/index.php/2016/11/bt-broadband-lines-now-support-ipv6-internet-addresses.html](http://www.ispreview.co.uk/index.php/2016/11/bt-broadband-lines-now-support-ipv6-internet-addresses.html) so I had expected to hear from some BT users at least.

---

### Post by The Cog on 2017-09-10
I have an answer. My mother just upgraded to BT Infinity, and the new home hub provides both IPv4 and IPv6. In the home-hub setup there is the usual IPv4 port forwarding configuration, and for IPv6 there is a similar setup page for creating "pinholes" which they say is the equivalent of port forwarding for IPv4. So by default, incoming IPv6 connections are not allowed - the router implements a stateful IPv6 firewall. Excellent, this is as it should be.

---

