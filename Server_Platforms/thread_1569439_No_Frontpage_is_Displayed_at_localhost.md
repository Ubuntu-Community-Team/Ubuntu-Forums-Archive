---
title: "No Frontpage is Displayed at localhost"
date: 2010-09-06
forum: Server Platforms
---

### Post by ismailkimyacioglu on 2010-09-06
Hi,

I don't know whether it was answered before.  At the same time, I don't know how to search for it.  I have a problem.

Instead of XAMPP or LAMP, I installed a local web server to my Ubuntu 10.04.  Apache and phpmyadmin works well.

I copied the files of my Joomla website to /var/www folder.  When I go to administrator panel, it works.  But when I type in the browser "http://localhost/[folder_name], a blank page appears and nothing else.

What would be the problem ? Please help me to solve it.

---

### Post by 0004tom on 2010-09-06
what happens when you try

[http://localhost/](http://localhost/)[folder_name]/index.php/html etc etc

---

### Post by ismailkimyacioglu on 2010-09-07
Hi 004Tom,

Thanks for the reply.  I am sorry when you replied, no mail sent to me and I have just seen your message.  Well, it was showing nothing.  But I have found the problem.  I had to clean the cache of my Joomla site and then it works fine.

Thanks your kind concern, again.

---

