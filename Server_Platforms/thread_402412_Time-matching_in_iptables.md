---
title: "Time-matching in iptables"
date: 2007-04-05
forum: Server Platforms
---

### Post by jaheds on 2007-04-05
Hello.

I have an Ubuntu server (running Dapper) which does NAT for my home network.  I've been trying to setup a rule that would reject packets from certain computers on my network within a certain time range.

After reading the man pages ("man iptables"), I can use the time extension ("iptables -m time --help"), but the corresponding libipt_time.so library isn't installed on my system.  I've also looked through the Ubuntu synaptic packages only to find that "libipt_time.so" was included in Warty and Hoary, but not in later releases.  I'd have to patch and recompile the kernel according to netfilter.org;  something I'd rather not do

Is there any other way to achieve this?

One way I thought of was to use crontab to update the iptables rules whenever a certain time period edge is passed.  This seems a bit unclean.

Thank you in advance :)

---

### Post by kidders on 2007-04-07
Hi there,

> **jaheds said:**
> One way I thought of was to use crontab to update the iptables rules whenever a certain time period edge is passed.That's what I would do, personally.

What is the purpose of the time limitations? Essentially, I'm interested in what type of network access you're chiefly interested in preventing. (Perhaps there is another option for you to consider.)

---

### Post by jaheds on 2007-04-07
The time limitations are for my younger sister

I want to block any TCP/UDP traffic from her PC;  and I identify her PC using her MAC address.  I don't think she knows she can change her mac address yet :) she'll eventually find out

I did consider using a transparent Squid proxy, if that's what you were thinking, to block her HTTP traffic after midnight; but I think she spends her time mostly on instant messengers like MSN and so on, and I want to leave the internet completely open for her until mid-night.

---

### Post by kidders on 2007-04-07
Yeah, proxying (although not necessarily transparent) was what I was thinking about. Hehe.

To be honest, I wouldn't bother with libipt_time ... a quick bash script add/remove an iptables rule would instantly give you the result you want, and would have the advantage of being far more easily portable between machines.

Other suggestions:
[LIST]
[*]If you wanted to be a little paranoid (and assuming your network uses DHCP with dynamic DNS updating), you could make the cron task an hourly one, blocking some/all traffic originating from unrecognised MAC addresses. For example, any computer that didn't have a corresponding "fixed-address" declaration in your DHCP config could be denied the use of IM protocols after midnight.
[*]If your sister is a Windoze user, sending a warning message (LinPopup?) a few minutes before dropping all IM packets might be a nice touch.[/LIST]I'm very sympathetic to the idea that younger family members often need to be policed a little. The last thing you need, I suppose, is to have finding ways to circumvent your efforts turn into some sort of game ... so whatever you choose to do needs to cover all the bases!

---

