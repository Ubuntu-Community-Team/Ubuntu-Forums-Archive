---
title: "Customisable GUI framework"
date: 2014-04-24
forum: Ubuntu Application Development
---

### Post by Tony Flury on 2014-04-24
I am trying (single handedly) to develop a game for Ubuntu, and it would be great if I could theme my game so it looks distinctive. I am using python as my primary language, so I need a GUI tool kit with a good python Library. I would rather not have to use another langauge for my GUI.

Specifically I would like to be able to retain all the nice GUI features, my current GUI design is in GTK and utilises all the well known widgets : windows, packing boxes, frames, notebooks, buttons, menus, sliders, scales, radio/check buttons, labels and drawable areas (and a few others that escape me) - but I don't have the deep control over how they appear and interact with the user.

I have tried to provide some application specific themes with the GTK gui, but i don't have the level of control I desire (for instance - I can't change the shape of the slider button, or change it's colour with affecting other parts of the slider control, and similarly I can't change the shape/colour of the scroll bars). The only way (so far) I have found to generate non-rectangular buttons is to use an Image and an EventBox and implement my own ImageMap capability - and that becomes impractical (or even impossible) when the GUI goes beyond a few simple click buttons.

Given the challenages I have had so far I am guessing that GTK is not the way to go, but is there a tool kit which meets my needs and is easy to use, or is there a simple(ish) way to do deep customisation of GTK like I have mentioned : I don't want to have to write my own Theme Engine.

As a plus I would like to be change some parts of the theme on the fly (i.e. as the game is running), depending on the actions of the player within the game.

---

