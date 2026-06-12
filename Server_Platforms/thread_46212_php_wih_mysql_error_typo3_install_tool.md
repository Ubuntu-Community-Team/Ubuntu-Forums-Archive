---
title: "php wih mysql error typo3 install tool"
date: 2005-07-03
forum: Server Platforms
---

### Post by miss tina on 2005-07-03
i would like typo3 up and running but i havea mysl problem....
typo3 install tool says:
[COLOR=Olive]Check database:
MySQL not available
PHP does not feature MySQL support (which is pretty unusual).[/COLOR]

ps. php4-mysql is installed...
pps. apache is up and running mysql is up and running

---

### Post by jarrett.wold on 2005-07-03
Are you using Synaptic, or compiling from source?

---

### Post by miss tina on 2005-07-04
i did the apache how to and mysql how to at:
[apache](http://www.frankandjacq.com/ubuntuguide/5.04/index.html#installapachehttpserver)
for typo3 i did:
[typo3](http://typo3.sunsite.dk/software/debian/) but i chanched it to 3.7.1 cause aptget used 3.5...

ps Mambo allso didn't w PHP version >= 4.1.0  	 Yes
mambo conftool says:  
  - [COLOR=Olive]zlib compression support 	Available
  - XML support 	              Available
  - MySQL support 	            Unavailable
configuration.php 	            riteable
Session save path 	           /var/lib/php4, Writeable
[/COLOR]

---

### Post by miss tina on 2005-07-04
this is my php info:
[COLOR=Olive]PHP Version 4.3.10-10ubuntu4

System 	Linux ubuntu 2.6.10-5-686 #1 Fri Jun 24 17:33:34 UTC 2005 i686
Build Date 	Apr 1 2005 14:09:30
Configure Command 	'../configure' '--prefix=/usr' '--with-apxs2=/usr/bin/apxs2' '--with-config-file-path=/etc/php4/apache2' '--enable-memory-limit' '--disable-debug' '--with-regex=php' '--disable-rpath' '--disable-static' '--with-pic' '--with-layout=GNU' '--with-pear=/usr/share/php' '--enable-calendar' '--enable-sysvsem' '--enable-sysvshm' '--enable-sysvmsg' '--enable-track-vars' '--enable-trans-sid' '--enable-bcmath' '--with-bz2' '--enable-ctype' '--with-db4' '--with-iconv' '--enable-exif' '--enable-filepro' '--enable-ftp' '--with-gettext' '--enable-mbstring' '--with-pcre-regex=/usr' '--enable-shmop' '--enable-sockets' '--enable-wddx' '--disable-xml' '--with-expat-dir=/usr' '--with-xmlrpc' '--enable-yp' '--with-zlib' '--without-pgsql' '--with-kerberos=/usr' '--with-openssl=/usr' '--enable-dbx' '--with-mime-magic=/usr/share/misc/file/magic.mime' '--with-exec-dir=/usr/lib/php4/libexec' '--without-mm' [COLOR=Red]'--without-mysql' [/COLOR]'--without-sybase-ct'[/COLOR]

how to remove the [COLOR=Red]'--without-mysql' [/COLOR], do i have to recompile it? what configure command should i use and do i have to dwnl the source? and compile it myself, or can i reconfigure the php4???

---

### Post by miss tina on 2005-07-04
ok stupid me i had to edit php.ini so it loads mysql.so :roll:

---

