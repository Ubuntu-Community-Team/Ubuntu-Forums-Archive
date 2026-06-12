---
title: "system monitor for netbook remix?"
date: 2009-12-03
forum: Ubuntu Moblin Remix
---

### Post by onesojourner on 2009-12-03
in a regular ubuntu install I like to keep a memory and cpu monitor open. I usually use the little system monitors in the top task bar. Is there any way to use these in unr?

---

### Post by Jackyboy86 on 2009-12-05
I've got it in my top bar in UNR.
Right click the bar at the top and 'add component' (i think. i'm on KDE ATM so can't check it)
Add System Monitor...

---

### Post by onesojourner on 2009-12-07
hmmm I don't have that option. Where on the top bar are you clicking exactly?

---

### Post by artsci2 on 2009-12-07
I trying UNR here at the coffee shop on my Toshiba A205-S5804.
Good so far.

I tried to click on the top menu to get the frequency scaling monitor. At first the only option I had was to "delete the panel"

after clicking that I then tried the right click on the task bar and got the "Add to panel" option and was able to set the frequency scaling monitor running in the task bar.

---

### Post by onesojourner on 2009-12-08
here are the only options I am getting when I right click on the top bar.

---

### Post by Yanneck on 2009-12-08
And there you could do it.
 Also you can open a shell and use 

```

top

```

---

### Post by Yanneck on 2009-12-08
Edit: Maybe Windowpicker hides your panel. So you have to remove it. ;-)

---

### Post by onesojourner on 2009-12-08
can you explain what you mean a little more?

---

### Post by Yanneck on 2009-12-09
Windowpicker is a small program that picks your windows. 
Rightklick on the Panel -> Remove it from the panel -> add something like windowchooser (I don´t know the name in english, sry) -> add your systemmonitor.

---

### Post by artsci2 on 2009-12-09
Onesoj, that is the same pulldown I had at first too. It seems that Yannek is right and the helper app window picker is hiding your real task bar. If you click on the "remove from panel" on the pull down menue in your screenshot then try again with a right click on the task bar, you will get the "add to panel option".

The remove does take away the window picker tabs that appear. I have not tried to reinstall window picker yet. I'll submit a bug report about the window picker not allowing access to the add to taskbar menue.

Edit:
I just tried reinstalling window picker and then right clicked on the middle of the task bar (see attached middle right click) then I right clicked a bit to the left of the task bar and got the desired and expected drop down menu (see attached a bit to the left). So the issue seems to be that the window switcher does not show itself and we didn't realize we were clicking on it instead of an unused section of task bar space.

---

### Post by onesojourner on 2009-12-11
Thanks artsci2. I think I am all set now.

---

