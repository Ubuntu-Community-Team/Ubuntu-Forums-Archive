---
title: "How to install lampp and set up php page in var/www/html directory ?"
date: 2023-01-08
forum: Server Platforms
---

### Post by ashokabrother on 2023-01-08
I am  a new ubuntu user, plz help me,  How to install lampp and set up php page in var/www/html directory ?

---

### Post by deadflowr on 2023-01-08
*Thread moved to **Server Platforms***


Don't know, maybe this would be a good starting point: 
[https://ubuntu.com/server/docs/lamp-applications]("https://ubuntu.com/server/docs/lamp-applications")

---

### Post by SeijiSensei on 2023-01-09
There are a multitude of pages on the web about how to install the LAMP stack on Ubuntu. This one seems pretty good: [https://phoenixnap.com/kb/how-to-install-lamp-in-ubuntu](https://phoenixnap.com/kb/how-to-install-lamp-in-ubuntu)

---

### Post by LHammonds on 2023-01-09
If you are new to Linux administration, I would recommend learning how to install each component individually and understand the risks and countermeasures for each component...especially if you ever intend for them to be exposed to the Internet.

There are several areas you need to install / configure / secure:

1. Ubuntu Server
2. MariaDB (I would not use MySQL but the commands and API are the same)
3. Apache web server + PHP + DB libraries

I have documented how I setup servers step-by-step but it isn't for everyone.  I like to configure servers for long-term use with as little need for me to touch it as possible.

I use LVM and separate various areas into their own partitions and set their size based on where the data is expected to grow (for example, /var for a web server might get the most space if web sites will continue to ingest data...such as a video server)

The tutorials below can help you get a handle on managing servers or at the very least, have insight in how one particular person manages his servers with detailed documentation.

[How I install Ubuntu Server 22.04 LTS](https://hammondslegacy.com/forum/viewtopic.php?f=40&t=301)
[How I install MariaDB 10.6 on Ubuntu 22.04](https://hammondslegacy.com/forum/viewtopic.php?f=40&t=304)
[How I install Apache Web Server on Ubuntu 22.04](https://hammondslegacy.com/forum/viewtopic.php?f=40&t=302)

My server environment is all virtualized so my instructions are based on that.  They are generally the same for bare-metal installs but you have to take into consideration the hardware available such as drives and RAID arrays which I do not cover.

LHammonds

---

