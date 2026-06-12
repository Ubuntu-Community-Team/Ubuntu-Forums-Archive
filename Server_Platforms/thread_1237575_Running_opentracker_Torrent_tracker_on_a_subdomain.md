---
title: "Running opentracker Torrent tracker on a subdomain"
date: 2009-08-11
forum: Server Platforms
---

### Post by nonexistentera on 2009-08-11
Basically.
I am wondering how, because most of the one's that I have seen run off of a sub-domain.

One such is openbittorent, which runs off of 
[http://tracker.openbittorrent.com/announce](http://tracker.openbittorrent.com/announce)
I am wondering if there is anyone familiar enough with this to give me some guidance on how to do this.

Or if there is any general way to use dns to accomplish this.

Thanks in advance for any help.

---

### Post by Barrucadu on 2009-08-11
The subdomain will point to a different server, which runs the tracker.

---

### Post by nonexistentera on 2009-08-11
Can this be done through DNS like so:

Server1(main server): Runs WWW,DNS, and is the first machine.
server2(tracker): Specifically for the tracker

Is it possible I can force the tracker to run on the subdomain using only one server

Could I do this, or would I need a server just for the DNS. 
I have BIND9, running on Ubuntu 9.04

---

