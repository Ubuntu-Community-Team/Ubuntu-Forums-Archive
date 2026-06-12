---
title: "Trouble saving qjackctl settings"
date: 2010-11-02
forum: Ubuntu Studio
---

### Post by PatrickZ on 2010-11-02
Hi,

I've been fiddling about with jack and have encountered a problem, I can't save the settings in qjackctl unless i open it with sudo. (In which case it doesn't work, but I can save my settings.) So it's probably some kind of permissions issue, right..?

---

### Post by AutoStatic on 2010-11-02
What is the output of the terminal command **ls -l ~/.config/rncbc.org/QjackCtl.conf** ? You should be able to set the permissions with the command **chown yourusername:yourusername ~/.config/rncbc.org/QjackCtl.conf**

Best,

Jeremy

---

### Post by PatrickZ on 2010-11-02
Oh....So that's where it was! (=**~/.config/rncbc.org/QjackCtl.conf) **As i suspected, for some reason i didn't have permission to edit that. But now it seems to be working just fine. Many thanks. :)

---

