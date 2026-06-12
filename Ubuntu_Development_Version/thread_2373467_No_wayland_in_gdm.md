---
title: "No wayland in gdm"
date: 2017-10-06
forum: Ubuntu Development Version
---

### Post by richard-osterloh on 2017-10-06
I've upgraded to 17.10 and I can't seem to get the option in gdm to run a wayland session. I've got "Gnome on Xorg" or "Ubuntu on Xorg" options. Is this related? I'd love to know how to fix this.

---

### Post by mc4man on 2017-10-06
> **richard-osterloh said:**
> I've upgraded to 17.10 and I can't seem to get the option in gdm to run a wayland session. I've got "Gnome on Xorg" or "Ubuntu on Xorg" options. Is this related? I'd love to know how to fix this.
This thread is old & no longer topical.
If those are your only 2 options, are you using nvidia drivers on a laptop? (i.e. using nvidia-prime

---

### Post by Perfect Storm on 2017-10-06
Posts moved to own thread.

---

### Post by amano on 2017-10-07
The nvidia 340.xx drivers are legacy drivers that don't support wayland (and probably never will). If you are on a legacy card, the only option for wayland is Nouveau.

Just in case...

---

### Post by fthx on 2017-10-07
And with latest 384 drivers, do you get a Wayland session ?

---

### Post by cariboo on 2017-10-07
I'm getting wayland with one of my users, using 340.104 drivers. My main user still logs into an X session. This will probably get straightened out when I do a fresh install on 17.10 release day.

---

### Post by fthx on 2017-10-07
I created a new user, I do not either get any Wayland session with Nvidia selected in prime...

---

### Post by mc4man on 2017-10-07
> **fthx said:**
> I created a new user, I do not either get any Wayland session with Nvidia selected in prime...
That is the expected behavior.
You should get the option for a Ubuntu (wayland) session when switching back to Intel via nvidia-prime
(- though there could be a new bug where if setting kms for nvidia when switching back from nvidia only an xorg session will continue to be presented

---

### Post by mc4man on 2017-10-08
> **mc4man said:**
> That is the expected behavior.
You should get the option for a Ubuntu (wayland) session when switching back to Intel via nvidia-prime
(- though there could be a new bug where if setting kms for nvidia when switching back from nvidia only an xorg session will continue to be presented

[https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1722078](https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1722078)

---

### Post by fthx on 2017-10-08
Could you confirm that the expected behavior with Nouveau is X and no Wayland too ?

---

### Post by mc4man on 2017-10-08
> **fthx said:**
> Could you confirm that the expected behavior with Nouveau is X and no Wayland too ?

With my laptops i've never seen any way to use nouveau, it's either nvidia or intel drivers, so I can't.

---

### Post by dino99 on 2017-10-30
today test on 18.04 with an intel igp

gdm3 login: ubuntu/gnome sessions (wayland) loops; xorg ones work
lightdm login: ubuntu/gnome sessions are opening smoothly, but ' echo $XDG_SESSION_TYPE ' shows a x11 session instead of a wayland one as expected

---

