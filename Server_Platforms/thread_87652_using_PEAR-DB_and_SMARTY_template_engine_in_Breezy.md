---
title: "using PEAR-DB and SMARTY template engine in Breezy"
date: 2005-11-08
forum: Server Platforms
---

### Post by OneSeventeen on 2005-11-08
I just installed SMARTY and PEAR-DB but I'm not quite sure how to use it... don't I have to add PEAR and SMARTY to my include path?

If so, where did PEAR and SMARTY install to?
(I just added the universe repositories to my sources.list and installed pear, php-db, and smarty via apt-get)

---

### Post by OneSeventeen on 2005-11-08
Okay, apparently they are stored in /usr/share/php/smarty/libs/ and /usr/share/php/PEAR.php

I don't know how to use PEAR yet, so I'll search their site, but the only problem I'm having now is getting the web user to have write access to the smarty template_c and cache folders...

Basically I need to give PHP scripts write access to certain folders.  How do I do this?

So let's say I have the folder:
/var/smarty/templates_c
And I want PHP to be able to write to that folder, here's what I've done so far:
chown -R nobody /var/smarty/templates_c
chmod -R 775 /var/smarty/templates_c

yet it still is not writable... is nobody not the web user?  if so, which user is?

---

### Post by OneSeventeen on 2005-11-08
Okay, to answer my own question, the web user is www-data and to use the PEAR stuff, I just added ":/usr/share/php" to my include_path in the php.ini

And now I'm learning all the crazy complicatedness that is SMARTY, but it looks pretty cool so far!

---

