---
title: "Tiger"
date: 2010-02-12
forum: Security
---

### Post by mkvnmtr on 2010-02-12
I seem to be having trouble reading the reports from Tiger and root kit hunter and a couple of other security apps. I gksudo nautilus to them and it says it is an unknown file type and can not be opened. Does anyone have an idea why. I have trouble believing that thes apps would be making reports that can not be read.

---

### Post by JT9161 on 2010-02-12
> **mkvnmtr said:**
> I seem to be having trouble reading the reports from Tiger and root kit hunter and a couple of other security apps. I gksudo nautilus to them and it says it is an unknown file type and can not be opened. Does anyone have an idea why. I have trouble believing that thes apps would be making reports that can not be read.

Did you try passing them through file ?

---

### Post by mkvnmtr on 2010-02-13
I do not understand what you mean by passing them through file.

---

### Post by cariboo on 2010-02-13
The previous poster meant, did you use the **file** command to see what type of file it is that you are trying to open eg:

```
file log.txt
log.txt: ASCII text
```

Can you cat the files?

```
cat log.txt
```

---

### Post by mkvnmtr on 2010-02-13
Thank you that made them readable in the terminal. I realize daily how little I know.

---

