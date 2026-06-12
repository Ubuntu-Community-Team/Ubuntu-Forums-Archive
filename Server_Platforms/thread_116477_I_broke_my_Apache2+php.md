---
title: "I broke my Apache2+php"
date: 2006-01-12
forum: Server Platforms
---

### Post by Sepht on 2006-01-12
(breezy p3 server box)
I seem to have broken my Apache2 install. See, I used php4 for a while and just today I upgraded to php5, and my webserver started server couldn't server php files anymore, so I tried to downgrade.. still didn't work.. I played with the modules.. still didn't work...

So I'm wondering, how to I reinstall apache2+php4 in order to recreate it with the default config files, because apt-get remove apache2 php4 --purge and then installing them doesn't do the trick....
(I consider myself a fairly expirenced linux user, first set it up on my home box in 1998 :-/ I just wanna figure out how to get apt to redo it's config files, google searchs didn't show up anything)

---

### Post by i_am_socket on 2006-01-13
I suppose first you could see if php is working properly, then check your apache2.conf to make sure its using php properly to parse the files.  

make sure you have:
AddType application/x-httpd-php .php .html
AddType application/x-httpd-php-source .phps

in your apache2.conf and that you have php5.conf and php5.load in your apache2/mods-enabled directory.  That's about all the configuration that I needed to do to make it work.

---

### Post by oberon on 2006-01-14
I am having the same problem with a freshly loaded 5.10 machine.  Checked in apache2.conf and uncommented the lines refering to php, made sure that the mod were listed in "mods-enabled", restarted apache and still nothing.  Anyone else out have any problems with this?  Anything else to look at?

Thanks,
-oberon

---

### Post by majikstreet on 2006-01-14
libapache2-mod-php5
are you sure you have that installed? i had a similar issue when upgrading to php5..

and make sure that php5.conf and php5.load are enabled in apache.. you can symlink /etc/apache2/mods-available/php5.conf to /etc/apache2/mods-enabled/php5.conf  and /etc/apache2/mods-available/php5.load to /etc/apache2/mods-enabled/php5.load

you know how to symlink right? sudo ln -s original_file symlink
majik

---

### Post by oberon on 2006-01-14
> 
libapache2-mod-php5
are you sure you have that installed? i had a similar issue when upgrading to php5..

and make sure that php5.conf and php5.load are enabled in apache.. you can symlink /etc/apache2/mods-available/php5.conf to /etc/apache2/mods-enabled/php5.conf and /etc/apache2/mods-available/php5.load to /etc/apache2/mods-enabled/php5.load

you know how to symlink right? sudo ln -s original_file symlink
majik


yes, libapache2-mod-php5 is installed and the symlinks for php5.conf and php5.load are in /etc/apache2/mods-enabled.

---

### Post by harisund on 2006-01-15
Did you manage to get PHP4 working again? 

In case you didn't, you might want to read my post here, which is taken from a post I had made on these forums !

[http://harisund-linux.blogspot.com/2006/01/uninstalling-software.html](http://harisund-linux.blogspot.com/2006/01/uninstalling-software.html)

And anyway, if you are interested in purging apache2 and php4 and start from a complete scratch, simply do the following: 
apt-get --purge remove apache2 apache2-common php4
apt-get install apache2 php5

---

### Post by oberon on 2006-01-15
Okay after purging it and reinstalling it (php5) for about the 5th time it started working.  Not really sure why, but it is working as it should.

-oberon

---

### Post by Sepht on 2006-01-17
heh, after waiting here for 30min, and then sitting around in #ubuntu, i've concluded that if I have an issue with ubuntu, I'm better off going to #debian. 

Purging, installing and changing modules clearly didn't work, I explained that in my original post, I knew my problem was in producing clean config files. No one here produced a valid response that either A) answered my question or B) was something I didn't already try. 

I went to #debian and in less then 2 minutes they explained to my that dpkg(debian package management, what ubuntu and debian both use) assumes that if you change or delete a config file, you meant to do so and unless you use **apt-get -o DPkg::Options::="--force-confmiss"** it won't rebuild your config files. 

So as sad as it is for me to say, from what I've seen, ubuntu's community quality of support really quite poor, besides being unable to answer the question, being sidetracked, they are completely unfamiliar with the package management system.

---

