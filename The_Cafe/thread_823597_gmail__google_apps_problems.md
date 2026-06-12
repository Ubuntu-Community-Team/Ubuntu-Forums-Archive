---
title: "gmail / google apps problems"
date: 2008-06-09
forum: The Cafe
---

### Post by hkgonra on 2008-06-09
Anybody else having MAJOR issues trying to access gmail or google apps this morning ?

---

### Post by jethro10 on 2008-06-09
Yes,
Me and I have some remote working colleagues, both of them are as well.

---

### Post by jimrz on 2008-06-09
no problem here using either

---

### Post by hkgonra on 2008-06-09
Just doing a google search is going slow for me now but any other site and my bandwidth tests look good.

[[IMG]http://www.speedtest.net/result/281839975.png[/IMG]](http://www.speedtest.net)

---

### Post by wdaniels on 2008-06-09
GMail has been fine for me so far, but Google searches have been troublesome and Adsense has some problem with the SSL certificate.

---

### Post by hkgonra on 2008-06-09
To make this more interesting this only seems to be happening on people using Comcast. 
All other sites pull up fine , so Comcast is of course laying the blame on google but none of my users are having problems if they use a different ISP. 

Here is what I get on ping. 

Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\hkgonra>ping pop.gmail.com

Pinging gmail-pop.l.google.com [209.85.163.109] with 32 bytes of data:

Reply from 209.85.163.109: bytes=32 time=35ms TTL=239
Request timed out.
Request timed out.
Request timed out.

Ping statistics for 209.85.163.109:
    Packets: Sent = 4, Received = 1, Lost = 3 (75% loss),
Approximate round trip times in milli-seconds:
    Minimum = 35ms, Maximum = 35ms, Average = 35ms

C:\Documents and Settings\hkgonra> ping pop.gmail.com

Pinging gmail-pop.l.google.com [209.85.163.109] with 32 bytes of data:

Request timed out.
Request timed out.
Request timed out.
Reply from 209.85.163.109: bytes=32 time=32ms TTL=239

Ping statistics for 209.85.163.109:
    Packets: Sent = 4, Received = 1, Lost = 3 (75% loss),
Approximate round trip times in milli-seconds:
    Minimum = 32ms, Maximum = 32ms, Average = 32ms

C:\Documents and Settings\hkgonra>ping smtp.gmail.com

Pinging gmail-smtp.l.google.com [209.85.163.109] with 32 bytes of data:

Request timed out.
Reply from 209.85.163.109: bytes=32 time=31ms TTL=239
Reply from 209.85.163.109: bytes=32 time=40ms TTL=239
Request timed out.

Ping statistics for 209.85.163.109:
    Packets: Sent = 4, Received = 2, Lost = 2 (50% loss),
Approximate round trip times in milli-seconds:
    Minimum = 31ms, Maximum = 40ms, Average = 35ms

C:\Documents and Settings\hkgonra>

---

### Post by hkgonra on 2008-06-09
Turns out it is a DNS issue between Comcast and Google. 
They are both aware of the problem.

---

