---
title: "scaling MySQL"
date: 2016-10-22
forum: Server Platforms
---

### Post by Vegan on 2016-10-22
I run a bunch of web sites from one database, so I was can MySQL scale up with hundreds, thousands or even millions of articles before i should up a new server or 3

How about a swarm of databases?

---

### Post by cariboo on 2016-10-22
This Forum runs on vBulletin and mysql the database runs at about 70Gib, which equals 2,137,403 threads or 12,918,029 posts plus various attachments and avatars.

---

### Post by Vegan on 2016-10-22
I assume this forum lives on a SSD, hate to see how thrashed a hard disk would be.

I was more interested in larger databases, say a NSA file on every person on the planet etc?

Perhaps a database of genomes?

---

### Post by cariboo on 2016-10-22
> **Vegan said:**
> I assume this forum lives on a SSD, hate to see how thrashed a hard disk would be.

I was more interested in larger databases, say a NSA file on every person on the planet etc?

Perhaps a database of genomes?

If the Forums ran on a single ssd, we would be down more often then not. I haven't checked what hardware we are running now, but it has been updated from the pair of 8 core opterons with 300+GiB ram and multiple hard drives we upgraded to in 2011.

---

### Post by Vegan on 2016-10-22
That much RAM should make for an excellent cache for the web server in addition to the database.

Is the standard LAMP stack able to use available resources as needed or should I consider some settings for higher workloads?

My own virtual machine runs on a dual socket E5 box, but that should not matter that much with a fist full of web sites

---

