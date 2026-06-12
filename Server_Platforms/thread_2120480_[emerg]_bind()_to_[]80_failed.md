---
title: "[emerg] bind() to [::]:80 failed"
date: 2013-02-26
forum: Server Platforms
---

### Post by el canadiano on 2013-02-26
I think this might likely have been answered before, but I just made a fresh install of Ubuntu and attempted to install nginx. When I attempt to run sudo service nginx default, I get this.

```
username@ilose-ubuntu:/etc/nginx$ sudo service nginx start
 * Starting nginx nginx                                                         nginx: [emerg] bind() to [::]:80 failed (98: Address already in use)
nginx: [emerg] bind() to [::]:80 failed (98: Address already in use)
nginx: [emerg] bind() to [::]:80 failed (98: Address already in use)
nginx: [emerg] bind() to [::]:80 failed (98: Address already in use)
nginx: [emerg] bind() to [::]:80 failed (98: Address already in use)
nginx: [emerg] still could not bind()

```

Was wondering if you guys might know why it's doing it and how I can get nginx (more specifically, LEMP) up and running on my local machine.

---

### Post by Pimentel on 2013-02-27
If this is a fresh install, you probably have Apache installed by default.

```
sudo netstat -nltup | grep :80
```

Please post the output of the command above, it will let you know which service is listening to this port. Feel free to kill or uninstall it if it's not necessary, or bind Nginx to a different port.

---

### Post by el canadiano on 2013-02-27
> **Pimentel said:**
> If this is a fresh install, you probably have Apache installed by default.

```
sudo netstat -nltup | grep :80
```

Please post the output of the command above, it will let you know which service is listening to this port. Feel free to kill or uninstall it if it's not necessary, or bind Nginx to a different port.

```
username@ilose-ubuntu:~$ sudo netstat -nltup | grep :80
username@ilose-ubuntu:~$ 
```

There is no output. I was pretty sure I uninstalled apache2 if it was there. When I try to start apache or apache2, it's an "unrecognized service."

```
username@ilose-ubuntu:~$ sudo service apache2 start
apache2: unrecognized service
username@ilose-ubuntu:~$ sudo service apache start
apache: unrecognized service
username@ilose-ubuntu:~$ 

```

---

### Post by Pimentel on 2013-02-27
Any chance you have an IPv6 address associated to this setup? Try setting nginx to listen to the loopback interface only. In the vhost config file (presumably "/etc/nginx/sites-available/default"), replace the parameter inside the server block "listen 80;" or "listen [::]:80;" (whichever is uncommented) with "listen 127.0.0.1:80;".

If this works and you still want to make it listen to external addresses as well, change it to "0.0.0.0:80".

Otherwise, please post this file here.

---

### Post by el canadiano on 2013-02-27
I'll take a look into that when I get home tonight. I don't believe I have any ipv6 setups, and I'm only using nginx as a local test server.

---

### Post by el canadiano on 2013-02-28
So at the very top, I saw this.

```

	listen 80;
	listen [::]:80 default_server;

```

It was commenting the second line and replacing it with "listen 127.0.0.1:80". I can also view localhost without issue. Cheers!

---

