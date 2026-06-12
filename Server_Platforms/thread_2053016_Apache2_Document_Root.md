---
title: "Apache2 Document Root"
date: 2012-09-04
forum: Server Platforms
---

### Post by mrwebmaster on 2012-09-04
Hi, 

some months ago, I changed the apache2 Document Root from /var/www to /home/myname/folder .

Now, I want it back to /var/www , but I don't remember how I changed it. 

I've tried adding > DocumentRoot /var/www in /etc/apache2/apache2.conf and changing DocumentRoot to /var/www in /etc/apache2/sites-available/default , without success. 

/etc/apache2/httpd.conf is a blank file and there is no /etc/apache2/sites-enabled/default

I also searched for the string > /home/myname/folder in every file under /etc/apache2/ using grep, and found no occurrences. 

Does anyone know where else can I search for the Document Root directive? I'm using Apache/2.2.22 (Ubuntu) on ubuntu 12.04.1

Thanks!

---

### Post by Bachstelze on 2012-09-04
What do you mean by "without success"? Have you restarted Apache?

---

### Post by wojox on 2012-09-04
> **mrwebmaster said:**
> 
I've tried adding  in /etc/apache2/apache2.conf and changing DocumentRoot to /var/www in /etc/apache2/sites-available/default , without success. 


Should be:
```
sudo nano /etc/apache2/sites-enabled/000-default
```

---

### Post by Bachstelze on 2012-09-04
> **wojox said:**
> Should be:
```
sudo nano /etc/apache2/sites-enabled/000-default
```

which is exactly the same thing because the latter is a symlink to the former.

---

### Post by mrwebmaster on 2012-09-04
Thanks for your replies. Yes, I've restarted apache and navigated to [http://localhost](http://localhost) and to [http://127.0.0.1](http://127.0.0.1) and the document root is still /home/myname/folder  (I've also restarted the computer and tried again).

Wojox, there is no /etc/apache2/sites-enabled/000-default . But I copied 

/etc/apache2/sites-available/default 

to 

/etc/apache2/sites-enabled/000-default

and now it's working fine. 

Curiosly, when I delete /etc/apache2/sites-enabled/000-default , Document Root is again /home/myname/folder . So I think this setting must be somewhere else. Anyway, it's working for me now. Thanks for your help!

---

### Post by Bachstelze on 2012-09-04
/etc/apache2/sites-enabled/000-default as I said is supposed to be a symlink to /etc/apache2/sites-available/default. If it does not exist, copying the file is a bad idea (you introduce a potential discrepancy), and you should create it instead. Remove your file and do

```
sudo a2ensite default
```

---

### Post by wojox on 2012-09-04
> **Bachstelze said:**
> which is exactly the same thing because the latter is a symlink to the former.

that's right, a2ensite. :p

---

### Post by mrwebmaster on 2012-09-04
Thanks, Done

---

