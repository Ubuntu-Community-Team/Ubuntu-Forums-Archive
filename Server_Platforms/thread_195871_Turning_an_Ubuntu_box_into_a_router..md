---
title: "Turning an Ubuntu box into a router."
date: 2006-06-13
forum: Server Platforms
---

### Post by spindrift on 2006-06-13
I normally only lurk on forums, but since (for once) Google and forum search have been unhelpful, here goes...

I've recently gained access to an old PIII/766mHz running Windows 98 that's simply screaming to be transformed into a sturdy Linux server.  The thing is, since it came with a Hauppage TV tuner, I'm looking to turn it into both a router/firewall/wireless AP (using a Linksys WRT54GX2 in switch mode) **AND** a MythTV backend.  I'll later be using a modded Xbox for a livingroom frontend.

Now, I know about KnoppMyth for the MythTV portion and m0n0wall/pfsense/Coyote for the router and firewall bit, but AFAIK each of those are single-purpose distros.  I've recently fallen in love with *Ubuntu (I use Kubuntu as my primary OS now) and wanted the extra functionality that an actual distro like Xubuntu or Ubuntu-Lite would provide.

To head off other questions, I'm not just using the Linksys router because I've noticed some inexplicable DDoS attacks in its logs that have been dropping my connection like a prizefighter, and I see no reason to spring for a hardware firewall when a better solution is within reach for the price of an additional ethernet card.

So I guess my real questions are,

1) Is *Ubuntu a suitable solution for this sort of project?  I've heard of FreeBSD's amazing performance, and I previously compiled a Gentoo system (but was unimpressed).  Just not sure if there are any distro/kernel-specific traits that would inherently limit bandwidth throughput in any way, whether between *Ubuntu/Linux and *BSD, or a general vs. specialized distro like m0n0wall.

2) Is there any *nix software that would be well suited for this (without being a specialized distro solution), or are we just talking kernel-based stuff like configuring a DHCP server and IPtables?

3) Would there be any possible way (AFAYK, I know this is the wrong forum) to install MythTV on something like Coyote?  I could give up the infinite functionality for perfect dual-functionality if needed.

I'm not looking for hand-holding or howtos, just a kick in the right direction and some good advice.  I love RTMFing, Google, and I'm only technically a l00nix n00b (I've taken to it like a fish to water).

Thanks, and sorry for the long post.

---

### Post by mscman on 2006-06-13
For router/firewall use, you can use firestarter.  That's what we use in my lab at school.  This shouldn't limit any bandwidth usage as far as I've experienced (we get 10MB/sec down in the lab).  I'm not sure how installing MythTV software (or any software for that matter) on firewall/router distros would go, since they're usually VERY barebones.

---

### Post by spindrift on 2006-06-13
Wow, that actually looks just about perfect, thanks.  So I guess it can run on any distro with equal throughput?  Looks like I'd be able to setup a lightweight Xubuntu server, then run Firestarter and MythTV as standalone programs.

Doing a little bit more research I just found ClarkConnect router/firewall, which apparently can host a MythTV backend, but CC itself looks too corporate and conglomerated (anything that comes in various 'feature levels' makes me cringe).

---

### Post by tomski on 2006-06-13
Hi there
i have done exactly this (ubuntu/router)
all i did was a fresh install of ubuntu & at the boot prompt i typed 'server'
(for the server install)
then i run:
apt-get install webmin webmin-shorewall open-ssh
that would then pull everything in needed except for a few others i cant remember.
on the hardware level this box is:
Dell optiplex Desktop
p3 ???mhz
128mb ram
50gb excelstore hd (ata100)
cd drive
floppy
2 realtec nic's
eth0 wan (dhcp client) (shorewall = net)
eth1 lan 192.168.1.0 (shorewall = loc)

i should let you know that this does have a desktop but only accessable via vnc on the lan interface (just for emergencies)
a majority of admin i do via ssh or webmin
i use notp or darkstats for realtime status other than that i tend to only install what i need so then i can share a partition as /public via nfs for my mp3's i can then access these via linux & windows xp (using services for unix) as a network share.

if you like i'll upload my shorewall configs for you to use as a base to start from

---

### Post by tsumi on 2006-06-13
i would like to see those configs please.

Edit: apt-get install webmin does not fly, do i need to edit the sources for apt-get?

Editx2: yeah, its in universe

---

### Post by mscman on 2006-06-15
[QUOTE=spindrift]Doing a little bit more research I just found ClarkConnect router/firewall, which apparently can host a MythTV backend, but CC itself looks too corporate and conglomerated (anything that comes in various 'feature levels' makes me cringe).[/QUOTE]
While I lack an extra machine to test ClarkConnect on, a local GeekSquad Agent (don't worry, we were just talking...) told me he loves ClarkConnect, and proceeded to show me his home setup.  I must say, I was impressed, and if I had a spare machine to turn into a router, I would probably use ClarkConnect.  That being said, I'm not sure as to the firewall security of ClarkConnect.  I would venture to guess that it uses IPtables just like Ubuntu, but I can't really say for sure.  Let me know what you decide to do, I'd like to hear your results! :D

---

### Post by spindrift on 2006-06-15
Hahah - that's funny, I'm a GeekSquad Agent too. :P

I was doing some research on the feasibility of running MythTV on a CC gateway box, and I've seen some mixed results.  I'd rather run a specifically slimmed-down distro like Xubuntu, install Firestarter and MythTV seperately, and see if the box can handle the load.  As a bonus, I'd have something that could kick the crap out of the Win98 that the box was previously running.

I'm just about to start the Xubuntu installation, so we'll see how that goes.  I tried comparing it with the VectorLinux LiveCD, and somehow I still like Xubuntu better.  I'll keep posted with the success/failure of the project.

---

### Post by dccool879 on 2006-07-08
> **spindrift said:**
> (using a Linksys WRT54GX2 in switch mode)

how did you turn your linksys in switch mode? can i do it in its configuration? thanks

---

### Post by dccool879 on 2006-07-08
> **tsumi said:**
> i would like to see those configs please.

Edit: apt-get install webmin does not fly, do i need to edit the sources for apt-get?

Editx2: yeah, its in universe

This might help you [http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html](http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html)

---

