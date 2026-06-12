---
title: "How do I lock my PC?"
date: 2009-12-01
forum: The Cafe
---

### Post by daniel014 on 2009-12-01
Hello. Hope this isn't in the wrong place on the forums.

I recently had my school computer email used to send a very offensive email around the school under my name.

Unfortunately, because the old Windows XP Pro computers are so locked down, I cannot lock the computer whilst not at my desk.

Does anyone know of a hack or USB drive app that would solve this problem and lock my computer?

Thanks for any help. =]

---

### Post by Cam42 on 2009-12-01
> **daniel014 said:**
> Hello. Hope this isn't in the wrong place on the forums.

I recently had my school computer email used to send a very offensive email around the school under my name.

Unfortunately, because the old Windows XP Pro computers are so locked down, I cannot lock the computer whilst not at my desk.

Does anyone know of a hack or USB drive app that would solve this problem and lock my computer?

Thanks for any help. =]
If your system is password protected, you can hit super+l

---

### Post by Psumi on 2009-12-01
> **Cam42 said:**
> If your system is password protected, you can hit super+l

What's the command to lock screen so I can assign a keyboard shortcut to SUPER+L for that?

xfce4 metapackage doesn't install SUPER+L Shortcut for that (Nor Run Command.)

---

### Post by RiceMonster on 2009-12-01
> **Psumi said:**
> What's the command to lock screen so I can assign a keyboard shortcut to SUPER+L for that?

xfce4 metapackage doesn't install SUPER+L Shortcut for that (Nor Run Command.)

For Xfce it's xflock4, but you need to have xscreensaver installed, then assign it to that shortcut.

---

### Post by Psumi on 2009-12-01
> **RiceMonster said:**
> For Xfce it's xflock4, but you need to have xscreensaver installed, then assign it to that shortcut.

Here:

```
/usr/bin/xflock4: 28: xlock: not found
~$ sudo apt-get install xflock4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xflock4
```

Also, xlock is referred by another package or depreciated. So what now? xscreensaver is installed.

---

### Post by earthpigg on 2009-12-01
> **daniel014 said:**
> Unfortunately, because the old Windows XP Pro computers are so locked down, I cannot lock the computer whilst not at my desk.

Does anyone know of a hack or USB drive app that would solve this problem and lock my computer?

yes.

save [this wikipedia article]("http://en.wikipedia.org/wiki/Information_assurance") to a thumb drive.

throw it at the head of the local sysadmin. hard.

---

### Post by squilookle on 2009-12-02
> **daniel014 said:**
> Hello. Hope this isn't in the wrong place on the forums.

I recently had my school computer email used to send a very offensive email around the school under my name.

Unfortunately, because the old Windows XP Pro computers are so locked down, I cannot lock the computer whilst not at my desk.

Does anyone know of a hack or USB drive app that would solve this problem and lock my computer?

Thanks for any help. =]

Hi Daniel014, from the replies, I have a feeling I missed something, but if the computer is running Windows XP Pro (not Linux), can you tell us what happens if you press Control, Alt, and delete - unless the computer is REALLY locked down, it should bring up a window with six options, the first being "lock computer"

---

