---
title: "Ubuntu 18.04 just now stopped booting into xorg"
date: 2018-02-08
forum: Ubuntu Development Version
---

### Post by garriguer2 on 2018-02-08
With latest update my ubuntu 18.04 changed from ubuntu (with wayland) as default to ubuntu (with xorg) But now it does'nt boot into ubuntu (xorg default), only into ubuntu with wayland. Somebody knows what happened? Thank you

---

### Post by dino99 on 2018-02-08
the fallback to ubuntu on xorg is due to the latest grub2 change. Your issue could be related to the graphic driver used.
you can open a terminal to glance at 'journalctl -b' to get more details about that boot failure.

---

### Post by garriguer2 on 2018-02-08
I had a look to "journalctl -b" after a boot failure and I'm not capable to sort out the problem, ..too much data for me. I can paste it here if you want, but its very long.

---

### Post by kansasnoob on 2018-02-08
Could it be a gdm3 thing? I had to install 'lightdm-gtk-greeter' and 'lightdm' to get the flashback w/metacity session to boot.

---

### Post by deadflowr on 2018-02-08
> **garriguer2 said:**
> I had a look to "journalctl -b" after a boot failure and I'm not capable to sort out the problem, ..too much data for me. I can paste it here if you want, but its very long.

Pastebinit, please:
[https://help.ubuntu.com/community/Pastebinit]("https://help.ubuntu.com/community/Pastebinit")

---

### Post by dino99 on 2018-02-08
> **garriguer2 said:**
> I had a look to "journalctl -b" after a boot failure and I'm not capable to sort out the problem, ..too much data for me. I can paste it here if you want, but its very long.

Only focus on the 'red' words

---

### Post by zika on 2018-02-09
Check if ~/.Xauthority is stale...

---

