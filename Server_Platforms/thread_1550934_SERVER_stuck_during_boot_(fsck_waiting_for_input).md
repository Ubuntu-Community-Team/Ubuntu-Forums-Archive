---
title: "SERVER stuck during boot (fsck waiting for input)"
date: 2010-08-11
forum: Server Platforms
---

### Post by zosky on 2010-08-11
all is well on my headless Lucid server until a recent *apt-get upgrade && shutdown -R now* ... it did not come back up ??? 

after i moved a screen to the other side of the house, i found fcsk waiting for input during the boot process 
[INDENT]errors on / ... (I)gnore / (F)ix " ...[/INDENT]so i had to attach a keyboard just to push <F> 

i could change /etc/fstab so it never runs fsck, but this doesn't seem wise.
how can i make it <F>ix automatically ? ( or maybe after Xsec )

---

### Post by CharlesA on 2010-08-11
It's normally not wise to have fsck fix errors automatically. If there are errors, you would be better off shutting down the server and booting off a livecd to run fsck on the root partition.

It would not be wise disable fsck checking.

---

