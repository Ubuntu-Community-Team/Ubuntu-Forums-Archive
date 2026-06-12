---
title: "dansguardian vs squid"
date: 2014-09-10
forum: Security
---

### Post by hohoangluan on 2014-09-10
Hi there.
    I'm newbie. I'm working with dansguardian vs squid transparent but in my system just only work on 1 in 2 server, not both.
```

$IPT -t nat -A PREROUTING -i $LAN_IF -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 3128
$IPT -t nat -A PREROUTING -p tcp -m tcp --dport 80 -s 172.22.0.0/24 -j DNAT --to-destination 172.22.0.2:8080[

```
1. When i use that script only squid work can not filter porn site 

```

$IPT -t nat -A PREROUTING -p tcp -m tcp --dport 80 -s 172.22.0.0/24 -j DNAT --to-destination 172.22.0.2:8080
$IPT -t nat -A PREROUTING -i $LAN_IF -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 3128

```
2. When i use that script only dansguardian can filter porn site but rules on squid does not work

My configugration in below
1. Squid
```

http_port 3128 transparent

```
2. Dansguardian
```

filterip = 
filterport = 8080
proxyip = 127.0.0.1
proxyport = 3128
```

---

