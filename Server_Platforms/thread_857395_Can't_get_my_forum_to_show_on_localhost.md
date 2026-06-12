---
title: "Can't get my forum to show on localhost"
date: 2008-07-12
forum: Server Platforms
---

### Post by -ronin- on 2008-07-12
I've installed a forum on our Ubuntu 8.04 fileserver. When you type into your browser *http://<fileserverIP#>/forum*, you get to the forum just fine. But I don't want people to have to go around remembering IP#s. I want them to simply type forum.mysite.org and get into it.

I created a file called forum in /etc/apache2/sites-available

```
<VirtualHost *>
        ServerAdmin webmaster@localhost
        ServerName forum.mysite.org

        DocumentRoot /var/www/forum
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/forum>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

         ErrorLog /var/log/apache2/forum-error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
        ServerSignature On
</VirtualHost>


```

Then in /etc/apache2/sites-enabled I ran the command **a2ensite forum** to create the symlink. After that I restarted apache. But whenever I try navigating to forum.mysite.org I get the following error message, instead:
 
> The requested URL could not be retrieved

While trying to retrieve the URL: [http://forum.mysite.org/](http://forum.mysite.org/)

The following error was encountered:

    Unable to determine IP address from host name for forum.mysite.org 

The dnsserver returned:

    Name Error: The domain name does not exist. 

This means that:

 The cache was not able to resolve the hostname presented in the URL. 
 Check if the address is correct. 


---

### Post by goexplode on 2008-07-12
You might want to read up on how [DNS]("http://en.wikipedia.org/wiki/Domain_Name_System") works. If you want your site to be accessible to the public without having to type in something like http://<insanelyhardtorememberIP#>/ then you'll need to register your domain at a registrar like [GoDaddy]("http://www.godaddy.com/"). If you're planning on hosting your site off of a home broadband connection such as cable or DSL, then [DynDNS]("http://www.dyndns.com/") is a good start. If running a web server is something new to you, then you would probably be better off just paying $5 or $10 a month for a good host and save yourself from the trouble and security risks.

Google is a really good resource, I'd say 99% of what you need to know can be found there.

---

### Post by -ronin- on 2008-07-12
> **goexplode said:**
> You might want to read up on how [DNS]("http://en.wikipedia.org/wiki/Domain_Name_System") works. If you want your site to be accessible to the public without having to type in something like http://<insanelyhardtorememberIP#>/ then you'll need to register your domain at a registrar like [GoDaddy]("http://www.godaddy.com/"). If you're planning on hosting your site off of a home broadband connection such as cable or DSL, then [DynDNS]("http://www.dyndns.com/") is a good start. If running a web server is something new to you, then you would probably be better off just paying $5 or $10 a month for a good host and save yourself from the trouble and security risks.

Google is a really good resource, I'd say 99% of what you need to know can be found there.

The forum I'm creating is supposed to be accessible only via the **intra**net. And if indeed Google were such a valuable resource, then we wouldn't need things like ubuntuforums.org, would we? It's because of pos(t)ers like you that I very rarely even bother with this place. SMH

---

### Post by goexplode on 2008-07-12
> The forum I'm creating is supposed to be accessible only via the intranet.

In the future you might want to provide an adequate amount of information about your problem whenever you ask for help. Nowhere in your original post do you mention that your setup is for intranet only.

Furthermore, there are several other questions that still need to be answered before help can be provided. For example, is [http://mysite.org/](http://mysite.org/) accessible? If so, it is probably only a matter of setting up your virtual hosts correctly. Or is it only accessible by IP? In any case, you should still read up on DNS and how it works.

Try adding "127.0.0.1 localhost forum.mysite.org" to "/etc/hosts" on your server. Although, if you want to be able to access forum.mysite.org from other machines on your intranet, you will also need to add appropriate lines to their hosts file, i.e. "<serverip> mysite.org forum.mysite.org". This can be pretty time consuming, and setting up a DNS server on your local network might be a better solution.

---

### Post by windependence on 2008-07-12
Indeed as goexplode has mentioned, your problem is that you need a DNS alias in your hosts file on every computer on your network, OR run a DNS server if there isn't one there already and insert a DNS entry for the server. On linux, this is usually in /etc/hosts. On Windoze it is in C:\Windows\system32\drivers\etc\ Add an entry as follows to the end of the hosts file and save it, where xxx.xxx.xxx.xxx is the IP of your server.

xxx.xxx.xxx.xxx  yourservername

Note my signature. Had you googled "website not reachable from LAN" you would have gotten tons of answers also.

-Tim

---

