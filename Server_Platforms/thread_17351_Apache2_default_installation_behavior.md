---
title: "Apache2 default installation behavior"
date: 2005-02-28
forum: Server Platforms
---

### Post by Chris C on 2005-02-28
By default, Apache2 only seems to show the "welcome to apache" page.  It doesn't matter what I point it at in /var/www/, if it's not the root, I get an access denied.

I know this has something to do with the virtual server configuration, but after hours of reading I just don't understand it.  ](*,) 

I want it to serve pages/images whatnot "normally" from /var/www/ instead of denying everything or diplaying welcome to apache from the base URL. I'm sure that other forum members have had to edit the various config files to get what I'm trying to do. What *exact* changes do I need to make?

---

### Post by az on 2005-02-28
The file is
/etc/apache2/sites-enabled/default

Comment out the  RedirectMatch  line.

---

### Post by Chris C on 2005-02-28
Thank you. The other acccess issue was bad file permissions. How embarrasing.

---

