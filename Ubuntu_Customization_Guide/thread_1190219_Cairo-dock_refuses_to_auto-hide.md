---
title: "Cairo-dock refuses to auto-hide"
date: 2009-06-17
forum: Ubuntu Customization Guide
---

### Post by malluen on 2009-06-17
I just installed and setup Cairo-dock from the cairo repositories (v2.05 + 2.05 plugis). Everything is smooth however auto-hide does not seem to work (although the older cairo-dock from the ubuntu repositories did). When I go to configure cairo-dock >> hidden dock >> click on 'jump to' it reads "The accessibility plug-in was not found. Be sure to install it in the same version of the dock to enjoy these features". Simple enough. Although I can't seem to find the plugin needed.

---

### Post by fabounet on 2009-06-18
this bug is fixed on the SVN.
you can simply go to Behavior -> Accessibility and there activate the "auto-hide" option ;) 
(the "keep below" is nice too)

---

### Post by GuiH on 2009-06-20
The problem may persist if you try to configure without a config script. 

Unfortunately we have looking for a config to simple make a perfect function of "auto hide dock when far away of mouse hover":popcorn:. 
You can only config to "accessibility hide", and make dock below others windows. 
To see your dock, minimize all windows (win+d) :D .

Mint: version 6.0 | Cairo: version 2.0.5

---

