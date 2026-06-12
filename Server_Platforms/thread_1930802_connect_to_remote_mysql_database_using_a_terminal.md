---
title: "connect to remote mysql database using a terminal"
date: 2012-02-24
forum: Server Platforms
---

### Post by 1cookie on 2012-02-24
hi

I want to login to a remote mysql database server from my laptop at home. I'm using:

```

andy@andy-R519-R719:~$ mysql -h dbipaddress -u user -p
Enter password: 

```I get to the enter password stage, enter the password, and it just hangs; eventually i have to ctrl Z to abort the command. Anyone?

---

### Post by rubylaser on 2012-02-24
This is the proper format. Have you granted privileges for your user to connect from the host you're trying to connect from?  Can you just connect via SSH and run your queries with that user?

---

### Post by roelforg on 2012-02-24
Try specifing the DB on the command line

---

### Post by 1cookie on 2012-02-24
> **rubylaser said:**
> This is the proper format. Have you granted privileges for your user to connect from the host you're trying to connect from?  


not sure about that. It's my works database.

> 
Can you just connect via SSH and run your queries with that user?
I try this approach with:

```

ssh user@mydatabase.co.uk -p 3306

```The terminal returns a flashing cursor, it doesn't prompt me for a password - just hangs?

---

### Post by 1cookie on 2012-02-24
> **roelforg said:**
> Try specifing the DB on the command line

hi

I tried:

```

andy@andy-R519-R719:~$ mysql -h dbipaddress -D dbname -u user -p Enter password:

```it still hangs....

---

### Post by roelforg on 2012-02-24
> **1cookie said:**
> hi

I tried:

```

andy@andy-R519-R719:~$ mysql -h dbipaddress -D dbname -u user -p Enter password:

```it still hangs....
I was thinking in the
```

mysql -h ip -u user -p dbname

```
area

---

### Post by 1cookie on 2012-02-24
> **roelforg said:**
> I was thinking in the
```

mysql -h ip -u user -p dbname

```area

Nope, it's not playin....:(

---

### Post by 1cookie on 2012-03-02
> **rubylaser said:**
> This is the proper format. Have you granted privileges for your user to connect from the host you're trying to connect from?  Can you just connect via SSH and run your queries with that user?

hi

Yes, the setup was a single login (via SSH) to a Unix server for security. From there, I can access web server[1,2,3].co.uk, and db servers with a simple ```
mysql -h db.server -u user -p dbname
```.

It's my inexperience with SSH that was the problem. Thanks for the help. :)

---

