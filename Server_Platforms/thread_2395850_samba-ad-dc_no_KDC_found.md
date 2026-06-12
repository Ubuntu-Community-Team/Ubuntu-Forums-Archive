---
title: "samba-ad-dc no KDC found"
date: 2018-07-07
forum: Server Platforms
---

### Post by rsteinmetz70112 on 2018-07-07
I'm setting up a new Samba Active Director Domain Controller and I seem to have done something to the kerberos, since I can't contact the KDC.

I've never set one of these up before so I'd appreciate some tips on how to fix it. I'm using the build in DNS, and that seems to be working.

Is it possible to simply re-provision the domain to fix this?

```

#kinit adminisrtator@ORLEANS
kinit: Cannot find KDC for realm "ORLEANS" while getting initial credentials
```

```
$ kinit administrator
kinit: Cannot find KDC for realm "ORLEANS.STEINMETZNET.COM" while getting initial credentials
```

```
$ klist
klist: No credentials cache found (filename: /tmp/krb5cc_1000)
```

```
$ host -t SRV _kerberos._udp.orleans.steinmetznet.com.
Host _kerberos._udp.orleans.steinmetznet.com. not found: 3(NXDOMAIN)
```

Checking further the domain seems provisioned:

```
# samba-tool domain level show
Domain and forest function level for domain 'DC=orleans,DC=steinmetznet,DC=com'

Forest function level: (Windows) 2008 R2
Domain function level: (Windows) 2008 R2
Lowest function level of a DC: (Windows) 2008 R2
```
```

running a series of pings with mixed results
[CODE]root@hamlet:~# ping -c3 steinmetznet.com
PING steinmetznet.com (69.197.18.174) 56(84) bytes of data.
^C
--- steinmetznet.com ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2045ms

root@hamlet:~# ping -c3 hamlet.steinmetznet.com
PING hamlet.steinmetznet.com (192.168.1.1) 56(84) bytes of data.
64 bytes from hamlet.steinmetznet.com (192.168.1.1): icmp_seq=1 ttl=64 time=0.069 ms
64 bytes from hamlet.steinmetznet.com (192.168.1.1): icmp_seq=2 ttl=64 time=0.050 ms
64 bytes from hamlet.steinmetznet.com (192.168.1.1): icmp_seq=3 ttl=64 time=0.050 ms

--- hamlet.steinmetznet.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2048ms
rtt min/avg/max/mdev = 0.050/0.056/0.069/0.010 ms
root@hamlet:~# ping -c3 hamlet
PING hamlet.attlocal.net (127.0.1.1) 56(84) bytes of data.
64 bytes from hamlet.attlocal.net (127.0.1.1): icmp_seq=1 ttl=64 time=0.069 ms
64 bytes from hamlet.attlocal.net (127.0.1.1): icmp_seq=2 ttl=64 time=0.050 ms
64 bytes from hamlet.attlocal.net (127.0.1.1): icmp_seq=3 ttl=64 time=0.050 ms

--- hamlet.attlocal.net ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2037ms
rtt min/avg/max/mdev = 0.050/0.056/0.069/0.010 ms
root@hamlet:~# host -t A steinmetznet.com
series of ping and host tests with mixed results:

PING steinmetznet.com (69.197.18.174) 56(84) bytes of data.
^C
--- steinmetznet.com ping statistics ---
6 packets transmitted, 0 received, 100% packet loss, time 5101ms

root@hamlet:~# ping -c3 steinmetznet.com
PING steinmetznet.com (69.197.18.174) 56(84) bytes of data.
^C
--- steinmetznet.com ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2045ms

root@hamlet:~# ping -c3 hamlet.steinmetznet.com
PING hamlet.steinmetznet.com (192.168.1.1) 56(84) bytes of data.
64 bytes from hamlet.steinmetznet.com (192.168.1.1): icmp_seq=1 ttl=64 time=0.069 ms
64 bytes from hamlet.steinmetznet.com (192.168.1.1): icmp_seq=2 ttl=64 time=0.050 ms
64 bytes from hamlet.steinmetznet.com (192.168.1.1): icmp_seq=3 ttl=64 time=0.050 ms

--- hamlet.steinmetznet.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2048ms
rtt min/avg/max/mdev = 0.050/0.056/0.069/0.010 ms
root@hamlet:~# ping -c3 hamlet
PING hamlet.attlocal.net (127.0.1.1) 56(84) bytes of data.
64 bytes from hamlet.attlocal.net (127.0.1.1): icmp_seq=1 ttl=64 time=0.069 ms
64 bytes from hamlet.attlocal.net (127.0.1.1): icmp_seq=2 ttl=64 time=0.050 ms
64 bytes from hamlet.attlocal.net (127.0.1.1): icmp_seq=3 ttl=64 time=0.050 ms

--- hamlet.attlocal.net ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2037ms
rtt min/avg/max/mdev = 0.050/0.056/0.069/0.010 ms
root@hamlet:~# host -t A steinmetznet.com
```

---

