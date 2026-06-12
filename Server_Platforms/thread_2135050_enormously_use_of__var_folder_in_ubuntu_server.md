---
title: "enormously use of  /var folder in ubuntu server"
date: 2013-04-13
forum: Server Platforms
---

### Post by perco on 2013-04-13
Hi I have Ubuntu server running Virtualmin and it work like dedicated web server. But the problem is it with the /var directory which is on separate partition of 7 GB and is now full. But when I run the comand:
df -h var/ 
Filesystem Size Used Avail Use% Mounted on /dev/sda7 7.4G 6.6G 379M 95% /var

but when i run the command:
du -ch var/
 793M total

How I can clean this and is this posible? 
Thanks a lot

---

### Post by deadflowr on 2013-04-13
You could run
```
sudo apt-get clean
```

which should clear up the /var/cache/apt stuff.

You could also look at the log files in /var/log, and look at deleting older log files.

There are probably twenty other things you could do to that directoryto clean it up,  but those two are simple.

---

### Post by prodigy_ on 2013-04-13
```
find /var -type f -exec du -b '{}' \; | sort -rn | less
``` will output the list of all files in /var sorted by file size in bytes.

---

### Post by perco on 2013-04-13
du -sh *
1.5M    backups
43M     cache
4.0K    crash
454M    lib
4.0K    local
0       lock
24M     log
16K     lost+found
4.0K    mail
4.0K    opt
92K     run
24M     spool
4.0K    tmp
44K     usermin
67M     webmin
196K    www

---

### Post by perco on 2013-04-13
> **prodigy_ said:**
> ```
find /var -type f -exec du -b '{}' \; | sort -rn | less
``` will output the list of all files in /var sorted by file size in bytes.

it return empty screan

---

### Post by prodigy_ on 2013-04-13
Yeah, while **sort** is waiting for **du**. Don't worry.

---

### Post by volkswagner on 2013-04-13
I see your du command has no total for /var.

Try:

```
sudo du -h --max-depth=1 /var
```

Compare the difference of the sub directories to the /var directory.  The difference is the contents of /var not including sub directories.

The large file can be in the root of /var, so do:

```
ls -alh /var
```

---

