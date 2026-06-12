---
title: "svn connection problem"
date: 2007-12-03
forum: Server Platforms
---

### Post by mitjab on 2007-12-03
I use this howto
[http://www.blendedtechnologies.com/setting-up-subversion-on-ubuntu/11](http://www.blendedtechnologies.com/setting-up-subversion-on-ubuntu/11)

but when i try to connect to my svn connection is refused. I search but i can not find any solution.

I try with
svn://192.168.123.171:3690/projekti/TERRAMAR

any idea why?

Thx

---

### Post by pwaldo on 2007-12-05
Do you have an SVN server running at that address?  You can use telnet to see if the host and port is reachable, like this:

```
$ telnet anonsvn.kde.org 3690
Trying 138.246.255.177...
Connected to anonsvn.kde.org.
Escape character is '^]'.
( success ( 1 2 ( ANONYMOUS ) ( edit-pipeline svndiff1 absent-entries ) ) ) ^]

```
Hit Ctrl-] to get back to the telnet prompt and type quit.

You will probably get something like this:
```
$ telnet 192.168.123.171 3690
Trying 192.168.123.171...
telnet: Unable to connect to remote host: Connection timed out

```

If this is what you get, there is no server running at that address.  HTH!

---

