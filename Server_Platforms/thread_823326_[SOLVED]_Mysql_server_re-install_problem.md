---
title: "[SOLVED] Mysql server re-install problem"
date: 2008-06-09
forum: Server Platforms
---

### Post by acheun on 2008-06-09
Hi, I just did a careless nasty thing myself.  I accidental delete /etc/mysql and /var/lib/mysql.  I tried to re-install mysql-server package, but they are not re-created.  I think when I do the re-installation, MYSQL does not install from scratch, because it does not ask me about the root password like the first time I did.

How can I do a clean re-installation for Mysql?

---

### Post by bluefrog on 2008-06-09
sudo apt-get install --reinstall $(dpkg -l mysql* | grep ii | awk '{print$2}' | tr "\n" " ")

if not enough then you can always
sudo dpkg-reconfigure mysql-server

---

### Post by gtdaqua on 2008-06-09
Remove: (includes repair broken installations)

```

sudo apt-get autoremove
sudo apt-get autoclean

sudo apt-get update
sudo apt-get install -f

sudo apt-get remove mysql-server --purge
sudo apt-get remove mysql-client --purge

```

Install again:
```

sudo apt-get install mysql-server mysql-client

```

---

### Post by acheun on 2008-06-09
Thank you for your help.  I can now have the re-install it and it is now working.

But I still have a problem.

When I re-install, it did not prompt me for the root password and it defaults to no password.  It looks like apply to the user 'debian-sys-main' as well.  I would like to set a password to it, but it seems now debian.cnf need the password to be encrypted password.  I don't know how to put an encrypted password in.  I have tried the "sudo dpkg-reconfigure mysql-server", but nothing happen. Any one know how to do so?

thanks in advance

---

### Post by gtdaqua on 2008-06-10
see here: [MySQL Change Root Password]("http://www.cyberciti.biz/faq/mysql-change-root-password/")

On a fresh mysql install, root password is not set. However, the package installation should have asked. Follow the URL and you will get useful info to change the root password.

---

### Post by acheun on 2008-06-10
I actually mean to set a password to debian-sys-maint in the debian.cnf file.

Actually, I just search the answer from google. Although it looks like the password in debian.cnf is encryted, it's not.  So I put the password in plain text and it works.

Thank everybody's help.

---

