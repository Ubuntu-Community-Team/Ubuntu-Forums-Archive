---
title: "Perfect apache - ftp - administrative user configuration"
date: 2008-11-03
forum: Server Platforms
---

### Post by drdre on 2008-11-03
Hi,
I have the apache user www-data, my administrative user (lets call him fred who has sudo) and maybe some ftp users.

I've decided to put all my sites as subfolders in /var/www/ (unless someone points out a much improved way)

Whats the perfect way to setup the permissions safely with out having to deal with it all the time?

Should fred get to chown everything then share with apache? or some combination of group sharing?  I'm sure there must be some accepted practice I couldnt quite google.

Any help greatly appreciated!

Thanks!

DRE

---

### Post by drdre on 2008-11-04
I'm thinking they should all be in the same group. But who should own, and what group? Or am I on the wrong track.

Puhleeze?

---

### Post by Ric_ on 2008-11-04
Do multiple users have their own sites on this server? If so you could use the userdir module

as root run:

a2enmod userdir

Now when a user creates a public_html folder in their home dir, they have the web url of:

[http://www.yourdomain.com/~username](http://www.yourdomain.com/~username)

If you want user "fred" to have his own web address just set up a virtual host and point it to to /home/fred/public_html

First edit /etc/apache2/apache2.conf and at the bottom add the lines

NameVirtualHost YOURIP:80
NameVirtualHost *:80

restart apache.

create a file in /etc/apache2/sites-available called <yourdomain>

<VirtualHost YOURIP:80>
  ServerName YOURDOMAIN.TLD
  ServerAlias [www.YOURDOMAIN.TLD](www.YOURDOMAIN.TLD)
  ServerAdmin [email]yourname@yourdomain.tld[/email]
  DocumentRoot "/home/fred/public_html/"
  ErrorLog "/var/log/fred-error.log"
  CustomLog "/var/log/fred-access.log" combined
</VirtualHost>

then run the command:

a2ensite <yourdomain>

And you should now be able to browser to your url.

This way is a lot more secure then adding everyone to the www-data group!

hope that helps.

Ric

---

### Post by drdre on 2008-11-05
Ric, thanks for the response!  

So then to give apache the correct rights for that, what would I do?  This is for a blog and for some homegrown php apps so just read write access I think.  Would I put the apache user in that group?

Also, then if I were to setup a ftp server. Would there be any specific user configuration steps?

I feel like I'm a bit confused on the best way to manage the users and how they interact with each other and the file system and the overlaps.  

Thanks again!
DRE

---

### Post by Ric_ on 2008-11-10
Sorry for the slow reply!

From memory once public html is created and apache has the module loads its all good to go. No messing about with permissions. (I'll double check this on a VM for you its been a while)

I recommend proftpd for your FTP server. Then the stock install will be good. Just remember to upload into the public_html dir to put files on your site.

Ric

---

