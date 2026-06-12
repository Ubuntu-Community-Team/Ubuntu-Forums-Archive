---
title: "Nslookup one more time please..."
date: 2009-10-15
forum: The Cafe
---

### Post by kevin11951 on 2009-10-15
I am sorry I have to keep doing this, but I have no other way to test my dns server...

nslookup kviero.com
nslookup [www.kviero.com](www.kviero.com)

and visit both in a web browser if they work in nslookup (there is nothing there, so its not like I am just trying to get people to visit my site :))

---

### Post by Sam on 2009-10-15
```
$ nslookup kviero.com
Server:		192.168.1.1
Address:	192.168.1.1#53

Non-authoritative answer:
Name:	kviero.com
Address: 192.168.2.2

$ nslookup www.kviero.com
Server:		192.168.1.1
Address:	192.168.1.1#53

Non-authoritative answer:
Name:	www.kviero.com
Address: 192.168.2.2
```

Both doesn't work at all...

---

### Post by kevin11951 on 2009-10-15
> **Sam said:**
> ```
$ nslookup kviero.com
Server:		192.168.1.1
Address:	192.168.1.1#53

Non-authoritative answer:
Name:	kviero.com
Address: 192.168.2.2

$ nslookup www.kviero.com
Server:		192.168.1.1
Address:	192.168.1.1#53

Non-authoritative answer:
Name:	www.kviero.com
Address: 192.168.2.2
```

Both doesn't work at all...

I am so confused!!!  Its so weird, if i use random proxys to try to test it, a few will work, then a few wont...  I dont get it!

---

### Post by JillSwift on 2009-10-15
OpenDNS has your address on either the phishing or adware block list.

```
~$ nslookup kviero.com
Server:        192.168.0.1
Address:    192.168.0.1#53

Non-authoritative answer:
Name:    kviero.com
Address: 208.67.219.131

~$ nslookup www.kviero.com
Server:        192.168.0.1
Address:    192.168.0.1#53

Non-authoritative answer:
Name:    www.kviero.com
Address: 208.67.219.131

~$ host 208.67.219.131
131.219.67.208.in-addr.arpa domain name pointer [COLOR=Red]hit-block.opendns.com[/COLOR].

```

---

### Post by kevin11951 on 2009-10-15
> **JillSwift said:**
> OpenDNS has your address on either the phishing or adware block list.

```
~$ nslookup kviero.com
Server:        192.168.0.1
Address:    192.168.0.1#53

Non-authoritative answer:
Name:    kviero.com
Address: 208.67.219.131

~$ nslookup www.kviero.com
Server:        192.168.0.1
Address:    192.168.0.1#53

Non-authoritative answer:
Name:    www.kviero.com
Address: 208.67.219.131

~$ host 208.67.219.131
131.219.67.208.in-addr.arpa domain name pointer [COLOR=Red]hit-block.opendns.com[/COLOR].

```

Under opendns, do you have "*Block internal IP addresses*" enabled?  Its under advanced settings.

---

### Post by JillSwift on 2009-10-15
> **kevin11951 said:**
> Under opendns, do you have "*Block internal IP addresses*" enabled?  Its under advanced settings.
YupIdo.

---

### Post by kevin11951 on 2009-10-15
> **JillSwift said:**
> YupIdo.

Well, then.  That explains it.

---

### Post by JillSwift on 2009-10-15
> **kevin11951 said:**
> Well, then.  That explains it.
Yus It Duz.

---

