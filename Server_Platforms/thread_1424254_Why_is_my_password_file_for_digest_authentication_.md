---
title: "Why is my password file for digest authentication readable by anonymous visitors?"
date: 2010-03-07
forum: Server Platforms
---

### Post by TheForumDude on 2010-03-07
Why is my password file for digest authentication readable by anonymous visitors?

I have configured Apache to require a password for a folder on my web server using digest authentication.  This involves an .htaccess file, of course, and also a password file which I named passwd.dav.  Everything seems to be working fine, except that I'm shocked that I can access and read the passwd.dav file from any computer with a web browser without even logging in!!!  ...yet I have to log in in order to access the folder that it protects.  So the passwd.dav is working in that it's helping to enforce authentication against the folder I want to protect, but yet anyone can see the passwd.dav file!  How can I make is so that web browsers can not request and read the passwd.dav file?!?

My first thought was that this must have something to do with permissions.  So I locked down the permissions on both the .htaccess file and the passwd.dav file using the following command...

chmod 600 .htaccess
chmod 600 passwd.dav

This means that the owner of the file has read and write access to the files, but the group and all other users have absolutely no access.  So why can anonymous visitors read my passwd.dav file?!?

I set the owner:group to www-data:www-data as this was necessary in order to get WebDAV to work according to the instructions I followed.  Likewise, if I change the owner:group to something like root:admin, then that solves the problem and anonymous visitors can't read the passwd.dav file, but it breaks WebDAV.  I have to have the owner:group set to www-data:www-data it seems.

By[FONT=Verdana] the way, when someone goes to [http://www.myserver.com/WebDAV/passwd.dav](http://www.myserver.com/WebDAV/passwd.dav), this is what they see...
[/FONT][FONT=Verdana]my_username:realm_name:41fa19ca1004220f14495e3be9ec9419

...where "my_username" is the name of my user and "realm_name" is the name of the realm.

For some reason, this is not a problem with my .htaccess file.  No one can read that one except me when I'm logged in as root.

Can someone please tell me (1) why any visitor can read passwd.dav despite the strict file permissions and (2) how I can lock down the file so that no one can ready it but yet still allow WebDAV to work.

Thanks in advance for any assistance!

- TheForumDude

[/FONT]

---

### Post by Jive Turkey on 2010-03-09
First, your passwd.dav file MUST live outside of your webserver's document root, ie /var/www.  /var would be fine, just remember to update the htaccess file that references it with the correct path.  

Regarding the permissions, if apache owns/has read permissions, it can serve the file over http if it in the document root and no directive exists to the contrary (in either .htaccess, httpd.conf, or whatever virtual host file you have for the site).  In addition to moving the passwd file outside of the document root of the site it would be a good idea to bone up on htaccess rules.  You can restrict what files, or types of files apache will serve to the public, and lock down the server a bit more.

---

