---
title: "Transparent Proxy without NAT"
date: 2007-03-03
forum: Server Platforms
---

### Post by nabberuk on 2007-03-03
I've read various guides on the net on how to set up a transparent proxy with squid ect. But these require the box i set it up on to have an ip address. I'm trying to create a box so you just plug it in between the router and server of an existing network and it will just work.

I'm guessing that i wont need NAT, does anyone have any advice that could put me on target in setting this up.


Many thanks!

---

### Post by jonathan.lees on 2007-03-03
Every device on a network needs an IP address, I guess you mean that the box with Squid needs a public IP address?

---

### Post by gaten on 2007-03-03
I know this is possible in BSD. See here: [http://ezine.daemonnews.org/200207/transpfobsd.html](http://ezine.daemonnews.org/200207/transpfobsd.html)

So this IS possible. However, I have no idea how to accomplish this with Ubuntu, I'm sorry. For me, I'm going to use BSD as my firewall/proxy, but I know that doesn't answer your question. But there IS hope :P

---

### Post by nabberuk on 2007-03-04
I was reading about a vmware option, it's called bulletproof glass which ia based on centos. This is where i got the idea from. [http://www.vmware.com/vmtn/appliances/directory/710](http://www.vmware.com/vmtn/appliances/directory/710)

I'm not that good with linux to be able to investigate and put my findings into action on a debian based distro. But i'm working on it.

Anyone else have any advice?

thanks!

---

### Post by nabberuk on 2007-03-20
Well i've created a simple bridge between the 2 nics, simple gave them an ip of 0.0.0.0 and now i can get the internet through them.

Just need to look into how to get squid to listen on a nic and not an ip.

---

### Post by nabberuk on 2007-03-20
I'll explain a little more, this is how it will work;

eth0 (internal lan, port 80)  --> iptables (from port 80, to port 3128)  --> Squid (from 3128, eth1) --> router 

 now squid is set up to be transparent so i do not have to enter an ip in the browser proxy settings. Not that i could as the proxy server doesnt have an ip. I have the following rule set up in iptables 

iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 3128

This should accept all incoming packets on port 80 and redirect them to squid on port 3128.

If i do iptables -L -v the packet numbers go up showing the the rule is bein met.

I should note that i can get onto the internet with the pc's that are behind the proxy server.

Please help me.........ta!

---

