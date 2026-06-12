---
title: "Power saving options"
date: 2008-05-04
forum: Server Platforms
---

### Post by Benedict on 2008-05-04
Hello All,

I'm trying to figure out the best power saving options for my ubuntu server. 

The server is used infrequently but I need it on all the time. I've experimented with Wake On Lan, but it doesn't do exactly what I need. The problem with WOL is that I may not be accessing the server from a PC that can send the WOL packet. 

What I need is for the server to power down after an arbitrary length of inactivity, but to wake up when network traffic is sent to the server. Is this possible?

Cheers
Benedict

---

### Post by MJN on 2008-05-04
<Ignore this post - I gave some duff info>

---

### Post by c128 on 2008-06-12
I'd be interested in any responses to this thread too...

At the moment I'm using Windows XP as my server OS, although I'd like to move to Ubuntu.  In a nut-shell my server is currently configured to power-down the hard-disks after 10 minutes of activity and then go into S3 after 25 minutes of activity.  However, it's also set to wake-up from S3 if any LAN traffic is directed at its IP address - I have an Intel onboard NIC and they term this "Wake on Directed Packet", which basically means "wake up from S3 when accessed".  This works really, really well - I have various shares on my server with clients mapped to them and, when a client accesses a share (e.g. "Documents" folder from an XP lap-top, my mp3 collection from Vista Media Center) if the server is asleep then it wakes up.  Note: as per the OP, this is distinct from Wake on LAN, which is essentially a manual process - the wake from S3 occurs automatically based on LAN traffic.

So: is "Wake on Directed Packet" something supported with Ubuntu server?

---

### Post by molotov00 on 2008-06-12
Is there a computer on your network that is always on and that can send a WOL packet? Or, are there several computers that can send a WOL packet and any of which will always be on?

I have a couple computers so in your situation I'd write a script that could send the packet (and put that script on the WOL-packet-sending computers). Then, if I needed to access the server from outside the network I could connect to the computer with the script, send the packet, then connect to the server. It sounds a little tricky but really it adds no steps to the user. In both cases they are sending an instruction to boot the computer. You could use SSH, HTTP, or even telnet. It doesn't have to be secure, if all your doing is starting a script to send a packet.

I've never done it... but that's what makes sense to me.

---

### Post by c128 on 2008-06-12
I guess my take on this is that I want my server's shares accessible *as if* it were on all of the time - access needs to be totally transparent to the end user e.g. opening up a document from the recent documents list on Word's "File" menu fires up the server (if need be) because that's where the document is stored.  This only really works, for all client situations, if either (a) the server _is _actually on all of the time or (b) the "Wake on Directed Packet"/"Wake on Network Activity" is used, so it wakes automagically when accessed.  I can't see how you can really mimic this with WOL and magic packets, and get the same transparent operation, but I might be misunderstanding your point :).  Option (a) would work, but is too espensive, and option (b) works a treat on Windows XP, as I'm using it now, so I'm wondering whether the same is possible with Ubuntu.

---

### Post by c128 on 2008-06-14
Been doing a bit of wattage calculation, and my machine draws about 70W in normal use and around 55W with the disks spun-down...  Still more than I'd want on all of the time, and I think enough to stop me moving from Xp->Linux...

With that in mind, is anyone making use of selective wake from S3 on network activity for their home server/datastore use, or are folk mostly "always on"/manually kick-starting based on a WOL magic packet?

---

### Post by c128 on 2008-06-17
No-one with any experience of "Wake on Directed Packet" and/or "Wake on Network Activity"?

I've resorted to dropping Intel support a few words to see if they've any information on configuring this sort of functionality in their onboard NICs on Linux...

---

### Post by windependence on 2008-06-17
Frankly I don't know why you want to do this. I have a rack with 5 servers here and they are on 24/7/365, and don't take that much money to run. One is a dual processor system and another is also a dual quad core system. Two of them have 500W redundant power supplies, and I run dual 1500va UPS boxes. I am running many more servers on this hardware through the use of virtual machines. IMHO, this is the way to go to save power. If you only have one or two servers, it isn't worth going to the trouble anyway. 

To acheive 'transparent' to the user power down I think is impossible. It still takes time to wake up a machine. The fans still have to run, so what are you saving, the harddrives? That's not much. You would be better off setting up one very powerful box and running 5 or more VMs on it. Of course, YMMV.

-Tim

---

### Post by c128 on 2008-06-17
> **windependence said:**
> To acheive 'transparent' to the user power down I think is impossible. It still takes time to wake up a machine.

Impossible?  mmm...then I have an impossible XP-based setup working for the last year or so:). For me, it's perfect.  The longest delay I have in wake-up is around 5-7 seconds when the machine *first *wakes from S3, and most of the time it's quicker as it won't have gone fully to sleep but has just spun down the disks.  Yes, it really does work transparently!

> **windependence said:**
> The fans still have to run, so what are you saving, the harddrives? That's not much. You would be better off setting up one very powerful box and running 5 or more VMs on it. Of course, YMMV.

In S3, whilst wating for network activity, the machine uses ~6W.  As above, that's versus 55W when idling.  So that's a saving of 49W, and not to be sniffed at in my book...

So..."Wake on Directed Packet" is a function of the NIC, I suppose.  Is this something configurable for Intel NIC drivers on Linux, or is Linux lacking in this respect?  I guess I had thought that if there was something "tweakable", then it would be available in the Linux world...

---

### Post by c128 on 2008-06-17
mmm...well, predictable response from Intel about the onboard NIC of my motherboard:

