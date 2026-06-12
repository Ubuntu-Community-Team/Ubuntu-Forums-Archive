---
title: "Permissions on /var/www and synching with Unison | Change ownership of own file"
date: 2018-09-29
forum: Server Platforms
---

### Post by gijs007 on 2018-09-29
I'm setting up Unison to sync my /var/www directory between two webservers.

I can run Unison as root, but this requires the root user to be accessible over SSH. Which is undesirable because of the security implications.  
As such I'm running Unison as non root user, however I have a permission issues which need to be fixed.

I'm currently unable to copy content which is created by the user www-data from system A to B or vice versa.
I've set the following permissions:

```
sudo usermod -a -G www-data unison[FONT=Calibri]
sudo chown -R unison:www-data /var/www/&#8217;[/FONT]
sudo chmod -R 775 /var/www
```

With these permissions I can copy all the content created by the Unison user from system A to system B.
However content created by the user www-data cannot be copied as I get the following error: 

[HTML]ETAFailed [html/myText2.txt]: Error in setting file ownership:
Operation not permitted [chown(/var/www/html/.unison.myText2.txt.42c63edfb042108894a5b1164d7601bf.unison.tmp)][/HTML]

Note:
I'm able to workaround this problem if the content was created by www-data on server A, by disabling the owner synchronization in Unison. 
However Unison is still unable to sync files created on server B by the www-data user.


Update:
Turns out Unison was trying to set the group permissions on system A, when syncing content from system B. (and not the user permissions, as I mistakenly thought)
Unison wasn't able to set the group permissions because the permissions assignment only become active after a reboot..

The workaround where I disable the user synchronization in Unison works fine.

---

### Post by TheFu on 2018-09-29
If this is solved, help the community by marking it SOLVED - Thread Tools button near the top.

---

