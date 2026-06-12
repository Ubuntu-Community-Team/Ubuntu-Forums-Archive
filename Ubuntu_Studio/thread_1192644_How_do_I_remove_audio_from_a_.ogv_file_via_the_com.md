---
title: "How do I remove audio from a .ogv file via the command line?"
date: 2009-06-20
forum: Ubuntu Studio
---

### Post by Rytron on 2009-06-20
Hi.
I can remove audio from an flv file with this command:
ffmpeg -i input.flv -an -vcodec copy output.flv

How do I remove audio from a .ogv file via the command line? I don't mind if ffmpeg of mencoder is used.

Edit: I used VFFF to remove audio from a .ogv file. A command line method would still be appreciated though.

---

### Post by exit3219 on 2010-11-10
oggSplit in the oggvideotools package did the trick for me.

---

### Post by GendeDios on 2010-11-10
KMediaGrab

```
mencoder file.ogv -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=800 -nosound -o file.mpeg
```

---

### Post by Rytron on 2010-11-11
Awesome. Thank you both  exit3219 & GendeDios. :P

---

