---
title: "changing port number"
date: 2010-08-04
forum: Server Platforms
---

### Post by mentes on 2010-08-04
Hello everyone I would like to change port number for a specific folder name on linux server like domain.com/folder_name:yyyy so people can access that folder with pre defined port number. is there a way that I can do that?
thanks for your interest

---

### Post by arrrghhh on 2010-08-04
Hrm... I'm going to take a stab in the dark and assume you're using apache (the more information the better next time ;))

Assuming you are, I believe you can do this with [vhosts](http://httpd.apache.org/docs/1.3/vhosts/).

I'm not exactly sure if you can tailor those to what you want, vhosts are usually used for different domains...

---

### Post by mentes on 2010-08-04
thank you very much for your reply. I was wondering is there a way that I can override apache configuration with .htaccess and make specifed folder to accept traffic only pre defined port number on .htaccess file

---

