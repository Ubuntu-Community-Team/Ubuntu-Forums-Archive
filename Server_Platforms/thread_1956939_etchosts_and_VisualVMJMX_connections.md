---
title: "/etc/hosts and VisualVM/JMX connections"
date: 2012-04-11
forum: Server Platforms
---

### Post by vapid2323 on 2012-04-11
Hey guys, I am sorry but I googled the crap out of this one and I am still not really understanding the job of the hosts file and if mine is setup correctly. 

I am attempting to connect to my server from home to get stats for my java application. I have all the needed ports open and I am able to telnet to the ports but no matter what I do I cant connect to the JMX Server after its running.

I was told it might be because of my hosts file, and something to do with my domain. I have had an error show up when one of my admins uses sudo and it might be related. 

```
127.0.0.1	localhost
127.0.1.1	vapidflats.com	vapidflats
127.0.0.1 BukkitServer localhost.localdomain localhost
216.22.20.194 vapidflats.com MC

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

If anyone can tell me how to confirm this is setup correctly that would help a bunch. I am just a bit confused on this file and what needs to be placed in it.

Let me know if I am missing any information that you need to help me. :D

---

### Post by Jonathan L on 2012-04-12
Hi Vapid

The role of the hosts file is to translate names to IP addresses, just like the domain name system.  The difference is a) the /etc/hosts file is private to the computer it is on, and b) it normally overrides the DNS.

As far as I can tell you're trying to connect to a public server from your home computer, and ordinarily you wouldn't need to put anything in particular in your /etc/hosts.

I'd try putting your /etc/hosts back to normal.   In particular you have two entries for vapidflats.com, which almost certainly will go wrong as name lookups will use the first one.  (Ie note that vapidflats.com is in the DNS as 207.244.153.118, a different address again.)   Are you able to connect to your services by literal IP address rather than name?

Tell us the error message you get and perhaps we can help some more.

There is only one thing I can think of where you pretty much must use /etc/hosts, and that's the circumstance where a) you're contacting a server by name (eg, name-based virtual web servers) and b) you can't change the DNS, or c) where you need different answers in different places.

Here are a few typical uses that people put /etc/hosts to:


[LIST]
[*] Alan has a laptop and is the only user of a rented server somewhere on  the internet.  Instead of using DNS he just puts the name and IP address  in his laptop's /etc/hosts
[*] Beth has a server and a laptop at home, 192.168.0.32 and 192.168.0.128.  She runs the server as a web server and has his router forward to port  80.  Her public home IP address is in the DNS for the server.  She puts  server.example.com. with the address 192.168.0.32 in her laptop to override DNS on her own laptop only.
[*] Charles has a family each with a laptop, and a file server which stays  on.  Each laptop copys /etc/hosts from the server when it boots.  He  does this instead of running local DNS, as it's pretty straightforward  and only changes once a year.  The real reason he does it is because  he's old and that's how they did it before DNS.
[/LIST]
 
Hope that's of some help.

Kind regards,
Jonathan.

---

