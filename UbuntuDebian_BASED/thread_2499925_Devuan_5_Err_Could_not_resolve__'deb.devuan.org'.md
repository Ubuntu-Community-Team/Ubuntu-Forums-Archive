---
title: "Devuan 5: Err: Could not resolve  'deb.devuan.org'"
date: 2024-08-15
forum: Ubuntu/Debian BASED
---

### Post by maketopsite on 2024-08-15
```
root@maketopsite:/home/maketopsite# apt-get update
Ign:1 http://deb.devuan.org/merged daedalus InRelease
Ign:2 http://deb.devuan.org/merged daedalus-security InRelease              
Ign:3 http://deb.devuan.org/merged daedalus-updates InRelease               
Ign:4 http://deb.devuan.org/merged daedalus-backports InRelease             
Ign:5 http://deb.devuan.org/devuan daedalus-proposed-updates InRelease      
Hit:6 https://download.docker.com/linux/debian bookworm InRelease
Ign:1 http://deb.devuan.org/merged daedalus InRelease
Ign:2 http://deb.devuan.org/merged daedalus-security InRelease
Ign:3 http://deb.devuan.org/merged daedalus-updates InRelease
Ign:4 http://deb.devuan.org/merged daedalus-backports InRelease
Ign:5 http://deb.devuan.org/devuan daedalus-proposed-updates InRelease
Ign:1 http://deb.devuan.org/merged daedalus InRelease
Ign:2 http://deb.devuan.org/merged daedalus-security InRelease
Ign:3 http://deb.devuan.org/merged daedalus-updates InRelease
Ign:4 http://deb.devuan.org/merged daedalus-backports InRelease
Ign:5 http://deb.devuan.org/devuan daedalus-proposed-updates InRelease
Err:1 http://deb.devuan.org/merged daedalus InRelease
  Could not resolve 'deb.devuan.org'
Err:2 http://deb.devuan.org/merged daedalus-security InRelease
  Could not resolve 'deb.devuan.org'
Err:3 http://deb.devuan.org/merged daedalus-updates InRelease
  Could not resolve 'deb.devuan.org'
Err:4 http://deb.devuan.org/merged daedalus-backports InRelease
  Could not resolve 'deb.devuan.org'
Err:5 http://deb.devuan.org/devuan daedalus-proposed-updates InRelease
  Could not resolve 'deb.devuan.org'
Reading package lists... Done
W: Failed to fetch http://deb.devuan.org/merged/dists/daedalus/InRelease  Could not resolve 'deb.devuan.org'
W: Failed to fetch http://deb.devuan.org/merged/dists/daedalus-security/InRelease  Could not resolve 'deb.devuan.org'
W: Failed to fetch http://deb.devuan.org/merged/dists/daedalus-updates/InRelease  Could not resolve 'deb.devuan.org'
W: Failed to fetch http://deb.devuan.org/merged/dists/daedalus-backports/InRelease  Could not resolve 'deb.devuan.org'
W: Failed to fetch http://deb.devuan.org/devuan/dists/daedalus-proposed-updates/InRelease  Could not resolve 'deb.devuan.org'
W: Some index files failed to download. They have been ignored, or old ones used instead.
```

Is it please a server-side problem ?

---

### Post by #&amp;thj^% on 2024-08-15
I can reach all those sites, DNS or resolve.config or firewall,might be at play here.

Is this the first you have seen this? And is this a new install?
Can you show us this:
```
dig deb.devuan.org

; <<>> DiG 9.20.0 <<>> deb.devuan.org
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 53945
;; flags: qr rd ra; QUERY: 1, ANSWER: 22, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 1232
; COOKIE: a01482c53aa5ce490100000066be29019c6e320388e4e509 (good)
;; QUESTION SECTION:
;deb.devuan.org.			IN	A

;; ANSWER SECTION:
deb.devuan.org.		1799	IN	CNAME	deb.rr.devuan.org.
deb.rr.devuan.org.	1800	IN	A	106.178.112.231
deb.rr.devuan.org.	1800	IN	A	141.84.43.19
deb.rr.devuan.org.	1800	IN	A	46.4.50.2
deb.rr.devuan.org.	1800	IN	A	195.85.215.180
deb.rr.devuan.org.	1800	IN	A	160.16.137.156
deb.rr.devuan.org.	1800	IN	A	94.16.114.15
deb.rr.devuan.org.	1800	IN	A	185.183.113.131
deb.rr.devuan.org.	1800	IN	A	200.236.31.1
deb.rr.devuan.org.	1800	IN	A	185.236.240.103
deb.rr.devuan.org.	1800	IN	A	103.146.168.12
deb.rr.devuan.org.	1800	IN	A	185.38.15.84
deb.rr.devuan.org.	1800	IN	A	125.228.189.120
deb.rr.devuan.org.	1800	IN	A	131.188.12.211
deb.rr.devuan.org.	1800	IN	A	95.216.15.86
deb.rr.devuan.org.	1800	IN	A	147.78.194.22
deb.rr.devuan.org.	1800	IN	A	67.219.104.166
deb.rr.devuan.org.	1800	IN	A	185.178.192.43
deb.rr.devuan.org.	1800	IN	A	5.161.180.234
deb.rr.devuan.org.	1800	IN	A	190.64.49.124
deb.rr.devuan.org.	1800	IN	A	130.225.254.116
deb.rr.devuan.org.	1800	IN	A	198.58.118.8

;; Query time: 935 msec
;; SERVER: 151.236.14.64#53(151.236.14.64) (UDP)
;; WHEN: Thu Aug 15 10:12:49 MDT 2024
;; MSG SIZE  rcvd: 438


```

