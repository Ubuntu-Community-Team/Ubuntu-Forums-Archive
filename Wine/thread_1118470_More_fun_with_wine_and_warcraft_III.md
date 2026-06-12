---
title: "More fun with wine and warcraft III"
date: 2009-04-07
forum: Wine
---

### Post by harujai on 2009-04-07
I apologize ahead of time if this is in the wrong place. I've got wine to run warcraft fine, but the graphics are absolutely horrendous. I'm running the open source drivers currently. This is my terminal output

[email]harujai@harujai-desktop:~/.wine[/email]/drive_c/Program Files/Warcraft III$ wine 'Frozen Throne.exe' -opengl
fixme:mixer:ALSA_MixerInit No master control found on AK5370          , disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
err:ole:CoCreateInstance apartment not initialised
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x33f2e4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f658,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f690,0x00000000), stub!

---

### Post by Stunts on 2009-04-07
Hello!
What are your specs? You say you are using Open source drivers, but to what card?
Let's see what I can do for you.

---

### Post by harujai on 2009-04-07
I'm using a Radeon 3650. I just tried using the Ati/Ambd proprietary FGLRX drivers (something i really didnt want to do), and there was some texture issues (some things on the startup screen) were black. However, the game seemed to have 30 fps. On the flipside, program windows leave chaser artifacts. Thoughts?

I'm going to try turning off some of compiz effects and see if that removes the artifacts when programs startup.

---

### Post by Stunts on 2009-04-07
ATI + wine usually = trouble. But I think it can be done tough.
Compiz is also known to cause trouble with War3 under wine (hell, even on my nVidia it causes trouble), you would do well to try without it.
```
 metacity --replace
```
Doing this should drastically improve your framerate, and stop the dragging windows.
Some people report that runing
```
wine 'Frozen Throne.exe' -opengl -windowed
```
also improves performance.
I'd give that a shot.
Let me know what you got afterwards.

---

