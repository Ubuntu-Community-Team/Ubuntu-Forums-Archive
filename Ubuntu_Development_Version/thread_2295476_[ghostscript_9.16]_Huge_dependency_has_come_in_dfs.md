---
title: "[ghostscript 9.16] Huge dependency has come in dfsg~0-0ubuntu2 (current)"
date: 2015-09-19
forum: Ubuntu Development Version
---

### Post by tista on 2015-09-19
Greetings,

Today I've tried to upgrade whole Wily Gnome, then ```
libgs9-common
``` seems to need adding a lot of packages... :(

All I want to install lbgs9-common is to install gimp, gnome-document and gnome-sushi so, I won't add LaTeX environment though.

Launchpad discussion is here: [https://bugs.launchpad.net/ubuntu/+source/ghostscript/+bug/1449875]("https://bugs.launchpad.net/ubuntu/+source/ghostscript/+bug/1449875") 
I don't think current version's "heavy dependency" would be right decision...

Regards.

**EDIT #1**
Required packages (newly installed) here:
```

fonts-ipaexfont-gothic fonts-ipaexfont-mincho fonts-ipafont-gothic
  fonts-ipafont-mincho fonts-lmodern ghostscript latex-cjk-all
  latex-cjk-chinese latex-cjk-chinese-arphic-bkai00mp
  latex-cjk-chinese-arphic-bsmi00lp latex-cjk-chinese-arphic-gbsn00lp
  latex-cjk-chinese-arphic-gkai00mp latex-cjk-common latex-cjk-japanese
  latex-cjk-japanese-wadalab latex-cjk-korean latex-cjk-thai libpotrace0
  libptexenc1 libsynctex1 libtexlua52 libtexluajit2 libzzip-0-13 lmodern
  ps2eps tex-common texlive-base texlive-binaries texlive-font-utils
  texlive-lang-chinese texlive-lang-cjk texlive-lang-japanese
  texlive-lang-korean texlive-lang-other texlive-latex-base
  texlive-latex-base-doc
```

**EDIT #2**
Seems evince also depends on libgs9-common.

---

### Post by dino99 on 2015-09-19
got that madness packages list too, but cant find what force them as dependencies (maybe some compile dependencies left with the final package)
that update is very (too) heavy

---

### Post by Irihapeti on 2015-09-19
So it's not just me.... I got that, too.

In my case, I think libgs9 is a dependency of ghostscript which is a dependency of cups and hplip. I've had both cups and hplip installed for a while.

Recommends for the latest version of libgs9-common (as seen in Synaptic) shows texlive-lang-cjk. I guess that pulls in all the other Tex stuff.

---

### Post by dino99 on 2015-09-19
I've started to clean the room: installing that texlive-lang-cjk (with 'recommends' installed by default) also set texlive-lang-all, and the cascade is up & running then, and also tex & ruby

unsetting 'recommends' before upgrading libgs9-common is needing to avoid these unexpected dependencies (at least some of them). Hopes Till will propose an other lighter upgrade

---

### Post by Irihapeti on 2015-09-19
Does one of us need to file a bug report?

---

### Post by dino99 on 2015-09-19
> **Irihapeti said:**
> Does one of us need to file a bug report?

see the latests (#9+) comments
[https://bugs.launchpad.net/ubuntu/+source/ghostscript/+bug/1449875](https://bugs.launchpad.net/ubuntu/+source/ghostscript/+bug/1449875)

in short, its needed by 'eps', but this still is too invasise for all the non 'eps'; maybe a specific package for that case be a better choice.

---

### Post by mc4man on 2015-09-19
An apparently stupid bug fix. The recommend isn't 'translated' to the image seed so on a fresh install of 15.10 the bug would still exist for the few affected. 
The recommend should be changed to a suggest. (or some other resolution that doesn't force packages that the vast majority of users don't need.

---

### Post by harry332 on 2015-09-19
This bug is fixed now.
In the ghostscript version 9.16~dfsg~0-0ubuntu3:

> debian/rules: Demote texlive-lang-cjk from Recommends: to Suggests:     as it pulls in a large amount of unneeded packages (LP: #1449875).

---

### Post by tista on 2015-09-19
Greetings,

I now saw the proposed **dfsg~0-0ubuntu3** version on launchpad, too.

Hmm... They just only go back to the start point of fixing *true* bug. Unfortunately they didn't fix the EPS bug yet, but finally ton of unneeded packages dependency has gone...

Best Regards.

---

