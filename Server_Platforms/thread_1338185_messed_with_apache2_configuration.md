---
title: "messed with apache2 configuration"
date: 2009-11-26
forum: Server Platforms
---

### Post by tapas_mishra on 2009-11-26
I have messed up with my apache2 configuration so I am having some problem the following is the error message I am getting while restarting apache2

apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs

Any hints what should I look in for.

---

### Post by Iowan on 2009-11-26
There are cleaner ways to do [this]("https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20Apache"), but it's one option.

---

### Post by tapas_mishra on 2009-11-26
I opened in vi editor and found file /etc/apache2/conf.d/fqdn as mentioned on the above link does not exist on my system so I had to create it and added the line ServerName localhost but still there was the error remains the same

---

