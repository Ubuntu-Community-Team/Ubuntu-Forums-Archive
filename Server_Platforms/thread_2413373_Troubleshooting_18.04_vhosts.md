---
title: "Troubleshooting 18.04 vhosts"
date: 2019-02-24
forum: Server Platforms
---

### Post by Drone4four on 2019-02-24
I’m troubleshooting three vhosts on my 18.04 Droplet on DigitalOcean for my basic, static HTML websites. I've set up similar vhosts the past. I'm not sure what is different this time. Perhaps I am overlooking something very trivial this time.

As resources so far I’ve been primarily using “[How To Install the Apache Web Server on Ubuntu 18.04]("https://www.digitalocean.com/community/tutorials/how-to-install-the-apache-web-server-on-ubuntu-18-04")”. I’ve followed this guide closely while being extremely mindful by using all my custom variables like my domain names through out instead of the author's stock ‘example.com’ (and other variables).

I encountered some issues with the apache2ctl configtest failing and with Apache being unable to qualify the DomainName. To overcome this issue, I relied on an AskUbuntu question called [Apache error “Could not reliably determine the server's fully qualified domain name”]("https://askubuntu.com/questions/256013/apache-error-could-not-reliably-determine-the-servers-fully-qualified-domain-n"). Specifically, [this AskUbuntu answer]("https://askubuntu.com/a/448403/737660") by **empugandring** is what resolved the issue for me.  The configtest now passes with “Syntax OK” and Apache loads and reloads without the previous traceback or any traceback.  No tracebacks are good news, right?

Here is one of my three vhosts: [https://angeles4four.info/](https://angeles4four.info/) It reads: "This site can’t be reached".

The strange thing is that if you navigate to my ip address - -  [159.89.124.104 ](159.89.124.104) - - my index.html renders perfectly. So something is set up correctly meanwhile something else isn’t.

Here is the Apache configuration file for this vhost:
```
/etc/apache2/sites-available$ sudo cat angeles4four.info.conf 
<VirtualHost *:80>
    ServerAdmin <user>@gmail.com
    ServerName angeles4four.info
    ServerAlias www.angeles4four.info
    DocumentRoot /var/www/angeles4four.info/html
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```

Here are the contents of my html directory with user and group permissions showing:

```
/var/www/angeles4four.info/html$ ls -la
total 12
drwxr-xr-x 2 <user> <group> 4096 Feb 25 03:01 .
drwxr-xr-x 3 root   root   4096 Feb 24 02:15 ..
-rw-rw-r-- 1 <user> <group>  23 Feb 25 01:44 index.html
```

The content of index.html is simply: “ANGELES 4 FOUR / DRONE 4 FOUR vhost test”

Here are my DNS records showing on my DigitalOcean dashboard: [https://i.imgur.com/aoD4shD.jpg](https://i.imgur.com/aoD4shD.jpg)

Is there any other information I could provide to help you people better help me?

---

### Post by volkswagner on 2019-02-25
When I navigate to your domain, I get a web page that displays:
```
ANGELES 4 FOUR / DRONE 4 FOUR vhost test
```

Perhaps you have a local DNS issue, or you have some override in your 
test machine's /etc/host file.

On your workstation, do:
```
nslookup angeles4four.info
```

---

### Post by Drone4four on 2019-02-26
Thanks **@Agovolkswagner**. You are right it is working now. The problem was I was previously using [http**s**://angeles4four.info](http**s**://angeles4four.info) when I should have been using [http://angeles4four.info](http://angeles4four.info). I was attempting to access my website as if ssl certificates were set up and enabled. All three are accessible via regular http as they should be.

I knew it was something trivial!

---

