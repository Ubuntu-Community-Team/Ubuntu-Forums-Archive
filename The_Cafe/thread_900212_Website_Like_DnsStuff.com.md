---
title: "Website Like DnsStuff.com"
date: 2008-08-25
forum: The Cafe
---

### Post by Vishal Agarwal on 2008-08-25
Earlier I was used to check my IP with [DnsStuff ]("http://www.dnsstuff.com"). But now it has become a paid website, and I cannot check my IP/Dns/Mx etc. reports. Can anybody suggest any website like Dns Stuff ?

---

### Post by Bachstelze on 2008-08-25
Something like this?

```

firas@iori ~ % dig ubuntu.com ANY

; <<>> DiG 9.5.0-P2 <<>> ubuntu.com ANY
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 63906
;; flags: qr rd ra; QUERY: 1, ANSWER: 4, AUTHORITY: 3, ADDITIONAL: 3

;; QUESTION SECTION:
;ubuntu.com.                    IN      ANY

;; ANSWER SECTION:
ubuntu.com.             48268   IN      NS      ns1.canonical.com.
ubuntu.com.             48268   IN      NS      ns2.canonical.com.
ubuntu.com.             48268   IN      NS      ns3.canonical.com.
ubuntu.com.             560     IN      A       91.189.94.250

;; AUTHORITY SECTION:
ubuntu.com.             48268   IN      NS      ns2.canonical.com.
ubuntu.com.             48268   IN      NS      ns3.canonical.com.
ubuntu.com.             48268   IN      NS      ns1.canonical.com.

;; ADDITIONAL SECTION:
ns1.canonical.com.      48665   IN      A       91.189.94.173
ns2.canonical.com.      48665   IN      A       91.189.94.219
ns3.canonical.com.      48665   IN      A       209.6.3.210

;; Query time: 3 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Mon Aug 25 11:53:04 2008
;; MSG SIZE  rcvd: 198

```

---

### Post by mellowd on 2008-08-25
I was going to suggest the same. dig is a great tool and its built in

---

### Post by Vishal Agarwal on 2008-08-25
The dig command I was using. But with the dnsstuff.com it was showing all the report for security issues, blacklisted Ip with many lists. And many other reports. 
I am searching for some printout If I could have and I can load it here.

---

### Post by Vishal Agarwal on 2008-08-25
I know that DNS reporting good sites are there, But I am unable to find some good one.

---

### Post by Vishal Agarwal on 2008-08-25
I am still in problem.

---

