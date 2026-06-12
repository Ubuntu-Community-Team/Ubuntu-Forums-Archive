---
title: "Newbie networking questions"
date: 2006-02-28
forum: Server Platforms
---

### Post by jamyskis on 2006-02-28
Hi all,

While I'm around average for using Ubuntu, I've never really played around with networking before. I have an old Athlon 1700+ lying around which I've decided to set up as a file server, proxy server and HTTP server although I've run into a number of problems.

The first is that the older computer doesn't seem to recognise the DSL modem, whereas the newer computer does and dials in without a problem. This isn't a problem with the network card - ifconfig eth0 reports everything fine with the thing, and the cable between computer and modem is exactly the same one. Still, running pppoeconf reports that it can't find the access concentrator on eth0.

With that, I've had a go at trying to create an NFS file server on the older system. I've installed NFS and created a share (the home directory, in which there is nothing at the moment). There is, at the very least, a connection between the two computers, as the NFS client (the newer) seems to have recognised it, but cannot open it.

Can anyone give me some starter tips on how to get this going, including whether it is possible to run a file server, proxy server and HTTP server on one network card, and if there are any good sites out there that have eluded Google thusfar?

Cheers in advance.

J

---

### Post by suRoot on 2006-02-28
[QUOTE=jamyskis]
The first is that the older computer doesn't seem to recognise the DSL modem, whereas the newer computer does and dials in without a problem. This isn't a problem with the network card - ifconfig eth0 reports everything fine with the thing, and the cable between computer and modem is exactly the same one. Still, running pppoeconf reports that it can't find the access concentrator on eth0.[/QUOTE]

The modem is probably bound to the MAC address of the other system.  Hook the one up you're having problems with & then reset the modem.

[QUOTE=jamyskis]
With that, I've had a go at trying to create an NFS file server on the older system. I've installed NFS and created a share (the home directory, in which there is nothing at the moment). There is, at the very least, a connection between the two computers, as the NFS client (the newer) seems to have recognised it, but cannot open it.

Can anyone give me some starter tips on how to get this going, including whether it is possible to run a file server, proxy server and HTTP server on one network card, and if there are any good sites out there that have eluded Google thusfar?

Cheers in advance.

J[/QUOTE]

I won't speak to NFS as my experience is somewhat limited, but regarding all the services on one NIC, technically it shouldn't be a problem. If you're running this at home just for yourself, don't worry about it.  The NIC can handle it.  Remember though, there are other issues to consider when you're sizing a server.  If the box is thrashing disk I/O due to someone writing a lot of data to the NFS share, it may never even handle all the data the 100Mbps link could throw at it.  In that case, you look at IDE -vs- SATA -vs- SCSI / etc.  Just other things to think about besides network speed.

---

