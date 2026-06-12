---
title: "SSH and NFS rejected to only 1 host until networking restart"
date: 2009-04-24
forum: Server Platforms
---

### Post by Adam B. on 2009-04-24
I have a network file server setup on Jaunty.  I installed the beta a few months ago and aptitude full-upgrade'd to the latest release.

It was working fine until the other day (possible after an upgrade).

I had windows computer setup to mount an NFS share.  One day it stopped working from that windows computer.  I thought it was a problem with Windows, so I installed the Jaunty release on that same machine.  The problem still exists.

Whenever I try to access the nfs share, it will just sit there.  A `df` will hang until I cancel it.  When I try to SSH into that box I will receive a "ssh: connect to host 192.168.0.50 port 22: Connection refused".  When I do a "sudo /etc/init.d/networking restart" on the file server, I can connect and everything works well for a few minutes (10-15), but then it will stop again.

I have another Ubuntu computer on the network that can access the NFS share and SSH into the server without problems when the symptoms are occurring on the other desktop.

I've tried changing the IP address on the problem computer with the same results.

This has me baffled.  Could it be a problem with the network card?  It doesn't seem to be related to the operating system or software at all.

There doesn't see to be anything in the logs that would explain this either.

---

### Post by Adam B. on 2009-04-26
If anyone else has the same issues, It turned out to be an IP conflict on the network.

---

