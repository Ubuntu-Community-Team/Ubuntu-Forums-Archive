---
title: "Verbos Mode, and having to do startx"
date: 2007-12-07
forum: The Cafe
---

### Post by blithen on 2007-12-07
How do I make it so that happens? Meaning now boot screen, I want to see everything happen, and how do I make it so I have to startx when it finishes booting?

---

### Post by ssam on 2007-12-07
if you have gdm (or kdm or xdm) installed then X will start at boot time.

in some odd cases you may need to press ctrl+alt+F7 to get to it.

---

### Post by beniwtv on 2007-12-07
Hi,

To make he boot-up verbose (means text mode), remove the "quiet" and "splash" commands form the kernel command line.

(Edit /boot/grub/menu.lst).

If you don't want to start X at startup, you can either remove the gdm (or kdm) from /etc/init.d/, or modify them so that they don't execute anything.

Hope that helps.

---

