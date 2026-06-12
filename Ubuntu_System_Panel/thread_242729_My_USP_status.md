---
title: "My USP status"
date: 2006-08-24
forum: Ubuntu System Panel
---

### Post by Romu on 2006-08-24
Hi all, 
I'm using dapper on a Dell Inspiron with XGL/Compiz and USP.

Here is a little status of the USP 0.41 :
- Custom color doesn't work except for titles (Applications, Places...)
- Panel size doesn't work,
- Border size doesn't work, I can see a size change of the whole panel, but no border

A question : will it be possible to animate the expand/collapse of USP with the XGL/Compiz effects (like the standard Ubuntu menu)?

Thanks.

---

### Post by chanders on 2006-08-24
> **Romu said:**
> Hi all, 
I'm using dapper on a Dell Inspiron with XGL/Compiz and USP.

Here is a little status of the USP 0.41 :
- Custom color doesn't work except for titles (Applications, Places...)
- Panel size doesn't work,
- Border size doesn't work, I can see a size change of the whole panel, but no border

A question : will it be possible to animate the expand/collapse of USP with the XGL/Compiz effects (like the standard Ubuntu menu)?

Thanks.

1. Did you check the use_custom_color key?
2. Panel size was meant to help Metacity users..
3. Did you set the border color? If possible post a screenshot of your gconf-editor let me see what settings you have..

Currently GTK does not support any sort of animation per se. All animation would have to be done by compiz. Come to think of it, somrthing like the showdesktop plugin would be nice :wink:

---

### Post by Romu on 2006-08-24
> **chanders said:**
> 1. Did you check the use_custom_color key?
2. Panel size was meant to help Metacity users..
3. Did you set the border color? If possible post a screenshot of your gconf-editor let me see what settings you have..

Currently GTK does not support any sort of animation per se. All animation would have to be done by compiz. Come to think of it, somrthing like the showdesktop plugin would be nice :wink:

What a quick answer Chanders, don't you ever sleep?

1. Absolutely, indead this works well for headlines (titles) after unload/reload of USP, but not for the others.
2. Ok, I forget it
3. Yes I set a color, I'll try to post a screeshot of the USP and the gconf tomorrow, I can't today.

I thought about the menu animation because, the default Ubuntu menu is animated with XGL/Compiz without doing anything. By default it is not, XGL/Compiz does all the job. So the question could be: what to do to make USP animated by XGL/Compiz?

---

### Post by delfick on 2006-08-24
> **Romu said:**
>  So the question could be: what to do to make USP animated by XGL/Compiz?

add "menu" as a window type for whatever affect you want...

for example, if you want it to wobble, then set "menu" as a window type for the wobbly map effect, see screenshot

---

### Post by Romu on 2006-08-24
Thanks a lot for the tip, I'll try this asap.

---

### Post by Romu on 2006-08-25
Chanders,
As promised, you'll find here 2 screenshots, one of the USP opened with a border of 10 and one of the cgonf.

I tried to set the border color to FF0000 (plain red), just to see it, but no effect.

---

### Post by chanders on 2006-08-25
Ok, from your first screenshot, I can see something happening where the border is supposed to be. Try to change you theme to something that is different (just for testing) then change the border color to red (if you like) and restart USP (right click -> remove -> add) Just for the heck of it, try it with use_custom_color checked and un-checked...

Let me know the results...

---

### Post by Romu on 2006-08-25
Ok, then thanks to wait for the next monday, I desesperatly waiting or my Internet link at home.

---

### Post by Romu on 2006-08-25
Just to add more information, I think indead the border is here but masked by the theme.

Is the empty space between the USP button and the menu itself normal ?

---

### Post by minisori on 2006-08-25
> **Romu said:**
> Just to add more information, I think indead the border is here but masked by the theme.

Is the empty space between the USP button and the menu itself normal ?

I have same thing with the empty space, changing pane_size to 1 put it a litle bit more close, but still.

---

### Post by Romu on 2006-08-25
Another problem found, but I think it is already known. If you modify a menu with "Alacarte", you have to restart USP to see the changes.

---

### Post by chanders on 2006-08-25
> **Romu said:**
> Another problem found, but I think it is already known. If you modify a menu with "Alacarte", you have to restart USP to see the changes.

Already known ;) will be fixed in the next release..

---

