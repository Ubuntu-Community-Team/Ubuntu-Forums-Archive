---
title: "no alsamixer or sound on PPC"
date: 2012-10-03
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by 2blue on 2012-10-03
On a freshly installed lubuntu quantal ppc I have no alsamixer in terminal. I have reinstalled alsa-utils package and ran the command sudo rm /etc/modrpobe.d/blacklist.local.conf which did the trick in 12.04. I still have no sound or audio icon on taskbar, but alsamixer showed up in terminal for a while with a message; "this sound device does not have any controls". Today after a reboot, alsamixer no longer shows in terminal and is back to; "cannot open mixer: No such file or directory". 

Any idea what this is about?

---

