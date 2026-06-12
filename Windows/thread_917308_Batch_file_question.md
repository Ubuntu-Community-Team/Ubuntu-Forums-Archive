---
title: "Batch file question"
date: 2008-09-11
forum: Windows
---

### Post by RATM_Owns on 2008-09-11
Basically, the main computers in some places have blocked CMD from working, but bat files still work, so what I was hoping to do was create a bat file to simulate the CMD Prompt.

Here's what it is so far:
```
@echo off
cls
:cmd
set /p c=Command: 
//
goto cmd

```

What I need is in place of the // line is just a line which tells cmd.exe to run the input.

---

### Post by jaqie on 2008-09-11
> **RATM_Owns said:**
> Basically, the main computers in some places have blocked CMD from working
You may wish to check the rules. If the computer is not owned by you, it is not only against the rules here to discuss circumventing those restrictions they have placed, it may be illegal as well.

---

### Post by bodhi.zazen on 2008-09-11
first, wrong OS

second, this type of activity is not supported on the Ubuntu forums. If you need this kind of access go talk to your sys admin.

---

