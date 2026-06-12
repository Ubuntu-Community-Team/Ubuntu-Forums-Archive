---
title: "Horde Groupware Webmail problem"
date: 2007-03-26
forum: Server Platforms
---

### Post by vertigo_0 on 2007-03-26
You will notice this is my first post here... I have been racking my brain for the past week, searching forums, reading documents, and looking anywhere I can. . . I am hoping this is a simple problem that I missed.

I've been trying to setup a mail server for my place of work(old server died). We used OpenWebmail before, but I wanted to switch over to Horde Groupware Webmail. I have followed the steps as far as I can tell. I've installed/configured the various parts, but after the last stage of the configuration, and try to login, I get an error... "Auth_imp: Required IMAP extension not found." There are two warnings at the top of the first page also:

"
Warning: register_shutdown_function() [function.register-shutdown-function]: Invalid shutdown callback 'imap_errors' passed in /var/www/horde/imp/lib/base.php on line 145

Warning: register_shutdown_function() [function.register-shutdown-function]: Invalid shutdown callback 'imap_alerts' passed in /var/www/horde/imp/lib/base.php on line 146
"

I am guessing it is a PHP error, dealing with a modual not being installed or setup correctly. I'm really confused. The documents on this are a bit.... lacking... so ANY help would be nice, and thanks in advance.

---

### Post by drakkan on 2007-03-26
apt-get install php5-imap

regards
drakkan

---

### Post by vertigo_0 on 2007-03-27
Welllll, what do you know, it works...

Thanks, I knew it had to be a simple problem. Thanks again for your help.

---

