---
title: "OpenSSH Chroot Issue"
date: 2010-02-11
forum: Server Platforms
---

### Post by SectorNine50 on 2010-02-11
I have OpenSSH configured to allow a user to be Chroot'd to a folder he owns (/var/www/mventura), however, every time FileZilla tries to log in, an error comes up saying:

Connection closed by server with exitcode 2147483647
Could not connect to server

However, when I Chroot him one file up (/var/www) he can just enter mventura and operate perfectly that way.  While it doesn't really cause any issues since he doesn't have permission to access anything above mventura, it doesn't really pose a security threat.  However, I'd rather not have my SFTP users seeing what I have in my www folder.

Here's what I have written in my OpenSSH_config file:

Match user mventura
ChrootDirectory /var/www/mventura
ForceCommand internal-sftp
X11Forwarding no
AllowTcpForwarding no

When I change the Chroot directory to this:

ChrootDirectory /var/www

Everything works fine, he just doesn't log-in in the /mventura folder like I want him to.

Any idea as to what's going on?  I can't find much info on the FileZilla error on google.

---

### Post by joberly on 2010-02-11
Post the output of 

ls -l /var/
and
ls -l /var/www/

Usually the chroot'd directory must be owned by root. /var/www probably is, and /var/www/mventura is most likely not.

---

### Post by SectorNine50 on 2010-02-11
Here ya go:
```
root@wileyserver:~# ls -l /var/
total 44
drwxr-xr-x  2 root root 4096 2010-02-05 06:58 backups
drwxr-xr-x 11 root root 4096 2010-01-20 02:50 cache
drwxrwxrwt  2 root root 4096 2010-01-28 06:25 crash
drwxr-xr-x 33 root root 4096 2010-01-23 04:20 lib
drwxrwsr-x  2 root root 4096 2009-10-19 17:04 local
drwxrwxrwt  4 root root   80 2010-02-11 06:38 lock
drwxr-xr-x 13 root root 4096 2010-02-11 06:38 log
drwxrwsr-x  2 root root 4096 2010-01-19 22:20 mail
drwxr-xr-x  2 root root 4096 2010-01-19 22:20 opt
drwxr-xr-x 12 root root  520 2010-02-11 11:15 run
drwxr-xr-x  4 root root 4096 2010-01-19 22:32 spool
drwxrwxrwt  2 root root 4096 2009-10-19 17:04 tmp
drwxr-xr-x  3 root root 4096 2010-02-11 02:25 www

```
```
root@wileyserver:~# ls -l /var/www/
total 8
-rw-r--r-- 1 root     root  133 2010-02-11 02:25 index.html
drwxr-x--x 3 mventura root 4096 2010-02-05 21:22 mventura
lrwxrwxrwx 1 root     root   21 2010-01-20 02:55 phpsysinfo -> /usr/share/phpsysinfo
```

So your saying even though that is set as the user's home, the user shouldn't own the directory?

---

### Post by joberly on 2010-02-11
Correct. It may be easier to make a group of users allowing sftp, and adding users to that group instead of matching specific users. (Unless you only need this 1 user).

See here: [http://blogs.techrepublic.com.com/opensource/?p=229](http://blogs.techrepublic.com.com/opensource/?p=229)

---

### Post by SectorNine50 on 2010-02-11
> **joberly said:**
> Correct. It may be easier to make a group of users allowing sftp, and adding users to that group instead of matching specific users. (Unless you only need this 1 user).

See here: [http://blogs.techrepublic.com.com/opensource/?p=229](http://blogs.techrepublic.com.com/opensource/?p=229)
Ah-ha, that %h feature is pretty nice.  That was my one concern about groups was that I couldn't chroot them to their home unless they were specific users.  I'll give this a shot and let you know how it goes.

Thanks for your help!

---

