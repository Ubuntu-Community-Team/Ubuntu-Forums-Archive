---
title: "[SOLVED] Apache2 - php5 not parsing .php files"
date: 2007-07-23
forum: Server Platforms
---

### Post by ecomber on 2007-07-23
There have been a few threads along these lines, and I have followed all the suggestions without success - when I browse to a .php page I get the file downloading rather than PHP having been called to parse it. It looks like apache2 doesn't think that a.php file is of special importance.

On looking at php5.conf I see ...

:$ cat php5.conf
<IfModule mod_php5.c>
  AddType application/x-httpd-php .php .phtml .php3
  AddType application/x-httpd-php-source .phps
</IfModule>

So, it seem to me that a2 isn't being wised up to .php files, and the reason is there is no mod_php5.c file anywhere on my system.

T his was all installed using tasksel, so I presume it's a coinfiguration problem.

I don't want to hand edit the php5.conf file if I can avoid it in case it breaks some timestamped dependencies but that looks to me to be the problem.

Any views on the above?

Eddie

---

### Post by Gruelius on 2007-07-23
mine worked out of the box, i dont think i have a php5.conf file...

I suggest you move this to server's and security, they will give you much better support. THis area is more hardware issues than serving software.

---

### Post by bapoumba on 2007-07-23
Thread moved to "Servers & Security".

---

### Post by #Reistlehr- on 2007-07-23
if it happens surfing the internet, its the webserver, and nothing you can do. if it's a local LAMP server you made, then i suggest you read up on Apache, and the httpd.conf config file.

---

### Post by jtc on 2007-07-23
Sure the PHP5-module is enabled? Do you see symlinks to php5.conf and php5.load in /etc/apache2/mods-enabled/ ?

By the way, there isn't supposed any file named mod_php5.c

---

### Post by ecomber on 2007-07-23
Well, it works now - after uninstall and reinstall of LAMP, though I'm mystified as to why it should, although there appear to be more files in mods-enabled than previousy (sorry to be so vague).

There are funny things going on with the LAMP package IMO.

Thanks for the advice all 'round.

Eddie.

---

