---
title: "Installing WoW from scratch"
date: 2010-02-02
forum: Wine
---

### Post by PuK84 on 2010-02-02
Hi all,

Ok! have made the plunge and installed ubuntu on my main pc however I am coming across a bizarre issue with trying to install WoW. whenever I run Installer.exe I get the following message.

puk@PuK:~$ wineconsole World_of_Warcraft_\(Disc_1\)_iso/Installer.exe
fixme:ole:OleCreateStaticFromData (not shown), stub!

And in another window I get a message saying "Missing Symbol {LanguageCode}! (SymbolTable::UnMappedSymbolSubstitution)" 

The installer also opens a window saying that no installer data could be found. What am I doing wrong?

---

### Post by PuK84 on 2010-02-02
Whoops! sorry, I forgot to mention. wine version 1.1.37 and ubuntu 9.10

---

### Post by PuK84 on 2010-02-03
*sigh* nevermind. Turns out it doesn't like being mounted as an image. once I burned it to a CD it started up without issue

---

