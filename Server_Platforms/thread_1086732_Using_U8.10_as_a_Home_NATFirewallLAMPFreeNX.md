---
title: "Using U8.10 as a Home NAT/Firewall/LAMP/FreeNX"
date: 2009-03-04
forum: Server Platforms
---

### Post by KamakazieX on 2009-03-04
Hey everyone. I am going to run an 8.10 2U server with a SuperMicro 6022P-6 on SL79V's (2x 3Ghz Netburst /w 4Mb L3) with 4x 36gb Cheetah U320 drives in RAID5 on an Adaptec 2010S (/ and 3Gb-swap), and a 750Gb SATA-II on a Syba SD-PCXSA2-2E2R hot swap (/store). I used to have an old tower running clarkconnect but I want to run much more now.- But it offered everything I wanted out of the box, it just wasn't debian based. I also want to be able to FreeNX and use it as a workstation. I was looking for some insight before actually building the box to know what road blocks and limitations I may see when using this for the following.

Firewall *ipchains or better? I would prefer an active intrusion prevention system with a ruleset. Suggestions? (web interface?)
NAT for home - (web interface?)
LAMP* - TorrentFlux
Squid | DansGuardian
dnsmasq or some other/better dns caching?
OpenSSH - Security repercussions of it web-facing?
FreeNX (does X have to be running on the box or does the service just need to be installed?)

I am going to pull my stack of chained switches and wireless router (Finally! :D ) and replace it with a single gigabit switch and N access point.

---

### Post by matey3 on 2009-03-04
I dont know? I am not an expert at all but good luck trying it with SATA disks. I think may be you wont have any problems with Adaptec as I did with 3Wire raid/controller.
Any way we use Zope and Plone for web and security.
I know very little about zope but have installed diff. versions like 2.8/9 and 3.0,
I could may be give you a tip or 2 in zope installation , but thats about it..
good luck!

---

