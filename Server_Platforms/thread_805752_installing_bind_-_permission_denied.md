---
title: "installing bind - permission denied"
date: 2008-05-24
forum: Server Platforms
---

### Post by Mrwasab1 on 2008-05-24
Hi all,

I have installed 8.04 server and am in the process of setting it up.
I am following a fairly simple to use guide located [Here](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p4).
Now i got as far as setting up my DNS server and now ive come to a road block. When i attempt to start bind, i get the following 

```

* Starting domain name service... bind                                  [fail] 
```

i check /var/log/syslog to see what is happening and it tells me that it failed due to not being able to open a file, due to permissions.
here is the result of tail -10

```

May 24 23:06:03 wasabi-server001 named[7834]: loading configuration: permission denied
May 24 23:06:03 wasabi-server001 named[7834]: exiting (due to fatal error)
May 24 23:06:03 wasabi-server001 kernel: [ 6408.616166] audit(1211634363.625:10): type=1503 operation="inode_permission" requested_mask="r::" denied_mask="r::" name="/var/lib/named/etc/bind/named.conf" pid=7835 profile="/usr/sbin/named" namespace="default"
May 24 23:07:12 wasabi-server001 named[7876]: starting BIND 9.4.2 -u bind -t /var/lib/named
May 24 23:07:12 wasabi-server001 named[7876]: found 1 CPU, using 1 worker thread
May 24 23:07:12 wasabi-server001 named[7876]: loading configuration from '/etc/bind/named.conf'
May 24 23:07:12 wasabi-server001 named[7876]: none:0: open: /etc/bind/named.conf: permission denied
May 24 23:07:12 wasabi-server001 named[7876]: loading configuration: permission denied
May 24 23:07:12 wasabi-server001 named[7876]: exiting (due to fatal error)
May 24 23:07:12 wasabi-server001 kernel: [ 6477.135475] audit(1211634432.275:11): type=1503 operation="inode_permission" requested_mask="r::" denied_mask="r::" name="/var/lib/named/etc/bind/named.conf" pid=7877 profile="/usr/sbin/named" namespace="default"
```

i checked the permissions of the file (and following the tutorial to the letter and no where does it tell me to touch the permissions for this file) and this is what they are

```

-rw-rw-rw- 1 bind bind 907 2008-04-10 05:42 /etc/bind/named.conf
```

while doing all this i am logged in as root, so i dont think i should have a problem.

Anyways ive tried googling but nothing ive found has resolved this problem. 

any ideas would be welcome

---

### Post by RealPSL on 2008-05-25
Do you have the selinux package installed?

```
dpkg --list selinux
```

I would also not leave that /etc/bind/named.conf file with the world writable permisions. SELinux might be providing an extra layer of security you might not be expecting.

---

### Post by Mrwasab1 on 2008-05-25
no i dont have that package installed. The guide i was following didnt request it, so i didnt think it was necessary. 

I changed the permission of the file to be writeable for testing, obviously it didnt work, but i have since changed it back to  RW R R.

I dont know why but after a reboot of the server, bind started up normally. Thanks anyway

---

### Post by yonkman on 2008-05-29
I found the fix here

[http://www.howtoforge.org/forums/showthread.php?p=116893](http://www.howtoforge.org/forums/showthread.php?p=116893)

---

