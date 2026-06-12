---
title: "Need advice on a good DNS/DHCP solution"
date: 2009-04-08
forum: Server Platforms
---

### Post by lykwydchykyn on 2009-04-08
Here's the scenario:
Our network admin wants to set up individual DNS servers at each location in our WAN to reduce WAN traffic back to the main server room.  The idea is also to have dynamic DNS updates with DHCP.  Right now DHCP is handled by the (Cisco) routers, but that can potentially be changed.

The network admin like Windows DNS because the interface is easy.  But we can't afford a copy of Windows Server for every location, so me being the "Linux guy" piped up and said I might be able to come up with an open source solution.

I've worked with dhcp3-server and bind9 before, but I am a complete failure at getting them to sync up no matter how many howtos I try.  I always end up with mysterious errors and break bind whenever I try.

Now, here's the thing:  *I* have the patience and Linux experience to slog through this and maybe eventually make it work.  But my coworkers are not going to dig it if it takes monkeying around in the console.

So can anyone point me to a complete solution that involves:
 - A GUI or web interface
 - Dynamic DNS
 - Quick'n'easy setup?

I've tried ebox, and it didn't seem to have a ddns setup.  Couldn't get webmin's to work.  Tried various CLI methods and couldn't get it to work.

Please note: I'm not asking for help troubleshooting these setups (yet).  I'm just wondering what other people use that is known to work and work well without a lot of tinkering.  If it's something I've already tried, then I may pick your brain about how you got it to work and what errors I've gotten.

---

### Post by koenn on 2009-04-08
How about this:

you set up dnsmasq servers at each Location. You let it do dhcp for the hosts on that segment. Its dns server will automatically be aware of the address-name pairs of leases the dhcp gives out, if the dhcp clients send their hostnames with the dhcp request. Windows does that.

you can let the dnsmasq use your headquarter dns as forwarder, so it will handle and cache queries for hosts not on their segment.

If the HQ DNS also needs to be aware of hostnames on remote segments, you'll need to arrange zone transfers, I don't know how dnsmasq handles that, but from your OP I can't tell that this is actually required.

managing dnsmasq (after it's been set up) is as simple as editing a hosts file. Literally. If your colleagues need a GUI for that, hm ... problem.

As for the initial setup, you could probably just make a master dnsmasq.conf and scp or rsync it any place you want - the power of unix will shield your GUI-dependent admins of actually having to do anything.

---

### Post by lykwydchykyn on 2009-04-08
> **koenn said:**
> 
If the HQ DNS also needs to be aware of hostnames on remote segments, you'll need to arrange zone transfers, I don't know how dnsmasq handles that, but from your OP I can't tell that this is actually required.

It would definitely seal the deal, but I wasn't sure if it was actually possible.
> 
managing dnsmasq (after it's been set up) is as simple as editing a hosts file. Literally. If your colleagues need a GUI for that, hm ... problem.

I use it at home, but only for DNS caching.  I've never tried it for DHCP/ddns.  I thought about it as a fallback, but the lack of a GUI is going to be a hard sell on them.
> 
As for the initial setup, you could probably just make a master dnsmasq.conf and scp or rsync it any place you want - the power of unix will shield your GUI-dependent admins of actually having to do anything.

Not a bad idea.  I may have to pick the NA's brain some more to see what kind of inter-updating he wants going on.

---

### Post by koenn on 2009-04-08
> **lykwydchykyn said:**
>  ... but the lack of a GUI is going to be a hard sell on them.
I understand, kind of. On the other hand, in Windows DNS, you rightclick, 'Add New Host' and you still have to actually *** type a hostname and an IP address***. I guess doing this in a dialog box in stead of a text file makes all the difference to some people.

Maybe you can write wrapper around this with zenity or something web (php, ...)


> **lykwydchykyn said:**
> It would definitely seal the deal, but I wasn't sure if it was actually possible.
...
Not a bad idea.  I may have to pick the NA's brain some more to see what kind of inter-updating he wants going on.

I thought scp or rsync your conf would be a good way to avoid having windows admins setup something on linux, but come to think of it ...

dnsmasq uses its hosts /etc/hosts file as a dns zone file (combined with its dhcp leases file), but it could be configured to use additional files as well. If zone transfers don't work out, you might be able to work something out with scheduled copying of files among all servers, or a central deposit exported through NFS, where every dnsmasq updates its own files but can read the others. 
Just thinking out loud ...

---

### Post by lykwydchykyn on 2009-04-08
> **koenn said:**
> I understand, kind of. On the other hand, in Windows DNS, you rightclick, 'Add New Host' and you still have to actually *** type a hostname and an IP address***. I guess doing this in a dialog box in stead of a text file makes all the difference to some people.

Maybe you can write wrapper around this with zenity or something web (php, ...)

Webmin actually provides for this pretty well, as does YAST on Suse (which they like, since they are long-time Novell fans).  It's not adding records that's a problem, it's the trickier stuff -- setting up replication, adding subdomains, etc.  I'd be lying if I said this stuff (the intricacies of DNS, that is) wasn't a bit over my head, though I'm slowly getting a grasp of it.

---

### Post by koenn on 2009-04-08
> **lykwydchykyn said:**
>  It's not adding records that's a problem, it's the trickier stuff -- setting up replication, adding subdomains, etc.  I'd be lying if I said this stuff (the intricacies of DNS, that is) wasn't a bit over my head, though I'm slowly getting a grasp of it.

Yes, but wouldn't this be managed at your present HQ DNS, which I presume is a Windows server. The remote DNS servers would simple query this server and cache te results, plus handle resolution of their local LAN, so that's where you save bandwidth - and it's better than what you have now cause now ALL dns goes to HQ. 

If you're going for full blown replication all  over the place, I am not sure a simple tool like dnsmasq can handle it, but I looked at man dnsmasq and apparently, in stead of zone transfers, you can configure forwarders by domain/network range, so it looks like you could have all dnsmasq servers point to all others for the specific range they cover. So you could probably cover the entire network, WAN included, and count on the dns cache to keep traffic reasonable. After all, replication between real (MS or Bind) DNS servers would also cause traffic over your WAN lines

I haven't done this, so you'd have to investigate yourself, unless someone comes up with a working solution for easy configurable dynamic updated bind9 with a gui.

You could also ask your NA why he think it's the dns traffic that's putting a strain on the WAN connections  - a dns query/reply is just a few bits ....

---

