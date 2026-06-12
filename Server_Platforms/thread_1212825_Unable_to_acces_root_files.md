---
title: "Unable to acces root files"
date: 2009-07-14
forum: Server Platforms
---

### Post by florianderouck on 2009-07-14
Dear forum,

I may be having a real dumb question, but for some reason i can't figure it out myself. I just installed ubuntu hardy server, but for me to acces it properly i need to adjust some files, for example the /ect/network/interfaces file to gain a static IP-adres. 

For some reason both Vi and Nano just pop up a new document, as if the old one doesn't even exist. 

```
nano /ect/network/interfaces
```!(EDIT) (as root)

Can you help me acces the right document? What am i doing wrong here?

Thanks in advance,

Florian

---

### Post by dragos2 on 2009-07-14
> **florianderouck said:**
> Dear forum,

I may be having a real dumb question, but for some reason i can't figure it out myself. I just installed ubuntu hardy server, but for me to acces it properly i need to adjust some files, for example the /ect/network/interfaces file to gain a static IP-adres. 

For some reason both Vi and Nano just pop up a new document, as if the old one doesn't even exist. 

```
nano /ect/network/interafaces
``` (as root)

Can you help me acces the right document? What am i doing wrong here?

Thanks in advance,

Florian


```
interafaces
```

---

### Post by windependence on 2009-07-14
Well that's certainly part of it, but you need sudo too if you want to edit those files. :-)

```
sudo nano /etc/network/interfaces
```-Tim

---

### Post by florianderouck on 2009-07-14
Seriously guys, i'm not kidding. Yes i was root when i did it. And yes it was written correctly. I have no idea what I'm doing wrong.

---

### Post by lisati on 2009-07-14
> **florianderouck said:**
> Seriously guys, i'm not kidding. Yes i was root when i did it. And yes it was written correctly. I have no idea what I'm doing wrong.

Note based on thumbnail: that should be "etc" (as in the latin words *et cetera*, remember Yul Brunner in "[The King and I]("http://www.imdb.com/title/tt0049408/")"?), not "ect" (as in [Electro Convulsive Therapy]("http://en.wikipedia.org/wiki/Electroconvulsive_therapy"), a.k.a. "[shock treatment]("http://www.imdb.com/title/tt0083067/")")

---

### Post by windependence on 2009-07-14
Hehe, I didn't catch that one either.

-Tim

---

### Post by florianderouck on 2009-07-14
Well that proves it, im retarded. 
I apologize for the waste of time i caused.

A humiliated Florian

SOLVED!

---

### Post by windependence on 2009-07-14
Don't feel bad, this happens to me all the time. The thing is, in the future, you'll know exactly what is wrong when it happens. It's the best way to learn IMHO.

-Tim

---

### Post by lisati on 2009-07-14
> **florianderouck said:**
> Well that proves it, im retarded. 
I apologize for the waste of time i caused.

A humiliated Florian

SOLVED!

Nah, don't be too hard on yourself! Typos happen!

---

