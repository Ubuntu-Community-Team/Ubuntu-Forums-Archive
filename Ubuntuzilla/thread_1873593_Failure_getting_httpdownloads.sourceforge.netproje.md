---
title: "Failure getting http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/..."
date: 2011-11-01
forum: Ubuntuzilla
---

### Post by Karlchen on 2011-11-01
Hello, nanotube.

For the past few days - might actually be longer than that, not sure - Synaptic keeps on returning this error when trying to update its software list:
```
Failure getting [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/all/Release.gpg](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/all/Release.gpg)
Something bad happened trying to resolve »:http« (-5 - No host matches this address.)
Failure getting [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/all/main/binary-i386/Packages.gz](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/all/main/binary-i386/Packages.gz)
Cannot connect to downloads.sourceforge.net:http :
```The Ubuntuzilla entry in the file /etc/apt/sources.list reads ```
deb [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt) all main
```Linux version: Lucid Lynx 10.04.3 Desktop 32-bit

Could there be something wrong on Sourceforge or should I look for errors in my apt configuration?

Kind regards,
Karl

---

### Post by Karlchen on 2011-11-02
Guess I can answer my own question by now:
Removing [the Ubuntuzilla entry]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Technical_Details") from the file /etc/apt/sources.list and re-adding it mysteriously fixed the error.
Mysteriously, because there was no obvious error in the file.

Anyway, adding [the same entry]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Technical_Details") on a second Ubuntu machine and telling Synaptic to update its package list worked flawlessly, too.

Case closed.

Karl

---

