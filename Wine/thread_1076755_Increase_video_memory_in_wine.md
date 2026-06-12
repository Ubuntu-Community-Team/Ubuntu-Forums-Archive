---
title: "Increase video memory in wine"
date: 2009-02-21
forum: Wine
---

### Post by ubudog on 2009-02-21
How do I increase video memory in wine?

---

### Post by kostkon on 2009-02-21
Open a terminal, give
```
wine regedit.exe
```
and then find the *HKEY_CURRENT_USER &#8594; Software &#8594; Wine &#8594; Direct3D &#8594; VideoMemorySize* and set it to the value of VRAM that your card has.

I assume that Wine does not recognise the right value for the VRAM of your card and so you want to change it manually. Am I right?

---

### Post by ubudog on 2009-02-21
I can't see "VideoMemorySize in that folder.

---

### Post by kostkon on 2009-02-21
Then create it yourself. Right-click on *Direct3D* and select *New &#8594; String Value* and name it *VideoMemorySize*. Then double click on this new created key and enter the amount of your VRAM in MBs.

---

### Post by ubudog on 2009-02-21
Thanks.  I will try that.  I will respond tomorrow.

---

### Post by ubudog on 2009-02-22
Thanks, that worked.

---

