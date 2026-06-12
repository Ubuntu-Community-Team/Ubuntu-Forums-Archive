---
title: "Alt+Tab in WOW Makes WOW unplayable"
date: 2008-01-05
forum: Ubuntu Gamers Arena
---

### Post by tssom on 2008-01-05
When ever I alt+tab in WOW, it glitches up something bad. So i have to restart the game.
Anyone know of a workaround for this?

Running with latest wine, On DirectX.

*update*
Changed to opengl, 
Seems like i can alt+tab now, but my screen turns black, the game returns to normal when i alt+tab again.
That implies that it is working more or less. 

Any help appreciated.

Thanks

tssom

---

### Post by Dreamlocked on 2008-01-11
I have a problem alt-tabbing WoW when the compositor is turned on.
If you don't need/use transparency, you could turn the compositor off?

---

### Post by airtonix on 2008-08-31
1. turn off compiz
2. set wow to windowed mode
3. set wow to maximised mode
4. prefix your wow command with aoss to allow yourself to also run ventrilio if required.
5. alt+f2(or however you summon the run dialog box) : type gconf-editor, then press enter
6. /apps/metacity/global_keybindings/panel_run_dialog : change to <Super>r
7. /apps/metacity/global_keybindings/show_desktop : change to <Super>d
8. /apps/metacity/general/mouse_button_modifier : change to <Super>


should fix some of your more superficial problems.

Last three affected more since I was a healer using grid & clique. metacity originally uses the alt key for window operations...and so when i would hold alt in wow and try to click on the tanks unit frame, it ended up attempting to drag the wow window around. Changing the metacity keybindings fixed this.

---

### Post by donkyhotay on 2008-09-30
I've found most games running fullscreen in wine have trouble with alt-tabbing. On my system I have desktop effects permanently disabled (I don't like the way they look) and even starcraft gives me problems when alt-tabbing. Personally I just make it a point to never alt-tab when using any program in wine.

---

