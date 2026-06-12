---
title: "Stop Resize on Edge Click"
date: 2012-09-19
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by mmxbass on 2012-09-19
Currently in Ubuntu 12.10 beta, whenever I click on the bottom edge of a window, it expands that window vertically.

Suffice to say this is absolutely infuriating and needs to be taken out back and shot. PLEASE someone tell me that this can be disabled (and how to do it).

---

### Post by mmxbass on 2012-09-22
Surely someone must know a simple way to disable this? Unless it's truly impossible in which case it's off to launchpad's bug report form I suppose.

---

### Post by mmxbass on 2012-09-25
Bump... also behavior only apparently happens when the window is at the bottom edge of the screen.

---

### Post by cariboo on 2012-09-26
Moved to the U+1 Quantal sub-forum, where you may get a quicker answer to your question.

---

### Post by mc4man on 2012-09-26
What you are seeing is a default enabled option in the resize window plugin - see screen
Disable if you don't like

Basically by being at both edges you are resizing at the same time as hitting bottom edge so action (max vert) is initiated

Due to the current nature of compiz/dconf/gsettings you'll need to use ccsm to disable (compizconf-settings-manager

---

