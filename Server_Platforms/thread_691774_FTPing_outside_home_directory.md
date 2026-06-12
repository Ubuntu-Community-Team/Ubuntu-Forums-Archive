---
title: "FTPing outside home directory?"
date: 2008-02-09
forum: Server Platforms
---

### Post by xelapond on 2008-02-09
Hello Everyone, 

I am setting up a basic multi-user web, file, git, mail server.  I have mostly everyone working(not mail yet, havn't started).  But I encountered a problem with FTP.  I am using proftpd.

Here is my problem:

when user1 FTPs into the server, all he can see if the home directory.  user1 happens to be the web admin, so he needs access to var/www.  Is there any way to give him access to just his home directory and /var/www?

Thanks, 

Alex

---

### Post by soulresin on 2008-02-09
> **xelapond said:**
> Hello Everyone, 

I am setting up a basic multi-user web, file, git, mail server.  I have mostly everyone working(not mail yet, havn't started).  But I encountered a problem with FTP.  I am using proftpd.

Here is my problem:

when user1 FTPs into the server, all he can see if the home directory.  user1 happens to be the web admin, so he needs access to var/www.  Is there any way to give him access to just his home directory and /var/www?

Thanks, 

Alex

If user1 is the only person that should have access to the files, a couple solutions  would be to make /home/user1 the DocumentRoot for that virtual host and have user1 own all the files.  Or make the home directory for user1 /var/www and chown all the files to that user.

If more than 1 user needs to have access to /var/www, make a group (like webdev or something), and the users to the group and make the directory tree g+rwx.  Set the users' home dirs to /var/www.

Hope that helps.

---

### Post by xelapond on 2008-02-09
Sorry, im really a new to Linux servers.

Would there be anything wrong with just moving the web directory to his home folder?  Which configuration file would I use to move the web directory?  The documentation says /etc/apache2/httpd.conf, but the file is empty.

Thanks, 

Alex

---

### Post by gnaunited on 2008-02-09
This should work (maybe):

ln -s /var/www /home/username/apache

If not, then I don't know. This will just create a link to the other directory in the users home directory.

---

