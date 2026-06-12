---
title: "Configuing firehol fo rssh..."
date: 2006-12-30
forum: Ubuntu Christian Edition
---

### Post by jlc on 2006-12-30
In case anyone finds firehol a tad confusing and need some sshd going on, do this... :)

```

$ sudo /usr/sbin/firehol-wizard >/tmp/firehol.conf
$ vi /tmp/firehld.conf

```

For your interfaces, add  server ssh accept

You will see a section for example on my laptop it has eth0 and eth1 so I added it to the list for eth1 (wireless)

```

# Here are the services listening on eth1.
        # TODO: Normally, you will have to remove those not needed.
        client dhcp accept
        server ICMP accept
        server ntp accept
        server squid accept
        server webcache accept
        server ssh accept

```


Copy it over to /etc/firehol

```

$ sudo cp /tmp/firehol.conf /etc/firehol/

```

Then restart the service

```

$ sudo /etc/init.d/firehol restart
Restarting iptables firewall: FireHOL ...done.

```

---

### Post by jlc on 2006-12-30
Just an example of before and after

Before (BAD)

```

justin@echelon:~$ sudo nmap-sS 192.168.1.105
Starting Nmap 4.10 ( http://www.insecure.org/nmap/ ) at 2006-12-30 14:31 CST
All 1679 scanned ports on 192.168.1.105 are filtered
MAC Address: 00:18:DE:71:0E:D1 (Unknown)

Nmap finished: 1 IP address (1 host up) scanned in 134.761 seconds



```

After (GOOD)

```

justin@echelon:~$ sudo nmap -sS 192.168.1.105

Starting Nmap 4.10 ( http://www.insecure.org/nmap/ ) at 2006-12-30 14:29 CST
Interesting ports on 192.168.1.105:
Not shown: 1675 filtered ports
PORT     STATE  SERVICE
22/tcp   open   ssh
123/tcp  closed ntp
3128/tcp open   squid-http
8080/tcp open   http-proxy
MAC Address: 00:18:DE:71:0E:D1 (Unknown)

Nmap finished: 1 IP address (1 host up) scanned in 32.711 seconds

```

---

