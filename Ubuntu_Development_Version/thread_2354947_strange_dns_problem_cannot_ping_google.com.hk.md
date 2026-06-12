---
title: "strange dns problem: cannot ping google.com.hk"
date: 2017-03-07
forum: Ubuntu Development Version
---

### Post by 3togo on 2017-03-07
I made a fresh install of zesty. Everything is running smoothly except that I can't dns resolve any domain names ended with .hk

```
jc@jc-T5400:~$ ping  google.com.hk
ping: google.com.hk: Name or service not known

jc@jc-T5400:~$ ping ftp.cuhk.edu.hk
ping: ftp.cuhk.edu.hk: Name or service not known

jc@jc-T5400:~$ ping google.com
PING google.com (172.217.25.14) 56(84) bytes of data.
64 bytes from 172.217.25.14 (172.217.25.14): icmp_seq=1 ttl=55 time=3.76 ms
64 bytes from 172.217.25.14 (172.217.25.14): icmp_seq=2 ttl=55 time=3.46 ms

jc@jc-T5400:~$ nmcli dev show|grep -i dns
IP4.DNS[1]:                             4.4.4.4
IP4.DNS[2]:                             158.132.14.1
IP4.DNS[3]:                             158.132.18.1
IP4.DNS[4]:                             8.8.8.8
```

Any pointer on how to trace the problem?

---

### Post by papibe on 2017-03-07
Hi 3togo.

Could you post the output of these commands?

```
dig google.com.hk

dig ftp.cuhk.edu.hk

nslookup google.com.hk 

nslookup google.com.hk 8.8.8.8
```
Regards.

---

### Post by 3togo on 2017-03-08
```
marvel@marvel-X1:~$ 
marvel@marvel-X1:~$ dig google.com.hk

; <<>> DiG 9.10.3-P4-Ubuntu <<>> google.com.hk
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 13452
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;google.com.hk.			IN	A

;; Query time: 29 msec
;; SERVER: 127.0.0.53#53(127.0.0.53)
;; WHEN: Wed Mar 08 23:02:36 CST 2017
;; MSG SIZE  rcvd: 42

marvel@marvel-X1:~$ dig google.com

; <<>> DiG 9.10.3-P4-Ubuntu <<>> google.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 44232
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;google.com.			IN	A

;; ANSWER SECTION:
google.com.		228	IN	A	172.217.24.206

;; Query time: 7 msec
;; SERVER: 127.0.0.53#53(127.0.0.53)
;; WHEN: Wed Mar 08 23:03:02 CST 2017
;; MSG SIZE  rcvd: 55

marvel@marvel-X1:~$ dig ftp.cuhk.com.hk

; <<>> DiG 9.10.3-P4-Ubuntu <<>> ftp.cuhk.com.hk
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 61063
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;ftp.cuhk.com.hk.		IN	A

;; Query time: 9 msec
;; SERVER: 127.0.0.53#53(127.0.0.53)
;; WHEN: Wed Mar 08 23:03:20 CST 2017
;; MSG SIZE  rcvd: 44

marvel@marvel-X1:~$ nslookup google.com.hk
Server:		127.0.0.53
Address:	127.0.0.53#53

** server can't find google.com.hk: SERVFAIL

marvel@marvel-X1:~$ nslookup google.com
Server:		127.0.0.53
Address:	127.0.0.53#53

Non-authoritative answer:
Name:	google.com
Address: 172.217.24.206

marvel@marvel-X1:~$ nslookup google.com.hk 8.8.8.8
Server:		8.8.8.8
Address:	8.8.8.8#53

Non-authoritative answer:
Name:	google.com.hk
Address: 172.217.24.195

marvel@marvel-X1:~$ nslookup google.com 8.8.8.8
Server:		8.8.8.8
Address:	8.8.8.8#53

Non-authoritative answer:
Name:	google.com
Address: 172.217.24.206

marvel@marvel-X1:~$ 
```

> **papibe said:**
> Hi 3togo.

Could you post the output of these commands?

```
dig google.com.hk

dig ftp.cuhk.edu.hk

nslookup google.com.hk 

nslookup google.com.hk 8.8.8.8
```
Regards.

---

