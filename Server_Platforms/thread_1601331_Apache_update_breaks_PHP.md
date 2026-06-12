---
title: "Apache update breaks PHP"
date: 2010-10-20
forum: Server Platforms
---

### Post by thegodfaza on 2010-10-20
I updated my server (Ubuntu 10.04 LTS) today and had about 23 updates in Webmin. After the update suddenly apache doesn't render php pages anymore, instead letting you download the source code for the scripts. I checked the logs and found this:
```
Syntax error on line 1 of /etc/apache2/mods-enabled/php5.load: Cannot load /usr/lib/apache2/modules/libphp5.so into server: /usr/lib/apache2/modules/libphp5.so: cannot open shared object file: No such file or directory
```

I tried reinstalling php5 but I can't get it to work. I also hope that this was a glitch and that updates that break stuff like this don't get through QA.

---

### Post by ProntoAnthony on 2010-10-20
Yes, I have the same problem.

Forgive me for not better understanding the dpkg.log, this may not have anything to do with it, but what is 'half-installed'? and why is it suggesting alternative installs?

```

2010-10-20 09:25:46 configure php5-cli 5.3.2-1ubuntu4.5 5.3.2-1ubuntu4.5
2010-10-20 09:25:46 status unpacked php5-cli 5.3.2-1ubuntu4.5
2010-10-20 09:25:46 status half-configured php5-cli 5.3.2-1ubuntu4.5
2010-10-20 09:25:49 update-alternatives: run with --install /usr/bin/php php /usr/bin/php5 50 --slave /usr/share/man/man1/php.1.gz php.1.gz /usr/share/man/man1/php5.1.gz
2010-10-20 09:25:49 status installed php5-cli 5.3.2-1ubuntu4.5
2010-10-20 09:25:49 configure php5-cgi 5.3.2-1ubuntu4.5 5.3.2-1ubuntu4.5
2010-10-20 09:25:49 status unpacked php5-cgi 5.3.2-1ubuntu4.5
2010-10-20 09:25:49 status half-configured php5-cgi 5.3.2-1ubuntu4.5
2010-10-20 09:25:50 update-alternatives: run with --install /usr/bin/php-cgi php-cgi /usr/bin/php5-cgi 50 --slave /usr/share/man/man1/php-cgi.1.gz php-cgi.1.gz /usr/share/man/man1/php5-cgi.1.gz
2010-10-20 09:25:50 update-alternatives: run with --install /usr/lib/cgi-bin/php php-cgi-bin /usr/lib/cgi-bin/php5 50
2010-10-20 09:25:50 status installed php5-cgi 5.3.2-1ubuntu4.5
2010-10-20 09:25:50 configure libapache2-mod-php5 5.3.2-1ubuntu4.5 5.3.2-1ubuntu4.5
2010-10-20 09:25:50 status unpacked libapache2-mod-php5 5.3.2-1ubuntu4.5
2010-10-20 09:25:50 status unpacked libapache2-mod-php5 5.3.2-1ubuntu4.5
2010-10-20 09:25:50 status unpacked libapache2-mod-php5 5.3.2-1ubuntu4.5
2010-10-20 09:25:50 status half-configured libapache2-mod-php5 5.3.2-1ubuntu4.5
2010-10-20 09:25:52 status installed libapache2-mod-php5 5.3.2-1ubuntu4.5
2010-10-20 09:25:53 configure php5-curl 5.3.2-1ubuntu4.5 5.3.2-1ubuntu4.5
2010-10-20 09:25:53 status unpacked php5-curl 5.3.2-1ubuntu4.5
2010-10-20 09:25:53 status unpacked php5-curl 5.3.2-1ubuntu4.5
2010-10-20 09:25:54 status half-configured php5-curl 5.3.2-1ubuntu4.5
2010-10-20 09:25:54 status installed php5-curl 5.3.2-1ubuntu4.5
2010-10-20 09:25:54 configure php5-gd 5.3.2-1ubuntu4.5 5.3.2-1ubuntu4.5
2010-10-20 09:25:54 status unpacked php5-gd 5.3.2-1ubuntu4.5
2010-10-20 09:25:54 status unpacked php5-gd 5.3.2-1ubuntu4.5
2010-10-20 09:25:54 status half-configured php5-gd 5.3.2-1ubuntu4.5
2010-10-20 09:25:54 status installed php5-gd 5.3.2-1ubuntu4.5
2010-10-20 09:25:54 configure php5 5.3.2-1ubuntu4.5 5.3.2-1ubuntu4.5
2010-10-20 09:25:54 status unpacked php5 5.3.2-1ubuntu4.5
2010-10-20 09:25:55 status half-configured php5 5.3.2-1ubuntu4.5
2010-10-20 09:25:55 status installed php5 5.3.2-1ubuntu4.5

```

---

