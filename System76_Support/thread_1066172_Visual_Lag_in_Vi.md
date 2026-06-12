---
title: "Visual Lag in Vi"
date: 2009-02-10
forum: System76 Support
---

### Post by chez17 on 2009-02-10
I am having weird issues with vi. When I move up and down there is a "visual lag" where the lines are off. If I click on the window with the mouse, everything gets fixed. I haven't noticed it in any other program, however vi is the only terminal based editor I use. I have vim-full installed.

Pangolin: Panp4n
Intrepid 64 bit
NVidia GeForce 9300M GS

---

### Post by thomasaaron on 2009-02-10
Whew. I know approximately squat about Vim. I like Gedit! And nano if I have to use a CLI editor.

Can you tell me exactly how to reproduce and recognize the problem? I'll see if I can duplicate it.

Oops! One other thought...

Disable desktop effects and see if it still happens (System > Prefs > Appearance > Visual Effects > None. Could be a compiz bug.

---

### Post by Guille Damke on 2009-02-10
I use vi in a Pangolin and have no lag. Probably the "vi-full", which is described as a "transitional package" in Synaptics package manager can cause problems? (I have no idea actually). I have installed "vim-nox" and works fine, probably you can uninstall vim-full and try vim-nox.

---

### Post by chez17 on 2009-02-11
Tom,

I think you are correct, it's look like this is a compiz issue. Thanks for the help.

Dave

---

