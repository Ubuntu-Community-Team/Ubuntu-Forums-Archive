---
title: "Newbie DNS help"
date: 2009-02-04
forum: Server Platforms
---

### Post by tr33m4n on 2009-02-04
Hello there,

Basically im new to the whole DNS thing... I've been running a server for a while and have become pretty adept at doing everything, but never really got my head around DNS. Basically as it stands i have a dyndns account assigning my ip a domain name... however this is just a forward. I have purchased a proper domain name and I have just upgraded my connection with my ISP to have a static IP address rather than dynamic. Basically im confused as to what information my domain name provider needs and what information i need to put in my server. Eg, do I use my isps dns servers? use my domain name providers dns server? what ip do I put where? what dns records do I need to change in my domain names admin panel? Im very confused

Any help would be greatly appreciated
Cheers
Dan

---

### Post by HermanAB on 2009-02-04
As a minimum, you need an A record.  Preferably, you should have a PTR record as well.  The registrar you got the domain name from, should provide a wizard for that.

On your server, you should point to the fastest domain name servers you can find.  This would normally be your ISP name servers.  You can test the name server speed with 'dig'.  See 'man dig' for details.

Hope that helps!

Herman

---

### Post by tr33m4n on 2009-02-08
Hello again,

Thats cleared a few questions up... I'm still not sure what I should be doing though... Basically my server is behind a router with firewall that points to my isps dns servers for the internet connection. I have recently installed bind9 but I am confused as to what sort of setup I need... so i basically just have it as a caching name sever atm, with my isps dns servers forwarded. Is this correct? My goal is to have example.com resolve properly to my server so i dont have to use 'web forwarding' from my domain name provider.

Thanks for the previous message, however I'm still a tad confused :s

Cheers
Dan

---

### Post by HermanAB on 2009-02-08
It is always smart to install a cacheing name server, since it is zero maintenance and speeds up web access enormously at your end of the wire.

If your Registrar handles the DNS for your domain, then you need not do anything.  Within 3 or 4 days of registering, the whole world should be able to resolve your new domain.

You can test whether your registrar DNS works with nslookup or with dig:
$ nslookup example.com
$ dig example.com

or
$ dig @registrardnsipaddress example.com

Cheers,

Herman

---

