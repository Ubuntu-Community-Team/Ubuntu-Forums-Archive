---
title: "Many MySQL, Apache und named processes eat all the RAM"
date: 2013-06-30
forum: Server Platforms
---

### Post by rreimche on 2013-06-30
Hi all.

I run a VPS on Ubuntu Server 10.04. The server has something about 750 Mb RAM, which is, soon after the server has started, almostly all consumed by numerous mysqld, named and apache2 processes:

[https://dl.dropboxusercontent.com/u/54107411/Bildschirmfoto%202013-06-25%20um%2013.54.38.png](https://dl.dropboxusercontent.com/u/54107411/Bildschirmfoto%202013-06-25%20um%2013.54.38.png)

There are 2-4 websites with very little traffic running on this server.

Can I somehow optimise this or I simply need more RAM? I think there is something wrong, that a server without any serious workload consumes so much memory.

---

### Post by sandyd on 2013-06-30
> **rreimche said:**
> Hi all.

I run a VPS on Ubuntu Server 10.04. The server has something about 750 Mb RAM, which is, soon after the server has started, almostly all consumed by numerous mysqld, named and apache2 processes:

[https://dl.dropboxusercontent.com/u/54107411/Bildschirmfoto%202013-06-25%20um%2013.54.38.png](https://dl.dropboxusercontent.com/u/54107411/Bildschirmfoto%202013-06-25%20um%2013.54.38.png)

There are 2-4 websites with very little traffic running on this server.

Can I somehow optimise this or I simply need more RAM? I think there is something wrong, that a server without any serious workload consumes so much memory.

I see the top memory users are apache/mysql

First, Apache is kind of a memory hog, if you want it to fit on a small VPS, use something like nginx + php5-fpm which is much much much much lighter, and will have a greater chance on fitting on 750 Mb RAM.

Second, MySQL is kind of heavy too, if you have little traffic, you may want to limit the amount of mysql processes that are spawned.
See [http://superuser.com/questions/345592/how-can-i-limit-the-number-of-child-processes-that-mysql-spawns](http://superuser.com/questions/345592/how-can-i-limit-the-number-of-child-processes-that-mysql-spawns) and [http://stackoverflow.com/questions/621516/how-can-i-set-the-max-number-of-mysql-processes-or-threads](http://stackoverflow.com/questions/621516/how-can-i-set-the-max-number-of-mysql-processes-or-threads)

You can set those options by adding them to  /etc/mysql/my.cnf , and restarting mysql

Also, if your not using bind9 (dns server), it is sometimes installed on VPS templates by default
If you dont need it, remove it by running
```
sudo apt-get remove bind9
```

---

### Post by rreimche on 2013-06-30
Thank you, sandyd.

Could you tell me, please, if I don't use any CGI stuff, could I stay without [COLOR=#000000]php5-fpm?[/COLOR]

---

### Post by SeijiSensei on 2013-06-30
You can reduce Apache's footprint to some degree by limiting the number "children" it spawns. In /etc/apache2/apache2.conf take a look at:

```

IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>

```

Try starting with 3 for the first two items and 5 for MaxSpareServers.

That said, I have apache, mysql, postgresql, bind9, and a couple of other items running on a 512 MB CentOS 6 virtual server and have memory left to spare.  

```

Mem:    506644k total,   437972k used,    68672k free,    67608k buffers
Swap:   262140k total,    73744k used,   188396k free,    62072k cached

```

Do you have a swap partition?  That can help some, though as you see here only about 70M is in use.  If you don't have and cannot configure a partition for swap, [create a swapfile on the drive]("http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/") and use that instead.

However I'll also mention that I did not follow my own advice about the number of children and still do not have a memory problem.  This machine currently has 20 apache child processes running, each of them using somewhere between 10MB and 20MB of unique memory.  (About 30 MB is shared by all the children.)

My mysqld runs with just a single process consuming about 125MB. PostgreSQL starts five processes which collectively add up to about the same amount of memory as mysqld.

It's possible that one of the web applications you are running is misconfigured somehow and spawning unending processes.  I've had that experience with PG and large databases.  If the database is not well-indexed, people running a SELECT query can grow tired of waiting for the results and try to cancel the request by hitting stop in the browser or reloading the page.  The background SQL process will not die in this case, but just hang idle in the background.  Reloading is even worse since an entirely new process will be spawned as well.

---

### Post by sandyd on 2013-07-01
> **rreimche said:**
> Thank you, sandyd.

Could you tell me, please, if I don't use any CGI stuff, could I stay without [COLOR=#000000]php5-fpm?[/COLOR]

If you don't need PHP5, you don't need php5-fpm.

---

### Post by rreimche on 2013-07-01
Thanks. Very useful.

---

