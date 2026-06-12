---
title: "Installing phpMyAdmin"
date: 2008-10-07
forum: Server Platforms
---

### Post by Dave Smith on 2008-10-07
OK ... this is an appeal to get me out of a little nightmare :(

I'm using **Unbuntu 6.06 LTS Server** and I've downloaded **phpMyAdmin** (the latest version 3.0.0), un-tarred it and ... now my problems.

I am not at all clear what directory to put this application in. There are some suggestions that it should directly in *root* ... other suggestions put it in */var/www/* ... but I also seem to have it in */etc/*

Where ever it is, it is not working. When I log on to */mydomain/phpMyAdmin* all I get '*mydomain*' but no phpMyAdmin.

I know that I have to configure the *config.inc.php* file - but I seem to have at least two of them. So which one to edit? Which one is read first?

I'm trying to work out whether my problem is that the application is in the wrong directory - or whether I just haven't configered my *config.inc.php* file correctly.

Any help, advice, comments, sugestions would help to stop me going greyer that I already am.

Thanks.

Dave Smith

---

### Post by tspec on 2008-10-07
When I installed it (in hardy though) it was installed to /etc/phpmyadmin/

I believe you won't find it in /var/www/ as a symbolic link gets created from there to the install directory. The symbolic link should get done automatically now, it's been a long time since I had to do it manually.

To get it to work though, I had to add this line to the end of my apache2.conf file in /etc/apache2/

# Enable PHPMyAdmin
Include /etc/phpmyadmin/apache.conf

That path will obviously depend on where it's been installed. If you're not sure where it's installed, you could type:

sudo updatedb
sudo locate phpmyadmin

Once you've made a change to the apache file, you will of course then need to restart apache.

Hope that helps.

---

### Post by Dave Smith on 2008-10-07
thanks for your quick reply and suggestions. I try this out tomorrow. :)

---

### Post by lykwydchykyn on 2008-10-08
Is it not in the repositories for 6.06?  I believe the way it usually installs is to /usr/share/phpmyadmin.  Then you use an alias in apache to redirect whatever path you want to use to that directory.  Or you can symlink it, that usually works too.

If you can get it from the repository, that's a whole lot easier.

---

### Post by tspec on 2008-10-08
Problem is if you want the latest version of a piece of software, in my experience, you rarely find it in the repositories. Of course, if you don't care about having the latest version and prefer a potentially less problematic installation, the repository is the way to go.

---

### Post by Dave Smith on 2008-10-08
This is an interesting example of the confusion that I was getting which prompted my first question. 

I had seen the location as being */var/www/ and/*or */etc/*, **tspec** thought */etc/phpmyadmin/* and now **lykwydchykyn** is suggesting */usr/share/phpmyadmin* as the natural place to go.

That's the problem I was getting when searching the various forums and doing a *Google* search. The *phpMyAdmin wiki* does not give a clear answer on this either.

I am too naive in thinking there has to be a correct location? Or maybe it doesn't matter if you can make the correct links ...

Thanks for the continuing suggestions.

---

### Post by lykwydchykyn on 2008-10-08
There is not really a "correct" location in terms of making it work.  /usr/share/phpmyadmin is where the package manager puts it.  You can stick it in the web root, or you can stick it somewhere else and symlink it to the webroot (or use an apache alias).  It really shouldn't matter, but IMHO best practice would be to put it in a safe location like /usr/share (or more appropriately for non-repo software, /usr/local/share) and use an apache alias.

---

### Post by tspec on 2008-10-08
Dave: Sorry my bad.

Looked a bit further into my config and yeah, looks like the guts of phpmyadmin is sitting in /usr/share/, I was basing it off what i had in apache2.conf as I don't really use phpmyadmin.

Web related:
/etc/phpmyadmin
/etc/phpmyadmin/apache.conf
/etc/phpmyadmin/config.footer.inc.php
/etc/phpmyadmin/config.header.inc.php
/etc/phpmyadmin/config.inc.php
/etc/phpmyadmin/htpasswd.setup
/etc/phpmyadmin/lighttpd.conf

Docs:
/usr/share/doc/phpmyadmin/

