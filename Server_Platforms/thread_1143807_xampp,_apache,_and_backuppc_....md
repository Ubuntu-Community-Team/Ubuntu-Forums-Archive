---
title: "xampp, apache, and backuppc ..."
date: 2009-04-30
forum: Server Platforms
---

### Post by dakochan on 2009-04-30
Hi,

Sometimes ago I installed xampp on my linux mint 6 (ubuntu 8.10) at "/opt/lampp", and it was working perfectly. I can access xampp with "http://localhost" and it would be automatically redirectly to "http://localhost/xampp".

A few days ago I installed backuppc into my pc. I think it also automatically installed apache2 into my system. When I tried to connect to "http://localhost", it showed "It works!", and never connected to xampp again. I also remembered when I installed the backuppc, it also mentioned that I could access backuppc through "http://presario" (presario is my pc name). In addition, I also could not connect to backuppc, even though I tried to access using "http://presario/backuppc".

In the "/etc/hosts", it contains:
```
127.0.0.1	localhost
127.0.1.1	presario

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

According to the "hosts" file I should be able to connect to xampp, but I can't.
Now I have to disabled the apache2 from the Services menu, in order to access xampp.

1. Anyone can help me to access xampp while I can use backuppc?

2. How to run the backuppc?

3. I understand that the "root" for xampp is in "/opt/lampp/htdocs" folder, and for apache2 is "/var/www". But how to find the setting file that contains "http://localhost" should link to "/opt/lampp/htdocs", while "http://presario" should link to "/var/www"?

Please help. 


Best Regards,
Dakochan.

---

### Post by Kareeser on 2009-04-30
Oooh, shifty. You might have conflicting apache installs.

Traditionally, apache is installed in /etc/apache2, this is most likely where backuppc installed apache to.

Since xampp isn't configured to co-exist peacefully with the second apache install, it most likely failed to start during system boot-up.

First, shutdown the initial apache install, temporarily:
```
sudo /etc/init.d/apache2 -k graceful-stop
```

Then search /opt/lampp for some sort of startup script, assuming apache is installed there as well.

---

### Post by dakochan on 2009-04-30
Hi Kareeser,
From your explaination I guess I won't be able to use backuppc while I'm using xampp, am I right ?
Btw, do you know how the system know if "http://localhost" link to "/opt/lampp/htdocs" folder?

Thanks,
Dakochan

---

