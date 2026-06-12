---
title: "Ubuntu Server with Lighttpd and PHP seems to be caching and eating all my RAM"
date: 2013-05-05
forum: Server Platforms
---

### Post by hoppipolla on 2013-05-05
Heya peeps :)

Ok here is what happens!

The RAM starts at about 1.1gb used. It then slowly uses more and more and more as the server runs and serves my sites, until the RAM is all full (the "free" command reports it is nearly all cached) and then it puts about 5mb into swap, and frees up about 110mb of RAM. Then this depletes to 0, it puts a bit more into swap, and then free up lots of RAM again, and I think this continues.

Usually, I reboot the server before it repeats this too much as I am concerned that it will eventually hinder site performance.

What do you guys think about this?

I do sometimes use APC, XCache, memcached and/or Varnish, but the problem remains even with ALL of them off. I run 3 sites, 1 of them is very busy (relatively speaking) with a lot of PHP and MySQL use. Lighttpd uses Fast CGI.

My VPS has 2 vCores and 2gb total RAM, and 1gb swap. I use Ubuntu 12.04 (updated, server edition, 64 bit).

Overall my server's performance is pretty good and fast with or without caching and the CPU seems to be doing ok.

I have the official Ubuntu 1.4.28 version of Lighty installed and my lighttpd.conf is attached below.

[ATTACH]242244[/ATTACH]

Thanks so much! :)

Hoppi!

---

