---
title: "Mysql5 + Php5"
date: 2005-11-10
forum: Server Platforms
---

### Post by dbee on 2005-11-10
What's the best way to install these two for ubuntu ??

synaptic or binary compilation ??

EDIT: if it's synaptic, then does anyone have a backport server that has these packages ??

---

### Post by pitr on 2005-11-11
Php5 I think is in breezy so its easiest installing it with synaptic. As for mysql5 I think they supply rpm so you could use alien to convert it to a deb or you could compile it directly from source.

---

### Post by dudus on 2005-11-22
I think you should compille both since I had some issues with the php5 in the repos like tha lack of mysqli.

---

### Post by dudus on 2005-11-22
I wrote a how to compile mysql5 [here]("http://www.ubuntuforums.org/showthread.php?t=93725&page=1&pp=10").

---

### Post by OneSeventeen on 2005-11-22
Just to be "that annoying guy" of the thread:
As long as you are just testing things out, I'd reccomend compiling both, but if it is in a production environment, it might be better to stick with PHP5 from the supported repository along with the supported version of PostgreSQL (8.0 I think)

PostgreSQL has been doing stored procedures and triggers for a while, it's a little more difficult to get started with, but once you do the payoff is nice.  I'm a long time MySQL user that just switched, and it was tough, but I'm glad I did it.

With that said, have fun compiling and let us know how dudus' tutorial went!

---

### Post by gymsmoke on 2006-04-14
I am preparing to install Ubuntu 5.10 as a production server, and would like to use mysql5 and php5 as components for this.  I did see earlier in the thread about being able to find mysql5 in synaptic.  I have multiverse and universe, as well as backports enabled in my apt sources, but searching for mysql5 turns up empty.

Any ideas?  Or should I be installing this from source?

---

### Post by Gtaylor on 2006-05-11
try mysql-server-5.0 or mysql-server. Or better yet, open up Synaptic and just search for mysql :)

---

### Post by Gtaylor on 2006-05-11
try mysql-server-5.0 or mysql-server. Or better yet, open up Synaptic and just search for mysql :)

---

