---
title: "Opening MS Office 07 files without pre-opening MS Office"
date: 2010-09-26
forum: Wine
---

### Post by Trilby on 2010-09-26
A few days ago, I [rather reluctantly] installed *MS Office 07* on my *Ubuntu* laptop using *Play on Linux*. Everything works fine* expect one thing**: When I go to a saved docx file (or xlsx etc) and try to open it, I get the message:
```
There is no windows program configured to open this type of file
```
If I open up the appropriate MS program and find the file from the "open" button/menu, I can open the file without a problem.

However, I'd like to be able to open MSO files with a double click, like I would normally with .odt and .ods files when using OO. I know this can be done because I saw it once before on this site but forgot to take note of how to do it.

Can anyone help?
Thanks,
Trilby.

*As fine a MS' stuff normally could be said to "work"
**Well, two things: One-Note crashes when I close it and then re-opens, not that this is a problem since I never use it anyway.

---

### Post by Trilby on 2010-10-08
I've solved the problem using the command:
```
/usr/share/playonlinux/playonlinux --run "Microsoft Office Word 2007"
```
for Word

```
/usr/share/playonlinux/playonlinux --run "Microsoft Office PowerPoint 2007"
```
for PowerPoint

```
/usr/share/playonlinux/playonlinux --run "Microsoft Office Excel 2007"
```
for Excel

---

