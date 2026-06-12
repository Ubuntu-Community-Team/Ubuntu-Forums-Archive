---
title: "Apache help"
date: 2015-03-07
forum: Server Platforms
---

### Post by fzaman2 on 2015-03-07
Alright...I've been trying to get apache to server my website via a domain I own and I am getting nothing but the default ubuntu page.

I went through the following steps using info I found on [this website]("https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-14-04-lts"): 

```
fzaman@zserver:~$ sudo mkdir -p /var/www/farabeck.com/public_html

fzaman@zserver:~$ sudo chown -R $fzaman:$fzaman /var/www/farabeck.com/public_html




fzaman@zserver:~$ ls -l /var/www/farabeck.com/
total 4
drwxr-xr-x 2 fzaman fzaman 4096 Mar  6 21:38 public_html


fzaman@zserver:~$ sudo chmod -R 755 /var/www


fzaman@zserver:~$ sudo cp /var/www/html/index.html /var/www/farabeck.com/public_html/index.html


fzaman@zserver:~$ sudo nano /var/www/farabeck.com/public_html/index.html


#edited last line in index.html to state <p> farabeck index.html page </p>


fzaman@zserver:~$ sudo cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/farabeck.com.conf


fzaman@zserver:~$ sudo nano /etc/apache2/sites-available/farabeck.com.conf


#added following to farabeck.com.conf file


ServerAdmin XXXXXXXXXX@XXXXXXXXX.com
        ServerName farabeck.com
        ServerAlias www.farabeck.com
        DocumentRoot /var/www/farabeck.com/public_html


fzaman@zserver:~$ sudo a2ensite farabeck.com.conf


fzaman@zserver:~$ sudo service apache2 reload

fzaman@zserver:~$ sudo service apache2 restart




```

I believe I have the virtual host set up correctly as well the folder that contains my website's index.html.

Not sure what I am doing wrong but any help would be appreciated.

---

### Post by volkswagner on 2015-03-07
Can you post contents of /etc/apache2/sites-available/farabeck.com.conf

```
cat /etc/apache2/sites-available/farabeck.com.conf
```

Did you run:

```
sudo a2ensite farebeck.com.conf
sudo service apache2 restart
```

Apache runs as www-data user. The directory needs to be readable by www-data. Depending con content, it may
also need to be writeable by www-data.

---

