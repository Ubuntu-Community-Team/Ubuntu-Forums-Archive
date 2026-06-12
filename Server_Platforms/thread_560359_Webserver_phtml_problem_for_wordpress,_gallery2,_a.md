---
title: "Webserver phtml problem for wordpress, gallery2, and phpmyadmin"
date: 2007-09-26
forum: Server Platforms
---

### Post by DigitalDuality on 2007-09-26
I am running Ubuntu Dapper for my main webserver. Trying to get everything up and running from my last crash.

I started off installing gallery2 with php4 and mysql. Next I installed phpmyadmin and they both worked wonderfully.

Finally I installed wordpress (view the tar.gz, not ubuntu repo's). Got it installed just fine, exported my xml file from my wordpress blog into my home-hosted setup. Everything was working perfectly.

Until power went out. I had rebooted post gallery2/phpmyadmin install, but i did not after the wordpress install.

Now every site i have, except for a static front/portal page that's just basic html and one little jscript, prompts me to download a phtml file.

I've read around the tubes a bit and saw that editting /etc/apache2/apache2.conf would apply a fix if I uncommented the following two lines and restarted apache.

    AddType application/x-httpd-php .php .phtml
    AddType application/x-httpd-php-source .phps 

i've done that. I've uninstalled apache and php4 as well as php4-common restarted apache, reinstalled them, restarted apache.. and i'm getting the exact same results.

Any help would be appreciated.

---