### Post by Perfect Storm on 2017-03-08
code tags added.

---

### Post by SeijiSensei on 2017-03-08
I have no problem resolving any of those names from here:
```

$ host google.com.hk
google.com.hk has address 172.217.11.35
google.com.hk has IPv6 address 2607:f8b0:4006:814::2003
google.com.hk mail is handled by 50 alt4.aspmx.l.google.com.
google.com.hk mail is handled by 10 aspmx.l.google.com.
google.com.hk mail is handled by 20 alt1.aspmx.l.google.com.
google.com.hk mail is handled by 30 alt2.aspmx.l.google.com.
google.com.hk mail is handled by 40 alt3.aspmx.l.google.com.

```

Can you ping 172.217.11.35? 

The servers 216.239.32.10, 216.239.34.10, 216.239.36.10, 216.239.38.10 are reported as authoritative for google.com.hk.  (They are ns1-ns4.google.com.)  Can you ping them?

---

### Post by 3togo on 2017-03-08
Hi SeijiSensei,

I tried the zesty at different locations using different wifi providers. The problem remains the same. 

jc@jc-T5400:~$ host google.com
google.com has address 216.58.221.238
google.com has IPv6 address 2404:6800:4005:805::200e
google.com mail is handled by 10 aspmx.l.google.com.
google.com mail is handled by 40 alt3.aspmx.l.google.com.
google.com mail is handled by 20 alt1.aspmx.l.google.com.
google.com mail is handled by 30 alt2.aspmx.l.google.com.
google.com mail is handled by 50 alt4.aspmx.l.google.com.
jc@jc-T5400:~$ host google.com.hk
Host google.com.hk not found: 2(SERVFAIL)
jc@jc-T5400:~$ ping 172.217.11.35
PING 172.217.11.35 (172.217.11.35) 56(84) bytes of data.
64 bytes from 172.217.11.35: icmp_seq=1 ttl=48 time=203 ms
64 bytes from 172.217.11.35: icmp_seq=2 ttl=48 time=202 ms
64 bytes from 172.217.11.35: icmp_seq=3 ttl=48 time=202 ms

--- 172.217.11.35 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 202.849/202.936/203.054/0.086 ms

---

### Post by papibe on 2017-03-08
Try this:
```
host google.com.hk 8.8.8.8

host google.com.hk 4.4.4.4

host google.com.hk 158.132.14.1

host google.com.hk 158.132.18.1

```
4.4.4.4 is a Google DNS, btw.

Regards.

---

### Post by 3togo on 2017-03-09
thank you to Papibe and Seiji&#65294; I might have found the problem. Probably, I messed up the dns-resolv. 

Below is what I did to purge the conflicting programs. 
p.s. I didn't install rdnssd but I think it is no harm to purge it as well.

sudo apt-get purge dnsmasq resolvconf rdnssd


ref. [https://ctrl.blog/entry/how-to-debian-dns-resolv](https://ctrl.blog/entry/how-to-debian-dns-resolv)

---

### Post by 3togo on 2017-03-11
Below is how I solved the mess up of obsolete dns and dhcp configs. Deleting the whole /etc/NetworkManager might be too drastic but it is essential to my case
 
```
sudo apt-get purge dnsmasq resolvconf rdnssd bind9 libnss-resolve 
sudo rm /etc/NetworkManager/* -Rf
sudo service networking restart
sudo dhclient -nw
sudo apt-get --reinstall install network-manager ubuntu-minimal
sudo reboot
```

after rebooting and reconfig your network-manager-gnome

```
ping google.com.hk
```

---

### Post by 3togo on 2017-04-01
I have another metod to solve the problem

I fixed the problem by setting DNSSEC to no in /etc/systemd/resolved.conf followed by

>sudo service systemd-resolved restart

but, setting dnssec to no is not a good idea, isn't it?

---

### Post by wgarcia on 2017-04-02
On setting dnssec to no, see:

[https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1647031](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1647031)

There is something not working very wll in DNS resolving for CNAME DNS definitions (subdomains), it seems. In my case, if I don't have DNSSEC set to no OR have a browser (Firefox, Chrome) running, subdomains are not resolved. How can starting a browser solve something like this, goes beyond my comprehension.

---

