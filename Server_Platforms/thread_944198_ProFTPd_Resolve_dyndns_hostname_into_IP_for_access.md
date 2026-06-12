---
title: "ProFTPd: Resolve dyndns hostname into IP for access?"
date: 2008-10-11
forum: Server Platforms
---

### Post by ensnare on 2008-10-11
Hi -- is it possible to grant access to a dyndns host?  Here's the problem:

I want host 1.2.3.4 to connect whose reverse dns resolves to 1-2-4-4.isp-example.com.  I could put the IP into an "allow from" but then when the ip changes, the host will no longer be granted access.

The host has a dyndns name of "name.dyndns.org" and I'd like to be able to enter that.  Except if I enter that host into the "allow from" the server does a reverse lookup of 1.2.3.4, finds 1-2-4-4.isp-example.com, and rejects access.

So, is there a way to do a lookup of "name.dyndns.org," resolve that to IP, and add that to the access list at each connect?  Or is there another workaround?

Thanks for your help.

---

