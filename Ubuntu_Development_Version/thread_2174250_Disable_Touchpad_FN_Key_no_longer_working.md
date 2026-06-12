---
title: "Disable Touchpad FN Key no longer working"
date: 2013-09-13
forum: Ubuntu Development Version
---

### Post by sacridex on 2013-09-13
Hello,

I have a Lenovo Ideapad U410 and running 13.10 on it.
The Disable Touchpad Key did not work in 13.04, so I was truly happy with it working in 13.10.
But recently, this very FN Key is no longer working for me. I did not change anything in any settings, and all the other FN Keys are working fine.
Anyone has this issue as well?

Thank you

EDIT: Well what an coincidence, did some updates and now it works... Didnt check what updates had been done...
But still, it isn't working in 13.04 and I dont know if it isn't just working randomly here in 13.10.

---

### Post by Pako Pako on 2013-09-13
Wait, is the FN key not working, or just the disable-touchpad *feature*?

If the FN key was not working, you wouldn't be able to use the other keyboard shortcuts like auto-dim screen or mute-audio.

If the F2 button (IIRC, this was the button with disable-touchpad as a Fn function) isn't working, then you wouldn't be able to rename files (in Nautilus or PCman or Windows Explorer, the F2 is bound to the "rename" function).

---

### Post by sacridex on 2013-09-13
Well after a reboot, it is no longer working again. But the F6 key itself is working though(Jumps to address bar).
I guess the disable touchpad *feature* is not working then(at least sometimes).

I tried to get the keycode with *xev*, but the FN version has none.
The regular F6 button has a keycode. Some other FN keys do not have a keycode as well, but they are working!
And some FN Keys have a keycode and do work.

---

### Post by sacridex on 2013-09-14
A little update: Now the function is working again(for how long? ^^).
But still there is no keycode available with *xev*. Just in case this is helping.

How else is the key triggered?

---

