---
title: "Issues with left 4dead menu"
date: 2009-03-31
forum: Wine
---

### Post by Sqeaky_TheTrulyOpen on 2009-03-31
I have:
Wine 1.1.18
latest steam version - running
Left 4 dead
Ubuntu Linux 8.10

2gb ram
710 phenom 2 triple core
sapphire ATI 4850 - ati drivers seem to work fine for native linux games

The game installs fine and the movies play fine, but when I get to the main menu the text is invisible. 

Someone suggested I enable GLSL, but did not tell me how, so I (after some googling) made a registry key HKEY_CURRENT_USER\Software\Wine\Direct3D

with a UseGLSL string set to 1

I had to make Direct3D Key

This did not seem to have any affect

There is no CLI output, I have tried windowed mode and virtual desktop, and I have played with a few of the shader settings. it is set to windows xp, I have tried vista no change.

:( What should I try next?

---

### Post by asdfoo on 2009-04-01
> **Sqeaky_TheTrulyOpen said:**
> I have:
Wine 1.1.18
latest steam version - running
Left 4 dead
Ubuntu Linux 8.10

2gb ram
710 phenom 2 triple core
sapphire ATI 4850 - ati drivers seem to work fine for native linux games

The game installs fine and the movies play fine, but when I get to the main menu the text is invisible. 

Someone suggested I enable GLSL, but did not tell me how, so I (after some googling) made a registry key HKEY_CURRENT_USER\Software\Wine\Direct3D

with a UseGLSL string set to 1

I had to make Direct3D Key

This did not seem to have any affect

There is no CLI output, I have tried windowed mode and virtual desktop, and I have played with a few of the shader settings. it is set to windows xp, I have tried vista no change.

:( What should I try next?

I think GLSL has been enabled by default since wine-0.9.49...

l4d works ok here on nvidia, could be an ati only issue

---

### Post by Sqeaky_TheTrulyOpen on 2009-04-01
Then I guess I will try disabling it.


:( 

No Apparent effect

---

### Post by asdfoo on 2009-04-04
> **Sqeaky_TheTrulyOpen said:**
> Then I guess I will try disabling it.


:( 

No Apparent effect

Not sure what else to suggest, maybe setting OffscreenRenderingMode to fbo if you have not already.  In HKEY_CURRENT_USER\Software\Wine\Direct3D

---

### Post by Sqeaky_TheTrulyOpen on 2009-04-05
OffscreenRenderingMode

This made a noticeable improvement in reducing graphical corruption in other source based games (Portal :) ), I am sorting out some steam account issues, and I will test L4D as soon as possible.

i will also be updating my ati catalyst drives

---

