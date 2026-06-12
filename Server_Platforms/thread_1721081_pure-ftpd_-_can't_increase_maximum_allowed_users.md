---
title: "pure-ftpd - can't increase maximum allowed users"
date: 2011-04-04
forum: Server Platforms
---

### Post by c01e on 2011-04-04
I running the command 

```

/usr/sbin/pure-ftpd -l puredb:/etc/pure-ftpd/pureftpd.pdb -X -O clf:/var/log/pure-ftpd/transfer.log -A -u 1000 -p 40110:40115 -x -C 100 -P SOME.IP -8 UTF-8 -c 20 -E -B 

```

But it still says my maxium allowed users are 3:

```

someone@somewhere:~$ ftp www
Connected to www.somewhere.com.
220---------- Welcome to Pure-FTPd [privsep] [TLS] ----------
220-You are user number 1 of 3 allowed.

```

FYI: I'm using Ubuntu 10.04.2 LTS

Any ideas?

---

### Post by falko on 2011-04-04
I suggest you try
```
echo "100" > /etc/pure-ftpd/conf/MaxClientsNumber
```
Then restart PureFTPd using its init script (in /etc/init.d).

---

### Post by c01e on 2011-04-04
Definitely not that. As you can see from the command it was first set to 20. I just changed it to 100 for the hell of it. But still no luck. Any other suggestions?

```

root@www:~# cat /etc/pure-ftpd/conf/MaxClientsNumber 
100
root@www:~# cat /etc/pure-ftpd/conf/MaxClientsPerIP 
100

```

---

### Post by falko on 2011-04-04
When you ran that /usr/sbin/pure-ftpd command - are you sure that no other PureFTPd instance was running?

---

### Post by c01e on 2011-04-04
100%.

Anyway fixed the issue. There where two problems: the passive port range and the order of -c and -p.

The port range based on my first case was: (40115 + 1 - 40110) / 2=3

And ubuntu doesn't ensure -c comes before -p, so if you use the default config and run script in /etc/init.d/pure-ftpd then it will not work (even if you get the port range correct).

---

