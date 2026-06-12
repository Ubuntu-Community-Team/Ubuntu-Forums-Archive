---
title: "X-Window wrapper for SheepShaver"
date: 2009-07-06
forum: Virtualisation
---

### Post by xris_xcess on 2009-07-06
Hi... 


 My goal: Set up a regular PC with a minimal ubuntu sytem that will run SheepShaver in fullscreen mode, with no other windowed processes.

 In other words, a kind of transparent "Clone". I've kind of got it working manually:

Pc boots --> log in --> startx --> run SheepShaver (no gui, boots straight up).

What I would like is to automate all of this. I know you can enable automatic login. But what about running SheepShaver in its own diplay? or starting X and then getting SheepShaver to run atomatically?

A simillar example would be with a web browser. Kind of a kiosk setup. No window manager or desktop, just the browser.

In a minimal sytem with just xorg (no gdm, gnome, etc), when one types startx you get an xterm window on tty7. I thought the if startx is loading xterm, why don't I just point startx to SheepShaver and skip xterm? I've been looking at where you can set this, but no luck yet.

Has anyone setup something similar, not necessarily with SheepShaver, but with X?

---

### Post by xris_xcess on 2009-07-09
Well, i've got A solution working... not all the way though:

I used rungetty to autologin to the account that runs SheepShaver and then added an xinitrc file to that users home folder that starts up SheepShaver in X. All working quite well up to here, except that when SheepShaver starts up, its window is pinned to the top left corner of the screen untill the OS switches from 600x400 to 800x600. I guess its a minor thing overall.

What I haven't been able to work out is how to shut down the machine when I shut down SheepShaver. I know I'm looking for some kind of monitoring daemon of sorts.

¿Does anyone know of one?

---

### Post by juancarlospaco on 2009-07-10
Disable GDM *(automatic X starting)*, and Try:
[B]sudo apt-get update && sudo apt-get install openssh-server && sudo apt-get clean

ssh -X $USER@localhost sheepshaver && sudo shutdown now[/B]

it brings up Sheepshaver and if its closed start a shutdown process.

---

### Post by afrodeity on 2009-12-14
If you get all this working would be interested in finished recipe and/or iso. I haven't managed to get it running with karmic.Hardy worked a charm.

---

