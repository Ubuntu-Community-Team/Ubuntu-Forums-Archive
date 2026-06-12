---
title: "httpd (pid 4167?) not running"
date: 2007-10-11
forum: Server Platforms
---

### Post by GavinPearce on 2007-10-11
I got the following message when restarting apache2:

httpd (pid 4167?) not running

Haven't come across any problems, and I notice another post says it's nothing to worry about, but just checking what causes this and how to stop it happening, happens everytime on apache2 restart.

Any ideas anyone?

---

### Post by James79 on 2007-10-11
I'll give it a try :)

When you restart apache, it will first attempt to stop any currently running instance of it.

I believe it will look in "/var/run/apache2.pid" for the old process ID. When apache is shutdown, I believe this file gets deleted. Perhaps apache was shutdown improperly at some point (system crash?) and this file never got removed and is now stale.

I would try this: stop apache. delete that file. start apache.

Do you still get the error then?

---

