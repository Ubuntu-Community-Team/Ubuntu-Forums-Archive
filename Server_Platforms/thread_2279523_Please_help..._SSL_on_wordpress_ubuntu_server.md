---
title: "Please help... SSL on wordpress ubuntu server"
date: 2015-05-24
forum: Server Platforms
---

### Post by sean92 on 2015-05-24
Hi i have ubuntu as a webserver and have loaded wordpress on there already.. however when implementing SSL, the https only works for the homepage ([https://www.mydomain.com](https://www.mydomain.com)) but not the other links to the site such as ([https://www.mydomain.com/about-us](https://www.mydomain.com/about-us))... it gives



[COLOR=#000000][FONT=Times New Roman]The requested URL /about-us/ was not found on this server.[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman][I]Apache/2.4.7 (Ubuntu) Server at [www.mydomain.com](www.mydomain.com)  Port 443[FONT=arial]
[FONT=arial black][FONT=arial]Im not sure what im doing wrong... please help.. ive already tried a few things in the default-ssl.conf file.. [/FONT][/FONT] [/FONT]
[/I][/FONT][/COLOR]

---

### Post by SeijiSensei on 2015-05-24
What if you connect to [http://www.mydomain.com/about-us/](http://www.mydomain.com/about-us/) instead?  Does that work even though it fails with SSL?

---

### Post by sean92 on 2015-05-25
that fails as well... i think thats because theres a force https plugin implemented

---

### Post by SeijiSensei on 2015-05-25
Then I'd have to guess that /about-us/ doesn't exist.  I have a WP blog with an "About the Author" link, but it points to /about/.  Since there are a gazillion themes I don't know if that helps you at all, though.  What about links to postings or to the /wp-admin/ URI?  Do those work with SSL?

---

### Post by sean92 on 2015-05-26
i think i fixed it by following a post from digitalocean..  i had to create a new virtual host entry (*:443) under the 000-default.conf file under sites-enabled... and had to enter in some rules such as 

[COLOR=#333333][FONT=monospace]Options Indexes FollowSymLinks MultiViews[/FONT][/COLOR]        AllowOverride All
        Order allow,deny
        allow from all [COLOR=#333333][FONT=monospace]                Require all granted[/FONT][/COLOR] 

thanks for your help

---

