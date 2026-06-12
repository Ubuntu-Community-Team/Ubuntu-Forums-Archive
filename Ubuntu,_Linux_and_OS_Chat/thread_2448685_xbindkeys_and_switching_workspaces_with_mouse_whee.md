---
title: "xbindkeys and switching workspaces with mouse wheel + pause key"
date: 2020-08-11
forum: Ubuntu, Linux and OS Chat
---

### Post by Gottier on 2020-08-11
So, I use left handed mouse, and although (ctrl + alt + up) and (ctrl + alt + down) are not terrible for switching workspaces, I want to try to change that to the pause button + mouse wheel scrolling. From years of typing and right handed mouse usage, my right hand is damaged, and I have numbness in my index finger. Being able to customize the keyboard/mouse is really handy. I already use xbindkeys, and it seemed the right tool for the job, so I thought I'd give that a shot. This fails miserably, as xbindkeys for some reason ignores the pause button and switches workspaces anytime the mouse wheel scrolls.

So, I ran xbindkeys --key in the terminal, and when I press the pause/break key it outputs:
```
"(Scheme function)"
    m:0x10 + c:127
    Mod2 + Pause
```

Using xev, I determined that my mouse wheel up is **b:4** and my mouse wheel down is **b:5.**

All of that was important when adding the following lines to my ~/.xbindkeysrc file:
```
#I didn't actually add this line, just uncommented it
keystate_numlock = enable

#Go up to workspace
"xte 'keydown Control_L' 'keydown Alt_L' 'key Up' 'keyup Alt_L' 'keyup Control_L'"
  Mod2 + Pause + b:4

#Go down to workspace
"xte 'keydown Control_L' 'keydown Alt_L' 'key Down' 'keyup Alt_L' 'keyup Control_L'"
  Mod2 + Pause + b:5
```

After I add those lines I run xbindkeys in the terminal, and then when I use the mouse wheel to scroll it switches workspaces, even when the pause key is not depressed. Even more frustrating is that if I go back to the ~/.xbindkeysrc file and comment out the lines, then run xbindkeys in the terminal again, the behavior does not revert back to normal. I have to uninstall xbindkeys to get it to stop binding to the mouse wheel.

I was hoping that somebody here would have a clue as to what is going on. There's not much information about this that I could find by searching around the internet.

Thank you.

---

