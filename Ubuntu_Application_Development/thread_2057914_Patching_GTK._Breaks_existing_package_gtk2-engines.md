---
title: "Patching GTK. Breaks existing package gtk2-engines-pixbuf"
date: 2012-09-14
forum: Ubuntu Application Development
---

### Post by jonim8or on 2012-09-14
I'm trying to create a patched build of gtk, which fixes an [ annoying bug with wacom&xinerama.](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/479810)

I've created a .deb file (unsigned), and want to install that. But then this is what I get:
 Breaks existing package gtk2-engines-pixbuf

Here are the steps I followed:
Installed scripts and compiler that are needed
```

sudo apt-get install build-essential devscripts

```

installed dependencies for gtk package
```

sudo apt-get build-dep gtk+2.0

```

made a directory for sources, and downloaded the source of the gtk package
```

cd ~/src
sudo apt-get source gtk+2.0

```

applied a change in the lines of [the patch](https://launchpadlibrarian.net/35459288/gtk-wacom-xinerama.patch). for me it was replacing the lines 
```

      x_scale = gdk_screen_get_width (gdk_drawable_get_screen (window)) / device_width;
      y_scale = gdk_screen_get_height (gdk_drawable_get_screen (window)) / device_height;

      x_offset = - impl_window->input_window->root_x - priv->abs_x;
      y_offset = - impl_window->input_window->root_y - priv->abs_y;

```
by these lines:
```

int core_pointer_x, core_pointer_y, cur_monitor;
      GdkRectangle mon_geometry;
      GdkScreen *cur_screen;
      gdk_display_get_pointer(gdk_drawable_get_display(window),
			      &cur_screen,&core_pointer_x,&core_pointer_y,0);
      cur_monitor= gdk_screen_get_monitor_at_point(cur_screen,
						   core_pointer_x,
						   core_pointer_y);
      gdk_screen_get_monitor_geometry(cur_screen,cur_monitor,&mon_geometry);
      x_scale = mon_geometry.width / device_width;
      y_scale = mon_geometry.height / device_height;
      x_offset = mon_geometry.x - impl_window->input_window->root_x;
      y_offset = mon_geometry.y - impl_window->input_window->root_y;

```

Committed the changes to the package and added a message describing the change to the changelog of the package
```

sudo dpkg-source --commit
sudo debuild -i -us -uc -b

```

Finally double-clicked the libgtk2.0-0_2.24.10-0ubuntu7_amd64.deb file to install it. THat gave the error message (see image)

---

