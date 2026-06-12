---
title: "symbolic link does not read from site root"
date: 2008-10-25
forum: Server Platforms
---

### Post by dan_118 on 2008-10-25
I have a storage mount at /mnt/storage.
I made a symbolic link:
ln -s /mnt/storage/zips /var/www/zips.

In zips I have a .php file that makes an include call for my header, footer, nav_bar, etc in my root /var/www.  I am getting the error:

Warning: include(/footer.php) [function.include]: failed to open stream: No such file or directory in /mnt/storage/zips/index.php on line 36

Warning: include() [function.include]: Failed opening '/footer.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in /mnt/storage/zips/index.php on line 36

If I use an http path or call /var/www/footer.php it works.  This does not:
<div id="footer"><php include("/footer.php");?></div>

Thanks,
dan

---

### Post by hyper_ch on 2008-10-25
well:

/footer.php is not the same as /mnt/storage/zips/footer.php

---

