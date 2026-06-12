---
title: "[TUTORIAL]Wacom Bamboo - Disable TOUCH"
date: 2012-06-29
forum: Tutorials
---

### Post by snowz on 2012-06-29
[IMG]http://ubuntuone.com/42dPxO9KGXTFVwiWWwN2dY[/IMG]

Basically this is a short tutorial on **HOW TO DISABLE THE TOUCH FUNCTION ON THE TABLET WACOM BAMBOO PEN & TOUCH**

> 
Reasons for doing this: Sometimes when you want to draw with the tablet the TOUCH function does some pretty weird things. It clicks and changes stuff, that you don't want it to, while you're drawing.


To DISABLE the TOUCH function:


[LIST]
[*]Open the Terminal
[*]Type: xsetwacom --list
[*]You will get a list of IDs which are assigned to your tablet
[*]The second option should be the touch one
[*]Type: **xsetwacom set [COLOR=DarkOrange]YOUR_ID_NEXT_TO_TOUCH[/COLOR] touch off**
[/LIST]
> [B]I know there is already my topic about the tablet and a reply including pretty much this guide in the Art forum but I've decided that this should be a pretty much useful tutorial for Bamboo tablet users, so I've posted this here also.
[/B]


---

### Post by daslinkard on 2012-09-22
Very interesting post here.  I'm thinking about getting a Bamboo pad and hadn't thought about the drawing issue.

---

