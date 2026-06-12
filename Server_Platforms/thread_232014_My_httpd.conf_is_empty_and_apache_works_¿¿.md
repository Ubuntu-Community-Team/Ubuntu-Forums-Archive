---
title: "My httpd.conf is empty and apache works ¿¿??"
date: 2006-08-08
forum: Server Platforms
---

### Post by benjaminwr on 2006-08-08
Hi,

I was trying to get to the configuration of my apache and went to /etc/apache2/httpd.conf and found this....

# This is here for backwards compatability reasons and to support
#  installing 3rd party modules directly via apxs2, rather than
#  through the /etc/apache2/mods-{available,enabled} mechanism.
#
#LoadModule mod_placeholder /usr/lib/apache2/modules/mod_placeholder.so

Nothing else in the file... but even so.. apache works.

I would like to know if the ubuntu repository configures apache in some different location.

Id appreciate some insight

:P

---

### Post by clif2 on 2006-08-08
> I would like to know if the ubuntu repository configures apache in some different location.


/etc/apache2/apache2.conf :)

---

### Post by benjaminwr on 2006-08-08
dumb me...

thanks alot

---

