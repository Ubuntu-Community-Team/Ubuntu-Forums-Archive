---
title: "can't access webpages"
date: 2007-06-22
forum: Server Platforms
---

### Post by mattskent on 2007-06-22
I'm having trouble accessing web pages hosted on my server from off of my home network. I used the Dapper Server CD to set up a basic LAMP server, and I am able to access the pages while on my network. I'm running the server through a router, and have port forwarding set up correctly so that HTTP traffic gets forwarded to the server, so while on the network, I can access the web pages with the internal IP address for the machine or my external IP address. When I'm on a different network though, I get a page cannot be displayed error when using the external IP address. I'm not sure where to look for help for this issue...can you guys help me or give me ideas where to look? Thanks.

---

### Post by tux821 on 2007-06-22
Can it be that your router also has a firewall ?

I remember a modem/router where I had to setup the port forwarding and also had to open up the http/80 port of the firewall.

Another way to check if your http port / 80 is open is with an external firewall scan service, for example with:
[http://www.derkeiler.com/Service/PortScan/](http://www.derkeiler.com/Service/PortScan/)

If your router settings are correct your http/80 port should be shown as 'open'.

---

### Post by mattskent on 2007-06-23
Hmm...running the port scan shows only one open port, and it's not port 80. I looked around through the security settings on the router, and did manage to find a rather basic firewall. I unchecked the box next to "Block Anonymous Internet Requests," which I thought would be the problem, but I still can't access the web pages from off the network. Any other ideas?

---

### Post by tux821 on 2007-06-24
So there is no open port 80.

This means the problem is on the path between the outside of your router to your web server..
(I assume your provider is not blocking incoming port 80..)

Check your router forward settings again.
- is there no firewall blocking ?
- is the port forward correct (to the correct IP of your web server) ?

What router are you using (the exact type indication) ?

---

### Post by mattskent on 2007-06-24
Actually, now that I think about it, I'm not sure if it's safe to assume my provider isn't blocking incoming port 80. By being able to use my external IP, doesn't that mean that traffic can potentially get through on that port and the problem lies somewhere between my router and server?

The router is a Linksys WRT54G. I attached a few screenshots of what should be the relevant config pages. I have a static IP set up on my server, so that IP should be correct.

---

### Post by tux821 on 2007-06-24
Your firewall and port forwarding looks ok.
The  "Block Anonymous Internet Requests" is only to drop ping requests so it should not be a problem.

As you also said .. I now also think you should check if your provider blocks the incoming port 80/http 
You can try an Apache configuration and port forward using a higher port number like 8000

---

### Post by mattskent on 2007-06-24
Ok, I did a little bit of research, and I'm pretty sure my provider blocks port 80 (and a whole bunch of other ports...), so I set up Apache to listen on port 8000 by editing the ports.conf file, and I was able to access it from off the network using [http://externalip:8000/](http://externalip:8000/)
How can I configure it to work without specifying a port in the address?

---

### Post by Wardazo on 2007-06-24
I don't think you can. 

Without the :8000 suffix the browser will default to port 80, but for both these reasons:

1. your isp blocks such traffic to port 80, and 

2. Apache is listening on port 8000

...  it wont work without the :8000

But if someone does come up with a solution please post back saying it works - I'd be fascinated to see what it is.;)

---

### Post by tux821 on 2007-06-24
Check out this page:

[http://www.dtdns.com/index.cfm?fuseaction=info.faq](http://www.dtdns.com/index.cfm?fuseaction=info.faq)

look for 'My port 80 is blocked'

Personally I would go for another provider, what provider do you have btw ?

---

### Post by mattskent on 2007-06-24
We have Charter...I'm living with my parents right now while I'm home from college for the summer, so since they're paying the bills, I can't really complain...

The FAQ page you linked to seems to be specific to that particular service, but it gave me the idea to look into some other stuff, and I ended up using a free DNS service called DynDNS since it was supported natively by my router. That let me set up what basically amounts to a forwarding address. The free service has some limitations, but it works for what I need it to right now.

Thanks for all your help!

---

### Post by tux821 on 2007-06-25
np, great you made it work!

---

