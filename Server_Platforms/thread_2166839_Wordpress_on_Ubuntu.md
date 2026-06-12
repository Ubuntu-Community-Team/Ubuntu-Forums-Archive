---
title: "Wordpress on Ubuntu"
date: 2013-08-11
forum: Server Platforms
---

### Post by nCMpdkB on 2013-08-11
Hi Everyone,

I've tried installing wordpress on my Ubuntu server by using this guide [https://help.ubuntu.com/community/WordPress](https://help.ubuntu.com/community/WordPress)

but when I run up localhost/ I get this message displayed in my browser

Neither **/etc/wordpress/config-11.123.123.123.php** nor **/etc/wordpress/config-123.123.123.php** could be found. 
 Ensure one of them exists, is readable by the webserver and contains the right password/username.

Any thoughts? I've had a google for the error but not been able to work it out yet.

Thank you!

---

### Post by Chris of Arabia on 2013-08-11
Can you see either of those two files in /etc/wordpress/ in your file manager?

---

### Post by nCMpdkB on 2013-08-11
no, there are only three files in that directory:

config-localhost.php  htaccess  wp-config.php

Thanks

---

### Post by Chris of Arabia on 2013-08-11
Well that would explain the message. We just need to work out why they're not there. More reading needed (for me that is...)

---

### Post by nCMpdkB on 2013-08-11
OK, thanks.
I just noticed that the numbers in the missing file (which I have changed to **11.123.123.123**) is my external ip address. not sure if that matters though.

---

### Post by Chris of Arabia on 2013-08-11
Looking at the installation guide again, that would definitely matter, as it looks like you've asked the installation routine to look for files that don't exist.

---

