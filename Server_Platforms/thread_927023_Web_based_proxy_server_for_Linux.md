---
title: "Web based proxy server for Linux"
date: 2008-09-22
forum: Server Platforms
---

### Post by jvincent08 on 2008-09-22
I was wondering if anyone knows of web based proxy servers for Linux. By "web based" I mean something like [this]("http://webproxiez.com/") or [this]("http://howlongtodeepfryaturkey.com/"), rather than a SOCKS proxy over SSH. I've been Googling for something like this all day, and all the results are for Squid which, as far as I know, is a different type of proxy all together (correct me if I'm wrong).

Any help would be greatly appreciated. Thanks in advance.

---

### Post by windependence on 2008-09-23
You are probably looking for a reverse proxy, which squid can do so you can surf around filters and other stuff. I did this once but I forgot how, but there are plenty of things on the net of you search for "squid reverse proxy".

-Tim

---

### Post by Dr Small on 2008-09-23
bblocked is a web-proxy written for Php:
[http://www.bblocked.org/](http://www.bblocked.org/)

---

### Post by jvincent08 on 2008-09-23
> **Dr Small said:**
> bblocked is a web-proxy written for Php:
[http://www.bblocked.org/](http://www.bblocked.org/)

Ahh, **that's** the type of thing I was looking for. Thanks a bunch! :D

---

### Post by jvincent08 on 2008-09-25
Well, does anyone else know of any others? Bblocked doesn't seem to handle javascript and cookies very well.

---

### Post by Dr Small on 2008-09-25
> **jvincent08 said:**
> Well, does anyone else know of any others? Bblocked doesn't seem to handle javascript and cookies very well.
I know there are others out there, but I don't remember any of their names. I have used various ones before, but that was the current one that I have on my server. Try looking around, I'm sure you'll find some.

Dr Small

---

### Post by greenhat.hackers on 2011-09-09
Do any one know about any other proxy servers except squid?

Please give suggesion?

---

### Post by lahirukannangara on 2011-09-09
> **jvincent08 said:**
> Well, does anyone else know of any others? Bblocked doesn't seem to handle javascript and cookies very well.

Try this one 
[http://sourceforge.net/projects/poxy/](http://sourceforge.net/projects/poxy/)

---

### Post by haqking on 2011-09-09
remote or local ?

Tor with Polipo i use [http://www.pps.jussieu.fr/~jch/software/polipo/]("http://www.pps.jussieu.fr/%7Ejch/software/polipo/")

or is that not what you are after ?

Edit: ahh just saw you meant web based ;-)

your mean like this [http://zend2.com/](http://zend2.com/)

---

### Post by dudumomo on 2011-09-12
In my case, I'm using [Glype](http://www.glype.com/) which is very easy to install and use but javascript doesn't really work (as always....)

---

### Post by Dangertux on 2011-09-13
If you don't want to use Squid, you probably won't want to use Apache, but it is capable of acting as a proxy if you want.

---

