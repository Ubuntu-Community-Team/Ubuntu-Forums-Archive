---
title: "Updated to 18.04 .. phpmyadmin updated, overwrote local config. help?"
date: 2020-05-17
forum: Server Platforms
---

### Post by nyktovus on 2020-05-17
Long story short, during the update PHPmyAdmin updated and i dont know how or when, but it overwrote the local config and seems to be in a default state. 

Any idea how i can retrieve or view the databases that existed? mostly wordpress sites.. etc.. 

Would love to know if theres a way to UnHose my situation. 

nyk.

---

### Post by LHammonds on 2020-05-18
Easy to unhose if you made backups.  Do you have "any" backups?

LHammonds

---

### Post by nyktovus on 2020-05-18
if there are backups. i dont know where they were stored.

---

### Post by nyktovus on 2020-05-18
SO basically aside from restoring from a backup.. when the update went thru and confirmed whether to use the maintainer version of the file or keep the local copy: that wiped out all the databases ?

---

### Post by LHammonds on 2020-05-19
I do not use phpmyadmin but I assume if you told it to overwrite a config file, it is just the config file.  MySQL/MariaDB databases will not get purged / deleted because of an upgrade.  They are still there and probably still running just fine.

You just need to re-configure phpmyadmin exactly how you did it the 1st time when you set it up.

If you can access your server via SSH, you can use the command-line "mysql" and type "show databases;" to see all your databases.

If re-configuring phpmyadmin is too problematic, you might want to look at an alternative such as [adminer]("https://www.adminer.org/") which is a single php script and can connect to a wide variety of database backends.  (FYI - I am not affiliated with adminer, I just like its simlicity....but I prefer the mysql console)

> **nyktovus said:**
> if there are backups. i dont know where they were stored.
If I were you, I would setup a new/blank server and then install the software needed to make it like the other, then figure out what configuration / data needs to be migrated to the other server to make it work the same way.  The "configuration / data" you migrate is what you need to backup to another location on a regular basis in case you lose that machine.  I would also include the documentation on what/how to install a new server as part of that data that gets backed up.  Just imagine losing the server and only having the backup.  You will need to setup a new server, install software and restore the configuration / data.  Never assume a backup is magically made for you.

This is why I document how to install my servers from scratch on [my forum]("https://hammondslegacy.com/forum/viewforum.php?f=40").  If I only have the data in a backup location, I will know how to install a server from scratch and restore the data.

LHammonds

---

### Post by nyktovus on 2020-05-20
OMG. thank you!! Show databases shows all my things.. now i guess the bigger question is how can i fix the phpmyadmin interface and access these?
Should i and HOW do i back them up from here?
Would love the help. total mysql tard. 
I'm learning. 

I'm stoked to have found them.  but I dont know how to rescue. and building another server isnt really an option.

---

### Post by nyktovus on 2020-05-20
when i hit MySite/phpmyadmin atm it shows.. > <?php
/* vim: set expandtab sw=4 ts=4 sts=4: */
/**
 * Main loader script
 *
 * @package PhpMyAdmin
 */
use PMA\libraries\RecentFavoriteTable;

/**

---

### Post by nyktovus on 2020-05-20
The wordpress sites only render : > <?php
/**
 * Front to the WordPress application. This file doesn't do anything, but loads
 * wp-blog-header.php which does and tells WordPress to load the theme.
 *
 * @package WordPress
 */

/**
 * Tells WordPress to load the WordPress theme and output it.
 *
 * @var bool
 */
define( 'WP_USE_THEMES', true );

/** Loads the WordPress Environment and Template */
require( dirname( __FILE__ ) . '/wp-blog-header.php' );

I'm assuming it wouldnt take much to repoint the database to the right.. thing?

---

### Post by LHammonds on 2020-05-20
Editing gone horribly wrong...see next post. ;)

---

### Post by LHammonds on 2020-05-20
Let's step back for a second.  You never mentioned what you were running before the upgrade or what you are running now...other than 18.04

Were you on Ubuntu Server 16.04 and then 18.04 or did you go from some other version?  Please list what you are running currently.

Looking back at my tutorials, I initially installed the following versions for each OS:

Ubuntu 16.04 - Apache 2.4.18, PHP 7.0.2, MariaDB 10.1.28 and WordPress 4.4.2.
Ubuntu 18.04 - Apache 2.4.29, PHP 7.2.7, MariaDB 10.1.29 and WordPress 4.9.8.
Ubuntu 20.04 - Apache 2.4.41, PHP 7.4.3, MariaDB 10.4.13 and WordPress 5.4.1

