---
title: "Advice me!!"
date: 2010-04-08
forum: Server Platforms
---

### Post by Acceptance on 2010-04-08
Hi everyone! i'm new in Linux!
i installed Apache on Ubuntu and i can't start !!

Error code is below

[COLOR=Red]administrator@administrator-desktop:~$ /usr/local/apache2/bin/apachectl start
[/COLOR][COLOR=DarkOrange][COLOR=Red]httpd: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(13)Permission denied: make_sock: could not bind to address [::]:80
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs[/COLOR]
[/COLOR]  
how can i solve this problem !!
advice me ! thz.

---

### Post by lisati on 2010-04-08
Moved to "Server Platforms"

Have a look here: [https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20Apache](https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20Apache)

---

### Post by wojox on 2010-04-08
Usually when you install it it starts it for you. What does this produce

```
sudo /etc.init.d/apache2 restart
```

---

### Post by Acceptance on 2010-04-08
thank for your advice ! but i still have a problem!
i can't save that .

[B][ Error writing /etc/apache2/conf.d/fqdn: No such file or directory ]

sorry for my interruption
[/B]

---

### Post by cdenley on 2010-04-08
> **Acceptance said:**
> thank for your advice ! but i still have a problem!
i can't save that .

[B][ Error writing /etc/apache2/conf.d/fqdn: No such file or directory ]

sorry for my interruption
[/B]

Can't save what? What command are you trying to run when you receive that output? Are you trying to create that file to configure "ServerName" globally to avoid that harmless warning?
```

echo "ServerName localhost" | sudo tee /etc/apache2/conf.d/fqdn

```

---

### Post by Acceptance on 2010-04-19
Thz brothers!!
i got it!!

---

### Post by Iowan on 2010-04-20
[Another]("https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20Apache") version of the same advice...

[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")? :)

---

