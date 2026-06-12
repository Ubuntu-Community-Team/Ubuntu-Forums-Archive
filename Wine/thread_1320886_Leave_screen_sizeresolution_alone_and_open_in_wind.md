---
title: "Leave screen size/resolution alone and open in windowed"
date: 2009-11-09
forum: Wine
---

### Post by Imoen on 2009-11-09
I am trying to get the sims 3 to play with playonlinux. It installs fine but then when I try to start the game makes my screen go to black/no signal. I can hear the game starting by the sound so I know it is running. I tried setting the wine settings to use the same desktop size as my normal settings but it made no difference. Is there a setting that I can set to force Wine to run the game in the same resolution/size as my desktop is?

Also I was wondering if there's a way to have games run in windowed mode instead of full screen.

---

### Post by beastrace91 on 2009-11-09
Force a Wined application to run in a virtual desktop to run it windowed. By virtual desktop I meant opening your WineCFG (Applications->Wine->WineCFG or in terminal winecfg) and clicking over to the graphics tab and selecting "run in a virtual desktop". (This will force all your Wined apps to run in a window of the defined dimensions.)

Regards,
~Jeff

---

### Post by Imoen on 2009-11-11
Awesome, thanks!

---

