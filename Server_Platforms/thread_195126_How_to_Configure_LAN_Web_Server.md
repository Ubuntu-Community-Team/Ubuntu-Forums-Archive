---
title: "How to Configure LAN Web Server"
date: 2006-06-12
forum: Server Platforms
---

### Post by DapperGra on 2006-06-12
Hi everybody,

I'm a new user of Ubuntu and i would run a Linux Web Server for a whole lan network. My target is make a web site on my linux web server machine browsable just from the computers connected to the lan.

So, I ve already installed successfully Apache2 and Bind9...the test page on apache seems to work but the idea is giving a DNS name in order that whenever the server is rebooted and automatically change IP (it happens more or less every time i reboot or connect for a new time to my LAN network) i can just put the name foregoing the IP number.

Then, to do so i try to set up a db.example and a db.192 files and update the named.conf in order to make the mapping.

Now, the problem is that when i put the name whereas the IP number i see that other web pages are running from the net....firefox start to look around the net for the name that i put and open others URL.

Somebody could please Tell me how i can do that step by step?

Thanx

Graz

---

### Post by mjm115 on 2006-06-12
This is not an issue with your server, but an issue with your router and DNS.  How are you connecting to the Internet?  Is it a direct connection, or do you have everything going through some type of router/firewall?

---

### Post by DapperGra on 2006-06-12
Well, I m connected to a LAN network that go outside with a router. The Lan is firewalled that means that i outside the LAN can,t see any computers....I hope i was clear...

---

### Post by houstonbofh on 2006-06-12
This is a name resolution issue, not a server issue.  Since you did not tell us what you are using, I will just use my router as an example...  In m0n0wall ([www.m0n0.ch](www.m0n0.ch)) the router does DHCP and DNS forwarding.  There is a checkbox to register DHCP leases in DNS.  You need to find this for your router, or whatever does DHCP and DNS for you.  The other thing you must do is make sure your default domain name is accurate.  Then it will work.

---

