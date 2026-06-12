---
title: "Guake shortcut not working sometimes"
date: 2022-04-07
forum: Ubuntu Development Version
---

### Post by yaminb on 2022-04-07
Running the latest dev version of 22.04.

I'm having a problem with guake where it just doesn't work sometimes. The shortcut (F12) doesn't bring down the terminal. Then randomly, it will start working.
If I 'reinstall' guake via APT, things start working again for a time.

Should also mentinon, the guake icon in the top bar is also non responsive when this happens.

Any ideas on where to start debugging this?

---

### Post by vanadium on 2022-04-07
On Wayland, set up a shortcut key that calls "guake-toggle". The build-in global shortcut system only works on Xorg.

---

### Post by yaminb on 2022-04-07
I tried that. Guake was still acting funny.

I found this one which works straight forward.
[https://github.com/amezin/gnome-shell-extension-ddterm](https://github.com/amezin/gnome-shell-extension-ddterm)

---

