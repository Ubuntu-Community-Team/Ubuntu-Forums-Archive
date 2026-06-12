---
title: "Any TinyDNS experts in da house?"
date: 2005-08-25
forum: Server Platforms
---

### Post by kevinfreitas on 2005-08-25
Just had a server crash and it took all my config files with it. I'm trying to setup TinyDNS so my server can act as a name server and host for multiple websites and domains. I've had this running and my domain registrar's are all pointed to ns.example.net but I'm not having any luck. Can someone have a look at my TinyDNS data file to tell me if I'm doing things correctly?

```

# the nameserver is running on the same machine as the web server
.example.net:1.2.3.4:ns.example.net:86400

# example.net with a couple of sub-domains
=example.net:1.2.3.4:86400
+www.example.net:1.2.3.4:86400
+some.example.net:1.2.3.4:86400
+another.example.net:1.2.3.4:86400

# example2.org and multiple other domain names
=example2.org:1.2.3.4:86400
+www.example2.org:1.2.3.4:86400

```

I'm pretty sure my apache config is working since I altered my PCs local "hosts" file to bypass DNS goodness. I really appreciate any help. Cheers!   ~ Kevin

---

### Post by my3ke on 2005-08-25
I can't help you with the configuration problem (sorry).  What I was wondering is where did you find tinydns?  I'm currently trying to set up a list server and was thinking that tinydns would be better for this type of task than Bind.  How has it worked out for you?

Thanks for your time,
my3ke

---

### Post by kevinfreitas on 2005-08-25
It's a part of the djbdns package that can be found at [http://cr.yp.to/djbdns.html](http://cr.yp.to/djbdns.html) 

On the server that died it was running great and it was really easy to add new domains. Only bummer is I didn't set that server up so don't quite know where to start.

There's a seeminly good tutorial for setting up djbdns and its components at [http://www.djbdnsrocks.org/](http://www.djbdnsrocks.org/)    That site has a package of tools that also comes with a snazzy web front end for TinyDNS. Still doesn't explain everything in enough detail for me to feel comfortable with my multiple domain configuration.

Enjoy!

---

### Post by nocturn on 2005-08-26
You should substitute 1.2.3.4 with the IP addresses of your hosts.  

I used TinyDNS in the past and it is the best DNS server I have ever seen, I dumped it in favour of MaraDNS however because TinyDNS is not Free Software.

---

### Post by kevinfreitas on 2005-08-26
1.2.3.4 represents the IP address of the server I'll be using to run everything. It's a single server acting as a name server with multiple domains.

---

