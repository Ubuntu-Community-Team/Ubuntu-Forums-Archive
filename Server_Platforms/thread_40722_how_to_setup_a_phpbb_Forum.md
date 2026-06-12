---
title: "how to setup a phpbb Forum??"
date: 2005-06-10
forum: Server Platforms
---

### Post by lartan on 2005-06-10
Hello,

I like to setup a forum on a webpage which is hosted on my ubuntu server (the server has no graphical interface, only shell).

Someone told me phpbb is a good forum, so I did 'apt-get install phpbb'.

What are the following steps to set up a simple forum? Can anyone provide me with some information?

Thanx!
Arne

---

### Post by nocturn on 2005-06-10
[QUOTE=lartan]Hello,

I like to setup a forum on a webpage which is hosted on my ubuntu server (the server has no graphical interface, only shell).

Someone told me phpbb is a good forum, so I did 'apt-get install phpbb'.

What are the following steps to set up a simple forum? Can anyone provide me with some information?

Thanx!
Arne[/QUOTE]

I want to stress this first, make sure you have the latest version of phpbb, there have been many security issues with it lately.  if the .deb version is older, get the tar.gz from the phpbb site.

You will need to install MySQL and set up a user for phpbb.  
Then you can follow the install doc at: [http://www.phpbb.com/support/documents.php?mode=install](http://www.phpbb.com/support/documents.php?mode=install)

If anything is unclear, please post back.

---

### Post by LoclynGrey on 2005-06-11
I know this is Ubuntu world but I set up a webserver under fedore 3 and are running a phpbb forum + other stuff. You can go and muck round with installing MYSQL, PHP etc etc or instead install xampp for linux that does it all for you. [http://www.apachefriends.org/en/](http://www.apachefriends.org/en/)
Then all you need is to install phpbb, set it up into MYSQl and you are rockin.
For those Fedore 3 haters dont panic, my next project is a Ubuntu server, raided to replace my Fedore set up. (Like MS windows Fedore crashes)

---

### Post by afonic on 2005-06-11
[QUOTE=lartan]Hello,

I like to setup a forum on a webpage which is hosted on my ubuntu server (the server has no graphical interface, only shell).

Someone told me phpbb is a good forum, so I did 'apt-get install phpbb'.

What are the following steps to set up a simple forum? Can anyone provide me with some information?

Thanx!
Arne[/QUOTE]
 Don't use the pbpBB package from apt-get.

I assume you have Apache2, PHP and MySQL up and running. (if not do it using apt-get or Synaptic). Make sure you set a root password for MySQL ([http://dev.mysql.com/doc/mysql/en/index.html](http://dev.mysql.com/doc/mysql/en/index.html) for help).

Then download phpmyadmin using apt-get. It should be installed in localhost/phpmyadmin. Use it to create a new database user and a database for phpBB.

Download phpBB from [www.phpbb.com](www.phpbb.com), extract it somewhere inside your www root and follow the simple install steps.

---

