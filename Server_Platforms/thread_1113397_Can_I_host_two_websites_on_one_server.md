---
title: "Can I host two websites on one server?"
date: 2009-04-01
forum: Server Platforms
---

### Post by doctorbighands on 2009-04-01
If so, how do I do it?

I already have Apache2 (in Ubuntu 8.10 Server) running perfectly for one site, and I have the CNAME for the second site pointed to my home server address. How do I have siteA.com and siteB.com running on the same server? So far, Google searches have been relatively unhelpful for this.

Just FYI, I'm still pretty new to server stuff, so a lot of hand-holding will probably be necessary here. It took me a long time to figure out how to get the first site live, so getting the second one live will probably take time, too.

Thank you!

---

### Post by albinootje on 2009-04-01
> **doctorbighands said:**
>  How do I have siteA.com and siteB.com running on the same server?


You would use Virtual Hosts in Apache for this.
Here's one example for one Virtual Host in the Apache configuration :
```

<VirtualHost *>
    ServerName yoursite.org

    DocumentRoot /home/yoursite.org/public_html
    DirectoryIndex index.php index.html index.htm

        <Directory "/home/yoursite.org/public_html">
                Options Indexes FollowSymLinks
                AllowOverride None
                Order allow,deny
                Allow from all
        </Directory>

    ErrorLog /var/log/apache2/yoursite.org-error.log
    TransferLog /var/log/apache2/yoursite.org-access.log
</VirtualHost>

```

---

### Post by doctorbighands on 2009-04-01
Where do I find that Virtual Hosts file?

---

### Post by albinootje on 2009-04-01
> **doctorbighands said:**
> Where do I find that Virtual Hosts file?
You can put a Virtual Host in a separate text file.
And then I think it's a matter of putting the text file in the /etc/apache2/sites-enabled/ directory and then restart Apache.

Or you insert it in : 
/etc/apache2/sites-enabled/000-default

---

### Post by Iowan on 2009-04-01
See if [this]("http://ubuntu-tutorials.com/2008/01/09/setting-up-name-based-virtual-hosting/") one helps.

---

