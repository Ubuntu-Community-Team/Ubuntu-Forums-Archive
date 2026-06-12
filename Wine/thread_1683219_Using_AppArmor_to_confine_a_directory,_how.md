---
title: "Using AppArmor to confine a directory, how?"
date: 2011-02-07
forum: Wine
---

### Post by 3602 on 2011-02-07
Basically I installed Office 2007 in WINE, because when you write a lab report in O-O-o with formulae, and you save that file into a *.docx* then open said file with Office, the formulae are not displayed and the tables are all out of whack.
So here's the thing. I am afeared that some time in the future I may hit a macrovirus (or worse, macroviruses, virii?) or an embedded rootkit. So what I'd like to do is to lock down */.wine/dosdevices/C:* so nothing in there can get out (all the progeams run fomr there, right).
So, in short, how? From reading the sticky, I have understood that *genprof* is for a *program*. Now I don't want to confine WINE (or maybe I do, please tell me), just the fake C: directory.
Thank you very much.

---

### Post by cariboo on 2011-02-07
Wouldn't removing symbolic links to other file systems do the same thing?

---

### Post by 3602 on 2011-02-07
> **cariboo907 said:**
> Wouldn't removing symbolic links to other file systems do the same thing?Could you please elaborate? Under *dosdevices* I have C: (the fake C: drive) and D: (an always-plugged-in flash card as an expansion SSD). And another one, perhaps Z: (I'm not on my computer right now) is locked. When I try to open it, it says "you're not the owner".

---

### Post by cariboo on 2011-02-07
I haven't felt the need to use wine in years, but i think Z is linked to the Ubuntu file system.

This question should really be in the Wine sub-forum, where people that actually use wine could better answer your question. Moved.

---

