---
title: "Server Static Netplan DNS Failure"
date: 2020-05-01
forum: Server Platforms
---

### Post by paintballer4lfe on 2020-05-01
So this happened out of the blue to my ubuntu network monitor server and I have no clue how to fix this and fiure out whats not working.

So some backstory:
The device is 18.04 up to date, static network config via netplan and apply works fine. nameserver is setup for the local DNS only. Nothing resolves on the server but every other server and client can use the DNS server just fine. I see nothing failing on the DNS server end and only generic outputs on the ubuntu server end.

nslookup:
```
nslookup
> server
Default server: 127.0.0.53
Address: 127.0.0.53#53

```

netplan config
```
Fileame: 01-netcfg.yaml
network:
        version: 2
        renderer: networkd
        ethernets:
                enp1s0:
                        dhcp4: no
                        addresses: [10.10.21.6/27]
                        gateway4: 10.10.21.1
                        nameservers:
                          addresses: [10.10.10.1]

```
Google ping output:
```
ping google.com
ping: google.com: Temporary failure in name resolution

```
nslookup
```
nslookup google.com
;; Got SERVFAIL reply from 10.10.10.1, trying next server
Server:         127.0.0.53
Address:        127.0.0.53#53

** server can't find google.com: SERVFAIL

```
ping to DNS server
```
ping 10.10.10.1
PING 10.10.10.1 (10.10.10.1) 56(84) bytes of data.
64 bytes from 10.10.10.1: icmp_seq=1 ttl=63 time=0.155 ms
64 bytes from 10.10.10.1: icmp_seq=2 ttl=63 time=0.223 ms

```

Netplan debug appl output
```
** (generate:17755): DEBUG: 13:06:54.243: Processing input file /etc/netplan/01-netcfg.yaml..
** (generate:17755): DEBUG: 13:06:54.243: starting new processing pass
** (generate:17755): DEBUG: 13:06:54.244: enp1s0: setting default backend to 1
** (generate:17755): DEBUG: 13:06:54.244: Configuration is valid
** (generate:17755): DEBUG: 13:06:54.244: Generating output files..
** (generate:17755): DEBUG: 13:06:54.244: NetworkManager: definition enp1s0 is not for us (backend 1)
DEBUG:netplan generated networkd configuration changed, restarting networkd
DEBUG:no netplan generated NM configuration exists
DEBUG:enp1s0 not found in {}
DEBUG:Merged config:
network:
  bonds: {}
  bridges: {}
  ethernets:
    enp1s0:
      addresses:
      - 10.10.21.6/27
      dhcp4: false
      gateway4: 10.10.21.1
      nameservers:
        addresses:
        - 10.10.10.1
  vlans: {}
  wifis: {}

DEBUG:Skipping non-physical interface: lo
DEBUG:device enp1s0 operstate is up, not changing
DEBUG:{}
DEBUG:netplan triggering .link rules for lo
DEBUG:netplan triggering .link rules for enp1s0

```

manual connections and pings to direct IP's work fine but I need the DNS resolving back working for updates and such. I'm not sure what else to show you from the server config but any help is greatly appreciated.

---

### Post by LHammonds on 2020-05-01
> **paintballer4lfe said:**
> nameserver is setup for the local DNS only.

> **paintballer4lfe said:**
> every other server and client can use the DNS server just fine.

> **paintballer4lfe said:**
> ```
ping google.com
ping: google.com: Temporary failure in name resolution
```


Is the nameserver for local addresses only?  If not, is the nameserver registered at your domain registrar?

Are the other clients that are working only have that server as their only DNS entry or do they have secondary entries such as 1.1.1.1 or 8.8.8.8?  It's good practice to have more than one name server as a backup.

LHammonds

---

