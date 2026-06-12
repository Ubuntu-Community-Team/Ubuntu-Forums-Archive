---
title: "Nautilus actions scripts ???"
date: 2013-02-26
forum: Ubuntu Development Version
---

### Post by stinkeye on 2013-02-26
I added the [**_[COLOR="DarkRed"]Nautilus Actions Extra ppa[/COLOR]_**]("https://launchpad.net/~nae-team/+archive/ppa") and installed
**nautilus-open-terminal-here** and **nautilus-open-as-root**
but they don't show in nautilus.

Do theses not work anymore?

---

### Post by ft_ on 2013-02-26
the first one exists in the official repos and works ok.

---

### Post by stinkeye on 2013-02-26
Ok, thanks.
Found the **nautilus-open-terminal** package, and it works.
Any open-as-root package?
Do nautilus scripts still work?
Would prefer it in the main menu though.

---

### Post by mc4man on 2013-02-26
You should consider filing a bug on the Dr.'s ppa, he's fairly receptive to issues.
It would appear that some, at least the 2 mentioned, of his python-extension scripts will not function atm.
If after logging in with one or more installed check ~/.xsession-errors for some python2.7 error messages

---

