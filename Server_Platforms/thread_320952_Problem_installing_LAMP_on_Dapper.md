---
title: "Problem installing LAMP on Dapper"
date: 2006-12-18
forum: Server Platforms
---

### Post by Starcraftmazter on 2006-12-18
Okey.

I've compiled apache2 and php5 (latest of both) from source, and installed the mysql 5 binaries, because I couldn't find the source (which is odd, maybe I didn't look hard enough).

I've got all the deps for the 3 things, and I've added mysql's bin to the $path, just in case.

I've compiled php  --with-mysql-dir=/usr/local/mysql  option, and I've got everything set up, BUT for some reason, php just refuses to recognise mysql.

Neither MySQL or MySQLi are coming up in the phpinfo, no matter what I do.

Every single thing I've read everywhere, suggests that for php5, which doesn't come with mysql libraries as we all know, compiling it with mysql does the trick....well I pose the question - wtf???


I would assume the mysql libraries for php aren't being loaded, well why? Where are they, and how do I load them into php?


Here's my full configure string:
'./configure' '--with-apxs2=/usr/local/apache2/bin/apxs' '--with-mysql-dir=/usr/local/mysql/' '--with-xml' '--enable-bcmath' '--enable-calendar' '--enable-exif' '--enable-ftp' '--enable-mbstring' '--enable-mbstr-enc-trans' '--enable-mbregex' '--enable-memory-limit' '--enable-magic-quotes' '--enable-discard-path' '--enable-sockets' '--enable-track-vars' '--with-libxml-dir=/usr' '--with-xsl=/usr/local' '--with-zlib=/usr' '--with-mysqli-dir=/usr/local/mysql'


I have tried using mysql using terminal, and it works fine.
Other than that - php works fine.


But when I try to use mysql functions, it says they don't exist.


All of the scripts I've made previously which made use of mysql, come up blank. Note, I have set php to display all errors, and less complicated test scripts...like the one I just made work fine.

Trying a copy of phpbb3 (I always keep a few around), it cannot find support for any databases apart from sqlite, though it does work apart from that, so I'm sure php isn't broken, and I've recompiled it about 50 times when I've tried many things.


Weeeell, if anyone can suggest anything, please do 8)

---

### Post by az on 2006-12-18
Why can't you use the binary packages?

---

### Post by marianom on 2006-12-18
I compare your configure string with mine (I built it from source too).

3 ideas/questions:
1- Did your run phpinfo to verify if mysql isn't there?
2- I would start simple and add more options to test if everything works fine.
For example:
```

./configure --with-apxs2=/usr/local/apache2/bin/apxs --with-mysql-dir=/usr/local/mysql/
make
make install

```
3- if you compile with mysql, I'm not sure you need to compile with mysqli too.

Let us know how it goes. I'll try to help

---

### Post by Starcraftmazter on 2006-12-18
> **azz said:**
> Why can't you use the binary packages?

No control over config.

> **marianom said:**
> 1- Did your run phpinfo to verify if mysql isn't there?

Yes, as I have mentioned both mysql and mysqli are missing from phpinfo.

> **marianom said:**
> 
2- I would start simple and add more options to test if everything works fine.
For example:
```

./configure --with-apxs2=/usr/local/apache2/bin/apxs --with-mysql-dir=/usr/local/mysql/
make
make install

```

I'll go do that now.

> **marianom said:**
> 3- if you compile with mysql, I'm not sure you need to compile with mysqli too.

Indeed it's not necessary, but entirely possible.
The reason I do it, is because I want to have my php config synced with my server on the net.


Edit:
Unfortunately, compiling it with just apache2 and mysql didn't make a difference.
I used,
 './configure' '--with-apxs2=/usr/local/apache2/bin/apxs' '--with-mysql-dir=/usr/local/mysql/'

Still no mysql in phpinfo.


I'm stumped :s

---

### Post by az on 2006-12-19
> **Starcraftmazter said:**
> No control over config.



Isn't it modular?
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=apache2-mod&searchon=all&subword=1&version=dapper&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=apache2-mod&searchon=all&subword=1&version=dapper&release=all)

What in particular do you need apache to do that the binary packages don't already do?

---

### Post by Starcraftmazter on 2006-12-19
> **azz said:**
> Isn't it modular?
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=apache2-mod&searchon=all&subword=1&version=dapper&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=apache2-mod&searchon=all&subword=1&version=dapper&release=all)

What in particular do you need apache to do that the binary packages don't already do?

The extensions aren't. Apache's modules are, but regardless....

...Look, I'm not looking to install binaries like a windows user, I specifically need to install it from source. I have my reasons, now I'm sure this is entirely possible, given it was designed to be compiled from source. Given everything must be compiled from source.

---

### Post by az on 2006-12-19
> **Starcraftmazter said:**
> The extensions aren't. Apache's modules are, but regardless....

...Look, I'm not looking to install binaries like a windows user, I specifically need to install it from source. I have my reasons, now I'm sure this is entirely possible, given it was designed to be compiled from source. Given everything must be compiled from source.

Make sure you have the deb-src entries for main enabled in your /etc/apt/sources.list
and run

sudo apt-get source apache2

then look in the source tree at the debian/rules makefile.  Edit the makefile to suite your needs and then build the package.
Sorry, but I forget the command to bump the package version and update the changelog right now...


