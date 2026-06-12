---
title: "Restricting file listings etc."
date: 2010-11-07
forum: Security
---

### Post by ilppi on 2010-11-07
Hi. We set up a server with my friend (still newbies :)) a couple of months ago using Ubuntu 10.04 LTS server edition and agreed to let some folks at school to use it to install drupal on it for teaching and learning purposes. So the idea is that there are multiple users that all install drupal in their home folders separately using SSH and continue from there on etc.

Everything is set up for that to work (domain, settings etc), but there's one thing nagging me, and that's how everyone can look at everything on the server. They dont have rights to modify anything but can look at file listings and view inside files etc.

So how do I restrict the viewing rights of users to inside their home folder, BUT so that they can use the cd command to go to folders inside their home folder, but not outside of it. As far as I know rbash purely keeps you inside home and allows nothing else, so that doesn't work, because you need the cd command.

---

### Post by uRock on 2010-11-07
If you change the permissions of the home folders to 700, then none can see anyone else's data.

---

### Post by SuilAmhain on 2010-11-07
Changing the umask settings will set the default permissions for any and all new files & directories created by a user.

Type umask in a terminal to see what your value is. By default it is set to 022. Which means that directories get created with permissions of 755 & files with permissions of 644. 

To change the default behavior:

```
sudo vi /etc/profile
```

find umask and change it's value from 022 to 077
After this change is made once a user logs in all files they create will have have permissions of 600 and any directories will have 700.

As the server administer to retroactively change all permissions on home directories and their sub directories to 700 issue the following command:

```
sudo chmod -R 700 /home/          # Changes all subdirectories of home  
sudo chmod -R 700 /home/username  # Changes just a specific users dirs

```
I'm not sure what effect these permissions will have on Drupal.

If the umask setting does not take effect for a user check their .profile or .bashrc to see is it being set again at login from one of those files.

This page explains umask better than I did...
[http://ubuntuforums.org/showthread.php?t=905566](http://ubuntuforums.org/showthread.php?t=905566)

Thanks,
SuilAmhain

---

### Post by FuturePilot on 2010-11-07
> **SuilAmhain said:**
> 

```
sudo chmod -R 700 /home/          # Changes all subdirectories of home  
sudo chmod -R 700 /home/username  # Changes just a specific users dirs

```


The -R is not necessary and will probably mess things up if you're serving files with Apache through your home directory.

---

### Post by SuilAmhain on 2010-11-07
> **FuturePilot said:**
> The -R is not necessary and will probably mess things up if you're serving files with Apache through your home directory.

Suitably scorned :P

---

### Post by ilppi on 2010-11-07
Thanks alot! I'll have to try those out tomorrow (sleepy time now)

---

### Post by SeijiSensei on 2010-11-08
> **SuilAmhain said:**
> I'm not sure what effect these permissions will have on Drupal.

It will likely break your ability to upload content, themes, etc., to Drupal using the web interface.  The Apache web server runs as user www-data and group www-data. Drupal thus has the same privileges.  You can ameliorate this problem by making certain directories writable by group www-data.  I haven't used Drupal in quite some time, so I can't help you with identifying the directories you need to change.  The easiest method to figure out what you need to do is to apply the most restrictive permissions (700) then try to install a theme.  Drupal will complain it can't write the file to the correct location. You should also see errors in /var/log/apache2/error.log.

---

