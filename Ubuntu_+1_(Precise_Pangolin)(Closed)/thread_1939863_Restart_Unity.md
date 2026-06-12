---
title: "Restart Unity"
date: 2012-03-12
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by psych1610 on 2012-03-12
I've been looking for a way to restart Unity in Precise. Most of the threads and searches google turns up refers to 11.04 or 11.10. While I thought these methods would work they don't seem to on my machine.

In particular, I've tried methods in these two questions.

[http://askubuntu.com/questions/38579/how-do-i-restart-an-unity-session-from-the-terminal](http://askubuntu.com/questions/38579/how-do-i-restart-an-unity-session-from-the-terminal)
[http://askubuntu.com/questions/46788/is-it-possible-to-restart-the-unity-panel-without-restarting-compiz](http://askubuntu.com/questions/46788/is-it-possible-to-restart-the-unity-panel-without-restarting-compiz)

compiz --replace hangs somewhere (usually) or completes but doesn't seem to restart. Unity --replace or plain old Unity either results in a segfault or it hangs right after initializing plugins. I've tried these methods both from the terminal, the "run" dialog, and by dropping down to a shell ctrl + alt + f1.

Does anyone have a reliable way to restart Unity or am I the only one experiencing these seg faults? I know apport (I think) tried to automatically report one but I'm not sure where it is and for the life of me I can't seem to find the relevant log that would have something like this.

---

### Post by dino99 on 2012-03-12
log out/in

---

### Post by rburkartjo on 2012-03-12
or you could use alt+printscreen+k. this will bring you back to the login screen. note that you will not be able to save anything you have opern

---

### Post by psych1610 on 2012-03-12
@dino99, logging out and logging in would do the trick, yes :) What I should have mentioned was that I was looking at a method to use in case I couldn't use Unity/Menu bars like today when I accidentally "shook" Chromium to maximize it and the orange overlay filled up the whole screen and didn't respond to any other keys. 

Or when I updated Ubuntu today and upon restarting I was greeted with a blank desktop with no Unity and no top panel.

The shortcut mentioned by rburkartjo will hopefully do the trick next time.

Thanks to the both of you.

As an aside, is anyone else having problems with the methods mentioned in the threads (typing Unity, Unity --replace & disown, Compiz --replace, etc), or is it just me? Are these supported ways that would be worth filing a bug for?

---

### Post by castrojo on 2012-03-12
Running "unity" shouldn't crash it, when you run that does the apport thing pop up saying there was a crash?

---

### Post by ubuntu27 on 2012-03-13
I don't know about just restarting Unity, but you could try killing the X Server.

Open the **keyboard** **preferences** (Search for keyboard in Dash), go to the Layout tab and press Options. Open Key sequece to kill the X server and toggle Control + Alt + Backspace

[http://askubuntu.com/questions/39571/how-to-set-keyboard-combination-to-kill-the-x-server](http://askubuntu.com/questions/39571/how-to-set-keyboard-combination-to-kill-the-x-server)


When done, you can kill the X server by "Control + Alt + Backspace"."

---

### Post by psych1610 on 2012-03-13
> **castrojo said:**
> Running "unity" shouldn't crash it, when you run that does the apport thing pop up saying there was a crash?

Good day, running unity command from alt+f2 doesn't seem to do anything, at least not anything visible. 

Running unity command or unity --replace from either a terminal or dropping down to a shell (I think that's what it is) by pressing ctrl+alt+f1 usually results in a seg. fault with a message right before it saying screen geometry has changed. Unfortunately this usually results in no Unity, no top panel, and no recognition of key presses in what used to be the Gnome environment making "sudo reboot" from ctrl+alt+f1 screen the only way to get out of this.

Oh, and to actually answer your question, no, the apport thing doesn't pop up.

---

### Post by VinDSL on 2012-03-13
> **dino99 said:**
> log out/in

> **psych1610 said:**
> @dino99, logging out and logging in would do the trick, yes :) What I should have mentioned was that I was looking at a method to use in case I couldn't use Unity/Menu bars like today when I accidentally "shook" Chromium to maximize it and the orange overlay filled up the whole screen and didn't respond to any other keys.
I guess that I  don't exactly understand the question, but...

On my Unity desktop, I've done a lot of customization, and avoid resetting/restarting Unity, like the plague.  It's akin to doing a fresh install.  LoL!  :D

So, when Unity goes janky, I do as Dino recommended and log out / log in.  99.9% of the time, that restores Unity.

On the other hand, if something goes awry, and I can't log out / log in (for whatever reason) I simply Alt-Crtl-F1, followed by an Alt-Ctrl-Delete in the terminal.  

This, of course, will restart Ubuntu et al.  But, IMO that's preferable to having to reconfigure my custom Unity DE from scratch.  ;)

---

