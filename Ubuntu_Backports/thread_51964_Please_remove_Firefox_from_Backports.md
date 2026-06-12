---
title: "Please remove Firefox from Backports"
date: 2005-07-25
forum: Ubuntu Backports
---

### Post by Amaranth on 2005-07-25
As the title says, this is a request to remove firefox from backports. hoary-security has mozilla-firefox-1.0.6-0ubuntu0.1 which is the latest release of firefox. The backport is no longer needed. Also, the backport package is 'firefox' which provides 'mozilla-firefox' and the new version of mozilla-firefox causes conflicts between the two packages.

---

### Post by NeoChaosX on 2005-07-25
jdong just updated the Firefox backport to 1.0.6 as well. Just installed it, it's working fine.

---

### Post by Amaranth on 2005-07-25
[QUOTE=NeoChaosX]jdong just updated the Firefox backport to 1.0.6 as well. Just installed it, it's working fine.[/QUOTE]
 A user in #ubuntu just tried upgrading from the backports version to the hoary-security version (which is shown as newer) and they conflicted.

Plus, why have something in there that isn't needed? I'd certainly hope the devs would be happy to get rid of the burden that is a custom firefox.

---

### Post by NeoChaosX on 2005-07-25
What version did he try to upgrade from? 

And what I meant to say is that jdong promoted the Firefox 1.0.6 backport from staging to main, and that it upgrades over the hoary-security package just fine.

---

### Post by rpgcyco on 2005-07-26
But why have Firefox 1.0.6 is backports, if the full 1.0.6 (not 1.0.2 with patches) is in the official repos?

- Rpg Cyco

---

### Post by ephman on 2005-07-26
OH JEEZ,

i just updated because the little red dot appeared, and now i've totally lost all internet connectivity.  does this make any sense?  please help me...

ephman

---

### Post by jdong on 2005-07-26
Clearup:

When the hoary-security update first came out, the latest backports version was 1.0.4, which couldn't upgrade successfully to 1.0.6 hoary-security because of a Breezy packaging bug with the rename and not enough Conflicts: stanzas.

In addition, I had a couple users tell me that my Backports 1.0.6 crashes much less frequently (if at all) than the hoary-security version.


As a result, I decided to promote the Backports firefox 1.0.6 to stable, which is 'newer' than the hoary-security 1.0.6 and solved this problem.

---

### Post by rwabel on 2005-07-27
[QUOTE=jdong]Clearup:

When the hoary-security update first came out, the latest backports version was 1.0.4, which couldn't upgrade successfully to 1.0.6 hoary-security because of a Breezy packaging bug with the rename and not enough Conflicts: stanzas.

In addition, I had a couple users tell me that my Backports 1.0.6 crashes much less frequently (if at all) than the hoary-security version.


As a result, I decided to promote the Backports firefox 1.0.6 to stable, which is 'newer' than the hoary-security 1.0.6 and solved this problem.[/QUOTE]
 I can confirm the stability and it's newer than the hoary-security one. Didn't have conflict problems at all!

---

### Post by Toddy on 2005-07-28
Backport upgrade to FF 1.0.6 went smooth for me too...

---

