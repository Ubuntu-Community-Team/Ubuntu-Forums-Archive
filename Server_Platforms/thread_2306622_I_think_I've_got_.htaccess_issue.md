---
title: "I think I've got .htaccess issue"
date: 2015-12-17
forum: Server Platforms
---

### Post by Grigoriy on 2015-12-17
Hello!

I run Ubuntu 14.04 and a LAMP stack. I'm having strange issues with my  Joomla site and I suspect that maybe it's because of my errors in  running a web server. Since it's not a Joomla forum, I won't get into  Joomla problems too deep, but in short -- I'm getting a wrong addresses  when I create new menu items (A strange directory "Feeds" appears and I  see just the main Joomla page)

If I recall correctly, when I created my original Joomla site in J 1.5 I  did use .htaccess in my Joomla root and I chose an appropriate option  in Joomla admin panel. Another important point is that I built an  original site in a hosting environment (ie, on a distant server,  probably running PHP 5.3 I would assume). I'm not an expert in Apache,  but I think that I must use a certain directive to enable use of  .htaccess (I think it's disabled by default). I haven't enabled it. The  reason why I even decided to upgrade my Joomla installation from J 1.5  to 2.5 is because I had issues when I tried to add a payment module in  Virtuemart and I thought that maybe the reason was because of  incompatibility of J 1.5 and PHP 5.5 (it's a default PHP version under  Ubuntu 14.04). And though I did successfully an upgrade of Joomla  version from 1.5 to 2.5, after that I couldn't open any of my menu items  (except for the home page). I was getting 404 errors everywhere! And  then I turned off my "Use URL rewriting" option and renamed back  .htaccess to htaccess.txt And after that everything got back to normal  (everything that was already there, not NEW menu items -- I simply  didn't create any new menu items at THAT point in time).

What I'm trying to ask here... Maybe I should just enable .htaccess use  in Apache to avoid those kind of issues? And what's the right way to  achieve that under Ubuntu 14.04 and LAMP?

---

### Post by SeijiSensei on 2015-12-17
Generally if you have to add directives, and you control the server, you should put them in the <Directory> container in the configuration file for the virtual host rather than using .htaccess.  Presumably you have a file in /etc/apache2/sites-available/ that contains the site's configuration.  Add whatever you need there:
```

<VirtualHost *:80>
ServerName  myserver.example.com
Document Root /path/to/the/site
<Directory "/path/to/the/site">
     add directives here
</Directory>
[other stuff]
</VirtualHost>

```

---

### Post by Grigoriy on 2015-12-18
Thanks for your reply!
[TABLE]
[TR]
[TD="class: comment-score"][/TD]
[TD][/TD]
[/TR]
[/TABLE]
I was told that I have to  enable rewriting on Apache by doing this:  sudo a2enmod rewrite  and  then I restarted Apache. That's first... Second... I usually put my Apache  directives into /etc/apache2/apache2.conf
 I did that and it seemed to be  working, though it hasn't solved my issue. At least now I get my user friendly URLs as they should appear and I don't get those silly 404 errors, so that's a start.
In my /etc/apache2/apache2.conf file I changed this

<Directory /var/www/>
    Options Indexes FollowSymLinks
    **AllowOverride None**
    Require all granted
</Directory>

to this:

<Directory /var/www/>
    Options Indexes FollowSymLinks
    **AllowOverride All**
    Require all granted
</Directory>

So what do you think? What about enabling mod rewrite on Apache? If it's a neccessary step, then why did you omit it in your advice?

P.S. My site's root is /var/www/html (I don't understand why it says "Directory /var/www/" or maybe it's the way it should be?).

---

### Post by SeijiSensei on 2015-12-18
Most ordinary sites should not need mod_rewrite at all.  You should be able to resolve most issues with the correct DocumentRoot specification for each virtual host, or maybe an Alias directive to point to directories outside /var/www.

In general, you shouldn't need to change files like apache2.conf at all.  You should read [https://help.ubuntu.com/lts/serverguide/httpd.html](https://help.ubuntu.com/lts/serverguide/httpd.html) if you have not done so already.  We really can't help very much if you don't follow the standard Ubuntu practices described there.

Starting with Apache 2.4, the default website directory is /var/www/html.  On Apache 2.2, it was /var/www.

---

### Post by Grigoriy on 2015-12-18
The problem is solved. It was a Joomla/Virtuemart issue, not really a  web server problem. Had to go to Menu manager in Joomla and press  Rebuild button there to get menu items in order.

---

