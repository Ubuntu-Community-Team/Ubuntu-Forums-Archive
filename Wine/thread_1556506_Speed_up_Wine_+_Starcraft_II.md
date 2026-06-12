---
title: "Speed up Wine + Starcraft II"
date: 2010-08-19
forum: Wine
---

### Post by JNCR on 2010-08-19
Hey all, does anyone know any ways to speed up Starcraft II in wine?

I ran wine as Windows 7 and that increased my speed.

I just added the registry entry HKEY_CURRENT_USER\Software\Wine\Direct3D\UseGLSL = false and it significantly increased my performance.

I want to run Starcraft II in its own x server (still trying to get that to work).  That should speed it up a little more.

Does anyone have any other tips to speed up wine for Starcraft II?

Thanks,
JNCR

---

### Post by lurker8 on 2011-02-16
To start Starcraft II in its own x-server:

1. Close anything important, as step 4 will end your current gnome session
2. Ctrl+Alt+F5  (F1 - F6 should also work)
3. Log in and run the following from the terminal
4. Command: "sudo service gdm stop" (this will end your current gnome session)
5  Command: "xinit :1" (this will open up a new xserver and display an instance of xterm)
6. In the new xterm run the following (move the mouse if xterm doesn't have focus):
7. Command: "ck-launch-session" (this got the sound working for me)
8. Command: "wine <Enter your path to StarCraft II here>"

Those are the basic steps.  I know this is a rather late response, but I  was searching for something else and found this and knew the solution.  Maybe someone else will find this and find it helpful?

---

### Post by deckoff on 2011-08-27
Nice . Unfortunately, it doesnt work for me :( I try to start a few old games in a seperate x-window. I dont have sound, even if using this method. Strangely, when I go back to tty5 ( or x0) if that matters, I hear the game - but I dont see it.
Any help or ideas, pulseaudio issue??

---

### Post by Erufailon on 2011-08-29
> **lurker8 said:**
> To start Starcraft II in its own x-server:

1. Close anything important, as step 4 will end your current gnome session
2. Ctrl+Alt+F5  (F1 - F6 should also work)
3. Log in and run the following from the terminal
4. Command: "sudo service gdm stop" (this will end your current gnome session)
5  Command: "xinit :1" (this will open up a new xserver and display an instance of xterm)
6. In the new xterm run the following (move the mouse if xterm doesn't have focus):
7. Command: "ck-launch-session" (this got the sound working for me)
8. Command: "wine <Enter your path to StarCraft II here>"

Those are the basic steps.  I know this is a rather late response, but I  was searching for something else and found this and knew the solution.  Maybe someone else will find this and find it helpful?

I followed the steps one by one and they worked but I had 2 problems. First, I could not connect to battle.net, I could play only offline (I suppose closing the session in step 4 shuts down all the connections). Second I didn't had any sound at all.

---

### Post by pAsM on 2011-08-30
> **Erufailon said:**
> I followed the steps one by one and they worked but I had 2 problems. First, I could not connect to battle.net, I could play only offline (I suppose closing the session in step 4 shuts down all the connections). Second I didn't had any sound at all.
Hello,
[INDENT]This actually makes sense, with Gnome-Network-Manager shutdown with GDM, you may have to establish networking manually if your on wireless. I cannot comment on the Sound because I typically play it muted.

In my case, SC2 runs very well on a stock install inside of wine (not in its own X session). I am also running Gnome3 and several apps in the background. I rarely have any performance issues or lag
[/INDENT]

---

