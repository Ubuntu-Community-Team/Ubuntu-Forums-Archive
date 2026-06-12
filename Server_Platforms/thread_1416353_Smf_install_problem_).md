---
title: "Smf install problem :)"
date: 2010-02-26
forum: Server Platforms
---

### Post by waloshin on 2010-02-26
I have created a folder in my /var/www/ as /var/www/borneo and when I try to install a smf forum I get this error: 550 Failed to change directory.

I have installed vsftpd for the ftp.

---

### Post by waloshin on 2010-02-26
I am getting a file download when running trying to install now it identifies it self as:

application/x-httpd-php

I am 100% sure php5 is installed and integrated with apache2. So would installing fail2ban cause this?

---

### Post by cdenley on 2010-02-26
Are you sure apache's php module is enabled, and apache has been restarted since then?
```

sudo a2enmod php5
sudo /etc/init.d/apache2 restart

```

---

### Post by waloshin on 2010-02-26
> **cdenley said:**
> Are you sure apache's php module is enabled, and apache has been restarted since then?
```

sudo a2enmod php5
sudo /etc/init.d/apache2 restart

```

It said that Module php5 already enabled. 

Everything is working.

---

### Post by cdenley on 2010-02-26
> **waloshin said:**
> It said that Module php5 already enabled.

And after restarting apache, the problem persists?

---

### Post by waloshin on 2010-02-26
> **cdenley said:**
> And after restarting apache, the problem persists?

Nope I everything works I have installed my Smf forum now.

---

