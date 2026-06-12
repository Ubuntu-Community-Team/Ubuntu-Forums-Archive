---
title: "is there a specific file where saved form data can be found for a web browser?"
date: 2010-11-08
forum: The Cafe
---

### Post by user1397 on 2010-11-08
i'm talking mostly about chrome/chromium, but it would be interesting to know firefox's and even IE's.

i'm interested because sometimes i feel like deleting just some of the saved form data, not all of it, but i can't remember how long ago i entered them so i can't risk losing all of the data by deleting from last week, month, etc

---

### Post by user1397 on 2010-11-08
bump

---

### Post by GabrielYYZ on 2010-11-08
for firefox, i think it'd be: /home/user/.mozilla/firefox/profile.default/formhistory.sqlite

i don't know how to open or edit the sqlite file though... but i'm fairly confident that's the place the form data is stored.

edit: also, just as a heads up, there's a 24 hour waiting period for bumping.

---

### Post by Quadunit404 on 2010-11-08
Not sure about Chrome/ium, but I do know that Opera stores and encrypts passwords in ~/.opera/wand.dat

---

### Post by Tibuda on 2010-11-08
I think it is ~/.config/chromium/Default on chromium.

---

### Post by koenn on 2010-11-08
> **GabrielYYZ said:**
> for firefox, i think it'd be: /home/user/.mozilla/firefox/profile.default/formhistory.sqlite

i don't know how to open or edit the sqlite file though... but i'm fairly confident that's the place the form data is stored.
it's a database, you need sqlite to open it, then query it with sql statements. But apparently it's encrypted, so you'd have to go look in FF's source code to see how they talk to it.

---

### Post by user1397 on 2010-11-08
> **koenn said:**
> it's a database, you need sqlite to open it, then query it with sql statements. But apparently it's encrypted, so you'd have to go look in FF's source code to see how they talk to it.
hmm not so, i installed sqlite and sqlitebrowser which can view sqlite files.  I was able to see the firefox one quite clearly, but i still don't know exactly which one chrome/ium uses.

---

### Post by GabrielYYZ on 2010-11-08
> **koenn said:**
> it's a database, you need sqlite to open it, then query it with sql statements. But apparently it's encrypted, so you'd have to go look in FF's source code to see how they talk to it.

ah right on, i knew it was a sqlite database but i thought you could use another program to open/edit it. kind of how you can open a .java file with gedit or something and see the code. 

about chrome: did you check /home/user/.config/google-chrome/default/Current Session or /.../Login Data? maybe chromium is the same (i don't use chromium though)

---

### Post by koenn on 2010-11-09
> **ubuntuman001 said:**
> hmm not so, i installed sqlite and sqlitebrowser which can view sqlite files.  I was able to see the firefox one quite clearly, but i still don't know exactly which one chrome/ium uses.
hm, interesting.
I tried to view the firmhostory.sqlite with sqlite (the cli program) but keep getting "SQL error: file is encrypted or is not a database". Maybe I'm doing it wrong

---

### Post by treesurf on 2010-11-09
The dev version of Chrome allows you to edit form data straight from the preferences dialog.  I'm not sure if the stable/beta versions have that feature yet.

---

