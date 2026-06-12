---
title: "Help me install xPUD to a flash USB."
date: 2008-12-27
forum: The Cafe
---

### Post by Islington on 2008-12-27
[http://xpud.org/](http://xpud.org/)

It claims to be superfast on bootup(check out the youtube link on that page) and I wish to test this.

Unfortunately I do understand how to install this to a USB flash drive.The syslinux file mentioned, turns out to be an .exe file, confusing me even further. Google reveals nothing.:(

---

### Post by init1 on 2009-01-04
> **Islington said:**
> [http://xpud.org/](http://xpud.org/)

It claims to be superfast on bootup(check out the youtube link on that page) and I wish to test this.

Unfortunately I do understand how to install this to a USB flash drive.The syslinux file mentioned, turns out to be an .exe file, confusing me even further. Google reveals nothing.:(
I've tried it, but it can't really do much yet. Most of the features have not yet been implemented. 
If you want to install it:
1. Unzip [xpud-0.8.5.zip](http://www.xpud.org/download/xpud-0.8.5.zip) into your pendrive.
2. Unmount your pendrive and install syslinux
```

syslinux /dev/yourpendrive1

```
That should work

---

### Post by zmjjmz on 2009-01-04
Could you mind telling me what the resource usage is like when you get it going?

---

### Post by init1 on 2009-01-04
> **zmjjmz said:**
> Could you mind telling me what the resource usage is like when you get it going?
It's hard to say, they don't give you a terminal, or any virtual terminals. You can't actually do anything with it yet, but it does look promising.

---

### Post by cardinals_fan on 2009-01-04
That's fascinating.  I'm giving it a try in Qemu.

---

### Post by zmjjmz on 2009-01-04
> **init1 said:**
> It's hard to say, they don't give you a terminal, or any virtual terminals. You can't actually do anything with it yet, but it does look promising.

[img]http://xpud.org/screenshot/plate-run.jpg[/img]
Is lilyterm not a vt?

---

### Post by cardinals_fan on 2009-01-04
> **zmjjmz said:**
> 
Is lilyterm not a vt?
[http://lilyterm.luna.com.tw/index_en.html](http://lilyterm.luna.com.tw/index_en.html)
> A light and easy to use libvte based X Terminal Emulator

---

### Post by init1 on 2009-01-04
> **zmjjmz said:**
> [img]http://xpud.org/screenshot/plate-run.jpg[/img]
Is lilyterm not a vt?
None of that was actually in the distro. For most of the menu options, it says "Oops, this is a not yet implement feature" when you click on them.

---

