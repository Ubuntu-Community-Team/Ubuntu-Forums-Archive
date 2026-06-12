---
title: "Apache Port issue"
date: 2008-09-04
forum: Server Platforms
---

### Post by inadaze on 2008-09-04
Hello,
Unfortunately, my ISP blocks port 80.  I have a Hardy Server connected to a router and I CAN access my Website by typing the ipAddress and another Port number.

xxx.xxx.xxx.xxx:81  

I opened port 81 on my router.
I was wondering if there was a way to specify to Apache not to use port 80 as defaut, use port 81.  i would like my website to be accessed without adding a port number.  So, is there a way that I could configure apache so that all I would have to do is type

xxx.xxx.xxx.xxx

in the address bar?
I tried modifying the port.conf so that "Listen 80" is "Listen 81" but that doesn't change anything.

thanks
Jay

---

### Post by HermanAB on 2008-09-04
Sounds like you already have Apache running on port 81.  Your problem is your browser that assumes port 80 - make a bookmark to the web site.

---

### Post by lazyart on 2008-09-04
If your ISP blocks port 80, you have no choice but to add the port number to the address.  Leave apache's ports alone, and have your router forward incoming traffic on port 81 to your apache server *on port 80.*

---

### Post by inadaze on 2008-09-04
ok - that makes sense.  But how do I Port forward?

I have a Belkin wireless router.  I already created "virtual servers" :

apache1....inboundPort 81....tcp...my.IP.Adress....outboundPort 81
apache1....inboundPort 443....tcp...my.IP.Adress....outboundPort 443

cheers,
Jay

---

### Post by inadaze on 2008-09-04
Never mind.  I suppose the question really is: 

Can I access my server with a domain name without entering the port number?  I would like to send people to [www.mySite.com](www.mySite.com) rather than [www.mySite.com:81](www.mySite.com:81)

AND

This is a stupid question but here goes:
Does my server have a domain name that can be accessed by the outside, or do I need to buy one?  I assume that I need to buy one, but I am a bit confused as to what the hostname of the server is for...

---

### Post by HermanAB on 2008-09-04
If you want to run a real server, then you need to pay your ISP the $10 or so per month extra for a real server account.

---

### Post by az on 2008-09-04
> **inadaze said:**
> Never mind.  I suppose the question really is: 

Can I access my server with a domain name without entering the port number?  I would like to send people to [www.mySite.com](www.mySite.com) rather than [www.mySite.com:81](www.mySite.com:81)

No.  Not with the kind of account you have with your ISP.  If you get an account that allows outgoing traffic on port 80, then you won't have than problem.

> **inadaze said:**
> 

This is a stupid question but here goes:
Does my server have a domain name that can be accessed by the outside, or do I need to buy one?  I assume that I need to buy one, but I am a bit confused as to what the hostname of the server is for...

The hostname is the name the web server thinks it is.  The domain name is the name that a DNS server will associate with your IP address.  Your IP address probably changes every few hours because you are not paying your ISP for a static IP address.

You can use dynamic DNS:

[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

A VitrualHost is a host served by the Apache webserver.  You can server many VirtualHosts from one single machine.  So, you can have many domain names' pages being served by the same machine at the same time.

Does this make things clearer or more confusing?

---

### Post by windependence on 2008-09-05
If he uses no-ip.com, there is an option to redirect to a specific port and mask the domain so that it looks like a regular URL. He just needs to point his domain at the no-ip domain (masked) and viola! he can serve on a different port. As I have said many times though and hermannn has stated, getting a static IP is best because some places block dynamic IP blocks. There will be people who can't access your site that way.

-Tim

---

### Post by az on 2008-09-05
> **windependence said:**
> If he uses no-ip.com, there is an option to redirect to a specific port and mask the domain so that it looks like a regular URL. He just needs to point his domain at the no-ip domain (masked) and viola! 

Yes, all dynamic DNS providers provide that.

But the URL will simply get rewritten to the final dynamic DNS domain with the port appended at the end.  So you still have to serve the actual page from a different port.  As you mentioned, many corporate/government/school firewalls do not permit fetching web pages on anything but port 80.

---

### Post by inadaze on 2008-09-08
Thank you all for your help!

---