---

### Post by maketopsite on 2024-09-01
> **#&thj^% said:**
> I can reach all those sites, DNS or resolve.config or firewall,might be at play here.

Is this the first you have seen this? And is this a new install?
Can you show us this:
```
dig deb.devuan.org

; <<>> DiG 9.20.0 <<>> deb.devuan.org
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 53945
;; flags: qr rd ra; QUERY: 1, ANSWER: 22, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 1232
; COOKIE: a01482c53aa5ce490100000066be29019c6e320388e4e509 (good)
;; QUESTION SECTION:
;deb.devuan.org.            IN    A

;; ANSWER SECTION:
deb.devuan.org.        1799    IN    CNAME    deb.rr.devuan.org.
deb.rr.devuan.org.    1800    IN    A    106.178.112.231
deb.rr.devuan.org.    1800    IN    A    141.84.43.19
deb.rr.devuan.org.    1800    IN    A    46.4.50.2
deb.rr.devuan.org.    1800    IN    A    195.85.215.180
deb.rr.devuan.org.    1800    IN    A    160.16.137.156
deb.rr.devuan.org.    1800    IN    A    94.16.114.15
deb.rr.devuan.org.    1800    IN    A    185.183.113.131
deb.rr.devuan.org.    1800    IN    A    200.236.31.1
deb.rr.devuan.org.    1800    IN    A    185.236.240.103
deb.rr.devuan.org.    1800    IN    A    103.146.168.12
deb.rr.devuan.org.    1800    IN    A    185.38.15.84
deb.rr.devuan.org.    1800    IN    A    125.228.189.120
deb.rr.devuan.org.    1800    IN    A    131.188.12.211
deb.rr.devuan.org.    1800    IN    A    95.216.15.86
deb.rr.devuan.org.    1800    IN    A    147.78.194.22
deb.rr.devuan.org.    1800    IN    A    67.219.104.166
deb.rr.devuan.org.    1800    IN    A    185.178.192.43
deb.rr.devuan.org.    1800    IN    A    5.161.180.234
deb.rr.devuan.org.    1800    IN    A    190.64.49.124
deb.rr.devuan.org.    1800    IN    A    130.225.254.116
deb.rr.devuan.org.    1800    IN    A    198.58.118.8

;; Query time: 935 msec
;; SERVER: 151.236.14.64#53(151.236.14.64) (UDP)
;; WHEN: Thu Aug 15 10:12:49 MDT 2024
;; MSG SIZE  rcvd: 438


```

This is the first time I have seen this.  This is not a new install.

```
maketopsite@maketopsite:~$ dig deb.devuan.org

; <<>> DiG 9.18.28-1~deb12u2-Debian <<>> deb.devuan.org
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 4566
;; flags: qr rd ra; QUERY: 1, ANSWER: 22, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 512
;; QUESTION SECTION:
;deb.devuan.org.            IN    A

;; ANSWER SECTION:
deb.devuan.org.        1800    IN    CNAME    deb.rr.devuan.org.
deb.rr.devuan.org.    1800    IN    A    94.16.114.15
deb.rr.devuan.org.    1800    IN    A    185.236.240.103
deb.rr.devuan.org.    1800    IN    A    106.178.112.231
deb.rr.devuan.org.    1800    IN    A    5.161.180.234
deb.rr.devuan.org.    1800    IN    A    67.219.104.166
deb.rr.devuan.org.    1800    IN    A    185.38.15.84
deb.rr.devuan.org.    1800    IN    A    185.183.113.131
deb.rr.devuan.org.    1800    IN    A    131.188.12.211
deb.rr.devuan.org.    1800    IN    A    147.78.194.22
deb.rr.devuan.org.    1800    IN    A    195.85.215.180
deb.rr.devuan.org.    1800    IN    A    103.146.168.12
deb.rr.devuan.org.    1800    IN    A    95.216.15.86
deb.rr.devuan.org.    1800    IN    A    200.236.31.1
deb.rr.devuan.org.    1800    IN    A    46.4.50.2
deb.rr.devuan.org.    1800    IN    A    130.225.254.116
deb.rr.devuan.org.    1800    IN    A    141.84.43.19
deb.rr.devuan.org.    1800    IN    A    190.64.49.124
deb.rr.devuan.org.    1800    IN    A    160.16.137.156
deb.rr.devuan.org.    1800    IN    A    185.178.192.43
deb.rr.devuan.org.    1800    IN    A    198.58.118.8
deb.rr.devuan.org.    1800    IN    A    125.228.189.120

;; Query time: 139 msec
;; SERVER: 10.0.0.138#53(10.0.0.138) (UDP)
;; WHEN: Thu Aug 15 18:31:49 CEST 2024
;; MSG SIZE  rcvd: 400

maketopsite@maketopsite:~$
```

---

