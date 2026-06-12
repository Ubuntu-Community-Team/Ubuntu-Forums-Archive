---
title: "mysql fails to start on boot - unable to manually start service"
date: 2009-05-15
forum: Server Platforms
---

### Post by marty pain on 2009-05-15
Having a bit of a bad day and any help here would be appreciated.

The server has been up and running LAMP for three months. I did a base install of Ubuntu 8.04 and installed all the separate LAMP components (and a few other things) using apt-get. All has been running fine.

Today (whilst I was under the desk the server is on) a multi-plug blew and all the servers went off (and I smacked my head on the desk!) Now I have a massive lump on my head and a server that wouldn't start (operating system missing message)!

I booted the server using the install CD and could get a shell working on the main partition, so tried to re-install the GRUB. This failed. I rebooted the server and this time it did boot up correctly (luckily!). The only problem I have left now is that MySQL will not start.

when running /etc/init.d/mysql start i just get:

* Starting MySQL database server mysqld [fail]

same as on boot.

Typing mysql results in:
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

but I guess this is because it isn't running.

I have tried running mysqld_safe and it sends back:
nohup: ignoring input and redirecting stderr to stdout
Starting mysqld daemon with databases from /var/lib/mysql
mysqld_safe[6027]: started
STOPPING server from pid file /var/run/mysqld/mysqld.pid
mysqld_safe[6037]: ended

so no errors there, but no help for me either.

Does anyone have any ideas? Should i just save off /var/lib/mysql along with the config files and reinstall MySQL? Or is there a way to find out what is wrong and fix it?

Thanks in advance!
Marty

Forgot to mention that I’m running (well, should be) MySQL 5

---

### Post by drave on 2009-05-15
i'd do a fsck on all your partions

possibly from a recovery cd

---

### Post by marty pain on 2009-05-15
OK, I ran fsck with the -p option for /dev/sda1 and got the following:
/dev/sda1: recovering journal
/dev/sda1: clean, 45919/15081472 files, 1022490/60293945 blocks (check in 4 mounts)

So all looks ok??

I rebooted the machine (just for good measure) and mysql is still not working

I have backup all my databases from /etc/lib/mysql and have copied those on to my laptop. I can now see those via the MySQL console on my laptop and execute SQL statements successfully. I have copied off the my.conf file too, so i think i will just remove MySQL and re-install it.

Will post once it's all completed

---

### Post by drave on 2009-05-15
is there anything in /var/log/mysql.err ?

---

### Post by marty pain on 2009-05-15
OK!! All sorted! When the server booted back up after the power down, it was assigned a new IP from the DHCP server. In my.cnf MySQL server was binded to the previous IP. I changed the bind-address to the current IP and restarted. All working!!

All just in time for the weekend! At least the day ended well! Thanks for your help! Time for beers!

---

