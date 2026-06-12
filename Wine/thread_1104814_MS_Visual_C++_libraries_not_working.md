---
title: "MS Visual C++ libraries not working"
date: 2009-03-24
forum: Wine
---

### Post by anlag on 2009-03-24
Trying to run my freshly bought and installed (through Steam) Football Manager 2009. However, I get an error relating to Visual C++ libraries. I think I installed these with winetricks previously, but attempting to do now or verify, produces errors.

```
anlag@casper:~/Downloads$ sh winetricks vcrun2005

(...)

Note: command 'wine /home/anlag/.winetrickscache/vcrun2005/vcredist_x86.exe' returned status 194.  Aborting.
```

The same happens for vcrun2005sp1, and vcrun2008. I've deleted the subfolders in ~/.winetrickscache, to no avail. Also, I tried entering the wine add/remove utility via the menu - and find VC2008 showing up once and VC2005 showing up twice. However, marking either of these and clicking to remove does nothing; it simply unmarks and scrolls back up to the top.

So, in short, does anyone know of a good way to remove/reinstall the Visual C++ libraries, since they seem to be rather broken on my wine installation?

Cheers.

---

### Post by secundar on 2009-05-19
I'm having the same problem but in conjunction with running other software (DAZ Studio).

---

### Post by slegrand on 2009-11-15
Yeah same. Has anyone found what the problem was?

---

