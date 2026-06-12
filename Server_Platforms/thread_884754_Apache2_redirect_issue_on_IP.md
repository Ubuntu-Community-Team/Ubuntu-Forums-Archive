---
title: "Apache2 redirect issue on IP"
date: 2008-08-09
forum: Server Platforms
---

### Post by gizmobay on 2008-08-09
I have two linux computers on my local network running two distros both running apache. On the Fedora one when I enter [http://192.168.0.3](http://192.168.0.3) from a remote PC on the network I end up with the Apache welcome page. On the Ubuntu one, when I enter [http://192.168.0.5](http://192.168.0.5) the address bar changes to [http://localhost](http://localhost) and then I get an error saying can't connect to the server. If I'm on the ubuntu PC naturally this works okay. My question is how do I turn off the IP forwarding to the localhost domain?

---

### Post by windependence on 2008-08-09
I don't think your forwarding IPs, I think you have a firewall issue with the Ubuntu box. Not sure how to tell you to fix it though, I don't do IPtables. ;)

-Tim

---

### Post by gizmobay on 2008-08-09
I must have something else going on. I didn't have the default index.html file since I have an index.php. I added the index.html file to the folder and I was able to see It Works! at [http://192.168.0.5](http://192.168.0.5) but when I try the index.php file I get an unable to connect issue. Do I have php permission issue?

---

### Post by gizmobay on 2008-08-09
Blah, I'm stumped

[http://192.168.0.3/index.html](http://192.168.0.3/index.html) works from all machines

[http://192.168.0.3/index.php](http://192.168.0.3/index.php) redirects to [http://localhost/index.php](http://localhost/index.php) and only works when using firefox on the ubuntu PC

---

### Post by windependence on 2008-08-09
No, you need to load the php module into Apache.

You may also need to actually enable it, by doing sudo a2enmod php5 followed by sudo /etc/init.d/apache2 restart. If sudo a2enmod php5 returns "$ This module does not exist!", you should purge (not just remove) the libapache2-mod-php5 package and reinstall it.

Be sure to clear your browser's cache before testing your site again. 

-Tim

---

### Post by gizmobay on 2008-08-09
Thanks for the help. The a2emod said that php5 is already enabled. I then retested and php doesn't work from a remote host on the LAN.

---

### Post by gizmobay on 2008-08-11
Sorry, it was my index.php script that was redirecting to localhost :(:(

---

