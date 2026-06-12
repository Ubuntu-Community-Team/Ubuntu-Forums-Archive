---
title: "Is it ready for small home server?"
date: 2012-01-22
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by mattlach on 2012-01-22
Hey all, 

I'm struggling with what Ubuntu release to install on my home server.

My old one (running 8.04 LTS) is dying and in desperate need of replacement, so I have to do it very soon.

Once in place the server needs to live with whatever version it has installed (I don't trust upgrades, and don't want to bring it down for a full reinstall and reconfigure)

To this end, I only use LTS releases for my servers.

So my choices are to go with the soon to be replaced 10.04 LTS, or risk it and go with the 12.04 LTS alpha.

What would you do?   How stable is the alpha for server use currently?

Much obliged,
Matt

---

### Post by MG&amp;TL on 2012-01-22
It's not. If you want to run a server, go for 10.04. Obviously that's my opinion, but sensibly you're not going to run a server off an alpha. Test machine, or laptop maybe, not a server.

---

### Post by snowpine on 2012-01-22
"Soon to be replaced" is April 2015. :)

---

### Post by philinux on 2012-01-22
> **MG&TL said:**
> It's not. If you to run a server, go for 10.04. Obviously that's my opinion, but sensibly you're not going to run a server off an alpha. Test machine, or laptop maybe, not a server.

+1 why would anyone risk alpha software. Wait to April.

---

### Post by Double.J on 2012-01-22
I'm with MG&TL & Philinux here, you don't want to be putting loads of effort into a server - just set it up and let it run as long as possible, especially at home :)

If nothing else just the amount of updates coming through will cause too much maintenance! Things are being fixed and broken on a daily basis at the moment, If I were you I'd stick with 10.04 until the release of 12.10.. with servers stability is usually far more important than "the latest thing" :)

One thing for future reference is that it is really best practice to upgrade your server once it becomes unsupported - for this reason I suggest 10.04. There is nothing wrong with 8.04 at the moment; support will not cease for this until 12.04 has been out a year (a good time to switch). However if you are setting up a new box, 10.04 gives you more longevity and newer packages until you decide to switch ro 12.04.. if you do! if you had a reason (I have no idea what) to really not run 12.04, 10.04 would last out until 14.04 (I'm routing for "Tyrannical Tasmanian Devil")

---

### Post by mattlach on 2012-01-22
Thank you guys, I appreciate the input.

My primary concern was security, especially as I am considering using the server as my edge device for my home network.  

My philosophy here has always been that newer versions = better security, as old holes have been fixed, and new ones have likely not been discovered yet.

I know that 10.04 will be supported until 2015, but won't the older packages have higher security risks?

---

### Post by MG&amp;TL on 2012-01-22
> **mattlach said:**
> Thank you guys, I appreciate the input.

My primary concern was security, especially as I am considering using the server as my edge device for my home network.  

My philosophy here has always been that newer versions = better security, as old holes have been fixed, and new ones have likely not been discovered yet.

I know that 10.04 will be supported until 2015, but won't the older packages have higher security risks?

...not really, probably slightly, but if you secure your system properly, on a home network, probably not a problem. And you're the one running 8.04. :P

If you're that bothered, upgrade to 10.04 now, then use 12.04 when it comes out. But I'm thinking you're not, so either wait, or use 10.04.

Hope we're helping. :)

PS by all means, use 12.04-but don't expect stability. :)

---

### Post by snowpine on 2012-01-22
> **mattlach said:**
> My philosophy here has always been that newer versions = better security, as old holes have been fixed, and new ones have likely not been discovered yet.

I know that 10.04 will be supported until 2015, but won't the older packages have higher security risks?

Someone on the security sub-forum can probably answer your question with more authority than I can, but in my limited understanding, Ubuntu "backports" security patches from newer upstream versions of a package to the "frozen" stable version number supported for the LTS release.

Here is a much better explanation of what I'm trying to say (written for Red Hat but also applies to Ubuntu): [https://access.redhat.com/security/updates/backporting/?sc_cid=3093](https://access.redhat.com/security/updates/backporting/?sc_cid=3093)

In terms of age-of-packages, Ubuntu 10.04 is roughly comparable to Red Hat Enterprise 6 and Debian 6, which are widely considered among the most secure server distributions.

---

### Post by effenberg0x0 on 2012-01-22
I have a 24/7/365 Ubuntu server at my Home-Office that is responsible for a lor of stuff like home automation, load-balancing 3 broadband connections, dhcpd for all other devices, local dns, ftpd, firewall, printers/scanners server, vpn, git, svn, transmission, sickbeard, sabnzbd, some instances of xbmc that run in different rooms and lircd instances to their remote controls, sshd, dyndns, apache, PHP, SQL, NFS, Samba, apt-proxy, security cameras, mpd, it mounts my remote personal work folder to a local one via ssh so I can work from home, mdadm RAID 1 for system and mdadm RAID 5 with 10 hotplug Sata HDD for Storage, etc. 

It was running MM until a couple weeks ago. I'm testing it with PP for 2 weeks now. It works OK: I haven't stumbled into any serious problem. But please note that:

- It's under a barracuda security appliance and a professional router
- GUI is not a concern. I create X sessions only for XBMC instances that run on the TVs, but there's no desktop. 
- All ports (web, ftp, dns, dhcpd) are at alternative numbers and respond only to the lan. When I'm outside I have to authenticate via encrypted RSA key+login in the appliance and then SSH to the services alt. ports, also with encryption and login/passwd. P2P/download services and web server run in VMs, saving/allowing access exclusively to limited virtual disks. 
- I keep hourly, daily, weekly, monthly backups of it's content folders in the RAID. Local machines securely rsync to it and backup with the same frequencies. Some events are logged and SMS'ed to me.
- Since all machines depend on it to work (to get an IP, dns, etc), it's running with it's own UPS. The broadband modems, router and security appliance also are attached to UPSs. 
- It's not a setup one will generally do at home and it takes some time and investment to set a rack like this and make it work perfectly. 

I wouldn't feel comfortable advising anyone to go for PP at this development stage. In my case, I'm relying on what I consider to be a very safe environment, but I'm willing and prepared to deal with any fault. I wouldn't consider putting it on a personal server, much less a work server, if it wasn't for this environment in which I trust.

Regards,
Effenberg

---

### Post by Dangertux on 2012-01-22
A note about the security updates. All non end of life versions of Ubuntu receive security updates. This means 10.04 will receive security patches until April of 2015. 

Though the base application may be an older version. (stable and LTS type released usually are) the security updates are backported appropriately. In your case I would recommend 10.04. 

 Hopefully this is helpful.

---

