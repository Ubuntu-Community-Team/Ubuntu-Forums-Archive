---
title: "hi do you install this"
date: 2009-06-18
forum: Security
---

### Post by Part Of What on 2009-06-18
hihow do you insta ll this?///http://www.torproject.org/docs/tor-doc-unix.html.en

---

### Post by nothingspecial on 2009-06-18
Go [[COLOR="Red"]here[/COLOR]]("https://wiki.torproject.org/noreply/TheOnionRouter/TorOnDebian") and follow the instructions

---

### Post by SuperSonic4 on 2009-06-18
Installing that from source is the silly way :p

See instructions here: [https://wiki.torproject.org/noreply/TheOnionRouter/TorOnDebian](https://wiki.torproject.org/noreply/TheOnionRouter/TorOnDebian)

-----
In a terminal (system -> administration -> terminal)

```
sudo nano /etc/apt/sources.list
```

To the bottom of the page append the following lines (shift+ins acts as paste)

```
  deb     http://mirror.noreply.org/pub/tor jaunty main
  deb-src http://mirror.noreply.org/pub/tor jaunty main
```

(or hardy/intrepid etc)

Verify the signiature with
```
sudo gpg --keyserver keys.gnupg.net --recv 94C09C7F && sudo gpg --fingerprint 94C09C7F && sudo gpg --export 94C09C7F | sudo apt-key add -
```

Update the database and install tor
```
sudo apt-get update && sudo apt-get install tor
```

---

### Post by nothingspecial on 2009-06-18
Sorry

See [[COLOR="Red"]here[/COLOR]]("https://help.ubuntu.com/community/TOR")

---

### Post by imlinux on 2009-06-18
is there anyway to configure squid proxy to use "tor ",instead of Privoxy or other way is squid to use privoxy and privoxy to use tor,i use squid server to local cache.

---

### Post by cdenley on 2009-06-19
> **imlinux said:**
> is there anyway to configure squid proxy to use "tor ",instead of Privoxy or other way is squid to use privoxy and privoxy to use tor,i use squid server to local cache.

As shown in the link before your last post, the typical setup with tor is to have privoxy go through tor.
[https://help.ubuntu.com/community/TOR#Configure%20Privoxy](https://help.ubuntu.com/community/TOR#Configure%20Privoxy)

Are you sure you understand what tor does and doesn't do?
[https://wiki.torproject.org/noreply/TheOnionRouter/TorFAQ#head-75d5f6d474527a80fc370d208252b4dfd2ea2efd](https://wiki.torproject.org/noreply/TheOnionRouter/TorFAQ#head-75d5f6d474527a80fc370d208252b4dfd2ea2efd)

---

### Post by epicoder on 2009-06-19
The easiest way is through the repositories:
```
sudo apt-get install tor
```

---

### Post by SuperSonic4 on 2009-06-20
> **sh228 said:**
> The easiest way is through the repositories:
```
sudo apt-get install tor
```

This is true if you want an outdated, largely unmaintained version

> Do not use the packages in ubuntu's universe. They are not maintained and most likely old and therefore miss out on stability and possibly security fixes.

Source: [https://wiki.torproject.org/noreply/TheOnionRouter/TorOnDebian](https://wiki.torproject.org/noreply/TheOnionRouter/TorOnDebian)

---

### Post by Part Of What on 2009-06-25
this :sudo gpg --keyserver keys.gnupg.net --recv 94C09C7F && sudo gpg --fingerprint 94C09C7F && sudo gpg --export 94C09C7F | sudo apt-key add -

---

### Post by Part Of What on 2009-06-25
> **SuperSonic4 said:**
> Installing that from source is the silly way :p
 
See instructions here: [https://wiki.torproject.org/noreply/TheOnionRouter/TorOnDebian](https://wiki.torproject.org/noreply/TheOnionRouter/TorOnDebian)
 
-----
In a terminal (system -> administration -> terminal)
 
```
sudo nano /etc/apt/sources.list
```
 
To the bottom of the page append the following lines (shift+ins acts as paste)
 
```
  deb     http://mirror.noreply.org/pub/tor jaunty main
  deb-src http://mirror.noreply.org/pub/tor jaunty main
```
 
(or hardy/intrepid etc)
 
Verify the signiature with
```
sudo gpg --keyserver keys.gnupg.net --recv 94C09C7F && sudo gpg --fingerprint 94C09C7F && sudo gpg --export 94C09C7F | sudo apt-key add -
```
 
Update the database and install tor
```
sudo apt-get update && sudo apt-get install tor
```
 
how do you open this to behave as proxy at the end?

---

