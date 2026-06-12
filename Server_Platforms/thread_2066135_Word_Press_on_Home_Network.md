---
title: "Word Press on Home Network?"
date: 2012-10-03
forum: Server Platforms
---

### Post by echolink on 2012-10-03
So here is what I have going on at my home guys. Currently I have Ubuntu Server 12.04 installed on my home computer. This server is hooked up to the Internet, but I don't have a FQDM. This is not a problem because this server is being used on the local network only at my home. Currently I have LAMP installed it is working fine. I can access the default test page using IP 10.0.0.3 from any device on my network. I also have Samba installed, and working properly. Also I have the Ubuntu Desktop installed. Webmin, phpMyAdmin, and Wordpress, and proftpd. They all are installed and the entire system works properly across my network. I opted for the Ubuntu Desktop install to be able to use phpMyadmin, Webmin, and Wordpress. The problem that I am currently having is the only way I can access wordpress is using [http://localhost/wordpress](http://localhost/wordpress). I'm not sure what I did wrong, is there a specific way I can access my wordpress via other devices on my network using an IP address. I attempted to change the url to IP via wp_options using phpmyadmin. However this broke the link, and had to change it back to [http://localhost/wordpress](http://localhost/wordpress) to access it directly on the server. So basically how do I change wordpress to access it across the network. The whole reason behind this project is to have a central server in our home for ftp, samba, website, and bog on wordpress that the family can use to store data, and share data. Again everything else works across the network, just cant access wordpress. Any advice would be greatly appreciated :)

---

### Post by volkswagner on 2012-10-03
This is likely a wordpress setting.  What do you have entered for "site address url" and "wordpress url" in your general settings (wp-admin/options-general.php)?

My guess is you have localhost listed there.  Try changing it to your machines ip address (10.0.0.3).

Also what do LAN users get when they type [http://10.0.0.3](http://10.0.0.3) in a browser?  Do they get the default ("It Works") Apache2 page?

---

### Post by echolink on 2012-10-03
> **volkswagner said:**
> This is likely a wordpress setting.  What do you have entered for "site address url" and "wordpress url" in your general settings (wp-admin/options-general.php)?

My guess is you have localhost listed there.  Try changing it to your machines ip address (10.0.0.3).

Also what do LAN users get when they type [http://10.0.0.3](http://10.0.0.3) in a browser?  Do they get the default ("It Works") Apache2 page?

Correct 10.0.0.3 shows "It Works Page"

---

### Post by hasan.akgoz on 2012-10-04
Where do you have entered for "http://localhost/wordpress" ? Server or PC on local network. if you can see apache default page, apache is working.

---

### Post by Gregorybekkers on 2012-10-04
If you see the apache default page make sure permissions are set to the right user. 
and that is loads from the right directory.

---

