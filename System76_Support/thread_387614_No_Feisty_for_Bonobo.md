---
title: "No Feisty for Bonobo"
date: 2007-03-18
forum: System76 Support
---

### Post by rapha on 2007-03-18
Hi Sys76,

is there a way to make the Ubuntu installation work for the Bonobo? The X server doesn't start, not even in safe graphics mode, not even when I tamper around with the Live CD's xorg.conf myself. Kinda sad, since the Bonobo is supposed to be kind of a special Linux laptop.

Regards,
Raphael

P.S.: I do know about the Alternate Install CD and am downloading it right now. I would nevertheless love to be able to use the recommended standard CD...

P.P.S.: Any progress on the Webcam and TV Card driver front?

---

### Post by rapha on 2007-03-18
Feisty is installed now. However, after the first boot I had to:

- Ctrl-Alt-Backspace my way out of the X-server
- Manually edit xorg.conf to use the vga (!) driver (vesa won't work)
- apt-get install restricted-manager; use that to install fglrx
- Issue 'sudo /etc/init.d/gdm restart' to finally get X running properly

Sad imo. Either for Ubuntu or for Sys76 (or for both...

[EDIT: Screenshot after seeing X for the first time, with the vga driver enabled]

---

### Post by qamelian on 2007-03-18
> **rapha said:**
> Feisty is installed now. However, after the first boot I had to:

- Ctrl-Alt-Backspace my way out of the X-server
- Manually edit xorg.conf to use the vga (!) driver (vesa won't work)
- apt-get install restricted-manager; use that to install fglrx
- Issue 'sudo /etc/init.d/gdm restart' to finally get X running properly

Sad imo. Either for Ubuntu or for Sys76 (or for both...

[EDIT: Screenshot after seeing X for the first time, with the vga driver enabled]

Why is it sad when you're installing a version of Ubuntu that isn't even released yet? Seems to me that expecting everything to work just peachy while Feisty is still in development is what's sad. If the problems persist after Feisty is released and becomes a supported release, then you have room to complain.

---

### Post by rapha on 2007-03-18
I'm almost sure it won't change for the final release; the Breezy Live-CD installation didn't work for the Bonobo either... otoh you're quite right and we'll see.

---

