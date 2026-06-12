---
title: "Could not update repositories"
date: 2006-12-04
forum: Repositories &amp; Backports
---

### Post by ivuntu on 2006-12-04
Hi,

I've read a few threads that have a similar problem, but I get a different error message when I try to do a software/dis update. I tried different http addresses (us localization), but I get the same error message. It might have something to do with the router, but I don't know how to check that.

Any suggestions are most welcome! Thanks!

This is what I get:

```

ivo@ubuntu:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
Writing extended state information... Done
Err http://security.ubuntu.com dapper-security Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com dapper-updates Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com dapper Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Reading package lists... Done

```

---

### Post by RJARRRPCGP on 2006-12-04
Unload Firestarter.

---

### Post by ivuntu on 2006-12-05
Thanks for replying,

unloading Firestarter does not help :( (I tried stopping the Firestarter and killing the service entirely).

Is there something else that could be blocking? (Internet connection etc. is working normally.)

---

### Post by ivuntu on 2006-12-06
I got another idea: the error message seems to suggest that it does not connect via the normal internet connection (eth0) but via the loopback (lo), which of course doesn't work. 

How can I change this???

---

### Post by ivuntu on 2006-12-07
Hi,

I finally know what is wrong: it was a program called anon-proxy! see other threads that discuss this!

---

