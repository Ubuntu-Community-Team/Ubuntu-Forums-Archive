---
title: "Ubuntu 11.04 won´t boot into Grub even if i press shift or esc"
date: 2011-07-30
forum: Security
---

### Post by Sonicrulz12 on 2011-07-30
Hi, I forgot my password because i tried to change it , but i accidentally pressed generate a few seconds before closing and saving, and i tried pressing esc or shift when booting Ubuntu it says GRUB LOADING or BOOTING and just boots normally like if nothing happened so how can i fix it, btw i made another account before any of this happened but its a desktop user account.

---

### Post by Sonicrulz12 on 2011-07-30
can anyone help please

---

### Post by drs305 on 2011-07-30
I'll answer your question even though I'm not sure I understand the reason for getting to the Grub menu.

For Grub 2, it should normally display the menu by *holding down* the SHIFT key during boot until it appears.

If the keystatus check isn't incorporated (the held SHIFT key), then rapidly pressing the ESC key at the correct time may force the G2 menu to appear.

The third way would be to try to interrupt the boot by any method about half way through the boot process (after Grub has passed control to the kernel). CTRL-ALT-DEL, poweroff, etc. This should cause a recordfail and the next time it boots it should halt at the Grub menu.

---

### Post by Sonicrulz12 on 2011-07-30
I tried pressing shift a second time and it worked sorry if i made you misunderstand but what i meant was i wanted to change my password and and when i was about to close the window where i changed the password i pressed the generate a password button on accident and closed the window

---

### Post by drs305 on 2011-07-30
> **Sonicrulz12 said:**
> I tried pressing shift a second time and it worked sorry if i made you misunderstand but what i meant was i wanted to change my password and and when i was about to close the window where i changed the password i pressed the generate a password button on accident and closed the window

Glad you got it solved. I just wasn't clear how getting the Grub menu to display was going to help... but no worries.

Please mark this thread solved via the 'Thread Tools' link at the top right of the first post if you have no more questions.

---

