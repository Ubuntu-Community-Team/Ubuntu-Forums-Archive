---
title: "mysql died overnight on my Ubuntu 8.04 server"
date: 2011-01-14
forum: Server Platforms
---

### Post by scheibo on 2011-01-14
After X days of blissful uptime my mysql failed on my server for some reason. I have had 0 problems with it for over a year and it simply died overnight. I have been upgrading old packages occasionally so it is possible that could have effected it. Anyway, after reading around tons about how /var/run/mysqld/mysql.sock doesn't exist and solutions to fix it I finally ended up attempting to reinstall mysql (I take regular database backups so I wan't concerned about losing data). The typescript from this endeavor is here: [https://gist.github.com/779972](https://gist.github.com/779972). Hopefully someone knows what the heck is going on?

Cheers



EDIT: after pulling my hair out trying to get this to work for 5 days I decided to install simply wipe out ubuntu entirely and install 10.4 and try again. this worked, but its a horrible solution.

---

### Post by Thirtysixway on 2011-01-15
Is your disk full?

---

### Post by Thirtysixway on 2011-01-15
(stupid server, double post)

---

### Post by scheibo on 2011-01-15
> **Thirtysixway said:**
> Is your disk full?


I thought of that, I included a df in the gist already:

```

root@scheibo# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/xvda1             12G  4.1G  6.7G  38% /
udev                  261M  124K  261M   1% /dev
none                  261M     0  261M   0% /dev/shm
none                  261M   28K  261M   1% /var/run
none                  261M     0  261M   0% /var/lock
none         

```

Doesn't seem to be full from what I can tell

---

### Post by scheibo on 2011-01-15
> **Thirtysixway said:**
> Is your disk full?


I thought of that, I included a df in the gist already:

```

root@scheibo# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/xvda1             12G  4.1G  6.7G  38% /
udev                  261M  124K  261M   1% /dev
none                  261M     0  261M   0% /dev/shm
none                  261M   28K  261M   1% /var/run
none                  261M     0  261M   0% /var/lock
none         

```

Doesn't seem to be full from what I can tell

---

### Post by scheibo on 2011-01-15
> **Thirtysixway said:**
> Is your disk full?


I included a `df` dump in the gist file:

```

root@scheibo# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/xvda1             12G  4.1G  6.7G  38% /
udev                  261M  124K  261M   1% /dev
none                  261M     0  261M   0% /dev/shm
none                  261M   28K  261M   1% /var/run
none                  261M     0  261M   0% /var/lock
none                  261M     0  261M   0% /lib/init/rw

```

Doesn't seem that anything is full from what I can tell.

- scheibo

---

### Post by scheibo on 2011-01-15
> **Thirtysixway said:**
> Is your disk full?


I included a `df` dump in the gist file:

```

root@scheibo# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/xvda1             12G  4.1G  6.7G  38% /
udev                  261M  124K  261M   1% /dev
none                  261M     0  261M   0% /dev/shm
none                  261M   28K  261M   1% /var/run
none                  261M     0  261M   0% /var/lock
none                  261M     0  261M   0% /lib/init/rw

```

Doesn't seem that anything is full from what I can tell.

- scheibo

---

