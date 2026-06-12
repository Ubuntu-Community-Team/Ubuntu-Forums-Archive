---
title: "Get (main) display color profile"
date: 2020-01-23
forum: Ubuntu Application Development
---

### Post by gvanvoor on 2020-01-23
I'm working on a color managed application and in order to display colors correctly, I need to know which color profile is used by the (main) display.
I've found out that the icc profiles are stored in ~/.local/share/icc but I currently have no idea which of those files I need to use (there's more than one on my machine).
Does anyone know how to go about this? Preferable in C/C++ but command line would be fine as well.

---

### Post by gvanvoor on 2020-01-23
I managed to find a solution: using libcolord, I can list the devices, get the default profile for a device and then get the filename for that profile.

---

