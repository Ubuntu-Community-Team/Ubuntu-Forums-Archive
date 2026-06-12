---
title: "FTP and HTTP account"
date: 2006-01-24
forum: Server Platforms
---

### Post by franke on 2006-01-24
I'm gonna have an ftp and http-server, and I want my users to be able to have their own homepage. 

I looked at pureftpd with virtual users and a separate root for the users. Is there any good way to connect the users homepage to that account?

For instance,  user Joe should be able to log into the ftp , where he sees two folders ..  his http-folder for online stuff, his private ftp-space, and also the public ftp on my server.. 

Not sure how to combine these things.

---

### Post by robinl on 2006-01-25
htaccess files? Or just configure Apache to deny access to private folders.
eg.
/www/joe/ = online
/www/joe/private = private 

and configure your apache to something like this
<Directory /www/*/private>
     Order Deny,Allow
     Deny from all
</Directory>
I'm unsure about the "/www/*/private" part but if it works, it will deny anyone trying to go to someone's private folder and only the ftp can access them.

---

### Post by jimwillsher on 2006-01-25
Or create symlinks in joe's home folder, e.g.

ln -s /var/www/joe /home/joe/webspace

etc etc.

Jim

---

