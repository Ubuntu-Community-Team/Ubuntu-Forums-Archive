---
title: "apr_dbd_mysql, MySQL module for Apache"
date: 2009-09-27
forum: Server Platforms
---

### Post by omarshariffdontlikeit on 2009-09-27
Hi Everybody,

This is my first post here so please excuse any community faux-pas on my behalf.

I've recently purchased a VPS server which comes with Ubuntu 8.04 and a basic LAMP stack pre-configured. I've been poking around for the last week or so getting everything configured as I like it and installing things such as SVN etc;

Now, I've got to the configuring of Apache phase. I want to use some of the Apache modules that interact with MySQL, but I appear to be having some problems determining if the database driver modules are installed or included. Under Mac OSX, my usual platform for development, I by passed all these little problems by compiling Apache 2.2 myself, and including apr_dbd_mysql in the config to enable this db driver, but under ubuntu I can't seem to determine if:


[LIST=1]
[*]The module is already installed (I can't locate it anywhere on the server)
[*]Wheither or not the version of libaprutils has this module included
[*]Which version of libaprutils is installed
[*]Wheither of not any of the versions of libaprutils apt-get provided actually has apr_dbd_mysql as part of its package
[/LIST]

The only information I have found on the subject after a heavy google session relates to Ubuntu 7,  and suggest compiling the module myself, by downloading the apache and myslq source. Interestingly, the article in question mentions that Ubuntu 8 should have this module available.

Here is a link to the article I found:
[http://www.cb1inc.com/2008/04/22/mod_dbd-mysql-driver-woes-with-ubuntu-7.04](http://www.cb1inc.com/2008/04/22/mod_dbd-mysql-driver-woes-with-ubuntu-7.04)

Can anyone help me? If someone could provide me with some steps to determin the current version of libaprutils on my system, that should help me work out if apr_dbd_mysql is part of that package, and if some one could direct me to a simple way of determining the contents of each package, again, this should provide me with the means to work out the rest for myself.

I really dont want to go through the hassle of compiling this module via apache and mysql source when its possible that there is a much simpler way of pulling the ready to go version from Ubuntus package management system.

Thanks for your help.

Cheers!

Ben

---

### Post by omarshariffdontlikeit on 2009-09-29
Just a quick follow up to let anyone else who has the same problem know what the solution is.

It appears that in all my hours of searching Google, I never entered the phrase "apr_dbd_mysql ubuntu", which lo and behold, returned the solution. A rather useful chap by the name of Francois Pesce posted the following blog with detailed instructions:
[URL="http://jok.is-a-geek.net/jblog/index.php/post/2009/02/12/How-to-cleanly-build-apr_dbd_mysqlc-on-Ubuntu-Server"]
http://jok.is-a-geek.net/jblog/index.php/post/2009/02/12/How-to-cleanly-build-apr_dbd_mysqlc-on-Ubuntu-Server[/URL]

I followed them to the letter and everything he describes happens, and the result worked first time.

So, there you have it. 

Easy peasy, without any need to recompile apache from scratch; you can just re-create the apr-utils package with mysql enabled.

Rad.

Cheers!

Ben

---

