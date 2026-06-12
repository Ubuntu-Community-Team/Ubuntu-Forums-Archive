---
title: "Server down -Cannot load /usr/lib/apache2/modules/libphp5.so into server"
date: 2010-11-30
forum: Server Platforms
---

### Post by mybayworkz on 2010-11-30
Hello all,
I am not too good with Linux, but I am trying to learn. Kindly bear with me.
My apache and wordpress were running fine till this morning. I ran updates via webmin,though I wasn't sure what those updates were for.

 Then when I tried to access mysite.com, index.php downloads instead of opening.

 I tried some troubleshooting and followed a form where it was advised to enable mod php5, so I did a2enmod php5 and tried to restart apache.
Since I get this error  Cannot load /usr/lib/apache2/modules/libphp5.so into server.

Please help me as I don't want to loose all the previous configuration I have.
Thanks for any possible help or guidance

---

### Post by mybayworkz on 2010-11-30
apt-get install libapache2-mod-php5 helped

---