Edit:  Running dch will increase the version and create a new changelog entry for you to fill out.

[http://www.fifi.org/cgi-bin/man2html/usr/share/man/man1/dch.1.gz](http://www.fifi.org/cgi-bin/man2html/usr/share/man/man1/dch.1.gz)
[http://www.debian.org/doc/maint-guide/ch-update.en.html](http://www.debian.org/doc/maint-guide/ch-update.en.html)

---

### Post by Starcraftmazter on 2006-12-19
I already installed apache 2 from source, I do not understand why you suggest that I do it again, unless you want me to recompile it?

---

### Post by az on 2006-12-19
> **Starcraftmazter said:**
> I already installed apache 2 from source, I do not understand why you suggest that I do it again, unless you want me to recompile it?

Yes. So that you get to control the config.  And you get the benefit of deb packaging.  What more do you want?

---

### Post by Starcraftmazter on 2006-12-19
I don't understand why I need to use any kind of packaging, and what that has to do with anything.

Anyway,  I recompiled apache, and it didn't help.

---

### Post by Starcraftmazter on 2006-12-19
Well, there have been some new developments....

Changing the config strong to simple '--with-mysql', completely ommiting the directory, seems to give mysql support in php.

Though on phpinfo version shows up as 5.0.22 and when I try to connect, it says cannot connect to socket, even though mysql is running.

This makes me think I somehow have 2 versions of mysql installed somewhere on my comp.


Doing a search, I found:
libmysqlclient15off_5.0.22-0ubuntu6.06.2_i386.deb (1.3 mb)
and
libmysqlclient15-dev_5.0.22-0ubuntu6.06.2_i386.deb (5.9 mb)

In /var/cache/apt/archieves
But I can't find any other mysql install folders.


Can someone try and make sense of all this please? :s

---

### Post by az on 2006-12-20
> **Starcraftmazter said:**
> 

Doing a search, I found:
libmysqlclient15off_5.0.22-0ubuntu6.06.2_i386.deb (1.3 mb)
and
libmysqlclient15-dev_5.0.22-0ubuntu6.06.2_i386.deb (5.9 mb)

In /var/cache/apt/archieves

How did you install mysql?  Did you compile it from source or install it using the package manager?

Those two files are deb packages.  When you install something using the package manager, it first downloads the debs into that directory.  Whether they are installed or not is another story.  Check the package manager.

dpgk -l|grep mysql

any deb package that is suffixed with a -dev means it's the developmental headers - so no, this is not two different versions of mysql.

And since these are the mysql client packages and not mysql server, you would need more to have a functioning LAMP stack.

Good luck!

---

### Post by Starcraftmazter on 2006-12-20
I obtained the latest stable (5.0.27) binaries from their website, and installed them manually.

When I try "dpgk -l|grep mysql", I get a command not found :(
Though those two files are in the Synapic Package Manager.
Should I uninstall them?

Do I need to get the latest .27 ones, since they seem to be for .22, and most importantly, where do I get them from, aside from package managers?


Thanks!

---

### Post by az on 2006-12-20
> **Starcraftmazter said:**
> I obtained the latest stable (5.0.27) binaries from their website, and installed them manually.

When I try "dpgk -l|grep mysql", I get a command not found :(
Though those two files are in the Synapic Package Manager.
Should I uninstall them?

I'm sorry.  I made a typo that should have been dpkg and not dpgk.  But anyway, using synaptic is the same - and if they are listed as installed, then they are installed.

If you say you installed a mysql binary from a third party, and you also have the mysql-client package installed by synaptic, and you can't find them on your system I would say something is borked...

> **Starcraftmazter said:**
> 
Do I need to get the latest .27 ones, since they seem to be for .22, and most importantly, where do I get them from, aside from package managers?


Thanks!

I dunno.  I'm still wondering why you got them from somewhere else than the ubuntu repositories.  We would not be having this conversation.

The version in the repositories work fine and will receive security upgrades and bug fixes for years.  It is not very popular to use cutting-edge versions of the individual components of the LAMP stack unless you are developing them.  It's much less popular to install binary versions of applications that are already available in the repositories.  Much less so is compiling them from source.

So, I'm trying, but I can't help you much...

---

### Post by Starcraftmazter on 2006-12-20
Well because the ones in the repositries aren't the latest, and are far behind the latest :s

I'll attempt to uninstall everything to do with mysql, and reinstall it from the repositries though, see if that'll help.

---

### Post by chrisfay on 2006-12-21
The benefit of the repositories far outweighs anything you'd gain from having a slightly newer, less tested release of any package IMHO. Especially when the release 'will' come when it's been sufficiently tested.

Is there a specific security update in the package that you feel paramount in having?

---

### Post by Starcraftmazter on 2006-12-21
No, I just prefer to have the latest php and mysql. Suppose it won't make much difference with 5.0.22 to 5.0.27

---

### Post by Starcraftmazter on 2006-12-22
After a manual uninstall of my handywork, an install with synapic, having it not work, a complete uninstall of anything with "mysql" in it using synaptic, and a fresh install of whats required...using synaptic - IT ALL WORKS!!!

I'd like you thank everyone for their help 8)

---

