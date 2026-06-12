---
title: "Old-fashioned Swedish sort rules. Where can I report it?"
date: 2014-01-31
forum: Ubuntu Translations
---

### Post by kjellahl on 2014-01-31
Traditionally w has been considered equivalent to v when sorting Swedish text strings (like Umlaut vowels in German). Since a couple of years this sort rule has changed. Now w is considered a full-blown letter, sorted right after v, like in English.

Ubuntu 13.10 with LANG=sv_SE.UTF-8 sorts according to the old rule.
Where can I report this old-fashioned behaviour? It should be changed.

I guess this is a very unusual type of change. The rule changed with the 13th edition of *Svenska Akademiens ordlista* (SAOL), published 2006.
See e.g. [http://sv.wikipedia.org/wiki/Svenska_Akademiens_ordlista_%C3%B6ver_svenska_spr%C3%A5ket](http://sv.wikipedia.org/wiki/Svenska_Akademiens_ordlista_%C3%B6ver_svenska_spr%C3%A5ket)

---

### Post by kjellahl on 2014-02-06
Now I have checked also in *Svenska skrivregler*, 3rd edition, ISBN 978-91-47-08460-9. The situation is not as clear-cut as I thought. There are two recommendations to choose from. Either sort w together with v as has been done for a long time in Sweden, or sort w after v as in most languages that use the Latin alphabet. Just be consistent in each alphabetically sorted list.

Considering this dual recommendation, it's not (yet) time to ask for a change in Ubuntu. I think, though, that the right place to file such a request would be in Launchpad, [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu).

---

