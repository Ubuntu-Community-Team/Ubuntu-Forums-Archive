---
title: "USP2 SVN menu panel shadow"
date: 2007-04-08
forum: Ubuntu System Panel
---

### Post by cmost on 2007-04-08
Please forgive me if this has already been asked (I did a search but didn't turn up anything.)  I want to make just the USP menu itself display with a shadow (like the rest of my windows.)  I'm using Beryl for compositing.  If I enable shadows on panel type windows (in Beryl settings manager) I get an ugly shadow underneath the entire panel (but also under USP menu.)  I'd like to keep the shadow under the menu, but not on the entire panel.  Yuck.  I know there's a way to enable the shadow by using the 'window specific settings' applet in the Beryl settings manager.  I'm not sure, however, how to add the entry for USP.  Can anyone assist?  Much appreciated.

---

### Post by cmost on 2007-04-10
*BUMP*

Anyone??? anyone????

---

### Post by zekopeko on 2007-04-10
there is an application which you run in terminal and then click on a window. after that it gives you the relevant info about that window including the name. 

i just can't remember what is the name of that command/app.

EDIT:

try:   xwininfo in terminal

---

### Post by groggyboy on 2007-06-12
i  would also like to put a dropshadow under the USP menu.  running xwininfo gave me this: ```
xwininfo: Window id: 0x2e00035 "System Panel"
```

but i can't find the window specific settings function in beryl.  Under window management, there is a plugin called "Set Window Attribs by various criteria", but it doesn't have a dropshadow option.  I'm using USP2 svn and the standard beryl 0.2.1 that comes with ubuntu.

can anyone point me in the right direction to get this effect?

---

