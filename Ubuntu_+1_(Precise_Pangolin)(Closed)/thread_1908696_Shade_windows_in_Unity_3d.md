---
title: "Shade windows in Unity 3d?"
date: 2012-01-13
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by loukingjr on 2012-01-13
sorry if this has been asked and answered but I didn't find it in a search. Is there a way to make Unity 3D shade windows by double-clicking the title bar?

thanks

---

### Post by effenberg0x0 on 2012-01-13
Sorry for answering with question: When you say "shade" you mean the compiz shade effect (roll-up as default), a change in alpha/opacity or something else I didn't catch? 

If you mean a change in alpha/opacity, I have something set via CCSM/obs plugin. Mine is set to increase opacity with alt+Button4 and decrease with alt+button5. It means I can hold alt and use the mouse wheel up/down to make a windows visible/transparent/invisible quickly. You can achieve something similar using the Color Opacify plugin and setting a mouse/keyboard command to add a fake argb to the active window. WHatever you choose, you can probably hack something to use a double click using ccsm/command plugin to associate a mouse command with a script that will simply push your desired compiz setting via gconftool-2.


EDIT: Ah, I found out. The definition of shade seems to be RollUp (only the app titlebar is left on screen). It is set on "CCSM/General Compiz Options/Toggle Window Shaded" to Ctrl+Alt+s. I think you can set that as the action for titlebar double-click via ubuntu-tweak, if it still works (no idea).

---

### Post by loukingjr on 2012-01-13
> **effenberg0x0 said:**
> Sorry for answering with question: When you say "shade" you mean the compiz shade effect (roll-up as default), a change in alpha/opacity or something else I didn't catch? 

If you mean a change in alpha/opacity, I have something set via CCSM/obs plugin. Mine is set to increase opacity with alt+Button4 and decrease with alt+button5. It means I can hold alt and use the mouse wheel up/down to make a windows visible/transparent/invisible quickly. You can achieve something similar using the Color Opacify plugin and setting a mouse/keyboard command to add a fake argb to the active window. WHatever you choose, you can probably hack something to use a double click using ccsm/command plugin to associate a mouse command with a script that will simply push your desired compiz setting via gconftool-2.
actually I meant roll up. if I dbl-clk the title bar it maximizes the window. I already have opacity set up. no need to apologize.

edit: I found the setting. in Advanced Settings>Windows there was a choice to Shade or Toggle Shade. Shade doesn't work. Toggle Shade does.

---

### Post by effenberg0x0 on 2012-01-13
> **loukingjr said:**
> actually I meant roll up. if I dbl-clk the title bar it maximizes the window. I already have opacity set up. no need to apologize.

Ok, as I edited above, I found it active via CCSM using ctrl+Alt+s, but there's no obvious way to associate it with a titlebar double-click. Some sites mention that it was possible to set using the ubuntu-tweak tool. Maybe you should give it a try. 

If it's not possible via this tool, we'll have to dig deeper into other settings. But it probably is doable.

---

### Post by loukingjr on 2012-01-13
> **effenberg0x0 said:**
> Ok, as I edited above, I found it active via CCSM using ctrl+Alt+s, but there's no obvious way to associate it with a titlebar double-click. Some sites mention that it was possible to set using the ubuntu-tweak tool. Maybe you should give it a try. 

If it's not possible via this tool, we'll have to dig deeper into other settings. But it probably is doable.

thanks, see above :D

---

### Post by cariboo on 2012-01-13
According to the Unity 5 testing we did yesterday, a double click on the title bar maximizes/restores the window size by design, I'm not sure if you can change the behavior to rollup/down by double-clicking.

---

### Post by effenberg0x0 on 2012-01-13
I found the relevant key:

<key>/apps/metacity/general/action_double_click_titlebar</key>

The possible values are described below. Shade is one of them. The default is toggle_maximize.

> Description: This option determines the effects of double-clicking on the title bar. Current valid options are 'toggle_shade', which will shade/unshade the window, 'toggle_maximize' which will maximize/unmaximize the window, 'toggle_maximize_horizontally' and 'toggle_maximize_vertically' which will maximize/unmaximize the window in that direction only, 'minimize' which will minimize the window, 'shade' which will roll the window up, 'menu' which will display the window menu, 'lower' which will put the window behind all the others, and 'none' which will not do anything. So, it's there. Not sure it works though.

---

### Post by xyzzyman on 2012-01-13
Install Ubuntu Tweak, and under 'Window Manager Settings' you can change 'titlebar double-click action' to 'Roll up' instead of 'Maximize'. Just tested in 11.10 and 12.04.

---

### Post by loukingjr on 2012-01-13
> **cariboo907 said:**
> According to the Unity 5 testing we did yesterday, a double click on the title bar maximizes/restores the window size by design, I'm not sure if you can change the behavior to rollup/down by double-clicking.
if you go into Advanced Settings(gnome-tweak-tool/Ubuntu Tweak)>Windows>action on title bar double-click and select Toggle Shade it rolls the window up and down. I'm using Unity 5 btw. An odd thing is I'm running 12.04 in VirtualBox on a Mac host but unlike 11.10, Unity3D works like a charm.

If I select 'Shade' it just maximizes the window. 'Toggle Shade' works as I mentioned above.

---

### Post by effenberg0x0 on 2012-01-13
Cool, You can activate/deactivate directly writing to That key via gconftool-2.

---

