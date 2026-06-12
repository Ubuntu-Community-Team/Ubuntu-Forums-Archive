---
title: "/var/www Permission Issues"
date: 2011-10-13
forum: Server Platforms
---

### Post by maverickaddicted on 2011-10-13
I created one folder inside /var/www/ named - demo
I have given them the permission using this command - 
sudo chown user2 /var/www/demo/
sudo chmod 775 -R /var/www/demo.


However, when I try to install CMS like Drupal or Joomla, the files are getting created with the owner www-data and read only access to other users. Then, I have to again chmod the directory, but this is annoying. Since chmod is a repetitive process.

I have also added the user2 account in the group members of www-data group.
So, what should I do now, so that every folder created either by using www-data or user2, will have read and write access permission to every users present in the system

---

### Post by Jonathan L on 2011-10-13
> **maverickaddicted said:**
> I created one folder inside /var/www/ named - demo
I have given them the permission using this command - 
sudo chown user2 /var/www/demo/
sudo chmod 775 -R /var/www/demo.


However, when I try to install CMS like Drupal or Joomla, the files are getting created with the owner www-data and read only access to other users. Then, I have to again chmod the directory, but this is annoying. Since chmod is a repetitive process.

I have also added the user2 account in the group members of www-data group.
So, what should I do now, so that every folder created either by using www-data or user2, will have read and write access permission to every users present in the system

Hi 

To get your files writeable by all the people, you have two choices:

[LIST=1]
[*]add all the people to the www-data group, change the umask to 02, and the setgid bit on /var/www
[*]change the umask to 0
[/LIST]

The first is recommended, the second is easier.  The umask filters out permissions, and is set for each kind of program.  How are your users creating files?  If it's FTP you set umask in the FTP server settings, shell in the shell settings, and so on. I believe in Drupal it's done with umask(02); in the settings.php file, or you can do it by adding umask 02 in /etc/apache2/envvars (and restarting apache in either case.)

To get the right group on the subdirectories, you make it have the right group and with 'setgid'. The setgid bit on /var/www will make all subdirectories owned by the same group (and also inherit setgid):
```
sudo chgrp www-data /var/www
sudo chmod ug=rwx,o=rx,g+s /var/www
```/var/www should therefore look like this:
```
drwxrwsr-x 2 whoever www-data 4096 2011-10-13 09:46 www
```You only have to do that once, before the subdirectories are created.  If they already exist you can fix them with
```
sudo chgrp -R www-data /var/www
sudo chmod -R g+w /var/www
sudo find /var/www -type d -exec chmod g+s '{}' ';'

```You change your umask in the running shell with umask 02, or .profile if you want it every time.

What you're describing is quite common, and is exactly how I run a client's web site with about ten users, all in www-data group, all umask 2,  Nonetheless, it's quite an open system; you might want to reconsider it a bit if you think you're at risk from your users in any way.

Hope that gets you in the right direction.

Kind regards,
Jonathan.

---

### Post by maverickaddicted on 2011-10-13
Thank for your reply, I will try that.

---

### Post by maverickaddicted on 2011-10-20
> **Jonathan L said:**
> Hi 

To get your files writeable by all the people, you have two choices:

[LIST=1]
[*]add all the people to the www-data group, change the umask to 02, and the setgid bit on /var/www
[*]change the umask to 0
[/LIST]

The first is recommended, the second is easier.  The umask filters out permissions, and is set for each kind of program.  How are your users creating files?  If it's FTP you set umask in the FTP server settings, shell in the shell settings, and so on. I believe in Drupal it's done with umask(02); in the settings.php file, or you can do it by adding umask 02 in /etc/apache2/envvars (and restarting apache in either case.)

To get the right group on the subdirectories, you make it have the right group and with 'setgid'. The setgid bit on /var/www will make all subdirectories owned by the same group (and also inherit setgid):
```
sudo chgrp www-data /var/www
sudo chmod ug=rwx,o=rx,g+s /var/www
```/var/www should therefore look like this:
```
drwxrwsr-x 2 whoever www-data 4096 2011-10-13 09:46 www
```You only have to do that once, before the subdirectories are created.  If they already exist you can fix them with
```
sudo chgrp -R www-data /var/www
sudo chmod -R g+w /var/www
sudo find /var/www -type d -exec chmod g+s '{}' ';'

```You change your umask in the running shell with umask 02, or .profile if you want it every time.

What you're describing is quite common, and is exactly how I run a client's web site with about ten users, all in www-data group, all umask 2,  Nonetheless, it's quite an open system; you might want to reconsider it a bit if you think you're at risk from your users in any way.

Hope that gets you in the right direction.

Kind regards,
Jonathan.

That somehow work, but If I paste some file from my drive to /var/www folder it is again created with no permissions, but my previous issue is solved. Only this is remaining.

---

### Post by Jonathan L on 2011-10-25
> **maverickaddicted said:**
> That somehow work, but If I paste some file from my drive to /var/www folder it is again created with no permissions, but my previous issue is solved. Only this is remaining.

... sounds like you need to find another umask setting, the one for the desktop manager.

Added: umask in /etc/profile is honoured for the login; but I see that nautilus copies the permissions when files are copied (rather like cp -p) ... not sure if that's changable, but having a look.

Kind regards,
Jonathan.

---

