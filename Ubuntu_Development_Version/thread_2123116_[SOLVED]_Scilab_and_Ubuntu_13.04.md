---
title: "[SOLVED] Scilab and Ubuntu 13.04"
date: 2013-03-07
forum: Ubuntu Development Version
---

### Post by gspe on 2013-03-07
[COLOR=#333333][FONT=Ubuntu Beta]I've just upgraded my 12.10 to 13.04. The only problem I have right now is with scilab.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]After the upgrade, scilab doesn't start correctly: the software starts but the graphics are strange, and I'm not able to move or resize the window and click on the menu.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]The problem is related to Ubuntu 13.04 because I've tried every version of scilab and all show the same problem.

Can someone point me in the right direction? Thanks[/FONT][/COLOR]

---

### Post by dino99 on 2013-03-07
you might try to find usefull warnings/errors logged inside ~/.xsession-errors & /var/log/
then report on launchpad (using : ubuntu-bug thatfaultypackage) to hope getting a fix.

or compile from sources:
[http://wiki.nosdigitais.teia.org.br/Scilab](http://wiki.nosdigitais.teia.org.br/Scilab)

---

### Post by gspe on 2013-03-07
Thank you for answer, but i haven't find any useful info inside log file.

---

### Post by gspe on 2013-03-09
After the last software update scilab works again.

---

