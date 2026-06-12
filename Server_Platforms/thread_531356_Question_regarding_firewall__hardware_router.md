---
title: "Question regarding firewall / hardware router"
date: 2007-08-21
forum: Server Platforms
---

### Post by southernman on 2007-08-21
I am having a time getting my head around this. Would it be correct to say that even though I have an old Linksys BFSR41 router I should also use a software firewall such as shorewall or ipkungfu. 

I haven't really looked into IPTABLES how to as of yet... does it sound if my needs are basic enough that I should focus entirely on using this or will one of the front ends afford me an easier go of it.

On my router, I only forward the required ports 80 and 22 at this point... may do 443 for self signed ssl certs. NAT is disabled on the router.

To complicate matters even moreso, should I overlook the software firewall on the server itself, in lieu of running a dedicated firewall box with something such as smoothwall

My home network is very complicated *grins*

internet > dsl modem > router > two desktops and one server

A little off topic of firewalls but, seeing as webmin isn't in the repositories I am leary of using it. I've read another post by p_quarles that webmin should be used by someone new to server administration. Should I go ahead and install the latest version of webmin and sign up for update notices? (I probably should huh?)

I hope this isn't to muddled to be made sense of.

TIA 
Steve

---

### Post by a9k on 2007-08-21
I used to have the same setup as you with DSL->Linksys->multiple machines.

If you have a spare old PC around (800mHz P3 in my case) and two ethernet cards, then install IPCop on it [http://ipcop.org/](http://ipcop.org/). It's a great firewall for beginners and experts. I've saved a couple situations involving active expert hackers with judicious application of IPCop machines to partition a LAN. IPCop is able to forward ports to different machines on your private network. Handy if you want port 80 to go to your web server, port 22 to go to your home desktop and port 2222 to go to your webserver.

IPCop will save you from having to get your head around iptables until you have the inclination to spend a couple days on it. Also it includes support for Snort so you can see all the hacking attempts on your web server and become glad you set up a firewall.

I used to use Webmin when I was a beginner but I found that most times it was more work and much more tedious doing a task in Webmin than just editing the configuration files. In particular, I found the BIND DNS section annoying to use. Apache configuration wasn't much better.

---

### Post by southernman on 2007-08-21
Hey a9k, thanks!

If you have a moment (again) let me ask this of you.

I just listened to a series of podcase from Steve (GRC) and Leo. Steve suggested the use of 2 routers if running a home server... something like this attached image.

Couldn't the same thing be done with IPCop?

---

