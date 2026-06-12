---
title: "mysql php"
date: 2005-08-18
forum: Server Platforms
---

### Post by mrweirdo on 2005-08-18
Ok I have this problem with mysql in php not working. I have installed everything from Synaptic including php4 and php4-mysql. However trying to run any simple script that conects to mysql returns:
Fatal error: Call to undefined function: mysql_connect() in /home/www/check.php on line 2

here is the actualy script except username password etc changed:
[PHP]mysql_connect("hostname", "username", "password");
mysql_select_db("database");
$sql = "SELECT email FROM `users`";
$result = mysql_query($sql);
while ($rows = mysql_fetch_array($result)){
		echo $rows[email];
}
[/PHP] 


So I go to check phpinfo and look at the configure comand and find that the problem stems from  '--without-mysql' being isued in the configuration even though the php4-mysql package is installed. Anyone have any ideas how I can fix this?

---

### Post by LordHunter317 on 2005-08-18
Is the mysql section showing in phpinfo()?  If so, then no, everything is ok.

Any that error means there is a problem in **your** script.  test() ain't any function I've ever heard of.

---

### Post by deuce868 on 2005-08-18
[QUOTE=LordHunter317]Is the mysql section showing in phpinfo()?  If so, then no, everything is ok.

Any that error means there is a problem in **your** script.  test() ain't any function I've ever heard of.[/QUOTE]

Exactly, it sounds more like you called test() and never defined a function test () {} anywhere.

---

### Post by LordHunter317 on 2005-08-18
The next correct response was, "Do they speak english in test()?" ;)

---

### Post by mrweirdo on 2005-08-19
oops that was suposed to be mysql_connect() instead of test() I'm not sure why i typed that but I was half asleep at the time. Ill edit my first post to change it. Anyways no the mysql section does not show in phpinfo() and the configure comand from within phpinfo shows php without mysql support.

---

### Post by Velox Letum on 2005-08-19
[QUOTE=mrweirdo]oops that was suposed to be mysql_connect() instead of test() I'm not sure why i typed that but I was half asleep at the time. Ill edit my first post to change it. Anyways no the mysql section does not show in phpinfo() and the configure comand from within phpinfo shows php without mysql support.[/QUOTE]
 You'll need to compile in MySQL support to PHP then for it to work, as its a module that can be left out. Myself I don't trust .deb packages for things such as PHP, as I like to know exactly what goes where, and what is compiled into it.

---

### Post by deuce868 on 2005-08-19
I've always had great luck with php debs. I use the Sarge debs on one machine and the dotdeb php5 on another. I've even setup a test machine at home with the php5 debs from unstable. 

Anyway, make sure that you have mysql loaded in the php.ini file. If you installed php4-mysql then it should be, but maybe something went wrong. 

extension=mysql.so

---

### Post by lee_connell on 2005-08-19
i had same problem, try dpkg-reconfigure php4-mysql.

i actually purged all my settings and it over again but that may not be neccessary for you.

---

### Post by mrweirdo on 2005-08-19
[QUOTE=lee_connell]i had same problem, try dpkg-reconfigure php4-mysql.

i actually purged all my settings and it over again but that may not be neccessary for you.[/QUOTE]

Ok well the good news is that did it for me since the module is now showing up in phpinfo() even though the config line still says without mysql.  now for some reason my same php script doesnt print anything out when its run. I'll do some checking to make sure its geting data from a mysql database though. It might not be able to conect to the remote server I have a test database setup on atm and might not be printing an unable to conect error.

If it still doesnt work I'm guesing I could try compiling php from the source. Only problem I have with doing that I'm not exactly sure what all the paths should be in the ./configure comand.

---

### Post by Velox Letum on 2005-08-20
Most of the required packages can be found with whereis. I'll paste my include line from my server (warning, I put tons of modules into mine)

From phpinfo()

./configure --with-apxs=/usr/local/apache/bin/apxs --with-xml --enable-bcmath --enable-calendar --with-curl --with-dom --with-dom-xslt --with-dom-exslt --with-swf=/usr/local/flash --enable-ftp --with-gd --with-jpeg-dir=/usr/local --with-png-dir=/usr --with-xpm-dir=/usr/X11R6 --with-gettext --with-imap --with-imap-ssl --with-kerberos --enable-mbstring --enable-mbstr-enc-trans --enable-mbregex --with-mcrypt --with-mhash --with-ming=../ming-0.2a --enable-magic-quotes --with-mysql --with-openssl --enable-discard-path --with-pear --with-pspell --enable-xslt --with-xslt-sablot --enable-sockets --enable-track-vars --with-ttf --with-freetype-dir=/usr --enable-gd-native-ttf --enable-versioning --with-xmlrpc --with-zip --with-zlib

The most important ones in my opinion are zlib, magic-quotes, mbregex, mcrypt, mhash, curl, GD (love GD, and its needs JPEG and PNG libraries), mysql, openssl, and xmlrpc.

---

### Post by mrweirdo on 2005-08-20
Ok it works now thanks for all the help everyone :)

