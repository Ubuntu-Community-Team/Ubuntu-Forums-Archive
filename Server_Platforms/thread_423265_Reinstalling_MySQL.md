---
title: "Reinstalling MySQL"
date: 2007-04-25
forum: Server Platforms
---

### Post by Torahteen on 2007-04-25
Hey everyone... sorry for the Qs, but I'm just trying my best to get myself a fully working LAMP server. My next problem is quite simple. I tried installing PHPMyAdmin, and realized I've locked myself out of MySQL (I completly forgot the details of my installation, password, db name, etc.), so I want to just reinstall MySQL. I did "sudo apt-get remove mysql-server mysql-client" and also removed the mysql library (forget the name ATM). Then I reinstalled the packages, and tried to set up MySQL again, but it's like I never did anything... I can't make a root user/password because I don't have a password to use MySQL... what files to I need to remove from my hard drive before trying to install MySQL again?

---

### Post by primski on 2007-04-26
Is this the default mysql installation? Usually there is no password for root account, so first try that:

```

$ mysql -u root

```

then, if you want to completely wipe out mysql installation, you need to add --purge to your 'apt-get remove' line

```

$ apt-get remove --purge mysql

```

Then try reinstalling.

---

