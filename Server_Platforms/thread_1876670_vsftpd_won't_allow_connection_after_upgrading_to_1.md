---
title: "vsftpd won't allow connection after upgrading to 11.10"
date: 2011-11-06
forum: Server Platforms
---

### Post by hirohitosan on 2011-11-06
Hi there 
I upgraded my Ub server from 11.04 to 11.10 and I cannot log in as a local user to vsftp server.

My  /etc/vsftpd.conf is same as before:
```

listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
# Debian customization
secure_chroot_dir=/var/run/vsftpd/empty
rsa_cert_file=/etc/ssl/private/vsftpd.pem

```

When I try to log in using my user name and pass it comes:
```
Connected to 111.222.333.444.
220 (vsFTPd 2.3.2)
Name (111.222.333.444:user):
331 Please specify the password.
Password:
530 Login incorrect.
Login failed.

```

Please help me to solve this!

Many thanks!

---

### Post by jbfoley1 on 2012-01-21
For what it's worth, I have the same problem.  I'm using exactly the same config as I used in 10.04 which worked fine, but I have the same thing.  I also added /usr/sbin/nologin and /bin/false to /etc/shells and tried changing the root directories specified for the users to chmod 777, and no luck.  

I can get it to work if I use anonymous login, but always 530 login incorrect for local users.

Please help!

---

### Post by LHammonds on 2012-01-21
Could this be the result of apparmor getting in the way?

---

### Post by kevinthecomputerguy on 2012-01-22
+1 LHammonds

Also try running vsftpd as a dameon

Also try stopping UFW (assuming you know about iptables and the risks)

---

