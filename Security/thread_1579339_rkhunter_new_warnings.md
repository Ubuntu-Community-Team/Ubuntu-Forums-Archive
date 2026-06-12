---
title: "rkhunter new warnings?"
date: 2010-09-21
forum: Security
---

### Post by Crazedpsyc on 2010-09-21
I was just wondering why I suddenly got this: >      /usr/bin/dpkg                                            [ Warning ]     /usr/bin/dpkg-query                                      [ Warning ]  when I ran rkhunter? everything else was fine and clamav didn't find anything

---

### Post by OpSecShellshock on 2010-09-21
Both of those packages were recently updated. If rkhunter's expected hashes were not also updated prior to running it, then there would be a mismatch.

---

### Post by Crazedpsyc on 2010-09-21
Ok, thanks. I don't remember getting any updates... but oh well, i'll try updating it

---

### Post by Crazedpsyc on 2010-09-21
all clear after rkhunter --propupd! thanks

---

