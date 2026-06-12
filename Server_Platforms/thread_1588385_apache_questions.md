---
title: "apache questions"
date: 2010-10-04
forum: Server Platforms
---

### Post by neoginn on 2010-10-04
I installed apache and when i go to my 127.0.1.1 ip i see the welcome page. 

I found the directory where the html is located (var/www/index.html but i cannot edit the file.

 what is going on here?  why cant i edit the HTML file?

---

### Post by Ryan Dwyer on 2010-10-05
You don't have permission. It makes sense if you think about it. If any user on your server could write to your web files then anyone with an account on your server could deface your website.

If you want to manage the files yourself then the best options is to change Apache's DocumentRoot to somewhere in your home directory. An alternate method would be to add yourself to the www-data group, then chmod everything in /var/www/ so group has write access.

---

