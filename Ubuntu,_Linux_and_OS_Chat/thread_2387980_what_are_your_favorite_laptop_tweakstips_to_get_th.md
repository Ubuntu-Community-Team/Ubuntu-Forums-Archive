---
title: "what are your favorite laptop tweaks/tips to get the most from your sceen size?"
date: 2018-03-26
forum: Ubuntu, Linux and OS Chat
---

### Post by kerry_s on 2018-03-26
hi all,
i'm looking for tweaks/tips, just want to know what others are doing.

i'm currently using gnome on pop!_os. so far i've found gnome to be the easiest set & forget kinda setup, cause i can get it to automate the tasks. for example: i like to multi-task so i would normally drag windows to the edge to split the screen. then i found **tilingnome** it does it automagically just open your apps & bam! i don't have to manually do it anymore.

another great tweak i found on the net, is to collapse firefox tabs when there's only 1 tab, it's done via userChrome.css

```

#tabbrowser-tabs, #tabbrowser-tabs > .tabbrowser-arrowscrollbox {
	min-height: 0 !important;
}

#tabbrowser-tabs tab[first-tab="true"][last-tab="true"] {
	visibility: collapse;
}

#tabbrowser-tabs .tabs-newtab-button { 
	visibility: collapse !important;
}

#tabbrowser-tabs tab {
	min-height: var(--tab-min-height)
}


```

i've tried a lot more things, but these 2 tweaks i've found to be the simplest but makes a huge difference in use.
[ATTACH=CONFIG]279104[/ATTACH][ATTACH=CONFIG]279105[/ATTACH]

---

### Post by lighthousebeacon on 2018-03-26
Ubuntu Mate 16.04.4
My old Dell laptop res is 1366x768, hard to find nice wallpaper to fit perfectly. But if I dl in 3840x2160 res, it scales images down perfectly to that size using gimp or pinta.
Decrease swap use, inode cache, and intel graphics --> [https://sites.google.com/site/easylinuxtipsproject/speed](https://sites.google.com/site/easylinuxtipsproject/speed)
Use HUD, top panel applet.
Use workspace switcher (great for multi-tasking)

---

### Post by kerry_s on 2018-03-26
i got the same res1366x768. mate's nice, i like that each corner can give half of a half window snap, same with xfce, 4 corner window snap.
mate & xfce have got the best panel/panels for tweaking, a lot of options.

thanks for the input.

---

