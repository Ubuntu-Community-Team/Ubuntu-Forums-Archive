---
title: "MariaDB, what do you think ?"
date: 2012-02-16
forum: Server Platforms
---

### Post by linoseros on 2012-02-16
Everything is in the title. Did you try MariaDB ? what do you think of it ?

---

### Post by LepeKaname on 2012-02-16
I have been using MariaDB (in production servers as well) for the last year or so... so far so good. It has some extra features that I like but I don't use them all.

If you use PHP, be aware that you can't update PHP (from the repository) as mariadb's "mysql-common" version is slighly older than the one of MySQL (required by php-mysql module). But soon or later its updated and then you can update PHP (probably not to the last version). For me, it hasn't be a big issue. I just have to be sure to put php-mysql in "hold".

If you don't need the MariaDB extra features, then I would say there won't be so much difference of using MySQL.

Cheers.

---

### Post by CivilizationII on 2012-02-17
MariaDB is fine. The main question is trusting or not Oracle regarding MySQL, technical point of view currently being "the same".

---

### Post by linoseros on 2012-02-21
> **LepeKaname said:**
> I have been using MariaDB (in production servers as well) for the last year or so... so far so good. It has some extra features that I like but I don't use them all.

If you use PHP, be aware that you can't update PHP (from the repository) as mariadb's "mysql-common" version is slighly older than the one of MySQL (required by php-mysql module). But soon or later its updated and then you can update PHP (probably not to the last version). For me, it hasn't be a big issue. I just have to be sure to put php-mysql in "hold".

If you don't need the MariaDB extra features, then I would say there won't be so much difference of using MySQL.

Cheers.

Very interesting what are the extra features ? and are you using it for big databases ?

---

### Post by LepeKaname on 2012-02-22
This is the Official list of features: [http://kb.askmonty.org/en/mariadb-versus-mysql-features]("http://kb.askmonty.org/en/mariadb-versus-mysql-features")

In my case, I moved to MariaDB because of these reasons: The "virtual-columns" support, row lock, increased performance and restore/replay from logs.

I'm not sure what do you mean by "BIG", but one of our largest databases that is running in MariaDB is around 5GB compressed (largest table size is arond 1 million records).... so far, so good.

The best part is that MariaDB is practically an exact replacement of MySQL, so you don't need to modify your codes or your queries from MySQL -> MariaDB. You can perform some benchmarks with your actual data and see if you gain performance. If for some reason you don't feel like staying with MariaDB, then you can easily go back (unless you are using some MariaDB-only features).

---

### Post by linoseros on 2012-03-07
Thank you I'm looking at it.

---

### Post by Indian Summer on 2012-11-16
I'm considering replacing MySQL with MariaDB for my PHP-based forums. I probably won't need the absolutely latest PHP version, so if it's a bit behind on that I guess it won't be a problem.

---

