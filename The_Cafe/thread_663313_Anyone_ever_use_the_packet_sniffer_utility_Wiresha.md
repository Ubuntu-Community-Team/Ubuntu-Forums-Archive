---
title: "Anyone ever use the packet sniffer utility Wireshark?  Any tips?"
date: 2008-01-10
forum: The Cafe
---

### Post by kevdog on 2008-01-10
Anybody ever use Wireshark??  Seems very powerful however difficult to interpret output.

---

### Post by jrusso2 on 2008-01-10
This might help

[http://www.chrissanders.org/?p=47](http://www.chrissanders.org/?p=47)

---

### Post by kevdog on 2008-01-10
Ive download a sample http packet with gzip content

This came from the wireshark sample capture list:

```


ET /test/ethereal.html HTTP/1.1

Host: cerberus

User-Agent: Mozilla/5.0 (X11; U; Linux ppc; rv:1.7.3) Gecko/20041004 Firefox/0.10.1

Accept: text/xml,application/xml,application/xhtml+xml,text/html;q=0.9,text/plain;q=0.8,image/png,*/*;q=0.5

Accept-Language: en-us,en;q=0.5

Accept-Encoding: gzip,deflate

Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7

Keep-Alive: 300

Connection: keep-alive

Cookie: FGNCLIID=05c04axp1yaqynldtcdiwis0ag1



HTTP/1.1 200 OK

Date: Fri, 29 Oct 2004 05:21:00 GMT

Server: Apache/2.0.50 (Fedora)

Last-Modified: Fri, 29 Oct 2004 05:20:21 GMT

ETag: "126e1f-6d-371b2f40"

Accept-Ranges: bytes

Vary: Accept-Encoding

Content-Encoding: gzip

Content-Length: 92

Connection: close

Content-Type: text/html; charset=UTF-8



............(......HML....).,.I.s-.H-JM.Qp.H.-.IU.HLO...Hr..CT.$..T.5qbU.4L.....l....n.Cm...


```

Is it possible to decode the 92 byte gzip data with wireshark?

---

### Post by mr.propre on 2008-01-10
I sometimes use it on a network on my school, they only use hubs so it easy to listen and to 'steel' password. Though I don't test or use them, its just fun thing when I'm bored. On the other hand, if your password is "beer1985", than you deserve to get your password stolen! :lolflag:

---

### Post by bufsabre666 on 2008-01-10
> **mr.propre said:**
> I sometimes use it on a network on my school, they only use hubs so it easy to listen and to 'steel' password. Though I don't test or use them, its just fun thing when I'm bored. On the other hand, if your password is "beer1985", than you deserve to get your password stolen! :lolflag:

CRAP
*quickly changes*

---

### Post by FuturePilot on 2008-01-10
I used Ethereal (what is now Wireshark) for a class. It is very powerful almost overwhelming at first. But it is good.
Funny story, we had a list of packet sniffers to choose from. I never heard of any of them so I just randomly picked one. Just so happens it was the only open source one on the list. :D

---

