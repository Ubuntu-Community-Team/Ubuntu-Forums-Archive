---
title: "opening port 80"
date: 2007-01-15
forum: Server Platforms
---

### Post by speedingbullet on 2007-01-15
The OS of the computer im trying this on is Xubuntu Edgy Eft.

root@MrX:/home/richard# apache2
apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(98): make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs
root@MrX:/home/richard# 

now how would I open up port 80 on a linksys WRT54GS router? And would my ip address be the address computers would connect to?

---

### Post by kingmonkey on 2007-01-15
[http://portforward.com/](http://portforward.com/)

I think your using this the wrong way. The webserver runs automatically as a deamon. No need to issue the command apache2.

```
 sudo /etc/init.d/apache2 start 
```

This should be used to start it.

---

### Post by kingmonkey on 2007-01-15
Your IP address is would be the external IP address of your modem.

You need to forwad port 80 to the internal IP address of your computer.

---

