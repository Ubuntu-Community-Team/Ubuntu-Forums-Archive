---
title: "being flooded on port 80"
date: 2008-09-22
forum: Security
---

### Post by e2ekel on 2008-09-22
Hi,
i use ubuntu 8.04 server edition and shorewall4.
i'm running lighttpd as webserver, i have the 80 port open.
i also run an Half-life dedicated server.
today i encountered some problems with people getting kicked due to some connection errors, so i took a look in jnettop (to see active connections) and saw it was someone flooding. it looks like this:

my_ip <-> some_ip                                                                181b/s 2.82K/s  3.00K/s
 my_ip                            4065    TCP  some_ip                            80     727b   11.3K    12.0K
  GET /1/31917/13195/images/clock.gif
my_ip <-> some_ip                                                                168b/s 2.19K/s  2.35K/s
 my_ip                            4063    TCP  some_ip                           80     672b   8.76K    9.42K
  GET /1/31917/13195/images/tn16.jpg
my_ip <-> some_ip                                                                168b/s 2.06K/s  2.22K/s
 my_ip                            4060    TCP  some_ip                            80     672b   8.24K    8.90K
  GET /1/31917/13195/images/tn13.jpg

i guess someone is requesting files from my webserver that aren't actually there, somehow exhausting my bandwidth resources.
on my webserver i'm serving only three simple html pages, with no images (they're actually redirect pages)
the ip address marked with some_ip is changing every few seconds, so writing rules for each ip address won't help.

what should i do?
thanks

---

### Post by The Cog on 2008-09-22
This article describes how to rate limit incoming SSH connections. Change to port 80 and it will rate-limit incoming HTTP connections.
[http://www.debian-administration.org/articles/187](http://www.debian-administration.org/articles/187)
This will work for you provided that:
* Your real users only connect once and get a redirect, not fetching lots of images etc.
* You are actually getting a series of connections from each of the non-users, enough to trigger the blocking action.

---

