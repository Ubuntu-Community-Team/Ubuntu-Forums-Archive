---
title: "FTP to /var/www owned by root"
date: 2011-07-03
forum: Server Platforms
---

### Post by norjms on 2011-07-03
Hello, 
     I have a ubuntu lamp server setup and working. The issue I am trying to overcome is the the /var/www directory is owned by root. I am trying to remotely upload content from my development machine using FTP. I don't know what the "right" way to setup remote ftp to the /var/www directory.I don't want to introduce serious security holes but, I do want to be able to just click publish from my dev box. A tutorial would be great if anyone knows of a good one. If not just letting me know what I am supposed to do.

James
ubuntu 11.04 x64

---

### Post by Lars Noodén on 2011-07-04
The right way is to use SFTP instead of FTP.  FTP is insecure.  SFTP is part of the package OpenSSH-server and installing that package will set you up with a working, configured [SFTP](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/SFTP).

---

### Post by rudelgurke on 2011-07-04
Create an user that "owns" the webroot /var/www and make this directory group-writeable to www-data - then login via FTP with this user.
Or create a Vhost - specially if you're serving multiple sites with your webserver - doing the same as above.

And - sftp won't help uploading files as root - except you allow a root login via SSH which is a bad bad idea.

---

### Post by Lars Noodén on 2011-07-05
> **rudelgurke said:**
> ... and make this directory group-writeable to www-data - then ...

Avoid using the group **www-data**.  That group is the group that the web server runs as and giving write access to it will give write access to the web server, and that will leave you vulnerable to a lot of bad things.  

Create a new group for those activities, **webmasters** or something like that, and add users to it and use that instead.

---

### Post by patmaherjfm on 2012-12-24
> **rudelgurke said:**
> Create an user that "owns" the webroot /var/www and make this directory group-writeable to www-data - then login via FTP with this user.
Or create a Vhost - specially if you're serving multiple sites with your webserver - doing the same as above.

And - sftp won't help uploading files as root - except you allow a root login via SSH which is a bad bad idea.

how do you create a user  that owns the web root ?

---

### Post by OliverHaslam on 2012-12-27
I'd be interested in this too. I was having issues having Wordpress update itself, and was told to set the /var/www/wordpress directory to be owned by www-data, which I did. As that's the user that runs Apache, the updates now work fine.
 
Was that not a good idea?
 
Cheers.

---

### Post by Wim Sturkenboom on 2012-12-28
Personally I move web directories out of /var to the user's home directories; that way I don't have to fight with permissions and I can easily jail users to their home directory.

If interested, see post #10 in [http://ubuntuforums.org/showthread.php?t=2070802](http://ubuntuforums.org/showthread.php?t=2070802) ; start where it says 'mkdir website1'.

---

