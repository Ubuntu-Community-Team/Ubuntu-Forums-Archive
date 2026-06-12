---
title: "Windows menul.list equivalent?"
date: 2006-02-03
forum: The Cafe
---

### Post by Curlydave on 2006-02-03
I've been messing around with Windows Vista beta among other things, and ended up with several windows installations. To handle this, Windows has its own boot loader similar to grub, which is accessible from GRUB.

I want to remove this loader, and be able to get to my windows partition directly through GRUB again. This loader contains 3 entries, 2 of which lead to nothing because I deleted them. The Win boot loader doesn't realize this.

How do I fix this? Thanks!

---

### Post by aysiu on 2006-02-03
So you want to install Ubuntu's Grub to manage Windows?
Or you want to change which version of Windows is in charge of the boot record?

---

### Post by Curlydave on 2006-02-03
Nvm, I should have googled it first. It's called "boot.ini". I deleted the extra stuff.

---

### Post by bored2k on 2006-02-03
On Windows (at least on XP and below), hitting the Winkey+Pause/Break button should load up your system configuration menu (or whatever it's name is). There, go to System Recovery (or similar) --> Boot, click on Edit and delete the undesired lines.

---

