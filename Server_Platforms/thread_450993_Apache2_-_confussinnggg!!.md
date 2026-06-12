---
title: "Apache2 - confussinnggg!!"
date: 2007-05-21
forum: Server Platforms
---

### Post by macmatt on 2007-05-21
Hey chaps!.

Just installed feisty server edition... with LAMP (standalone version)...

HOW oh HOW do I configure my "DocumentRoot" to point to a folder in my /home/apache (apache is my login name on this server box!).

CONFUSING!!. Apache 1.3 didn't give me all this grief... WHY is it so confusing?. Either call me stupid, or help me see where I am slipping up, because I am LOSSST!!!. In apache 1.3 I just edited "httpd.conf" - SIMPLE!.

Thanks chaps - all your time is very much appreciated indeed! :)

[PS] no geek speak please - SIMPLE laymans terms, thanks.

---

### Post by mbradlcu on 2007-05-22
I'm with ya,, create a file in /etc/apache2/conf.d with the below contents (any name for the config file will do),, 

Alias /BestSiteEver /home/apache
<Directory /home/apache>
  Options FollowSymLinks
  AllowOverride All
  DirectoryIndex index.php
</Directory>

you'll have to restart apache2 for the changes to take effect.
let me know if you have any questions about this.

---

### Post by MJN on 2007-05-22
Do it properly!

You site config should now be in /etc/apache2/sites-available/ (there'll be a default file in there already - use that). You then enable this site (config) with **sudo as2ensite** where it will offer you a choice of sites.

Check the archives out (sites-available would be a good starting string) and check out the README in /etc/apache2/

Mathew

---

### Post by macmatt on 2007-05-23
> **mbradlcu said:**
> I'm with ya,, create a file in /etc/apache2/conf.d with the below contents (any name for the config file will do),, 

Alias /BestSiteEver /home/apache
<Directory /home/apache>
  Options FollowSymLinks
  AllowOverride All
  DirectoryIndex index.php
</Directory>

you'll have to restart apache2 for the changes to take effect.
let me know if you have any questions about this.

Sounds.. uhmmm.. wrong, in a word!. Thanks all the same for trying.

There is a file "default" which seems to contain the line "DocumentRoot" and I am going to try that out.

Remember guys, it is APACHE 2.2 *not* 1.x !

---

### Post by MJN on 2007-05-23
Did you miss my post?

---

