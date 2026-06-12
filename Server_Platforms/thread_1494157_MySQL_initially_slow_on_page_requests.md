---
title: "MySQL initially slow on page requests"
date: 2010-05-26
forum: Server Platforms
---

### Post by R.Bucky on 2010-05-26
I have a MySQL server on Ubuntu 8.04, RAID1, 3GHz Intel Core2 Duo that seems like it needs to wake up on a page load request. Once the page is loaded, the server operates well. When serving static .html or php pages their is no lag. Any ideas why a slow start off the initial request (approximately 4 seconds).

---

### Post by tgalati4 on 2010-05-26
Anything in the /var/log/apache2 log files?

---

### Post by R.Bucky on 2010-05-26
Nothing in the error.log, kern.log, or any other log for that matter. I enabled slow logging for mysql and found nothing.

---

### Post by tgalati4 on 2010-05-27
Install htop on the server and watch it during a mysql call:

sudo apt-get install htop
htop

Try to describe the load and what is happening during the mysql query.  What web application are you using?  Is this a home-grown database application, or something off-the-shelf?

---

### Post by dragos2 on 2010-05-27
Are you using desktop hard drives or green hdd's ? Or non-enterprise like ?

---

### Post by tgalati4 on 2010-05-28
mysql builds cache instances for each user to speed up queries.  It sounds like when you first query mysql and the cache is empty, it may take a few seconds to to build up before serving the first page.  Perhaps you set a configuration setting to clear caches too soon?

The other possibility is your RAID1 (mirror) is slowing down the initial mysql query.  What is your RAID hardware?  If it's software-based and you are CPU-bound, then that could be the bottleneck.  htop should show that if you hit 100% CPU routinely with initial mysql queries.

---

### Post by Vegan on 2010-05-28
I dislike software RAID, get a real RAID card.

Also if you are short on memory things can slow down considerably.

My old backup server runs fast because it has enough RAM. It handles lots of requests every day and no problems at all.

See my site for details.

---

