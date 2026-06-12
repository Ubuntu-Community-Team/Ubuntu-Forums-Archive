---
title: "find replace recursively in zips"
date: 2015-12-10
forum: Server Platforms
---

### Post by iacoposk8 on 2015-12-10
Hello everyone!
 I have zip files, with inside zip files that can contain other zip and / or files.
 I would like to get recursively in all zip files and do a find replace in all files.
 how can I do?

---

### Post by matt_symes on 2015-12-10
Hi

> **iacoposk8 said:**
> Hello everyone!
 I have zip files, with inside zip files that can contain other zip and / or files.
 I would like to get recursively in all zip files and do a find replace in all files.
 how can I do?

```
zip update ....
```

?

> update (-u) 
                                                                                                          
Update  existing entries if newer on the file system and add new files.  If the archive does not exist issue warning then create a new archive.

Do you want to update the files inside the zip files or will the zip files lower in the main zip archive already have been created ?

Kind regards

---

### Post by iacoposk8 on 2015-12-10
if I have:
test.zip/test.xml
test.zip/test.zip/test.xml

 I would like to find replace in both xml file

---

