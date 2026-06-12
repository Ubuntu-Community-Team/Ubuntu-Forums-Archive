---
title: "Age of Mythology causes logout"
date: 2009-11-02
forum: Wine
---

### Post by Altay_H on 2009-11-02
I initially installed wine to play Age of Mythology back when I first used Ubuntu. Using Hardy Heron (and an older version of wine) I had no significant problems. However, in both Jaunty Jackalope and Karmic Koala Age of Mythology works perfectly only until the movie sequence ends. Immediately after the movie player finishes (whether it's allowed to play the entire sequence, or it's skipped at some point) Ubuntu logs out. This not only makes the game unplayable, but also causes it to essentially crash any other programs that may be running. Does anyone have any ideas?

I tried using older version of wine, but every version since 1.0 causes Ubuntu (9.04 & 9.10) to log out. I'd go back to using Hardy Heron, but if I'm going to let video game compatibility determine which operating system I use, I might as well use Windows. Did the way Ubuntu logs out change from 8.10 to 9.04? Honestly I'm slightly more interested in finding out what's causing this behavior than solving it. Thanks in advance for any ideas.

---

### Post by Falc7 on 2009-11-02
I have this problem on one of the laptops in the family, the solution i use is to not run the game in full screen, i did this by emulating a virtual desktop

---

### Post by Altay_H on 2009-11-02
> **Falc7 said:**
> the solution i use is to not run the game in full screen, i did this by emulating a virtual desktop
Could you please go into more detail? When you say "virtual desktop" are you referring to a virtual machine?

---

### Post by Falc7 on 2009-11-03
Nope, go to configure wine-> add application-> select AOM-> then go to graphics tab-> tick the box emulate virtual desktop-> play around with the resolution of the virtual desktop-> press ok -> play

Once you are ingame i also found selecting 'run in a window' from the game options to be useful

I plan to install AOM again soon, if this dosen't work i can get it working on mine and post exactly step-by-step on what i do. The above is the solution from memory

---

### Post by Altay_H on 2009-11-03
Thanks. When I emulate a virtual desktop Age of Mythology successfully runs, although the sounds doesn't work. It tells me something about not recognizing my sound hardware. That's not too big a problem though.

My main concern is that it's very difficult to play when it's not full screen. The lower gnome panel covers parts of buttons in the menus and the favor resource in game. It also makes it impossible to use the cursor to scroll the view down in game. Is there a way to either make the emulated desktop full screen or to confine the cursor to the game window? Maximizing the window doesn't work and choosing "Allow DirectX apps to stop the mouse leaving their window" from Wine configuration doesn't do anything. Any ideas?


> **Falc7 said:**
> I plan to install AOM again soon, if this dosen't work i can get it working on mine and post exactly step-by-step on what i do. The above is the solution from memory
I'll look forward to hearing how that goes.

---

### Post by Falc7 on 2009-11-05
Okay try changing to size of the virtual desktop to be exactly the same size as you display resolution, then select play in window. It is effectively full screen and works perfectly :) no bars or something

---

### Post by bi9kahuna on 2009-11-07
I actually ran into this problem before upgrading to Karmic (I was running a newer version of Wine from winehq), so I am pretty sure this something that has been caused by Wine, not your upgrade to Karmic.  Avoiding full-screen mode was the only thing that I found that solved it. sort of (although other Wine applications work fine full screen).

---

### Post by raj7095 on 2009-11-07
I installed age of mythology using a program called playonlinux and now it works perfectly fine. I don't know for sure if it will work for you because it crashes in jaunty jackalope.

---

