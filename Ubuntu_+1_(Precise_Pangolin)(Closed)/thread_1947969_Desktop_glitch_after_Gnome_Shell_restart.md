---
title: "Desktop glitch after Gnome Shell restart"
date: 2012-03-27
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by sgage on 2012-03-27
I am experiencing the following buglet in Gnome Shell. I believe it first showed up in 3.3.92, but it still exists in 3.4.0:

After restarting the shell (Alt-F2, r) the desktop display of the wallpaper is glitched. It's as though a copy of the wallpaper is being displayed down and to the right, and is superimposed on the normal, proper presentation of the wallpaper.

I tried to look this up on launchpad, but I seem to have bad luck finding pre-existing bugs there. Does anyone else experience this?

---

### Post by Gregory Lee on 2012-03-27
Yes, I got that, too, starting yesterday afternoon.  I gave up and used Unity for a while.  But after updating a short while ago and doing a cold reboot, I'm up again in Gnome Shell 3, and everything looks okay again.

(I did have a problem getting the computer shut down, though.  I had to use the power button.)

---

### Post by sgage on 2012-03-27
> **Gregory Lee said:**
> Yes, I got that, too, starting yesterday afternoon.  I gave up and used Unity for a while.  But after updating a short while ago and doing a cold reboot, I'm up again in Gnome Shell 3, and everything looks okay again.

(I did have a problem getting the computer shut down, though.  I had to use the power button.)

I installed an extension that puts a "Restart Shell" in your user menu, and it reloads the shell without incident. "gnome-shell --replace" works fine. But if you restart via alt-F2/r, the glitch occurs. 

Oh well!

---

### Post by sgage on 2012-03-29
> **sgage said:**
> I installed an extension that puts a "Restart Shell" in your user menu, and it reloads the shell without incident. "gnome-shell --replace" works fine. But if you restart via alt-F2/r, the glitch occurs. 

Oh well!

No, the glitch is still there for me. All updated. Even using the aforementioned extension, the glitch still occurs. Oh well, just have to wait...

---

### Post by lyka on 2012-03-29
Is it something like this?

If so i'm experiencing the same problem..

---

### Post by Flywaver on 2012-03-29
Same here....glitch appears of I restart shell with ALT-F2 r

---

### Post by sgage on 2012-03-29
> **lyka said:**
> Is it something like this?

If so i'm experiencing the same problem..

Sort of... mine is more like this:

---

### Post by macstevejb on 2012-03-29
Yes I can confirm...I'm getting exactly the same

regards,

Steve

---

### Post by xzy3186 on 2012-04-06
> **sgage said:**
> I am experiencing the following buglet in Gnome Shell. I believe it first showed up in 3.3.92, but it still exists in 3.4.0:

After restarting the shell (Alt-F2, r) the desktop display of the wallpaper is glitched. It's as though a copy of the wallpaper is being displayed down and to the right, and is superimposed on the normal, proper presentation of the wallpaper.

I tried to look this up on launchpad, but I seem to have bad luck finding pre-existing bugs there. Does anyone else experience this?

Still exist. I suffered this bug after upgrading to gnome-shell 3.4 in both archlinux and ubuntu

---

### Post by creosote on 2012-04-06
I have the same issue.

Fully updated 12.04 beta 2, Gnome-shell 3.4,Intel 945 GM

If i use Advanced settings and turn off "Have file manager handle the desktop", problem disappears.

---

### Post by sgage on 2012-04-06
> **creosote said:**
> I have the same issue.

Fully updated 12.04 beta 2, Gnome-shell 3.4,Intel 945 GM

If i use Advanced settings and turn off "Have file manager handle the desktop", problem disappears.

You're right. Some interaction between GS and nautilus I guess.

---

