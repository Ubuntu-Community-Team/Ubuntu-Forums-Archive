---
title: "Changing host name in windows guest"
date: 2015-10-01
forum: Windows
---

### Post by zexelon2 on 2015-10-01
I am wondering if anyone knows a way to auto generate a new "Computer Name" for Windows 7 at or around boot time. 

Essentially I have a gold master image of a windows install and I would like to effectively spawn temporary images off of it using thin-provisioning. This all works well however every temporary spawned VM will have the same host name as the master image. Is there a way to either update the windows computer name offline before boot from linux or to auto update it as windows boots?

---

### Post by TheFu on 2015-10-01
"Other OS" would be a better forum for this question. There are ways to do it. I don't know how. They use paid microsoft deployment tools  to make it happen when I've seen this at previous jobs.

---

### Post by howefield on 2015-10-02
Thread moved to the "*Windows*" forum.

---

### Post by zexelon2 on 2015-10-02
Sorry for the confusion, thanks for moving this thread!

---

### Post by zexelon2 on 2015-10-02
I found the following program for Linux: chntpw I am going to give it a shot and see if it can offline change a windows hostname via registry edits.

---

