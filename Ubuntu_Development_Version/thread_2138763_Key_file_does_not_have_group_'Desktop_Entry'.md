---
title: "Key file does not have group 'Desktop Entry'"
date: 2013-04-25
forum: Ubuntu Development Version
---

### Post by dino99 on 2013-04-25
Have a few lines logged like that one:

Could not parse file "~/.local/share/applications/compiz.desktop": Key file does not have group 'Desktop Entry'

i'm wondering what might be done

---

### Post by dino99 on 2013-04-25
I suppose they are all old settings file left behind; and as they are empty they seem conflicting with those inside /usr/share/applications/...
As files can be cleanly recreated inside .local/, i'm now deleting these empty *.desktop

---

