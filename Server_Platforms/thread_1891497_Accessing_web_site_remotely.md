---
title: "Accessing web site remotely"
date: 2011-12-05
forum: Server Platforms
---

### Post by habuchas on 2011-12-05
I have installed Ubuntu 11.04 server. I have install drupal6 in var/www/drupal6 dir and have no problem accessing it from a browser using the url. However I have also installed drupal6 in /home/username/public_html/drupal6 dir but can not access it from a browser using url/~username/drupal6. I get a '500 Internal Server Error'. I am at a loss in finding the config file or script to modify to allow access.  At 77 years old I have little else to do but play with computers but this is aging me faster than I would like!
Any assistance would be greatly appreciated.

---

### Post by arrrghhh on 2011-12-05
You can either a) symlink that /home/username folder to /var/www, or b) I believe it's a 'vhost' in Apache.  I'm kinda a n00b myself when it comes to Apache, but I'm pretty sure you can't have two webroot's... a vhost is the way around it, if you have multiple sites.

---

### Post by volkswagner on 2011-12-05
It is likely a permission issue.

Check the current permissions of the folder.

```
ls -alt /~username/public_html/drupal6
```

You may need to add the www-data group.  You may also need to modify a couple key files if the group does  not have read permissions.

You may just want to set the owner to www-data recursively.

```
sudo chown -R www-data /home/username/public_html/drupal6
```

Also I assume this is a typo. You mention installing to  /home/username/public_html/drupal6  but dropped the "public_html" portion from the url string.

---