Install Base:
/usr/share/phpmyadmin/
/usr/share/phpmyadmin/js/
/usr/share/phpmyadmin/lang/
/usr/share/phpmyadmin/libraries/
/usr/share/phpmyadmin/pmd/
/usr/share/phpmyadmin/scripts/
/usr/share/phpmyadmin/themes/

Using "sudo locate phpmyadmin | less" should give you all this information. Did you check your apache2.conf file to add this?

# Enable PHPMyAdmin
Include /etc/phpmyadmin/apache.conf

---

### Post by Dave Smith on 2008-10-08
Thanks for all of this. It's late here and so I'll check out some of this tomorrow. Suggestions and comments are much appreciated.

---

### Post by jdcnosse on 2008-10-08
I have a similar problem.  I'm running Ubuntu Hardy Heron 8.04 LTS server edition with phpMyAdmin that I downloaded from the repositories.

I'm trying to follow a tutorial online on how to install it and so far I've got it installed I think.

I searched for the folder and here are all of the places that have a "phpmyadmin" folder:

/etc/phpmyadmin/
/usr/share/phpmyadmin/
/usr/share/doc/phpymyadmin/
/var/lib/phpmyadmin/

I know I have to edit the config.inc.php file in /etc/phpmyadmin/ too.

this is what I have so far for the config file:

```
/**
 * Server(s) configuration
 */
$i = 0;
// The $cfg['Servers'] array starts with $cfg['Servers'][1].  Do not use $cfg['Servers'][0].
// You can disable a server config entry by setting host to ''.
$i++;

/* Authentication type */
//$cfg['Servers'][$i]['auth_type'] = 'cookie';
/* Server parameters */
//$cfg['Servers'][$i]['host'] = 'localhost';
//$cfg['Servers'][$i]['connect_type'] = 'tcp';
//$cfg['Servers'][$i]['compress'] = false;
/* Select mysqli if your server has it */
//$cfg['Servers'][$i]['extension'] = 'mysql';
/* Optional: User for advanced features */
// $cfg['Servers'][$i]['controluser'] = 'root';
// $cfg['Servers'][$i]['controlpass'] = 'rootpass';
/* Optional: Advanced phpMyAdmin features */
// $cfg['Servers'][$i]['pmadb'] = 'phpmyadmin';
// $cfg['Servers'][$i]['bookmarktable'] = 'pma_bookmark';
// $cfg['Servers'][$i]['relation'] = 'pma_relation';
// $cfg['Servers'][$i]['table_info'] = 'pma_table_info';
// $cfg['Servers'][$i]['table_coords'] = 'pma_table_coords';
// $cfg['Servers'][$i]['pdf_pages'] = 'pma_pdf_pages';
// $cfg['Servers'][$i]['column_info'] = 'pma_column_info';
// $cfg['Servers'][$i]['history'] = 'pma_history';
// $cfg['Servers'][$i]['designer_coords'] = 'pma_designer_coords';

/*
 * End of servers configuration
 */
```

What else do I need to do to get phpmyadmin to work?

Right now it goes to this: [[IMG]http://img296.imageshack.us/img296/3610/screenshotdd6.th.png[/IMG]](http://img296.imageshack.us/my.php?image=screenshotdd6.png)[[IMG]http://img296.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

---

### Post by lykwydchykyn on 2008-10-08
@jdcnosse: I don't remember having to do much of anything after installing it from the repos, though it's been a while since I did it last.  In your case it looks like apache is not running.  If you just put "localhost" in the browser, do you get a page or an error?

---

### Post by jdcnosse on 2008-10-09
I get the same error...

---

### Post by lykwydchykyn on 2008-10-09
Well, then you need to start apache.  Try this:
```

invoke-rc.d apache2 restart

```

---

### Post by jdcnosse on 2008-10-09
nope still nothing.

so maybe it's something to do with my config file?

---

### Post by Dave Smith on 2008-10-09
**jdcnosse** - What on-line tutorial did you use?

---

### Post by jdcnosse on 2008-10-09
honestly...I don't know right now lol

I was using it on my ubuntu machine...I'm on my windows machine right now...

---

### Post by lykwydchykyn on 2008-10-09
Is apache even installed?  What happened when you ran that command?  Did you get an error?  Did it say it was starting and stopping?

What is the output from:
```

apache2ctl status

```

---

