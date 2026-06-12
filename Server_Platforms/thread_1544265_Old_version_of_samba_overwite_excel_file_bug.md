---
title: "Old version of samba overwite excel file bug"
date: 2010-08-02
forum: Server Platforms
---

### Post by david.garceau on 2010-08-02
Hey guys, i recently updated my servers to ubuntu 10.04 with the latest samba, from a much older version. Everything is perfect and working as expected. My only problem is that a bug with samba was patched (normally this is great haha). I tracked this to pre-3.011 Before update whenever we would save any .xls files, a box would come up with the following message....


The file "<insert .xls file here>" may have been changed by another 
user since you last save it.  In that case, what do you want to do?"  

You are then given the option to save a copy, or to overwrite changes. 

My office absolutely loved this feature... 

Does anyone know of a way to replicate this with only .xls files, in the newest version of samba?

---

### Post by david.garceau on 2010-08-02
Or even if this isnt possible. Is there a way server side to make it so that whenever someone saves an excel file, it asks them if they are sure they want to overwrite it? even if they click the SAVE button and not the SAVE AS button?

---

### Post by CharlesA on 2010-08-02
What version of excel are you using? I haven't seen that prompt in Excel 2007, but I do see it on Excel 2003.

---

### Post by david.garceau on 2010-08-02
Yeah, we are using 2003

---

### Post by david.garceau on 2010-08-03
bump

---

