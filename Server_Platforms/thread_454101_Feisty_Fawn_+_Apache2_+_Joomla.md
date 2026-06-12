---
title: "Feisty Fawn + Apache2 + Joomla"
date: 2007-05-25
forum: Server Platforms
---

### Post by dimmanramone on 2007-05-25
Hi to all,

yesterady i installed lamp server on my feisty fawn, and decided to install joomla also.
The installation of the lamp server and joomla went ok...

but my problem is that i cannot make the webpage work on the internet and locally.

I've made an virtual server for my dyndns exaple.com in sites-available and sites-enable with the next configuration:

<VirtualHost example.com>
ServerAdmin webmaster@localhost
ServerName example.com
ServerAlias exaple.com
DocumentRoot /var/www/joomla
</VirtualHost>

then i changed in joomlas configuration.php the live_site configuration from [http://localhost/joomla](http://localhost/joomla) first to [http://example.com](http://example.com) and was working locally but not over the internet, over the internet i was seeing in my browser 3 directories(apache,phpmyadmin,joomla) and then i changed it in [http://example.com/joomla](http://example.com/joomla) and it was working over the internet but in [http://example.com/joomla](http://example.com/joomla) and not [http://example.com](http://example.com) like i want and locally i could see the webpage but only the text :S

any ideas?
do i have to change something in my default virtual hosts file?

/dimman

---

### Post by turinglabs on 2007-05-25
I think your virtual host is configured wrong. Try something like this:

<VirtualHost *>
ServerAdmin webmaster@localhost
ServerName hostname.example.com
ServerAlias example.com
DocumentRoot /var/www/joomla
</VirtualHost>

The 'ServerName' should generally be a fully-qualified name, so replace 'hostname' with whatever your hostname is. Then [http://hostname.example.com](http://hostname.example.com) and [http://example.com](http://example.com) should both work.

---

