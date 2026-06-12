---
title: "Gimp+.dll Hell"
date: 2007-02-18
forum: Windows
---

### Post by FuturePilot on 2007-02-18
I solve one problem and run into another.:(  It seems that a .dll for Gimp has run away on me. Every time I try to start Gimp I get```
This application has failed to start because libexpat.dll was not found
``` I tried reinstalling but doesn't work. Where can I find this .dll?

---

### Post by erlyrisa on 2007-02-18
is libexpat a part of GTK+ ? - I think it is, maybe you could try re-installing that.

---

### Post by mand0 on 2007-02-20
I had the same problem.. I downloaded the missing .dll file from here and it worked:

[http://www.dll-files.com/dllindex/dll-files.shtml?libexpat](http://www.dll-files.com/dllindex/dll-files.shtml?libexpat)

---

### Post by FuturePilot on 2007-02-20
Thanks! What directory do I put it in though?

---

### Post by mand0 on 2007-02-20
Oh sorry.. forgot that important bit.  Add it to your windows/system32/ folder

---

### Post by FuturePilot on 2007-02-24
Thank you! Everything is working again:)

---

