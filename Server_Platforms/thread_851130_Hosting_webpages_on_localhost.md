---
title: "Hosting webpages on localhost"
date: 2008-07-06
forum: Server Platforms
---

### Post by -ronin- on 2008-07-06
We've got a fileserver (Hardy) at our university, serving Hardy clients (Laptops & Desktops), with a handful of Windows clients here and there. I need to set up the following things for students, professors and other staff.

I want these individuals to each have their own limited webspace on our fileserver. That is, when you're on our Intranet and you type http://<ip_of_fileserver>/<username> into your broswer, it should take you to the index.html of their personal web directory, which I assume must be a subdirectory in /var/www/ on our fileserver.

How do I set this up? Do I create a pub directory under each user's home directory? Or is it simply a matter of creating directories for each user under /var/www/?

What I want is for these directories to be the same as their usernames. I want the owners of these directories to have to upload their pages with ftp, for example. I need them to log in with the same username and password they use for logging into the Hardy workstations at the lab. This way, I won't have UserA mucking about in the web directory of UserB. 

It's a Sunday afternoon, and I'm wondering what's the quickest way of getting this set up before tomorrow?

Thank you :)

---

### Post by ibutho on 2008-07-06
If the users have a home directory on the server, you can just enable the userdir apache module. Usually ~/public_html is set as the default directory for a users html files, but you can change it to something like www or whatever you want. You need to make sure that the home directories and the directories containing the users web files have permissions of 755. Users can then enter something like [http://fileserver/~username](http://fileserver/~username) in order to see their web files.

---

### Post by -ronin- on 2008-07-06
cool, thanks! that worked! but the fileserver is not accepting ftp connections :-(

---

### Post by osjak on 2008-07-06
> **-ronin- said:**
> cool, thanks! that worked! but the fileserver is not accepting ftp connections :-(

You need to install and configure an FTP server for that. For example:
```
sudo apt-get install vsftpd
```
And configuration instructions can be found here:
[http://ubuntuforums.org/archive/index.php/t-91887.html](http://ubuntuforums.org/archive/index.php/t-91887.html)

---

### Post by bvidinli on 2008-11-09
have a look at ehcp,
it may be suitable for your needs..
[www.ehcp.net](www.ehcp.net)
or 
[http://ubuntuforums.org/forumdisplay.php?f=180](http://ubuntuforums.org/forumdisplay.php?f=180)

it is a hosting control panel for Ubuntu

---

