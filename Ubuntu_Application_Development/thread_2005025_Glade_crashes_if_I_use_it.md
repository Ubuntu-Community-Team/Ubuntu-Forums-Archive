---
title: "Glade crashes if I use it"
date: 2012-06-16
forum: Ubuntu Application Development
---

### Post by clicker4721 on 2012-06-16
Using Glade 3.8.0 on 64-bit Ubuntu 12.04. I can open the program and make a new project, but crashes when I try to open projects. So I ran it from the terminal. I can open my project, but can't add boxes. The terminal readout goes like this:
```

me@mycomputer:~$ glade
GladeUI-Message: 2 missing displayable value for GtkWidget::events
GladeUI-Message: No displayable values for property GtkTreeSelection::mode
GladeUI-Message: 1 missing displayable value for GtkCellRendererAccel::accel-mode
GladeUI-Message: 14 missing displayable value for GtkCellRendererAccel::accel-mods

(glade:16233): Gtk-WARNING **: (/build/buildd/gtk+3.0-3.4.2/./gtk/gtktreemodelfilter.c:2875):gtk_tree_model_filter_rows_reordered: runtime check failed: (g_sequence_get_length (level->seq) == 0)
```

Can anybody tell me how to fix it? I'm lost.

---

