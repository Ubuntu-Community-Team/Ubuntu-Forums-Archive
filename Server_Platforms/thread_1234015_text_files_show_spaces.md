---
title: "text files show spaces"
date: 2009-08-07
forum: Server Platforms
---

### Post by t_ras on 2009-08-07
Kubuntu 9.04. using ISPConfig3

I had HTML files created in windows in one of the sites that I took from back up when I upgraded. they worked fine on 8.10, but now they seem to have spaces between each letter. In windows they look fine, in Kate I see the spaces.
How can did be?? what changed between versions?
DO I have to go now and fix all files one by one?

BTW it happens only with files from windows, other backed up sites I have work fine.

---

### Post by cdenley on 2009-08-07
It sounds like the file is saved in a 16-bit format, but kate is expecting it to be 8-bit. Try this command:
```

strings -e l broken.txt>fixed.txt

```
By the way, gedit works correctly with unicode text documents created with wordpad in windows.

---

### Post by t_ras on 2009-08-08
thanks!

---

