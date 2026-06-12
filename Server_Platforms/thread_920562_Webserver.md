---
title: "Webserver"
date: 2008-09-15
forum: Server Platforms
---

### Post by bigfatdummy on 2008-09-15
I am about to purchase a new webserver for my company. It would be nice to get some other users opinions. The website traffic varies day to day. Some days we have almost no traffic and other days we have 250 users on the site for multiple hour sessions. We have a bonded T1 connection (2 T1 circuits). Off site hosting isn't really an options due to the size of the website (currently 350 GB, with 10-25 GB being added & removed weekly). I am replacing my webserver due to hardware failure issues. Obviously, I need to have some large hard drives to hold the site. This server will only be used as a LAMP server. I do not want to lose visitors due to an unresponsive site. Any suggestions on hardware? I don't want to waste money and have way too much server for what I need.

---

### Post by jamesrfla on 2008-09-15
I just use a plain computer that I built as my server. I would recommend building your server not buying a desktop. I recommend a 64Bit system with about 4GB. Also make sure it has a 1.0Gps wired network interface in it.

---

### Post by Drezard on 2008-09-17
I would recommend also setting a raid of some sort. Also make sure u have an amazing disaster recovery and power cut solution.

---

### Post by bigfatdummy on 2008-09-17
I bought an IBM eServer with 4GB memory and 4 1TB drives. I have a Drobo with 4 1TB drives in it as a temporary backup solution and additionally keep a mirror copy of the site on my work pc as well as a copy of the site minus the html/php pages (pdfs, tifs, zip files, etc).

Thanks for the advice.

---

