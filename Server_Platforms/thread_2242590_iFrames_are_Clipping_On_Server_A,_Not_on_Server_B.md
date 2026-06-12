---
title: "iFrames are Clipping On Server A, Not on Server B"
date: 2014-09-02
forum: Server Platforms
---

### Post by kschiff on 2014-09-02
We have cloned a PHP-based web app from one Ubuntu 12.04 LAMP server to another. We've made some modifications on the database records side, but environment wise, both sites are the same (there maybe some subtle differences to the server set up). When we display the content on site B (the clone), the iFrames that are constructed to deliver the content are being clipped height and width wise (see the attached image). All the PHP and CSS code is the same on both sites. Both sites have PHP Version 5.3.10-1ubuntu3.13 and Apache/2.2.22

I've wondered whether this might be a PHP or Apache configuration difference, but I don't have enough experience to determine what might be causing this. I have noticed that apache2/mods-enabled are not exactly the same for both servers. For example php5.conf is included in mods-enabled on the good server, but not on the one that's clipping.

[ATTACH=CONFIG]256081[/ATTACH]

---

