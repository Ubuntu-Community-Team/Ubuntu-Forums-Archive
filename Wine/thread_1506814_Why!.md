---
title: "Why!??"
date: 2010-06-10
forum: Wine
---

### Post by Colo2 on 2010-06-10
Hello.

I can't patch Max Payne. 

> The file '/home/tom/Desktop/patch.exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

I've tried doing as some suggested. Marking it as executable. When I do that, I double click, and nothing happens, no error, no patch, nothing. I can't see what's wrong

please help

Thanks

---

### Post by cogadh on 2010-06-10
If you've already marked it as executable, run it from the terminal. If it works, great, if it doesn't, the terminal error messages may explain what is happening.

---

### Post by Colo2 on 2010-06-11
Hi.

When I run it in terminal, I get this:

[IMG]http://i45.tinypic.com/1o95io.png[/IMG]

(Just hangs there)

any ideas?

---

### Post by Colo2 on 2010-06-11
no?

---

### Post by gamblor01 on 2010-06-11
Let's see the ls -l output for the patch.exe file.  Also, since it's not producing any output at this point, let's just set the wine debug to max.  Try to launch it like this:

```

WINEDEBUG=all wine patch.exe

```

Or you might need to add the plus sign:

```

WINEDEBUG=+all wine patch.exe

```


Someone here could probably help but you might be better off posting on the winehq forums...

---

### Post by _Mark_ on 2010-06-11
I maybe wrong here it's a long time since i have used Wine but doesn't the windows executable need to be in the virtual C: Drive wine creates to be able to run. 

eg wine ~/.wine/drive_c/myapps/patch.exe or wine c:\\myapps\\patch.exe

---

### Post by hikaricore on 2010-06-11
> **_Mark_ said:**
> I maybe wrong here it's a long time since i have used Wine but doesn't the windows executable need to be in the virtual C: Drive wine creates to be able to run. 

eg wine ~/.wine/drive_c/myapps/patch.exe or wine c:\\myapps\\patch.exe

You are wrong here.
There is no reason that a binary needs to be on a virtual drive or even in the wine path to function.

---

### Post by Colo2 on 2010-06-11
Thanks :D

works great now.

---

