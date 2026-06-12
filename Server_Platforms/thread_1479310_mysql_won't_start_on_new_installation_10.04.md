---
title: "mysql won't start on new installation 10.04"
date: 2010-05-10
forum: Server Platforms
---

### Post by senor_smile on 2010-05-10
I just installed a brand new ubuntu server 10.04 32-bit, choosing the LAMP option on install.  

Upon reboot I couldn't connect to mysql from another machine, so on this new server I changed the file at /var/mysql/my.cnf 

```
bind-address            = 192.168.5.21
```

That is the IP address of the server itself.  For whatever reason, when I run ```
/etc/init.d/mysql start
``` or a restart, it just hangs and never starts the daemon now.  Any ideas?

---

### Post by Bachstelze on 2010-05-10
Is MySQL server running currently? You can see that with

```
ps aux | grep mysql
```

If it is running, try [font=monospace]kill[/font]ing it and then starting it with the init script. If it's not, try to run it directly with

```
mysqld
```

(as root, so do a [font=monospace]sudo -i[/font] beforehand), and see if you get any helpful error message.

---

### Post by senor_smile on 2010-05-10
> **Bachstelze said:**
> Is MySQL server running currently? You can see that with

```
ps aux | grep mysql
```

If it is running, try [font=monospace]kill[/font]ing it and then starting it with the init script. If it's not, try to run it directly with

```
mysqld
```

(as root, so do a [font=monospace]sudo -i[/font] beforehand), and see if you get any helpful error message.

I have gotten a little further.  I rebooted the server for the umpteenth time, and this time went for a coffee break.  I came back and did a ```
ps -ef | grep mysql
```
Lo and behold, the service is running.  It seems like that for whatever reason it's taking it a minute after the server first boots up in order to fully run the mysql daemon.  I kept logging in right away, seeing that it wasn't running and trying to stop it through ```
/etc/init.d/mysql restart
``` which kept either having strange messages or just hanging.  

Now, I am back to square one.  The mysqld is running, but I can't connect to the mysql service on another machine.  

Under /etc/mysql/my.cnf, I have 
```
bind-address            = 0.0.0.0
``` 
in order to allow it to accept any incoming connection.  However, I can't connect from another machine, only locally.  I can connect via ssh to the server, so I know it's not a network issue.

---

### Post by Bachstelze on 2010-05-10
> **senor_smile said:**
> 
However, I can't connect from another machine, only locally.

What happens when you try?

---

### Post by senor_smile on 2010-05-10
> **Bachstelze said:**
> What happens when you try?

```
ERROR 1130 (HY000): Host '192.168.5.130' is not allowed to connect to this MySQL server
```

---

### Post by Bachstelze on 2010-05-10
> **senor_smile said:**
> ```
ERROR 1130 (HY000): Host '192.168.5.130' is not allowed to connect to this MySQL server
```

This is not really a connection problem then, you can connect to the server just fine, it's just denying you access. Check your privileges table.

---

### Post by cdenley on 2010-05-10
There is a bug in 10.04. If you have it bind to a specific interface, it will fail to start on reboot because it attempts to start after any network interface (such as 127.0.0.1) is initialized. The interface it was configured to bind with won't be initialized yet. You can either bind it to all interfaces by commenting that line out, or edit /etc/init/mysql.conf.
```

# MySQL Service

description     "MySQL Server"
author          "Mario Limonciello <superm1@ubuntu.com>"

start on (net-device-up** IFACE=eth0**
          and local-filesystems)
stop on runlevel [016]

respawn

env HOME=/etc/mysql
umask 007

pre-start script
    #Sanity checks
    [ -r $HOME/my.cnf ]
    [ -d /var/run/mysqld ] || install -m 755 -o mysql -g root -d /var/run/mysqld
    LC_ALL=C BLOCKSIZE= df --portability /var/lib/mysql/. | tail -n 1 | awk '{ exit ($4<4096) }'
end script

exec /usr/sbin/mysqld

post-start script
    while ! /usr/bin/mysqladmin --defaults-file=$HOME/debian.cnf ping
    do
        sleep 1
    done
    exec $HOME/debian-start
end script

```
[https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.1/+bug/566736](https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.1/+bug/566736)

For error 1130, you need to grant permission for that host to connect remotely.
```

GRANT ALL ON table.* TO 'user'@'192.168.5.130' identified by 'mypassword';

```
or for any host
```

GRANT ALL ON table.* TO 'user'@'%' identified by 'mypassword';

```

---

### Post by senor_smile on 2010-05-10
> **Bachstelze said:**
> This is not really a connection problem then, you can connect to the server just fine, it's just denying you access. Check your privileges table.

Ah, I see.  This is my first mysql installation.  I am installing it to try to figure out how to use it in lieue of MS sql.  

I googled around a bit on setting privileges.  I tried a few commands but none were successful.  How would I add a single local host, or a subnet to allow access to mysql?

---

### Post by cdenley on 2010-05-10
> **senor_smile said:**
> I googled around a bit on setting privileges.  I tried a few commands but none were successful.  How would I add a single local host, or a subnet to allow access to mysql?

See the end of my previous post.

---

### Post by senor_smile on 2010-05-10
> **cdenley said:**
> See the end of my previous post.

Ah thanks, I think we were writing our replies at the same time.  
When I run either command I get:

```
mysql> GRANT ALL on table.* to root@% identified by 'temppassword';
ERROR 1064 (42000): You have an error in your SQL syntax; check the
 manual that corresponds to your MySQL server version for the right 
syntax to use near '* to root@% identified by 'temppassword'' at 
line 1
```

---

### Post by cdenley on 2010-05-10
> **senor_smile said:**
> Ah thanks, I think we were writing our replies at the same time.  
When I run either command I get:

```
mysql> GRANT ALL on table.* to root@% identified by 'temppassword';
ERROR 1064 (42000): You have an error in your SQL syntax; check the
 manual that corresponds to your MySQL server version for the right 
syntax to use near '* to root@% identified by 'temppassword'' at 
line 1
```

You need to substitute "table" with the table name you want to connect with, the username has to be in quotes, and the hostname has to be in quotes.

---

### Post by senor_smile on 2010-05-10
> **cdenley said:**
> You need to substitute "table" with the table name you want to connect with, the username has to be in quotes, and the hostname has to be in quotes.

Thank you!  I hadn't realized those were "variables" to be filled in.  That worked like a charm.

---

### Post by cdenley on 2010-05-10
> **senor_smile said:**
> Thank you!  I hadn't realized those were "variables" to be filled in.  That worked like a charm.

That should be "database" not "table". I just realized my mistake.

---

### Post by fixitdude on 2011-06-30
Also check to see if it's "my.cnf" NOT "my.conf", it's easy to get that wrong and some places even show it that way.

---

### Post by 123fix on 2012-04-12
I can give you better solution for installation.

i found great article about this
some fixes also there, auto configuration:

[http://www.discusswire.com/mysql-installation-ubuntu-10-04/](http://www.discusswire.com/mysql-installation-ubuntu-10-04/)

---

