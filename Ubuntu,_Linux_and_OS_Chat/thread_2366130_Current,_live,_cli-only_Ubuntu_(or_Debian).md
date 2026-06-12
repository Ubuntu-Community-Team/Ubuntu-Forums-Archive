---
title: "Current, live, cli-only Ubuntu (or Debian)?"
date: 2017-07-14
forum: Ubuntu, Linux and OS Chat
---

### Post by MetalMusicAddict on 2017-07-14
I currently have a need for a live, cli-only (Ubuntu or Debian-based) linux. I just can't find one.

If not, I guess I'll have to make one. :) Suggestions welcome.

---

### Post by ajgreeny on 2017-07-14
As far as I'm aware there isn't one; one way to run a live command line would be to get the live Lubuntu system, boot to it, and then using Ctrl+Alt+F1 stop the display manager which I think is lightdm with command ```
systemctl stop lightdm.service
``` and simply continue with command-line only.

---

### Post by MetalMusicAddict on 2017-07-14
> **ajgreeny said:**
> As far as I'm aware there isn't one; one way to run a live command line would be to get the live Lubuntu system, boot to it, and then using Ctrl+Alt+F1 stop the display manager which I think is lightdm with command ```
systemctl stop lightdm.service
``` and simply continue with command-line only.

That was one route. I need to create a live system w/persistence that logs in as a user then runs a script. All automatically. I'm thinking I might need to go Arch.

---

