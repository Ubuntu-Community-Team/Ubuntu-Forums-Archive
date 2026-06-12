---
title: "network routing server"
date: 2010-07-16
forum: Server Platforms
---

### Post by staticextasy on 2010-07-16
Okay everyone. ilve recently decided that i wanted to do a network routing server for my home network. i have a 6 yr old dell machine that i plan on using.  for this setup i want to have the network routed with wired and wireless access. 

now to my questions.

what extra hardware should i be in the market for? extra nic cards, wireless access point?

what kind of setups can be achieved? im not limiting myself to one solution im actually looking for a variaty of options and see which one may suit me best.

my OS of choice will of course be server 10.04 LTS. getting/finding hardware for the setup will not be a problem.

My reasons for wanting to build this network routing server is for advanced security reasons, bandwidth limiting/monitoring. and just for the fun of it.

also what do you think about also using this machine as a file storage server as well as a web development server(apache and database) as far as conflicting with network routing. 

any opinions are welcome and article suggestions welcome to. 

thank you

---

### Post by iponeverything on 2010-07-16
> what kind of setups can be achieved?

A better question would "what can't achieved?"

The sky is the limit. 

> network routed with wired and wireless access.

routing -
Most routing in for home consist of a automatically generated route for local interface and a default route for everything else.

wireless access -
wireless access would best be achieved through dedicated wireless router, my preference would be something that support dd-wrt. Though if you do decide to by card and have machine also serve as an wireless access point, note that you have to buy a device that supports AP mode under linux and you will more than likely lose quite a bit with regard tx power. For the the same cost, you can get a dedicated wireless router that supports dd-wrt. 

interfaces -
I think the machine should have 1000-BaseT interface.
Buy a cheap small 1000-BaseT switch to attach to it. 

> 
network routing server is for advanced security reasons, bandwidth limiting/monitoring. and just for the fun of it.


advanced security -
there are tons of tools that put on the box to achieve about anything you imagine.

> bandwidth limiting/monitoring

bandwidth limiting - 
TC is quite useful for this. 

monitoring -
Ntop is very good.

---

### Post by YesWeCan on 2010-07-16
[QUOTE=staticextasy]My reasons for wanting to build this network routing server is for advanced security reasons, bandwidth limiting/monitoring. and just for the fun of it.

also what do you think about also using this machine as a file storage server as well as a web development server(apache and database) as far as conflicting with network routing.[/QUOTE]
Go for it! Since I started using linux 9 months ago my computer belongs to me again. And I managed to revive a disused laptop and now it is a useful resource.
If you want a dedicated router then there are a load of custom linux distros available; install, a few configs and you are done.
It sounds like Ubuntu would be good so you can add lots of other services. I have a 10.04 server that runs an Apache webserver, a complete email service (Fetchmail/Postfix/Dovecot/Squirrelmail), a mySQL database server, a RAID filesystem, an OpenVPN server for "road warrior" and for remote administration via VNC, and a Java/Netbeans development platform.
I am not sure how to predict the router performance of your Dell. 
[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)
[http://www.linuxjournal.com/article/5826](http://www.linuxjournal.com/article/5826)
[http://en.wikipedia.org/wiki/List_of_router_or_firewall_distributions](http://en.wikipedia.org/wiki/List_of_router_or_firewall_distributions)

---

