---
title: "I'm DNS (dum not smart)"
date: 2006-07-29
forum: Server Platforms
---

### Post by joshchernoff on 2006-07-29
OK you win, I lose. I now can say from my hart that I trully hate DNS nameservers!


alright now that I got that out. I need some help under standing what is it that I need to make this web hosting home brewed server work.


this is what I got now.

> 
One:
amd64 3000+ with a gig of ram and plenty of harddisk space.

Two:
Ubuntu server made and running from a guide off [http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)
(I got this up and running localy with no problems)

Three:
Ispconfig web managment

Four:
One static IP from my dsl provider with 856kbs up stream

Five:
Two domains from godady.com


Now I know I need to have a name server to give to godady to point the domain to. then the nameserver points to the IP of the host server. I don't know how this will work if I dont have my own DNS nameservers, or how I can have a 3rd party nameserver point more then one domain to a single IP.
  please keep in mind that I wormed my way this far on my own in one week never running a server befor. So please lay in on me esay.

---

### Post by gruepig on 2006-07-29
You don't need your own DNS servers; you can have godaddy handle DNS for you:
[http://help.godaddy.com/article.php?article_id=682&topic_id=163&&](http://help.godaddy.com/article.php?article_id=682&topic_id=163&&)

---

### Post by joshchernoff on 2006-07-29
ok so what do I do about having a virtual host server and haveing godady point two domains to the same IP and then have them go to the right web site on the server.

Ex [http://portlandcraftmafia.com/](http://portlandcraftmafia.com/) points to my main IP of my server. I made a site on ISPconfig but it still gos to the main index page not it's own page that I made.
So if I had a nother domain point to that IP it to would go to the same place as [http://portlandcraftmafia.com/](http://portlandcraftmafia.com/). how do I have it point to it's own page on the server, not just the main IP index.

I hope I'm right about what I'm asking sorry if its to vage.

---

### Post by LordHunter317 on 2006-07-29
You point it to the same IP and use name-based virtual hosting.

I don't know if those tools will actually support that correctly, which is why I shun them.

---

### Post by chrisfay on 2006-07-29
In order for you to host multiple web sites from your computer you have to configure Apache virtual hosts for both sites. 

If you are using Apache2 you need to add your domains to the http.conf file in the format:

<VirtualHost *>
DocumentRoot "/var/www/yourdomain"
ServerName [www.yourdomain.com](www.yourdomain.com)
<Directory "/var/www/yourdomain">
allow from all
Options +Indexes
</Directory>
</VirtualHost>

<VirtualHost *>
DocumentRoot "/var/www/yourdomain2"
ServerName [www.yourdomain2.com](www.yourdomain2.com)
<Directory "/var/www/yourdomain2">
allow from all
Options +Indexes
</Directory>
</VirtualHost>

Restart apache

If you are using a 3rd party DNS like zoneedit, add "A" records to the zone for both sites that point to the IP of your server.

---

### Post by strixy on 2006-07-29
A few tips...

The config file you want to edit for apache virtual services under Ubuntu are
/etc/apache2/sites-available/default (if memory serves )

and make sure this file exists (or copy it from mods-available)
/etc/apache2/mods-enabled/vhost_alias.load

to edit them easily you can use the command line

sudo -H gedit

And then follow up on the great advice already given above.

Or, even easier, (but way more limited option)...

the main directory apache serves files from is

/var/www

You can pickup a free dyndns.org domain (and their ip updaters etc) to get a domain like myhost.homeunix.net pointing to your server. Then use godaddy's domain forwarding option to forward the domain to your dyndns address (which is then forwarded to your home server) with a subfolder. Like so...

if you set the files for one domain as

/var/www/domain1

and the other as 

/var/www/domain2

you can use godaddy's forwarding option to point domain1 to yourserver.yourdynds.net/domain1, and then mask the URL (in godady) and then forward domain2 to yourserver.yourdyndns.net/domain2

It's easier than editing apache files. (Though editing apache files is already pretty darn easy). And you usually get screwed if your doing anything fancy on your server as Godaddy uses frame forwarding, which is a big PIA.

To get around the godaddy PIA, check out zoneedit.(as mentioned above)

---

### Post by joshchernoff on 2006-07-29
ok so I winged it and got it to work with a diffrent name server from [https://www.xname.org](https://www.xname.org). I got it to where I got diffrent sites in the shared IP. this seems to work ok now though I'm not sure I got it all the way up right yet. the smpt dont work right yet. when I dig @ns0.xname.org any republic-of-funk.com I get

> 

; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 10283
;; flags: qr aa rd; QUERY: 1, ANSWER: 4, AUTHORITY: 0, ADDITIONAL: 3

;; QUESTION SECTION:
;republic-of-funk.com.          IN      ANY

;; ANSWER SECTION:
republic-of-funk.com.   86400   IN      SOA     ns0.xname.org. ceo.jrcproduct.com. 2006072905 10800 3600 604800 10800
republic-of-funk.com.   86400   IN      MX      0 mail.republic-of-funk.com.
republic-of-funk.com.   86400   IN      NS      ns0.xname.org.
republic-of-funk.com.   86400   IN      NS      ns1.xname.org.

;; ADDITIONAL SECTION:
mail.republic-of-funk.com. 86400 IN     A       216.99.199.102
ns0.xname.org.          600     IN      A       195.234.42.1
ns1.xname.org.          600     IN      A       193.218.105.149

;; Query time: 192 msec
;; SERVER: 195.234.42.1#53(195.234.42.1)
;; WHEN: Sat Jul 29 12:36:55 2006
;; MSG SIZE  rcvd: 203


I use the ISPconfig to add a email for the site republic-of-funk.com  when I try to log in it dont like the password. I'm sure that it sees the email address though. I'v tryed every diffrent way I know to log in. I wonder if it's the dns or some thing else?

---

### Post by chrisfay on 2006-07-29
> The config file you want to edit for apache virtual services under Ubuntu are
/etc/apache2/sites-available/default (if memory serves )

Thanks for the correction...

---

