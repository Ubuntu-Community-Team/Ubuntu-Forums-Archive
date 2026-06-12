---
title: "FTP access to /var/www/"
date: 2008-07-15
forum: Server Platforms
---

### Post by figmented on 2008-07-15
I want to allow FTP access to /var/www/

I'm using vsftpd

/var/www/ is set to "755" with the owner as "www-data" (apache default)

The only "real" user on the server is "figmented"

(I'm not sure what makes the user "real" yet, but I've noticed that "www-data" doesn't have its own "home" dir)

vsftpd uses "real" users as logins so i can login as "figmented" but i can NOT write to files in /var/www/ (since the dir is set to "755" and it has a different owner)

I don't want to change permissions or users...can someone suggest what else I could try to get this to work? if anything, could i just add "root" to the list of users that login via FTP?

I only need to login here-and-there to do some updates...

---

### Post by windependence on 2008-07-16
Can you post your access log?

-Tim

---

### Post by mbeach on 2008-07-16
Having had a similar issue a long time ago except it was with mapped drives, could you change the document root to something in figmented's home directory, and change the group for that folder and all files within to www-data?  

You can try it without disrupting the current setup - if it doesn't work for you, just change the DocumentRoot and directory directives back to what they were and delete the new folder /home/figmented/www.

Create the directory (can be named whatever you like)
> mkdir /home/figmented/www
Copy the contents of /var/www over
> sudo cp /var/www/* /home/figmented/www/
Set the ownership appropriately
> sudo chown -R figmented:www-data /home/figmented/www

the edit 
/etc/apache2/sites-available/default
> gksudo gedit /etc/apache2/sites-available/default
changing the DocumentRoot line to 
DocumentRoot /home/figmented/www

you'll also need to change the 
<Directory /var/www/>
to
<Directory /home/figmented/www/>

then tell apache to reload the configuration
> sudo /etc/init.d/apache2 reload


I'll probably take some opposing views for this suggestion, but its how I think its best setup.  That way, if/when you move away from ftp, to ssh and winscp or whatever, no further changes are required for special access to /var/www and its a gentle introduction to how the virtual hosts conf files are setup, as well as taking the first step towards a virtual hosting setup with multiple users/sites etc.

---

### Post by windependence on 2008-07-16
I don't understand why a simple symlink isn't working here. I have done this myself even in a chroot jail (with a hard link) and it worked fine. Seems like a lot of trouble just to upload you files. Don't have an ftp server on any of my web servers, I just use WinSCP, scp, fugu (on the mac) or sftp in Linux and it works fine. You don't want hundreds of people accessing your web server anyway unless they are developers and then it should be a staging server.

-Tim

---

