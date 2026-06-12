---
title: "Last Logs Reset?"
date: 2012-08-15
forum: Security
---

### Post by Tamalin on 2012-08-15
So, I logged into my server today and ran the last command, which promptly informed me that the only login on record was my current SSH session.  Is there some mechanism by which the login history can be reset automatically?  To my knowledge, I have never done so, and I am the only user on the machine.

---

### Post by CharlesA on 2012-08-15
I do not believe it can reset unless you removed [/var/log/wtmp]("http://unixhelp.ed.ac.uk/CGI/man-cgi?last")

Please see this page:

[https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned](https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned)

I just checked my server and I had an archived wtmp file:

```
charles@Thor:~$ ls -l /var/log/wtmp*
-rw-rw-r-- 1 root utmp 38784 Aug 15 16:44 /var/log/wtmp
-rw-rw-r-- 1 root utmp 52992 Jul 31 07:53 /var/log/wtmp.1

```

I don't think you got owned, but it is a good idea to check to make sure.

---

### Post by uRock on 2012-08-15
I think /var/log/auth.log shows logins.

UFW can be configured to log ssh connections, though I am not sure if it would show the username. It will show the IP address of such connections.

---

### Post by CharlesA on 2012-08-15
Yep the auth.log shows all login attempts. ;)

---

### Post by Tamalin on 2012-08-27
Thanks, you were right.  I found it in wtmp.1.  The machine was turned off for about a month while I was on vacation, so it must I booted it up.
Does anyone know why, even though I have logged in multiple times recently, lastlog still lists "never logged in" for all users, even though login records are listed in wtmp?  It seems to reset with every reboot.

---

### Post by CharlesA on 2012-08-27
You might want to run a fsck to make sure the file system is ok.

It should show all successful logins, and it is isn;t and a fsck doesn't fix it, I would reinstall the box just to be safe.

---

