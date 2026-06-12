---
title: "Apache /var/www permissions for a public server?"
date: 2007-12-22
forum: Server Platforms
---

### Post by Webu on 2007-12-22
Hey everyone \\:D/

I've got my LAMP configuration working properly on Ubuntu Server 7.10 (it's so great over Windows), all contents are under /var/www with default permissions and as you can suppose, i have to use sudo for all file transfering and editing (and i can't use software like WinSCP yet).

I've been reading a lot of different topics around Apache permissions, but most of them focus on local and development usage so i didn't get clear answers how should i set these things for public usage (hosting a few websites).

1. I'd like to have (as an admin) one main user who has access to all contents of /var/www for easily managing and editing them. Am i right that the most recommended + proper (and a safe) way to do this is simply creating a new usergroup, giving that group (full) access for /var/www and adding myself to it (maybe an another admin later)?

2. What's the best way to do the above thing for just a single website like /var/www/gamingsite (for it's owner to be able to edit and manage his/her site and content freely)?

2b. Maybe the same way i already suggested in first question, just giving the access for that particular directory?

2c. Do i need to do something special to prevent access for all the other directories where he/she shouldn't have access to?

Thanks for your great support, remember to have a [COLOR="Red"]Merry Christmas[/COLOR] ;-)

---

### Post by X40nick on 2007-12-22
sudo nautilus

Then just change the permissions of /var/www

---

### Post by Webu on 2007-12-22
Isn't Nautilus a GUI? Since i'm running an Ubuntu Server i'm not able to use that :-? Sorry to say but i'm afraid you didn't read my questions properly #-o

---

### Post by rsw686 on 2007-12-22
What I do is create a new user for the site. The website is stored in the user's public_html directory. A virtual apache server is configured pointing their domain name to that location. You can add additional user's, just have add them as part of the website user's group.

If you are planning on hosting multiple websites you need to read up on suexec and suphp. Unless you have alot of time on your hand to test and lock down the machine your better off only allowing users who you know won't do anything harmful and will use secure passwords.

By default all scripts run as the www-data user. This means the scripts can change any file writable by www-data and read any file readable by www-data. So if a forum password is stored another user could grab it and start changing the database or files.

Suexec runs cgi-scripts under the user that owns the file. Suphp is used for running php scripts under the file's owner. Htscanner should also be installed to allow php flags in htaccess files.

Most likely you'll need to recompile suexec. Atleast from my experience with apache2 on fedora the docroot is locked to /var/www. Meaning that the scripts stored under /home can't run. You'll also need to disable the uid/gid check or add in another user to allow in the code if you have shared cgi-scripts like awstats. Alternatively you can just place a copy of the script in each user's directory, however this doesn't work for webmail apps.

---

### Post by dantrevino on 2007-12-23
create a non-admin user for your website ('gamingsite').  Then
```
chown -R gamingsite /var/www/gamingsite
```
and
```
chgrp -R www-data /var/www/gamingsite
```

www-data is the user that will be used by the apache process to access files.  So that group needs only read access to your files, unless you'll be using a web-based application to modify them (for instance a theme editor).

Take special care of your file permissions.  Especially, make sure your configuration files are not world readable.

---

