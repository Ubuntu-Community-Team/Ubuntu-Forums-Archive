---
title: "Wine + MS Office"
date: 2010-02-01
forum: Wine
---

### Post by The_Eggert on 2010-02-01
Hey
I just installed Microsoft Office 2007 with Wine. I'm not particularly proud of it, but it's just that much easier to me;)
Anyway...It is now set as the default editor for *.docx files, which should be fine, but when I doubleclick a *.docx file, it does open MS Word, but it gives me this error message (Translated from danish;)):
"The file wasn't found.
(Z:\home\eggert\Documents\<name>.doc(x)"
And it gives me an error message for each word, of the document name. The last word is given the extention .docx, while the rest is given .doc (Don't know if it is relevant, but I might as well give as much info as I've got:P)
Nevertheless...Is there anyway I can open the file from my file browser, without getting the error message?

---

### Post by Soepstengel on 2010-02-02
It's a known bug (and very annoying): [http://bugs.winehq.org/show_bug.cgi?id=19385](http://bugs.winehq.org/show_bug.cgi?id=19385)

[Comment #6]("http://bugs.winehq.org/show_bug.cgi?id=19385#c6") on that page shows a "solution". It works for me for docx files, but not for doc files (I guess that's a different registry key).

---

### Post by The_Eggert on 2010-02-02
> **Soepstengel said:**
> It's a known bug (and very annoying): [http://bugs.winehq.org/show_bug.cgi?id=19385](http://bugs.winehq.org/show_bug.cgi?id=19385)

[Comment #6]("http://bugs.winehq.org/show_bug.cgi?id=19385#c6") on that page shows a "solution". It works for me for docx files, but not for doc files (I guess that's a different registry key).

Alright :D
Thanks, it was starting to drive me crazy ;)

---

