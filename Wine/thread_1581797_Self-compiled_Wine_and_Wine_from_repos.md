---
title: "Self-compiled Wine and Wine from repos"
date: 2010-09-25
forum: Wine
---

### Post by kroq-gar78 on 2010-09-25
Hello Ubuntu Forums Community,

I compiled Wine-git with checkinstall (build a deb pkg) and AcceptEX patch to be able to play Warcraft 3 and Spore. I compiled the latest release and eventually an update came to 1.3.2 (I use dev releases). In the update manager, it said that wine1.3 (had 1.3.1 installed/ compiled) had an update to 1.3.2. I recompiled wine to 1.3.2, rebooted (just to clean things up) and saw that the update was still there. I have ignored the problem since, but now the release is 1.3.3. I recompiled and installed wine, and the update is *still* there.

Any idea on how to solve this problem?
Thanks in advance.

---

### Post by beastrace91 on 2010-09-27
Just disable the Wine development PPA you added if you do not want to upgrade Wine through it anymore.

~Jeff

---

### Post by kroq-gar78 on 2010-09-29
k thanks. forgot to check thread :s sorry

EDIT: I used checkinstall to build the package, and I think I gave it the pkg name "wine", not "wine1.3". Should I recompile it and would fix the problem?

---

### Post by beastrace91 on 2010-09-30
> **kroq-gar78 said:**
> k thanks. forgot to check thread :s sorry

EDIT: I used checkinstall to build the package, and I think I gave it the pkg name "wine", not "wine1.3". Should I recompile it and would fix the problem?

No. It would still want to upgrade to the "latest" 1.3 from the Wine PPA. In order to turn off the message you need to disable the ppa.

~Jeff

---

