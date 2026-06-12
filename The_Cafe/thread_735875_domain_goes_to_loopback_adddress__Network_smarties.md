---
title: "domain goes to loopback adddress?  Network smarties, can you figure this out?"
date: 2008-03-26
forum: The Cafe
---

### Post by Atomic Dog on 2008-03-26
Four pings to the same domain name in a row.  two ping the loopback address, two ping the correct address.  Well maybe like 5 seconds in between pinging the domain.  It is the strangest thing I have ever seen.

so I used dig..

 <<>> DiG 9.3.4 <<>> NS20.NETRIPLEX.COM domain.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 26593
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 5, ADDITIONAL: 1

;; QUESTION SECTION:
;ourdomain.com.                  IN      A

;; ANSWER SECTION:
ourdomain.com.           3600    IN      A       70.204.196.170
ourdomain.com.           3600    IN      A       127.0.0.1


So what does this mean?  Did one of our network people insert the loopback address by accident?  I'm just curious.

---

### Post by Jim! on 2008-03-26
One day I'll understand something about that crazy jibberish you just wrote, but till then I better keep studying for me Cisco networking course - I have a test next tuesday:O

---

### Post by Atomic Dog on 2008-03-28
meany!  :p

---

