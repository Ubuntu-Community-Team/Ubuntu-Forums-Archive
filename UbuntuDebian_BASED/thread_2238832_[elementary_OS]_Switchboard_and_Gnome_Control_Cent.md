---
title: "[elementary OS] Switchboard and Gnome Control Center crash upon plugin selection"
date: 2014-08-10
forum: Ubuntu/Debian BASED
---

### Post by gbauer156 on 2014-08-10
Whenever I try to use a plugin that was meant for Gnome Control Center in either Switchboard or GCC the both crashed. When I run it through a terminal to see whats going on I get this

        [COLOR=#0000ff][_LOG_LEVEL_INFO 11:41:44.479459][/COLOR] Application.vala:153: System Settings version: 2.0
        [COLOR=#0000ff][_LOG_LEVEL_INFO 11:41:44.479844][/COLOR] Application.vala:155: Kernel version: 3.16.0-6-generic
        [COLOR=#ff8c00][_LOG_LEVEL_FATAL 11:41:45.340506] [/COLOR][Gtk] gtk_grid_get_child_at: assertion 'GTK_IS_GRID (grid)' failed
        [COLOR=#ff8c00][_LOG_LEVEL_FATAL 11:41:45.340971][/COLOR] System Settings will not function properly.
        [COLOR=#ff8c00][_LOG_LEVEL_FATAL 11:41:45.341680][/COLOR] [GLib-GObject] g_object_set: assertion 'G_IS_OBJECT (object)' failed
        [COLOR=#ff8c00][_LOG_LEVEL_FATAL 11:41:45.342117][/COLOR] System Settings will not function properly.
        Segmentation fault (core dumped)

And that happens with both.

---

