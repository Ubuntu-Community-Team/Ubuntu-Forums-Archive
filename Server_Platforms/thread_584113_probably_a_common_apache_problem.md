---
title: "probably a common apache problem"
date: 2007-10-20
forum: Server Platforms
---

### Post by supersonicdarky on 2007-10-20
i installed apache2, php5 and mysql and when I try to start apache i get

```
kernel@laptop:/var/www$ sudo apache2
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(98)Address already in use: make_sock: could not bind to address [::]:80
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs

```

somehow it seems like a common error, but it's too long to search properly.

Running Gutsy Desktop.

---

### Post by Dr Small on 2007-10-20
Try:
```
sudo /etc/init.d/apache2 start
```

---

### Post by supersonicdarky on 2007-10-21
now
```
kernel@laptop:~$ sudo /etc/init.d/apache2 start
[sudo] password for kernel:
 * Starting web server apache2
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
httpd (pid 5227) already running


```

---

### Post by conjur3r on 2007-10-21
The install process most probably started apache up for you so you do not need to manually start it for your current session.

Check to see if apache is running and serving:
# apache2ctl status

Or tell apache to restart:
# sudo apache2ctl restart

By the way, that wasn't the proper way to start apache.  The proper way is either:
# sudo apache2ctl start
or
# sudo /etc/init.d/apache2 start

---

### Post by supersonicdarky on 2007-10-23
Thnx, will remember. But I have one very simple question left: Before I installed ubuntu server in a vm, and I had to go to some url to configure everything. What is the url? Or do I have to install something extra to enable that?

---

### Post by conjur3r on 2007-10-24
Sounds like you had something like webmin installed.  Pretty much an administrative tool which you can edit settings to various system and program stuff using your browser.  I tend to stay well away from it but others swear by it.  Personal preference in the end.

---

