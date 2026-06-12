---
title: "Dapper gateway server, frequent DNS timeouts"
date: 2008-08-06
forum: Server Platforms
---

### Post by dmizer on 2008-08-06
I've been having DNS problems with my Dapper server. I keep getting timeouts locally, and through my SSH/socks proxy tunnel.

The server is not a DNS server, it's just a file server which I also use for ssh, proxy, and ddclient update.

I'm configured for openDNS servers which have always been speedy and trouble free for me.

```
$ cat /etc/dhcp3/dhclient.conf | grep prepend
prepend domain-name-servers 208.67.222.222,208.67.220.220;
```

```
$ cat /etc/resolv.conf
nameserver 208.67.222.222
nameserver 208.67.220.220
nameserver 192.168.0.1
```

No iptables rules in place.

My daemon log shows that the ddclient is regularly timing out.
```
Aug  7 07:43:09 localhost ddclient[15446]: WARNING:  cannot connect to checkip.dyndns.org:80 socket: IO::Socket::INET:connect: Connection timed out
```

Other computers on the network don't have any trouble unless I proxy through the Dapper server.

---

