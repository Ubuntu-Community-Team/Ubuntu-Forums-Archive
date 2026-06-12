---
title: "Need quick DHCP server/bind/windows client advice"
date: 2006-10-01
forum: Server Platforms
---

### Post by wgaprotest on 2006-10-01
Ok, I had a static IP for my new lamp server, it and son's pc (xp with wireless card) were both behind a dlink router in a p2p config, with samba, of course. So the chain was cable modem-router-xp desktop/ubuntu server.

Now, for various reasons, I'm trying to change this to a diagram like I've tried to attache here (and failed), so there are numbered points below  instead. I am quite confused about where bind comes in, and why my dhcp server isn't working out that well. My intial foray was to follow the howto in the ubuntu server guide, and it seemed to work, but webmin gave me the error that command shell didn't, and then it seemed the dhcp server was on eth0 AND eth1, preventing me from surfing for more howtos even before I could get my son's pc online as a host. Anyway, I'm sure I can retrace my steps in getting the static IP, but I really do need some help in making sure I'm not missing something, where bind comes into play (bind server's not installed yet) and the right steps in the right order. Then there's the proxy...but I think I can do a transparent proxy through iptables in my firewall. At which stage, tho? I've also got the Linux bible here that I'm using for documentation, but the different parts of all this is very confusing.

I know: I'm not asking for much, right? If I could get some help from various people on different parts of this project I'd really appreciate it. .

Anyway, here's what I want ASAP, the semi-end goal, and I'm sure my son will complain very vocally if I don't get him online again in the next 24 hrs, as he's already been offline now for 2 days due to the server needing a trip to the shop (builder and I thought mobo was dead):

1. cable modem (connected via eth0 on Ubuntu Lamp Server (serving DHCP addresses for 2 clients
2. above server's eth1 chained to router/Acess point, used as simple switch
3. above r/ap split to support 2 machines, (1, son's xp desktop; 2, an old PII box, running as print and file server (files include backups, other storage on 20G hdd, Linux distro still TBD - advice? (only has 128MB ram, old bios)
4. print server on PII, obviously connected to a printer, which is a brother mfc210C, and would therefore be better suited to a i386 architecture than current setup on ubuntu server (running kubuntu desktop on top of ubuntu; dapper, amd64)

No, I wasn't able to connect the PII to the cable modem for it to protect the ubuntu server. and I tried doing a gentoo minimal-install on the PII for firewall & other purposes, but the installation hung on mounting the cdrom drive, and it's really last on my priorities. 

After I get my son's pc online my next priority is getting the ivtv drivers setup, as this high-end system (now the ubuntu server) was always intended to be  aa home theatre pc, and my windows xp media center edition installation became toasted with the mobo probs (probably caused them) AND the first install disk is now physically cracked. So fixing that will have to wait until I can get replacement media. 

So I hope you can see why I need help fast? If I can get it all set in the next 2-3 days (wishful thinking?) I'll be one happy camper. Heck, maybe the mobo probs and the resulting windows/installation disks hell will have provided the added impetus to speed my migration along.

Thanks in advance for any help or support.

---

### Post by Iowan on 2006-10-01
Since on one else has jumped in yet, I may as well at least bump the post up.   I'm certainly no expert (and probably dead-wrong)... but we'll see.

The LAMP server is being used as a router?  It is located between the modem and the other boxes?  It may need router-type software installed. The router might be able to serve this purpose just as well - besides acting as a hub.

BIND is a DNS server - again, the router *might* have DNS built in.
DHCP... well, the router again - although I have a separate server handling DHCP (I'd prefer to have my router/firewall route/firewall only... but non-router DNS is proving problematic).

Perhaps a more knowledgeable guru will advise otherwise, but to my untrained eye, it would seem like the modem should connect to the router which would connect to the XP box, the PII, and the server (which could also serve as print/file  AND DHCP server)

---

### Post by wgaprotest on 2006-10-02
Hi Iowan,

thanks for your reply. I'll put a quick update towards the end of this post with some good news, but for now I'd like to answer your comments:
> The LAMP server is being used as a router? It is located between the modem and the other boxes? It may need router-type software installed

That's a key purpose of most servers, including a lamp: to route traffic between machines. And even a ubuntu desktop has routing already installed in the network part of the settings - you just don't need to be as aware of it as with a true server. 

> it would seem like the modem should connect to the router which would connect to the XP box, the PII, and the server (which could also serve as print/file AND DHCP server

This topology you desribe, or diagram, is what I originally had set up (minus the PII), but the new topology I'm trying to configure is actually a fairly standard one found in most of the books and other documentation. (not quite a DMZ, but halfway there) My reasons for wanting the new topology (cable modem-ubuntu  server- hub/switch-XP & PII) are:

1) my son does a number of fairly unsafe things on his xp box, and I get totally tired of the full-time job it's become just to keep 2 windows pc's secure and patched, when *none* of the anti-virus, anti-spyware, and registry cleaners, patches (including bad ms updates) etc. will catch everything. Every single one of these have to be updated almost every single day, and with a linux server hiding everything (just one firewall to worry about), it's less likely to be a target. And the security suites for windows are always screwing up other applications...You'd think an 18-yr-old would bother to defrag or something once a year at least, but noooooooo; "there's nothing in the world lazier than a teenage boy." Then he complains when it's not working optimally.
2) yes, I'm still in the process of migrating away from windows for this htpc, but even when I will get back to the windows for brief periods when I really have to, it'll be easier to maintain one machine, still keeping his hidden.
3) the router by itself was doing very little to protect us, we've had it for 2 years, and the main reason we have it is as the wireless access point.
4) Remember I tried to use the PII as a router/firewall while the server was in the shop overnight, and was having trouble installing a linux distro cause of the very old hardware. Besides, it's so old (gotta be 10 yrs; my son wasn't even a teen when we got it used) I don't consider it reliable as a working system -- except for the hdd. So it's ok for a print server that could be quickly re-located if necessary, and for storage of files...I can always move the hdd elsewhere again.

As far as the Bind is concerned, I was looking over my lamp documentation I used to set it up, cause bind did sound familiar, and yes, I had to install it for the lamp. It's just v. 8 though, and that's why webmin confused me when it said a bind server wasn't installed. Webmin meant v. 10.

Now for the update:
I just got my dhcp server working! Woohoo! It took almost 2 days, and my son's asleep so I can't reboot his pc to really test how it's working, but there were plenty of error messages from webmin during all my trial-and-error, but none now. I've even rebooted, and everything's still fine on both the wan-eth0 and the local-lan-eth1 (where the dhcpd server is). 

Now to perfect my firewall...It's up, and minimal, but iptables rules exist...:-)

Cheers!

---

