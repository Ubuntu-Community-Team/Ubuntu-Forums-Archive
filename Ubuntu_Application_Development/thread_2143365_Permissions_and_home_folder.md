---
title: "Permissions and home folder"
date: 2013-05-08
forum: Ubuntu Application Development
---

### Post by Curlydave on 2013-05-08
I'm new to programming. I made a program in Windows using Python 3 that downloads FAA approach plates. It uses the QT gui. I recently installed Ubuntu 13.04, and have been trying to get my program to work on Ubuntu. I installed the python modules and QT, and ran my program with the built-in Python installation, in a subfolder of my Home folder.

The program launches, and the GUI looks native. However, it won't download the plates due to permission errors. My understanding was that the Home folder was a safe zone from [permission errors](http://www.xkcd.com/1200/). I tried running Python under SUDO. I didn't get permission errors, but the GUI looked like it was from  Windows 95, and the files didn't actually download, despite the program not reporting an error. Any ideas?

---

### Post by tctx on 2013-05-09
> **Curlydave said:**
> [...] and ran my program with the built-in Python installation, [...]
If I'm not mistaken the default Python interpreter on Ubuntu 13.04 is Python 2.7, not Python 3.x. Are you sure you ran your program using Python 3?
Try to run:
```
$ python3 myprogram.py
```

> **Curlydave said:**
> [...] in a subfolder of my Home folder.
What are the permissions of this folder? Find out with:
```
$ ls -l ~/path-to-your-subfolder
```

> **Curlydave said:**
> [...] despite the program not reporting an error. Any ideas?
Do you have any try-except blocks in your code that catch any error raised?
```
try:
    ...any error raised here...
except:
    ...is caught here...

```

---

