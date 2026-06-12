---
title: "Creating virtual server with Webmin&amp;&amp;Apache"
date: 2009-08-28
forum: Server Platforms
---

### Post by iamed18 on 2009-08-28
So I own a domain via 1and1 hosting and I have the server sitting right next to me that the DNS server points to.

I decided that I wanted to have a subdomain, so I set it up with 1and1, and I tried to make a virtual server that would listen on just that address call.  The new subdomain is going to listen on the old directory of the domain I own (/var/www) and the old domain is going to go for /var/www/new.www

I have the subdomain working, but the old domain refuses to just pull files from new.www.

I will post whatever conf files that you need, and would very much appreciate any kind of help/advice.

Also, I have rtorrent, wtorrent, and a scgi port connecting the two.  These files are located in /var/www and is what the new subdomain is pointing to.

Thanks

---

### Post by volkswagner on 2009-08-28
You should post your vhost.config files.  Post any errors in log.

```
cat /var/log/apache2/error.log
```

Did you restart apache2 after making changes? Any errors? 

```
sudo /etc/init.d/apache2 restart
```


When I have set vhosts in Webmin I always select "Default Server", in the Virtual Sever Address section (at the bottom of the first page of the vhost. 

Also Post the output of

```
ls -alt /etc/apache2/sites-enabled
```

---

