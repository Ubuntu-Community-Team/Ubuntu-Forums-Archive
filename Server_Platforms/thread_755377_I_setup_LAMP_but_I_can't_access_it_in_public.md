---
title: "I setup LAMP but I can't access it in public"
date: 2008-04-14
forum: Server Platforms
---

### Post by haryoh on 2008-04-14
I setup LAMP but I can't access it publicly. I setup SSH and other things I love to have on a web server but there is no public access. Help.

---

### Post by Canuckelhead on 2008-04-14
I am assuming that localhost works from the same system?

Make sure if you are using a router, it is port forwarding to the right computer.

---

### Post by haryoh on 2008-04-14
Localhost runs from the same computer. I'm using a router(linksys). could this be the problem? What do I do?

---

### Post by PilotJLR on 2008-04-14
Have you forwarded port 80 from the router to the static private address of the ubuntu system?

---

### Post by Canuckelhead on 2008-04-14
Right on. Go into the router settings and set prot 80 for web server/ 21 for FTP etc to forward requests to the network IP of the machine with the servers.

I'd also have that machine use a static IP rather than using DHCP.

---

### Post by haryoh on 2008-04-14
Ok.. I will do that when I get home. Am still at work right now.. but I will message you guys if it works.

I'm thinking of doing something. like using Windows server 2003 as my DNS using DC(domain controller) and forward a sub-domain to my ubuntu hostname. I don't know how cool that is. but I'll try what you guys just thought me now...

Thanks

---

### Post by Canuckelhead on 2008-04-14
Post your router type and I'll give you more specific instructions if you needem.

---

### Post by haryoh on 2008-04-14
cool.. I will... how long will you be on the forum for?

Linksys® WRT54G Wireless-G Router
I use a linksys switch which is an old switch but my server is connected straight to the router.

---

### Post by Canuckelhead on 2008-04-15
Yeah go into the router 192.168.1.1

and then select the applications and games I think the tab is called.

set port 80 in the left side and have to forward to the IP of the ubuntu machine...

then any requests from the outside will be routed to that machine's webserver.

That router also works well with DYNDNS which is a plus you can set up a Nomain name that will be updated if you have a dynamic IP from your ISP.

---

### Post by haryoh on 2008-04-16
Thanks for that information. I figured it out but wasn't sure until I saw what you posted to me.

I might be having a simple problem though. Setting up the BIND9, I don't  how to come about setting up a reverse or forward zone DNS so I can know what to add to my registrant's DNS lists.

Thanks so much for your help.

---

### Post by Canuckelhead on 2008-04-16
That's outa my league.

I'm ok with the small stuff (I run a pretty basic system using DynDns.)

Hopefully everything is working o.k. for you.

---

