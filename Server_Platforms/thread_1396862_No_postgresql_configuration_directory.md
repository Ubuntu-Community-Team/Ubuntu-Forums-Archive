---
title: "No postgresql configuration directory"
date: 2010-02-02
forum: Server Platforms
---

### Post by Sh4wn on 2010-02-02
Hi guys,

I'm trying to install postgresql 8.4 on ubuntu server 9.10, simply by running apt-get install postgresql. All fine and apt get succeeds, but there's a slight problem:

There is no configuration directory created with the postgresql config files. /etc/postgresql does not exists, only /etc/postgresql-common, but it doesn't contain the config files.

The only files I can find are the sample files in /usr/share/postgresql/8.4, but I don't think I should mess with because I believe it contains markers for automatic config file building.

I've tried the following:
dpkg-reconfigure postgresql
No result

When I try to start psql I get the following error:
```

postgres@ct143:/etc/postgresql-common$ psql
psql: could not connect to server: No such file or directory
	Is the server running locally and accepting
	connections on Unix domain socket "/var/run/postgresql/.s.PGSQL.5432"?

```

Which, according to the documentation, means it tries to connect to the server through TCP/IP, but the server probably doesn't accept TCP/IP connections. But I also can't find a postmaster/postgresql process running anywhere.

Anyone an idea?
Thanks in advance.

---

### Post by lykwydchykyn on 2010-02-02
What is the output of:
```

aptitude search postgresql|grep ^i

```

and 
```

sudo /etc/init.d/postgresql-8.4 restart

```

---

### Post by Sh4wn on 2010-02-02
Here it is:

```

root@ct143:/etc/postgresql-common$ aptitude search postgresql|grep ^i
i   postgresql-8.4                  - object-relational SQL database, version 8.
i A postgresql-client-8.4           - front-end programs for PostgreSQL 8.4     
i A postgresql-client-common        - manager for multiple PostgreSQL client ver
i A postgresql-common               - PostgreSQL database-cluster manager       
root@ct143:/etc/postgresql-common# /etc/init.d/postgresql-8.4 restart
root@ct143:/etc/postgresql-common# 

```

---

### Post by lykwydchykyn on 2010-02-02
Let's try a reinstall; something is definitely not right.
```

sudo aptitude purge postgresql postgresql-8.4 postgresql-common
sudo aptitude install postgresql

```

Post the output if that doesn't fix it.

---

### Post by slazyk on 2010-02-03
If you're getting some perl errors during install like this:
```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "pl_PL.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
```Try:
```
LC_ALL="C" sudo aptitude install postgresql
```

---

### Post by Sh4wn on 2010-02-09
> **lykwydchykyn said:**
> Let's try a reinstall; something is definitely not right.
```

sudo aptitude purge postgresql postgresql-8.4 postgresql-common
sudo aptitude install postgresql

```

Post the output if that doesn't fix it.

This did the trick (I didn't purged postgresql-common, only had reinstalled postgresql)

@Above, the first install did have those messages, later I build the locales which made them disappear.

---

