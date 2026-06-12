---
title: "Big problem with iso files"
date: 2008-10-12
forum: Ubuntu Studio
---

### Post by dj_ee3 on 2008-10-12
Hi, I have big problem with the iso files. The problem is that if for example I want to install program which is in two iso files. I mount the first one open it and installed everything is good so far. But, when the instalation reach the place where it has to change iso files for example at 52%  I have to unmouth the first iso file which can't happen and mouth iso two. There is not a problem in mouthing iso 2 but I can't unmouth iso 1 as I said. So the instalation things that if iso1 is still in the system than iso2 is not running so it ask me for disc 2 again and  I can't finish my instalation. I have several very important aplications that has instalation divided in two iso files. I need them very much and I need your help a lot. Thank you in advice. 

PP: I don't think the problem is from the aplications since I tried two different aplications.

---

### Post by iponeverything on 2008-10-13
What not combine the two iso's into one big one.

```

mkdir both-iso iso1 iso2
mount -o loop iso1.iso iso1
mount -o loop iso2.iso iso2
cp -av iso1/* iso2/* both-iso/
genisoimage -R -o both-iso.iso  both-iso

```

---

### Post by dj_ee3 on 2008-10-13
> **iponeverything said:**
> What not combine the two iso's into one big one.

```

mkdir both-iso iso1 iso2
mount -o loop iso1.iso iso1
mount -o loop iso2.iso iso2
cp -av iso1/* iso2/* both-iso/
genisoimage -R -o both-iso.iso  both-iso

```
I combine them but the instalation still wants it's second cd. I burn the images to discs but when it's time to change them ubuntu says that the disc is used right now so the disc doesn't come out and let me change it.

---

