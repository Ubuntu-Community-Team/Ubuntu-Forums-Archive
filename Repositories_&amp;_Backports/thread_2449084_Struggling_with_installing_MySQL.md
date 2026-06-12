---
title: "Struggling with installing MySQL"
date: 2020-08-19
forum: Repositories &amp; Backports
---

### Post by mekanik3 on 2020-08-19
Hello,

I just got Ubuntu 18.04.4 on my new computer and trying to install MySQL on it.

However, once installed it can't start because of missing file "mysqld.sock".
It really looks strange to me as it comes just right after completing the installation and nothing seemed to go wrong with it.[IMG]https://zupimages.net/viewer.php?id=20/34/6t83.png[/IMG]
[IMG]https://zupimages.net/viewer.php?id=20/34/6t83.png[/IMG]

Please check the attached screenshots to see what it gives.

Hoping to find a way to fix this problem, I would be very glad to find any good clues.

Thank you,

---

### Post by TheFu on 2020-08-20
Did you start the mysqld service?  Use **systemctl** to do that.

Please don't post images of text.  Copy/paste the text so people with sight issues can help and everyone can copy/paste the important parts to highlight solutions.

If you don't absolutely have to use mysql, perhaps mariadb would be a nicer choice?  It is from the creators of mysql, before Oracle bought it. The team left Oracle and created an API compatible replacement. All the commands and clients are the same - just no Oracle.

---

### Post by SeijiSensei on 2020-08-20
mysqld.sock is not really a file, but a "[socket]("https://opensource.com/article/19/4/interprocess-communication-linux-networking")," a method for applications to communicate with other applications. I suspect the server wasn't running. As TheFu suggests, try
```
sudo systemctl restart mysql.service
```
and see what happens.

---

### Post by mekanik3 on 2020-08-20
Hello,

Thank you for your responses.

I simply tried to reinstall mysql, this time with "apt install" instead of "apt-get install", and surprisely it worked fine.
So, the case is now solved.

Thank you again.

---

### Post by TheFu on 2020-08-20
> **mekanik3 said:**
> I simply tried to reinstall mysql, this time with "apt install" instead of "apt-get install", and surprisely it worked fine.
So, the case is now solved.

There's little chance that solved it.  'apt' is just a wrapper around most 'apt-get' commands.

---

