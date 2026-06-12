---
title: "WWW Directory Permissions"
date: 2011-04-28
forum: Server Platforms
---

### Post by rainleader on 2011-04-28
I've got a new Ubuntu 10.10 server with LAMP configured on it and have a question as to what is the "optimal" security configuration for a Wordpress site. Currently, my website's root directory is /var/www. Here's what I've done so far:

[LIST]
[*]Added my user account to the www-data group
[*]chown -R www-data /var/www
[*]chgrp -R www-data /var/www
[*]chmod -R 755 /var/www
[/LIST]

But, it looks like Apache does NOT have write access under this configuration (I have to chmod to 775, temporarily). Also, when I login via SFTP, my user account does NOT have write access (to upload files, I have to temporarily chown -R myuser /var/www and then switch it back to www-data when I'm done -- not ideal).

My question:

[LIST=1]
[*]Is there a way I can retain write access for my account while allowing Apache to also have write access (e.g. Wordpress auto-matic update)?
[*]Also, is it safe to leave the permissions on /var/www as 775 instead of 755?
[/LIST]

---

### Post by rubylaser on 2011-04-28
Apache should be running as the www-data user unless you've changed the user that it's running under. You can view this by checking these two files...
```
root@svr-cc-web:/etc/apache2# cat /etc/apache2/envvars | grep APACHE_RUN_USER
export APACHE_RUN_USER=**www-data**
root@svr-cc-web:/etc/apache2# cat /etc/apache2/apache2.conf | grep APACHE_RUN_USER
User ${APACHE_RUN_USER}

```

You shouldn't operate with 775 permissions on /var/www and I really like to let root own /var/www and have www-data:www-data be the user and group on the applications inside /var/www.

---

### Post by rainleader on 2011-04-28
Hmm... Thanks for the tip on letting root own /var/www. 

Apache is definitely set to use www-data. Still not sure why I don't have write access if my user account is a member of the www-data group.

---

### Post by rubylaser on 2011-04-29
Have you verified that your user is part of the www-data group?
```
root@svr-cc-marketing:~# groups rubylaser
```

I'm not sure why you're trying to write with your user to /var/www that should be left to the www-data user via your application, which should work fine if www-data is the user and group and the permissions are 755.

---

### Post by rainleader on 2011-04-29
Verified I'm in the group. I was trying to write to it when uploading the initial files via SFTP from my local machine since I don't have access to the www-data account.

It seems like, although I'm in the www-data group, I can't write to /var/www unless I temporarily set my user account to the owner.

---

### Post by rubylaser on 2011-04-29
Now, I understand what you're trying to do.  The reason your user won't work is the 755 permissions.  The www-data user has rwx permissions, but the group permissions are 5, so you only have 5 read and execute access.  

What sort of stuff are you trying to do via sftp in this folder?  If it's just uploading new applications, I'd do that with the root user, then chown the directory, and if it's to make changes to your site, I'd probably do those as root as well (or scp them over to your user account, and sudo cp them into their final location).  Finally, if it isn't a public website, just change the permissions for the time being while you develop, and change the permissions back before deployment.

---

### Post by rainleader on 2011-04-29
That makes much more sense, thanks! What would you leave the /var/www as 755 with ww-data being the owner + group of application files (in a production environment)?

---

