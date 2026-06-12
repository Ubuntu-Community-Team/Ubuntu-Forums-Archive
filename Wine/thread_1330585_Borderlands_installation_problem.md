---
title: "Borderlands installation problem"
date: 2009-11-18
forum: Wine
---

### Post by PowerSource on 2009-11-18
I've got an extremely legal copy of borderlands, and when i right click the file named "Borderlands.exe" on the disk, this pops up:
[IMG]http://upload.snelhest.org/images/091118borderlands_error.png[/IMG]

When i run the file using a command this error comes:
```

wine: could not load L"Z:\\media\\isoimage\\Borderlands.exe": Bad EXE format for

```

help?

---

### Post by beastrace91 on 2009-11-18
What Wine version are you using? Always be sure you have the [latest release](www.winehq.org/download/deb).

Regards,
~Jeff

---

### Post by PowerSource on 2009-11-19
doesn't wine update automatically?

---

### Post by PowerSource on 2009-11-19
i just installed the latest, but it still doesn't work :(

---

### Post by Xog on 2009-11-19
> **PowerSource said:**
> i just installed the latest, but it still doesn't work :(

terminal:
```
wine --version
```

---

### Post by beastrace91 on 2009-11-19
Also can you please post the output terminal gives when the installer crashes out? To do this run the setup.exe from your Borderlands disc by running ```
wine setup.exe
``` from your cd's directory in terminal.

Regards,
~Jeff

---

### Post by Falc7 on 2009-11-19
> **PowerSource said:**
> 
When i run the file using a command this error comes:
```

wine: could not load L"Z:\\media\\isoimage\\Borderlands.exe": Bad EXE format for

```


I also get this problem, with the same message
[http://img177.imageshack.us/i/wine.jpg/](http://img177.imageshack.us/i/wine.jpg/)

---

### Post by PowerSource on 2009-11-19
> **Xog said:**
> terminal:
```
wine --version
```

```
:~$ wine --version
wine-1.1.33

```

---

### Post by beastrace91 on 2009-11-19
> **PowerSource said:**
> I've got an extremely legal copy of borderlands

If this is the case can you try running the Borderlands.exe off of the actual CD instead of using a disc image? It really shouldn't matter but it cannot hurt to try (also IMO this is one of the many reason I like to get things through Steam hehehe) If that still does not work try couple [older Wine versions](http://wine.budgetdedicated.com/archive/index.htmlhttp://wine.budgetdedicated.com/archive/index.html) and see if they give you any luck.

@Flac7 - That screenshot you posted clearly proves that you torrented Borderlands (and didn't buy it). You have both a folder labeled "crack" open and there is "torrent" in the path to your ISO image :/ Please don't ask for help with stolen software.

Regards,
~Jeff

---

### Post by joeelmex on 2009-11-19
Owned

> **beastrace91 said:**
> 
@flac7 - that screenshot you posted clearly proves that you torrented borderlands (and didn't buy it). You have both a folder labeled "crack" open and there is "torrent" in the path to your iso image :/ please don't ask for help with stolen software.

Regards,
~jeff

---

### Post by psypher on 2009-11-20
try mounting the image without acetone. sudo mount path/to/iso /media/cdrom0 -o loop

---

