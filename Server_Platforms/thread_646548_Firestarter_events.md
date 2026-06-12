---
title: "Firestarter events"
date: 2007-12-21
forum: Server Platforms
---

### Post by niethslim on 2007-12-21
I recently started getting lots of events on my Firestarter (see attached image).
What does that mean? Why is it happening? What should I do?
If you need any system/network information, please ask.


Thanks,
niethslim

---

### Post by FakeOutdoorsman on 2007-12-21
Looks like you're running bittorrent, which I believe uses TCP.  The list looks like a bunch of torrent peers.

---

### Post by niethslim on 2007-12-21
Thanks for the reply FakeOutdoorsman. I am running Bittorrent and you are probably  right.
I still don't understand why only some of the processes get blocked or why at times there are no events at all and at times there is a new event every minute or so. 


niethslim

---

### Post by FakeOutdoorsman on 2007-12-21
I'm not familiar with Firestarter, but you may need to tell your bittorrent client which ports to use, and then allow those ports to be open for TCP in Firestarter.

---

### Post by niethslim on 2007-12-21
My Bittorrent client (Deluge) is running on default setting with the ports set to 6881-6889.
Firestarter allows some of the ports that it recognizes as Bittorrent (6881-6889) and some of the other ports, too.
I'm not sure that the other ports are related to the Bittorrent ports.
I don't recognize many of the allowed services, they weren't there before.
Here are some of them, maybe someone would be able to tell me what they are:
Afs3-fileserver, SUN-RPC portmap, Back orifice 2K, Subseven, Gnutella (isn't it some kind of Kazaa protocol?!),
 eDonkey (I have aMule installed, but I haven't used it in this session), SIP over TLC, webadmin and traceroute.
After looking at this list it sure doesn't seem as if Deluge is causing all this by itself.
Another problem is that Firestarter started crashing frequently.

Any help will be appreciated,
niethslim

---

### Post by santaslittlehelper on 2007-12-21
I think firestarter got some issues, crashing is a known one, don't know if there's any fix.
[https://bugs.launchpad.net/firestarter/+bug/120445](https://bugs.launchpad.net/firestarter/+bug/120445)

Do deluge have DHT - [http://en.wikipedia.org/wiki/Distributed_hash_table](http://en.wikipedia.org/wiki/Distributed_hash_table) - as I think it might bring some traffic you're way that you didn't ask for, that you can either en/or disable. Might help but not sure at all.
Maybe it's just one of those things that comes with bittorrent.

---

### Post by niethslim on 2007-12-22
Thanks for the reply santaslittlehelper.
Deluge has Mainline DHT enabled. Should I disable it?
What will be the effect on download speed?


niethslim

---

### Post by santaslittlehelper on 2007-12-23
Hi, I can't really tell you, it was more of a suggestion to try out.

---

### Post by perixx on 2008-01-13
> Back orifice 2K, Subseven

Anybody please correct me if I'm wrong, but aren't those VIRUSSES (Trojans)??

perixx

---

### Post by niethslim on 2008-01-13
Yes, but as far as I understand they don't exist for Linux.
Firestarter determines the service by looking at the port it uses, and bittorrent just happens to use the ports those viruses use on Windows machines.

---

### Post by perixx on 2008-01-15
Yes I thought so :] 
So the ports in question are only opened when you start bittorrent?

perixx

---

### Post by brunolabs on 2008-01-15
I have a lot o serious events, like 1 per minute.

They mostly indicate:

Service: Microsoft-ds   and   DCOM-scm
Protocol: TCP


What should I do?

Thanks.

---

### Post by niethslim on 2008-01-15
> **perixx said:**
> Yes I thought so :] 
So the ports in question are only opened when you start bittorrent?

perixx

Yes.

---

### Post by thomasyen on 2008-01-16
Hello,

I have (I think) a much more serious problem. My Firestarter is getting a hit every few seconds, and I don't have any type of file-sharing running. Can anyone help me out? Thanks.

---

### Post by perixx on 2008-01-16
Hy thomasyen...

I was worrying about those events you mentioned before as well. But then I realized how Firestarter actually works; as long as events are reported, this means, they're BLOCKED. The list printed is only showing events that are denied! 

In rejective mode, you have to particularly specify which events you allow - so you already know of them - all other's are blocked by default. Apart from that - I wonder if most of those MS-services were relevant for us Linuxer's anyway. If you don't use Samba filesharing, I doubt you have to be afraid of such events for instance.... I'm not perfectly sure, of course.

Btw., why don't you enable IN/OUT column in your list? I'm suspecting you're running bittorrent or some in-game server maybe (or a bittorrent client is trying to connect to you)... oh, and does anybody know what the 'gam_server' in the tasklist exactly is?

But generally, if you use Linux in non-admin-mode, without a server...? I have, though, deactivated the automatic network-service 'avahi' - if I'm not mistaken, that poses some similar thing like UPnP under XP. Someone please correct me if I'm wrong!

perixx

---

### Post by thomasyen on 2008-01-17
Hello Perixx,
I later realized that I had restarted my computer after a Windows session (I use a dual-boot machine), which had BitTorrent running by default in Windows. Perhaps the other machines in the swarm did not get the message that I wasn't sharing files any more (I don't have Deluge enabled by default in Linux), and they were still trying to connect to me. I also noticed that the ports Firestarter was blocking were the ports BitTorrent used in Windows mode. After I booted directly into Linux, I no longer have these problems. Thank you for your time, though!

---

