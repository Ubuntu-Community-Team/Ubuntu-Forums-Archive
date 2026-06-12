---
title: "I'm in permission hell with LAMP..."
date: 2010-12-07
forum: Security
---

### Post by Wolf_22 on 2010-12-07
I have a LAMP installation and I'm struggling with permissions. I have PHP5 installed and my web directory is your standard vanilla setup with the "www" directory being within "var". I use WinSCP3 a lot for my server access / administration stuff and while trying to use PHP to create a simple txt log, I wound up with the following error being generated:

> **Warning**:  fopen(../log.txt) [[function.fopen]("http://139.102.68.177/function.fopen")]: failed to open stream: Permission denied in **/var/www/includes/tracker.php** on line **14**The "tracker.php" file is nothing more than a simple script that's supposed to create that text file with details about the visitor of the web page. From what I understand, PHP is having problems creating the txt file due to permissions.

This permission stuff is hard to get the head wrapped around! Any insight into this is appreciated. In case you're curious, index.php requires tracker.php and the folder tracker is in is set to "777" (which is bad, I know, but I was desperate) and I've set "www" to "755". 

Any insight into this is appreciated.

---

### Post by bodhi.zazen on 2010-12-07
See :

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

Ownership and permissions should be either 

root.www-data or www-data.www-data

permissions 770 on directories (in /var/www), 440 on static files, 660 on dynamic files.

---

### Post by anomie on 2010-12-08
Are you using open_basedir in /etc/php.ini? 

Also, you might want to test creating log.txt using an *absolute* path instead (to make sure it's really being created where you think it is).

---

