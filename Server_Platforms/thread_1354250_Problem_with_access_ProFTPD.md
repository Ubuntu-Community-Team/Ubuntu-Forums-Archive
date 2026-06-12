---
title: "Problem with access? ProFTPD"
date: 2009-12-13
forum: Server Platforms
---

### Post by Spikerok on 2009-12-13
I have installed latest ProFTPD ( ' apt-get install proftpd ' ) and got it running with MySQL

But after trying to access ftp on same computer I got error that apparently I have used incorrect password.

Answer - i have installed proftpd incorrectly.

After deleting it ProFTPD

```

sudo apt-get autoremove proftpd
sudo rm -rf /etc/proftpd/

```

I have installed it again, but correct version.
```

apt-get install proftpd-mod-mysql

```

---

### Post by Spikerok on 2009-12-13
doubple post

---

### Post by Spikerok on 2009-12-13
double post

---

### Post by Spikerok on 2009-12-13
double post

---

### Post by Spikerok on 2009-12-13
double post

---

### Post by Spikerok on 2009-12-14
bump

---

### Post by Spikerok on 2009-12-14
double post

---

