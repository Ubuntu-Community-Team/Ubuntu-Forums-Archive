---
title: "iptables -- really that necessary?"
date: 2011-02-10
forum: Server Platforms
---

### Post by garfonzo on 2011-02-10
Hey Folks:

I'm about to set up a Linux server to host a business website and an online private (staff only) web database (MySQL backend) which handles the businesses daily operations. My plan was simply to put the server behind a router and call it a day, but should be thinking about setting up iptables? Or, should I consider a hardware firewall? I just figured the router would suffice as far as keeping unwanted connections out. 

Any thoughts?

---

### Post by rudelgurke on 2011-02-11
Hmm - dunno what you want to protect with Iptables. Don't let MySQL listen on your external IP and check with netstat if everything looks fine.
Usually then you won't need Iptables - could even open more security problems when activating it.

---

### Post by stlsaint on 2011-02-11
never underestimate the effectiveness of a good firewall. Considering you will have some open ports i would say that a basic firewall would just be a nice extra layer of security. Especially if you ever open up a ssh port (trust from personal experince that unless you have a good option based router than it will not protect much against attacks) my servers are attacked on a constant non-stop daily basis and iptables lets me sleep easy at night. Even if its to stop your basic DDOS attack, iptables is invaluable. Any server i ever manage that runs linux will run iptables. Im a bit of a security nut though so thats just me. I would say at least read up on them: [http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

---

### Post by garfonzo on 2011-02-11
Thanks for the responses. I did a bunch of research last night on iptables and, while they seem potentially complicated, they may also be rather straight forward. On a howtoforge.com tutorial, they mentioned locking *yourself* out of your own system by not setting up the proper "allow" rule. That would suck.

I think that with this server sitting listening to various ports (SSH, SFTP, web connections...) I'm leaning towards putting iptables on this thing. As mentioned, it would allow me to sleep at night knowing that there is at least a decent line of defense against script-kiddies out there in the interwebs. I've become a "backup junkie" after I was burned hard with a drive failure and now with this server going online I think I, too, will become something of a security junkie *before* getting burned by having my system taken down by an attack. 

I think I will set up a few basic rules to block everyone out but me, then slowly open the necessary ports.

---

### Post by iissmart on 2011-02-11
Look into pgl/Peer Guardian/Moblock/blockcontrol. It it normally used for P2P security but also contains lists for all types of security like hackers, bots, etc. It will automate your iptables entries for you and gets freshly updated lists daily. Pretty much impossible to lock yourself out with this software, and it runs quite well. I run it on an HTTP server that gets hit with bad guys daily. If I turn it off, in about an hour my disk is trashing with I/O requests and I can barely ssh to my server because there are so many apache threads. With it running, the system is at 4% load and runs perfectly, without over-blocking the good IP addresses.

---

### Post by rudelgurke on 2011-02-11
Would still say Iptables isn't necessary in the most cases. You've a Webserver, SSH, SFTP running and nothing else.
So why DROP or REJECT packages on ports where nothing is running anyways ? Specially for the dDoS / DoS issue - that should be done application side on the ports that are open and your server provides.
mod_security as example for Apache.
And what's the sense blocking a 2 MB Ping Request ? The traffic already made it to you, your server had to handle it. And dDoS attacks that just flood your IP or your Webserver - there Iptables won't even help except you completely block anything - result is the same that your machine isn't reachable from the outside.

Better take care of the services you provide and you most probably want to let your customers access, if you've done this maybe then think about a firewall but still, in the most cases it's pretty useless.
As example:

iptables -A INPUT -p TCP --sport 1024:65535 --dport 80 \
 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTPUT -p TCP --sport 80 --dport 1024:65535 \
 -m state --state ESTABLISHED,RELATED -j ACCEPT

Would as you see allow connections to your Webserver and allow it reply to these connections. Additionally only clients ports.
Still bots, other webservers, etc. etc. will act as clients when they try to access content on your webserver anyways.
Anything else - mod_security will proud to get rid of it.

Still the result of a typo would probably look yourself out or:

[http://kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.21.4](http://kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.21.4)

"[PATCH] NETFILTER" ...

So this additional layer of security opened - in this case - an additional hole on your system. Without it, no hole, no problem.

Let your router handle it, if you really want to "firewall" - do it there, not on the same machine. Still this all won't help against bad PHP scripts, insecure configuration etc.

---

### Post by iissmart on 2011-02-11
Oh, if you're running it behind a router let it handle the TCP/UDP ports by only port forwarding the one's you'll be using: 80, 22, etc. However, at the IP layer you'll want blockcontrol to filter IP addresses that are hitting you constantly through port 80. Since it's using iptables it operates at the kernel level so your application doesn't have to deal with it.

---

### Post by garfonzo on 2011-02-11
Thanks for the responses. I see your point, rudelgurke. I have never used a full on firewall before for my personal systems (including my 24/7 linux server) and have never had a problem. I was just thinking that in this commercial situation, perhaps I should step up my security situation. I will be locking down the system and ensuring that each application/server (SSH, MySQL) is individually secure. 

> **iissmart said:**
> ... you'll want blockcontrol to filter IP addresses that are hitting you constantly through port 80. Since it's using iptables it operates at the kernel level so your application doesn't have to deal with it.

So blockcontrol (formerly mod_block I believe?) essentially has a list of IP addresses which are known to be malicious and simply denies them any access on port 80 (the web port)? That is pretty cool. So, since I *will* be hosting the server behind a router only and **only** opening the few ports necessary (22, 80, etc.) I should be good to go (and with blockcontent running)? 

Sounds like a good setup.

---

### Post by iissmart on 2011-02-11
Yeah, I'm not sure what the actual program is called. I think it started with PeerGuardian Linux, but then became MoBlock, then someone created blockcontrol to act as a "wrapper" for MoBlock, then they changed blockcontrol to pglcmd, or something. "mobloquer" fits in there somewhere too, but I have no idea. And don't forget nfblock which is a clone of moblock. :)

On my web server I use blockcontrol to manage iptables, but the official site now references pglcmd: [http://moblock-deb.sourceforge.net/](http://moblock-deb.sourceforge.net/)

The user jre on this forum maintains it and has helped me in the past: [http://ubuntuforums.org/showthread.php?t=1456841&page=2](http://ubuntuforums.org/showthread.php?t=1456841&page=2)

---

### Post by garfonzo on 2011-02-11
> **iissmart said:**
> Yeah, I'm not sure what the actual program is called. I think it started with PeerGuardian Linux, but then became MoBlock, then someone created blockcontrol to act as a "wrapper" for MoBlock, then they changed blockcontrol to pglcmd, or something. "mobloquer" fits in there somewhere too, but I have no idea. And don't forget nfblock which is a clone of moblock. :)

On my web server I use blockcontrol to manage iptables, but the official site now references pglcmd: [http://moblock-deb.sourceforge.net/](http://moblock-deb.sourceforge.net/)

The user jre on this forum maintains it and has helped me in the past: [http://ubuntuforums.org/showthread.php?t=1456841&page=2](http://ubuntuforums.org/showthread.php?t=1456841&page=2)

This is great! Thanks for the links. I think this will become my solution.

---

### Post by elico on 2011-02-11
there is a myth called "Hardware Firewall".
firewall is an application level software in any variation you will look at it so dont bother thinking "hardware or software?"
the only different between what called "hardware firewall" to other machine is the level of compatibility of the firewall core to the Hardware.
many so called Hardware firewalls are using iptables or other software firewall.
all freeBSD based devices such as juniper are using the default freeBSD core firewall software IPFW or PF.
almost any linux based  firewall device is using IPTABLES as default because linux kernel is native to IPTABLES.

and to the bottom line: if you can use good firewall on the machine use it cause it's much more than a car safety belt!!!

just to understand the different of traffic in the machine and inside the machine:
yes indeed the lost download\upload bandwidth for the 2MB ping packet got to the machine interface
it doesn't mean it should get to other places on the kernel level processing it.
if you want to test the effect on open machine over closed machine be my guest it's one of the most fun things in the world!!

ubuntu comes with iptables built-in so just add 3 rules to the input interface to defend your server of DOS or DDOS.

it will take almost 30 seconds to put it in the machine.

---

### Post by rudelgurke on 2011-02-11
If you refer to ICMP or TCP synfloods and some other lower level attacks - sysctl is the way to go.
Then the kernel won't process such things anyways, using Iptables instead is the wrong way to get rid of such things.

Putting a box in front of the server that runs - as example - OpenBSD + PF and nothing else, really nothing else, that's a Firewall solution.
Running it on the same box as the services it should protect - well, see Windows and these so called "Install, Activate, put Brain in Offline Mode" security sites.
And still autoblocking IP's based on attack patterns can result in a lot of unwanted damage to potential customers - don't think they all know what they do all the time clicking on this funny "Click here to proof you're a spambot" image.
If it gets annoying with an IP scanning for /phpMyAdmin for some days, manually put it into the blocklist (of your Firewall box), take the logs and inform the ISP / Hoster.

And related to the argument some OS already have a firewall included, because it's there it doesn't mean it needs to make sense. The Linux kernel had a webserver included in the kernel for some versions ;)
It all depends on the usage and more specific how to use, not using it because it's already built-in.

---

### Post by psusi on 2011-02-11
By definition a firewall blocks access to some service that otherwise would be accepting connections.  If you don't install any services, then there is nothing for a firewall to block access to.  If you do install services, then you probably WANT it to accept connections, so you don't want to firewall.  If you don't want the service accepting connections, then either don't install it, or configure it to only accept connections from the local network, or authenticated clients.

A firewall is considered a requirement for Windows because it comes with several insecure services installed by default that will allow anyone access to your machine.  Linux distributions do not suffer from such brokenness.

The only reason to use iptables is if your machine is acting as a router and you want to protect the windows machines behind you, or you want to restrict the outgoing traffic from those machines.

---

### Post by lisati on 2011-02-11
I like this discussion, and want to encourage people not to get put off by the various suggestions offered.

It seems to me that there's a balancing act involved: what you are prepared to deliberately open up, and what screening process to use to keep out the rogues who will take advantage of what you open up. 

My own $0.02: worthy of mention is the mod_defensible add-on for Apache. It's a DNSBL-based screening system to help avoid blog spam.

---

### Post by elico on 2011-02-11
well, how paranoid am i?
one of the basics of IT security is "what you dont need dont install"
so indeed if there is no service working on the machine that will listen on specific port for connection than no one will answer to the "phone ring"
indeed windows has services that without firewall could be compromised.
so the question now is "windows or linux?"
but it's not the question.
the question is that: i have a machine, what should i do with it? should i give anyone who wants access to the machine?
should i use syn cookies blocking?

IT security remains the same for windows and linux.
so im asking: what is system hardening?
a local firewall counts as system hardening?

if you have couple of services such as http mail and ssh you should harden the specific services with any mean you need.

out of the box linux systems and many servers application are harden and the most common security holes are "HUMENS" or humen miscalculations.

if you do have the firewall running and out of the box with installation of the OS,
the first thing to do is to understand that your system is an advanced system that the people that designed the OS took many things while packing it and made sure that in the installation you choose to only open access to specific services.
so why you ask? 
i say : if you do ask it then it means you have a doubt about your knowledge what a firewall is and you should just put your server wide open to the world with static internet IP without firewall and check the results for 60-90 days.
if you dont have any problems and the server is performing well you almost got it.

just to understand it you must know that it's very good that you asked the question cause the one that will shut eventually will find the machine in a long sleep state :)

and i have a nice "server" story for you.
i have a nice friend that works in a big IT company and they tested a new machine out of the box.
so the question was "in the company network under firewall or out of it?"
so they started the server that has  only 4 services such ssh http mail and ftp.
after 3 weeks the server was online the head of IT comes to my friend with an order to get now into the company servers room and to unplug the network cable form the machine.
it appears that the server was compromised and the network usage was so high that 100MB internet download speed was the downside of it.

so what do you think?

recommend to anyone just to look on a very good site:
[https://calomel.org/](https://calomel.org/)  (not mine)

---

### Post by garfonzo on 2011-02-11
> **elico said:**
> i say : if you do ask it then it means you have a doubt about your knowledge what a firewall is and you should just put your server wide open to the world with static internet IP without firewall and check the results for 60-90 days. I question my knowledge about everything I claim to understand so I can always learn new things.

Thanks for the input (seriously) as it has caused me to think about my setup from yet another angle. 

Good discussion.

---

### Post by rudelgurke on 2011-02-12
> **elico said:**
> so they started the server that has  only 4 services such ssh http mail and ftp.
...
it appears that the server was compromised and the network usage was so high that 100MB internet download speed was the downside of it.

And how could a firewall protect such a machine in this case ? They provided services and if the machine was compromised, the services were unsecure because the bot / backdoor ... whatever - had to be placed somehow on the comp.
And I'm sure they would have blocked the 4 services and made them available to public.
My point is that a firewall can't protect (by design) against SQL injections, XSS and similar attacks.
That must be done on the application level.
And, if you decide to do outbound blocking, well - if your logs alert you about a hidden process trying to contact a weird server then it's already too late because the other levels of security failed.
Just saying to first focus on the services e.g. MySQL listening only on 127.0.0.1, not installing phpMyAdmin on / or even not installing it at all, etc. etc.
Then a firewall can still be placed in front of the machine.

---

### Post by elico on 2011-02-12
i indeed voting for application level hardening!!
phpmyadmin can be a remote sql machine management tool and there are many tools just for this purpose.
a firewall is a network level security level by definition.
some later mods were added to allow a more sophisticated app level into the firewall.

i know my servers and services and i do need to allow access from some remote places so im using a strict  ip blocking list.
only white-list IPs are allowed to my services.
also you can add a vpn\ipsec\ssh remote access and using them to access local applications.
almost always is a good thing to change the default ports of services on the internet work to other ports
such as 10000 of webmin to 6533
or 22 to 11112
and it's not a defensive mechanized against port scanning but it helps detect it so a firewall can detect DOS and port scanning before the attacker gets to the application it self.

if you do have production server on the internet and it worth money a firewall is a very good way to make sure that you can sleep at night and to find in the morning that you do know about port scanning or some other things.

but it's just the network layer.

most of the servers i know that are on production and national usage have a dedicated Firewall proxy and IDS system that are working directly one with the other.
you can try to look at this nice diagram:
[http://www.kernel-panic.it/openbsd/carp/net.png](http://www.kernel-panic.it/openbsd/carp/net.png)

---

### Post by hawkmage on 2011-02-12
I have worked in IT for over 20 years and the idea of what is secure or the best way to secure things has changed with the top perceived threats.  

There are benefits and drawback to host and appliance based firewalls.  

Host based firewalls have the great benefit of blocking/allowing exactly what you want for the individual host it is on but it quickly becomes a maintenance nightmare as you do this on more and more hosts.  

Appliance based firewalls are great for control access to large networks/zones and are more easily managed from a central location but does little to protect hosts on a network from other hosts on that network.  

A combination of these is probably the best approach, no single technology covers everything.  

There are a couple of things you should keep in mind.  

[LIST]
[*]First is something that applies any kind of security, do not spend any more on security that what you are protecting.
[*]Second any time you allow a connection through a firewall you are opening up a place for the hackers to attack.
[*]This brings me to  my third point, applications need to be hardened.
[/LIST]
Personally I may be a bit paranoid, my home network has multiple firewalled VLANs for VOIP, Storage, Wireless, DMZ and internal.  Not only do I limit the access between the VLANs but I also use host based firewalls like iptables, ipfw, pf or ipf.

---

