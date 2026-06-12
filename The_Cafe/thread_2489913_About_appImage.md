---
title: "About appImage"
date: 2023-08-14
forum: The Cafe
---

### Post by xinuzi on 2023-08-14
[Sorry that I am quite active here lately. Not my intention to take over the pub. It's just that, after a few recent installs and configurations, certain things caught my eye.]

appImage,

some write it AppImage, others Appimage, others appimage, others etc...

works a bit like windows .exe's

(could lead to similar security questions - but mostly okay...)

may have the advantage of being portable, transferable, storeable and the fact that it sometimes contains a more recent version of a software than available in the repositories or sth that is just not available.

Lubuntu is a modest ubuntu flavor, that we know.
After a recent installation of it, I was still surprised that appImage programs didn't function anymore.

A bit of stackexchanging and superusering brought the solution:

```
sudo apt install libfuse2*
```

So, if someone else encounters the same dilemma in the appImage context...

To name a few programs distributed in a nice appImage:

- [http://fixounet.free.fr/avidemux/download.html](http://fixounet.free.fr/avidemux/download.html) aka avidemux (ideal lightweight but still powerful gui for elementary video editing and converting)
- [https://crow-translate.github.io/](https://crow-translate.github.io/) aka Crow translate (uses google translate and a few other servers for quick, but still extensive and unlimited, translations in almost any language)
- [https://lmms.io/download#linux](https://lmms.io/download#linux) aka lmms (audio/music mixing software)
e.o.

[I'll leave the pub to go configure my woman now ;-) ]

---

