---
title: "virt hosts?"
date: 2006-07-11
forum: Server Platforms
---

### Post by philipMac on 2006-07-11
hey...
I have a server myServer.org, and I want to set up named based virt servers on it. 
However, I want it to work like:

myServer.org/lab_dev
myServer.org/lab
myServer.org/pub_dev
etc.
I want each virt server to log separately, have its own doc root, have its own allow deny etc. 
Running apache 2.0, I have read through the virt hosts document, I can do all of this with port nums:
myServer.org:80
myServer.org:81
etc, no problems. 

What do I do to get the name thing working and not all logging in the one place etc? Any example of this that I can look at?

---

### Post by Kurt` on 2006-07-11
Just make a new file in /etc/apache2/sites-enabled/ for each VirtualHost you want.

Feel free to use these as templates:

The main (default, non-subdomain) VirtualHost

```
<VirtualHost *>
        ServerAdmin webmaster@localhost

        ServerName "sitename.com"
        ServerAlias "www.sitename.com

        DocumentRoot /var/www/default/public_html
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/default/public_html>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # I like to keep my access.log right outside the public_html folder, feel free to keep yours wherever

        LogLevel warn
        CustomLog /var/www/default/access.log combined

</VirtualHost>
```

And a subdomain:

```
<VirtualHost *>
        ServerAdmin webmaster@localhost

        # note how we don't use a ServerAlias here
        ServerName "sub1.sitename.com"

        DocumentRoot /var/www/sub1/public_html
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/sub1/public_html>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # I like to keep my access.log right outside the public_html folder, feel free to keep yours wherever

        LogLevel warn
        CustomLog /var/www/sub1/access.log combined

</VirtualHost>
```

You could have all of your VirtualHosts in one file, or spread them across multiple files. Up to you. :)

---

### Post by philipMac on 2006-07-11
ServerName "sub1.sitename.com"

Do I not need to get in touch with DNS people to get this to work?

---

### Post by Kurt` on 2006-07-11
Ohhh, I see what you were originally asking now.

I'm not entirely sure how to do VirtualHosts with port numbers, but I believe you just change <VirtualHost *> to <VirtualHost *:81> for example.

The format of the rest of the <VirtualHost> will be exactly the same though (specifying the docroot, log locations, etc.).

Sorry I can't help further.

---

### Post by philipMac on 2006-07-11
Yeah, no doing it with numbers is no problem. I can do that. I just really dont like all these ports open. 

I just thought it would be neater to have 80 open, and have lots of virt servers residing there. 

I think I just need to get in touch with the DNS people, and carry on with the port numbers thing. 

I thought there would be a way...

---

### Post by Kurt` on 2006-07-11
Just so we're clear:

My first post in this thread showed how to have multiple VirtualHosts on a single port. So [http://sitename.com](http://sitename.com), and [http://sub1.sitename.com](http://sub1.sitename.com) both work.

The alternative, what you're doing now (I think), is having [http://sitename.com](http://sitename.com), [http://sitename.com:81](http://sitename.com:81), and so forth.

VirtualHosts can accomodate either of these situations, although I think the first one is a more elegant solution. See if your DNS people can give you a few subdomains to work with. :)

---

### Post by philipMac on 2006-07-11
Yes. We are clear. And I am in agreement with you, the way I am doing it is not elegant. 

Thanks Kurt. Much appreciated. I am waiting on the DNS boys and girls now. :neutral:

---

### Post by nihilocrat on 2006-07-11
> **Kurt` said:**
> Just make a new file in /etc/apache2/sites-enabled/ for each VirtualHost you want.

You could have all of your VirtualHosts in one file, or spread them across multiple files. Up to you. :)

To be more "elegant", you should probably be making the files in /etc/apache2/sites-available/ and just symlinking them (ln -s /etc/apache2/sites-available/mysite /etc/apache2/sites-enabled/mysite). This allows you to disable and later re-enable vhosts easily, as you have the original vhost configs at all times. It also gives you (and any other admins) a clear idea of which POSSIBLE sites the server is configured for. The EVEN MORE "elegant" way of doing this is to use a2ensite and a2dissite to enable/disable sites, but there's no difference in just deleting the symlinks to disable a site and remaking them to enable it.

---

### Post by philipMac on 2006-07-11
True. (This is actually what I am doing, cause I am so damn elegant ;))
The problem still remains though...

---

