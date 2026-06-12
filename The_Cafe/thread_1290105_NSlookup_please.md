---
title: "NSlookup please?"
date: 2009-10-13
forum: The Cafe
---

### Post by kevin11951 on 2009-10-13
Can someone outside my router (that would be all of you I hope :)) run "nslookup www.kviero.com" and then "nslookup kviero.com"  and post the results?  I am trying to setup my own dns server for my domain, and want to see if I got it right yet...

---

### Post by wojox on 2009-10-13
[www.kviero.com](www.kviero.com)
```

Server:		68.87.74.166
Address:	68.87.74.166#53

Non-authoritative answer:
Name:	www.kviero.com
Address: 192.168.2.3
Name:	www.kviero.com
Address: 192.168.2.2
```

kviero.com
```

Server:		68.87.74.166
Address:	68.87.74.166#53

Non-authoritative answer:
Name:	kviero.com
Address: 192.168.2.2
Name:	kviero.com
Address: 192.168.2.3

```

---

### Post by kevin11951 on 2009-10-13
> **wojox said:**
> [www.kviero.com](www.kviero.com)
```

Server:		68.87.74.166
Address:	68.87.74.166#53

Non-authoritative answer:
Name:	www.kviero.com
Address: 192.168.2.3
Name:	www.kviero.com
Address: 192.168.2.2
```

kviero.com
```

Server:		68.87.74.166
Address:	68.87.74.166#53

Non-authoritative answer:
Name:	kviero.com
Address: 192.168.2.2
Name:	kviero.com
Address: 192.168.2.3

```

Yup, its setup right, but that brings up a question.  Why do you see my internal ip addresses for my servers?

---

### Post by wojox on 2009-10-13
[http://www.oreillynet.com/pub/a/network/excerpt/dnsbindcook_ch07/](http://www.oreillynet.com/pub/a/network/excerpt/dnsbindcook_ch07/)

Scroll down to the bottom for Authorative

---

