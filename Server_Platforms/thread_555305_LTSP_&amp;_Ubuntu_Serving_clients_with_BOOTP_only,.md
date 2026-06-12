---
title: "LTSP &amp; Ubuntu: Serving clients with BOOTP only, without DHCP?"
date: 2007-09-20
forum: Server Platforms
---

### Post by RudeIota on 2007-09-20
Greetings,

I'd like to know if it is possible to use strictly BOOTP to serve PXE-based LTSP clients, rather than DHCP. I'm using Feisty and LTSP 5.

For example, I'm thinking of configuring the bootpd daemon to boot LTSP clients without the use of the dhcpd daemon, or effectively stopping the 'dhcp portion' of dhcpd so that it only provides BOOTP. Does that even *sound* possible?

It is my assumption that if booting ltsp clients via BOOTP is achievable, I could use BOOTP instead of DHCP and ultimately avoid interfering with our existing DHCP server (Cisco router).

The reason? Well, I'm in a corporate "political" situation where an existing DHCP server (Cisco Catalyst 3800) cannot be modified. LTSP seems to depend on DHCP, but it seems like it *could* work with BOOTP too... But I don't know enough to be sure, so I'd like to know if I'm chasing a red herring or not.

My goal? To have a LTSP server that can serve images AND let the existing DHCP server do its job without mucking up the hundreds of other non-LTSP, DHCP clients. 

Other solutions I've come up with (that cannot be done or I am avoiding) are:
[LIST=1]
[*]Creating a separate VLAN for the LTSP clients and server, allowing full reign of dhcpd
[*]Etherboot configured with LTSP server info via removable media (flash, cd, floppy etc)
[*]Changing the scopes of the router and the LTSP server to 'split' the existing VLAN so each leases IPs to part of the subnet, but never the other part.
[*]Somehow configuring the router to offer tftp file location, root-path (and other) info to clients during the DHCP offer/request/ack sequence
[*]Replace the router all together with the terminal server
[/LIST]

Let me know what you think. Along with an answer, I'd love to hear some fresh ideas too. Thanks! :)

---

### Post by koenn on 2007-09-20
I've never ever used bootp (and wonder if anybody still does :) ), but here goes :
bootp was designed to make diskless clients network-bootable, so i suppose it would work for LTSP as well. You'll need to dig up som documentation on the bootp though. 
bootp was extended to offer network config as well, and that's how dhcp came to be, so they're related. 
You might even be able to configure a dhcp server so that it does not hand out any address leases, just shows the clients the way to the boot files. 

A (tricky) workaround (apart from those you already have and which are all better) is to use dhcp reservations so your LTSP dhcp only gives ip leases to designated hosts, not to the non_TS clients. Unfortunately, this doesn't work the other way around : the LTSP-clients may still picj up IP-config and NO boot info from the Cisco router/dhcp server.

Which brings me to a final point : I'm kinda wondering why you would be setting up a LTSP environment while you don't control essential parts of your network, such as its dhcp server. 
Smells fishy. You sure you know what y're doing ?

---

### Post by RudeIota on 2007-09-21
Thank you for the reply.

> You might even be able to configure a dhcp server so that it does not hand out any address leases, just shows the clients the way to the boot files.I like this idea and I pitched it to the people above me. I was asked to make it work with BOOTP instead, so no configuration is necessary on their part. They *may* or may *not* know a lot about LTSP, PXE and so on... but I don't really know for sure. Since that combination really doesn't have any  penetration here (not as of yet!), I don't suspect they know the ins and outs of LTSP.
> A (tricky) workaround (apart from those you already have and which are all better) is to use dhcp reservations so your LTSP dhcp only gives ip leases to designated hosts, not to the non_TS clients. Unfortunately, this doesn't work the other way around : the LTSP-clients may still picj up IP-config and NO boot info from the Cisco router/dhcp server.This could possibly be a solution and this is the kind of stuff I'm searching for. 

The router, as it exists now, does not seem to lease DHCP addresses to PXE clients. It's my understanding that a PXE client will ignore arbitrary DHCP offers and move on to the ones that actually specify useful boot info. There's only one way to test this though, so I'm going to see what I can do to make this work (more specifically, work well). Thanks for the tip. 

> **koenn said:**
> Which brings me to a final point : I'm kinda wondering why you would be setting up a LTSP environment while you don't control essential parts of your network, such as its dhcp server. 
Smells fishy. You sure you know what y're doing ?

Do I know what I'm doing? Not necessarily... That's why I'm here! ;) I am a well experienced system technician, but a relative Linux scrub compared to many of the folks here. 

Fishy? Well, there's a lot of bureaucracy. I am but an individual who plays a very small role in the largest school district in the U.S . I'm the on-site tech person for a particular school, but there's also different levels of tech people for the unified district and even the  sub-districts.

