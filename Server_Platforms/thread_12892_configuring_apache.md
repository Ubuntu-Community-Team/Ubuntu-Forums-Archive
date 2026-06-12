---
title: "configuring apache"
date: 2005-01-27
forum: Server Platforms
---

### Post by akurashy on 2005-01-27
after i downloaded all is needed for a webserver using repository 
well everythign is working fine
but there are some things that are buggin the hell out of me >_<
like when i go to a folder it says "Permission denied"
and i think it has a case sensiteve or something because if you put a folder with caps you have to name the folder like it =/

how to remove those

---

### Post by albersag on 2005-01-27
If listing is denied in httpd.conf you can not view empty directories. 

The root directory for www (var/www) is defined in httpd.conf  (/etc/apache/httpd.conf)

Read apache documentation. It will help.

---

### Post by 3spades on 2005-01-27
You can create an .htaccess file in the dir with Options Indexes or stick that into the httpd.conf virtual host entry and it will list the dirs with no indexes.

---

### Post by akurashy on 2005-01-27
well the virtual setting have a lot of apache commands in it
like the allow and deny all etc etc
but i havent checked all of em

---

