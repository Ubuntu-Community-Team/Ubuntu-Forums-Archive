---
title: "Permission denied to Apache-CGI"
date: 2014-04-09
forum: Server Platforms
---

### Post by Rdorigo on 2014-04-09
I have a CGI script on /usr/lib/cgi-bin/ that works just fine.

But when the script tries to write a file to /var/www/my_custom_dir i  get the error "Permission denied". Just as a test i tried to set the folder chmod  from 755 to 0777 and the owner from root to www-data but it still does not  work, i'm stuck.

Any ideas?

I'm on 12.04 server 64bit. Thanks.

---

### Post by Kirboosy on 2014-04-10
Welcome to the forums! :D

You might want to try changing the owner to apache or whatever "web user" you have setup on your box.

```
sudo chown -R apache:apache /var/www/
```
Command break down
```
sudo (temporarily invoke root privileges) chown (change owner) -R (recursive) <user>:<group> <path/to/files/folder>
```
What user is your script running as?

Hope that helps!
~Caboose

---

### Post by SeijiSensei on 2014-04-10
> **Rdorigo said:**
> But when the script tries to write a file to /var/www/my_custom_dir i  get the error "Permission denied". Just as a test i tried to set the folder chmod  from 755 to 0777 and the owner from root to www-data but it still does not  work, i'm stuck.

Is it possible that the script is being denied from using something like an application while it is running?  I'd add some debugging statements to see where the script dies.

You can also test to see if the script runs as the www-data user from the prompt, but it's a bit tricky.  First you'll have to edit /etc/passwd and change the last entry for www-data from /usr/sbin/nologin to /bin/bash.  Now try this:
```
sudo su
su www-data
/path/to/your/script
```
Remember to disable logins for the www-data user when you're done.

---

