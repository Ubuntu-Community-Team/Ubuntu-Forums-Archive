---
title: "Trouble with defining nameservers with static ip and a proxy."
date: 2013-05-10
forum: Server Platforms
---

### Post by sesstreets on 2013-05-10
I have an ubuntu server using Ubuntu 12.04.2 LTS setup at my job, for one day I was able to ping TLD's and use apt-get to update the packages/install samba/take over the world. During setup I entered the proxy information for my work, and I was able to install openssh and samba soon after it booted up. However, after I tried setting a static ip address my box can no longer resolve any domain name regardless of it being local or out of network. Here are some pieces of info:

Ping google.com
```
dude@FileServer02:~$ ping google.com
ping: unknown host google.com
```

Ping google name server
```
dude@FileServer02:~$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_req=1 ttl=46 time=10.7 ms
64 bytes from 8.8.8.8: icmp_req=2 ttl=46 time=10.0 ms
64 bytes from 8.8.8.8: icmp_req=3 ttl=46 time=16.5 ms
64 bytes from 8.8.8.8: icmp_req=4 ttl=46 time=10.8 ms
```

/etc/network/interfaces
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address x.x.x.x
netmask x.x.x.x
network x.x.x.x
broadcast x.x.x.x
gateway x.x.x.x
dns-nameserver x.x.x.x
search example.org
```

I don't think the proxy comes into play but where should I be defining it?

Can anyone help?

---

### Post by SeijiSensei on 2013-05-10
The "dns-nameserver**s**" parameter is misspelled; it needs a final "s".

---

### Post by sesstreets on 2013-05-10
...trying now :(

EDIT: Dear lord... Thank you :popcorn:

---

