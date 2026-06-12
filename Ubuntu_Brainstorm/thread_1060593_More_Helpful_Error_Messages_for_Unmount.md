---
title: "More Helpful Error Messages for Unmount"
date: 2009-02-04
forum: Ubuntu Brainstorm
---

### Post by PirateChef on 2009-02-04
Sometimes, when I try to unmount a USB drive or DVD, I get this message:

```
Cannot unmount volume
An application is preventing the volume from being unmounted.
```

Well, that's fine, but...*which* application?
It doesn't tell me that, so I have to just click around, closing stuff, until I find the right one.

Will this error message be more helpful in the future?
What can I do in the meantime to determine what applications are tying up my devices?

---

### Post by Ptero-4 on 2009-02-04
you might want to use lsof in the terminal. It lists open processes and might tell you what is tying your USB stick.

---

