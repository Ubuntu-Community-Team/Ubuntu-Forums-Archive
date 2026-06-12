---
title: "Weird name resolution - slow cache?"
date: 2012-07-28
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by effenberg0x0 on 2012-07-28
#1
```

[13:47:31] ahsl@AL-DESK01:[~]: dig whatever.com

; <<>> DiG 9.8.1-P1 <<>> whatever.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 14462
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;whatever.com.			IN	A

;; ANSWER SECTION:
whatever.com.		14400	IN	A	216.240.188.132

;; Query time: 187 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Sat Jul 28 13:47:32 2012
;; MSG SIZE  rcvd: 46

```
#2 (cache)
```

[13:47:35] ahsl@AL-DESK01:[~]: dig whatever.com

; <<>> DiG 9.8.1-P1 <<>> whatever.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 31817
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;whatever.com.			IN	A

;; ANSWER SECTION:
whatever.com.		14338	IN	A	216.240.188.132

;; Query time: 9 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Sat Jul 28 13:48:36 2012
;; MSG SIZE  rcvd: 46

```
#3 (should be close to 0ms)
```

[13:48:40] ahsl@AL-DESK01:[~]: dig whatever.com

; <<>> DiG 9.8.1-P1 <<>> whatever.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 12671
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;whatever.com.			IN	A

;; ANSWER SECTION:
whatever.com.		14275	IN	A	216.240.188.132

;; Query time: 10 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Sat Jul 28 13:49:42 2012
;; MSG SIZE  rcvd: 46

```

I do get 0ms from #2 and on when using a local isc-dhcpd/dnsmasq server in the same LAN. What is it using 10ms for?

Regards,
Effenberg

---

### Post by ventrical on 2012-07-28
I do not have highspeed.


```
; <<>> DiG 9.8.1-P1 <<>> whatever.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 43263
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;whatever.com.            IN    A

;; ANSWER SECTION:
whatever.com.        14400    IN    A    216.240.188.132

;; Query time: 250 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Sat Jul 28 17:11:21 2012
;; MSG SIZE  rcvd: 46

dale@dale:~$ dig whatever.com

; <<>> DiG 9.8.1-P1 <<>> whatever.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 39334
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;whatever.com.            IN    A

;; ANSWER SECTION:
whatever.com.        14390    IN    A    216.240.188.132

;; Query time: 72 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Sat Jul 28 17:11:31 2012
;; MSG SIZE  rcvd: 46

dale@dale:~$ dig whatever.com

; <<>> DiG 9.8.1-P1 <<>> whatever.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 28260
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;whatever.com.            IN    A

;; ANSWER SECTION:
whatever.com.        14383    IN    A    216.240.188.132

;; Query time: 68 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Sat Jul 28 17:11:38 2012
;; MSG SIZE  rcvd: 46

dale@dale:~$ 

```

---

### Post by effenberg0x0 on 2012-07-29
I haven't managed to study this at all, but there's definitely something wrong here when comparing this Alpha to PP, when it comes to browsing. 

Alpha: Pages load slow, fail to load, load partially. PP: Pages load fast, complete, normal. This is on the same LAN, WAN and Hardware. It feels like DNS, because I can get normal speed on download tests from IPs. And those DNS results I posted above are not normal (IMO). 

I'll try to test it in details tomorrow...

Regards,
Effenberg

---

### Post by effenberg0x0 on 2012-07-29
Real DNS cache using standard DNSMasq on the same LAN (192.168.0.100). I'm 192.168.0.101.

**#1**
```

[00:22:38] ahsl@AL-DESK01:[~]: dig misskittin.com

; <<>> DiG 9.8.1-P1 <<>> misskittin.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 28857
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;misskittin.com.            IN    A

;; ANSWER SECTION:
misskittin.com.        14400    IN    A    80.190.139.145

;; Query time: **277 msec**
;; SERVER: 192.168.0.100#53(192.168.0.100)
;; WHEN: Mon Jul 30 00:22:43 2012
;; MSG SIZE  rcvd: 48

```[B]#2 (Cache)
[/B]```

[00:22:43] ahsl@AL-DESK01:[~]: dig misskittin.com

; <<>> DiG 9.8.1-P1 <<>> misskittin.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 35655
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;misskittin.com.            IN    A

;; ANSWER SECTION:
misskittin.com.        14394    IN    A    80.190.139.145

;; Query time: **0 msec**
;; SERVER: 192.168.0.100#53(192.168.0.100)
;; WHEN: Mon Jul 30 00:22:49 2012
;; MSG SIZE  rcvd: 48


```#3
```

[00:22:49] ahsl@AL-DESK01:[~]: dig misskittin.com

; <<>> DiG 9.8.1-P1 <<>> misskittin.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 65208
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;misskittin.com.            IN    A

;; ANSWER SECTION:
misskittin.com.        14392    IN    A    80.190.139.145

;; Query time: **0 msec**
;; SERVER: 192.168.0.100#53(192.168.0.100)
;; WHEN: Mon Jul 30 00:22:51 2012
;; MSG SIZE  rcvd: 48

```I have removed network-manager*, resolvconf, dnsmasq* from client and server, manually reinstalled dnsmasq to server and manually set /etc/network/interfaces, /etc/resolv.conf to sane values.

All local devices are browsing fast and normal now.

