---
title: "freshclam won't fetch updates - uses wrong DNS"
date: 2011-05-16
forum: Server Platforms
---

### Post by Skaperen on 2011-05-16
On a new machine  running Ubuntu 10.04.2, the freshclam program (in clamav-freshclam version 0.96.5+dfsg-1ubuntu1.10.04.2) won't do updates to the database.  It fails on DNS queries.  DNS works OK for other programs.  The tcpdump command shows that it sends the queries to 127.0.0.1 instead of the correct DNS servers specified by /etc/resolv.conf.  Of course it doesn't get an answer because it is asking the wrong IP address.

There is also a --no-dns option, but that didn't help/

Do I need to tell ot what the DNS servers are, somewhere?

Why would it query only 127.0.0.1 for DNS?

---

### Post by Skaperen on 2011-05-17
Problem is a bad apparmor configuration for the clamav-freshclam package.  Work around is to add read access to /etc/resolv.conf in the /etc/apparmor.d/usr.bin.freshclam file.

Filed bug report #784060.

---

