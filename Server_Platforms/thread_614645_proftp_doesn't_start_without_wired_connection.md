---
title: "proftp doesn't start without wired connection"
date: 2007-11-16
forum: Server Platforms
---

### Post by Kulgan on 2007-11-16
I have installed proftp, and have it working well when a wired connection is active. However, when I have either no or a wireless connection, starting the server results in: 

```
/etc/init.d/proftpd start
 * Starting ftp server proftpd                                                   
 - IPv4 getaddrinfo 'manetheren' error: No address associated with hostname
 - warning: unable to determine IP address of 'manetheren'
 - error: no valid servers configured
 - Fatal: error processing configuration file '/etc/proftpd/proftpd.conf'
```
"manetheren" is my hostname. 

And connecting of course doesn't work...
```
ftp 127.0.0.1
ftp: connect: Connection refused
ftp>
```

Everything works when I have a wired internet connection, and I can't see anything in the configuration that would influence this. 

Any ideas?
-K

---

