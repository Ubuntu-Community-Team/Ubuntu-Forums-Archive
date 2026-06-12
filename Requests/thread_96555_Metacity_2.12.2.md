---
title: "Metacity 2.12.2"
date: 2005-11-29
forum: Requests
---

### Post by elleuca on 2005-11-29
There are some interesting fix

 - Mave ancestors come along with the transient when moving the window from
   one workspace to another (Björn) [#314977]
 - Fix the workspace switcher tabpopup to display the right windows and to
   fix the pick-a-new-window-to-focus algorithm in order to not select
   windows that aren't showing (Björn) [#170475]
 - Fix a couple memory leaks (Kjartan, Søren, Elijah) [#313030]
 - Fix a crash that occurs when removing some virtual desktops and windows
   happen to be on those desktops (Elijah) [#318306]
 - Fix edge snapping for multi-screen (non-xinerama) setups (Elijah)
   [#319425]
 - Close a GSource leak just to be correct (Kjartan) [#320050]

---

