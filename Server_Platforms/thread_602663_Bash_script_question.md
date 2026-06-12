---
title: "Bash script question"
date: 2007-11-04
forum: Server Platforms
---

### Post by Dudsmacka2 on 2007-11-04
Why does the following work:

```
sed '/deb cdrom:/d' < /etc/apt/sources.list > /etc/apt/sources.list.new
rm /etc/apt/sources.list
mv /etc/apt/sources.list.new /etc/apt/sources.list
```

but, the following results in an empty sources.list:

```
sed '/deb cdrom:/d' < /etc/apt/sources.list > /etc/apt/sources.list
```

---

### Post by kast on 2007-11-04
**Sed ** makes no changes to the original input file . To make the changes permanent, you must redirect the output from **sed** into a temporary file and then move the file back to the old one:

**sed 's/whatever/WHATEVER/'  file1 > file2** *# Makes the changes*
[B]
mv file2 file1[/B] *# Makes them permanent.*

---

### Post by tkharris on 2007-11-05
< is opening the file descriptor to sed, because this file is already open when you try to redirect with > back into it the changes will be lost. You can never use that type of redirection to change a file.

---

