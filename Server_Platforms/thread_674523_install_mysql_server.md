---
title: "install mysql server?"
date: 2008-01-21
forum: Server Platforms
---

### Post by mpgarate on 2008-01-21
Im trying to install Vanilla forum software on a remote server, and im stuck in the mysql part of the setup. I do not know how to remotely install mysql, and configure it. can anyone help?

---

### Post by Vinno on 2008-01-21
Is the server running on ubuntu?

If so,
```
sudo apt-get mysql-server php5-mysql
```

Also get phpmyadmin, front end for mysql database control via webpage.

```
sudo apt-get install phpmyadmin
```

Make sure your also using the latest version of vanilia forum, there seems to a SQL injection vulnerability around before.

---

### Post by gtdaqua on 2008-01-22
if it is a REMOTE server, then make sure you can ssh over your network to it.

on the remote server console:

```

sudo apt-get install ssh openssh-server

```

then from your terminal
```

ssh <-l  server_username@server ip address>

```

then run the mysql installation.
```

sudo apt-get mysql-server php5-mysql
sudo apt-get install phpmyadmin

```

---

### Post by mpgarate on 2008-01-22
thanks! the host had a tool that I used, and it worked well. thanks for the help though!

---

