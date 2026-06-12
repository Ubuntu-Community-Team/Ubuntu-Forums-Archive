---
title: "FTP server"
date: 2008-10-21
forum: Server Platforms
---

### Post by eludlow on 2008-10-21
Hi all.

Just setting up my first true Ubuntu "server" and have now got around to setting up FTP.

I've installed vsftpd and the vsftpd module for webmin but am very unsure of where to go from here.

I've got local users set up so they can FTP into their home directory, but I'd also like certain users to be able to FTP into /var/www/

Is the best way to do this to create a user and set their home directory to /var/www so they can then just FTP to that as a normal user?

Is there anything to stop multiple users having the same home directory?  For instance I could have several users all using /var/www?

Thanks,
Ed Ludlow

---

### Post by eludlow on 2008-10-21
Solved myself!

---

### Post by TreeFinger on 2008-10-21
> **eludlow said:**
> Solved myself!


Can you explain how? I am going to be doing something similar because I just set up a web server and would like to have users be able to ftp into their website folder to create their own web sites.

---

### Post by eludlow on 2008-10-21
I've just created new users and set their home directories to be subdirectories of /var/www.

So userA will have /var/www/userA etc

Then just allowed local users under the vsftpd, and after a little bit of playing, making sure all users are in the same group, which then owns /var/www, all is well.

Ed

---

### Post by lykwydchykyn on 2008-10-21
The more traditional way of doing this is to enable the "userdir" module in apache.  Then users have a public_html folder in their home directories, and any files placed in those directories are published in [http://server/~username/](http://server/~username/)

That way, you don't have things like .bashrc and .bash_history being published to the web.

---

### Post by eludlow on 2008-10-22
Brilliant, thanks lykwydchykyn.

Ed

---

### Post by tubezninja on 2008-10-22
I have a number of users on my servers who need easy access to more than one directory in /var/www.  A lot of times these are web apps that can't/shouldn't appear as /~user/ in the URL.  For these situations, I create create symbolic links into the user's home directory that point to the locations in the webroot.

```
sudo ln -s /var/www/$directory /home/$user/$shortcut_at_users_home_dir
```

This way, the user sees these directories in their /home, making it easier for them.

Also, proper permissions/ownership need to be set on the target directories so that the user can do what they need to do.

---

### Post by y@w on 2008-10-22
Another great way to do this is to use something like the [Virtualmin]("http://virtualmin.com/") module in Webmin. You can setup user accounts and let them manage their FTP settings, MySQL databases, etc..

---

