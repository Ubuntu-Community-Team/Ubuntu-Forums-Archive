---
title: "netatalk overhead, or should I use smb"
date: 2010-09-05
forum: Server Platforms
---

### Post by wall_e on 2010-09-05
Hi guys,

I would like to pick your brains about something as I am still very much an ubuntu novice.

I've been doing a lot of research and experimenting with my ubuntu server as a centralised storage server for video editing.

Overall my setup works surprisingly well!

I have 10 Mac's connecting to AFP shares which are served up by Netatalk and advertised on the network by Avahi.

From a user perspective it is simple to mount a share.

Since client workstations are only editing DV25, which is 25mbps, so given the number of streams required, 10/100 between the client and the switch and 1gbit to the server seems fine - for now.

For storage I have a 3ware 9550sx RAID controller with 12 SATA drives connected. RAID5 I have approx 5.6Tb quick storage.

There are however a couple of bottlenecks I'd like to fix - if possible.

One thing I have noticed is that connected clients seem to take up a fair amount of CPU time on the server.

Those familiar with netatalk will understand that by default it shares the home folder of a ubuntu user'a to the network.

In my setup I simply create an ubuntu user via webmin when I need to with their home folder stored on the disc array, which is then automatically available to the network.

However as above when I watch my system monitor, each connected user seems to use a fair amount of CPU time - varying percentages between 10-45%.

Obviously this is fine when one user is connected, but it is also a bit of a bottleneck.

Am I barking up the wrong tree here, or is something like samba more efficient in the way that it works?

---

### Post by kidders on 2010-09-07
Hi there,

Just a few of questions ...[LIST]
[*]What version of netatalk do you have, and what CNID scheme is it using (probably either cdb or dbd)?
[*]What filesystem are you using on your RAID array?
[*]Do you notice the CPU usage rise during particular types of operations (eg writing, reading large numbers of small files, etc.)
[/LIST]

> **wall_e said:**
> Am I barking up the wrong tree here, or is something like samba more efficient in the way that it works?Neither is especially efficient, really ... at least not by comparison to something like FTP.

Regarding samba, using a Microsoft sharing protocol to exchange files between *nix boxes isn't the most "natural" choice, and can sometimes cause problems. Whether they would care depends very much on what your users are actually doing from day to day though.

---

