---
title: "New gtk4 windows displayed  content is copied from their background"
date: 2024-09-03
forum: Ubuntu Development Version
---

### Post by Wise Ferret on 2024-09-03
For a couple of days, new gtk4 windows (e,g, Files, gnome terminal, gnome settings, and and zenity windows too) are rendred with their original background as their content (see screenshot: this is how it looks like when I start Files). Terminal shows no errors.
This does not effect evince, firefox, libreoffice, etc.
Interacting and fiddling with these windows sometimes refreshes them and brings back their original content.
I ecperience this on an x11 session (not on wayland, but wayland has other problems) with nvidia drivers, both 550 and 555.
Any ideas? Does anyone else experience this?

---

### Post by vhaarr+launchpad on 2024-09-09
I had the same problem but a couple of days ago it stopped. I am using the -proposed repos.

It's still not perfect. For example when watching a movie using Celluloid, the rendering will break after 30-45 minutes and then I have to restart the player.

---

### Post by Wise Ferret on 2024-09-09
This stopped for me several days ago as well, but I thought it was because I upgraded my nvidia drivers. Perhaps it was some persisting corrupt cache.

---

### Post by jbicha on 2024-09-09
Well, we did have a new mesa release recently that then later got some bugfixes. If this issue is no longer affecting you, please mark the thread SOLVED.

---

