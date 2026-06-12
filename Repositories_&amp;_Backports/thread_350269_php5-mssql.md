---
title: "php5-mssql"
date: 2007-01-31
forum: Repositories &amp; Backports
---

### Post by hogman23 on 2007-01-31
I upgraded a server to Edgy and had some problems with php.  I need php5-mssql installed but it tells me "Package php5-mssql is not available, but is referred to by another package.".  How can I tell what package it is referred to now?
Thanks

---

### Post by az on 2007-01-31
There never has been a php5-mssql package.

---

### Post by hogman23 on 2007-01-31
> **azz said:**
> There never has been a php5-mssql package.

This is the output from 'dpkg -l php5-mssql' on my dapper server:

ii  php5-mssql                             5.1.2-1ubuntu3.4                       MSSQL module for php5

This is the output from the same on my Edgy Server:

pn  php5-mssql                             <none>                                 (no description available)


It is installed on my Dapper server, but what package do you use to mssql on Edgy???

---

### Post by hogman23 on 2007-01-31
This is strange, it looks like they combined the php5-mssql install with something else, but I can't figure out what.

---

### Post by hogman23 on 2007-01-31
Ok, here is the fix to get php5-mssql installed:

Install the Debian Package tools:
```
apt-get install build-essential debhelper
```

Then, download the PHP5 Source Files:
```
apt-get source php5
```

Get the dependencies for building PHP5:
```
apt-get build-dep php5
```

cd to the directory php5-5.1.2/debian and vi the file modulelist.  Insert a line above the one that says:
```
mysql MySQL
```
with the contents
```
mssql MSSQL
```

Next, edit the file rules and search for ```
–with-mysql=shared,/usr
```

Insert the following above it:
```
–with-mssql=shared,/usr
```

Make sure not to forget the backslash on the end.Now, we must edit the “control” file in the same directory. Add this to the end of the file:
```

Package: php5-mssql
Architecture: any
Depends: ${shlibs:Depends}, ${misc:Depends}, ${php:Depends}, php5-common (= ${Source-Version})
Description: MSSQL module for php5
 This package provides a module for MSSQL using FreeTDS.
 .
 PHP5 is an HTML-embedded scripting language. Much of its syntax is borrowed
 from C, Java and Perl with a couple of unique PHP-specific features thrown
 in. The goal of the language is to allow web developers to write
 dynamically generated pages quickly.
```

Move up a directory:
```
cd ..
```

Now run:
```
dpkg-buildpackage
```

This will compile PHP5 and create the debs in the parent directory.  This process takes a while, so relax.

When that is finished, cd to the parent directory and you will see your deb files.

Now, to install php5-mssql:
```
dpkg -i php5-mssql_5.1.6-1ubuntu2.1_i386.deb
```

