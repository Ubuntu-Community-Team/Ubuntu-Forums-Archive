---
title: "Web Server Confusion"
date: 2009-01-20
forum: Server Platforms
---

### Post by Hibby on 2009-01-20
I'm having a couple of problems setting up my server.
It currently works perfectly well as a samba server and intranet for my network, but being me I got bored etc and now I want more.

I would like to set up my server up so I can have remote access - http/80, ssh/22 etc.

The system has LAMP and SSH servers installed, with webmin for making control slightly easier.

Here's where the fun starts, though.

I'm in a confusing network. Look at it this way. My personal network is held within another network. While I have full access to my Personal stuff - router, server, clients. I have no access to the external router. It's a long story, but it's to do with where I live etc. Usual student life crap. So I've got my own, personal DHCP set up (I'm only allowed 1 mac address connecting to the external router at a time) within another DHCP setup. 

There are no ports restricted on the external router, so that's not a problem. And I can access my router's web interface when I type in my router's Wan IP, given by external DHCP. When I try and forward 80 and 22 to my server (set to a static IP within my network) I get timeouts. Nothing works. 

I've been reading about - [http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p3](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p3) specifically, and it mentions this:

```

127.0.0.1       localhost.localdomain   localhost
192.168.0.100   server1.example.com     server1
```

in /etc/hosts

which I don't have.

I have something like:

```

127.0.0.1       localhost
127.0.1.1       server.flatcluster.flatcluster  server.flatcluster
10.0.0.100      laptop
10.0.0.200      router

```

I know server.flatcluster.flatcluster is wrong. Any suggestions what I can replace it with - server.example.com? I don't own an example.com, does that matter?

I'm wondering - will I need to set up BIND, and what else can I do to sort this mess out?

For the record, DynDNS gets set to the external router's WAN ip.

Phew... confusing, eh?

Anyone got any ideas?

Hope this can all be sorted soon enough... give me something to do!

Regards,

Hibby

---

### Post by cariboo on 2009-01-20
The server name should be aliases to it's own ip address, just so you can access it by name. To access it from the internet you have to port forward it to the router that is connected to the internet, that you don't have access to. Htere is no other way to do it. Your router won't make any difference, it is really only working as a network hub.

It seems the network you attached to is set up to prevent what you want to do.

Jim

---

