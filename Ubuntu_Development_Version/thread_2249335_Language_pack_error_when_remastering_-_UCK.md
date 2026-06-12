---
title: "Language pack error when remastering - UCK"
date: 2014-10-21
forum: Ubuntu Development Version
---

### Post by spsf2 on 2014-10-21
Using UCK - Ubuntu Customization Kit + latest ISO (oct-17)
I got these erros whenever I select any language to be installed:
Any help? TIA
```

Installing language packs (de en es pt)...
Reading package lists...
Building dependency tree...
Reading state information...
language-pack-de is already the newest version.
language-pack-de-base is already the newest version.
language-pack-en is already the newest version.
language-pack-en-base is already the newest version.
language-pack-es is already the newest version.
language-pack-es-base is already the newest version.
language-pack-pt is already the newest version.
language-pack-pt-base is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 language-pack-touch-de : Conflicts: language-pack-de but 1:14.10+20141014 is to be installed
 language-pack-touch-en : Conflicts: language-pack-en but 1:14.10+20141014 is to be installed
 language-pack-touch-es : Conflicts: language-pack-es but 1:14.10+20141014 is to be installed
 language-pack-touch-pt : Conflicts: language-pack-pt but 1:14.10+20141014 is to be installed
E: Unable to correct problems, you have held broken packages.
apt-get install language-pack-de language-pack-de-base language-pack-touch-de language-pack-en language-pack-en-base language-pack-touch-en language-pack-es language-pack-es-base language-pack-touch-es language-pack-pt language-pack-pt-base language-pack-touch-pt failed, error=100
Restoring kernel update state...

```

---

### Post by spsf2 on 2014-10-22
Problem persists with the latest oct-22 ISO...
Has anyone tested this?

---

### Post by fingerheroes on 2015-10-07
The answer is to bypass the first language prompt. Don't check ANYTHING on it. Then, check the language for the next two.

If that doesn't work, skip both the first AND second language prompts, and just do the third one.

---

