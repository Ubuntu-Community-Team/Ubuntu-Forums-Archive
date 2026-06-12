---
title: "I can't get a config file my.cnf in mysql-server"
date: 2011-05-02
forum: Server Platforms
---

### Post by thoufiq on 2011-05-02
Hi All,
        I am the new user of linux and when installing mysql-server by this command [COLOR=Red]**sudo apt-get install mysql-server**[/COLOR]. Installaton is complete but i cant get a [COLOR=Red]**my.cnf**[/COLOR] file. Can anyone tell, what is the mistake i did and how to overcome from this error. Here, i am posting the results

[COLOR=Red][B]sam-osm@dhcppc4:~$ sudo nano /etc/mysql/
conf.d/   debian.cnf
[/B][/COLOR]


Thanks

---

### Post by volkswagner on 2011-05-02
Not sure what version you are using, but for Ubuntu 8.04 the location is:

/etc/mysql/my.cnf

```
ls /etc/mysql
conf.d  debian.cnf  debian-start  my.cnf

```

Verify your version:
```
mysql -V
```

You can try to reconfigure and see what happens.

```
sudo dpkg-reconfigure mysql-server-5.x
```

Replace the version number with what you found from earlier command.

---

### Post by jantonio.martin on 2011-06-14
I'm having just the same problem here in Ubuntu 10.04, with mysql-server-5.1.

```

sudo dpkg-reconfigure mysql-server-5.1

```

After running this, I am promted for a password, and then, I get this:

```

stop: Unknown instance:
110614  7:48:45 [Note] Plugin 'FEDERATED' is disabled.
110614  7:48:45  InnoDB: Started; log sequence number 0 44233
110614  7:48:45  InnoDB: Starting shutdown...
110614  7:48:46  InnoDB: Shutdown completed; log sequence number 0 44233
start: Job failed to start

```

Also, I can't find a my.cnf in my system:

```

ls /etc/mysql/
conf.d  debian.cnf  debian-start

```

By the way, I have been a whole day trying to get a working installation of mysql-server in Ubuntu-10.04-LTS, with no success. Among other things, I have made this:
[http://ubuntuforums.org/showpost.php?p=9852482&postcount=20](http://ubuntuforums.org/showpost.php?p=9852482&postcount=20)

---

