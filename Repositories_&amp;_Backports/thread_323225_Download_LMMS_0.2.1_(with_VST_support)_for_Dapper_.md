---
title: "Download LMMS 0.2.1 (with VST support) for Dapper HERE!"
date: 2006-12-21
forum: Repositories &amp; Backports
---

### Post by megamaced on 2006-12-21
I've built an LMMS 0.2.1 package that includes VST support. The older 0.1.2 package in the ubuntu repositories doesn't have VST.

You need to install the following to resolve dependencies:

```
sudo aptitude install jackd libjack0.100.0-0 libmikmod2 libsdl-sound1.2 libsmpeg0 wine
```

Download [LMMS here]("http://www.zshare.net/download/lmms_0-2-1-1_i386-deb.html")

Install it by typing:

```
sudo dpkg -i lmms_0-2-1-1_i386-deb
```

WARNING: This package is for Dapper only. It is completely untested on Edgy! Please reports bugs etc

---

### Post by lofiye on 2006-12-24
Thank you so much for this new LMMS package!  I yet have to test VST support, but so far it runs fairly well (on edgy). However, LMMS tends to react very erratic at some times. Sometimes it just takes a sec to do a certain thing (like dragging a sample.. enter/delete a not and such) along with audio hickups if i'd a pattern of song at that moment. However, playing a pattern or song is rock solid if i don't try to do anything else within LMMS. I'am not sure if this is normal LMMS behaviour (as it's still under heavy development). Do you experience the same behaviour? If you don't understand what i mean, i'll try to explain it more precisely :D It's not as awful as it might sound...just a tad annoying :D I can work with this version of LMMS! I'll copy over my samples and a few VST's right after xmas.

Keep up the good work and thanks a million!

---

### Post by megamaced on 2006-12-24
Well I built it on Dapper, for Dapper. As I said I haven't tested it on Edgy systems yet, but suffice to say it runs perfectly on Dapper. I certainly don't experience the lag that you are getting with LMMS.

PS. Glad you enjoyed the package :)

---

### Post by DirtDawg on 2007-05-06
Thank you. Repo version never worked. This one did. :)

---

