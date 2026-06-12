---
title: "Glitch with RB in ricotz"
date: 2013-04-08
forum: Ubuntu Development Version
---

### Post by zika on 2013-04-08
```
Unpacking librhythmbox-core7 (from .../librhythmbox-core7_2.99-0ubuntu1~raring1_amd64.deb) ...dpkg: error processing /var/cache/apt/archives/librhythmbox-core7_2.99-0ubuntu1~raring1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/librhythmbox-core.so.7.0.0', which is also in package librhythmbox-core6 2.98+git20130321.e2f0ebe7-0ubuntu1~13.04~ricotz0
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/librhythmbox-core7_2.99-0ubuntu1~raring1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Update&#8321;: With a bit tinkernig, removed librhythmbox-core6 and rest was easy...

---

### Post by jcouse1 on 2013-04-08
Can you elaborate?  I'm having the same problem and I'm hoping to resolve it.

---

### Post by VinDSL on 2013-04-08
> **jcouse1 said:**
> Can you elaborate?  I'm having the same problem and I'm hoping to resolve it.
Don't know what zika did, but...

Here's what I did:
[LIST=1]
[*]Removed librhythmbox-core6 (this removed several other rhythmbox items, too)
[*]Installed librhythmbox-core7
[*]Installed rhythmbox 2.99 (this installed items that were removed in step 1, also)
[/LIST]

Seems to have fixed the problem for me...  ;)

---

### Post by jcouse1 on 2013-04-08
> **VinDSL said:**
> Don't know what zika did, but...

Here's what I did:
[LIST=1]
[*]Removed librhythmbox-core6 (this removed several other rhythmbox items, too) 
[*]Installed librhythmbox-core7 
[*]Installed rhythmbox 2.99 (this installed items that were removed in step 1, also) 
[/LIST]

Seems to have fixed the problem for me...  ;)
  
Thank you! this worked for me too.

---

### Post by VinDSL on 2013-04-08
> **jcouse1 said:**
> Thank you! this worked for me too.
Welcome!

You know... I haven't cracked open RB in ages.

Been playing around with VLC lately, using it to play music, radio, podcasts, et cetera, but...

RB 2.99 doesn't look half-bad, IMO.  Think I'll play around with it, for a while.

---

### Post by zika on 2013-04-09
Sorry, I was sleeping but I can see You managed to sort this out withot any help of mine... Youth vs. geezer sleeping... ;)

---

### Post by QDR06VV9 on 2013-04-09
> **zika said:**
> Sorry, I was sleeping but I can see You managed to sort this out withot any help of mine... Youth vs. geezer sleeping... ;)

I can Relate zika (geezer sleeping) LOL
Oh the Golden Years!!   (More like Lead)

---

### Post by jcouse1 on 2013-04-09
> **VinDSL said:**
> Welcome!

You know... I haven't cracked open RB in ages.

Been playing around with VLC lately, using it to play music, radio, podcasts, et cetera, but...
and I 
RB 2.99 doesn't look half-bad, IMO.  Think I'll play around with it, for a while.


I'm fairly new to ubuntu but as a convert from Mac OSX I've found rhythmbox a more than capable replacement for Itunes.  I tried out Clementine, Amarok and Banshee but Rhythmbox handles large libraries the best.

---

