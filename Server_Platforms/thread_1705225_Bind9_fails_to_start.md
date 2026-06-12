---
title: "Bind9 fails to start"
date: 2011-03-11
forum: Server Platforms
---

### Post by inckiekage on 2011-03-11
Just installed a bind9 on Ubuntu 10.10, what am i missing here:

```
#1 Error
Mar 12 02:57:31 localhost named[16842]: loading configuration from '/etc/bind/named.conf'
Mar 12 02:57:31 localhost named[16842]: none:0: open: /etc/bind/named.conf: permission denied
Mar 12 02:57:31 localhost named[16842]: loading configuration: permission denied
Mar 12 02:57:31 localhost named[16842]: exiting (due to fatal error)
```
```
#2 Error 
Mar 12 02:57:31 localhost kernel: [276857.641381] type=1400 audit(1299895051.592:12): apparmor="DENIED" operation="open" parent=16841 profile="/usr/sbin/named" name="/var/lib/named/etc/bind/named.conf" pid=16843 comm="named" requested_mask="r" denied_mask="r" fsuid=103 ouid=0
```

```
# /etc/bind/named.conf
-rw-r--r-- 1 root bind 463 2011-02-23 16:22 /etc/bind/named.conf
```

What i have tried so far:
[LIST=1]
[*]Stopped AppArmor
[*]chmodded /etc/bind/named.conf to 777
[*]sudo apt-get remove --purge bind9 && sudo apt-get install bind9
[/LIST]

---

### Post by SeijiSensei on 2011-03-11
> **inckiekage said:**
> 
```
#2 Error 
Mar 12 02:57:31 localhost kernel: [276857.641381] type=1400 audit(1299895051.592:12): apparmor="DENIED" operation="open" parent=16841 profile="/usr/sbin/named" name="/var/lib/named/etc/bind/named.conf" pid=16843 comm="named" requested_mask="r" denied_mask="r" fsuid=103 ouid=0
```

```
# /etc/bind/named.conf
-rw-r--r-- 1 root bind 463 2011-02-23 16:22 /etc/bind/named.conf
```



Did you happen to make the server run in a chrooted environment as it says in /etc/init.d/bind9?

```
# for a chrooted server: "-u bind -t /var/lib/named"
```

The apparmor error above refers to the file /var/lib/named/etc/bind/named.conf, which is where the file /etc/bind/named.conf would be if running in a chrooted environment that begins in /var/lib/named.  Did you add those to the OPTIONS environment variable in /etc/init.d/bind9 or change /etc/default/bind9?

If you do want to run in a chrooted environment, create /var/lib/named/etc/bind/ and copy into it the contents of /etc/bind.  Use chown/chmod to assign ownership on /var/lib/named and its subdirectories to user and group bind with 0750 permissions, and assign 0640 permissions on all files.

---

### Post by inckiekage on 2011-03-12
> **SeijiSensei said:**
> Did you happen to make the server run in a chrooted environment as it says in /etc/init.d/bind9?

```
# for a chrooted server: "-u bind -t /var/lib/named"
```

The apparmor error above refers to the file /var/lib/named/etc/bind/named.conf, which is where the file /etc/bind/named.conf would be if running in a chrooted environment that begins in /var/lib/named.  Did you add those to the OPTIONS environment variable in /etc/init.d/bind9 or change /etc/default/bind9?


If you do want to run in a chrooted environment, create /var/lib/named/etc/bind/ and copy into it the contents of /etc/bind.  Use chown/chmod to assign ownership on /var/lib/named and its subdirectories to user and group bind with 0750 permissions, and assign 0640 permissions on all files.

[LIST=1]
[*]added the options to the OPTIONS variable.
[*]chown -R root:bind /var/lib/named
[*]chmodded all files 640 in /var/lib/named and subdirectories
[/LIST]

Now it looks like:
```
root@matilde:~# ls -la /var/lib/named/
total 20
drwxr-x---  5 root bind 4096 2011-02-27 01:54 .
drwxr-xr-x 42 root root 4096 2011-03-12 02:57 ..
drwxr-x---  2 root bind 4096 2011-02-27 01:54 dev
drwxr-x---  3 root bind 4096 2011-02-27 01:54 etc
drwxr-x---  4 root bind 4096 2011-02-27 01:54 var
```

```
root@matilde:/var/lib/named/etc/bind# ls -la
total 60
drwxr-sr-x 2 root bind 4096 2011-03-12 02:57 .
drwxr-x--- 3 root bind 4096 2011-02-27 01:54 ..
-rw-r----- 1 root bind  601 2011-02-23 16:22 bind.keys
-rw-r----- 1 root bind  237 2011-02-23 16:22 db.0
-rw-r----- 1 root bind  271 2011-02-23 16:22 db.127
-rw-r----- 1 root bind  237 2011-02-23 16:22 db.255
-rw-r----- 1 root bind  353 2011-02-23 16:22 db.empty
-rw-r----- 1 root bind  270 2011-02-23 16:22 db.local
-rw-r----- 1 root bind 2994 2011-02-23 16:22 db.root
-rw-r----- 1 root bind  463 2011-02-23 16:22 named.conf
-rw-r----- 1 root bind  490 2011-02-23 16:22 named.conf.default-zones
-rw-r----- 1 root bind  165 2011-02-23 16:22 named.conf.local
-rw-r----- 1 root bind  572 2011-02-23 16:22 named.conf.options
-rw-r----- 1 root bind    0 2011-02-27 02:04 rndc.conf
-rw-r----- 1 root bind   77 2011-03-12 02:57 rndc.key
-rw-r----- 1 root bind 1317 2011-02-23 16:22 zones.rfc1918
```

Still no luck, same errors.

The bind user can read the named.conf file
i could read it with nano running it like this
sudo -u bind nano /var/lib/named/etc/bind/named.conf
and this failed
sudo -u kimse nano /var/lib/named/etc/bind/named.conf which it should, because of the file rights.

---

