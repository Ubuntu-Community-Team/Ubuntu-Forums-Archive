---
title: "Is there a ubuntu control panel for apache,php,mysql like in xampp?"
date: 2010-07-04
forum: Server Platforms
---

### Post by ozstar on 2010-07-04
Hi,

I have been using wamp on an xp box and now have set up ubuntu with the localhost server seeming to be going okay.

As this is just a desktop graphical test server with no real public hosting, I was hoping to find a control panel like in wamp where one can stop/start php, apache, mysql, phpmyadmin and see logs etc.

I have done some searches but so far can't see anything.

Am I missing it, or maybe it does not exist.

Thanks

oz :-)

---

### Post by grenadeguy187 on 2010-07-04
Sorry to break it to you, but it doesn't have a graphical frontend.  But trust me, once you get the hang of the commandline, you wouldn't want a GUI.  It's pretty simple, just look up a couple of Apache guides online and you'll be on your way.

---

### Post by ozstar on 2010-07-04
Thanmks.

Are there simple instructions for dummys on what must be done to get the server, mySQL and phpmyadmin working.

I have done much searching and find it very confusing.. bits and pieces here and there, which is fine if you have some idea. I would like short concise definitive instructions on how to basically set it all up. 

I have used wamp for a while and xampp which have the interfaces I need.

One of the cofusi g thin gs is settin g up the virtula hosting etc.

I have the folders for each site in var/www/ but what files and where are they that I need to enter this info?

Thanks

oz :-(

---

### Post by StolerTech on 2010-07-04
Hi,

You said you were using a LAMP setup so here is how you get mysql working:

```
sudo apt-get install mysql-server
sudo apt-get install php5-mysql

```Make sure you setup a password for your root account it should prompt you when installing the package mysql-server

and then of course restart apache, sudo /etc/init.d/apache2 restart

Oh one last though: you need mcrypt for phpmyadmin I think, then restart apache again.
```
sudo apt-get install php5-mcrypt
```

---

### Post by kevinthecomputerguy on 2010-07-20
You might like Webmin, it makes life much easier. Not that you shouldnt learn command line (someday)
See complete webmin how-to at [http://woodel.com](http://woodel.com)
*Command line is important to learn next

---

