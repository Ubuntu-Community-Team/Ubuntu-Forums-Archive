---
title: "Apps bleed into adjacent workspaces when switching..."
date: 2012-03-13
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by neu5eeCh on 2012-03-13
I just opened a new or as yet unrecorded (I think) bug here:

[https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/954565](https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/954565)


> Unity 12.04 Beta 2
 

1.) When switching workspaces I notice that both Gimp and Libreoffice (unmaximized) bleed (move) into adjacent workspaces.
 

2.) I notice that when I move the GIMP toolbar back to the correct  workspace, if the toolbar originally moved incompeletely "upward" into  the workspace above, "a ghost" of the toolbar will remain beneath the  transparent Unity panel (even after the panel has been moved).


If you any of you can reproduce this bug, be sure and add yourselves to the bug report.

Also, I notice that Gimps toolbars exceed the size of the desktop. Surely this bug has been reported by now?

---

### Post by jbicha on 2012-03-13
I have no idea what your bug is. LibreOffice & Gimp seem to work ok here. Could you include a screenshot? What is your screen resolution?

---

### Post by mc4man on 2012-03-13
The part about having a  ghost" of" has happened here off & on for while, not lately though & could be almost any window
(forget if I filed a bug on, will have to look

When it was happening sometimes I used a synaptic window to 'clean' out the 'ghost', kinda hard to explain. (something like moving synaptic over a ghost area, switching workspaces, re-adjusting synaptic, moving Ws's ect.

atm I don't have grid or png plugins enabled, whether a factor in not getting anymore who knows ...

---

### Post by neu5eeCh on 2012-03-13
> **jbicha said:**
> I have no idea what your bug is. LibreOffice & Gimp seem to work ok here. Could you include a screenshot? What is your screen resolution?

1280 x 768

When GIMP first opens:

[IMG]http://poemshape.files.wordpress.com/2012/03/screenshot-from-2012-03-13-202540-thumb.jpg[/IMG]

The "ghost" left under the transparent panel (top leftish):

[IMG]http://poemshape.files.wordpress.com/2012/03/screenshot-from-2012-03-13-202632-thumb.jpg[/IMG]

Workspace view (notice the ghost in the middle of the top panel (transparent):

[IMG]http://poemshape.files.wordpress.com/2012/03/screenshot-from-2012-03-13-202713-thumb.jpg[/IMG]

And another bug I just discovered (notice how the window border disappeared from the left toolbar after moving it to the correct workspace:

[IMG]http://poemshape.files.wordpress.com/2012/03/missing-window-border.jpg[/IMG]

With libreoffice, it's not consistent, but if libre isn't maximized and I switch workspaces, it will sometimes cross/move halfway into an adjacent workspace.

---

### Post by mc4man on 2012-03-13
I see I  added it (improperly) to a bug on black text with a fully transparent panel
There is a video showing, (#5), though for me an upgrade to compiz fixed the overall issue, since then no longer use 2X2 nor wall either
(The video is much larger than it should have been, I can only view right by downloading if curious
[https://bugs.launchpad.net/unity/+bug/924592](https://bugs.launchpad.net/unity/+bug/924592)

Sounds like you should open a new bug on this

---

### Post by neu5eeCh on 2012-03-13
I opened a bug report (see the first post) and added the following image:

(I can now reproduce this at will. Open Libre or GIMP in **Workspace 1**, let's say, then go to workspace view. Move Libre or GIMP to another workspace. Return to **Workspace 1**, then click on the Libre or GIMP icon in the launcher. In my case, rather than taking me to the other Workspace, the right side of GIMP or Libre will be yanked into **Workspace 1**.

[IMG]https://launchpadlibrarian.net/96713139/Libre%20Creep.jpg[/IMG]

---

### Post by jbicha on 2012-03-13
By the way, the menu bar isn't transparent by default. A good bug report includes steps to reproduce from a default install (you can use a guest account for this if you like).

Anyway, it looks like this is a Unity bug, not a Gimp bug.

---

### Post by PaulW2U on 2012-03-14
> **jbicha said:**
> Anyway, it looks like this is a Unity bug, not a Gimp bug.

It most definitely **is** a Unity bug. 

I see this quite often but hadn't got around to submitting a useful bug report. I can't reproduce it at will but over time I find applications such as Firefox, Thunderbird and LibreOffice will move to a different workspace after a fair amount of switching between workspaces. Sometimes all I see is the extreme edge of my application in the wrong window and I can no longer switch to it. Applications I have open in small windows such as gnome-terminal will just move within a workspace.

[https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/954565](https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/954565) has been changed to reflect it is a Unity bug.

---

### Post by wgarcia on 2012-03-14
I'm seeing this in a machine with a NVIDIA graphics card. Do the users affected here have also NVIDIA cards?

---

### Post by neu5eeCh on 2012-03-14
> **wgarcia said:**
> I'm seeing this in a machine with a NVIDIA graphics card. Do the users affected here have also NVIDIA cards?

No, the laptop from which the images were drawn (above) uses an integrated Intel graphics board. I don't believe this is related to NVIDIA (for a change).

---

### Post by PaulW2U on 2012-03-14
> **VTPoet said:**
> I don't believe this is related to NVIDIA

Now showing as a compiz bug - [https://bugs.launchpad.net/compiz-core/+bug/954565](https://bugs.launchpad.net/compiz-core/+bug/954565).

I think its simply compiz calculating where application windows should be placed and under certain circumstances getting it wrong.

---

### Post by neu5eeCh on 2012-03-14
> **PaulW2U said:**
> Now showing as a compiz bug - [https://bugs.launchpad.net/compiz-core/+bug/954565](https://bugs.launchpad.net/compiz-core/+bug/954565).

I think its simply compiz calculating where application windows should be placed and under certain circumstances getting it wrong.

I noticed that. I'm glad to see more users registering the bug. Seems like it ought to be something ironed out (fairly significant) before LTS is released.

---

### Post by PaulW2U on 2012-03-14
> **VTPoet said:**
> I'm glad to see more users registering the bug. Seems like it ought to be something ironed out (fairly significant) before LTS is released.

Only six of us so far though. :rolleyes:

It's taken over four hours for this bug to show itself tonight. And even then two out of three small-windowed applications on workspace 4 moved down about 25% of the screen height. Nothing has moved either fully or partially to another workspace.

I wonder how many are affected by this bug and don't realise it?

---

### Post by neu5eeCh on 2012-03-14
As long as one keeps all the apps maximized, they'll stay put. This is the workaround, such as it is. The GIMP is especially vulnerable since one can't maximize all three windows.

---

### Post by ArgAthens on 2012-03-20
I also saw as soon as I upgraded to the beta 12.4.  I do a lot of workspace switching and consequently after a short period of time my windows are stacked in the first workspace.  I have unity disabled, and am using the gnome-shell with 10 workspaces.

---

### Post by ArgAthens on 2012-03-22
I did a partial upgrade this morning, followed by a full system update and now it's working great again.

---

