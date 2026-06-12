---
title: "/etc/hosts ignored"
date: 2012-02-07
forum: Server Platforms
---

### Post by awacs on 2012-02-07
# cat /etc/hosts
[...]
10.1.1.1        domain.example
[...]

# cat /etc/nsswitch.conf
passwd:         compat
group:          compat
shadow:         compat
hosts:          files dns
networks:       files
protocols:      db files
services:       db files
ethers:         db files
rpc:            db files
netgroup:       nis

# dig domain.example

; <<>> DiG 9.7.0-P1 <<>> domain.example
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 64739
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;domain.example.                        IN      A

[...]

What am I doing wrong? :confused:

Thanks!

---

### Post by papibe on 2012-02-07
AFAIK, 'dig' asks directly the DNS server. The rules set in nsswitch.conf are for applications that need to resolve an address.

Try how this other commands resolve that address:
```
ping domain.example

ssh -vvv domain.example

```
Hope it helps,
Regards.

---

### Post by awacs on 2012-02-07
More (useless?) info:
# cat /etc/host.conf
# The "order" line is only used by old versions of the C library.
order hosts,bind
multi on

# cat /etc/resolv.conf |grep -v "#"
#

---

### Post by awacs on 2012-02-07
> **papibe said:**
> AFAIK, 'dig' asks directly the DNS server. The rules set in nsswitch.conf are for applications that need to resolve an address.

Try how this other commands resolve that address:
```
ping domain.example

ssh -vvv domain.example

```
Hope it helps,
Regards.

Ah, thanks for that.

Is there no equivalent for 'dig' that tests the entire resolver? I just have to use ping to test? Interesting.

---

### Post by papibe on 2012-02-07
> **awacs said:**
> I just have to use ping to test?
'ping' resolves addresses just like a regular application, so it serves very well as a 'resolver test'.

'nslookup', 'dig' and 'host' ignore the nsswitch.conf rules and connect directly to the DNS servers.

Regards.

---

