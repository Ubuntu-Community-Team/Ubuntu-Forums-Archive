---
title: "Command and Conquer 3 Tiberium Wars"
date: 2010-03-21
forum: Wine
---

### Post by bigseb on 2010-03-21
I currently run Ubuntu 9.10 x64. I managed to install CNC3 (had to drag disc contents to desktop first) just fine, it starts up just fine but stops at the splash screen...

I remembered then that when running the game on my Windows 7 x64 I needed to download and install a patch otherwise it wouldn't work there either. Would the be something similar for Ubuntu? Having trouble finding info on this.

Thanks.

---

### Post by bigseb on 2010-03-24
Anyone?

---

### Post by asdfoo on 2010-03-24
check the appdb

---

### Post by bigseb on 2010-03-25
> **asdfoo said:**
> check the appdb

I did. It says it works but it won't run for me. I think it may be because of the whole 32-bit/64-bit issue.

---

### Post by Brebs on 2010-03-25
> **bigseb said:**
> it starts up just fine but stops at the splash screen

Obvious next thing to do is show some meaningful output:

```
cd ~/.wine/drive_c/"Program Files/Electronic Arts/Command & Conquer 3"
wine CNC3
```

The bug report is [here](http://bugs.winehq.org/show_bug.cgi?id=19159).

---

### Post by bigseb on 2010-03-25
> **Brebs said:**
> Obvious next thing to do is show some meaningful output:
 
```
cd ~/.wine/drive_c/"Program Files/Electronic Arts/Command & Conquer 3"
wine CNC3
```
 
The bug report is [here]("http://bugs.winehq.org/show_bug.cgi?id=19159").
 How did you even find that? I look and look and look and get nowhere. Anyway I read that link, they talk about some patch so I suppose that's the way to go. And what do I do with that code you wrote?

---

### Post by Brebs on 2010-03-25
> **bigseb said:**
> How did you even find that?
It's [right there](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7440) in the list of bugs.

> And what do I do with that code you wrote?
Get acquainted with the command-line ;)

It's a necessary skill. Linux is nowhere near user-friendly enough to avoid the command-line.

---

### Post by bigseb on 2010-03-26
> **Brebs said:**
> It's [right there]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=7440") in the list of bugs.
 
 
Get acquainted with the command-line ;)
 
It's a necessary skill. Linux is nowhere near user-friendly enough to avoid the command-line.
  Thanks brebs. Looks I got a TON of reading to do. Been using Linux a week now... hardcore stuff for a newbie...:D

---

