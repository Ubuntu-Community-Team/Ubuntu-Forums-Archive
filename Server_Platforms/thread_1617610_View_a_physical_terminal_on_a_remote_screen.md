---
title: "View a physical terminal on a remote screen?"
date: 2010-11-09
forum: Server Platforms
---

### Post by semperverus on 2010-11-09
I'm having trouble figuring out how to get the terminal displayed on my serverbox to show up in a terminal on my laptop. I have a minecraft server running on ubuntu server edition 10.04 on a headless server. I also have a monitor, but it's a big bulky CRT and my girlfriend doesn't like having a huge amount of stuff tucked behind our chair where the router is (wifi wasn't working right, nor is it stable).

Essentially, when I ssh into the box, it creates a new terminal for me to input things on. That's nice when I need to edit stuff in the background, but when I want to input commands on the server directly, there's no real way to do that without blindly typing on my keyboard on the box itself. Not to mention, I can't see anything if something goes wrong. A friend of mine mentioned the 'screen' command, and that sort of works I guess, but it still doesn't show the minecraft server output, nor let me input.

tl:dr;
is there a way to get a physical terminal output to display on a remote ssh terminal screen?

---

### Post by arrrghhh on 2010-11-09
Screen probably is the best solution.  I don't use minecraft, does it just dump output on the main terminal session...?  Seems odd.  I use rtorrent, it starts on boot - it creates a screen session so I can always restore & check it if I want to, or daemonize it (like minimizing it) so it's not in my way.  Very handy.

---

### Post by semperverus on 2010-11-09
well, minecraft sort of takes over the input the same way nano does, except it's a trailing terminal like the regular linux terminal is, instead of an editor. You have to bust out of the minecraft terminal to get back to the regular one.

---

### Post by CharlesA on 2010-11-09
Use a screen session to run minecraft then.

Ctrl + Alt + D will detach.

I did find this: [http://forums.contribs.org/index.php?topic=43940.0](http://forums.contribs.org/index.php?topic=43940.0)

Can out the man entry for screen.

---

### Post by semperverus on 2010-11-09
> **CharlesA said:**
> Use a screen session to run minecraft then.

Ctrl + Alt + D will detach.
Ok, but then how do I re-enter it if I need to do something else or see something?

---

### Post by CharlesA on 2010-11-09
Run ***screen -R*** to reattach to the newest session.

---

### Post by semperverus on 2010-11-09
oh wait, i think i get it now. screen will store a separate terminal session on the server itself, i could name that screen after my username, then screen -r username or something like that to re-attatch in the future :D
Huzzah!

Much thanks :)

---

### Post by CharlesA on 2010-11-09
It's kinda like that. I don't know if you can name it specifically, but if you have more then one screen session around, you can list them by running this:

```
screen -ls
```

---

### Post by semperverus on 2010-11-09
Ok, I checked the screens manfile, it says screen -s will allow me to name the screen, and that means that I should go add that command to my startup scripts :P
(It's amazing how much trouble I can get myself into with what little I know)

---

### Post by arrrghhh on 2010-11-09
Yes, you certainly can name it with -s.  GLad you've got it workin :D  I love screen, not sure how I managed cli life without it ;)

---

### Post by CharlesA on 2010-11-09
> **arrrghhh said:**
> Yes, you certainly can name it with -s.  GLad you've got it workin :D  I love screen, not sure how I managed cli life without it ;)

Oh, that's cool. I didn't know that. :)

I love using screen, I can't believe how many SSH windows I used to have open when working on multiple things.

---

### Post by FuturePilot on 2010-11-09
Better yet, check out Byobu. It makes using Screen a breeze especially if you've never used screen before and/or don't want to spend hours configuring it.

---

### Post by CharlesA on 2010-11-09
> **FuturePilot said:**
> Better yet, check out Byobu. It makes using Screen a breeze especially if you've never used screen before and/or don't want to spend hours configuring it.

I checked it out and it confused the living hell out of me. Then again, maybe it was cuz I didn't know how to configure it correctly. :P

---

### Post by FuturePilot on 2010-11-09
> **CharlesA said:**
> I checked it out and it confused the living hell out of me. Then again, maybe it was cuz I didn't know how to configure it correctly. :P

Think of it almost like a window manager for a terminal. F2 creates new "windows" F3 and F4 cycle backwards and forwards through them respectively. Ctrl+A+D will detach your session and 'byobu -x' will reattach it. I have all my servers set up to automatically launch byobu on login and to disconnect I just have to detach my session. It's very convenient. All of this and more is configurable through a nice ncurses interface with the F9 key.

---

### Post by CharlesA on 2010-11-09
Oh nice. I was trying to get it to show each screen window in a tab, but I was having problems with it.

The documentation I was looking at leaves something to be desired, for sure.

---

