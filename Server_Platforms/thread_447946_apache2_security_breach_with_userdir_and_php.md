---
title: "apache2 security breach with userdir and php"
date: 2007-05-18
forum: Server Platforms
---

### Post by legg on 2007-05-18
At uni, we have the labs server, this server also serves users homepages. Since students also learn php, we put ourselves in a position of risk. Particularly, if some user were to do this php code and ran it from his public_html:

[PHP]<?
include("/var/www/mambo/configuration.php");

echo $mosConfig_user;
echo "<br>";
echo $mosConfig_password;
?>[/PHP]

He could know information (about mambo) that should be restricted.
Any way to avoid this behaviour?

Thanks in advance.

---

### Post by craigp84 on 2007-05-18
Yeah, there's a few options. Google "chroot apache" and "suexec".

Plenty of good quality tutorials out there so you'll excuse me if i save my RSI :-)

-c

---

