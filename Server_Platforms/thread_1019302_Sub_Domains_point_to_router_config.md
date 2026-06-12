---
title: "Sub Domains point to router config"
date: 2008-12-23
forum: Server Platforms
---

### Post by R.Bucky on 2008-12-23
Hello all - I am another first-post noob. I have an Ubuntu 8.04 LAMP box with a fresh Apache install and a static ip. My domain ([http://buckyspalace.net](http://buckyspalace.net)) works just fine, however any of my sub domains return with my homepage (outside of my network) or my router configuration screen if I access them inside the network.

I configure my sub domains by inserting a file named john.conf into /etc/apache2/sites-available/john.conf with the following info:
Code:

```
#/etc/apache2/sites-enabled/john.conf
<VirtualHost *>
ServerName john.buckyspalace.net
DocumentRoot /var/www/subdomains/john
</VirtualHost>
```

I then enable and restart apache with sudo a2ensite, etc...

What gives? I know that this is an easy fix, but it escapes me. Any suggestions?

---

