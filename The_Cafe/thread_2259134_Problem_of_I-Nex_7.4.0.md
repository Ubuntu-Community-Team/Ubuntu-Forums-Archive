---
title: "Problem of I-Nex 7.4.0"
date: 2015-01-02
forum: The Cafe
---

### Post by bytr on 2015-01-02
Happy New Year folks.
I hope you all have a wonderful year.

By the way, stable builds of I-Nex 7.4.0 has a problem of unmet dependencies on Ubuntu, and cannot install from its package or PPA.

[ATTACH=CONFIG]258948[/ATTACH]

To avoid this problem, require the repository of Gambas:
```
sudo apt-add-repository ppa:gambas-team/gambas3 && sudo apt-get update

```

---

