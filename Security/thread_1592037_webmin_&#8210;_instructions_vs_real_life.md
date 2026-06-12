---
title: "webmin &#8210; instructions vs real life"
date: 2010-10-10
forum: Security
---

### Post by engine on 2010-10-10
A certain popular magazine* says cheerfully "Once webmin's installed, launch your favourite browser and point it to [http://127.0.0.1:100000](http://127.0.0.1:100000). This will bring up the login screen."

Well, actually, no.

First approach
> 
[http://127.0.0.1:10000](http://127.0.0.1:10000)
Error - Bad Request
This web server is running in SSL mode. Try the URL [https://localhost:10000/](https://localhost:10000/) instead.

Second approach, obediently
> [https://localhost:10000/](https://localhost:10000/)
This Connection is Untrusted
You have asked Firefox to connect securely to localhost:10000, but we can't confirm that your connection is secure.

How does a poor simple user get to connect to his newly-installed webmin, then? Thanks in advance for any hints.

* I've been reading magazines from this publisher, on and off, since my Amiga days about twenty years ago. You know, I have yet to follow a single tutorial of theirs that actually works out of the box ...

---

### Post by Jeroensum on 2010-10-10
Maybe you should complain to ***THEM*** instead of posting something that's obviously wrong, ***HERE***.

Then again, I think you probably shouldn't be using webmin anyway since the thing has had more leaks then B.P. and should focus on doing things manually, that way you won't stay a poor simple user and become a "1337" and educated admin one day!

--cheers!

---

### Post by cariboo on 2010-10-10
Usually webmin is used on a remote headless server, so that really isn't an issue.

When I was playing with it, I always accessed it via:

https://<servername>:10000

I always alias the ip addresses of systems I access remotely to a name, in /etc/hosts, as I'm to lazy to type the ip address all the time:

```

cat /etc/hosts
192.168.1.225	alexis-maverick	# Added by NetworkManager
127.0.0.1	localhost.localdomain	localhost
127.0.1.1	alexis-maverick
192.168.1.250	willy
192.168.1.215	chilanko
192.168.1.240	likely
```

---

### Post by ikt on 2010-10-10
> **engine said:**
> How does a poor simple user get to connect to his newly-installed webmin, then? Thanks in advance for any hints.

Confirm the security certificate:

[http://ubuntuone.com/p/JXg/](http://ubuntuone.com/p/JXg/)

---

### Post by engine on 2010-11-04
> **Jeroensum said:**
> Maybe you should complain to ***THEM*** instead of posting something that's obviously wrong, ***HERE***.

It's a point of view ... but I'm looking for an answer <g>

---

### Post by engine on 2010-11-04
Thanks! clear instructions that worked &#8210; life (and especially computing) should have more of these.

---

### Post by CharlesA on 2010-11-04
Since the SSL certificate is self signed, you'll get the "invalid certificate" warning, just add an exception and you'll be fine.

---

