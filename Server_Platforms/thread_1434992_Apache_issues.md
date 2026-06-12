---
title: "Apache issues"
date: 2010-03-21
forum: Server Platforms
---

### Post by Cavs23 on 2010-03-21
At first I installed xampp and it didn't work. So I scrapped it. Then I installed apache2 and php5 via synaptic. I could view html files just fine, but php files wouldn't work. Because I didn't start my server. I ran

```

sudo apache2 -k start // and I got the following output
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
httpd not running, trying to start
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs

```

I then saw somewhere I had to purge it and uninstall everything. So I did that and then I didn't have the apache2 folder. After completely removing apache2 and php5, I was able to get my folder back. But now I am missing config files. Luckily I backed up the apache2.conf. But I am missing the ports.conf and all other .conf files. My httpd.conf file is blank too.

Where might I find replacement files? Or any terminal commands that will help?

---

### Post by jimv2000 on 2010-03-21
Uninstall PHP and Apache.  Then run "sudo tasksel" and select LAMP server.  That will install Apache, PHP, and MySQL such that they will work together without any configuring.

EDIT - lol, I jumped the gun.  This doesn't really answer your question.  Sorry.

---

### Post by Cavs23 on 2010-03-21
I already did that.

---

