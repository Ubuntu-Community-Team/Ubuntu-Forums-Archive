---
title: "GPG Question"
date: 2010-02-15
forum: Security
---

### Post by bbourdet on 2010-02-15
Hello -

I have encrypted a file that I need to decrypt now. This particular file is a video file. When I use the command gpg --decrypt (filename) it decrypts it in the window. I want to be able to decrypt this file and save it somewhere else unencrypted with a different name. Anyone have any idea on how to do this?


Tarken

---

### Post by kiranmurari on 2010-02-16
Hi,

You can use the "-o file" option to save the decrypted file in your desired location.
```
$ gpg -o /path/to/save/file --decrypt file.gpg
```Hope this helps.

---

### Post by bbourdet on 2010-02-16
Thanks! Works great!

Tarken

---

