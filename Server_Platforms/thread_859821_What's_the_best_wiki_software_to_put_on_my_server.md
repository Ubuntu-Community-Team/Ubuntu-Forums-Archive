---
title: "What's the best wiki software to put on my server?"
date: 2008-07-14
forum: Server Platforms
---

### Post by indigoshift on 2008-07-14
I'm running a very modest little server here at home.  Mainly just for fun, but also because it's nice to have a file server--I'm often working on my Ubuntu laptop part of the day, and my Win XP desktop later the same day.  It's nice to have the important work documents all on one hard drive, accessible from any machine in the house.

I find that I'm in need of a wikipedia-like setup on the server, so I can edit certain documents in a browser from either computer.  I'm wondering if anyone here has any experience with doing this, and could suggest their favorites.

I'm not looking for a step-by-step "how to", per se.  Just some opinions.  I ran WikidPad on my XP box last year, but it wasn't quite what I was looking for.  That's pretty much the extent of my experience with anything wiki-related.

If there are any "gotchas" in running such a thing on an Ubuntu server, I'd appreciate knowing what those are, as well.  Seems like the Ubuntu community uses wikis quite a bit, so I figured this was the best place to ask.

Thanks in advance!

---

### Post by windependence on 2008-07-14
[http://twiki.org/](http://twiki.org/)

Pretty straight forward setup.

-Tim

---

### Post by wirelessmonkey on 2008-07-15
Um...MediaWiki? [www.mediawiki.org](www.mediawiki.org)

---

### Post by hyper_ch on 2008-07-15
mediawiki

---

### Post by jdavis on 2008-07-15
[MediaWiki]("http://mediawiki.org") is good for an all-round wiki that does everything you'll ever need, although it can be resource intensive and does require some configuration and occasional tweaking (also, I personally find Mediawiki a pain to upgrade)

[PMWiki]("http://pmwiki.org/") is much smaller, does not require a database and is much simpler to configure.

I use both of them on different sites, and they're both PHP so it depends on your usage really.

Jonathan

---

### Post by nanog on 2008-07-15
Mediawiki is far from a resource hog and stores wiki data in a very efficient manner. It is by far the most widely used wiki with na unparalleled range of plugins (it drives wikipedia).  The advantage of a database is that allows you to backup and restore a wiki very easily. I  lost an entire wiki install and was up and running again in 10 minutes!

Also, Open Office 3 has a new plugin that lets you design mediawiki pages in a WYSIWG (what you see is what you get format) format and save them as mediawiki markup. This allows you to build very sophisticated content without having to learn  esoteric wiki markup

Installation of mediawiki:

[https://help.ubuntu.com/8.04/serverguide/C/mediawiki.html](https://help.ubuntu.com/8.04/serverguide/C/mediawiki.html)

If you have not installed Apache:

```
sudo apt-get install apache2
```

To install Mysql:

[https://help.ubuntu.com/8.04/serverguide/C/mysql.html](https://help.ubuntu.com/8.04/serverguide/C/mysql.html)

---

### Post by davidshq on 2008-07-15
I use WikkaWikki, its very simple.
David.

---

### Post by songshu on 2008-07-17
another easy and simple one.

dokuwiki

i never tried to many others but i'm happy with what i got, you can check the link in my sig for an example

---

### Post by amenszer on 2008-07-17
Mediawiki is the bomb.com

---

### Post by hyper_ch on 2008-07-17
> **amenszer said:**
> Mediawiki is the bomb.com

and that is supposed to mean?

---

### Post by amenszer on 2008-07-17
That means its awesome. :)

---

### Post by indigoshift on 2008-07-22
> **nanog said:**
> Also, Open Office 3 has a new plugin that lets you design mediawiki pages in a WYSIWG (what you see is what you get format) format and save them as mediawiki markup. This allows you to build very sophisticated content without having to learn  esoteric wiki markup

I think I'm going with mediawiki, for this very reason.

Thanks to everyone for your input!

---

### Post by songshu on 2008-07-22
> **indigoshift said:**
> I think I'm going with mediawiki, for this very reason.

Thanks to everyone for your input!

the Hardy 2.4 version already has the "file""send" "to mediawiki"

so you don't need to wait or go Beta

---

