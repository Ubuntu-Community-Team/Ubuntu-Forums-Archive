---
title: "installing phpmyadmin"
date: 2010-06-09
forum: Server Platforms
---

### Post by markjrouse on 2010-06-09
I followed all the instructions on installing phpmyadmin and I still can't access the login page.  I've installed phpmyadmin on my ubuntu server box (no GUI), but the instructions say go to [http://localhost/phpmyadmin](http://localhost/phpmyadmin).

Question: how can I when on the server I have no GUI environment or browser. Instead I have to use a separate PC on the same subnet.  But type in [http://localhost](http://localhost) does not work, nor does [http://myservername/phpmyadmin](http://myservername/phpmyadmin).

Am I missing something?

---

### Post by Ryan Dwyer on 2010-06-09
Localhost is a loopback to the same machine, so that won't work. Using the server's hostname won't work if you don't have it set up to resolve to the server's IP address. You can either browse using server's IP address, or add it in /etc/hosts on the client machine.

---

### Post by markjrouse on 2010-06-10
Thanks for that.
 
I have used my server's ip address as well: [http://xxx.xxx.x.xxx/phpmyadmin](http://xxx.xxx.x.xxx/phpmyadmin), but this still does not work. My client machine will either be my MacBook Pro or my Windows XP Netwbook. I guess them my server needs to have the appropriate config. As you suggest: how do I set up my server to resolve to the server's IP address?
 
Is there a particular Apache or PHPMyAdmin config file that needs to specify my server's ip address?  What I would like to be able to do is on a wb browser from either my Mac or Netbook, just simply type in [http://xxx.xxx.x.xxx/phpmyadmin](http://xxx.xxx.x.xxx/phpmyadmin), where the ip address is for my server, and up comes the phpmyadmin interface.
 
Thanks for any help.

---

### Post by Ryan Dwyer on 2010-06-10
I would get it working by IP address before I try to get it working by hostname. Are you in the same local network? If so, you need to use its private IP address (commonly 192.168.x.x or 10.x.x.x). If not, you need to use the public IP address and also forward port 80.

---

### Post by markjrouse on 2010-06-14
Hi, yes, I'm in the same network and subnet.

I type in [http://192.168.x.x/phpmyadmin](http://192.168.x.x/phpmyadmin) but it does not work.  I can ping my ubuntu server, I just can't access the phpmyadmin website.  Should I set ufw to allow port 80?

---

### Post by wojox on 2010-06-14
Did you add this to apache2.conf and restart apache? 

[Troubleshooting Phpmyadmin & mysql-admin]("https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20Phpmyadmin%20&%20mysql-admin")

---

### Post by markjrouse on 2010-06-14
Yeap, works now.  did a sudo ufw allow 80, and now it works fantastically.

That is [http://192.168.x.x:80/phpmyadmin](http://192.168.x.x:80/phpmyadmin)

---