Regards,
Effenberg

---

### Post by effenberg0x0 on 2012-07-30
> **ventrical said:**
> I do not have highspeed.


```
; <<>> DiG 9.8.1-P1 <<>> whatever.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 43263
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;whatever.com.            IN    A

;; ANSWER SECTION:
whatever.com.        14400    IN    A    216.240.188.132

;; Query time: 250 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Sat Jul 28 17:11:21 2012
;; MSG SIZE  rcvd: 46

dale@dale:~$ dig whatever.com

; <<>> DiG 9.8.1-P1 <<>> whatever.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 39334
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;whatever.com.            IN    A

;; ANSWER SECTION:
whatever.com.        14390    IN    A    216.240.188.132

;; Query time: 72 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Sat Jul 28 17:11:31 2012
;; MSG SIZE  rcvd: 46

dale@dale:~$ dig whatever.com

; <<>> DiG 9.8.1-P1 <<>> whatever.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 28260
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;whatever.com.            IN    A

;; ANSWER SECTION:
whatever.com.        14383    IN    A    216.240.188.132

;; Query time: 68 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Sat Jul 28 17:11:38 2012
;; MSG SIZE  rcvd: 46

dale@dale:~$ 

```

Hi, 

The time it takes to resolve the first time is irrelevant: It will depend on a lot of factors (if you're using your ISP DNS, another public DNS like Google or OpenDNS, your broadband speed, etc). But, from then on, I expect 0ms, or very close to 0ms. That's what a cache means to me. 

The DNS+resolvconf thing we adopted since PP is what's weird in my first post - I can't seem to make it work as a cache on the current Alpha. 

It works fine on my PP laptop (0ms on query #2, #3, etc). 

Regards,
Effenberg

---

### Post by mcg on 2012-08-23
Wondering if this has gotten any better on QQ? Network Manager+dnsmaq seems totally busted for name resolution for me in QQ.

---

### Post by stoneguy on 2012-08-23
Been noticing that too. FF times out connecting on PP and QQ when LL on another box connects. All thru the same router.

---

### Post by dino99 on 2012-08-23
i've fallen in trouble too today: was working normally then without major upgrades, i've fully lost internet connection, even ping was failing.

so i've deactivated dns=dnsmasq into nm conf and set a static dns-nameserver into the interfaces.

Then internet is back again.

related thread:  [http://ubuntuforums.org/showthread.php?t=2046605](http://ubuntuforums.org/showthread.php?t=2046605)

---

### Post by effenberg0x0 on 2012-08-23
We had discussed the adoption of dnsmasq in nm since PP development cycle and, although I *think* I'm completely comfortable with the definition, usage and technical aspects of name resolution, I could never understand why one would dnsmasqd in certain situations, such as:

- Desktop or Laptop, any wired connection, DHCP or static, in any environment (home/office/public). You're just as exposed in terms of security with or without dnsmasq if you're in ethernet. There's no real performance gain;
- Desktop or Laptop, wired/wireless connection, DHCP or static, in any environment (home/office/public) when a trusted local nameserver is available.
- Desktop or Laptop, wired or wireless, DHCP or static, in any environment (home/office/public) when using a VPN and resolving in a predetermined (and then supposedly secure) nameserver.
- Desktop or Laptop, DHCP or static, directly connected to broadband link, using the ISP-provided nameserver. There's no one else else in your LAN side, you'll depend on the ISP nameserver anyway. 

And the only situation I can think of in which it would make sense is:
- Laptop/tablet, wireless connection, dhcp client, roaming through unknown routers, receiving specific IP/Gateway/nameservers via dhcp, considering the user is willing to use them instead of relying in a more secure nameserver, such as Google's, OpenDNS, his own, his company's, etc.

So the reasoning to have this enabled as a default for all connections continues to be a mystery to me. 

I work from home and have my own infrastructure, with a rack of server, WAN and LAN appliances (WAN modems, Load Balancer, Ubuntu Server (firewall, dhcpd, nameserver, VPN, www, SSH, FTP, other LAN/WAN services), LAN switch, wireless APs. It makes no sense to me to have other instances of dnsmasqd running on clients. I completely understand this is not the sort of infrastructure ordinary uers will have at home or small businesses. Yet, it's just a more professional implementation of the same architecture/services one would get in a typical "ISP Broadband Modem -> Wired/Wireless Router+AP -> clients" structure. 

In my understanding, this feature is exclusively aimed towards road warriors using mobile devices.

Regards,
Effenberg

---

### Post by dino99 on 2012-08-23
as Stephane Graber explain into his blog: this has been designed due to some vpn needs (so not everyone is concerned, i fully agree)

---

### Post by effenberg0x0 on 2012-08-23
> **dino99 said:**
> as Stephane Graber explain into his blog: this has been designed due to some vpn needs (so not everyone is concerned, i fully agree)

Hi Dino99 :)
Yep, I read it too, it makes no sense to me. How would enabling a local DNS cache to all nm connections be a good solution to solve the VPN specifics of some (I believe small?) percentage of users?

Which VPNs are these in which the user is not resolving names in the company trusted namserver? I use 2 VPNs, one is open source the other is Cisco-Based. In my experience, network administrators in IT expect our client machines to use the trusted nameserver at all times, not any local cache.

Regards,
Effenberg

---

