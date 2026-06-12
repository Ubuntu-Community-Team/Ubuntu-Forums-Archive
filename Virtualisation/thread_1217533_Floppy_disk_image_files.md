---
title: "Floppy disk image files"
date: 2009-07-19
forum: Virtualisation
---

### Post by Zelandeth on 2009-07-19
This seems to me to be a very silly question...but it's one which I can't seem to find an answer to!

Trying to set up a VM to run Windows 3.1, as I've a bunch of software from that era I'd like to play around with in its native environment - simply because I can!

However, VB refuses to talk directly to my floppy drive (it's a USB affair, so that may well be something to do with that - the internal one got ousted in favour of the Zip drive which I actually use sometimes - and I lack a spare 3.5" drive bay).

No problem I think - I'll just make image files of the floppies in question and load them in...except for the question of how on earth do I make a floppy into a .IMG file?

I've hunted around and can't honestly find any utilities to do this...

Okay...rephrasing that slightly, I can't find any utilities which work properly from within Ubuntu which do that.  Winimage refuses to talk to my USB floppy drive via WINE.

Can anyone point me in the right direction?

---

### Post by Cheesemill on 2009-07-20
I'm pretty sure you can just use dd:

```
dd if=/dev/floppy of=floppy.img
```

Obviously changing /dev/floppy as required.

---

