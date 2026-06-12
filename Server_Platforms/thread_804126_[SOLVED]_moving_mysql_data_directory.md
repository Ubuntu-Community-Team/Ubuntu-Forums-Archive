---
title: "[SOLVED] moving mysql data directory"
date: 2008-05-22
forum: Server Platforms
---

### Post by floz23 on 2008-05-22
Ok, I'm on a fresh server install of 8.04, with the mysql installed via the menu during the install.

Here are the steps I used:

1. stopped mysql.

2. I copied the /var/lib/mysql to /srv/mysql ```
sudo cp /var/lib/mysql /srv/mysql -p -r
``` to preserve all directory and file attributes.

3. Edited the /etc/mysql/my.cnf ```
datadir = /var/lib/mysql
``` was replaced with ```
datadir = /srv/mysql

```

4. Edited the /etc/apparmor.d/usr.sbin.mysqld, replaced ```
/var/lib/mysql/ r,
/var/lib/mysql/** rwk,

``` with ```
/srv/mysql/ r,
/srv/mysql/** rwk,
```
 
5. restarted apparmor.d

6. restarted mysql.d

7. got a [fail!] when trying to restart mysql.d, here is the error i got..```
May 22 21:03:12 larouchenet mysqld_safe[10288]: started
May 22 21:03:12 larouchenet mysqld[10291]: 080522 21:03:12 [Warning] Can't create test file /srv/mysql/larouchenet.lower-test
May 22 21:03:12 larouchenet mysqld[10291]: 080522 21:03:12 [Warning] Can't create test file /srv/mysql/larouchenet.lower-test
May 22 21:03:12 larouchenet mysqld[10291]: 080522 21:03:12  InnoDB: Operating system error number 13 in a file operation.
May 22 21:03:12 larouchenet mysqld[10291]: InnoDB: The error means mysqld does not have the access rights to
May 22 21:03:12 larouchenet mysqld[10291]: InnoDB: the directory.
May 22 21:03:12 larouchenet mysqld[10291]: InnoDB: File name ./ibdata1
May 22 21:03:12 larouchenet mysqld[10291]: InnoDB: File operation call: 'open'.
May 22 21:03:12 larouchenet mysqld[10291]: InnoDB: Cannot continue operation.
May 22 21:03:12 larouchenet mysqld_safe[10298]: ended

```

Am I missing a step?  As far as I can see, all of the permissions are exactly the same as when the directory was in /var/lib

Please, can anyone help?

-Adam S.

---

### Post by floz23 on 2008-05-22
Damn apparmor to hell! Just Kidding, I just solved my own problem, and I've give others the solution here, in case you do what I did.

My steps were right, but I did one extra thing.  I made a backup copy of the /etc/apparmor.d/usr.sbin.mysqld to /etc/apparmor.d/usr.sbin.mysqld.backup

It turns out the apparmor was loading BOTH configurations, with the second, backup one, overwriting the configuration of the updated one. 

Solution, delete the backup /etc/apparmor.d/usr.sbin.mysqld configuration, restart apparmor and mysql.

This is a MAJOR b*tch.  Thanks everyone ;)

---

### Post by photostyle on 2008-06-26
I spent all afternoon fighting this error. The apparmor profile adjustments did the trick for me. I didn't even know about apparmor until now.

(yes, I'm a linux noob.)

---

### Post by quackking on 2008-06-27
THANK YOU!!! What a PITA, I never would have thought of this..Now my MySQL  server is happily striping to a RAID 10! 

Whew...

---

### Post by l3dx on 2008-08-17
Thanks!

I also had problems getting MySQL up and running after changing the datadir location to my RAID.
I'd never even heard of apparmor...

---

### Post by Stretsh on 2008-09-22
Same here, never heard of apparmor before. Read something about it in the my.conf, but I thought it concerned the mysqld.sock.

Thanks a million for this one.

---

### Post by payman on 2009-08-12
> **floz23 said:**
> Damn apparmor to hell! Just Kidding, I just solved my own problem, and I've give others the solution here, in case you do what I did.

My steps were right, but I did one extra thing.  I made a backup copy of the /etc/apparmor.d/usr.sbin.mysqld to /etc/apparmor.d/usr.sbin.mysqld.backup

It turns out the apparmor was loading BOTH configurations, with the second, backup one, overwriting the configuration of the updated one. 

Solution, delete the backup /etc/apparmor.d/usr.sbin.mysqld configuration, restart apparmor and mysql.

This is a MAJOR b*tch.  Thanks everyone ;)

Thanks a lot. I have opened a bug on this. Look here:
[https://bugs.launchpad.net/bugs/403898](https://bugs.launchpad.net/bugs/403898)
I hope it is fixed.

---

### Post by floz23 on 2009-08-12
How is any of this a bug?  I believe this is exactly how apparmor is supposed to function.  The only complaint I had was the lack of documentation of how this all works.

Regards,

---

### Post by Wim Sturkenboom on 2009-08-13
> **payman said:**
> Thanks a lot. I have opened a bug on this. Look here:
[https://bugs.launchpad.net/bugs/403898](https://bugs.launchpad.net/bugs/403898)
I hope it is fixed.Very off topic but how the hell did you get it right to already get answers there :confused: I posted a bug ( [https://bugs.launchpad.net/ubuntu/+bug/389308](https://bugs.launchpad.net/ubuntu/+bug/389308) ) in june and still have not seen any activity around it :mad:

---

### Post by payman on 2009-08-13
> **floz23 said:**
> How is any of this a bug?  I believe this is exactly how apparmor is supposed to function.  The only complaint I had was the lack of documentation of how this all works.

Regards,

Well, if it's not a bug in apparmor, then it is definitely a bug in ubuntu packaging system that creates the extra conf files in the apparmor directory. Personally, I think apparmor shouldn't use the other conf files for mysql.

> **Wim Sturkenboom said:**
> Very off topic but how the hell did you get it right to already get answers there :confused: I posted a bug ( [https://bugs.launchpad.net/ubuntu/+bug/389308](https://bugs.launchpad.net/ubuntu/+bug/389308) ) in june and still have not seen any activity around it :mad:

I don't know. I just used the launchpad report wizard when the crash appeared and I was contacted by them later on.

---

