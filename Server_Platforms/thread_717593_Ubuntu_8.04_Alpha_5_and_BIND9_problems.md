---
title: "Ubuntu 8.04 Alpha 5 and BIND9 problems"
date: 2008-03-07
forum: Server Platforms
---

### Post by TheR on 2008-03-07
It might even be a bug.

I am trying to set bind9 as slave server, but I get this strange errors in messages log file.

Mar  7 13:55:01 ns2 kernel: [ 2924.895538] audit(1204894501.723:566): operation="inode_create" request_mask="w::" denied_mask="w::" name="/var/cache/bind/slave/tmp-f0wPIyvu2J" pid=4299 profile="/usr/sbin/named" namespace="default"

and in daemon.log file

Mar  7 13:55:01 ns2 named[4298]: zone myzone.com/IN: Transfer started.
Mar  7 13:55:01 ns2 named[4298]: transfer of 'myzone.com/IN' from 199.199.199.199#
53: connected using 199.199.199.199#46433
Mar  7 13:55:01 ns2 named[4298]: dumping master file: slave/tmp-f0wPIyvu2J: open: permission denied
Mar  7 13:55:01 ns2 named[4298]: transfer of 'myzone.com/IN' from 199.199.199.199#53: failed while receiving responses: permission denied
Mar  7 13:55:01 ns2 named[4298]: transfer of 'myzone.com/IN' from 199.199.199.199#53: end of transfer

I have tried a lot and my permisions are currently set as:
drwxrwxr-x 2 bind bind 4096 2008-03-07 12:57 slave


Help please.


by
TheR

---

### Post by jmprince80 on 2008-03-24
i solved this issue by removing the bind9 package and installing the bind 9.5.0 from source

good luck....

nothing worse than your DNS being down!

---

### Post by junke on 2008-06-05
I had exactly the same problem with Ubuntu 8.04. On Debian 3.0r3 the same configuration worked.
I used "ls -ld /etc/bind/slave/" or "lsattr -d /etc/bind/slave/" to check the permissions on the destination directory, but I didn't found any problems.
It looks like [AppArmor]("https://help.ubuntu.com/community/AppArmor") is preventing bind to save that file to the destination directory.
Simply omit the path and it will work.
```
zone "example.com" {
  type slave;
  masters { 192.168.1.1; };
  file "db.example.com";
};
```
This will save the zone file to /var/cache/bind/db.example.com

---

### Post by bstadil on 2008-07-15
I can confirm that removing the absolute path ie the /etc/bind/ suffix solves the problem. 

It must be something other than Appamor since I do not have this installed. 

Thanks so much I wasted 3 hours trying to solve this.

---

