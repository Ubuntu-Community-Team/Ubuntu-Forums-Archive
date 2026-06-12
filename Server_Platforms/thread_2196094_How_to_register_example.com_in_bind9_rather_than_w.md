---
title: "How to register example.com in bind9 rather than www.example.com"
date: 2013-12-27
forum: Server Platforms
---

### Post by dbillingsjr on 2013-12-27
I have a website with bind9 configured as the nameserver.  I can reach the site via [www.example.com]("http://www.example.com"), but nothing I try seems to work to allow it to be reached as example.com (without the www IE: for email, ssh, and other applications where [EMAIL="user@www.example.com"]user@www.example.com[/EMAIL] looks really funny)


I'm sure there's numerous problems with my config, as I'm pretty new to setting up a nameserver, but my db file (changed to example.com for simplicity, assume I own example.com) looks like this.  In addition to example.com not linking to my IP, there's some sort of problem with my mail server in general as it's not properly accepting my user credentials... But that's another question.
```

$TTL    604800
@    IN    SOA    example.com. root.example.com    (
                 2        ; Serial
            604800        ; Refresh
            86400        ; Retry
            2419200        ; Expire
            604800 )    ; Negative Cache TTL
@        IN    NS    ns.example.com.
@        IN    A    192.168.100.25
@        IN    AAAA    ::1
ns1      IN    A    1.1.100.25
ns2      IN    A    1.1.100.26
www      IN    A    1.1.100.25
         IN    A    1.1.100.25
mail     IN    A    1.1.100.25
         IN    MX 10    mail.example.com.

```

---

### Post by clearski on 2013-12-28
You can try this:


```
$TTL    604800
example.com.    IN    SOA    ns root (
                 3        ; Serial
            604800        ; Refresh
            86400        ; Retry
            2419200        ; Expire
            604800 )    ; Negative Cache TTL


        IN    NS    ns.example.com.
        IN    NS    ns1.example.com.
        IN    NS    ns2.example.com.

        IN    MX    10    mail.example.com.

        IN    A    1.1.100.25

ns        IN    A    192.168.100.25
ns1        IN    A    1.1.100.25
ns2        IN    A    1.1.100.26

mail        IN    A    1.1.100.25

www        IN    CNAME    ns1.example.com.
```

---

### Post by dbillingsjr on 2013-12-28
I put that change up, just waiting on caches to update to find out if it worked or not.   (dig still shows the previous serial number)

---

### Post by Doug S on 2013-12-28
Your file is almost right, missing a period at the end of the SOA line and your NS line tries to declare a non-existent name server. clearski's solution declares the non-existent name server, which is maybe what you want, or try this:```
doug@doug-64:~/config/bind/temph$ cat db.ex
$TTL    604800
@       IN      SOA     example.com. [COLOR=#ff0000]root.example.com.[/COLOR] (
                3               ; Serial
                604800          ; Refresh
                86400           ; Retry
                2419200         ; Expire
                604800 )        ; Negative Cache TTL
        IN      A       1.1.100.25
;
[COLOR=#ff0000]@       IN      NS      ns1.example.com.[/COLOR]
@       IN      A       192.168.100.25
@       IN      AAAA    ::1
ns1     IN      A       1.1.100.25
ns2     IN      A       1.1.100.26
www     IN      A       1.1.100.25
mail    IN      A       1.1.100.25
        IN      MX 10   mail.example.com.
```also use named-checkzone to test your file:```
doug@doug-64:~/config/bind/temph$ named-checkzone example.com db.ex
zone example.com/IN: loaded serial 3
OK
doug@doug-64:~/config/bind/temph$
```

---

