---
title: "Install Program"
date: 2012-04-10
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Miykel on 2012-04-10
G'Day; Have a couple of problems, Im trying to install Shape Collage.gz,
What I've done so far;
  cd Downloads

[B][I][COLOR=#000080]tar xvzf pkg.tar.gz  That worked fine, ended up with folder  "Shape Collage"
Tried to cd folder Shape Collage but told "no such folder yet it shows up if I ls, any clues ??

Next instruction says to su but when I try to su and enter pass word told pass word verification failure  nay clues ??

Kind Regards Miykel
[/COLOR][/I][/B]

---

### Post by Toz on 2012-04-10
Here is what I did to get it to work:

1. uncompressed the file:
```
tar xzvf ShapeCollage-2.5.3.tar.gz
```

2. This created a "Shape Collage" folder. cd'd into it (don't know why this didn't work for you):
```
cd "Shape Collage"
```

3. ran the executable file:
```
./"Shape Collage"
```

No need for su. Which instructions are you following?

---

### Post by Miykel on 2012-04-11
Thanks for the reply Toz, I didn't know I had to use    "  "  when I did that it worked fine except now I need Java, always something  LOL.
OK. I got Java Run time installed and then the commands run ok but the Shape Collage will only run in the terminal, is this normal ???
Regards Miykel

---

