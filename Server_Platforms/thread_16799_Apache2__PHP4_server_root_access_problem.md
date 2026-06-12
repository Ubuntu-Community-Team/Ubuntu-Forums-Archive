---
title: "Apache2 / PHP4 server root access problem"
date: 2005-02-23
forum: Server Platforms
---

### Post by ahmedf on 2005-02-23
Hi,

I've installed all the required modules for Apache2 and PHP4. The problem is that when I try to access the server root ([http://servername.com)](http://servername.com)), I get the "Open File" dialog instead of the index.php being executed. But when I try to access [http://servername.com/index.php](http://servername.com/index.php), it works!! How do I fix this?

---

### Post by az on 2005-02-24
You need to change /etc/apache2.apache2.conf

cat /etc/apache2/apache2.conf |grep php
DirectoryIndex index.php index.html index.cgi index.pl index.xhtml
AddType application/x-httpd-php .php
AddType application/x-httpd-php-source .phps

---

### Post by firfin on 2005-02-25
I have a similar problem. Whenever i point the browser to HOST/filename.PHP, it allows me to download the file (save as dialog appears.) I have done the following:
[QUOTE=azz]You need to change /etc/apache2.apache2.conf
AddType application/x-httpd-php .php
AddType application/x-httpd-php-source .phps[/QUOTE]
Any other pointers? :?:

---

### Post by kuam on 2005-02-25
As stated above, make sure you add "index.php" to this line:

DirectoryIndex index.php index.html index.cgi index.pl index.xhtml

Once you save, restart apache for it to take effect.

---

### Post by cpinto on 2005-02-27
[QUOTE=azz]You need to change /etc/apache2.apache2.conf

cat /etc/apache2/apache2.conf |grep php
DirectoryIndex index.php index.html index.cgi index.pl index.xhtml
AddType application/x-httpd-php .php
AddType application/x-httpd-php-source .phps[/QUOTE]

This is often said a solution but it's plain wrong (altough it'll work). 
In Apache2 you have an /etc/apache2/mods-available directory with the modules you may enable for use. Instead of hacking around in the apache2.conf file you may only symlink whatever files you want enabled to the /etc/apache2/mods-enabled directory.

For example, this php FAQ:
% ln -s /etc/apache2/mods-available/php4.load /etc/apache2/mods-enabled/
% ln -s /etc/apache2/mods-available/php4.conf /etc/apache2/mods-enabled/
% invoke-rc.d apache restart

and you're good to go. No apache2.conf voodoo knowledge required :-)

---

### Post by az on 2005-02-27
If the module is not enabled, just changing the conf will not work.  And also, Mr. Smarty Pants, there is a utility called a2enmod to enable modules.  It needs to be run as root and it does just that - create symlinks from mods-enabled to mods-available.

Ex:
sudo a2enmod rewrite



My point was that index.php should precede index.html on the line in the conf.

At least, that is what I had to do to get it to work.  There however must be a slicker answer out there, or it is a bug.

---

### Post by cpinto on 2005-02-28
That's weird, the precedence between index.php and index.html only matters if you have both files in the website's root.
Either way, enabling the php4 modules and restarting apache2 should be more than enough to figure out if php4 supported ([http://whatever-host/index.php](http://whatever-host/index.php)) and the page should be displayed.

---

### Post by firfin on 2005-02-28
[QUOTE=kuam]Once you save, restart apache for it to take effect.[/QUOTE]
> Either way, enabling the php4 modules and restarting apache2 should be more than enough to figure out if php4 supported ([http://whatever-host/index.php](http://whatever-host/index.php)) and the page should be displayed. 

Thanks you guys (and all the other replies of course) a restart of apache was indeed al that was required.  #-o  DOH

---

### Post by stardotstar on 2005-04-29
The sym links worked for this problem for me! But only in getting rid of the save-as dialogue for phpinfo.php when I call it from the /var/www/ root i get 

```
Warning: main(./libraries/grab_globals.lib.php): failed to open stream: No such file or directory in /var/www/phpinfo.php on line 9

Fatal error: main(): Failed opening required './libraries/grab_globals.lib.php' (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/phpinfo.php on line 9
```

but the phpinfo.php that is in the phpmyadmin folder at /usr/share/phpmyadmin and sym linked from /var/www works just fine - and in fact did before I did the "mod-enabled" sym links as shown above!

and in any directory below that i still get save as!!

Can some help me untangle this please?

Best Regards,
*.will

---