---

### Post by LordHunter317 on 2005-08-21
[QUOTE=Velox Letum] Myself I don't trust .deb packages for things such as PHP, as I like to know exactly what goes where, and what is compiled into it.[/QUOTE]Now that's an absolute silly, wrong, and unfounded belief.

You can figure that out with .debs, no problem.  THat's why phpinfo() exists.

---

### Post by Velox Letum on 2005-08-21
[QUOTE=LordHunter317]Now that's an absolute silly, wrong, and unfounded belief.

You can figure that out with .debs, no problem.  THat's why phpinfo() exists.[/QUOTE]
 But I also like it compiled just to my exact specifications. Thats why I compile most of my server software (MySQL included).

---

### Post by LordHunter317 on 2005-08-21
That just makes no sense.  What do you think you're gaining from this?

---

### Post by MDoten on 2005-09-22
Hi,

I'm having the same problem but I'm using php5, not php4. php5 runs fine on my apache server and I have php5-mysql installed. When I do phpinfo(), there is no mention of mysql in there at all. I tried to reconfigure it, using:

sudo dpkg-reconfigure php5-mysql

but that didn't work. I'm not really sure what else to try. Any help would be greatly appreciated.

---

### Post by blueshrike on 2005-10-03
I am having the same problem in 5.04

I am using the same php.ini in both the cli and apache2 directories (/etc/php4/*).  When I run php -m, I see that mysql gets loaded.

Whe I do phpinfo() i see the mysql settings however the configure command says:
[INDENT]'../configure' '--prefix=/usr' '--with-apxs2=/usr/bin/apxs2' '--with-config-file-path=/etc/php4/apache2' '--enable-memory-limit' '--disable-debug' '--with-regex=php' '--disable-rpath' '--disable-static' '--with-pic' '--with-layout=GNU' '--with-pear=/usr/share/php' '--enable-calendar' '--enable-sysvsem' '--enable-sysvshm' '--enable-sysvmsg' '--enable-track-vars' '--enable-trans-sid' '--enable-bcmath' '--with-bz2' '--enable-ctype' '--with-db4' '--with-iconv' '--enable-exif' '--enable-filepro' '--enable-ftp' '--with-gettext' '--enable-mbstring' '--with-pcre-regex=/usr' '--enable-shmop' '--enable-sockets' '--enable-wddx' '--disable-xml' '--with-expat-dir=/usr' '--with-xmlrpc' '--enable-yp' '--with-zlib' '--without-pgsql' '--with-kerberos=/usr' '--with-openssl=/usr' '--enable-dbx' '--with-mime-magic=/usr/share/misc/file/magic.mime' '--with-exec-dir=/usr/lib/php4/libexec' '--without-mm' **'--without-mysql' **'--without-sybase-ct'[/INDENT]

I had php log statup errors and there are none.

I have tried dpkg-reconfigure php4-mysql.  I have manually added extension=mysql.so to php.ini.  And I have reinstalled all related packages (from mysql-common) on up.

I am trying to install ampache.  In the create db phase, the install script ends on the mysql_pconnect with no error message.  All I see is a blank screen and no database gets created.

I am at wits end.  Between this and not being able to use my KVM switch I almost feel like giving up and going back to debian stable (where I had everything working).  Ok Ok I'm not that frustrated.

Can anyone suggest how I might fix this?  PLEASE!  

Bear in mind that I am relatively new to both linux and MySql.  (Sadly I work in a microsoft shop).  So you might have to provide a little more detail than usual.

Edit: I am using php4.4.3.10, apache2 and mysql 4.0.23.3

---

### Post by Glut on 2005-10-04
[QUOTE=Velox Letum]But I also like it compiled just to my exact specifications. Thats why I compile most of my server software (MySQL included).[/QUOTE][QUOTE=LordHunter317]That just makes no sense. What do you think you're gaining from this?[/QUOTE]
Ahh, a Gentoo style user. Arguing will get you nowhere.

---

### Post by FortyAcre on 2005-10-06
I'm having the same problems.   I followed all the directions in the Ubuntu Guide for setting up Apache/PHP/mySQL, and when I run phpInfo() I see the -without-mySQL listed and no MySQL section in the output.

I have completely removed all the packages and reinstalled them.  I've done the dpkg with php4-mysql, and go through all the prompts with no success.  My PHP.ini file, has the mysql.so extension enabled as well.

All of my install attempts have been done via packages, not source.    I have verified that Apache is working, PHP is working, and mySQL is working.  Just not all together.

Out of frustration, I have installed these products via xampp, but I'd like to know how to resolve this issue using the recommended configuration.

I've searched the forums extensively and believe I've tried the typically recommended fixes.  What's odd is that these fixes seem to work for some people, but not everyone.  

Any ideas from the experts out there?

-Craig

---

### Post by airtonix on 2006-05-10
Ahh, a Gentoo style user. Arguing will get you nowhere.

lol.....exakery.

he compiles it for same reason he uses linux instead of windows.....control and transparency.

---

