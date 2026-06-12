---
title: "Setting up virtual network as a testing lab"
date: 2017-05-24
forum: Virtualisation
---

### Post by LastDino on 2017-05-24
Okay, I've interest in learning networking so I could setup a home server when I actually do have money to buy more hardware. 

Right now, I do not have that option so I've been preparing VM, with lot of guests installed.

Right now, these are the guests installed in Virtual Box (Oracle Virtual box manager). Host is Linux eOs Loki

Ubuntu Server
Ubuntu
Win7
Manjaro
Kali

I intend to update laptop with some 8Gb more ram as 4 really wont be sufficient. Have i3 processor and also have prepared one WD external hard-disk for backup and ISO as well VDI storage. Also have spare router of TP link, not sure if it will suffice though.

This is not some huge project, but some basic one where I will learn to deal with various networking setups,  like that of NAS, Media or only some firewall or Email. Honestly, I don't know yet. I don't know if this is possible either. I would also like to do penetration testing in this same network.

I've tried googeling but didn't see anything that will address my query which is with free tools like Oracle VM and not with Workstation. 

If it is not too much trouble, and if you nice people out there have access to resources like easy **tutorials**, **things I should know **etc..which will help me in this process. I would like it very much if you could link me the same. 


Sorry, if this sounds bit silly, but I don't have computer background in education so mostly my one sided love affair. Please help with anything you can think of.

(don't know if right section, but guess VM related query so posted here)

---

### Post by TheFu on 2017-05-24
Don't do pentesting on a network connected to the internet. This needs to be a separated LAB. Don't want nasty stuff getting out.  Air gap. BIG TIME!

Lots of people use virtualbox. I did too, for a few years. Outgrew the capabilities it provides, plus it has high overhead when compared to KVM.  If you want to do non-trivial networking, you'll want to use [openvswitch]("http://openvswitch.org/").  

You can also use a virtual machine to run a router. Look at running pfsense/opensense.  Only use virtualization for a router inside your LAN. Never use it for your gateway. NEVER.

A Core i3 really isn't enough power to run as many VMs as you want.  Upgrade that.

Also, you'll want to add multiple NICs (intel pro/1000) to the system. Then you can add relatively cheap switches for your network needs.  Get 1 managed switch - about $75 and a few dumb switches for $20/ea.  Those will go a long way.

Look for used servers on the cheap. Just beware that servers suck lots of power, so if you need to avoid a huge power bill, be careful getting the 95W to 200W CPUs. They make lots of heat, which means lots of cooling and perhaps higher air conditioning bills.

A laptop really isn't sufficient for running a lab.  Get/build a cheap "server."  Upgrades for parts will be 50x less and a $300 desktop/server will blow away a $1000 laptop.  It is amazing what a $120 "server" can do.  Mine runs Plex, Kodi, Calibre and about 15 other services for my network, including the NAS.

Never, ever, forget backups. ALWAYS. Storage fails all the time. Had a disk fail last week. It was a minor inconvenience, nothing more.

For what you should know .... that is too long to list.  If you want to learn Linux, I have [this to say]("http://blog.jdpfu.com/2014/12/28/learning-linux").  If you want to run servers, then [this to say]("http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server").  Be consistent. Be paranoid.  Have a strong, layered, network architecture. Don't assume 1 network device provides "security."

And lastly, stick with LTS ubuntu releases.  Avoid as many bugs as possible. Servers should always run LTS, IMHO.

---

### Post by LastDino on 2017-05-24
Plan to get the desktop one six months down the line but till then need to get used to all the configurations. It wont be connected to Internet when I'm trying out pentesting within the network, so even if 2 machines at a time are able to run from the VM and I can try these settings, it will be sufficient. At least till I get hang of it and try the real hardware.  

And yes, all the versions I've installed in VM are LTS ones for Ubuntu. Others I keep upgrading with newer releases. Win7 is isolated machine with no net, but will come in handy to try networking with windows environment.

Any tutorials available for this? That links on "if you want to run a server" is not working for me. And yes, this is part of my Linux learning journey, just would like to develop the skill before actual money starts flowing there.

---

### Post by TheFu on 2017-05-24
No outages here this week.
```
Period 20170521-062611  - 20170524-132211
  Total Time: 4738 (min) 78.97 (hrs)
  Percent Up Time: 100.00 % 
  Percent Down Time: 0.00 % 
  Total Down Time: 0 min or 0.00 hrs
```

Try google cache or the [way-back machine]("https://archive.org/web/") or a vpn that exits from a different country.  Some countries decide to block the blog. Don't know why. I've seen issues in Thailand, India, Pakistan and parts of the middle east. Google doesn't think I'm dangerous. ;)

I also block some subnets due to past problems like attempted hacking.  Some *big name* corporate subnets are included, sadly. Sorry if you are caught up in my blocking.

When someone visits your home and behaves badly, there isn't much choice than to throw them out.

BTW, I have an i3 on my chromebook and run VMs once in a while on it.  In my office, I have a 7 yr old Core i5 that runs most of my VMs. Next to it is an i7 and a G3258 and another i5.  Retired a bunch of C2D systems, though they also ran 20 VMs before the main i5 took over that workload.

Those links are full of other links to learn Linux and learn to run linux servers.  You can probably find them on your own. I tried to stay with free or CC licensed stuff.  I use CC licensed training materials in my Linux admin classes. Makes life easier than forcing the class to buy a book that is already out-of-date before it gets printed.

---

### Post by LastDino on 2017-05-24
Hmm, will setting up openvpn on my eOs solve the problem? 

/just curiouse

---

