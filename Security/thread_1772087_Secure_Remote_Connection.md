---
title: "Secure Remote Connection"
date: 2011-05-31
forum: Security
---

### Post by doctortonic on 2011-05-31
I wish to install a remote server up, for controling my machine, it would be nice to have something like VNC / Team Viewer and ssh, but I don't trust ssh/vnc/team so mutch after seeing this movie:

[http://www.youtube.com/watch?v=IdYUJUoRNIA&NR=1]("http://www.youtube.com/watch?v=IdYUJUoRNIA&NR=1")

Any sugestion? Shoud I change the ssh remote port to smtg like 61982 instead of 22?

---

### Post by sj1410 on 2011-05-31
use RSA key based authentication and you can also use port knocking to secure your ssh port.

---

### Post by Lars Noodén on 2011-05-31
> **sj1410 said:**
> use RSA key based authentication ...

+1 for key-based authentication.  

For the [port knocking](http://www.linux.com/archive/feed/37888), it may be fun, but it's not worth anything.

---

### Post by sj1410 on 2011-05-31
you can also use a vpn connection to connect to your server, openvpn is a good choice

---

### Post by spynappels on 2011-05-31
Using a challenge passphrase which is formulated the same way as a strong password to secure the key will add another layer of security.

While it will not completely secure against a stolen key being used to access a server, it will buy some time to revoke the certificate of the key and disable it.

For any very sensitive servers, I tend to create 2 keypairs, one for normal use with a strong passphrase, and one for use only to access a server to revoke my working key, secured with an insane password. The "revocation" key is placed on a hardware encrypted USB drive, and the passphrase is encrypted and placed on a different hardware encrypted USB drive. The two drives are stored in different (secure) locations.

Still not perfect, but as good as I can get it.

---

### Post by HermanAB on 2011-06-01
Howdy,

SSH is pretty secure.  There is a reason why all the big data centres use it for everything.  I have used it on thousands of machines and have never had a compromise over 15 years (cross fingers).

The secret to security is three fold:
1. Use keys where possible.
2. Use loooooooooong passwords for all accounts.
3. Limit the effectiveness of brute forcers in some way (either by restricting the IP range, or by using the iptables limit rule to slow down attackers).

```
# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 30/minute --limit-burst 5 -j ACCEPT
```

---

### Post by Thewhistlingwind on 2011-06-01
While that great example of PWNage was quite entertaining, PDF readers have started using sandboxing, and what does this have to do with SSH? You worried about ophcrack?

---

