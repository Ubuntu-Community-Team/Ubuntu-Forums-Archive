---
title: "Webpages not working without login"
date: 2009-09-28
forum: Server Platforms
---

### Post by Mainlake on 2009-09-28
Hi,

my issue is following:

I have ubuntu 9.04 server running with apache etc. Everything works as planned (webpages show normally) when I'm logged in to server via ssh. But when I'm not logged in to server I (and everybody else) get a 403 error :confused:

What could be the problem here?

---

### Post by cdenley on 2009-09-28
I can't imagine how you being logged in could affect it unless you are serving files from a filesystem which is only mounted or decrypted when you login. What does the log say the problem is?
```

tail /var/log/apache2/error.log

```

---

### Post by Mainlake on 2009-09-29
Hi,

I get something like this:

```
tuomas@KotiUbuntu:~$ tail /var/log/apache2/error.log
[Mon Sep 28 21:48:19 2009] [error] [client 192.168.0.100] (13)Permission denied: access to /~tuomas/soile/ denied
[Mon Sep 28 21:59:52 2009] [error] [client 192.168.0.254] (13)Permission denied: access to / denied
[Mon Sep 28 22:21:54 2009] [error] [client 192.168.0.254] (13)Permission denied: access to / denied
[Tue Sep 29 07:57:36 2009] [error] [client 192.168.0.100] (13)Permission denied: access to /~tuomas/soile/ denied
[Tue Sep 29 07:57:43 2009] [error] [client 192.168.0.100] (13)Permission denied: access to /favicon.ico denied
[Tue Sep 29 07:57:46 2009] [error] [client 192.168.0.100] (13)Permission denied: access to /favicon.ico denied
[Tue Sep 29 07:57:49 2009] [error] [client 192.168.0.254] (13)Permission denied: access to / denied
[Tue Sep 29 07:57:54 2009] [error] [client 192.168.0.254] (13)Permission denied: access to /favicon.ico denied
[Tue Sep 29 07:57:58 2009] [error] [client 192.168.0.254] (13)Permission denied: access to /favicon.ico denied
[Tue Sep 29 08:40:18 2009] [error] [client 193.200.150.152] (13)Permission denied: access to / denied
```

---

### Post by cdenley on 2009-09-29
What are those paths on your local filesystem? In other words, what is your DocumentRoot? What are the permissions on those files/directories, as well as the parent directories? Since you seem to think it only happens when your user isn't logged in, you may want to create a second user and check permissions as that user while apache is broken. Post your site configuration.

Are you using encryption or anything related to your user account where the documents you're serving are located?

---

### Post by Mainlake on 2009-09-30
> **cdenley said:**
> What are those paths on your local filesystem? In other words, what is your DocumentRoot? What are the permissions on those files/directories, as well as the parent directories? Since you seem to think it only happens when your user isn't logged in, you may want to create a second user and check permissions as that user while apache is broken. Post your site configuration.

Are you using encryption or anything related to your user account where the documents you're serving are located?

Hi, and thank you for your help.
I've found the root cause of my problem which was wrong apache config. I.e. the DocumentRoot was wrong.
I'll try to configure the apache again, and if I have some more trouble I'll return.

---

