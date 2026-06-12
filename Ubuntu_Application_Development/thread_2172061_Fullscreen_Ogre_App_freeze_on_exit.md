---
title: "Fullscreen Ogre App freeze on exit"
date: 2013-09-03
forum: Ubuntu Application Development
---

### Post by chaitanya2 on 2013-09-03
I  have an Ogre App with CEGUI,OIS running in full screen mode.It allows launching of external predetermined applications for example xbmc.However, It crashes under a peculiar condition. If i click a button in this Ogre App to open say XBMC and then after exiting XBMC i come back to the Ogre app,Now if i click on the "Exit" button it freezes!! For the same steps under non full screen mode/windowed mode it works as expected! When i say it freezes what actually happens is the screen of this Ogre app freezes and everything else works perfectly in the Background.I can say this because i can "Feel" :P the mouse moving around different windows that are open in the background.Add to it if I change to other terminal (ctrl+alt+F2) and if immediately i turn to GUI using ctrl+alt+F7 the frozen full screen of Ogre app is disappeared!!and the system runs smoothly! Note: to exit i return false from the framerenderingqueued method. System:xubuntu 12.04LTS,ATI:confused:

---

