---
title: "Ubuntu Server 16.04 LTS on VPS and different virtual hosts"
date: 2017-06-23
forum: Server Platforms
---

### Post by albertocastillo2001 on 2017-06-23
Hello

I have a VPS server setup with a LAMP stack using tasksel
The web server runs the default "It Works" site properly by typing it's IP address

I have also installed phpmyadmin and apache2 documentation using
 ```

apt-get install phpmyadmin
apt-get install apache2-doc

```

I have also setup a virtual host which has been already enabled with the following configuration
```

<VirtualHost *:80>
        # The ServerName directive sets the request scheme, hostname and port that
        # the server uses to identify itself. This is used when creating
        # redirection URLs. In the context of virtual hosts, the ServerName
        # specifies what hostname must appear in the request's Host: header to
        # match this virtual host. For the default virtual host (this file) this
        # value is not decisive as it is used as a last resort host regardless.
        # However, you must set it for any further virtual host explicitly.
        ServerName www.domainname1.com
        ServerAlias *.domainname1.com


        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/domainame1.com/public_html


        # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
        # error, crit, alert, emerg.
        # It is also possible to configure the loglevel for particular
        # modules, e.g.
        #LogLevel info ssl:warn


        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined


        # For most configuration files from conf-available/, which are
        # enabled or disabled at a global level, it is possible to
        # include a line for only one particular virtual host. For example the
        # following line enables the CGI configuration for this host only
        # after it has been globally disabled with "a2disconf".
        #Include conf-available/serve-cgi-bin.conf
</VirtualHost>

```

I also plan to have another virtual host like this:
```

<VirtualHost *:80>
        # The ServerName directive sets the request scheme, hostname and port that
        # the server uses to identify itself. This is used when creating
        # redirection URLs. In the context of virtual hosts, the ServerName
        # specifies what hostname must appear in the request's Host: header to
        # match this virtual host. For the default virtual host (this file) this
        # value is not decisive as it is used as a last resort host regardless.
        # However, you must set it for any further virtual host explicitly.
        ServerName www.domainname2.com
        ServerAlias *.domainname2.com


        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/domainame2.com/public_html


        # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
        # error, crit, alert, emerg.
        # It is also possible to configure the loglevel for particular
        # modules, e.g.
        #LogLevel info ssl:warn


        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined


        # For most configuration files from conf-available/, which are
        # enabled or disabled at a global level, it is possible to
        # include a line for only one particular virtual host. For example the
        # following line enables the CGI configuration for this host only
        # after it has been globally disabled with "a2disconf".
        #Include conf-available/serve-cgi-bin.conf
</VirtualHost>

```

The server only has an IP Address. All the documentation I have found teaches you how to make virtual hosts, but none of them seems to show you how to bind one or more domain names to a specific virtual host on a unique server with a unique IP address.

How can I do this? My domain name is setup with NameCheap and I absolutely have no idea what to put there as it's asking for nameservers. Do I have to setup a DNS server in my Ubuntu Server installation do achieve this?

Eventually I would like to use postfix as a mail server and tie the server to both domain names as well for mailboxes and even have subdomains for different virtual hosts that might arise in the future.

I would like to do this the best and correct way possible to ensure it's scalable and won't have issues in the future. My knowledge about Linux is ok, but I am not a guru but would like to learn.

Thanks

---

### Post by darkod on 2017-06-23
If you have created the sites correctly in sites-available and enabled them (so that they show in sites-enabled too), your work on the webserver is done.

What your question is really about is public DNS for your domain name. Namecheap does have DNS manager in which you will need to create A record for the domain pointing to your VPS public IP. You should also create A record for [www.domain.com](www.domain.com) so that it work both with and without www in front in a browser.

That should do it... When anyone types your domain name in a browser, it will ask Namecheap for the public IP assigned to it. Then it reaches your server and even though you have only one public IP, the virtual host part of apache will open the correct site matching the domain name.

I'm no expert in apache but i think the correct virtual host definition to start with is the following:
```
ServerName domainname.com
ServerAlias www.domainname.com
```

That is covering the two basic situations, domain.com and [www.domain.com](www.domain.com). I don't know if wildcard definition like *. would work... Better to start with the above first. Besides, you really want your webserver to open any *.domain.com URL?

---

### Post by albertocastillo2001 on 2017-06-23
Hello

Thank you.

Correct, the virtual hosts show up in sites-enabled (I enabled them using a2ensite which is the same as a symlink to the sites-available file)

On NameCheap I find an Advanced DNS feature, is that the one you're talking about?

I attempted to do this one of my no-ip host names, A record pointing it to the public VPS IP address I have.
I updated the virtual host file to reflect the hostname from no-ip and after restarting the apache2 server it shows only the default site (just like if I manually typed the IP address in), but not the virtual host site.
I do want to keep the default host site accesible using the IP address tho

I didn't try using NameCheap first due to it seems to take a longer time to update records.

Did I do something wrong here?

EDIT: Yes, I did something wrong. My browser cached the page. :)) it works now using the No-IP dynamic host. So I will try soon using NameCheap.
EDIT: Used NameCheap as well and it worked! Set a DNS A Record for "www" host to the server's ip address

Thanks!

What about my mail server questions?

Thanks!

---

