---
title: "Raring OpenGL in Compiz"
date: 2013-03-29
forum: Ubuntu Development Version
---

### Post by ManamiVixen on 2013-03-29
Ok, after an update of Unity, the smart scopes were removed and I didn't realize it. So after reboot, Unity refused to load and after a bit of digging, I found my pre-preposed repo to be enabled. I sighed and I thought that was what caused the confict with the smart scopes and the crashing of Unity. So I reloaded my computer, renabled the smart scope ppa, made sure pre-perposed was disabled, and updated again. Thing is, after reboot, Unity still refused to load and I had no title boarders. So I opened a terminal and did "setsid unity" and it just exited with all pugins unloading. So I did "compiz --replace" to at least get boarders. There it got interesting. For some reason Compiz was reporting that my Nvidia Quadro 600 wasn't qualified to run Compiz or Unity due to the inability to run OpenGL. Does anyone have an explanation as to why that is happening? Also, after doing a ppa-purge of the smart scopes, Unity ran like normal.

---

### Post by mc4man on 2013-03-29
> **ManamiVixen said:**
>  For some reason Compiz was reporting that my Nvidia Quadro 600 wasn't qualified to run Compiz or Unity due to the inability to run OpenGL. Does anyone have an explanation as to why that is happening? 
Don't know what you got yourself in to with that prior update, as mentioned elsewhere didn't see issue.

As far as compiz reporting ..., I see that all the time in .xsession-errors, pay it no mind here, just some more Ubuntu/compiz nonsense. (not sure where/if you saw this..

Ex. - current, clipped 
> compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl
compiz (core) - Info: Unity is not supported by your hardware. Enabling software rendering instead (slow).
compiz (core) - Info: Unity is not supported by your hardware. Enabling software rendering instead (slow).
compiz (core) - Info: Starting plugin: opengl
compiz (core) - Info: Loading plugin: decor
compiz (core) - Info: Starting plugin: decor

(definitely not using software rendering despite what's reported

---

### Post by ManamiVixen on 2013-03-29
No, the error it gave was more along the lines of "Compiz failed to load GL Plugin. Hardware unsupported". It repeated this 7 times and then nothing. Nothing loads and I have to alt+ctrl+c the stop it.  Not even LLVM Pipe starts. Only on stock Unity does compiz load. Oh well.

---

### Post by grahammechanical on 2013-03-30
It think this is to do with the decision not to get Unity 7 and the 100 scopes into 13.04 before end of April. I had Unity 7 installed through a PPA. Today's update brought in Unity 6.12. The scopes were still there and working but a reboot brought a desktop without Unity, top panel or Launcher.

I got out of this by going a tty and

```
sudo apt-get install ppa-purge
```
```
sudo ppa-purge ppa:ubuntu-unity/experimental-prevalidation
```

and the rebooting.

Regards

---

### Post by ManamiVixen on 2013-03-30
Looks like the PPA is now defunct. There are users reporting the PPA regresses to Unity 6.2 and breaks the system. Bug is likely a result of that.

---

