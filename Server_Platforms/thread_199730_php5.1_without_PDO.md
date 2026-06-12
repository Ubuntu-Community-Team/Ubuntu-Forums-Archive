---
title: "php5.1 without PDO????"
date: 2006-06-19
forum: Server Platforms
---

### Post by deuce868 on 2006-06-19
I am setting up a new desktop for web dev with kubuntu 6.06. I've installed the php 5.1 packages and I'm suprised that PDO is not in the package. I thought PDO was built in as of 5.1? Am I mistaken here? Is there something goofy with the ubuntu packages?

I've tried to just install with pecl, but that bombs on me with:
> pecl install PDO
downloading PDO-1.0.3.tgz ...
Starting to download PDO-1.0.3.tgz (52,613 bytes)
.............done: 52,613 bytes
12 source files, building
running: phpize
sh: phpize: command not found
ERROR: `phpize' failed


So this fails and I can't figure out what the missing phpize command is. 

Thanks for the help.

---

### Post by deuce868 on 2006-06-19
Ok, some progress. After installing php5-dev, make, libmysqlclient-dev and some misc packages I have managed to get pecl to install pdo. Now I am trying to install the msyql driver for pdo and I am getting the following:

> 
configure: error:
You've configured extension pdo_mysql, which depends on extension pdo,
but you've either not enabled pdo, or have disabled it.

ERROR: `/tmp/tmp3Ab2KY/PDO_MYSQL-1.0.2/configure' failed


Of course what's odd is that I do have PDO enabled and in phpinfo() I can see pdo = enabled with drivers = no value. 

Any help appreciated. If I can't get this worked out I might just remove the ubuntu packages and try to pull the backports packages I run on my debian stable server instead.

---

### Post by nihilocrat on 2006-06-19
This probably won't help, seeing as how phpinfo() recognizes it, but make sure PDO has an entry in your php.ini file. It will probably show up in a line like "extension=pdo.so"

You should also check your PHP logs (or apache logs, if you're running php as an apache module) to see if PHP has complained about anything on startup.

---

### Post by deuce868 on 2006-06-19
[QUOTE=nihilocrat]This probably won't help, seeing as how phpinfo() recognizes it, but make sure PDO has an entry in your php.ini file. It will probably show up in a line like "extension=pdo.so"

You should also check your PHP logs (or apache logs, if you're running php as an apache module) to see if PHP has complained about anything on startup.[/QUOTE]

I did check phpinfo, but you gave me the idea to also check that the extension is loaded in the cli version of the php.ini since I think that is what pecl is using. Unfortunately once I added it I still get the same error. 

Thanks for the idea though.

---

### Post by aschlapsi on 2006-06-27
It seems that this is a bug with PHP 5.1.2. Have a look at [http://pecl.php.net/bugs/bug.php?id=6545](http://pecl.php.net/bugs/bug.php?id=6545)

This hack worked for me (found at [http://pecl.php.net/bugs/bug.php?id=6117):](http://pecl.php.net/bugs/bug.php?id=6117):)
> 
find PHP_ADD_EXTENSION_DEP inside /usr/lib/php5/build/acinclude.m4 (or
wherever yours is located)

and REMOVE this snippet from that function:
  if test "x$is_it_shared" = "x" && test "x$3" != "xtrue"; then
    AC_MSG_ERROR([
You've configured extension $1, which depends on extension $2,
but you've either not enabled $2, or have disabled it.
])
  fi

---

### Post by deuce868 on 2006-06-27
Yea, I found that bug. I posted a bug with Ubuntu. DotDeb has a php5-pdo package so maybe they can borrow some stuff. 

In the meantime I performed the action in that bug that said to do:
> 
However, if the user "re-installs" PDO via
 
pecl install --register-only PDO
 
this will fix the problem, and then "pecl install pdo_mysql" will work
just fine.


and that got me up and running ok.

---

### Post by davout on 2006-06-28
hmm...
that didn't work for me, it keeps complaining about pdo being neither installed nor enabled....
Even after trying to get it to register only...
```
# pecl install --register-only pdo
Skipping package "pecl/PDO", already installed as version 1.0.3
No valid packages found
install failed
#
```
Edit: The above hack posted by aschlapsi (bless ya) worked for me though :-)

---

### Post by deuce868 on 2006-06-28
[QUOTE=davout]hmm...
that didn't work for me, it keeps complaining about pdo being neither installed nor enabled....
Even after trying to get it to register only...
```
# pecl install --register-only pdo
Skipping package "pecl/PDO", already installed as version 1.0.3
No valid packages found
install failed
#
```
Edit: The above hack posted by aschlapsi (bless ya) worked for me though :-)[/QUOTE]

Yea, it's supposed to say it failed. Somehow that register only puts something somewhere that then lets the pdo_mysql driver install. 

So the steps are
1) Install pdo with pecl install pdo
2) rerun the pdo install with the --register-only and get the failed message
3) pecl install pdo_mysql

---

### Post by pressureman on 2006-06-29
It's annoying that Debian still has not created PDO packages for PHP5, even though it was requested 160 days ago (according to bugs.debian.org). They only just recently packaged PHP 5.1.4, despite 5.1.2 having a critical security flaw for about two months before that. I hope that PDO makes it into sid, and subsequently edgy eft, before October.

In the meantime, there is at least an alternate source for PHP5 on Debian and Ubuntu (other than dotdeb.org). Beware that these packages are slightly different (ie, broken down into more modular pieces) than the Debian/Ubuntu packaging. Just add one of these to your APT sources:

```

# PHP5.1 for Ubuntu dapper
deb http://people.debian.org/~dexter php5.1 dapper
deb-src http://people.debian.org/~dexter php5.1 dapper

# PHP5.1 for Ubuntu breezy
deb http://people.debian.org/~dexter php5.1 breezy
deb-src http://people.debian.org/~dexter php5.1 breezy

# PHP5.1 for Ubuntu hoary
deb http://people.debian.org/~dexter php5.1 hoary
deb-src http://people.debian.org/~dexter php5.1 hoary

```

---

### Post by hemna on 2008-02-05
It seems like ubuntu STILL has no PHP5 pdo support.  What gives?  PDO has been apart of PHP for quite some time now.  I just installed php5-common php5-dev php5 php-pear and no pdo support at all.

php -m gives
```
[PHP Modules]
bcmath
bz2
calendar
ctype
date
dba
dom
exif
filter
ftp
gettext
hash
iconv
json
libxml
mbstring
mime_magic
ncurses
openssl
pcntl
pcre
posix
Reflection
session
shmop
SimpleXML
soap
sockets
SPL
standard
sysvmsg
sysvsem
sysvshm
tokenizer
wddx
xml
xmlreader
xmlwriter
zip
zlib

[Zend Modules]

```

Why isn't PDO support enabled in the php5 package for gutsy?

---

### Post by deuce868 on 2008-02-05
It's in there. Check phpinfo()

Our whole business is running PHP5 with PDO (and the Doctrine ORM) on top of Gutsy on the server farm. 

Perhaps it's not part of the php5-cli build? Try the apache module and check it with phpinfo()

---

