---
title: "Office Server - How secure?"
date: 2011-05-29
forum: Security
---

### Post by Li1t on 2011-05-29
I'm presently setting-up a small server for my work (a web development company) to replace our gradually fossilising network drive. This drive has been at the company for longer than most of the staff, including me, and stores pretty-much everything the company does (from project briefs, through design masters, to the source for every site).

First-off, I'd like to get proper version control up and running, although I've also been asked to install Samba for general shared storage (not everyone is technical and knows/needs to know how to use SVN). Secondly, I'd like to create a proper development environment that can be used to test changes and export files to the production server when ready. I'd also like to make this system web-accessible to facilitate working from outside the office, probably limiting access to SSH/SFTP and HTTP(S). External SVN access will be via tunnled SSH. Some staff members have also asked for VPN access, probably through pptpd if it's secure enough.

Now I can handle most of the scripting, I have the Samba, SVN, and SSH servers up and running, but I'm wary of making it accessible to the internet without some form of additional security. It's not like we'll take credit card details or anything on it, so it doesn't need to be PCI compliant, but I know I want it hardened to some extent.

I experimented with installing and running Bastille, but thankfully I had the forethought to test this under virtualisation as it gave a bunch of errors when I applied the changes and made it impossible to log-in after I restarted the virtual machine (every attempt gave a "Module is Unknown" error). I'm thinking I'll avoid Bastille.

I'm thus left with an extremely long Securing Debian manual and a number of choices in terms of how exactly to proceed. I thus have a few questions:

[LIST=1]
[*]I've been looking at SELinux, but after hearing a lot of people talk-up how complex it is I'm wondering if I might not be better going with an AppArmor setup. What's the general consensus?
[*]I'm fairly certain I want apache in a chroot jail. Are there any other security suggestions you'd recommend for such an environment? I've been looking at suexec and wondering if that'd be a worthwhile addition.
[*]What steps should be taken to secure SVN, Samba, pptpd?
[*]Are there any other Daemons you'd recommend jailing? I don't think I'll be running BIND or Sendmail, but I could possibly want to in future.
[/LIST]

Cheers :guitar:

---

### Post by HermanAB on 2011-05-29
Hmmm, I think the first thing you got to do is to make a backup.

Secondly, ensure that the network is properly firewalled and that everybody has a proper, looooong password.  

Then, you can think about installing Samba etc...

---

### Post by Lars Noodén on 2011-05-29
> **Li1t said:**
> ... Some staff members have also asked for VPN access, probably through pptpd if it's secure enough...

It's not. ;)  PPTP or L2TP can only be secured by tunnelling it through IPSec or SSL. In that case you are better off running a plain vanilla [ipsec or ssl](http://www.vpnc.org/vpn-standards.html) VPN.  But truly if your service is not robust enough to be on the net without a VPN, then it probably has no business using TCP/IP at all anyway.  Samba is good enough there. Same for SVN and the other versioning systems.  The VPN will be more hassle than benefit.

As far as remote access goes, you can also do a lot with just SSH/SFTP or SSHFS (also SFTP).  That can be a supplement to Samba.

---

### Post by Li1t on 2011-05-30
Thanks for the input - it's definitely food for thought. I think we'll leave the VPN out for the time being, as the people who've requested it are technical enough to use SSH anyway.

Setting up automated backups ASAP is a good call, but what degree of backups to go for? Maybe 7 days remote backups (rolling rsync), but the main issue is where to store them. Ideally we'd rent space on some storage server somewhere, but we'd want somewhere a) secure and b) cheap. Any suggestions?

Right now, the office network is behind a router with a very basic firewall, running over NAT and forwarding ports to the server. As such, we do run security software on each of the machines, but there's no centralised security. I had contemplated going the whole hog, buying a second network card, and setting it up as a proper firewall/router for the office. Do you think that would be a good idea?

Thanks again!

---

### Post by Lars Noodén on 2011-05-30
> **Li1t said:**
> 
Setting up automated backups ASAP is a good call, but what degree of backups to go for? Maybe 7 days remote backups (rolling rsync), but the main issue is where to store them. Ideally we'd rent space on some storage server somewhere, but we'd want somewhere a) secure and b) cheap. Any suggestions?

I'd say get a few usb drives and rotate through those.  Two would be the minimum, so that one is always off site.

---

### Post by Lars Noodén on 2011-05-30
> **Li1t said:**
>  I had contemplated going the whole hog, buying a second network card, and setting it up as a proper firewall/router for the office. Do you think that would be a good idea?


There are advantages, but I'm hesitant to recommend making changes to any production system that is proven to be working as-is.  How do you see the changes as an improvement over the current setup?

---

### Post by Li1t on 2011-05-30
> **Lars Noodén said:**
> I'd say get a few usb drives and rotate through those.  Two would be the minimum, so that one is always off site.Cheers, I'll suggest that to my company and see what they say. We do have a similar practice in-use to back-up our network drive, but copying the files needed to be done manually, from a drive with an archaic (probably 10BaseT) network connection. 

I know the production servers are backed-up to another server, but I expect the two backup USB HDDs option will win on both price and ease of recovery.

As for implementing a proper firewall/all-in-one server... I feel relatively secure behind a NAT router with basic firewall, all of the machines are running their own security software as it is. I was mostly wondering in response to HermanAB's suggestion above.

---

### Post by tubbygweilo on 2011-05-30
> **HermanAB said:**
> Hmmm, I think the first thing you got to do is to make a backup.

Secondly, ensure that the network is properly firewalled and that everybody has a proper, looooong password.  

Then, you can think about installing Samba etc...

Baby steps first, these are the basics and when done (and backups tested) then it is time to think further.

Remember a tried and tested backup procedure / protocol is always a good place to start from.

---

