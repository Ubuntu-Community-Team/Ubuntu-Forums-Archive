---
title: "PPA/.deb for Muse 1.0?"
date: 2009-12-31
forum: Ubuntu Studio
---

### Post by gorgon on 2009-12-31
Hi all,

Just saw that [Muse]("http://muse-sequencer.org") has reached version 1.0 and wanted to give it a try - anyone know where there might be a PPA or .deb file of Muse 1.0 so I wont have to use the source?

cheers,

---

### Post by bluesscream on 2010-01-01
just compile it yourself. I hang at QTDIR. This was my solution: ```
export QTDIR=/usr/share/qt3 
```
[HTML]http://muse-sequencer.org/index.php/Cvs[/HTML]

---

### Post by blackcoatman on 2010-01-13
I have problems compiling it on Karmic. Specifically, even if i do "export QTDIR=/usr/share/qt3", while configuring i get:

```

checking for QT environment variable QTDIR... yes
checking for QT includes (/usr/share/qt3/include)... no
checking for QT libraries (/usr/share/qt3/lib)... no
checking for QT moc (/usr/share/qt3/bin/moc)... no
checking for QT uic (/usr/share/qt3/bin/uic)... no
configure: error: need qt >= 3.2.0

```

The above directories do exist. I don't know what is going wrong.

---

### Post by JC Cheloven on 2010-01-13
Here is a PPA for muse 1.0 and many other updated audio goodies.
[https://launchpad.net/~philip5/+archive/extra](https://launchpad.net/~philip5/+archive/extra)
Enjoy :-)

---

