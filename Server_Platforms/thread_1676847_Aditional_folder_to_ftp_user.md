---
title: "Aditional folder to ftp user"
date: 2011-01-27
forum: Server Platforms
---

### Post by da mono on 2011-01-27
Hello friends, I'm having trouble figuring out how to add another folder to my jailed ftp users, basically what i want is to let them acces my /var/www/ folder for the development purpose but still have them restricted to their home folders

software installed on my office server is

ubuntu 10.10 x86
LAMP
Webmin
ProFtpd Server

any other info you might need just ask :)
:guitar:

---

### Post by da mono on 2011-01-27
well I tried making a simlink but taht did'nt work well jejej just realized is text chain any info guys ?

---

### Post by Bob.Davis@wibble.net.nz on 2011-01-28
I am using Pure-FTPD but shoudl be similar on proftp 

what I do is to have my ftp server run as the www-data user, then you can create the users with the appropriate /var/www/websitename home directory

```
pure-pw useradd [username] -u www-data -d /var/www/[sitename]
```

I can give you a walk through on setting up pure-ftpd if you want me to ..

Bob

---

### Post by da mono on 2011-01-28
well actually waht I have on minde is share one [www.site](www.site) so we can work on one project at a time :)  but still  have them jailed in their home directory

---

### Post by da mono on 2011-01-29
bumpy  ?

---

