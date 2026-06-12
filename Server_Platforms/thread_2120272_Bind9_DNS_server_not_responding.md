---
title: "Bind9 DNS server not responding"
date: 2013-02-26
forum: Server Platforms
---

### Post by Toriku on 2013-02-26
I have a few Windows boxes all using an Ubuntu server for their primary DNS server... Its worked great for 8 months, however yesterday there was a power cut, and now DNS server isn't responding...

 I lost connection with the Ubuntu server at the time, I went and dug it out, reset it and connected via ssh, it can access the internet, Apache is working and Bind seems to be running, I've updated all the files with the new IP addresses, incremented the serial, rebooted the server and still nothing,

the Windows computers all say that the DNS server isn't responding,

can anyone point me in the right direction for recovering this function?
Thanks

---

### Post by Habitual on 2013-02-26
```
dig @ip.of.bind.server txt chaos version.bind
```

---

### Post by Toriku on 2013-02-26
I ran that and got a warning for recursion being unavailable, but otherwise it found the server... and this is from a separate office...

> ; <<>> DiG 9.8.1-P1 <<>> @[*server ip*] txt chaos version.bind
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 15299
;; flags: qr aa rd; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 0
;; WARNING: recursion requested but not available

;; QUESTION SECTION:
;version.bind.                  CH      TXT

;; ANSWER SECTION:
version.bind.           0       CH      TXT     "9.8.1-P1"

;; AUTHORITY SECTION:
version.bind.           0       CH      NS      version.bind.

;; Query time: 91 msec
;; SERVER: [*server ip*]#53([*server ip*])
;; WHEN: Tue Feb 26 17:06:03 2013
;; MSG SIZE  rcvd: 65


---

### Post by Habitual on 2013-02-26
Can the Windows boxen ping the dns server?
also you could try ```
telnet IP.of.dns.server 53
```from the Windows boxes (testing for firewall or other intervening mechanism). Can they telnet to the dns host?

Please let us know...

---

### Post by Toriku on 2013-02-27
> **Habitual said:**
> Can the Windows boxen ping the dns server?
also you could try ```
telnet IP.of.dns.server 53
```from the Windows boxes (testing for firewall or other intervening mechanism). Can they telnet to the dns host?

Please let us know...

Typing in the IP address of the server into a windows box brings up the page in apache2, I've checked from "http://www.yougetsignal.com/tools/open-ports/" and port 53 appears to be open, I can ssh/telnet into the system no problems...
any ideas?

---

### Post by Habitual on 2013-02-27
not a clue. Sorry.
Someone with more dns.fu will be along to help.

---

