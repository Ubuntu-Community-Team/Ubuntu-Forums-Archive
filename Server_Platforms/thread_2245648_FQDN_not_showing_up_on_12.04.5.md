---
title: "FQDN not showing up on 12.04.5"
date: 2014-09-25
forum: Server Platforms
---

### Post by mike248 on 2014-09-25
I've tried a number of different combinations of /etc/hosts file and it never seems to work 

_**Info:**_
Hostname = UB1204
Domain = you234
TLD = .com
local IP = 192.168.1.200

```

[SIZE=3][FONT=arial]127.0.0.1           localhost.localdomain   localhost

192.168.1.200   UB1204.you234.com     UB1204[/FONT][/SIZE]

```[SIZE=3][FONT=arial]
or

[/FONT][/SIZE][SIZE=3][FONT=arial]```

127.0.0.1            localhost.localdomain   localhost
127.0.1.1            UB1204.you234.com       UB1204
192.168.1.200        UB1204.you234.com       UB1204

```


or

[/FONT][/SIZE]```
[SIZE=3][FONT=arial]
127.0.0.1                localhost
[/FONT][/SIZE]
[SIZE=3][FONT=arial]127.0.1.1                UB1204
[/FONT][/SIZE]
[SIZE=3][FONT=arial]192.168.1.200        UB1204.you234.com          UB1204[/FONT][/SIZE]


```

It doesn't matter what I do whenever I type "hostname -f" I only get UB1204, the same as when I type hostname.

This is what I get when I restart Apache:
[IMG]http://images.tuprox.com/fqdnissue.png[/IMG]

Also, my domain name is located on a hosted server but I want a subdomain to be this machine, located at my residence, so the domain would be something like "private.you234.com"  so if I were to add my hostname to the equation, it would be UB1204.private.you234.com  Is that what I should put in my hosts file?

---

### Post by TheFu on 2014-09-25
Try:```

sudo hostname private
sudo domainname you234.com
```

then make the /etc/hosts file have
x.x.x.x   private private.you234.com

Of course, some DNS server somewhere on the internet will need to know this too.

---

### Post by nerdtron on 2014-09-25
> It doesn't matter what I do whenever I type "hostname -f" I only get UB1204, the same as when I type hostname.

Did you do "service hostname restart"? Did you log-out/log-in for the changes to take effect? Or reboot perhaps?

---

