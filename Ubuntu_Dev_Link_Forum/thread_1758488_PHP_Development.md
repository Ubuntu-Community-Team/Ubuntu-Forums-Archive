---
title: "PHP Development"
date: 2011-05-14
forum: Ubuntu Dev Link Forum
---

### Post by KiloKai on 2011-05-14
Let me start this by saying I am relatively new to Ubuntu and Linux in general. So I installed Apache 2, mysql, and php5 installed. I know Apache is working as the index.html in the var/www folder comes up when i go to localhost in my web browser. I know php5 is working. I made a info.php, called the phpinfo() function, and it worked fine. 

But, when I moved the folder from one of my sites into the www folder and navigate into that folder (localhost/mysite/index.php): nothing. White screen. No errors. Now, oddly enough, I thought Linux my do things differently with folders and localhosts, so I made a test folder inside the www folder and copied the index.html into the folder. It worked fine.

So, any ideas? Yes, the site does work on my windows setup.

---

### Post by flintman on 2011-05-15
by default php doesn't display errors.  You will get a white page with nothing on it.  

Edit

/etc/php5/apache2/php.ini

You will find the section on errors.  Change it to display errors and you should be good.

Hope this helps

---

