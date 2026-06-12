---
title: "/var/log/auth.log unknown login attempts."
date: 2008-11-29
forum: Server Platforms
---

### Post by spiderbatdad on 2008-11-29
I'm curious about this type of message in /var/log/auth.log ```
 Failed password for invalid user snort from 189.6.234.118 port 61367 ssh2
sshd[16713]: Connection from 189.6.234.118 port 61577
sshd[16713]: reverse mapping checking getaddrinfo for bd06ea76.virtua.com.br [189.6.234.118] failed - POSSIBLE BREAK-IN ATTEMPT!
sshd[16713]: Invalid user radiomail from 189.6.234.118
 sshd[16713]: pam_unix(sshd:auth): check pass; user unknown
 pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=189.6.234.118 
sshd[16713]: Failed password for invalid user radiomail from 189.6.234.118 port 61577 ssh2
sshd[16715]: Connection from 189.6.234.118 port 61975
sshd[16715]: reverse mapping checking getaddrinfo for bd06ea76.virtua.com.br [189.6.234.118] failed - POSSIBLE BREAK-IN ATTEMPT!

``` Of course I do not know this person or address. dig -x shows ```
; <<>> DiG 9.5.0-P2 <<>> -x 189.6.234.118
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 54281
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 3, ADDITIONAL: 0

;; QUESTION SECTION:
;118.234.6.189.in-addr.arpa.	IN	PTR

;; ANSWER SECTION:
118.234.6.189.in-addr.arpa. 3600 IN	PTR	bd06ea76.virtua.com.br.

;; AUTHORITY SECTION:
234.6.189.in-addr.arpa.	3600	IN	NS	dns1.virtua.com.br.
234.6.189.in-addr.arpa.	3600	IN	NS	ns.embratel.com.br.
234.6.189.in-addr.arpa.	3600	IN	NS	dns2.virtua.com.br.

;; Query time: 322 msec
;; SERVER: 66.189.132.4#53(66.189.132.4)
;; WHEN: Sun Nov 30 17:37:45 2008


```Is it normal for unknow users to suddenly see my server. Could it be related to the fact that an authorized user previously logged in...albiet from a local network?

---

### Post by martien on 2008-11-29
> **spiderbatdad said:**
> I'm curious about this type of message in /var/log/auth.log ```
 sshd[11058]: reverse mapping checking getaddrinfo for uk.chriselliott.info [78.110.170.243] failed - POSSIBLE BREAK-IN ATTEMPT!
sshd[11058]: Invalid user admin from 78.110.170.243
Nov 29 09:35:07 hedwig-laptop sshd[11058]: pam_unix(sshd:auth): check pass; user unknown
Nov 29 09:35:07 hedwig-laptop sshd[11058]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=78.110.170.243 
Nov 29 09:35:09 hedwig-laptop sshd[11058]: Failed password for invalid user admin from 78.110.170.243 port 52472 ssh2

``` Of course I do not know this person or address. dig -x shows ```
; <<>> DiG 9.5.0-P2 <<>> -x 78.110.170.243
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 52150
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 2, ADDITIONAL: 2

;; QUESTION SECTION:
;243.170.110.78.in-addr.arpa.	IN	PTR

;; ANSWER SECTION:
243.170.110.78.in-addr.arpa. 80243 IN	PTR	uk.chriselliott.info.

;; AUTHORITY SECTION:
170.110.78.in-addr.arpa. 80243	IN	NS	rdns2.vaserv.com.
170.110.78.in-addr.arpa. 80243	IN	NS	rdns1.vaserv.com.

;; ADDITIONAL SECTION:
rdns1.vaserv.com.	166643	IN	A	72.9.148.237
rdns2.vaserv.com.	166643	IN	A	77.74.198.180


```Is it normal for unknow users to suddenly see my server. Could it be related to the fact that an authorized user previously logged in...albiet from a local network?
You were attacked. Usually that are bots trying different login values with hope for success. You should change the ssh port or think about some way to defend the system (denyhosts, firewall rules, some other application).

---

### Post by spiderbatdad on 2008-11-29
The timing was bizarre in that a friend had just logged in locally from his ibook. I wonder if some bot is running on his machine?

---

### Post by hictio on 2008-11-29
> **spiderbatdad said:**
> I'm curious about this type of message in /var/log/auth.log ```
 sshd[11058]: reverse mapping checking getaddrinfo for uk.chriselliott.info [78.110.170.243] failed - POSSIBLE BREAK-IN ATTEMPT!
sshd[11058]: Invalid user admin from 78.110.170.243
Nov 29 09:35:07 hedwig-laptop sshd[11058]: pam_unix(sshd:auth): check pass; user unknown
Nov 29 09:35:07 hedwig-laptop sshd[11058]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=78.110.170.243 
Nov 29 09:35:09 hedwig-laptop sshd[11058]: Failed password for invalid user admin from 78.110.170.243 port 52472 ssh2

```Is it normal for unknow users to suddenly see my server. Could it be related to the fact that an authorized user previously logged in...albiet from a local network?

On that particular box, do you have the SSH access open to the internet?
If that is the case, do you have some sort of brute force blocking script monitoring your logs?

---

### Post by Thirtysixway on 2008-11-29
Change the ssh port, and install fail2ban

---