### Post by James78 on 2010-10-20
> **thegodfaza said:**
> I tried reinstalling php5 but I can't get it to work. I also hope that this was a glitch and that updates that break stuff like this don't get through QA.
Ya, reinstalling has a way of not wanting to actually reinstall things. I've come up with that problem wayyy too often. To fix that, you just do a apt-get purge package, then apt-get install package. If there are other dependencies on it, and you can't get rid of it without removing a chunk of the system, then just do dpkg -P --force-all package, then apt-get install package.

---

### Post by thegodfaza on 2010-10-20
Perhaps the apache update should be looked into as apparently others are having apache blow away php. Also after repeated installing / uninstalling of php, it decided to work again. I guess from now on I'm going to have to make a test vm and test all the updates to make sure something like this doesn't happen again.

EDIT: Also here is my webmin log of packages installed.
```
apache2.2-bin apache2.2-common apache2-mpm-worker apache2 apache2-mpm-prefork apache2-utils app-install-data-partner desktopcouch indicator-sound libc-bin libc6 libc6-i386 libc-dev-bin libc6-dev libpoppler-glib4 libpoppler5 libwebkit-1.0-common libwebkit-1.0-2 linux-headers-2.6.32-25 linux-headers-2.6.32-25-generic linux-image-2.6.32-25-generic linux-libc-dev man-db mobile-broadband-provider-info poppler-utils python-desktopcouch python-desktopcouch-records
```

---

### Post by ProntoAnthony on 2010-10-20
I fixed my problem by downgrading php to 5.2.  See the thread
[http://ubuntuforums.org/showthread.php?t=1459163]("http://ubuntuforums.org/showthread.php?t=1459163")

---

### Post by thegodfaza on 2010-10-20
BTW, I don't feel like marking this thread as solved as I believe that the Apache update that came down the line has some issues. It would be nice to get some input from Canonical or whoever maintains that package.

---

### Post by James78 on 2010-10-21
I updated PHP on my server just today, and everything went perfectly fine. I'm running a 10.10 server though.

P.S. If you want developer input, file a bug with Ubuntu on Launchpad.

---

### Post by AlistairH on 2010-11-25
I find this an on going issue. Every time I have upgraded Apache2 when flagged through Webmin, PHP breaks.

Since I set up a lamp server 2 months ago, there's been 3-4 updates and every time I have to go through hoops to get php5 working again. Each time I seem to end up doing it a different way.

Does anyone have a definitive way of sorting this, other than not installing the Apache2 updates in the first place!

---

### Post by Vegan on 2010-11-25
Mine is down too, from an update through webmin

so now my sites are all down, not what I want to see

---

### Post by James78 on 2010-11-25
Strange. I use 10.04.1 LTS with latest Webmin and updates, and I have never encountered any problems. Either way, with the newest Apache2 update, I SSH'd in and updated with apt. But I'm having no problems.. Clearly this is an issue though. Try removing php5 and installing it again. Dependencies are probably set on it, so do a forced removal, that way you can remove it without getting rid of the dependencies.  E.g. dpkg -r --force-all php5. What architecture is everyone else using? My server is i686 at the moment.

---

### Post by Vegan on 2010-11-25
Thanks, I tried reinstall php5 but I did not use the dkpg like you suggested, back up, thanks.

```

sudo dpkg -r --force-all php5
sudo apt-get install php5
sudo /etc/init.d/apache2 restart

```

Those are the steps I did to get my php pages to render again.

---

### Post by AlistairH on 2010-11-26
I did the usual steps mentioned earlier in the thread to no avail. I then had cause to create a php file with phpinfo() the only statement and it work. My webpages were still being downloaded rather than parsed. I cleared my cache in Chrome and lo and behold, it worked.

So, simply clearing your cache might resolve it, though I confess it is a bit bizarre.

---

### Post by James78 on 2010-11-26
Yup, browser cache has a way of playing tricks like that on you. It gets annoying really fast, especially when doing web development.

---

### Post by SeijiSensei on 2010-11-26
One way to deal with that is to enforce no-caching in PHP scripts like this:

```

# force page refresh
header("Pragma: no-cache");
header("Cache-Control: no-cache; must-revalidate");
header("Expires: -1");

```

Taken together, these enforce no-caching on most any browser.  

Since they're HTTP headers, they need to run ahead of any content the scripts might generate.

---

### Post by HungQuach on 2012-05-02
My upgraded to Ubuntu 12.04 LTS also broke my website. More specifically, my php code stopped working. Here's how I fixed it: 

Edit /etc/apache2/mods-enabled/php5.conf:
#    <FilesMatch ".ph(p3?|tml)$">
      <FilesMatch ".php">

I prefer to use .html for my .php files, so I used this instead:
      <FilesMatch ".html">

I restarted apache with:
sudo service apache2 restart

and everything was back to working order again!

---

