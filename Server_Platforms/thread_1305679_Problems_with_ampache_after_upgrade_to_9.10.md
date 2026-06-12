---
title: "Problems with ampache after upgrade to 9.10"
date: 2009-10-30
forum: Server Platforms
---

### Post by ilcapo09 on 2009-10-30
Hi there, I've been running Ampache on my Mythbuntu 9.04 server and never had any problems accessing my music through a web browser.Today I upgraded to 9.10 and when I try to access Ampache I get a "403 Forbidden, You don't have permission to acces this server". The strange thing is that this only happens if I type the address as follows [http://127.0.0.1/ampache](http://127.0.0.1/ampache), which used to always work. Now, if I type [http://127.0.0.1/ampache/login.php](http://127.0.0.1/ampache/login.php) it loads without a problem... any suggestions?

---

### Post by myth1914 on 2010-03-02
Did you ever find a solution to this?

I've attempted a direct symlink, modding the alias (bad idea) but all with the same result.

I highly doubt it's a permission issue as it does load when it's pointed to the login.php or index.php (redirects correctly to the login) page.

Could anyone point me in the right direction?

---

### Post by bazzawill on 2010-09-12
I found the solution on [http://wiki.debian.org/Ampache](http://wiki.debian.org/Ampache)

although the ubuntu package has the conf file it is different and editing it to resemble this worked for me


Create and edit ampache file for apache(the webserver). This will tell apache2 about ampache: "/etc/apache2/conf.d/ampache": 

Alias /ampache "/usr/local/bin/ampache/"
<directory />
       DirectoryIndex index.php index.html
       Options Indexes MultiViews
       AllowOverride None
       Order allow,deny
       Allow from all
</directory>

---

