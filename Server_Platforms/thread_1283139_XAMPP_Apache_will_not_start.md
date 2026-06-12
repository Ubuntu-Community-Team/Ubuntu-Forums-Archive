---
title: "XAMPP Apache will not start"
date: 2009-10-05
forum: Server Platforms
---

### Post by gabrielshier on 2009-10-05
Hey, 
Just installed XAMPP on my ubuntu. It ran perfectly well. After a reset (no changed made to any directory or configuration of the XAMPP) everything runs perfectly fine beside the Apache sever. On the GUI it gives me no error, just leaves it deactivated. Trying to run it from a terminal gives the error:
```
ayelet@ayelet-desktop:~$ cd /opt/lampp
ayelet@ayelet-desktop:/opt/lampp$ sudo ./lampp start
Starting XAMPP for Linux 1.5.3a...
XAMPP: Starting Apache with SSL (and PHP5)...
XAMPP: XAMPP-MySQL is already running.
XAMPP: XAMPP-ProFTPD is already running.
XAMPP for Linux started.
ayelet@ayelet-desktop:/opt/lampp$ 
```

Further more, when i tell it to run just the apache server it gives:
```
ayelet@ayelet-desktop:/opt/lampp$ sudo /opt/lampp/lampp startapache
XAMPP: Starting Apache with SSL (and PHP5)...
```

Thanks,
Gab

---

### Post by t3r0 on 2009-10-05
Hi,

Check if you have anything in Apache error logs.

- Tero

---

### Post by gabrielshier on 2009-10-05
Tried that. . . Apache error logs were empty. Tried removing in reinstalling xampp. No success either. 
Does anyone have any idea weather how am i to install a simple php, apache and a simple mail server on ubuntu?

---

### Post by cdenley on 2009-10-05
> **gabrielshier said:**
> Does anyone have any idea weather how am i to install a simple php, apache and a simple mail server on ubuntu?

```

sudo tasksel install lamp-server
sudo tasksel install mail-server

```

---

### Post by gabrielshier on 2009-10-05
Hey cdenley,
Thanks for the response. Tried that and it acctually installed those packages successfully. Only two things; first - i don't know how to manage these servers, secound - when i try to access http for localhost it redirects automatically to [http://localhost/xampp/](http://localhost/xampp/) and gives an error of page not found. If i could only get the xampp up and running everything would be okay. Have no idea why it acts that way. On the other hand, all rest of ports seems open and okay as if Apache server (XAMPP) still functining. Only can't get a normal HTTP reponse...
Thanks,
Gab

---

### Post by cdenley on 2009-10-05
The ubuntu package wouldn't redirect you to any xampp directory. Either you still have xampp running, or xampp changed the vhost configuration in /etc/apache2/sites-enabled. I can't help you with xampp as I've never used it before. You probably won't find much support for it here. I always suggest people stick with the repos whenever possible.

---

### Post by gabrielshier on 2009-10-07
Hey,
The folder /etc/apache2/sites-enabled is empty. XAMPP is not installed or running. Completely removed it. 
Any other thoughts?

---

### Post by cdenley on 2009-10-07
```

cat /etc/apache2/sites-available/default
sudo a2ensite default
sudo /etc/init.d/apache2 restart
sudo netstat -tlnp
grep DocumentRoot /etc/apache2/*.conf /etc/apache2/conf.d/* /etc/apache2/sites-enabled/*
sudo ls -1 /var/www

```

---

### Post by gabrielshier on 2009-10-11
Thanks cdenley,
It works perfectly well now! :)
Could you please explain to me what does these commands do?
> sudo a2ensite default   assume that these restores default settings.
> sudo /etc/init.d/apache2 restart restarts the server
> sudo netstat -tlnp does a basic netstat to check connections for what?
and > sudo ls -1 /var/www lists the files in the default folder currently set to /vat/www . 
Any way, thanks alot! It works greate and my site is back up again (well, at least the "coming soon" part :))

---

### Post by cdenley on 2009-10-11
```

sudo a2ensite default 

```
Enables the default site (virtual host) configuration located at /etc/apache2/sites-available/default if it isn't already enabled. The command enables it by creating the link /etc/apache2/sites-enabled/000-default.

```

sudo /etc/init.d/apache2 restart

```
Restarts apache, which is needed for global configuration changes.

```

sudo netstat -tlnp

```
Displays all processes listening for a TCP connection. This would identify what web server, if anything, is actually listening on TCP port 80.

```

sudo ls -1 /var/www 

```
Lists the contents of /var/www, formatted in a single column.

---

### Post by gabrielshier on 2009-10-14
Thanks!
Works like charm :)

---

