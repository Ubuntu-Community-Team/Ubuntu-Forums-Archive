---
title: "Metacity now installed w/gnome-session-fallback"
date: 2012-08-23
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by kansasnoob on 2012-08-23
I was just doing some very limited, lazy testing and I was curious about the future of metacity and the gnome classic (no effects) session in Quantal so I installed the QQ 20120822-i386 daily on my Intel box (the old VIA box is a no-go with it's P4M800 graphics) and both the classic session and classic (no effects) still work :D

Compiz is a mess but I don't care about that. The (no effects) session using metacity seems no different than it did in Precise, but I haven't tried my typical mods yet.

The real challenge is going to be how to install Ubuntu + classic on a box w/graphics not supported by the new Compiz + llvmpipe scheme :confused:

Twill be fun ;)

---

### Post by dino99 on 2012-08-23
Seems like metacity will be dropped soon; so i hope gnome-classic be able to work without it. But today upgrades want to uninstall gnome-session-fallback ;)

Will wait for a possible tweak before uninstalling it as its my favorite choice.

note: got a new metacity upgrade compatible with gnome-session-fallback, but still some issues now with compiz needing also some updates.

---

### Post by jbicha on 2012-08-23
Metacity won't be dropped. Compiz does need to be rebuilt against the updated metacity which should happen later today.

---

### Post by kansasnoob on 2012-08-23
> **jbicha said:**
> Metacity won't be dropped. Compiz does need to be rebuilt against the updated metacity which should happen later today.

I'm wondering about the future of the 18 old boxes I maintain with P4M800 graphics. I know they kind of suck anyway because they don't support full screen flash video, but that's why I spent a lot of time cooking up a classic (no effects) scheme for Precise:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

That gives me 5 full years to ponder what to do next :)

No real worries because openbox is decent enough, but metacity has long been my favorite window manager.

I just can't help but wonder about the future of metacity since Gnome is moving to mutter (metacity + clutter) and Ubuntu is moving to Compiz + llvmpipe.

I did play with a CLI install via Ubuntu alternate image earlier to see if I could do a "cleanish" install of 'gnome-session-fallback' but even after working through the xserver and lightdm crap I get the graphics check = fail warning :(

No big deal, I need to test some Lubuntu images real soon anyway. It's all good fun to me, but if you ever want me to test something just shout :guitar:

---

### Post by jerrylamos on 2012-08-24
My netbook, notebook, tower have the latest GUI capabilities - currently I'm running QQ + LXDE desktop installed on top.  I'll give a whirl with Gnome Ubuntu to see what that's like. CLI "top" shows no Unity or Compiz cycles. 

My choice, effects are for game code and I don't choose to have default Ubuntu code using up processor cycles too.  

Well, I use GUI desktop when I can for convenience and especially reducing my flying fingers problems with CLI.

If I notice a metacity no effects cookbook I'll give it a try.

Jerry

BTW, on the side I'm running Raspberry Pi with Debian LXDE.  At 900 mHz and 256 MB ARM processor not something Ubuntu is interested in.

---

### Post by cariboo on 2012-08-24
> **jerrylamos said:**
> My netbook, notebook, tower have the latest GUI capabilities - currently I'm running QQ + LXDE desktop installed on top.  I'll give a whirl with Gnome Ubuntu to see what that's like. CLI "top" shows no Unity or Compiz cycles. 

My choice, effects are for game code and I don't choose to have default Ubuntu code using up processor cycles too.  

Well, I use GUI desktop when I can for convenience and especially reducing my flying fingers problems with CLI.

If I notice a metacity no effects cookbook I'll give it a try.

Jerry

BTW, on the side I'm running Raspberry Pi with Debian LXDE.  At 900 mHz and 256 MB ARM processor not something Ubuntu is interested in.

Actually there is ongoing work to get Quantal to run on an arm processor. Check the QA mailing list.

---

