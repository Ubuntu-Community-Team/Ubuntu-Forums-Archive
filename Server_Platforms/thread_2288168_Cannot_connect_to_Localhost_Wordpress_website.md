---
title: "Cannot connect to Localhost: Wordpress website"
date: 2015-07-24
forum: Server Platforms
---

### Post by Gotlieb on 2015-07-24
Hi Guys,

So I installed a temporary webserver on my laptop (8GB ram and 700HDD) with Ubuntu 14.04 and I had wordpress working fine for two days now, I have made edits already and I do not want to start over, the problem occurred when I tried to fix my phpmyadmin because that failed from the start, after a few unsuccessful attempts, that is when I realized I might sadly made changes and cannot connect to my website anymore or localhost. Please help & thanks!

Gotlieb

---

### Post by Julind on 2015-07-24
Should be a apache problem because Phpmyadmin takes care only for databases, and it should not mess localhost. Try running this to restart the webserver.

```
sudo /etc/init.d/apache2 restart
```

---

### Post by sandyd on 2015-07-24
Moved to *Server Platforms*

---

### Post by cariboo on 2015-07-25
> **Julind said:**
> Should be a apache problem because Phpmyadmin takes care only for databases, and it should not mess localhost. Try running this to restart the webserver.

```
sudo /etc/init.d/apache2 restart
```

That should be:

```
sudo service apache2 restart
```

---

### Post by Gotlieb on 2015-07-25
Hi guys,

Thanks for replying, I did and I got this error back.
Trying to locate the Syntax error did not help either, cannot find the conf file.

Please help

[ATTACH=CONFIG]263368[/ATTACH]

---

### Post by Julind on 2015-07-25
You are better off uninstalling the reinstalling apache since you can't find that .conf file.

First stop the service
```
sudo service apache2 stop
```
Remove everything tha has to do with apache2
```
sudo apt-get purge apache2 apache2-utils apache2.2-bin apache2-common
```
Remove dependencies
```
sudo apt-get autoremove
```

Now run
```
whereis apache2
```
and if you get something like apache2: **/etc/apache2**, run
```
sudo rm -rf /etc/apache2
```

To install it simply run 
```
sudo apt-get update && sudo apt-get install apache2
```

---

### Post by Gotlieb on 2015-07-25
Hi, 

I tried it out. I cannot connect to localhost still. I am stuck, sadly.

---

### Post by Julind on 2015-07-25
Id say, reconfigure phpmyadmin by running
```
sudo dpkg-reconfigure phpmyadmin
```
But firstly back all the databases up, because Im not sure if it will mess the databases up.

If that doesn't fix it, purge remove phpmyadmin and reinstall it again. Don't forget to reload the apache service after all of this.

---

### Post by Gotlieb on 2015-07-26
Hi Guys

I had to start all over again and it is working again, thanks for the efforts and replies.

Cheers

---

