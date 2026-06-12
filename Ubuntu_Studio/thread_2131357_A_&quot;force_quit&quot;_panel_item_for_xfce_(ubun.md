---
title: "A &quot;force quit&quot; panel item for xfce (ubuntu studio)"
date: 2013-04-01
forum: Ubuntu Studio
---

### Post by youWho on 2013-04-01
I missed the "force quit" applet that one could add to a panel in the gnome based versions of ubuntu studio, but under xfce that's gone. Here's a way to do it (this is not ubuntu studio specific; it's basically xfce specific AFAIK).
Ssave the following in a text file:

#!/bin/bash
set -o errexit             # exit immediately if part of a pipeline, subshell, etc. exits with a non-0 status
# get the process ID
PIDBEHINDWINDOW=`xprop _NET_WM_PID | sed -ne 's/[^0-9]*\([0-9]\+\)/\1/p'`
# get the name of the app from that and ask for confirmation
NAME=`cat /proc/$PIDBEHINDWINDOW/cmdline | tr "\000" " " | awk '{ print $1 }'`
zenity --question --title='Force Quit' --window-icon=error --width=300 --height=150 --text="Force $NAME to quit???" && \
kill -9 $PIDBEHINDWINDOW         # force it to quit (by its PID)

Change the permissions so it's executable. Then add a "Quicklauncher" to the panel and for its command enter the path to the script that you just saved. Choose a nice icon for it and that's it. Pretty simple.
I know there's an xkill command but that only disconnects the app from the X server and though that usually means it quits, it doesn't necessariy have to.
If you don't want it to ask you for confirmation then just comment out the lines that start with "NAME..." and "zenity..."
I'm not sure if the "errexit" option is appropriate but it seemed like a good idea; please bash experts comment (I'll learn).
Various parts of this were copied from various postings, scripts, etc. Thanks to all.

---

### Post by NNJRob on 2013-04-01
I just open Task Manager, right click on the offending item & select "kill"

---

### Post by ManamiVixen on 2013-04-01
OR... If you know the name of the frozen program, open Xterm and do"killall "program""

---

### Post by youWho on 2013-04-02
true enough :-)  (to both NNJRob and ManamiVixen).

But I've been using claws for email and tho really I do like it (else I'd switch) it's frustrating how often it gets stuck. So I got to like the immediacy of the "force quit" icon in the panel.

---

