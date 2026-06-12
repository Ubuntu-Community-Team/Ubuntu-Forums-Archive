---
title: "php scripts downloading, not running"
date: 2008-07-30
forum: Server Platforms
---

### Post by woodsonoversoul on 2008-07-30
Hi all, I've googled this situation but haven't found any satisfactory information. I've got a nearly fresh install of Ubuntu 8.04 server edition, and have been working with some Javascript on it. Now I want to start working with PHP, but firefox wants to open the scripts as documents (download them or open them with Geany) instead of running them. I feel there must be a simple solution to this problem. What is it?

---

### Post by hyper_ch on 2008-07-30
Assuming you have installed apache2 and php5

```

sudo a2enmod php5

```

---

### Post by howlingmadhowie on 2008-07-30
it sounds like apache doesn't know what to do with php files. have you installed the following two packages?

libapache2-mod-php5
php5

---

### Post by jcr1 on 2008-07-30
Hi, I have the same problem.

I installed apache2 php5 mysql-server php5-mysql

libapache2-mod-php5 is installed.

```

sudo a2enmod php5
This module is already enabled!

```

When I browse to a test.php file, it tried to download it instead of displaying it!?

I have done this before, and it just worked...so not sure whats different this time.

---

### Post by udaykiranchapala on 2008-07-30
Hello Everyone! even I get the same problem.:KS
I have php5, libapache2-mod-php5

---

### Post by jcr1 on 2008-07-30
ok I found adding the contents of php5.conf to the end of apache2.conf did the trick

---