*In regards to your situation, Linux* is not a supported Operating system for the Intel(R) Desktop Board DG965WH. Please review the following list for supported Operating systems for your Desktop Board.*

---

### Post by windependence on 2008-06-17
Yes, isn't that shameful? That's one of the reasons I am an AMD Solution Provider. I guess Intel gets too much business from Micro$oft.

-Tim

---

### Post by c128 on 2008-06-18
I was actually a bit surprised by this, as I had originally thought that Intel was reasonably helpful to the open source community e.g.  supporting drivers for its onboard graphics solutions?  Obviously not if that's just their blanket response :(.

Does anyone know if there are specific linux drivers/utilities for Intel NICs that give you access to the "tweakable" options that are available in the Windows Device Manager?  I'm guessing there must be some way of getting "Wake on Directed Packet" working on Linux?

---

### Post by windependence on 2008-06-18
Looks like short of writing your own code, this is pretty much a Windoze thing from what I can google.

The other thing you need to find out is how much power does the system consume running Linux vs Windoze? How are you measuring power consumption BTW? Have you considered virtualization, or is this the only box you have? Also, passive heat sinks would help, fans are power consumers.

-Tim

---

### Post by c128 on 2008-06-20
> **windependence said:**
> Looks like short of writing your own code, this is pretty much a Windoze thing from what I can google.

Does seem that way, doesn't it :(

> **windependence said:**
> The other thing you need to find out is how much power does the system consume running Linux vs Windoze?

That's a good point, but I'm rather "wed" to the 6W that the machine consumes whilst in S3.  That I can live with, as it's basically next to nothing, and I guess there's no Linux-based machine out there that's going to come close to this when just idling rather than suspended, even if it does run a bit less "hungry" when properly going.

> **windependence said:**
> How are you measuring power consumption BTW?

Plug-in power monitor that sits between the mains plug and socket.  I'm assuming its reasonably accurate...or at least a decent indicator.

> **windependence said:**
> Have you considered virtualization, or is this the only box you have? Also, passive heat sinks would help, fans are power consumers.

It's my only machine - more just a file-server sitting in my loft, really.

I think I might have to stick with XP on this one, at least for now.  Windows Home Server seems less flexbile from a power management perspective than plain old XP, so that's not an option, and I think I'd quite miss "Wake on Network Activity" if I shifted to Linux and had to move to "Always on".

---

### Post by molotov00 on 2008-06-20
You can used vmware server; have Ubuntu inside XP. It would go to sleep but would consume more power when on. I've never measured power consumption but it's something you might want to consider.

---

### Post by c128 on 2008-06-22
I guess my main reason of considering Ubuntu is to actually ditch XP though.  Due to, ehhh, licensing issues :).  I think for now I may have to just consider a new pre-SP3 install of XP - shame though, "Wake on Directed Packet" etc. really is useful for power saving in small home server use...assuming it could be made to work with Linux, of course.

---

### Post by ljwobker on 2009-04-07
Old thread... but in case someone finds it:  most modern motherboards support wake-on-lan, and I have it working on Ubuntu server 8.10 with no problems. 

Look for "ethtool" and use it to enable wake-on-lan and you're good to go on the server side.

 My "client" machines are all XP, I just grabbed some random freeware "magic packet" generator and point it at the IP address... and ping... the machine wakes up properly.

--lj

---

### Post by c128 on 2009-04-12
> **ljwobker said:**
> Old thread... but in case someone finds it:  most modern motherboards support wake-on-lan, and I have it working on Ubuntu server 8.10 with no problems. 

Look for "ethtool" and use it to enable wake-on-lan and you're good to go on the server side.

 My "client" machines are all XP, I just grabbed some random freeware "magic packet" generator and point it at the IP address... and ping... the machine wakes up properly.

--lj

I'd be surprised if Wake On LAN didn't work with most modern motherboards and all flavours of Linux.  However, what's under discussion here is "Wake on Directed Packet" - this basically means, "Wake up the machine if **anything** is directed at its IP address".  This works really, really well for me with XP, doesn't work well with Vista and seems to be absent in terms of Linux Intel NIC support (unless anyone knows differently).  In terms of power-saving, it works a treat - if you try to access the machine, or one of its shares, it wakes up for you (assuming it isn't already awake) - operation is completely transparent to the client.  It's a shame this isn't more widely support in both the Windows and Linux worlds, although I suspect it doesn't always work that well; my old Buffalo router, for example, seemed to spout randomness at the machines on my local network, some of which was directed at my server and so woke it up unnecessarily, my newer D-Link router is, however, fine.

---

### Post by AeroKnight on 2009-09-27
C128,

What you describe is available under Linux. Assuming your hardware supports it, ethtool will let you set your ethernet adapter to wake up on any of the following events:

  p - Wake on phy activity  
u - Wake on unicast messages
m - Wake on multicast messages
b - Wake on broadcast messages
a - Wake on ARP
g - Wake on MagicPacket(tm)  

sudo ethtool -s eth0 wol ug - will enable wake on lan for unicast traffic and magic packet and so on - read the man pages for more.

Not sure which would give your users the most transparent access from S3, I would assume physical activity or unicast should do the trick.

Remember, ethtool settings are not persistent across reboots so once you have the settings you need you need to put them in a startup script so it runs evertime your computer boots up.

Hope this helps.

---

### Post by GriFF3n on 2009-12-23
Read the man pages but it doesn't go into detail about what each of the ethtool wol options actually mean. Any where I can look to get a description of what each option is supposed to do?

---

