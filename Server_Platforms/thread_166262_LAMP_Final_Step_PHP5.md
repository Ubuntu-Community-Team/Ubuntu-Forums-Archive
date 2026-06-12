---
title: "LAMP Final Step: PHP5"
date: 2006-04-26
forum: Server Platforms
---

### Post by charlie. on 2006-04-26
I am configuring an Intranet server for our office. So far, using the Dapper Beta install CD and the server guide, I have setup Ubuntu (text mode only) installed an SSH server, MySql 5.0 and Apache 2. All three have been configured and are running beutifully. All I need to do now is install PHP.

I want to install PHP 5, with mysqli. Which packages should I install? 'aptitude' lists 'libapache2-mod-php5' and 'php5' and a whole load more. Which is the one for me?

'aptitude' lists 'php-mysql' as a package, but does not mention 'mysqli' - unless I did not look correctly. What package must I install for 'mysqli'?

Additionally, our intranet makes heavy use of apache's mod_rewrite. I could not find that in aptitude. Is that installed with apache2? (It is, after all, very very common)

I was sadly disappointed that, while giving excellent instructions for MySql and Apache, the server guide made no mention of PHP - only the most common server-side language in all time!

Thanks for any help. (My server is currently only a LAM Server :rolleyes:  )

---

### Post by Ensnared on 2006-04-26
If think all you need to do is this:```
apt-get install php5 php5-mysqli
```
If that doesn't also pull the "libapache2-mod-php5" package, just add that to the end, but simply specifying "php5" will - if I remember correctly - get that package, plus a few others, thanks to dependencies.

The php5-mysqli package I'm actually not 100% certain of, but I believe it's correct. You can search for it though, by doing this:```
apt-cache search php mysqli
```

As for mod_rewrite, I believe it's installed by default. You can check though - all installed modules are located in "/etc/apache2/mods-available/" (or something similar - I'm unable to check right now), and all active modules are symlinked to their corresponding files there from "/etc/apache2/mods-enabled/" (again; or something similar ;) ).

---

### Post by charlie. on 2006-04-26
Thanks for the introduction to 'apt-cache search ...', I had never seen that before.

Alas, no joy. Searching for mysqli found nothing, with or without the php keyword. (I do have the universe and multiverse enabled and I have updated my indexes) Running "apt-get install php5 php5-mysqli" says that "Packages php5-mysqli is not available, but is referred to by another package."

I see that "apt-get install php5" (no mysqli keyword) reflects that libapache2-mod-php5 will be installed. It also recommends php-pear. It makes no mention of MySql or mysqli. (Alarmingly, it states that it will axe apache2-mpm-worker. I presume that this is because PHP only works in prefork mode, so its installation axes any alternatives! Clever...)

As for mod_rewrite, it is not listed under /etc/apache2/mods-available/ or /etc/apache2/mods-enabled/. The SO is, however, found in /usr/lib/apache2/modules - named mod_rewrite.so. Whether this module is enabled or not... I presume that it is not loaded because there is no LoadModule line for it in /etc/apache2/apache2.conf - There are no LoadModule lines at all! I suppose adding one would be a good idea... duh.

More help and information would be greatly appreciated. As for now, I am going to "take the leap" and install "php5". (Ubuntu is quick to reinstall if I total the system... like that would happen!) I will also enable mod_rewrite. That only leaves mysqli.

---

### Post by charlie. on 2006-04-26
I have completed my PHP5 installation with "apt-get install php5" and all is well. Quickly creating an 'index.php' with a phpinfo() line and browsing to my server reveals that PHP is running nicely.

After a bit of looking, I found "rewrite.load" in /etc/apache2/mods-available" - it referenced mod_rewrite.so - I symlinked it into /etc/apache2/mods-enabled and restarted apache. mod_rewrite is now working perfectly. (After I set AllowOverride to All)

All is now well - except for mysqli. Every other component that our intranet uses has been installed, configured and tested.

---

### Post by Ensnared on 2006-04-26
I could've sworn I saw php-mysqli or php5-mysqli when I upgraded from php4 just a couple of days ago, but I must have been seeing things cause I can't find it now, not on Breezy nor on Dapper.

