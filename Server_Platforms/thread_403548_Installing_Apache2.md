---
title: "Installing Apache2"
date: 2007-04-07
forum: Server Platforms
---

### Post by MCSD.NET on 2007-04-07
Hey dear , It is my first time that using Ubuntu Server.... I am not professional in Commands and etc.
I installed the Apache2 on my Server . I used this command for config tha:
/eta/apache2/apache2.conf
When I pressed enter message showed me that Perssmision denied.
I tried it by sudo command but nothing happend.
How can I do it?](*,)

---

### Post by bikeboy on 2007-04-07
If you're trying to edit the config file:```
sudo nano /etc/apache2/apache2.conf
```

If you're trying to start apache:```
sudo /etc/init.d/apache2 start
```

Note: some details of my post might be slightly wrong, I'm used to apache1.3 so I don't know if the config file and name is exactly right.

Hope that helps.

---

### Post by jaheds on 2007-04-07
You can also control apache using the "apache2ctl" command, like this:

To start:
```
sudo apache2ctl start
```

To restart config:
```
sudo apache2ctl restart
```

Good luck

---

### Post by MJN on 2007-04-08
Better to use the init script (which in turn calls apache2ctl) as it does other sanity checking besides.

Mathew

---

