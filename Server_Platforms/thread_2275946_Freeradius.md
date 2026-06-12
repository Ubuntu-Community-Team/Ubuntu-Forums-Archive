---
title: "Freeradius"
date: 2015-04-29
forum: Server Platforms
---

### Post by j3r3my2 on 2015-04-29
Hi everyone,
I have a freeradius server for auth my user on the wifi with coova chilli. I am using a db mysql.
It's working , my user can login and i can do ```
echo "User-Name='mysqltest',User-Password='testsecret'" | radclient -c '1' -n '3' -r '3' -t '3' -x '10.10.4.254:1812' 'auth' 'MynasSecret' 2>&1
Sending Access-Request of id 153 to 10.10.4.254 port 1812
    User-Name = "mysqltest"
    User-Password = "testsecret"
rad_recv: Access-Accept packet from host 10.10.4.254 port 1812, id=153, length=20


```

But when i try to logout one user i got this

```
echo "User-Name='mysqltest',User-Password='testsecret'" | radclient -c '1' -n '3' -r '3' -t '3' -x '10.10.4.254:1812' 'disconnect' 'MynasSecret' 2>&1
Sending Disconnect-Request of id 208 to 10.10.4.254 port 1812
    User-Name = "mysqltest"
    User-Password = "testsecret"
Sending Disconnect-Request of id 208 to 10.10.4.254 port 1812
    User-Name = "mysqltest"
    User-Password = "testsecret"
Sending Disconnect-Request of id 208 to 10.10.4.254 port 1812
    User-Name = "mysqltest"
    User-Password = "testsecret"
radclient: no response from server for ID 208 socket 3


```

Someone has a clue, why the disconnect fonction is not working ?

---

