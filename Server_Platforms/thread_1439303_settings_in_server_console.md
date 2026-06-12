---
title: "settings in server console"
date: 2010-03-26
forum: Server Platforms
---

### Post by v1ad on 2010-03-26
well i don't know how to describe this but in my ubuntu server the console has no colors, can't use up arrows to recall or do anything. all i see is black and white. and the arrow keys just output the arrow key code. in admin mode it works fine. added a user and it don't work in user mode.

---

### Post by KiLaHuRtZ on 2010-03-26
What shell are you using?

```
echo $SHELL
```

---

### Post by v1ad on 2010-03-26
sh :[
should be bash correct or at least thats what i had b4?
how would i change it to bash?

---

### Post by KiLaHuRtZ on 2010-03-26
Make sure '/bin/bash' is listed in '/etc/shells', then change it.

```
cat /etc/shells | grep bash
chsh -s /bin/bash
```

Logout and then log back in.

---

### Post by v1ad on 2010-03-26
sweet thanks.
that did the trick.

---

