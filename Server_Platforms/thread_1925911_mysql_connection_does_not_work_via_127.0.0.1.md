---
title: "mysql connection does not work via 127.0.0.1"
date: 2012-02-15
forum: Server Platforms
---

### Post by sohmc on 2012-02-15
My postfix connection is reporting an error this morning:
```
Feb 15 09:33:23 helo postfix/cleanup[45022]: warning: connect to mysql server 127.0.0.1: Can't connect to MySQL server on '127.0.0.1' (110)
```

When I try to connect to MySQL manually, it seems to work so long as I don't specify a host.  But when I do specify the localhost, it cannot connect.  It just times out.

The odd thing is that this works:
```
mysql -u postfix_user -p -h localhost 
```

But this does not:
```
mysql -u postfix_user -p -h 127.0.0.1 
```

I checked my /etc/hosts file and localhost does resolve to 127.0.0.1 so those two commands should work exactly the same.

No errors are shown in the syslog or the mysql logs.

A number of different google searches seem to suggest checking the firewall settings.  Outside of iptables, I don't have anything else installed (at least that I know of).

Can anyone offer a clue?

Thanks!

---

### Post by sohmc on 2012-02-15
I was able to fix this by changing the smtp/smtps chroot status to "no" in the master.cf.

Not sure what changed between reboots to make this not work.  But it's working now.

Posting here for posterity.

---

