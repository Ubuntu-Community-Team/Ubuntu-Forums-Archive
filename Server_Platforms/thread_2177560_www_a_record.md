---
title: "www a record"
date: 2013-09-29
forum: Server Platforms
---

### Post by Bondar_Mircea on 2013-09-29
Why [www.beestudio.ro](www.beestudio.ro) not? beestudio.ro work. I added www cname to my zone but not working. When enter the dig [www.beestudio.ro](www.beestudio.ro) the output is:

```

; <<>> DiG 9.8.4-rpz2+rl005.12-P1 <<>> www.beestudio.ro
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 63686
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 0


;; QUESTION SECTION:
;www.beestudio.ro.              IN      A


;; ANSWER SECTION:
www.beestudio.ro.       19663   IN      CNAME   beestudio.ro.beestudio.ro.


;; AUTHORITY SECTION:
beestudio.ro.           3022    IN      SOA     ns1.beestudio.ro. admin.beestudio.ro. 2013092908 10800 3600 604800 38400


;; Query time: 12 msec
;; SERVER: 192.168.0.1#53(192.168.0.1)
;; WHEN: Sun Sep 29 15:11:25 2013
;; MSG SIZE  rcvd: 107

```
Why [www.beestudio.ro](www.beestudio.ro) is cname for  beestudio.ro.beestudio.ro.

My zone is:

```

$ttl 38400
@	IN	SOA	ns1.beestudio.ro. admin.beestudio.ro. (
			2013092924
			10800
			3600
			604800
			38400 )
@	IN	NS	ns1.beestudio.ro.
@	IN	NS	ns2.beestudio.ro.
beestudio.ro.	IN	MX	10 mail.beestudio.ro.
beestudio.ro.	IN	A	5.12.101.175
ns1	IN	A	5.12.101.175
ns2	IN	A	5.12.101.175
mail	IN	A	5.12.101.175
www	IN	CNAME	beestudio.ro.

```

---

### Post by sanderj on 2013-09-29
... and beestudio.ro.beestudio.ro. does not exist ...


```
$ host beestudio.ro.beestudio.ro
Host beestudio.ro.beestudio.ro not found: 3(NXDOMAIN)
```


Furthermore, you have another entry for www, which results in:

```
$ host www.beestudio.ro
www.beestudio.ro is an alias for beestudio.ro.
beestudio.ro has address 5.12.101.175
beestudio.ro mail is handled by 10 mail.beestudio.ro.
```

which works:

```
$ wget www.beestudio.ro -O /dev/null
--2013-09-29 15:57:12--  http://www.beestudio.ro/
Resolving www.beestudio.ro (www.beestudio.ro)... 5.12.101.175
Connecting to www.beestudio.ro (www.beestudio.ro)|5.12.101.175|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 12 [text/html]
Saving to: ‘/dev/null’

100%[=====================================================================================================>] 12          --.-K/s   in 0s      

2013-09-29 15:57:12 (2,19 MB/s) - ‘/dev/null’ saved [12/12]
```

---

### Post by Bondar_Mircea on 2013-09-29
How to slve this? I created dns zone with webmin

---

### Post by sanderj on 2013-09-29
remove the line "www.beestudio.ro.       19663   IN      CNAME   beestudio.ro.beestudio.ro."

---

### Post by Doug S on 2013-09-29
Change this line:```
@    IN    SOA    ns1.beestudio.ro. admin.beestudio.ro. (
```To this:```
@    IN    SOA beestudio.ro. admin.beestudio.ro. (
```and give add line with an ip address. Also no need to use a CNAME record at all:```
$ttl 38400
@    IN    SOA    beestudio.ro. admin.beestudio.ro. (
            2013092925
            10800
            3600
            604800
            38400 )
    IN    A    5.12.101.175
;
@    IN    NS    ns1.beestudio.ro.
@    IN    NS    ns2.beestudio.ro.
beestudio.ro.    IN    MX    10 mail.beestudio.ro.
ns1    IN    A    5.12.101.175
ns2    IN    A    5.12.101.175
mail    IN    A    5.12.101.175
www    IN    A    5.12.101.175
```

---

### Post by Bondar_Mircea on 2013-09-29
that line does not exist in my zone file. I removed www in cname beestudio.ro.. But show same cname (www in cname beestudio.ro.beestudio.ro.)

---

### Post by sandyd on 2013-09-29
> **Bondar_Mircea said:**
> that line does not exist in my zone file. I removed www in cname beestudio.ro.. But show same cname (www in cname beestudio.ro.beestudio.ro.)

Can you post your current zonefile

---

### Post by Bondar_Mircea on 2013-09-29
$ttl 38400
@	IN	SOA	ns1.beestudio.ro. admin.beestudio.ro. (
			2013092925
			10800
			3600
			604800
			38400 )
@	IN	NS	ns1.beestudio.ro.
@	IN	NS	ns2.beestudio.ro.
beestudio.ro.	IN	MX	10 mail.beestudio.ro.
beestudio.ro.	IN	A	5.12.101.175
ns1	IN	A	5.12.101.175
ns2	IN	A	5.12.101.175
mail	IN	A	5.12.101.175

---

### Post by sandyd on 2013-09-29
Use this
```

$ttl 38400
@ IN SOA ns1.beestudio.ro. admin.beestudio.ro. (
2013092925
10800
3600
604800
38400 )
@ IN NS ns1.beestudio.ro.
@ IN NS ns2.beestudio.ro.
@ IN MX 10 mail.beestudio.ro.
@ IN A 5.12.101.175
ns1 IN A 5.12.101.175
ns2 IN A 5.12.101.175
mail IN A 5.12.101.175
www IN A 5.12.101.175

```

Restart bind9

---

