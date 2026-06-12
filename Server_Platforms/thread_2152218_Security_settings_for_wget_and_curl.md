---
title: "Security settings for wget and curl"
date: 2013-06-07
forum: Server Platforms
---

### Post by goape on 2013-06-07
Hello,
I have one small issue with my 10.04 ubuntu server.
Whenever I try to use wget or curl, I am getting 404

richard@w1:~$ wget [www.google.com]("http://www.google.com")
--2013-06-07 10:53:03--  [http://www.google.com/](http://www.google.com/)
Resolving [www.google.com]("http://www.google.com")... 173.194.67.105, 173.194.67.99, 173.194.67.147, ...
Connecting to [www.google.com|173.194.67.105|:80]("http://www.google.com|173.194.67.105|:80")... connected.
HTTP request sent, awaiting response... 404 Not Found
2013-06-07 10:53:03 ERROR 404: Not Found.

richard@w1:~$ ping [www.google.com]("http://www.google.com")
PING [www.google.com]("http://www.google.com") (173.194.67.105) 56(84) bytes of data.
64 bytes from wi-in-f105.1e100.net (173.194.67.105): icmp_seq=1 ttl=48 time=8.72 ms
64 bytes from wi-in-f105.1e100.net (173.194.67.105): icmp_seq=2 ttl=48 time=8.40 ms

I am able to use wget and curl normally from another, identical server.

Which means, that problem is in configuration.


Any thoughts on this?
Thanks.

---

### Post by goape on 2013-06-07
Cha!
it was our IP forwarding :)

---

