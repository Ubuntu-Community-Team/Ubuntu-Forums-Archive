---
title: "Im new with Linux servers, now question about nmap ?"
date: 2011-10-24
forum: Security
---

### Post by jaho22 on 2011-10-24
I have ubuntu 10.04 desktop as a server.

if i at my home computer try 'nmap -v -A MY_IP'.

then it shows that my ports 22 and 80 are open, i havent that much of set my server yet.

why there is also 

PORT    STATE    SERVICE      VERSION
22/tcp  open     ssh          OpenSSH 5.3p1 Debian 3ubuntu7 (protocol 2.0)
|  ssh-hostkey: 1024 0:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00 (DSA)
|_ 2048 00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00 (RSA)

i set the values to 00 to not show my ssh-keys.

why my ssh-key values are visible by default, and how to hide them ?

does it currently meen that anyone can use my server after nmap search ?

---

### Post by Dangertux on 2011-10-24
> **jaho22 said:**
> I have ubuntu 10.04 desktop as a server.

if i at my home computer try 'nmap -v -A MY_IP'.

then it shows that my ports 22 and 80 are open, i havent that much of set my server yet.

why there is also 

PORT    STATE    SERVICE      VERSION
22/tcp  open     ssh          OpenSSH 5.3p1 Debian 3ubuntu7 (protocol 2.0)
|  ssh-hostkey: 1024 0:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00 (DSA)
|_ 2048 00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00 (RSA)

i set the values to 00 to not show my ssh-keys.

why my ssh-key values are visible by default, and how to hide them ?

does it currently meen that anyone can use my server after nmap search ?

That's just your servers public key, there is no need to hide it.

---

### Post by Lars Noodén on 2011-10-24
> **Dangertux said:**
> That's just your servers public key, there is no need to hide it.

You can also use [ssh-keyscan](http://manpages.ubuntu.com/manpages/oneiric/en/man1/ssh-keyscan.1.html) to see your server's public key.

```

ssh-keyscan -t rsa MY_IP

```

---

### Post by Lars Noodén on 2011-10-25
You can use [ssh-keygen](http://manpages.ubuntu.com/manpages/oneiric/en/man1/ssh-keygen.1.html) to see the public key's fingerprint.

```

ssh-keyscan -t rsa MY_IP > /tmp/x
ssh-keygen -lf /tmp/x

```

Does that look familiar?

---

