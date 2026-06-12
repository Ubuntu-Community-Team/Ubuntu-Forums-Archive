---
title: "PECL Error on Mail Server"
date: 2011-05-27
forum: Server Platforms
---

### Post by tyelford on 2011-05-27
Hi all,

I am currently installing a mail server to handle email for our clients, I have started this server from scratch using Ubuntu server 11.04.

So far I've installed Exim, SA, Dovecot, and Clam AV and those all seem to be working as they should, I can send and receive email...

I am now trying to set up Horde, Horde 4 to be exact, I have been following the documentation on the Horde site :
[http://www.horde.org/apps/horde/docs/INSTALL](http://www.horde.org/apps/horde/docs/INSTALL)

Part 4, it is recommended to install certain PECL modules, and I would like these as well.
I have been pounded my head to try to get these to go, but just can't get past some of the error messages like this, for the first one:

# pecl install fileinfo
WARNING: "pear/Fileinfo" is deprecated in favor of "channel://php-src/ext/fileinfo/in php sources"
downloading Fileinfo-1.0.4.tgz ...
Starting to download Fileinfo-1.0.4.tgz (5,835 bytes)
.....done: 5,835 bytes
3 source files, building
running: phpize
Cannot find config.m4.
Make sure that you run '/usr/bin/phpize' in the top level source directory of the module

ERROR: `phpize' failed

Does any one know what this error mean. From what I can gather, it's looking for the phpize when the module is to be installed, however, how can I put the phpize file (or link) in the top level of the source directory before I have the source?

Any insight would be great

Tyson

---

### Post by rudelgurke on 2011-05-27
Installing the php5-dev package should help to solve this problem. And a note - if you want to get Horde4 running, don't follow their INSTALL file because that one is pretty outdated (and wrong).
With version 4 the Horde developers decided for some weird reason to split everything up into modules so installing it by pear is recommended to get anything it needs to run.
Just downloading the Tarball won't be enough because a lot of required libraries are missing.

---

### Post by tyelford on 2011-05-27
I already have the php5-dev installed, I tried to upgrade and it's at the lastest version.

When I installed horde using pear, everything goes ok and it starts to work, for example, I can goto http://<ipaddress>/horde/test.php (or something similar) and it opens a page which describes which packages are installed and which are not.  

The ones that are not installed are mostly the PECL ones listed on the horde website.

---

### Post by tyelford on 2011-05-29
> **rudelgurke said:**
>  And a note - if you want to get Horde4 running, don't follow their INSTALL file because that one is pretty outdated (and wrong).


Also, would you know where a better guide is. Doing a google search around obviously brings up tons of different choices but I dont know which ones are good and which ones are not

---

### Post by tyelford on 2011-05-31
Just tried these two steps as well:

apt-get upgrade php5-dev

This upgraded a bit and then said something about try with --fix-missing so:

apt-get upgrade php5-dev --fix-missing

This took a while and looked like it did a lot of extra, next:

pecl install fileinfo

Same error as first post, does anyone have any more suggestions about this problem?

---

### Post by ChristianSL on 2011-07-27
Same problem here @ lucid...
Does anybody know how to fix?

---

### Post by blindzero on 2011-09-14
Anything new on this topic?
I have the same issue here with some old hardy server...Fileinfo is failing because of config.m4 not found...:(

---

### Post by jazzon on 2011-10-09
same issue here on 10.04   HEEEEEEEEEEEEEELLLLPPPP!

---

### Post by jazzon on 2011-10-09
Took me all day to make this work, but here ya go!

[help.ubuntu.com]("https://help.ubuntu.com/community/Horde4%20Mail%20And%20Groupware%20Server")

---

### Post by gunthr on 2012-01-21
@Jazzon

I'm using your guide to set this up. I installed a fresh copy of 10.04 LTS with only sshd and LAMP. Did all updates, basic networking configuration.

I'm running into trouble at:

> Install The Required Modules
Move to where we want to be and install the first package:

cd /build/buildd/php5-5.3.2/pear-build-download

I don't have that directory, am I supposed to make it?

I made it and get the same *pecl install fileinfo* errors these folks are getting. 

Any ideas?

Thanks!

---

