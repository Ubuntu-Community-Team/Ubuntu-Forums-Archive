---
title: "my scariest terminal moment ever..."
date: 2009-01-12
forum: The Cafe
---

### Post by kyalee on 2009-01-12
I've been trying to increase my terminal-fu and last night I was playing with regular expressions and the rename command.

Did you know that

```
rename -n "s/t//g" /*
```

yields

```
/boot renamed as /boo
/etc renamed as /ec
/initrd.img renamed as /inird.img
/initrd.img.old renamed as /inird.img.old
/lost+found renamed as /los+found
/mnt renamed as /mn
/opt renamed as /op
/root renamed as /roo
/tmp renamed as /mp

```

I'm guessing that the system wouldn't have allowed me to do that for real (or would have at least made me log in as root before I did something that stupid) but still. Thank goodness for the no action flag. :lolflag:

---

### Post by JillSwift on 2009-01-12
> **kyalee said:**
> Thank goodness for the no action flag.
Hip Hip to that! -n has saved my bacon repeatedly.

---

### Post by neil_kelli on 2009-01-12
Wow, I don't have any idea what you just said  lol

---

### Post by kyalee on 2009-01-12
> **JillSwift said:**
> Hip Hip to that! -n has saved my bacon repeatedly.

*nods* I panic a little when I run rename without using it first. Not that I've screwed up yet, but I like to keep myself in the habit of putting that little -n in there first every time. Just in case. *g*

---