The people who are not on-site aren't really responsible for running each individual school's technology plan - That's my job - so they give us freedom to do as we please with our own equipment. However, we can't step on the district's toes by modifying the network infrastructure. That's strictly their stuff. Linux isn't 'officially' supported by the district either, so this is a little bit outside the box, but it serves our needs and wants on paper.

Our computers are woefully outdated (circa 1998-2001, mostly), but the money just isn't there to invest in a couple hundred new computers. I pitched the LTSP idea as a sort of..  experiment ...  for our school. It won't cost us much because we can reuse the majority of our equipment and it will (ideally) achieve what the students and staff currently lack - computers that can actually be useful for internet, word processing and education in the class room.  Also, our network was recently upgraded, which makes this seem like a fantastic opportunity.

---

### Post by RudeIota on 2007-09-21
> **koenn said:**
> use dhcp reservations so your LTSP dhcp only gives ip leases to designated hosts, not to the non_TS clients. Unfortunately, this doesn't work the other way around : the LTSP-clients may still picj up IP-config and NO boot info from the Cisco router/dhcp server.

Hey! I have some (possibly) good news.

I prepended my /etc/ltsp/dhcpd.conf with the additional keyword
```
**deny unknown-clients;**
# deny unknown-clients tells dhcpd to hand out leases to registered clients only
# which can be specified by mac address using statements. In essence, it ignores
# clients that aren't 'on the list'.

```

Lastly, I appended my existing /etc/ltsp/dhcpd.conf with the following host statement
```
[B]host test {
hardware ethernet 00:E0:4C:C6:E7:4D; 
fixed-address 192.168.0.23;
}[/B]

# "host test {" begins this host statement that will apply to a single computer

# "hardware ethernet ??:??:??:??:??:??;" identifies the MAC address of the
# client's network card, making this statement relevant only to that client 

# "fixed-address 192.168.0.23;" assigns a dhcpd-supplied static IP to the client
# with the specified MAC address 

```
And of course, I followed with a restart of the dhcp daemon: ```
sudo /etc/init.d/dhcp3-server restart
```

Using my (cheesy) equipment at home (a D-link home router and a 'client'  PC with an integrated nvida 100mb NIC), I was able to successfully boot. 

BUT, the exciting part is that my other PCs are keeping their leases from the Dlink router and not getting confused with my LTSP server running dhcpd. I tried disabling, releasing and renewing their IPs several times each and they are being consistent, even with the keyword *authoritative;*.

Now... I just need to hope this will work the same way on our network at school. :) Guess I'll find out tomorrow.

---

### Post by koenn on 2007-09-21
Good news indeed. 
The one thing to verify is that your LTSP / PXE clients will never accept a dhcp lease without boot-info, from that other dhcp server. I suppose you can test this at home by booting a pxe machine with the LTSP-dhcp server off. Then they'd either have to accept a lease from your D-link, or hang at the "looking for dhcp" stage. 
If they do accept a non_boot lease, you may occasionally have trouble with your thin clients in school, i.e. everytime the dhcp offer from the router arrives to a client before the LTSP offer.

---

### Post by RudeIota on 2007-09-21
Fantastic. 

This appears to be working at the school.

I'm going to start configuring some more clients and give LTSP a trial run using the *deny unknown-clients* trick. I'd like to have a thorough test before I dive in and commit, but for now, looks good!

Thank you again, for your inspiration. :)

---

### Post by koenn on 2007-09-21
:)

---

### Post by RudeIota on 2007-09-26
[SIZE="3"][COLOR="DarkRed"]Bad news![/COLOR]
[/SIZE]
What you warned me of was true - the clients don't prefer DHCP info from the LTSP server like I *thought *I had observed.

For whatever reason, after several restarts using a few different clients, it was working just fine. I tried it again a few days later and the exact opposite happened... The issue being that they will get DHCP info from the router (not configured to boot an LTSP client) rather than the LTSP server.

Since that, I'm currently exploring BOOTP. I've created a working boopd.conf that boots LTSP clients without dhcpd, but I'm having difficulty mounting the root NFS file system. If I find a solution or perhaps after I've done some more troubleshooting, I will post back with details... And hopefully a working config!

---

### Post by koenn on 2007-09-27
> **RudeIota said:**
> 
What you warned me of was true - the clients don't prefer DHCP info from the LTSP server like I *thought *I had observed.

the explanation might be that dhcp clients tend to request their existing leases be extended and therefore talk directly to the server that issued the lease. 
However, once a lease has expired, the clients send out broadcasts to find a (any) dhcp server, so here you can get weird results ur undesired effects if you have 2 dhcp servers for the same address pool.

If you get bootp working, I'd be interested to see your confs, so please do post.

---

