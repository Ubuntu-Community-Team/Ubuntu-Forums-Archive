---
title: "Cannot Properly Connect phpmyadmin to the Server"
date: 2016-12-26
forum: Server Platforms
---

### Post by cook150 on 2016-12-26
While setting up my web server, I went to install phpmyadmin. However, I remember that when I was configuring the application, I don't believe I configured it with apache2. The problem is that ***.***.***.***/phpmyadmin/ doesn't connect. (Asterisks are IP Address numbers.) Could someone tell me what's going wrong and how I can fix it?

---

### Post by darkod on 2016-12-26
We need more info than just this...

First of all, is the server public on the internet (like a hosting provider) or at your home/office behind an ISP router? Does it have public or private IP?

Does the apache default page open when you try to access the IP in browser?

---

### Post by cook150 on 2016-12-26
The server is meant to be public, but currently, it is only accessible by computers connected to my home's internet network.

I'm not exactly sure about the IP, but I believe it is private...

And the Apache2 "It works!" page does show up when accessing the IP Address in browser.

---

### Post by darkod on 2016-12-26
When trying phpmyadmin you are using ssl right? Try https://<server_ip>/phpmyadmin

Also pls post the content of /etc/apache2/conf-available

---

### Post by cook150 on 2016-12-26
The URL didn't work, and the file that you asked for content exists, but has nothing in it.

---

### Post by darkod on 2016-12-26
That's not a file, it's a folder. And it has to exist if apache is installed correctly. You might need to use sudo to open it, standard users might not have permissions...

---

### Post by cook150 on 2016-12-26
The content of the folder is:

javascript-common.conf

---

### Post by darkod on 2016-12-27
I haven't installed phpmyadmin too much, but if during installation it asked and you did not select to configure it automatically with apache, it might be faster to purge phpmyadmin and reinstall it. You are using apt-get to install it right?

Usually in /etc/apache2/conf-available you would see something like phpmyadmin.conf of in /var/www/html/ folder you should have something about phpmyadmin.

I would simply try reinstalling it:
```
sudo apt-get purge phpmyadmin
sudo apt-get install phpmyadmin
```

And make sure you select the correct options during installation, it saves you loads of time compared to manual configuration later... If you are unsure how to do it, google it, there must be million tutorials how to install phpmyadmin on ubuntu server.

---

### Post by cook150 on 2016-12-27
Alright, it's fixed!

Thank you so much for the help!

---

