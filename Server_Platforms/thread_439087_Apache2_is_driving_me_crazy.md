---
title: "Apache2 is driving me crazy"
date: 2007-05-10
forum: Server Platforms
---

### Post by TorchlightJay on 2007-05-10
So ya, my server runs feisty in xterm. I am using webmin to help edit the server. It seems to be running both apache2 and 1.3. I am trying to run two domain names (let's call them test.com & exam.com) and I set the ports and IPs to any. Apache2 won't start but Apache 1.3 will. Now either website shows the folder listing rather than the website. 

All of my web settings are for Apache2, it simply won't restart and be read by the server. Since it won't restart (seems like a port conflict), it goes to apache 1.3 which has nothing other than the /var/www folder lsting. Any ideas of how to fix this? Thanks.

---

### Post by az on 2007-05-10
Webmin is broken, do not use it.

Remove apache1.3

Remove the index directive in /etc/apache2/sites-available/default or whatever site you have configured

---

### Post by TorchlightJay on 2007-05-10
Any particular version of webmin or webmin in and of itself? Also, how should I configure it then. I Know I can use Vim but I am not an expert at the manual configurations. Know of any good tutorials? Thanks

---

### Post by hyperair on 2007-05-10
Have you made sure that your ports for Apache2 and Apache 1.3 are different? If one starts and the other it could be because the second cannot grab control of the specified port number.

---

### Post by TorchlightJay on 2007-05-10
I got it. Removing Apache 1.3 and upgrading webmin to 1.340 fixed it.

---

