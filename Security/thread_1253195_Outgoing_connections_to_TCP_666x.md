---
title: "Outgoing connections to TCP 666x"
date: 2009-08-29
forum: Security
---

### Post by dave562 on 2009-08-29
I was checking my firewall logs and I noticed a large number of connection attempts from my Ubuntu box (8.04) to seemingly random internet hosts.

The src ports are high order ports and the connections are trying to establish themselves to ports

6661
6665
6667
7000

It is happening approximately once every 60 seconds.  I have run a netstat -a and don't see anything running on TCP that would be trying to connect to those ports.

What other tools can I use to attempt to locate the process that is trying to connect to those ports?

---

### Post by The Tronyx on 2009-08-30
Looks like IRC traffic.  Are you on any IRC networks?  Is this on an Ubuntu server by chance?

You could also try using wireshark to dump the traffic and find one packet in the connection sequence.  Once you have that packet, right click it and choose the option, "Follow TCP Stream."  From there, you should have a good idea of what that network activity is trying to do.

---

### Post by dave562 on 2009-08-30
I agree that it looks like IRC traffic.  I am running Ubuntu server (8.04 LTS).  Is IRC installed by default?  I'd rather not mess with Wireshark.  Aren't there any utilities built into Linux that will identify which processes are trying to make network connections?

---

### Post by ApEkV2 on 2009-08-31
tcpdump

why hate wireshark?

---

