---
title: "Issues with apache2"
date: 2015-01-21
forum: Server Platforms
---

### Post by igor32 on 2015-01-21
I made local site as usual. 

---------------
/etc/apache2/sites-enabled/mysite.conf

<VirtualHost *:80>
    ServerAdmin [EMAIL="samusenkoiv@gmail.com"]samusenkoiv@gmail.com[/EMAIL]
    ServerName mysite
    DocumentRoot /home/igor/projects/mysite
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
-------
after that wrote in /etc/hosts 
127.0.1.1         mysite
-----------
then in terminal I wrote next : 
sudo a2ensite mysite.conf
sudo service apache2 restart
---------

I do it always, and all works correctly.
But here's thing.  When I follow to [http://mysite](http://mysite), it works like I follow just to [http://127.0.1.1/](http://127.0.1.1/)  I move to apache2 ubuntu default page.
So I'm trying to figure it out:
1. I tried to change DocumentRoot, it didn't help. I had the same behavior.
2. I tried to change ServerName (and line in /etc/hosts accordingly). And it worked. 

"mysit" works, "ysite" do too. But "mysite" doesn't. A really need to use "mysite" url ( "mysite" is here for example ).
I also should say that it worked before, I could follow to [http://mysite](http://mysite) correctly, but then something broke :( 
What can it be ? Some blacklist ? What can happen ?

---

### Post by TheFu on 2015-01-21
Which version of apache?  Things changed in the recent major release around the deny/allow commands. Think they use "grant" now.

Also, that virtualhost stanza seems short to me, but I don't really use apache too much anymore.
Don't you need the <Directory /> stuff too?

I vaguely remember that something about the configuration file names mattered which caused me pain too.  Don't know if it was the required .conf at the end or leading numbers? Sorry.  On my last apache system, we have both now.

---

### Post by SeijiSensei on 2015-01-21
Like TheFu says, you're missing a <Directory> stanza in the configuration file.  Add this just above "</VirtualHost>":
```

<Directory "/home/igor/projects/mysite">
     Options All
</Directory>

```
Restart Apache.  Any better?

You're trying to define a "[name-based]("http://httpd.apache.org/docs/current/vhosts/name-based.html")" virtual host.  Apache will use your configuration file for any requests to the URL [http://mysite/](http://mysite/).  For any other request, by IP or some different name, the file /etc/apache2/sites-enabled/default.conf will be used.

---

### Post by igor32 on 2015-01-21
I added <Directory>, it doesn't help.
As I said, I always do it, and it always works!
I have about 10 sites which have similar .conf files and they work correct.

About "name-based" =>  as I said, "mysite" it is just an example. In fact I use "mychinesemec.test" url. 

Something happened exactly with "mychinesemec.test" url =(

---

### Post by igor32 on 2015-01-21
I forgot to provide this lines from /var/log/apache2/access.log
They appear when I try to request  :.
127.0.0.1 - - [21/Jan/2015:17:32:17 +0200] "GET / HTTP/1.1" 200 3594 "-" "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Ubuntu Chromium/39.0.2171.65 Chrome/39.0.2171.65 Safari/537.36"
127.0.0.1 - - [21/Jan/2015:17:32:17 +0200] "GET /icons/ubuntu-logo.png HTTP/1.1" 304 179 "http://mychinesemecca.test/" "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Ubuntu Chromium/39.0.2171.65 Chrome/39.0.2171.65 Safari/537.36"

---

### Post by igor32 on 2015-01-22
Any ideas would be helpful. I hope for you.

---

