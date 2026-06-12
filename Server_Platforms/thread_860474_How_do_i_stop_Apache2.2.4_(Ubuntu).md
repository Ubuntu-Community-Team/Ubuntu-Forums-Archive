---
title: "How do i stop Apache/2.2.4 (Ubuntu)"
date: 2008-07-15
forum: Server Platforms
---

### Post by masoud23 on 2008-07-15
Hi

The Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6 Server at localhost Port 80 is running at my computer by default. I want to run Xampp. how do i stop Apache/2.2.4 (Ubuntu), also the command line in terminal.

---

### Post by cdenley on 2008-07-15
> **masoud23 said:**
> Hi

The Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6 Server at localhost Port 80 is running at my computer by default. I want to run Xampp. how do i stop Apache/2.2.4 (Ubuntu), also the command line in terminal.

To stop apache
```

sudo /etc/init.d/apache2 stop

```

To disable apache from starting automatically
```

sudo update-rc.d -f apache2 remove

```

To remove apache
```

sudo apt-get remove apache2 apache2.2-common

```

---

### Post by davidshq on 2008-07-15
reload or restart will restart the instance if you decide to reload the service at some juncture.
david.

---

### Post by cdenley on 2008-07-16
> **davidshq said:**
> reload or restart will restart the instance if you decide to reload the service at some juncture.
david.

restart = stop then start
reload  = re-read vhost configuration and re-open log files
start   = start apache from a stopped state

---

