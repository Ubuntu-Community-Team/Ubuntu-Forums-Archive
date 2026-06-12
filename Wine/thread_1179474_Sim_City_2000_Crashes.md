---
title: "Sim City 2000 Crashes"
date: 2009-06-05
forum: Wine
---

### Post by Epitaph44 on 2009-06-05
I am using Ubuntu Hardy Heron 8.04
I'm using the latest version of Wine as of June 4, 2009.
I installed Sim City 2000 just fine, and it plays great, but it crashes (closes) whenever I try to save or save as.
Anything I can do to be able to play my favorite retro game?

---

### Post by Stunts on 2009-06-05
> **Epitaph44 said:**
> I am using Ubuntu Hardy Heron 8.04
I'm using the latest version of Wine as of June 4, 2009.
I installed Sim City 2000 just fine, and it plays great, but it crashes (closes) whenever I try to save or save as.
Anything I can do to be able to play my favorite retro game?
If I recall correctly, SimCity2000 is a DOS game.
You'll probably be better off playing it using DOSBox rather than wine
```
sudo apt-get install dosbox
```

Give it a shot and let me know how it went.

---

### Post by hikaricore on 2009-06-05
SC2k has multiple versions including but not limited to dos.

---

### Post by wakingrufus on 2009-06-06
I also recommend running the DOS version of SC2000 in dosbox.  that is what i do.

---

### Post by Epitaph44 on 2009-06-07
The DOS emulator worked perfectly. Thank you very much!

---

### Post by hikaricore on 2009-06-07
Works fine under WINE on my roomie's system I checked it out.

---

### Post by Stunts on 2009-06-08
> **Epitaph44 said:**
> The DOS emulator worked perfectly. Thank you very much!

You are welcome!

Enjoy SC2000!

Edit: You should place a [Solved] tagged in the beginning of the title for other people to know it's solved.

---

### Post by scarf on 2011-12-11
i didn't like the dos emulator that much.  to overcome the crash when loading/saving, just set your windows version to NT 3.5 in the Wine configuration, as is mentioned in the bug report over at WineHQ.  now the windows version is working perfectly.

---

