---
title: "Subdomains"
date: 2009-12-22
forum: Server Platforms
---

### Post by Skidbladniir on 2009-12-22
How would I go about creating a subdomain on my home server?

I've been messing around with /etc/apache2/default, but I really don't know what to do...

Host: physibots.co.cc
IP: 192.168.1.3/70.114.165.50

---

### Post by Vegan on 2009-12-22
You need bind9 to have a DNS with the sub domains, then you can use vhosts in apache2 to use as many sites as needed.

---

### Post by Skidbladniir on 2009-12-22
I'm sorry, wut? :confused: I'm very knew to Ubuntu, Apache, and such.
Lol.  I have a tab open titled "BIND9ServerHowto" right now. xP
Still need help configuring it.  Just installed it w/ apt-get.

---

### Post by Skidbladniir on 2009-12-22
Ok, so I added a Zone Record (A).

Host: asset.physibots.co.cc
TTL: 1 D
Type: A
Value: 70.114.165.50

Edit:

```

root@physibots:~# vi /etc/apache2/sites-available/default
<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ServerAlias asset.localhost

        DocumentRoot /var/www/asset
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/asset/>
                Options FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/liv/cgi-bin">
                AllowOverride None
                Options +ExecCGI -Multiviews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

"/etc/apache2/sites-available/default" 84 lines, 1895 characters

```

---

### Post by BkkBonanza on 2009-12-22
I don't know why people keep recommending installing Bind9 to do DNS. There are several reasons why you should just use your domain registrar's usually free DNS.

1. They run multiple redundant servers to increase reliability vs. you have one DNS doing double duty with no recommended second server (usually).

2. They are almost always much faster than a home server running DNS. They are in a data center on a network backbone with much better conectivity than someone on an adsl home connection.

3. DNS is important and having it at home is more likely easier to hack and poison.

4. DNS is often not that easy to manage for beginners and it's just plain easier and more friendly to use one alreayd setup and functioning. 

5. Using the free one doesn't consume any resources on your own server. Not this is much for a small site anyway.

The only reason for a small home based server to run DNS is that they need local name services. That can usually be handled easily and more effectively on your router anyway.

So if you want to add a subdomain just go to your domain registrar or free DNS server that you use and add an A record for the subdomain and point it at your IP address. Then read up on Apache VirtualHost directive and add them as needed to your apache config files. Don't waste time installing and configuring and mis-configuring your own DNS server. I assume you have better things to do.

PS. In your config above you have a ServerAlias directive but no ServerName directive. You need to add that.

---

### Post by Skidbladniir on 2009-12-22
Well, I just read a tutorial, and it said to make a CNAME record, and I did.  I added what it said to add, and when I reload Apache2, it says, "*:80 has no VirtualHosts"

[http://knightlust.blogspot.com/2007/09/setting-up-subdomain-in-apache2-and.html](http://knightlust.blogspot.com/2007/09/setting-up-subdomain-in-apache2-and.html)

Edit: and the subdomain wont work.  :P

---

### Post by BkkBonanza on 2009-12-22
> **Skidbladniir said:**
> Well, I just read a tutorial, and it said to make a CNAME record, and I did.  I added what it said to add, and when I reload Apache2, it says, "*:80 has no VirtualHosts"

[http://knightlust.blogspot.com/2007/09/setting-up-subdomain-in-apache2-and.html](http://knightlust.blogspot.com/2007/09/setting-up-subdomain-in-apache2-and.html)

Edit: and the subdomain wont work.  :P

Check your config file again carefully. 
As I said above you are missing a required ServerName directive.
ServerAlias is not enough. That is used if you have multiple names for the same file location.

BTW a CNAME record will work as well if the subdomain is being hosted by the same IP as the main domain. CNAME = Canonical Name, means a mapping to that other name, same as the other name. A RECORD = address record, tells it what IP to return for that name. CNAME is useful if you will always have them on the same IP as you can change the A RECORD for the main domain and all the others will follow.

---

### Post by Skidbladniir on 2009-12-22
> **BkkBonaza said:**
> Check your config file again carefully. 
As I said above you are missing a required ServerName directive.
ServerAlias is not enough. That is used if you have multiple names for the same file location.

BTW a CNAME record will work as well if the subdomain is being hosted by the same IP as the main domain. CNAME = Canonical Name, means a mapping to that other name, same as the other name. A RECORD = address record, tells it what IP to return for that name. CNAME is useful if you will always have them on the same IP as you can change the A RECORD for the main domain and all the others will follow.
Well, for starters, I deleted all that and added what the tutorial I mentioned talked about.  So, what do I put for ServerName?

---

### Post by Skidbladniir on 2009-12-22
I have servername set.

```

*<VirtualHost *>*
*        DocumentRoot "/var/www/asset"*
*        ServerName asset.physibots.co.cc*
*        ServerAdmin webmaster@physibots.co.cc*
*        ErrorLog /var/log/apache2/kb.log*

*        <Directory /var/www/asset>*
*                Options Indexes FollowSymLinks MultiViews +Includes*
*                AllowOverride None*
*                Order allow,deny*
*                allow from all*
*        </Directory>*
[I]</VirtualHost>

```
[/I]

---

### Post by BkkBonanza on 2009-12-22
That looks about right. What do you get now (after you restart apache).

---

### Post by Skidbladniir on 2009-12-22
root@physibots:~# sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                                                                                             [Tue Dec 22 02:35:21 2009] [warn] NameVirtualHost *:80 has no VirtualHosts
 ... waiting [Tue Dec 22 02:35:23 2009] [warn] NameVirtualHost *:80 has no VirtualHosts
                                                                                                                                                      [ OK ]
root@physibots:~#

---

### Post by BkkBonanza on 2009-12-22
That term "NameVirtualHost *:80" in the error isn't present in the config you listed above. So I have to assume that the config files are not set up quite right. Take a step back and check that the main config file is indeed loading the sites-enabled configs. Something is still wrong there.

---

### Post by hessiess on 2009-12-22
Make sure you have a line like this:

```

NameVirtualHost *:80

```

Before any of the virtual host blocks, then just add your vhost blocks after it.

```

<VirtualHost *:80> <- must match the above line
        ServerName [subdomain].[your domain name]
        DocumentRoot [unique document root for the vhost]

        <Directory "[unique document root for the vhost]">
                Options FollowSymLinks ExecCGI
                AllowOverride All
                Order allow,deny
                Allow from all
        </Directory>
</VirtualHost>

```

---

### Post by oneloveamaru on 2009-12-23
DO NOT add in a line for NameVirtualHost *:80. If you are using Ubuntu, this is already present in /etc/apache2/ports.conf

The reason it's giving you that WARN message is because you have Apache set up to use VirtualHost *:80 but your config does not have it.

Just change <VirtualHost *> to <VirtualHost *:80>

and then restart apache. Error should be gone.

---

