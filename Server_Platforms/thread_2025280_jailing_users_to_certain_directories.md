---
title: "jailing users to certain directories"
date: 2012-07-14
forum: Server Platforms
---

### Post by P3t3r on 2012-07-14
Hi all,

I have a LAMP setup on my VPS (Ubuntu 10.04LTS) and I would like to give certain users a website on this server. I do not have a domain name, just an IP address, let's say [http://m.y.i.p/](http://m.y.i.p/)

By default, standard settings will make the http request fetch everything in /var/www, but I would like that:
[LIST]
[*]user1 can write to something appearing in [http://m.y.i.p/folder1/](http://m.y.i.p/folder1/) (i.e. /var/www/folder1)
[*]user2 can write to something appearing in [http://m.y.i.p/folder2/](http://m.y.i.p/folder2/) (i.e. /var/www/folder2)
[*]...
[/LIST]

However, I can't get things right. If I try to jail user1 to /var/www/folder1, I always either block him out of it (unable to get there, starting from /home/user1 in an sFTP client), or he's not jailed in for read operation (he can still read user2's documents in /var/www/folder2).

Obviously, users shouldn't be able to read eachother's folders. How should I do this?

---

### Post by sandyd on 2012-07-14
> **P3t3r said:**
> Hi all,

I have a LAMP setup on my VPS (Ubuntu 10.04LTS) and I would like to give certain users a website on this server. I do not have a domain name, just an IP address, let's say [http://m.y.i.p/](http://m.y.i.p/)

By default, standard settings will make the http request fetch everything in /var/www, but I would like that:
[LIST]
[*]user1 can write to something appearing in [http://m.y.i.p/folder1/](http://m.y.i.p/folder1/) (i.e. /var/www/folder1)
[*]user2 can write to something appearing in [http://m.y.i.p/folder2/](http://m.y.i.p/folder2/) (i.e. /var/www/folder2)
[*]...
[/LIST]

However, I can't get things right. If I try to jail user1 to /var/www/folder1, I always either block him out of it (unable to get there, starting from /home/user1 in an sFTP client), or he's not jailed in for read operation (he can still read user2's documents in /var/www/folder2).

Obviously, users shouldn't be able to read eachother's folders. How should I do this?
Why not just set that as the user's home directory?

---

### Post by P3t3r on 2012-07-14
> **sandyd said:**
> Why not just set that as the user's home directory?Set what as the user's home directory? You mean putting the files in /home/user1/folder1? If that could be made to work that's fine too, but then I fail to find how I should make [http://m.y.i.p/folder1/](http://m.y.i.p/folder1/) grab its files from this folder instead of from /var/www/folder1?

---

### Post by sandyd on 2012-07-14
> **P3t3r said:**
> Set what as the user's home directory? You mean putting the files in /home/user1/folder1? If that could be made to work that's fine too, but then I fail to find how I should make [http://m.y.i.p/folder1/](http://m.y.i.p/folder1/) grab its files from this folder instead of from /var/www/folder1?
Ah, the power of [mod_alias]("http://httpd.apache.org/docs/2.0/mod/mod_alias.html") prevails.

---

