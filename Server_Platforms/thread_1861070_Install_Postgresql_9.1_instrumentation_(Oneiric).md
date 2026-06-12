---
title: "Install Postgresql 9.1 instrumentation (Oneiric)"
date: 2011-10-15
forum: Server Platforms
---

### Post by tededet on 2011-10-15
Hi

Anyone knows how to install Postgresql 9.1 instrumentation?

Various sources found on Google specify these steps for Postgresql 9.0:
```
sudo apt-get install postgresql-contrib
sudo -u postgres psql < /usr/share/postgresql/9.0/contrib/adminpack.sql
```


Except that 'adminpack.sql' file does not exist on Ubuntu Oneiric for Postgresql 9.1 :(. 
Any help would be appreciated.

---

### Post by SeijiSensei on 2011-10-15
It looks like it's just a set of SQL commands.  Did you try running the 9.0 version?

---

### Post by tededet on 2011-10-16
No, I tried only 9.1 which seems to be default for Oneiric.

---

### Post by tededet on 2011-10-16
I think I found the answer to my question:

```

sudo -u postgres psql
CREATE EXTENSION "adminpack";

```

Also from psql shell you can:
1) see a list of installed extensions
```

select * from pg_extension;

```

2) see a list of all available extensions
```

select * from pg_available_extensions;

```

---

### Post by sierrasdetandil on 2011-12-06
Thank you for posting the answer! I was having the exact same problem.

---

### Post by Purkinje on 2012-06-13
When I installed 9.1, I found adminpack--1.0.sql in */usr/share/postgresql/9.1/extension*. This may be what you're looking for.

---

### Post by heway10 on 2012-07-06
> **tededet said:**
> I think I found the answer to my question:

```

sudo -u postgres psql
CREATE EXTENSION "adminpack";

```

Also from psql shell you can:
1) see a list of installed extensions
```

select * from pg_extension;

```

2) see a list of all available extensions
```

select * from pg_available_extensions;

```

I'm pretty new to Ubuntu and brand-new to Postgres. So I didn't know what I'm doing wrong when I tried 
```
sudo -u postgres psql CREATE EXTENSION "adminpack";
```

As you probably know, it's really two commands:
```
sudo -u postgres psql
```
to get the postgres prompt, then
```
CREATE EXTENSION "adminpack";
```

Right answer, just too advanced for my simple mind!;)

---

