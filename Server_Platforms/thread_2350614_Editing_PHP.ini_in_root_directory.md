---
title: "Editing PHP.ini in root directory"
date: 2017-01-25
forum: Server Platforms
---

### Post by Mike_Hughes on 2017-01-25
I need help getting access to the php.ini file inside my root directory. I can see the root directory listed even when login as root. But I can't cd /root to it so I can't get to php.ini. Any help to be able to edit would be appreciated.
also the only way I can do anything to files on the server is to be logged in as root. Sudo returns an error message. Any help appreciated. I am running 16.04 Server.

---

### Post by QIII on 2017-01-25
First, you shouldn't log in as root, so we need to figure out what the issue is with sudo.

Telling us you get an error is not very helpful.  Do you SSH into your server?  If so, please try a command prepended by sudo and post the results back here.

If you are not SSHed into the server, an image from your cell phone with the results will do.

---

### Post by Mike_Hughes on 2017-01-26
I can't ssh into the server. I know you shouldn't login as root. When I try to sudo. I get something about not being a sudoer

---

### Post by wildmanne39 on 2017-01-26
*Thread moved to **{forum for better support}**.*

---

### Post by darkod on 2017-01-26
But you need to know at least one username with admin rights. Who is administering this server? And if you can't ssh into it, how do you manage it, by GUI?

If you know one admin account it is easy to add any user to sudo group:
```
sudo usermod -aG sudo <username>
```

After that the username you specified will have sudo rights.

As for ssh, take a look at the setup, and solve that too, because that's the main way how you administer linux servers.

---

### Post by Mike_Hughes on 2017-01-26
When I went in as root said macmike was already in sudoer group.
when I try to do any sudo, I get
sudo: error in /etc/sudo.conf, line 0 while loading plugin 'sudoer_policy'
sudo: /user/lib/sudo/sudoers.so must be only be writable by owner
sudo: fatal error, unable to load plugins

---

### Post by Mike_Hughes on 2017-01-26
When I tried to service ssh start without sudo 
i got -
==== Authenticating For org.freedesktop.systemd1.manage-units ===
Authention is required to start 'ssh service'
Authenticating as: macmike,,  (macmike)
Password: (when I typed in password in)
===== Authentication Complete ====

---

### Post by darkod on 2017-01-26
Well, that message gives you a hint, that sudoers.so file needs to be writeable only by owner. Were you changing some permissions or ownership of that file or folder?
Write down the current permissions and then try setting 600 on that file. That makes it writeable only by owner.
After that try sudo again.

---

### Post by SeijiSensei on 2017-01-26
Concerning the original question, there are two copies of php.ini in an Ubuntu installation.  One is stored in /etc/php[57]/apache2 and is used with, surprise, the Apache web server.  The other is in /etc/php[57]/cli and governs the behavior of the php command-line executable, /usr/bin/php.

---

### Post by Mike_Hughes on 2017-01-26
I got the sudo working. I raised the max-file-upload size. But that didn't change the size in Wordpress.

---

### Post by Mike_Hughes on 2017-01-26
That issue is fixed. Chmod 655 and changing ownership to root solved that one.

---

### Post by SeijiSensei on 2017-01-27
What directory or directories did you change to root ownership?  The WordPress directory and its children like wp-content, etc.?  I would discourage that practice from a security perspective.  Those directories should be owned by the www-data user, or by another non-root user and the www-data group.  You also need to be careful about which directories and files have write privileges.  WP is commonly attacked with the intent of putting dangerous content in those directories or defacing the website itself.  

I use two simple scripts to manage this task.  This one should be run when the site needs updating, like when a new release of WordPress is announced:

```

#!/bin/sh
chmod g+w wp-admin wp-includes wp-content -R
chmod g+w *

```

I run this from the top of the /wordpress/ directory.  After the update is completed I run 

```

#!/bin/sh
chmod g-w wp-admin wp-includes wp-content -R
chmod g-w *

```

My installation is owned by a non-root user and the www-data group which generally has only read privileges except during updates. No other users have any privileges ("a-rwx" in chmod).   If the www-data user owns the WP installation, then you would need to use "u+w" and "u-w" in the chmod commands.

---

### Post by QIII on 2017-01-27
I am going to add my agreement with SeijiSensei:

I do not use WP, but my daily logs sent from my web server report hundreds of attacks attempting to exploit WP.  Don't give the bad guys the keys.  It's hard enough to keep them out as it is.

---