Looking at a current, fully patched install of 18.04, I have: Apache 2.4.29, PHP 7.2.24, MariaDB 10.3.23 and WordPress 5.4.1.

> **nyktovus said:**
> I dont know how to rescue. and building another server isnt really an option.

If it were me and I only had a single server on a bare-metal install, I would use VirtualBox on my PC to build up the server how it is running now but using the newer OS.  I would then copy over the configuration files (or make changes to the new versions by incorporating what is different in the old one) and copy the data over.  Once I got everything working in the virtual machine on my PC, I would not only have a better knowledge of how to upgrade the one-and-only server but also have a live-running copy on my PC should anything terrible happen to the one-and-only physical server.  Also, once you upgrade your physical server (such as format and re-install) with the new OS, you can directly migrate the configuration files and data you already have running on the new version in your virtual machine on your PC.

LHammonds

---

### Post by SeijiSensei on 2020-05-20
If you see the underlying code in WordPress rather than the rendered page, you are most likely missing the **libapache2-mod-php** module.

---

### Post by LHammonds on 2020-05-20
> **SeijiSensei said:**
> If you see the underlying code in WordPress rather than the rendered page, you are most likely missing the **libapache2-mod-php** module.But if he is missing that, he will likely be missing other required modules...thus the need to know what version of apache he is running along with the version of PHP and WordPress.

---

### Post by nyktovus on 2020-05-20
sorry. i was running ubuntu server 12 lts with a LAMP stack that was succesfully updated to 16.04lts and was running that for years. ran the dist-upgrade over the weekend and thats when i found the php sites didnt work
 phpmyadmin and wordpress .. but thanks to you guys i can see the databases are still there. 
Ill see if i can find a how to on that apache module

---

### Post by nyktovus on 2020-05-20
is there an easy command that will spit out what versions of apache (2 im guessing) php and likely wordpress 5 sites

> apache2 -v
php -v 

answered my own q.

---

### Post by nyktovus on 2020-05-20
Found some info on what its running now.. 


Server version: Apache/2.4.29 (Ubuntu)
Server built:   2020-03-13T12:26:16

PHP 7.2.24-0ubuntu0.18.04.4 (cli) (built: Apr  8 2020 15:45:57) ( NTS )
Copyright (c) 1997-2018 The PHP Group
Zend Engine v3.2.0, Copyright (c) 1998-2018 Zend Technologies
    with Zend OPcache v7.2.24-0ubuntu0.18.04.4, Copyright (c) 1999-2018, by Zend Technologies


is there anyway i can figure out what versions were running when it was on 16.04LTS? or does that even matter now?

---

### Post by nyktovus on 2020-05-21
ok acording to /etc/apache2/mods-available/

there are php5.conf and php5.load
as well as php7.2.conf and .load

neither of which are enables in mods-enabled/

---

### Post by LHammonds on 2020-05-21
Ok, that helps me identify which commands need to be run.

These are the commands I run on a clean server in preparation to run a wordpress site on Ubuntu 18.04 ([reference link]("https://hammondslegacy.com/forum/viewtopic.php?p=669#p669")):

```

apt-get -y install libapache2-mod-php7.2 php7.2-mysql php-ssh2 php7.2-tidy php7.2-curl
apt-get -y install php7.2-gd php7.2-xmlrpc php7.2-pspell php-imagick php7.2-imap php7.2-xsl
phpenmod imap
phpenmod json
systemctl restart apache2

```

You probably have several of these already installed but shouldn't hurt what you already have.

Once that is done, see if the web page will load.  If not, the next step is to see what version of wordpress you are running.

One method (iirc) to see what you have from the command line is to look at a "version.php" file...under the wp-includes folder...I think.  Open it with an editor and look near the top (should not need to scroll down) for an indication as to what version it is.

If you have not updated it recently, it is probably a good time to do so but FIRST, you need to have a good backup of your database and website files.  We can discuss more after you do these steps first.  Priority is to get the site running....then we can look at making backups and upgrading.

LHammonds

---

### Post by SeijiSensei on 2020-05-21
BTW, using the lamp-server package will avoid all these issues.  It will install Apache, MySQL, and PHP and any interstitial software needed.

```
sudo apt install lamp-server^
```

