---
title: "&quot;Ubuntu is running in low graphics mode&quot;: Unable to click &quot;OK&quot; button."
date: 2012-01-20
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2012-01-20
When updating kernel releases without rebuilding NVidia kernel module, I get a 640x480 blackscreen with a single GTK dialog saying "Ubuntu is running in low graphics mode" and a single button labeled "OK". 

This button is not selected and I cannot find a way to focus it. There's no mouse. Using the keyboard "tab" key doesn't work to select the button. Unplugging/plugging different models of USB/PS2 mouse/Keyboard doesn't work. At this point all I can do is switch to another VT, kill X, and proceed to rebuilding the VGA module and restart the DM.

A fun fact is that, although there are no remaining X sessions running, if I restart the DM and login to Unity at this point, as I always did, now no GUI application works. The error is that DISPLAY=:0.0 was not found. If I try DISPLAY=:1.0 <application> it works normally. 

And this happens even if there's a single monitor connected to the PC. There's no other X running in any other VT than 7. VT1-6 are at tty login screen and 8 to 12 are blank, as expected. I can't understand it.

Rebooting makes it all OK again.

---

### Post by kyleabaker on 2012-01-20
I've seen this behavior as well a week or two ago. I've since began installing nvidia drivers from the repo's again.

From time to time I was able to get a mouse cursor to appear, but most often it was invisible and still highlighting things.

---

### Post by effenberg0x0 on 2012-01-20
> **kyleabaker said:**
> I've seen this behavior as well a week or two ago. I've since began installing nvidia drivers from the repo's again.

From time to time I was able to get a mouse cursor to appear, but most often it was invisible and still highlighting things.

This is interesting, I really assumed the mouse wasn't there at all - didn't think of the invisible mouse cursor possibility. When you got past that button, did it successfully loaded the desktop in Low Graphics mode?

---

### Post by kyleabaker on 2012-01-20
> **effenberg0x0 said:**
> When you got past that button, did it successfully loaded the desktop in Low Graphics mode?

No. I was never able to get the low graphic mode to work when that happened.

---

### Post by mc4man on 2012-01-20
Saw this today on the current daily live image when trying to do a log out during the live session (which does not work no matter what

During one attempt to recover from the black screen/blinking cursor got the "Ubuntu is running in low graphics mode": Unable to click "OK" button prompt but at that point it seemed the touchpad & keyboard became inactive so nothing to do but power down

---

### Post by effenberg0x0 on 2012-01-20
Thanks guys, I'll report it as soon as I get a break here. I guess the low-graphics mode dialog is OK and obviously better than the "Black Screen" threads we see every day. But it should work.

Regards,
Effenberg

---

### Post by kyleabaker on 2012-01-21
> **effenberg0x0 said:**
> ...But it should work.

+1 Please post the bug report link as well so we can all track it!

---

### Post by Fitoschido on 2012-01-24
This also affects me (Atom netbook). As a workaround, press Ctrl+Alt+F1, log in with your user name and password and do:

sudo pkill xorg
startx

And use the computer.

---

### Post by mdhollis on 2012-01-24
I don't know if this is the same issue....... but this happened to me on a fresh install about a month ago.  I purged the nvidia-173 driver and installed the current driver in tty1 and this resolved it.  I also couldn't run in low graphics.  I believe apport ran once I logged in and the bug was already reported but I can't seem to find it now.

---

### Post by mdhollis on 2012-01-24
I found the bug report...........if this is even the same issue.

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/576648]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/576648")

---

### Post by Fitoschido on 2012-01-24
I just discovered that my problem was completely unrelated, so sorry about the noise.

---

