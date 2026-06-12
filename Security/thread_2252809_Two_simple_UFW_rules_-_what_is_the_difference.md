---
title: "Two simple UFW rules - what is the difference ?"
date: 2014-11-14
forum: Security
---

### Post by uncle-c on 2014-11-14
Rule 1 :

```
$ sudo ufw allow proto tcp from 192.168.1.1 to any port 443
$ sudo ufw status

To                         Action      From
--                         ------      ----
443/tcp                     ALLOW       192.168.1.1
```

Rule 2 :

```
$ sudo ufw allow proto tcp from 192.168.1.1 to 192.168.1.30 port 443
$ sudo ufw status

To                         Action      From
--                         ------      ----
192.168.1.30 443/tcp        ALLOW       192.168.1.1
```

Both rules allow access from 192.168.1.1 to port 443 of 192.168.1.30 so why use one and not the other ? Perhaps rule 2 is used in the event of the https server having two or more network interfaces ? Could someone kindly explain the difference. 

Thanks
uc

---

### Post by The Cog on 2014-11-14
I think you understand the difference. Rule 1 allows the connection to call any address. Rule 2 only allows it to call the one address. 

As for why choose one over the other, for a server with a known fixed address it probably doesn't make a practical difference. For computers with multiple addresses, it obviously does although why you might want to restrict it that way might be a little complicated. If you are using the computer as a router and forwarding packets then you might very well want to control   what can be connected to.

---

### Post by uncle-c on 2014-11-14
Many thanks for the swift reply. It was a silly thing which was bugging me !

cheers

---

