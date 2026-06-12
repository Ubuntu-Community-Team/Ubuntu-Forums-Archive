---
title: "proftpd Permission denied after upgrade from ubuntu server 8.1 to 9.1"
date: 2010-05-24
forum: Server Platforms
---

### Post by Nessaja on 2010-05-24
Hi,

After upgrading ubuntu server to the latest version (according to apt-get) proftpd stopped working. When I try to execute proftpd I get the following message (when logged in as root or user with root privileges) :


```


root@squid:/home/squid# proftpd -t
Checking syntax of configuration file
 - Fatal: LoadModule: error loading module 'mod_ldap.c': Permission denied on line 18 of '/etc/proftpd/modules.conf'


```Line 18 in modules.conf looks like this:

```


LoadModule mod_ldap.c


```I've tried removing and re-installing proftpd, but this doesn't help
If I comment line 18 in modules.conf, I just get permission denied on the next LoadModule command...

Can I remove all modules? or is there a way of fixing the permission denied issue?

---

### Post by yaztromo on 2010-08-29
I had this problem upgrading a hardy server to lucid.

The old modules.conf file is not compatible with the new proftpd-basic package.

Copy your /etc/proftpd/proftpd.conf to a safe place then do

apt-get purge proftpd-basic

apt-get install proftpd-basic

Then put back in your saved proftpd.conf if you wish.

---

### Post by ddoxey on 2010-11-06
Same problem here. Thanks **yaztromo** for the great tip.

```
cd /etc/proftpd
sudo ls *.conf | awk '{print "sudo mv "$1" "$1".old"}' | sh
sudo apt-get --reinstall install proftpd-basic
```

---

