---
title: "texlive-latex (what is this for?)"
date: 2010-05-30
forum: Security
---

### Post by Lori700698 on 2010-05-30
ClamAV don't like this file, it's coming up as a virus, it appears to have installed this weekend since I've been messing with snort, base, & snortsam.

```
/usr/share/doc/texlive-latex-extra-doc/latex/eCards/eCardstst.pdf: 

```

I normally pay no attention to viruses (Ubuntu blessing) but I have found that when my system was compromised last year I had some infected files that were installed so I now I run ClamAV via cron job daily and email myself a report just to keep an eye on things.

I'm using this system as a server and I hate having programs installed that I have no need for, so my question is... what is this and can I get rid of it?  If I can toss it should I delete the file(s) or autoremove something?  Googlen didn't turn up enough information for me to read up on my own to make an informed decision.

Thanks Again
Lori

---

### Post by cariboo on 2010-05-31
From synaptic:

> The TeX Live software distribution offers a complete TeX system.
It encompasses programs for typesetting, previewing and printing
of TeX documents in many different languages, and a large collection
of TeX macros and font libraries.

This metapackage provides a decent selection of the TeX Live packages
which should suffice for the most common tasks.

The distribution also includes extensive general documentation about
TeX, as well as the documentation accompanying the included software
packages.

If you don't use it, you can safely get rid of it.

```
sudo apt-get purge texlive
```

---

