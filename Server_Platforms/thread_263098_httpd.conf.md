---
title: "httpd.conf"
date: 2006-09-22
forum: Server Platforms
---

### Post by mukatira on 2006-09-22
Something's up with my httpd.conf file

The httpd.conf file in /etc/apache2 in its entiriety is here:

# This is here for backwards compatability reasons and to support
# installing 3rd party modules directly via apxs2, rather than
# through the /etc/apache2/mods-{available,enabled} mechanism.
#
#LoadModule mod_placeholder usr/lib/apache2/modules/mod_placeholder.so


I wanted to AddHandler and ScritpAlias so my localhost/cgi-bin/test looked at the correct html directories. Any ideas for why the httpd.conf file is so consice?

Thanks

Sm

---

### Post by Child of Wonder on 2006-09-22
Check apache2.conf.

Virtual Hosts should be in /etc/apache2/sites-enabled/000-default

---

### Post by compunuts on 2006-09-23
Apache changed its handling with Apache2. Now, you need to put your sites in /etc/apache2/sites-available and use a2ensite command to enable the sites.

If you need a quick howto, check it out [here](http://www.openfree.org/pet/index.php/Apache_2.0_-_Basic_-_on_Ubuntu_Linux).

---

