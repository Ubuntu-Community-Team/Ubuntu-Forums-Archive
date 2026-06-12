---
title: "Redirected to localhost"
date: 2009-10-01
forum: Server Platforms
---

### Post by dvlchd3 on 2009-10-01
I am extremely confused now.  For some reason whenever I attempt to go to gostats.com, I am redirected to localhost...

I have changed my /etc/resolv.conf file to 2.1.1.1 and 2.1.1.2, to make sure it is not my ISPs DNS server, however, still the same thing.

I have also attempted to go directly to gostats ip address (given to me by a friend), however, I am still redirected to localhost.

[I say "redirected" but its more like my apache server thinks it is gostats.com.  The address stays gostats.com in the address bar of Firefox.  If I go to gostats.com/base, it takes me to my Base page (for Snort).]

The only changes I've made past the defaults to apache are to the ports.conf file.  Since apache is only used as a dev environment, I changed that file to only accept requests from 127.0.0.1:80 and 127.0.0.1:443.

I also do not have any DNS server installed.

Ping:
```
ping gostats.com
PING gostats.com (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=0.072 ms
64 bytes from localhost (127.0.0.1): icmp_seq=2 ttl=64 time=0.069 ms
64 bytes from localhost (127.0.0.1): icmp_seq=3 ttl=64 time=0.073 ms
^C
--- gostats.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.069/0.071/0.073/0.007 ms

```

Traceroute:
```
traceroute gostats.com
traceroute to gostats.com (127.0.0.1), 30 hops max, 60 byte packets
 1  localhost (127.0.0.1)  0.072 ms  0.025 ms  0.026 ms

```

I'm extremely confused.  It seems to only be for gostats.com.  Obviously ubuntuforums.org is fine, as well as google, all of my client's websites, etc.

Has anyone experienced this issue, or have any idea of where I can begin to look for the problem?

---

### Post by shizzy-t on 2009-10-01
Check /etc/hosts or a firewall rule maybe?

---

### Post by doas777 on 2009-10-01
what do you get from this:
```

dig gostats.com
```

I get:
```

; <<>> DiG 9.5.1-P2 <<>> gostats.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 34175
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 5, ADDITIONAL: 2

;; QUESTION SECTION:
;gostats.com.            IN    A

;; ANSWER SECTION:
gostats.com.        604269    IN    A    208.43.215.131

;; AUTHORITY SECTION:
gostats.com.        85869    IN    NS    ns1.dnsmadeeasy.com.
gostats.com.        85869    IN    NS    ns2.dnsmadeeasy.com.
gostats.com.        85869    IN    NS    ns3.dnsmadeeasy.com.
gostats.com.        85869    IN    NS    ns4.dnsmadeeasy.com.
gostats.com.        85869    IN    NS    ns0.dnsmadeeasy.com.

;; ADDITIONAL SECTION:
ns2.dnsmadeeasy.com.    58621    IN    A    208.80.126.2
ns4.dnsmadeeasy.com.    125680    IN    A    208.80.127.2

;; Query time: 80 msec
;; SERVER: 10.88.2.10#53(10.88.2.10)
;; WHEN: Thu Oct  1 09:43:22 2009
;; MSG SIZE  rcvd: 179


```

also check your hosts file. do you have any entries there redirecting to localhost?

---

### Post by dvlchd3 on 2009-10-01
Wow, there are multiple entries in my /etc/hosts file that reference gostats.com.

And I know exactly where it came from.  I followed a post by bodhi.zazen to secure firefox.  One of the steps was to download a hosts file that blocks ads.  However, gostats is not an ad company, they provide statistics for web sites.  I guess I could see how this would scare people since they do track A LOT of information about the users.

Now I feel like an idiot.  Thank you all for the help!

---

