---
title: "Archive_Tar (PHP PEAR) broken since 9.10 update"
date: 2009-11-02
forum: Server Platforms
---

### Post by will81 on 2009-11-02
I've been using the PEAR object Archive_Tar in a PHP script I wrote to create a backup of my web site and the contents of its MySQL database.  It was working fine, and still is working on my development machine (Mac OS X 10.4 with Apache and PHP... erm... something older) but since upgrading my Ubuntu Server to 9.10, it's stopped working.  I can create Archive_Tar objects but as soon as I attempt to create or extract an archive, the script just dies without leaving any error in Apache's log.

What changed in the upgrade?  PHP?  PEAR?  Tar?

-Will.

---

