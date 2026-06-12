---
title: "cannot drag and drop normally, even with gksu"
date: 2014-03-29
forum: Ubuntu Development Version
---

### Post by ventrical on 2014-03-29
A very tedious testcase #5 while trying to drag and drop a .mp4 file to /srv/. You have to go to terminal and open thunar with gksu, then, drag to desktop, then, open /srv/ and drag from desktop to /srv/ an illogical extra step that can be confusing and is not well explained in the testcase.5.  It is not even assumed that you have to use root or gksu and it should be added in the testcase profile.


[https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1299496](https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1299496)

---

### Post by QDR06VV9 on 2014-03-29
> **ventrical said:**
> A very tedious testcase #5 while trying to drag and drop a .mp4 file to /srv/. You have to go to terminal and open thunar with gksu, then, drag to desktop, then, open /srv/ and drag from desktop to /srv/ an illogical extra step that can be confusing and is not well explained in the testcase.5.  It is not even assumed that you have to use root or gksu and it should be added in the testcase profile.


[https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1299496](https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1299496)
Hey Vent have you tried to use the control <keyboard> Then drag and drop.
so in other words hold <control> click and hold the file you are moving drop to where you want.

---

### Post by ventrical on 2014-03-29
> **runrickus said:**
> Hey Vent have you tried to use the control <keyboard> Then drag and drop.
so in other words hold <control> click and hold the file you are moving drop to where you want.


Don't work. It only copies a shortcut or bungy-boings back and forth. I succeeded once from desktop to home but that was it.

edit:

I think it has something to do with the way the desktop is set up here at this end. I did not go to any great trouble to tweak this install.. just test the image, so maybe there is some tweaks needed.

---

### Post by QDR06VV9 on 2014-03-29
> **ventrical said:**
> Don't work. It only copies a shortcut or bungy-boings back and forth. I succeeded once from desktop to home but that was it.

edit:

I think it has something to do with the way the desktop is set up here at this end. I did not go to any great trouble to tweak this install.. just test the image, so maybe there is some tweaks needed.
The reason I was asking I had run into this on Ubuntu-Studio also. But I had better results with key-combo.

---

### Post by ventrical on 2014-03-29
> **runrickus said:**
> The reason I was asking I had run into this on Ubuntu-Studio also. But I had better results with key-combo.


 I had a lot better results with UStudio also.

---

