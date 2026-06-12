---
title: "403 forbidden"
date: 2011-06-21
forum: Server Platforms
---

### Post by alex_grg on 2011-06-21
**Forbidden**

 You don't have permission to access /sitefolder/index.php on this server.
  Apache/2.2.17 (Ubuntu) Server at localhost Port 80

i'm getting this error while trying to run on localhost!! plz help,

em new to linux just taking test drive on ubuntu.

---

### Post by arrrghhh on 2011-06-21
Are you just typing ```
http://localhost
``` in the URL bar?  Is this an Ubuntu Server..?  In which case, I don't see how you're going to localhost on a browser in a server, unless you're using Lynx or something similar...

Edit - in the future, please don't [crosspost.](http://ubuntuforums.org/showthread.php?p=10964916)  I know you want an answer fast, but you were getting plenty of help in that other thread.

---

### Post by restorator on 2011-06-21
Have you given index.php the proper permissions? You should need execute permissions for it. Also do you have the server setup to interpret php files?

---

### Post by alex_grg on 2011-06-21
i typed [http://localhost/sitefolder/index.php](http://localhost/sitefolder/index.php) and yeah this is lamp server on ubuntu 11.04

---

### Post by alex_grg on 2011-06-21
regarding permissions i used nautilus then navigated to /var/www/ and there i right clicked my site folder, then properites->permissions and set owner (username), folder access (create and delete files), file access( -), group(root), folder access (none) and same to others as root, then i applied permissions to enclosed files and is still not working

i haven't created any virtual host for my site folder

---

### Post by crispy_420 on 2011-06-22
So everything is in /var/www right?

Try 'sudo chmod -R 0755 /var/www' and then restart apache with 'sudo service apache2 restart' I think. See if that helps at all.

---

### Post by arrrghhh on 2011-06-22
> **alex_grg said:**
> regarding permissions i used nautilus then navigated to /var/www/ and there i right clicked my site folder, then properites->permissions and set owner (username), folder access (create and delete files), file access( -), group(root), folder access (none) and same to others as root, then i applied permissions to enclosed files and is still not working

i haven't created any virtual host for my site folder

Nautilus?  Are you even using the server platform...?

---

### Post by alex_grg on 2011-06-22
yeah. that *_sudo chmod -R 0775 /var/www_* followed by _*sudo service apache2 restart*_ made it work, thanx a lot crispy_420 :) and by the way can you tell me what that first command actually do??

---

### Post by arrrghhh on 2011-06-22
> **alex_grg said:**
> yeah. that *_sudo chmod -R 0775 /var/www_* followed by _*sudo service apache2 restart*_ made it work, thanx a lot crispy_420 :) and by the way can you tell me what that first command actually do??

Changes permissions recursively (-R) to 0775.  If you want to know more about permissions, read [this page](http://www.zzee.com/solutions/linux-permissions.shtml#setuid).

---

### Post by alex_grg on 2011-06-22
thanx buddy.

---

### Post by crispy_420 on 2011-06-22
Thought I said 0755 but if that works for you good. Basically 7 is read/write/execute and 5 is read/execute. I think you can go with less rights but this works.

Want to mark as solved?

---

### Post by arrrghhh on 2011-06-22
> **crispy_420 said:**
> Thought I said 0755 but if that works you good. Basically 7 is read/write/execute and 5 is read/execute. I think you can go with less rights but this works.

Want to mark as solved?

You did say 0755, sorry about that I was just repeating what alex_grg said... looking at your post, 0755 was originally what you suggested (and is probably better than 775...)

It also appears to be marked [SOLVED] ;)

alex_grg - by no means required, but having correct permissions can cause issues or catastrophic failure.  In this case, it might mean someone will have write access when they should only have read/exec.  I would recommend redoing that command to reflect what was originally suggested.

---

