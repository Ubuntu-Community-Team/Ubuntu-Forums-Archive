---
title: "gnome-panel applets won't become transparent/change background"
date: 2012-04-12
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by jba3 on 2012-04-12
I've tried multiple fixes, such as the ~/.config/gtk-3.0/gtk.css changes, but I can't seem to get the panel applets transparent, or to take a background image. Ideally, I want a background image so I can match my AWN bar. No matter what I do, the applets keep the solid grey background. I've also tried poking around the /usr/share/themes/Ambiance/ files, changing the CSS there and restarting, but still to no avail. I'm using the default Ambiance theme.

I'm using the "gnome classic" mode, not gnome 3 shell or unity.

Attached is a screenshot. The lower right corner is the "trouble spot". It seems this is a 12.04 specific problem, since the 11.04/11.10 fixes/workarounds aren't working. My google-fu hasn't led me to any 12.04 working fixes.

---

### Post by NHclimber on 2012-04-12
Broken by GTK 3.4
Waiting to hear if the breakage is a permanent api change or accidental.
Feel free to file a bug in Launchpad against the gnome-panel package and I'll link the gnome bug to it.

---

### Post by jba3 on 2012-04-12
> **NHclimber said:**
> Broken by GTK 3.4
Waiting to hear if the breakage is a permanent api change or accidental.
Feel free to file a bug in Launchpad against the gnome-panel package and I'll link the gnome bug to it.
Ah, that's a shame. I'll see if I can sign up for an account and post a bug report later today. Thanks for the info.

For now I'll just set the AWN colors to match the gnome-panel color. It's 3C3B37 for the Ambiance theme, if anyone else wants a short-term color-matched workaround.

---

