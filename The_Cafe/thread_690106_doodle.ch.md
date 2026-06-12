---
title: "doodle.ch"
date: 2008-02-07
forum: The Cafe
---

### Post by hyper_ch on 2008-02-07
Hiho

Anyone can currently access [http://www.doodle.ch](http://www.doodle.ch) ?

I just a no connection error.

---

### Post by frup on 2008-02-07
I can access it from New Zealand. Try a proxy.

---

### Post by hyper_ch on 2008-02-07
What's the IP for you? It tries for me to ping to:  80.74.151.79

---

### Post by popch on 2008-02-07
NSLookup says:

Nicht autorisierte Antwort:
Name:    [www.doodle.ch](www.doodle.ch)
Address:  80.74.151.79

The browser will open the page without problem if accessed as [http://www.doodle.ch](http://www.doodle.ch) but will require authentication if accessed by IP address.

I live in Switzerland.

---

### Post by frup on 2008-02-07
This is my output from ping if it isn't working for you, sorry for the delay been doing a few things
> 
~$ ping -c 5 doodle.ch
PING doodle.ch (80.74.151.79) 56(84) bytes of data.
64 bytes from doodle.ch (80.74.151.79): icmp_seq=1 ttl=37 time=358 ms
64 bytes from doodle.ch (80.74.151.79): icmp_seq=2 ttl=37 time=358 ms
64 bytes from doodle.ch (80.74.151.79): icmp_seq=3 ttl=37 time=362 ms
64 bytes from doodle.ch (80.74.151.79): icmp_seq=4 ttl=37 time=354 ms

--- doodle.ch ping statistics ---
5 packets transmitted, 4 received, 20% packet loss, time 3998ms
rtt min/avg/max/mdev = 354.717/358.427/362.263/2.767 ms


---

### Post by WorldTripping on 2008-02-07
> **popch said:**
> 

The browser will open the page without problem if accessed as [http://www.doodle.ch](http://www.doodle.ch) but will require authentication if accessed by IP address.



I get exactly the same, and I'm in the UK.

---

### Post by xyz on 2008-02-07
OK here.

---

### Post by hyper_ch on 2008-02-07
sorry to respond this late :)

This was really strange... some domains worked, others not at all... pining to the IP didn't also work...

I have a server in Germany and a friend has also one at the same host. I could not connect to my server anymore but I could connect to my friend's server. When I sshed from my work to my home computer and tried to connect from there (with lynx) I could access my server... really strange.

---

