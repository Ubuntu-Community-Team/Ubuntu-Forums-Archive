---
title: "Broken graphics across multiple games"
date: 2011-05-05
forum: Wine
---

### Post by Arachan on 2011-05-05
Hello,

I have a problem with Wine. For multiple games (Guild Wars, Command and Conquer 3, Battleforge off the top of my head) graphics (textures, I think) are missing large chunks. As an example, Guild Wars seems to run fine, however bits of my and other people's characters are simply not there. In Command and Conquer 3, often whole units are not there are all.

I have the latest WINE, latest ATI propriety drivers, a HD5770 GPU, everything seems fine to me.

Does anyone have any idea?

Thanks,
Arachan.

---

### Post by Dlambert on 2011-05-06
> **Arachan said:**
> Hello,

I have a problem with Wine. For multiple games (Guild Wars, Command and Conquer 3, Battleforge off the top of my head) graphics (textures, I think) are missing large chunks. As an example, Guild Wars seems to run fine, however bits of my and other people's characters are simply not there. In Command and Conquer 3, often whole units are not there are all.

I have the latest WINE, latest ATI propriety drivers, a HD5770 GPU, everything seems fine to me.

Does anyone have any idea?

Thanks,
Arachan.

Try playonlinux, then modify graphics settings. Use open gl etc

---

### Post by Dlambert on 2011-05-06
Or if your more advanced, modify the wine registry

---

### Post by Tweak42 on 2011-05-08
Wine is not a fix all solution.  When trying to isolate a problem, stay to specifics, one program at a time.  Check the wine [appdb]("http://appdb.winehq.org") for tips on what to try.  One fix might break a different program, so using wineprefix to keep tweaks separated is recommended.  Playonlinux is useful in this regard because it enables easier management of separate wine prefixes.

---

