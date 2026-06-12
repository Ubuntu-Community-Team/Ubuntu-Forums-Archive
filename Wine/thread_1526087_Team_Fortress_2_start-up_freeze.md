---
title: "Team Fortress 2 start-up freeze"
date: 2010-07-07
forum: Wine
---

### Post by tmandpea on 2010-07-07
So I downloaded Wine 1.2 and all the necessary programs to run steam and games for steam. For a couple weeks Steam and Team Fortress 2 ran smooth (60 fps average), but all of a sudden when I load up Team Fortress 2 the game lags heavily in the start animation, and freezes when the "source" animation starts to fade away. I've also noticed that in the middle of the first animation the sound disappears. Before I was running Team Fortress 2 with -dxlevel 81. There is no way to exit the program when it freezes except to ctrl-alt-delete, and kill it with terminal. I'm open to all suggestions because I've tried everything I can think of. Thanks!

edit: I'm running Ubuntu 10.04

---

### Post by asdfoo on 2010-07-08
> **tmandpea said:**
> So I downloaded Wine 1.2 and all the necessary programs to run steam and games for steam. For a couple weeks Steam and Team Fortress 2 ran smooth (60 fps average), but all of a sudden when I load up Team Fortress 2 the game lags heavily in the start animation, and freezes when the "source" animation starts to fade away. I've also noticed that in the middle of the first animation the sound disappears. Before I was running Team Fortress 2 with -dxlevel 81. There is no way to exit the program when it freezes except to ctrl-alt-delete, and kill it with terminal. I'm open to all suggestions because I've tried everything I can think of. Thanks!

edit: I'm running Ubuntu 10.04

try reading the information on the appdb entry for this program, it probably suggests skipping the intro video.

also make sure you update to the latest version of wine, wine-1.2-rc6

---

### Post by jakejw93 on 2010-07-09
Like that guy said,If it crashes on the 'valve' video go to your launch options and in advanced options add ' -novid ' which gets rid of the start video for you

---

