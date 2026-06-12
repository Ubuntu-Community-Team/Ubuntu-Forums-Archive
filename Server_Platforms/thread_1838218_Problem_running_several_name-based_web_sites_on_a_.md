---
title: "Problem running several name-based web sites on a single IP address in apache2"
date: 2011-09-03
forum: Server Platforms
---

### Post by Josep CA on 2011-09-03
Hi, I'm running several name-based web sites on a single IP address in apache2 in order to test them locally. However, now I've installed [EyeOS]("http://en.wikipedia.org/wiki/EyeOS") (an operating system in the cloud) that works as just another website (eg. I type "eyeos" in my browser in order to use it) and I want to access it from another computer in my home network. My httpd.conf looks like this:

```

<VirtualHost *:80>
ServerName localhost1
DocumentRoot /home/josep/Documents/Aceites_Escoda
</VirtualHost>

<VirtualHost *:80>
ServerName localhost2
DocumentRoot /home/josep/Documents/myprimarycolors
</VirtualHost>

<VirtualHost *:80>
ServerName eyeos
DocumentRoot /home/josep/eyeos-2.5
</VirtualHost>

```
I can access all the websites from the server and I can use EyeOS. However when I type my server's IP address in my remote PC I only get the first website (Aceites_Escoda). Any ideas in how to access EyeOS from my remote computer?

Many thanks!

---

### Post by volkswagner on 2011-09-03
although there are some apache mods for running ip based virtual hosts or nameVIRTUAL hosts locally, I don't have any links at the moment.

There a two fairly simple solutions.  You can make your sites more tree like folder structure.  /home/username/www/site1, /home/username/www/site2, /home/username/www/eyeos.  With this make a vhost file named 000-main ( or similiar so apache will serve it first) with DocumentRoot  set to /home/username/www/

Option two would be edit your /etc/hosts file on the workstation so all your server names point to your server ip.  Depending on what OS your workstation is running will determine the hosts file location.

---

### Post by Josep CA on 2011-09-04
> 
There a two fairly simple solutions. You can make your sites more tree like folder structure. /home/username/www/site1, /home/username/www/site2, /home/username/www/eyeos. With this make a vhost file named 000-main ( or similar so apache will serve it first) with DocumentRoot set to /home/username/www/

Option two would be edit your /etc/hosts file on the workstation so all your server names point to your server ip. Depending on what OS your workstation is running will determine the hosts file location. 


Many thanks volkswagner! Option one worked. Just that easy! Option two doesn't work for my workstation running Ubuntu.

> 
although there are some apache mods for running ip based virtual hosts or nameVIRTUAL hosts locally, I don't have any links at the moment.


I intended to make it name-based but if anyone is interested in making it IP-based this is the [link]("http://httpd.apache.org/docs/2.0/vhosts/examples.html#twoips").

---

