---
title: "Deleted base zone files in error"
date: 2013-03-28
forum: Server Platforms
---

### Post by kevin999 on 2013-03-28
I have accidentally deleted the files named in the '/etc/named.conf' for my network. I am still able to server my webserver files, but my question is :

1. Where can I get replacements.
2. Do I need them - and what are they for ?

// be authoritative for the localhost forward and reverse zones, and for
// broadcast zones as per RFC 1912
zone "localhost" {
        type master;
        file "/etc/bind/db.local";
};
zone "127.in-addr.arpa" {
        type master;
        file "/etc/bind/db.127";
};

---

### Post by matt_symes on 2013-03-28
I think you may get a better response in the **Server Platform****s** subforum.

Thread moved.

EDIT: ... and welcome to the forums :)

---

