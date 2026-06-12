---
title: "Samba transfer speeds slow on HP proliant dl160 g6"
date: 2016-01-09
forum: Server Platforms
---

### Post by Magnus_Forsblom on 2016-01-09
Hi , does anyone know why my samba transfer speeds are so slow(11mb/s) when transferring from my main pc to my server(both have 1gb network card and are connected to the same router). Expected a bit more from a server with a Intel Xeon inside. Is it a software problem or what? My ftp speeds are slow as well.
Any help appreciated!

---

### Post by darkod on 2016-01-09
First obvious question: Are all your router ports 1Gb? Because 11MB/s is exactly what a 100Mb connection would give you... And the cables you are using are at least Cat5E to support 1Gb.

If it's not that, you might need some tweaking of samba, but I'm no expert on that. My samba copies quite good without any tweaking or anything... It also depends on raid level you are using (if any), etc, but you should be able to beat 11MB/s in most cases regardless of configuration.

---

### Post by Magnus_Forsblom on 2016-01-09
Lol I tried it with the cable that came with the router and now i'm getting 80mbs thanks so much!

---

