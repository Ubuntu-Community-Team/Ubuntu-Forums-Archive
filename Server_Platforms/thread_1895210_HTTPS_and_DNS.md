---
title: "HTTPS and DNS ?"
date: 2011-12-14
forum: Server Platforms
---

### Post by s.hijazi on 2011-12-14
Dear all friends.

i have a projet to create a HTTPS & DNS server , i finish from my https projet , i need to make my server as a dns for customer can be enter to [https://www.mysite.com](https://www.mysite.com) (only an example)

my steps in DNS are :
```

sudo apt-get install bind9
sudo gedit /etc/bind/named.conf.local
zone "mysite.com" {
        type master;
        file "/etc/bind/zones/db.mysite.com";
        };
sudo cp /etc/bind/db.local /etc/bind/db.mysite.com

```and i change in db.mysite.com to this :
```

$TTL    604800
@    IN    SOA    ubuntu.mysite.com. ubuntu.mysite.com. (
                  1        ; Serial
             604800        ; Refresh
              86400        ; Retry
            2419200        ; Expire
             604800 )    ; Negative Cache TTL
;
@    IN    NS    ubuntu.mysite.com.
www     IN      A       192.168.1.10
ns    IN    A    192.168.1.10
box     IN        A    192.168.1.10

sudo /etc/init.d/bind9 restart
sudo gedit /etc/resolv.conf

domain localdomain
search mysite.coom
nameserver 192.168.1.10


```

my questions are :
1.this code are correct ? i think i have error in resolv.conf & in db.mysite.com
2.i do this step named-checkzone mysite.com /etc/bind/zones/mysite.com.db
terminal says 
zone mysite.com/IN: has no NS records
zone mysite.com/IN: not loaded due to errors.
what i must to do ? 
thank you :) :)

---

### Post by s.hijazi on 2011-12-14
My ubuntu version is 11.04 :)

---

### Post by jonobr on 2011-12-14
Hey , most people go between forums so Id recommend against opening [multiple threads.]("http://ubuntuforums.org/showthread.php?t=1895215")

They are usually closed by mods for duplication.

---

### Post by DaveyG on 2011-12-14
I would recommend taking a look at [this thread]("http://ubuntuforums.org/showthread.php?t=236093").

---