### Post by gconn on 2015-03-07
If you follow this guide it should help. I refer to it often: [https://www.linode.com/docs/websites/hosting-a-website/](https://www.linode.com/docs/websites/hosting-a-website/)

---

### Post by fzaman2 on 2015-03-07
> **volkswagner said:**
> Can you post contents of /etc/apache2/sites-available/farabeck.com.conf

```
cat /etc/apache2/sites-available/farabeck.com.conf
```



Sure, here it is: 

```
fzaman@zserver:~$ cat /etc/apache2/sites-available/farabeck.com.conf<VirtualHost *:80>
    # The ServerName directive sets the request scheme, hostname and port that
    # the server uses to identify itself. This is used when creating
    # redirection URLs. In the context of virtual hosts, the ServerName
    # specifies what hostname must appear in the request's Host: header to
    # match this virtual host. For the default virtual host (this file) this
    # value is not decisive as it is used as a last resort host regardless.
    # However, you must set it for any further virtual host explicitly.
    #ServerName www.example.com


    ServerAdmin XXXXXXXX@XXXXXX.com
    ServerName farabeck.com
    ServerAlias www.farabeck.com
    DocumentRoot /var/www/farabeck.com/public_html


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


# vim: syntax=apache ts=4 sw=4 sts=4 sr noet
fzaman@zserver:~$ 



```

> **volkswagner said:**
> 
[COLOR=#000000]Did you run:

[/COLOR]```
[COLOR=#000000][FONT=Ubuntu Mono]sudo a2ensite farebeck.com.conf[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono]sudo service apache2 restart
[/FONT][/COLOR]
```


Yes I ran that...see the end of the code I pasted above.

---

### Post by fzaman2 on 2015-03-07
> **gconn said:**
> If you follow this guide it should help. I refer to it often: [https://www.linode.com/docs/websites/hosting-a-website/](https://www.linode.com/docs/websites/hosting-a-website/)

@gconn, thanks.  I just started looking at that and it has some info in it that looks like it may help.  I'll post what I get once I go through it.

---

### Post by fzaman2 on 2015-03-07
> **gconn said:**
> If you follow this guide it should help. I refer to it often: [https://www.linode.com/docs/websites/hosting-a-website/](https://www.linode.com/docs/websites/hosting-a-website/)

Ran into my first issue...I don't understand where I need to put this snipet of code:

```

[COLOR=#333333][FONT=Monaco]...
[/FONT][/COLOR]<IfModule mpm_prefork_module>
StartServers 2
MinSpareServers 6
MaxSpareServers 12
MaxClients 30
MaxRequestsPerChild 3000 
[COLOR=#333333][FONT=Monaco]</IfModule>[/FONT][/COLOR]
```

Do i paste this all at the end of the .conf file?  Also what do the 3 periods do?

---

### Post by fzaman2 on 2015-03-07
Ok, so I got the website working sort of...

By using 

```
s[COLOR=#333333][FONT=Monaco]udo a2dissite *default[/FONT][/COLOR]
```

This disabled the default side and made the index.html page I had loaded for farabeck.com start working.  However, now I have a couple of other issues still.

1)  I can only access the website externally.  I am sure this is a DNS issue of some sort, but don't know how to fix.  Any ideas?

2) When I access the website from outside my LAN by typing in the domain farabeck.com, the IP address replaces the domain name in the address bar.

Anyone familiar with how to fix these two issues?

---

### Post by fzaman2 on 2015-03-08
Ok so I figured out the answer to #2 in the post above.  I just updated the A host on Godaddy and that solved the ip issue.  Last thing I need help with is the internal issue. 

Any help appreciated

---

### Post by volkswagner on 2015-03-08
If you're having trouble accessing the site internally, it's likely due to NAT issue.

Your router may have settings for allowing NAT loopback or reflection.

---

### Post by fzaman2 on 2015-03-11
> **volkswagner said:**
> If you're having trouble accessing the site internally, it's likely due to NAT issue.

Your router may have settings for allowing NAT loopback or reflection.

Thanks.  I'll look at the router for that.

---

### Post by fzaman2 on 2015-03-11
> **volkswagner said:**
> If you're having trouble accessing the site internally, it's likely due to NAT issue.

Your router may have settings for allowing NAT loopback or reflection.

So just looked at that and didn't see anything labeled NAT, loopback or reflection anywhere in the router's settings.   Any other ideas?

---

### Post by sandyd on 2015-03-11
> **fzaman2 said:**
> So just looked at that and didn't see anything labeled NAT, loopback or reflection anywhere in the router's settings.   Any other ideas?

Whats your router model

May also be called hairpin nat.

Alternatively, setup a local DNS server or run
```

sudo sed -i '$a\local-ip-of-apache domainnamehere' /etc/hosts
```
on each computer that you want to access the site on (replacing local-ip-of-apache and domainnamehere)

---

### Post by fzaman2 on 2015-03-11
> **sandyd said:**
> Whats your router model

May also be called hairpin nat.

Alternatively, setup a local DNS server or run
```

sudo sed -i '$a\local-ip-of-apache domainnamehere' /etc/hosts
```
on each computer that you want to access the site on (replacing local-ip-of-apache and domainnamehere)


Hey, router model is a medialink mwn-wapr300n.  User man can be found [here]("http://m.setuprouter.com/router/medialink/mwn-wapr300n/manual-1740.pdf")

I searched for NAT, but didn't find anything.

---

### Post by sandyd on 2015-03-11
> **fzaman2 said:**
> Hey, router model is a medialink mwn-wapr300n.  User man can be found [here]("http://m.setuprouter.com/router/medialink/mwn-wapr300n/manual-1740.pdf")

I searched for NAT, but didn't find anything.

See [http://www.amazon.com/review/RA184WKY2NYXS/ref=cm_cr_rev_detmd_pl?ie=UTF8&asin=B00A3YN0Z0&cdForum=Fx2KC5YYUS76Z1V&cdMsgID=Mx10GGGKO28A012&cdMsgNo=10&cdPage=1&cdSort=oldest&cdThread=Tx2KHO87NKRLQZ&store=pc#Mx10GGGKO28A012](http://www.amazon.com/review/RA184WKY2NYXS/ref=cm_cr_rev_detmd_pl?ie=UTF8&asin=B00A3YN0Z0&cdForum=Fx2KC5YYUS76Z1V&cdMsgID=Mx10GGGKO28A012&cdMsgNo=10&cdPage=1&cdSort=oldest&cdThread=Tx2KHO87NKRLQZ&store=pc#Mx10GGGKO28A012)

---

### Post by fzaman2 on 2015-03-11
> **sandyd said:**
> See [http://www.amazon.com/review/RA184WKY2NYXS/ref=cm_cr_rev_detmd_pl?ie=UTF8&asin=B00A3YN0Z0&cdForum=Fx2KC5YYUS76Z1V&cdMsgID=Mx10GGGKO28A012&cdMsgNo=10&cdPage=1&cdSort=oldest&cdThread=Tx2KHO87NKRLQZ&store=pc#Mx10GGGKO28A012](http://www.amazon.com/review/RA184WKY2NYXS/ref=cm_cr_rev_detmd_pl?ie=UTF8&asin=B00A3YN0Z0&cdForum=Fx2KC5YYUS76Z1V&cdMsgID=Mx10GGGKO28A012&cdMsgNo=10&cdPage=1&cdSort=oldest&cdThread=Tx2KHO87NKRLQZ&store=pc#Mx10GGGKO28A012)

So the website [http://www.medialinkproducts.com/](http://www.medialinkproducts.com/) no longer exists and the domain is for sale so I couldn't get the firmware upgrade...but the DMZ settings were already in the router so setting the server IP in the DMZ settings and enabling it made it work!!!

Thanks again for your help.

---

### Post by sandyd on 2015-03-11
Side note:

This allows direct access to your server using your public ip address, setup iptables/fail2ban/etc if you are worried about security

---

### Post by fzaman2 on 2015-03-12
> **sandyd said:**
> Side note:

This allows direct access to your server using your public ip address, setup iptables/fail2ban/etc if you are worried about security


Thanks for for the heads up.  So is there a way to not enable the dmz and still see my site internally?

---

