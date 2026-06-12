---
title: "My computer shut's down"
date: 2008-01-25
forum: Windows
---

### Post by susiarad on 2008-01-25
I'm using a desktop computer with dual boot, sometimes when I'm using the xp it just shuts down in the middle of anything I'm doing even if I'm not doing anything. When I'm using the Ubuntu it seems to be just fine. Any ideas?

---

### Post by Lord Illidan on 2008-01-25
It's a windows problem, then, isn't it?
Does it show you a bluescreen? Even if only for a split second?

I moved it here, since it's a Windows problem.

---

### Post by susiarad on 2008-01-25
nope, no blue screen,
it might be a windows problem, I figured since guys in this forum know so much they could tell me if it is actually windows related or maybe hardware related.
I checked to see that the cpu fan still works fine.

---

### Post by Lord Illidan on 2008-01-25
Well..if it was hardware related, you'd be seeing the problems in Ubuntu too, I guess. Or perhaps Ubuntu ignores them, and Windows crashes on them.

Overheating could be a culprit. Also, check for viruses, perhaps?

EDIT : I also recommend these forums : [http://www.winforums.com/](http://www.winforums.com/)

They're not too bad at solving windows problems..

---

### Post by susiarad on 2008-01-25
i will try them thanks
if you could just answer me one last question I'll stop bothering you.
is there a way to scan the windows partition while using ubuntu? (the win xp partition is in NTFS if it matters)

---

### Post by Lord Illidan on 2008-01-25
> **susiarad said:**
> i will try them thanks
i think its probably a virus i guess i was hoing for some magical cure

Install Ubuntu? Oh wait, you've already done that :D

---

### Post by susiarad on 2008-01-25
if you could just answer me one last question I'll stop bothering you.
is there a way to scan the windows partition while using ubuntu? (the win xp partition is in NTFS if it matters)

---

### Post by rosegarden78 on 2008-01-25
When I sabotaged or tweaked my XP by disabling essential services and deleting system folders these strange things and bsod began to happen.

---

### Post by Sementis on 2008-01-26
> **Lord Illidan said:**
> It's a windows problem, then, isn't it?
Does it show you a bluescreen? Even if only for a split second?

I moved it here, since it's a Windows problem.

Unfortunately, this is exactly the problem with the dualboot-computer of my dad.
Windows won't start up after choosing it in grub, booting screen shows, then a bluescreen for a split of a second and then the maschine restarts.

You seem to have an answer to it? Please let me know :)

Greetings

---

### Post by rosegarden78 on 2008-01-26
Well if your Grub is intact and you boot into Ubuntu just fine, then you insert the Windows Install CD and navigate to Repair or Reinstall Previous Windows.  This will give you fresh install of Windows but leave the boot sectors alone.  Just make sure to backup your Documents and Settings folder to your Ubuntu desktop before proceeding, but last time I restored XP it left them alone.  Ubuntu should mount automatically but you might need the ntfs-fuse and/or nfts-3g packages to mount it.

---