The tilde ("^") is required.

---

### Post by LHammonds on 2020-05-21
> **SeijiSensei said:**
> BTW, using the lamp-server package will avoid all these issues.  It will install Apache, MySQL, and PHP and any interstitial software needed.

```
sudo apt install lamp-server^
```

The tilde ("^") is required.
Except we don't know if he is running MySQL or MariaDB and don't want to hose up his database install.

---

### Post by nyktovus on 2020-05-21
> **LHammonds said:**
> Ok, that helps me identify which commands need to be run.

These are the commands I run on a clean server in preparation to run a wordpress site on Ubuntu 18.04 ([reference link]("https://hammondslegacy.com/forum/viewtopic.php?p=669#p669")):

```

apt-get -y install libapache2-mod-php7.2 php7.2-mysql php-ssh2 php7.2-tidy php7.2-curl
apt-get -y install php7.2-gd php7.2-xmlrpc php7.2-pspell php-imagick php7.2-imap php7.2-xsl
phpenmod imap
phpenmod json
systemctl restart apache2

```

You probably have several of these already installed but shouldn't hurt what you already have.

Once that is done, see if the web page will load.  If not, the next step is to see what version of wordpress you are running.

One method (iirc) to see what you have from the command line is to look at a "version.php" file...under the wp-includes folder...I think.  Open it with an editor and look near the top (should not need to scroll down) for an indication as to what version it is.

If you have not updated it recently, it is probably a good time to do so but FIRST, you need to have a good backup of your database and website files.  We can discuss more after you do these steps first.  Priority is to get the site running....then we can look at making backups and upgrading.

LHammonds


ok.. i ran those commands you listed.. and still the wordpress sites show only 

```
<?php
/**
 * Front to the WordPress application. This file doesn't do anything, but loads
 * wp-blog-header.php which does and tells WordPress to load the theme.
 *
 * @package WordPress
 */

/**
 * Tells WordPress to load the WordPress theme and output it.
 *
 * @var bool
 */
define( 'WP_USE_THEMES', true );

/** Loads the WordPress Environment and Template */
require( dirname( __FILE__ ) . '/wp-blog-header.php' );
```


As for the wordpress version its
> $wp_version = '5.2.6';


I really appreciate the help..

---

### Post by LHammonds on 2020-05-21
Your WordPress is not horribly out of date so it should not be a compatibility issue with the app itself.

Now we need to see if the php mod is enabled.  What does this command show?

```
ls -l /etc/apache2/mods-enabled/php*
```

If it does not show php7.2.conf, then you need to enable it using this command:

```
sudo a2enmod php7.2
sudo systemctl restart apache2
```

**EDIT:** Also, I am assuming you are accessing the site in a browser using http:// instead of files://

---

### Post by nyktovus on 2020-05-22
OHHHH SNAPPPPPP!!!!!
 Guess whos back online!!!


yeah dude, not only was your assumption of how to fix it was right.. but yeah, i was accessing everything via http:// 

I kinda had a hunch last night when i noticed php wasnt in the mods enabled section. but i was super gunshy about flipping that switch and watch it wipe it all out.. hehehe.. 

I'm back in.. and the first thing i'm doing is a backup. thanx again!

---

### Post by ajgreeny on 2020-05-22
Brilliant!
Please mark as SOLVED from the Thread tools up top; it's  a great help to users searching the forums.

---

### Post by LHammonds on 2020-05-22
Awesome to hear.

Make sure your backup includes the following and make sure it is copied someplace other than that machine:


[list]
[*]mysqldump of all databases
[*][export the users/privileges](https://hammondslegacy.com/forum/viewtopic.php?p=870#p870) (because the individual databases do not contain user info except "mysql" which is not something you always want/can import)
[*]Backup config files in /etc
[*]Backup your private/public SSL certificates
[*]Backup your web files in /var/www
[/list]


Once you have a good backup, upgrade your wordpress plugins/themes if have any, then upgrade wordpress according to [their recommendations](https://wordpress.org/support/article/updating-wordpress/).

Keep an eye out for Ubuntu Server 20.04.1 LTS (1st point release) and prepare for upgrading to that version.  Again, I recommend setting up a virtual machine on your PC with 20.04 on it and get a working copy on the upgraded platform before attempting to do on a physical box (so you always have the experience/data to pull from...and in a dire emergency, can re-direct traffic to your VM. LoL

LHammonds

---

