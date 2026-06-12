---
title: "File Transfer Questions re: rsync / permissions"
date: 2005-04-10
forum: Server Platforms
---

### Post by bcnstony on 2005-04-10
Hello Everyone

I'm running ubuntu HH as a server to host a website. I develop the web pages on my laptop (OSX) and then transfer them over to my ubuntu server. My current transfer method is a bit ugly, I'm wondering what is the easiest way to do this.

I use rsync, but have to transfer to the /tmp directory as I don't have permision in /var/www. I then sudo to root, and cp the files to the right place.

# rsync -v -u -a --rsh=ssh test.html [email]mainuser@mywebaddress.org[/email]:/tmp/
(I ssh in,)
# sudo cp /tmp/test.html /var/www/test.html

Should I enable root and transfer the directories as [email]root@mywebaddress.org[/email]?
Should I do something (I'm a newbie) to the directory permisions in /var/www
Or something else?

thanks for your help

---

### Post by heimo on 2005-04-10
Hi!

I'll give a quick answer. You should check that directories and files under /var/www are owned by a group that your username belongs to, give read/write rights to that group and then use your normal user account to transfer the files.

You can use System->Administration->Users and Groups to create groups and give add user account to group, OR you can edit /etc/group file and add you username after the group (on the same line) - you should probably use pre-existing group www-data for this purpose.

As a root you can do 
```
chgrp -R www-data /var/www/
```to change all the files and directories under /var/www/ to www-data group (except files starting with dot) and then
```
chmod -R g+rw /var/www/

```to give www-data group read and write permissions to all files and directories. Now if your user belongs to group www-data, you can directly copy (scp) stuff to /var/www. You should probably also make sure that the files are owned by username www-data which is the username apache is run by default. (you can check your apache.conf of apache2.conf for lines like:

```
User www-data
Group www-data

```

---

### Post by bcnstony on 2005-04-23
Follow up:

Thanks! I got it working. If anyone else is reading this, they may also need to type in:


```
chgrp -R www-data /var/www/
chmod -R g+rw /var/www/
```


to change the www directory. Type ```
stat /var/www
``` to see the status of the directory and it's group owner, etc.

---

### Post by deuce868 on 2005-04-23
another thing to think about is using a versioning system like CVS or SVN. I use SVN so I can work on a copy of the site and then once I have all the changes made I can 
svn commit

then ssh to the server and just run svn update and it is all synced.

---

### Post by JeremyStein on 2006-09-14
It's probably better to export from the source control system rather than simply include a workspace there.  If you do checkout right to the web server, be sure to set up .htaccess to prevent access to the CVS or .svn directories.

---

