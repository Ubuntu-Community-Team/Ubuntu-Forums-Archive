---
title: "Mysql-server 4.0, repositories"
date: 2006-09-20
forum: Server Platforms
---

### Post by Isoss on 2006-09-20
Hi, I need to install mysql-server 4.0 but it's not in the repositories. any one knows what is the repos for it?

Thanks

---

### Post by paul.maddox on 2006-09-20
Hi, 

It's in the universe repositories, do you have them enabled in your /etc/apt/sources.list?


paul.maddox@paul-laptop:~$ apt-cache search mysql-server-4.1
mysql-server-4.1 - mysql database server binaries


EDIT: Sorry, just noticed you wanted 4.0 and I suggested 4.1, my mistake!

---

### Post by Isoss on 2006-09-20
no problem ... I know there are 4.1 and 5.0 .. what I need is 4.0 .. I guess this was in breezy! is it possible to add repositories of breezy with dapper? if not, isn't there just a repos for mysql 4.0?

Thanks

---

### Post by gfd on 2006-09-21
> **Isoss said:**
> no problem ... I know there are 4.1 and 5.0 .. what I need is 4.0 .. I guess this was in breezy! is it possible to add repositories of breezy with dapper? if not, isn't there just a repos for mysql 4.0?

Thanks

I'm looking for the exact same thing.
I need to install MySQL 4.0.27 and I can't find it in the repositories.

Is there anyway we can find this version for ubuntu??

---

