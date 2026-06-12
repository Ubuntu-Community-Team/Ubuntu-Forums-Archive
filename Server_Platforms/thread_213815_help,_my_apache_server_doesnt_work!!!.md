---
title: "help, my apache server doesnt work!!!"
date: 2006-07-11
forum: Server Platforms
---

### Post by %hMa@?b&lt;C on 2006-07-11
I recently aquired an old G3 Powermac. I decieded to run it as a server and I cannot connect to it from  a web browser.  I can ssh into the machine, and when i try running "apache2" i get this error.
```
root@maclintosh:/var/www# apache2
apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(98)Address already in use: make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs

```

---

### Post by DrSturgeon on 2006-07-11
Use the apachectl utility (or, for apache 2, apache2ctl) to start and stop apache; not sure what just running apache2 does.

```
apache2ctl start
```

will start apache2

As for your error, it looks like something else is already using port 80.  Are you sure apache isn't already running?  Try opening a browser and entering 127.0.0.1 and see what you get.

---

### Post by gruepig on 2006-07-12
What's in your apache config files (likely under /etc/apache2/)?  Specifically, have you set the ServerName directive?

Also, check that apache isn't already running. 'ps aux | grep apache' or 'pgrep apache' should tell you if it's running.  (Similarly 'telnet localhost 80' or  'sudo lsof -i | grep www' will tell you if anything is listening for connections on port 80.)

---

### Post by nkassi on 2006-07-12
Check you /etc/hosts file. You need to add your machinename.domain at the end of the 127.0.1.1 line

Use the following command to restart apache:  
sudo /etc/init.d/apache2 restart

This will kill all old instances of the server that might still be running and start a new one

Nic

---

### Post by %hMa@?b&lt;C on 2006-07-12
ok, added this line to he bottom,

ServerName maclintosh

now i need to try seeing if it works on port 80, because i mooved it to port 50 just to try it

---

