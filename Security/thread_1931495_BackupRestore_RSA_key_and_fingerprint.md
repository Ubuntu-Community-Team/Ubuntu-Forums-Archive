---
title: "Backup/Restore RSA key and fingerprint?"
date: 2012-02-25
forum: Security
---

### Post by Jonathan L on 2012-02-25
Hi All

I've got somes systems which are frequently, and automatically, installed from a CD-ROM image.  All works perfectly according to what's required except it would be good to restore the RSA Key (and fingerprints) so that when I ssh from another system it doesn't think it's been changed.

So my question is, which files do I backup and restore so that the ssh works without "WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!", and without opening up a pile of trouble.

Is it just these four? 
```
-rw------- 1 root root  668 2012-02-22 12:39 /etc/ssh/ssh_host_dsa_key
-rw-r--r-- 1 root root  601 2012-02-22 12:39 /etc/ssh/ssh_host_dsa_key.pub
-rw------- 1 root root 1675 2012-02-22 12:39 /etc/ssh/ssh_host_rsa_key
-rw-r--r-- 1 root root  393 2012-02-22 12:39 /etc/ssh/ssh_host_rsa_key.pub

```And then I presume?
 ```
/etc/init.d/ssh restart
```Any help and advice gratefully received.

Kind regards,
Jonathan.

---

### Post by CharlesA on 2012-02-25
Should work.

The location of the fingerprint files are located in /etc/ssh/sshd_config

---

### Post by Jonathan L on 2012-02-26
> Should work.Thanks Charles, works fine.

I added the following in a script called by rc.local:
```
(get keys.tar)
tar xpf keys.tar -C /etc/ssh
/etc/init.d/ssh restart
```Kind regards,
Jonathan.

---

### Post by CharlesA on 2012-02-26
Outstanding. :)

---

