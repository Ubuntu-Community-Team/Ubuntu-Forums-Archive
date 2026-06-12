---
title: "Hosted Website Automatically Redirecting"
date: 2016-01-29
forum: Server Platforms
---

### Post by Kyle_Souza on 2016-01-29
I am using Apache, until yesterday I only wanted to host one wordpress website on my server, now I want to host two.  I copied the 000-default.conf file (and the SSL conf, I have a certificate for both domains), made changes, and enabled the site.  Now the second site (site2) is working fine, but when I try to visit my other site (site1), the one that was there first, it automatically redirects to my new site.  If I rename the folder for site1 the redirect still happens, when I disable site1 in apache it still redirects... It seems that somehow site2 has become the primary/default site for the server, but I cannot figure out where/how.

Any help is appreciated, I can provide file contents as needed, I am new to the forum (bear with me as I learn how to use it).

Thank you in advance.

Two new pieces of info:
1.  [https://pandplandservice.com/owncloud](https://pandplandservice.com/owncloud) does not redirect, even though [https://pandplandservice.com](https://pandplandservice.com) does.
2.  I found this in the apache error log (I set it to debug):  No matching SSL virtual host for servername pandplandservice.com found (using default/first virtual host)
But I do have ServerName pandplandservice.com setup in a conf file.

---

### Post by darkod on 2016-01-29
When you say you copied the file and made changes, you refer to making changes inside the .conf file right? Because if you only changed the filename, that does not tell apache which site to open.

You need to take a look and compare the .conf files content, mainly the part about the Directory Root (where the files are for each site) and the URL of each site.

---

### Post by Kyle_Souza on 2016-01-29
Fixed it.  I had to add the ServerName to the SSL conf file for the two sites then rerun the WordPress config setup for the site that wasn't working.

---

### Post by ajgreeny on 2016-01-29
Great.

Please mark as SOLVED from the Thread Tools menu at the top.

---

