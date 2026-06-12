---
title: "Vm unable to connect server on domain running https://"
date: 2012-01-30
forum: Server Platforms
---

### Post by satimis on 2012-01-30
Hi all,

server1 vm ubuntu1010 64bit
vm ubuntu1004 desktop 64bit
host ubuntu1104 desktop 64bit
Orcle VirtualBox

vm unable to connect server on domain.

On vm browser
[https://server1.domain.com/webmail/](https://server1.domain.com/webmail/)
Secure Connection Failed```

An error occurred during a connection to server1.domain.com.
SSL received a record that exceeded the maximum permissible length.
(Error code: ssl_error_rx_record_too_long)

```

[http://server1.domain.com/webmail/](http://server1.domain.com/webmail/)
works w/o problem

On vm terminal
$ dig server1.domain.com```


; <<>> DiG 9.7.0-P1 <<>> ub1010ser01.satimis.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 51972
;; flags: qr aa rd; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 1
;; WARNING: recursion requested but not available

;; QUESTION SECTION:
;server1.domain.com.	IN	A

;; ANSWER SECTION:
server1.domain.com. 3600	IN	A	192.168.0.203

;; AUTHORITY SECTION:
server1.domain.com. 3600	IN	NS	ns.server1.domain.com.

;; ADDITIONAL SECTION:
ns.server1.domain.com. 3600 IN	A	192.168.0.203

;; Query time: 0 msec
;; SERVER: 192.168.0.203#53(192.168.0.203)
;; WHEN: Mon Jan 30 13:54:10 2012
;; MSG SIZE  rcvd: 90

```

Please help.  TIA

B.R.
satimis

---

### Post by littlepitt on 2012-01-30
I don't think your problem is a DNS problem...
Does the VM have the same configuration as the real machine?
Is the web browser the same version? The SSL packages?

---

