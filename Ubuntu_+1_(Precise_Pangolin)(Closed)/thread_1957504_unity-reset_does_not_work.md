---
title: "unity-reset does not work"
date: 2012-04-12
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by freakwit on 2012-04-12
It previously worked when I upgraded to 12.04 after running DISPLAY=:0 unity --reset and installing the proprietary AMD driver. Since then, I've kept my packages up to date, and it has not worked for about a week. I'm currently using unity2d to post this.

Here's what I'm seeing:

Upon login, only the background wallpaper and cursor is displayed.

If I press the power button, the shutdown prompt appears, but is missing the usual decorators.

From a virtual terminal (ctrl+alt+F1) DISPLAY=:0 unity --reset prints some normal output, and ends with a WARN for unity-glib.gobject about a NULL pointer and exits saying Trace/Breakpoint trap core dumped.

Is there something else I should be running besides unity --reset to try and get my system to a normal state so that unity loads properly?

---

### Post by jfernyhough on 2012-04-12
What happens if you run unity --reset from within Unity2D? I know it shouldn't make any difference, but...

I would have suggested adding the Unity testing PPA but 5.10 has just been pushed to the main repo so there's no point adding that PPA now.

---

### Post by freakwit on 2012-04-13
I did another update today, and have v5.10 now... I get some different console output, but still the same behaviour, hmm...

Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no

Screen geometry changed:
   0x0x1366x768

ERROR 2012-04-14 09:02:20 unity.launcher.trashlaunchericon TrashLauncherIcon.cpp:62 Could not create file monitor for trash uri: Operation not supported
ERROR 2012-04-14 09:02:20 unity.glib <unknown>:0 g_source_remove: assertion `tag > 0' failed
ERROR 2012-04-14 09:02:20 unity.glib <unknown>:0 g_source_remove: assertion `tag > 0' failed
ERROR 2012-04-14 09:02:20 unity.glib <unknown>:0 g_source_remove: assertion `tag > 0' failed
ERROR 2012-04-14 09:02:20 unity.glib-gobject <unknown>:0 g_object_unref: assertion `G_IS_OBJECT (object)' failed
ERROR 2012-04-14 09:02:20 unity.glib <unknown>:0 g_source_remove: assertion `tag > 0' failed
CRIT  2012-04-14 09:02:21 unity.glibmm <unknown>:0 
unhandled exception (type std::exception) in signal handler:
what: basic_string::_S_create

WARNING: Unity currently default profile, so switching to metacity while resetting the values

---

### Post by freakwit on 2012-04-19
since updating again it works!

---