The majority of the information from this post came from the following URL:
[http://panthar.org/2006/06/15/php-with-mssql-on-ubuntu-606/]("http://panthar.org/2006/06/15/php-with-mssql-on-ubuntu-606/")

---

### Post by az on 2007-01-31
Why is that dissabled in the source?  Are there licencing issues?

---

### Post by hogman23 on 2007-01-31
I'm not sure if it's a bug or what, but we had no problems installing it when the server was Dapper.  When we did an in-place upgrade to Edgy, the package wasn't available anymore.  So either, the package isn't there in the edgy repos, or there is another package that installs php5-mssql, but I couldn't find it if there is.

---

### Post by hogman23 on 2007-01-31
Oh yeah, another "note to self", Don't compile PHP5 from the server, because for some reason it uninstalls PHP5 from the server when you do that and you have to go back and reinstall everything.  Also, when PHP5 get's uninstalled, or course it removes PHP5 from mods-enabled in Apache2.

That took me 10 minutes to figure out...DUH!

---

### Post by az on 2007-01-31
> **hogman23 said:**
> So either, the package isn't there in the edgy repos, or there is another package that installs php5-mssql, but I couldn't find it if there is.

There is no php5-mssql package in any release of Ubuntu.

---

### Post by hogman23 on 2007-01-31
> **azz said:**
> There is no php5-mssql package in any release of Ubuntu.

Hmm, I wish I knew what installed it on the old server then, that would have saved me a bunch of work.

---

### Post by hogman23 on 2007-02-27
Problem has been reported as a bug...We'll see what happens, maybe they will at least give an answer as to why it isn't available.

---

### Post by silkstorm on 2007-04-03
> **hogman23 said:**
> Ok, here is the fix to get php5-mssql installed:

...

This worked flawlessly on the latest Ubuntu feisty.  Thank you!  I also would love to see php5-mssql in the Ubuntu distibution.

---

### Post by dim_par on 2007-04-21
php5-source does not compile in feisty.
These are the errors before the compilation stops

ln: creating symbolic link `debian/php5-imap/usr/share/doc/php5-imap' to `php5-common': No such file or directory
ln: creating symbolic link `debian/php5-interbase/usr/share/doc/php5-interbase' to `php5-common': No such file or directory
ln: creating symbolic link `debian/php5-mcrypt/usr/share/doc/php5-mcrypt' to `php5-common': No such file or directory
ln: creating symbolic link `debian/php5-xsl/usr/share/doc/php5-xsl' to `php5-common': No such file or directory
make: *** [binary-arch] Error 1


Any help please?

---

### Post by dim_par on 2007-04-23
False alarm!
I forgot to leave a blank line before inserting to the debian/control file.
Thanks anyway

---

### Post by hogman23 on 2007-05-22
Update:  They have reviewed the complaint that several of us have voiced in the bug that we reported and are supposed to be putting the php5-mssql package back in the repository.  Who knows when this will happen, but they are supposed to be working on it.
:D

---

### Post by ram.coelho on 2007-05-29
Does anyone have this .deb binary ready to dpkg -i? It would be nice to have the url. I could mirror it and post the new location back here and start to spread it around.

---

### Post by mgranado on 2007-09-21
Ok, i tried this, and worked fine.
sudo apt-get install php5-sysbase

this package looks like to be what everyone here is looking for....

Hope I could help

---

### Post by diggity on 2007-09-21
Just so there's no confusion, the correct package is** php5-sybase**
you will need to use the sybase functions instead of the mssql functions in your php code.

---

### Post by mgranado on 2007-09-23
No just that,  if you take a look in the description you gonna see 

    . This package provides a module for Sybase and Microsoft SQL Server database connections directly from PHP scripts.

so all the mssql functions are there

---

### Post by jolmash on 2008-04-18
Everything works FIIINE!!! Thanks!!!!!

---

### Post by bprof on 2008-04-23
I've tried the steps mentioned and I was able to connect but I can't query the DB, every time I try to run a query I'm getting this warning: 

Warning: mssql_query(): supplied argument is not a valid Sybase-Link resource

Any idea?

---

### Post by no_brakes on 2008-05-29
Note that php5-sybase doesn't give you everything php-mssql does.  It doesn't support running stored procedures, and code I have running under php-mssql needed modifying to call different functions under sybase.

---

### Post by nevermind_quack on 2008-06-17
Trying to install MDB2_Driver_mssql returns the error: > pear/MDB2_Driver_mssql requires PHP extension "mssql"
 php5-sybase will work with this package, but it doesn't know it -- to skip dependency checking in the pear install do:
```
pear install --nodeps MDB2_Driver_mssql
```

The driver also has a line to check for mssql support in PHP, it will return error: > extension mssql is not compiled into PHP

Comment out the test at /usr/share/php/MDB2/Driver/mssql.php line 314 (or search for text "is not compiled into PHP").

Everything we've tried so far works great!

see [http://pear.php.net/bugs/bug.php?id=12697]("http://pear.php.net/bugs/bug.php?id=12697")

---

### Post by pablosp on 2008-08-21
works perfectly in ubuntu hardy.
thank you very much..

---

### Post by pcmofo on 2008-10-29
> **hogman23 said:**
> 

Get the dependencies for building PHP5:
```
apt-get build-dep php5
```



I am stuck on this step... when I enter it in I get this result....

```

apt-get build-dep php5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libc-client-dev is a virtual package provided by:
  libc-client2007b-dev 7:2007b~dfsg-3
  libc-client2007-dev 7:2007~dfsg-1
You should explicitly select one to install.
E: Package libc-client-dev has no installation candidate
E: Failed to satisfy Build-Depends dependency for php5: libc-client-dev

```

The server is running hardy and is brand new... also it is on a DMZ... which was effecting its ability to download patches... is this what is wrong with it now? it looks like it is working then fails...

Any ideas?

---

### Post by ethos84 on 2009-03-25
Well I think I followed the guide properly.

How can I test / use this? :D

---

### Post by liquidApe on 2009-07-29
Has anybody gotten this working on 9.04  Jaunty Jackalope?

---

### Post by creeves1982 on 2009-08-24
There is no apt-get install php5-mssql 

there is aptitiude install php5-mssql.  That is most likely what you were thinking of

---

### Post by sathyendra on 2011-11-03
For installing MSSQL Drivers 

sudo install apt-get install php5-mssql (will automaticly select 'php5-sybase' for installing )
sudo pear install --nodeps MDB2_Driver_mssql 

restart apache

---

