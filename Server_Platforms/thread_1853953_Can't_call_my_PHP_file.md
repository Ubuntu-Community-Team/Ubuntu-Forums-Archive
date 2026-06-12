---
title: "Can't call my PHP file"
date: 2011-10-03
forum: Server Platforms
---

### Post by Old-un on 2011-10-03
I am running Ubuntu 11.04 and i've installed "XAMPP" and everything appears to be fine. I then made a php file called: phpinfo.php and after setting the permissions i moved the file to where XAMPP is located at: /opt/lampp. I then opened a browser and typed:
[http://localhost/opt/lampp/phpinfo.php](http://localhost/opt/lampp/phpinfo.php) but no luck?

I also saved the phpinfo.php file in the htdocs directory /opt/lampp/htdocs and tried to call it from there but still with out any luck?

Could someone tell me where i am going wrong please

---

### Post by [S|G] on 2011-10-03
Hi there!

First, its unlikely that you need to type in the "/opt/lampp" directory in your browser address bar. You just need to save the file in apache's www root directory (you can check that on /etc/apache2/sites-enabled/default) and then access it on "http://localhost/phpinfo.php".

On Ubuntu the default www root is /var/www (no htdocs), but I'm not familiar as to how you installed your server.

---

### Post by Old-un on 2011-10-04
Hello [S|G]

I downloaded and installed XAMPP as per instructions given at the site: [http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)

I do know that XAMPP is located at /opt/lampp But i can't find /var/www or Document root

Thanks for the reply

---

