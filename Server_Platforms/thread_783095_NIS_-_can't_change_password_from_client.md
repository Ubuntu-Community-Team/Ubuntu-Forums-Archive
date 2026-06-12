---
title: "NIS - can't change password from client"
date: 2008-05-05
forum: Server Platforms
---

### Post by arizonagroovejet on 2008-05-05
I've set up a NIS server on a virtual machine running hardy just to get the experience of doing it. I've got another virtual machine I already had running SLED 10 SP1 as the client. The passwd and shadow files are in /var/yp on the server.

So far I've got authentication set up so I can log in to the client as a user I created on the server. I can't get password changing from the client to work though. If I log in to the client as the test user and try to change their password I get

```
nistest@linux-mniw:~> passwd
Changing password for nistest.
Old Password:
New Password:
Reenter New Password:
yppasswdd not running on NIS master mike-desktop
Error: Password NOT changed.
passwd: Authentication token manipulation error
nistest@linux-mniw:~>
```

However yppasswd is running on the server.

```
root@mike-desktop:/var/yp# rpcinfo -p localhost
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100004    2   udp    854  ypserv
    100004    1   udp    854  ypserv
    100004    2   tcp    855  ypserv
    100004    1   tcp    855  ypserv
    100009    1   udp    857  yppasswdd
 600100069    1   udp    860  fypxfrd
 600100069    1   tcp    861  fypxfrd
    100007    2   udp    866  ypbind
    100007    1   udp    866  ypbind
    100007    2   tcp    867  ypbind
    100007    1   tcp    867  ypbind
root@mike-desktop:/var/yp# ps aux | grep yppasswd
root      5769  0.0  0.1   2152   956 ?        S    17:35   0:00 /usr/sbin/rpc.y
ppasswdd -D /var/yp
root      5907  0.0  0.1   3012   776 pts/2    S+   18:28   0:00 grep yppasswd
root@mike-desktop:/var/yp#
```

Can't find anything useful in the logs. I've been on Google for about an hour and got nowhere. Anyone know why changing the password doesn't work?

---

