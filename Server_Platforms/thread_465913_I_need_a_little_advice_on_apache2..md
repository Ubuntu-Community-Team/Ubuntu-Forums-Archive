---
title: "I need a little advice on apache2."
date: 2007-06-06
forum: Server Platforms
---

### Post by colonel_panic414 on 2007-06-06
I just installed Apache2 and the packages necessary for PHP 5 from the standard Ubuntu repositories in Ubuntu Feisty. I am using it to host an eyeOS setup on my computer for my friends and I. I placed it in this directory: /var/www/eyeOS. So, when someone wants to use my copy of eyeOS, they type in mydomain.org/eyeOS. This works well. But, if they just type in mydomain.com, they can see the contents of my /var/www. 

I talked to a friend of mine who makes a regular business of hosting his own Apache2 server, and he said all I should do is write a .htaccess file within my /var/www folder with this inside it:
```
Order deny,allow
Deny from all
Allow from 127.0.0.1
``` 

Well, even after restarting the Apache process, it doesn't read this .htaccess, and anyone who wants can see my directories. What my friend suggested next was to write just a short index.html page into my /var/www. That doesn't show up or get read either, but anything in a subfolder of /var/www does, such as my eyeOS. 

If anyone could help me out, I'd definitely appreciate it. Thanks!

---

### Post by rich.bradshaw on 2007-06-06
I set everything up using this link [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP), and that seemed to work...

If you delete the .htaccess (or rename it so it isn't parsed), does index.html show up then? It should do....

Maybe that .htaccess isn't doing the right thing - try looking up more info on it.

---

### Post by colonel_panic414 on 2007-06-06
Ok, my index.html now shows up. I deleted my .htaccess last night, so apparently thats not why my index didn't show up. It turns out all I did was place some incorrect value in /etc/apache2/apache2.conf. 

But, when I replaced my .htaccess a few moments ago as described in my first post, it still shows my directory when I take out my index.

---

### Post by jscrilla on 2007-06-06
When I setup my apache2 server, I didn't allow anyone to see the /var/www folder by simply creating folders for each domain name, like /var/www/mydomain1.com/docs. So then in apache2 httpd.conf file, I created the root directory for each domain as /var/www/mydomain1.com/docs, so no one could ever look in my root domain folder from the web. 

I also changed the group settings on the docs folder to a special www group, while the root domain name folder was set to root. Not sure if that helps, but its how i set mine up.

---

### Post by colonel_panic414 on 2007-06-06
Ok, I like that Idea. Could you explain how you edited httpd.conf? I'm somewhat familiar with linux, but apache config files... Not so much haha. Anyway, I appreciate all the help from you guys. Thanks!

---

