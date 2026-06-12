---
title: "php5-cgi"
date: 2006-11-17
forum: Server Platforms
---

### Post by SomeGuy on 2006-11-17
hey
i have php4 module setup on apache2
and basicly what i want to do is setup php5-cgi to execute .php files in say /var/www/php5

after installing php5-cgi and not knowing how to invoke cgi scripts or where to put them or which file extensions etc. i googled around for some turtorials, i found one about setting up php-cgi along side php module but it was out of date for edgy so the configuration didnt help me much

after googling around and messing with apache2.conf i was able to get cgi to exeute scripts but they didnt seem to be working with php interprter
ie
ScriptAlias /cgi-bin/ /var/www/php5/
<Directory "/var/www/php5">
AllowOverride None
Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
AddHandler cgi-script .php .cgi .pl .py
Order allow,deny
Allow from all
</Directory>

would just give me the "premature end of headers" problem
php-cgi automatily adds headers but just to make sure i tried this script
<?php
header("Content-Type: text/html\n\n");
echo 'hihi';
?>
so i dont knw wat it is doing

it would be very usefull to run php5 along side php4

---

### Post by adamkane on 2006-11-17
Visit here for the best info.
[http://httpd.apache.org/docs/](http://httpd.apache.org/docs/)

Unfortunately there's no howto for this one. I got CGI working once, but failed to take notes. If you get it working, please share.

I don't think there is anything special about Edgy. You will have issues trying to install PHP4 and PHP5 together. Not a good idea. Get one or the other working first, then try them together if you are daring (ahhchoo-crazy!).

---

### Post by SomeGuy on 2006-11-18
php4 as module works fine
ive ran php4+5 in the past but only thru using both as modules and installing apache1x and 2x
i supose that solution wouldnt matter to much for a developtment meachine as it wouldnt really effect my resources or nething

but i have no idea how to get php cgi working by itself at all

---

### Post by adamkane on 2006-11-18
This howto seems to have the relevant info:
[http://www.howtoforge.com/ubuntu6.06_dtc_isp_server](http://www.howtoforge.com/ubuntu6.06_dtc_isp_server)

---

### Post by SomeGuy on 2006-11-27
ok after reading what little i could find on php-cgi i decided to give up

i am now just running apache1 & 2 w/ php 4 n 5 as modules

and seeming as it WORKS i am happy :)

---

