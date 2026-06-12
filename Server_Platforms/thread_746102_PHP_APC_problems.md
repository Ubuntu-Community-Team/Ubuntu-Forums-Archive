---
title: "PHP APC problems"
date: 2008-04-05
forum: Server Platforms
---

### Post by timpea on 2008-04-05
Hi,

I am having problems with APC, have a look at:
[http://new.splatshop.co.uk/apc_03Apr.php](http://new.splatshop.co.uk/apc_03Apr.php)

It always shows Uptime of 0 minutes, so I assume it is being reloaded every time a page is called.  I am running PHP as a CGI with suPHP, check out phpinfo here:[http://new.splatshop.co.uk/phptest_03Apr.php](http://new.splatshop.co.uk/phptest_03Apr.php)

Any help would be great thanks, I've been scratching my head about this for the last couple of days.

Cheers
Tim

---

### Post by conjur3r on 2008-04-07
Have you tried running PHP normally, eg not via CGI, or not with suPHP?  I'm afraid one of these (most likely suPHP) may not be allowing the requested query to go to the root apache process.  I'm positive it is only displaying the uptime of the process servicing your request.

---

