---
title: "Ext4 on Web Server"
date: 2009-04-24
forum: Server Platforms
---

### Post by hanzgroove on 2009-04-24
Hi all,

I'm just wondering what your opinions are on using an ext4 file system for a web server. If it truly is a faster file system, will that equate to a speedier website? IE: Accessing files, reading from the database, etc? Just wondering if this will let me squeeze out a bit more performance from my server or if it will make very little difference.

Thanks!

---

### Post by lavinog on 2009-04-24
Memory will provide a speedier website before changing to the ext4 fs.
I don't even think the benefits of ext4 will benefit websites anyway. (at least static pages)

To speed up your site, you really have to look into where your bottlenecks are.
Are you running enough apache and mysql connections...
Is the slow down due to the number of users connecting? Bandwidth/latency?

Edit: Also are your pages light enough for the web (make sure that your images are resized properly and indexed to reduce bandwidth)

---

### Post by hanzgroove on 2009-04-24
Thank again for your help lavinog. You're really helpful around these forums.

In regard to my question, I was just wondering if ext4 had any benefits to web servers. I don't have any issue now in regard to speed. Just wondering if that "tweak" would have added some performance. Thanks for the info. I'll pass on ext4 for now.

---

### Post by skirkpatrick on 2009-04-24
Think about it this way:  your 'normal' hard drive transfer rate is several orders of magnitude faster than your Internet connection.

---

### Post by lavinog on 2009-04-25
ext4 is still pretty new. I would avoid it still because of potential data integrity issues:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/348836](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/348836)
This bug should be fixed now with the official jaunty release, but it affected me during RC1.
There can still be other bugs.
generally on a desktop you will notice any irregular issues, but issues on a webserver can go unnoticed for an extended period of time.

On the other hand, if your server is used for downloading torrents, ext4 may offer some benefits (not nessisarly speed though).

---

