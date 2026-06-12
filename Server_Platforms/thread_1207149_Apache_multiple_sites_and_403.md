---
title: "Apache multiple sites and 403"
date: 2009-07-07
forum: Server Platforms
---

### Post by bprof on 2009-07-07
I have apache server setup and working fine for a domain. I wanted to add a new domain domain2.com.

I created a file in sites-available called domain2.com.conf

The content of that file is

<VirtualHost *>
ServerName domain2.com
DocumentRoot /var/www/domain2
</VirtualHost>

I then ran the following

sudo a2ensite domain2.com.conf 

And add the following line to /etc/hosts
127.0.0.1 localhost kb.edgecast.com

Then

sudo /etc/init.d/apache2 reload 

The problem when I visit the new site I get 403.

The permission on the site folder is correct and owned by www-data.

Is there anything I miss configured that is causing this problem?

Thanks

---

### Post by Wim Sturkenboom on 2009-07-08
You virtualhost might need something like below
```

#WimS
# this is required to prevent message 403 "Forbidden"
    <Directory "/home/wim/www/site1/web">
        Order allow,deny
        Allow from all
    </Directory>

```

---

