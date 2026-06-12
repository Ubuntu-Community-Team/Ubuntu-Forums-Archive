---
title: "Is OpenLDAP my way?"
date: 2011-11-18
forum: Server Platforms
---

### Post by obrador on 2011-11-18
Hi, first of all I must say that I'm an absolutely beginner in LDAP matters. That's wy, before I start trying I would like to make sure LDAP is my solution.

If you don't mind, I'l expose my case and the only thing I would like to know is, first, if can it be done, and second, if can it be done with OpenLDAP.

We are a set of schools and want to create a common way to authenticate students and teachers. We only need a database with people data, uid, gid, and home directory. Each school is independent from the other, each one has it's own network, local servers and domain. We share a common server (called master) used as a puppet master server of each server, also it hosts a mediawiki, a moodle and some other web tools.

What I would like to achieve is centralized user administrator (via web) on this master server where each school can register their students and teachers, then each local server on each school would fetch from the master server only the registers related to their school (domain name would be great to tag each student). This data would be used to authenticate them on each network and mount (maybe will use autofs) it's home directory, etc... 

The goal is to make easy the user management, so easily user could be registered on a single place, and after that tehy would have rights to authorize to all places an school have: mediawiki, moodle, nfs, samba...

Questions are: 1.- can it be done with LDAP? 2.- where can I read to achieve this? 3.- Any case similar to this one?

I searched internet with very poor results.

Many thanks in advance,
jaume.

---

### Post by jaal on 2011-11-20
Maybe you can look at this page

[http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html](http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html)

   how they connect to the main server from different locations? via LAN or WAN, you must define your IP's addresses as statics.

---

