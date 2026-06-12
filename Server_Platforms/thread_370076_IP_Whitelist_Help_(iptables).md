---
title: "IP Whitelist Help (iptables)"
date: 2007-02-25
forum: Server Platforms
---

### Post by Chaos5lw on 2007-02-25
Hi, now I've got my server up and running with SVN and Trac and got the password system up and running, it's all but ready to be put on the net, however there is one last thing I have to setup, which is the firewall.

The Task
This server is going to be used for a small development team and ideally it is my plan to set it up with an IP Whitelist table so that only the devs can actually make a successful connection to it and as far as anyone else is concerned it doesn't exist.

I plan to do this by using iptables to filter the IPs, and then use the port forwarding on router to control which ports can be accessed from the outside world, for example, I won't be allowing port 10000 outside of my network because thats used for webmin.

I will be using webmin to configure iptables but I have a question about how to go about actually setting up the whitelist. I was thinking of setting the IPs i want to allow (both internal and external) first for all ports (since my router takes care of controlling port access) and then setting up a block for all IPs on all ports.

I am wondering how that would work with regards to which rule iptables would obey, would it obey the block rule, or the allow rule?

I was also wondering (since I'm not at home at the minute), can you setup iptables for all IPs on a subnet, and also, is there an easy way to block all IPs in one rule?

Thanks,
Jamie.

---

### Post by thenebcouk on 2007-02-26
I'd suggest really learning iptables from a view of understanding the commands, I don't use webmin but if this function ability is mirrored then I'd use it.

iptables works with a very strict stack method, your whitelist rules will need to be before anything blocking traffic.
For example if I wish to rate limit my ssh port, my whitelisted machines will need to come before the rate limiting.

The best way around this so that you can easily modify rules is to use a multiple set of jumps.

I.e all your INPUT traffic comes in on the INPUT chain, I personally jump this into two separate tables tcpIN & udpIN. Next I jump each table to a further whitelist table of which are my rules that need to be read before my rate limiting. Then all other traffic goes to a last table which handles rate limiting.

So hence I have for a typical tcpIN packet:
INPUT -> tcpIN -> tcpInWhite -> tcpInOther

So, just follow that plan with webmin.

---

