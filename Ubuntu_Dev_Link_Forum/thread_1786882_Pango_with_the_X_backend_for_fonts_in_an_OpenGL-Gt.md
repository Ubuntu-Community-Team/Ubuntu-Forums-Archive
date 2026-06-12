---
title: "Pango with the X backend for fonts in an OpenGL-Gtk+2.0-Widget under Ubuntu 11.04"
date: 2011-06-20
forum: Ubuntu Dev Link Forum
---

### Post by wehmann on 2011-06-20
Hello,

I've got problems with drawing of fonts in an OpenGL-Widget, using Gtk+2.0, GLX and Pango under Ubuntu 11.04. The same code runs without problems under Ubuntu 9.04. I use the X backend of Pango and the following GLX-function: glXUseXFont(). I tried to use the Xft backend instead of the X backend (I for example replaced pango_x_font_map_for_display() by pango_xft_get_font_map()), but it doesn't work with glXUseXFont(). Are there any packages to install, which allow to use the X backend of Pango under Ubuntu 11.04? Or are there any alternatives to glXUseXFont(), which do work with the Xft backend of Pango?

Thank you very much for help!

Best regards,

Christoph Wehmann

---