A quick search turned up [this](http://www.ubuntuforums.org/showthread.php?t=148292) though - I haven't tested it (I still use the old mysql extension) but it might be worth a shot if you need mysqli instead :)

---

### Post by charlie. on 2006-04-27
It appears that mysqli support has been missing since the dawn of time - and that people have been begging for it since Breezy was in development. I have all but given up hope of finding it in the repos! (one wonders why this is so...)

Plan B: Build it myself.

Logic tells me that, when I configure and make the PHP 5 source, it will not interfere with my installed PHP binaries that apt placed there. (Assuming I don't "make install" it.) Additionally, I should be able to build it and then find mysqli.so and install that manually - by sticking it in my PHP extensions DIR. As long as it is built on my system, with the correct development packages and the correct version of the source,  it should work. I will try this tomorrow.

As far as I can tell, all I need to install to make it compile is "build-essential", "flex", "yacc", "libxml2-dev" and "libmysqlclient15-dev". This last package comes in many versions, but aptitude shows that "libmysqlclient15off" is installed so I presume that 15 is the correct one.

I expect that I will have to recompile mysqli every time I upgrade PHP or MySql. This is not great, but it is an acceptable compromise.

Could someone PLEASE make a mysqli package for the repositories - it's not THAT hard!

---

### Post by Ensnared on 2006-04-27
That's pretty much what I found out too. But judging from the [thread I linked to](http://www.ubuntuforums.org/showthread.php?t=148292), the downloadable module from [here](http://www.untitledproject.co.uk/packages/) should work, and if so you atleast won't need to compile the whole thing yourself :)

---

### Post by charlie. on 2006-04-27
I like precompiled binaries from the Ubuntu repositories, because they are generally quite good and tested to work together. This other module is an enigma, however. As a software developer of trade, compiling PHP is no challenge. Additionally, it gives me peace of mind and a bloody good excuse to test Ubuntu's compiler/toolchain. More importantly, I know that I will always be able to recompile it if I update something. If I used this enigmatic download, I would have no guarantees that an updated version would be made available for future versions of its dependencies.

There is nothing quite like knowing that a key component in your corporations intranet was, not only installed, but COMPILED personally.

---

### Post by charlie. on 2006-04-28
Plan B has succeeded! (according to phpinfo()...)

I installed several dependencies: build-essential, flex, bison, libxml2-dev and libmysqlclient15-dev. I also downloaded the latest PHP source and extracted it. I ran configure with some options...

./configure --with-mysqli=shared,/usr/bin/mysql_config

... and then "make". I did NOT "make install" because that would interfere with the installed PHP binaries. I found "mysqli.so" in the 'modules' subdir and copied that to "/usr/lib/php5/20051025". I then modified php.ini by adding the following line...

extension=mysqli.so

.. and restarted Apache with my handy alias: restart-apache. Now, phpinfo() shows "mysqli" as a loaded extension with optional configuration block!

Finally, I axed my source/build tree - it is no longer necessary.

Yeah! That was easy!

---

### Post by jalonsom on 2006-04-28
The package is php5-mysql without the final "i", I think.
At least it is what I installed, and my apache/php/mysql server is running fine so far.

---

### Post by Ensnared on 2006-04-28
They aren't the same. The old mysql extension only support the older MySQL client-functions (e.g. MySQL 3.23 or somesuch), while you need the mysqli extension to make use of all the new features in MySQL 4.1 and newer.

[php-mysql](www.php.net/mysql)
[php-mysqli](www.php.net/mysqli)

---

### Post by charlie. on 2006-04-30
** This post exists because of cold hands, an unfamiliar keyboard and the inability to delete posts on this forum. The next message should have been this one. **

---

### Post by charlie. on 2006-04-30
"mysql" and "mysqli" are two entirely different PHP modules, although they both enable PHP to connect to a MySql server. The "i" is very significant. Your applications clearly use the older, slower, more common "mysql" extension and not the "mysqli" extension.

BTW: My server is working perfectly now. I uploaded my Intranet sources and databases and, after a brief scuffle with mod_rewrite's rules and case sensitive file systems, it worked.

---

### Post by jalonsom on 2006-05-18
php5-mysqli is in the repositories now.

---

