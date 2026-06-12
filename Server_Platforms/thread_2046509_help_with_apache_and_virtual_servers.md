---
title: "help with apache and virtual servers"
date: 2012-08-23
forum: Server Platforms
---

### Post by fgdl on 2012-08-23
o i am just about to write everything i wrote in my notebook [IMG]http://i.imgur.com/oRFEl.png[/IMG]



i have installed Apache2 on 2 virtual webservers, when i look for the directory in the *terminal* it doesnt find it.

Any commands i type in such as:



httpd -s = Command not found

no files or directories are being found.





When "run apache2ctl config" i get an error says :87:ulimit: error setting limit ( operation not permitted)
apache2 could not reliably determine the servers fully qualified domain name, using 127.0.1.1 for servername
Syntax OK



i install the apache2 on the webserver not on my pc, Some videos have shown that the directory is in "C:" 

but mine isnt there ??

---

### Post by matt_symes on 2012-08-23
Thread moved to "Server Platforms".

Title changed to help readabilty.

---

### Post by CharlesA on 2012-08-23
What OS are these web servers running?

If they are running Debian or Ubuntu, apache is located in /etc/apache2/

The default site is located in /var/www/

You would stop/start/restart the apache service by running this:

```
sudo service apache2 stop|start|restart|reload
```

---

