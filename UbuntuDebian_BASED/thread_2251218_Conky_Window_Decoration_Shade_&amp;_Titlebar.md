---
title: "Conky Window Decoration Shade &amp; Titlebar"
date: 2014-11-02
forum: Ubuntu/Debian BASED
---

### Post by tango_ninja on 2014-11-02
I'm running 4 conky windows overtop of my desktop (screenshot).  It's elementary OS Luna (Ubuntu 12.04) with the Gala window manager.
They have no window decoration and the edges are flat... that's not what I want.   I want them to have a drop shadow (as do all my windows via the window manager).  Here are my current conky window settings:

```
own_window  yes
own_window_transparent no
own_window_type desktop
own_window_hints undecorated,sticky,skip_taskbar,skip_pages
```

I can get the drop shadow by making these changes, but then I get a nasty titlebar (which I don't want, screenshot 2):

```
own_window  yes
own_window_transparent no
own_window_type **normal**
own_window_hints sticky,skip_taskbar,skip_pages
```

How do I get the drop shadow around the window without getting the titlebar?  I would like to accomplish it without installing compiz...

[ATTACH=CONFIG]257712[/ATTACH]. . .[ATTACH=CONFIG]257713[/ATTACH]

---

### Post by vasa1 on 2014-11-02
> **tango_ninja said:**
> ...
How do I get the drop shadow around the window without getting the titlebar?  I would like to accomplish it without installing compiz...
You may want to tell people your current distro, desktop environment, and window manager, and if you've installed some dock or panel.

Are you using Elementary OS?

---

### Post by tango_ninja on 2014-11-02
Added the distro (eOS Luna) and window manager (Gala).  cheers.

---

### Post by CantankRus on 2014-11-03
In Luna the shadow seems to depend on the window decoration.

Another option to define the window without using decorations would be 
to set a semi-transparent window using argb.
Note that you set **own_window_transparent [COLOR="#FF0000"]no[/COLOR]** and use **[COLOR="#FF8C00"]argb[/COLOR]** to set the transparency.

eg
```
own_window yes
own_window_transparent [COLOR="#FF0000"]no[/COLOR]
own_window_type normal
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
[COLOR="#FF8C00"]own_window_argb_visual yes
own_window_argb_value 100 [/COLOR]  # value 0-255 with 255 being totally opaque
```

---

### Post by Elfy on 2014-11-03
*Thread moved to **Ubuntu/Debian BASED**.*

---

### Post by tango_ninja on 2014-11-03
> **CantankRus said:**
> 
Another option to define the window without using decorations would be 
to set a semi-transparent window using argb.
Note that you set **own_window_transparent [COLOR="#FF0000"]no[/COLOR]** and use **[COLOR="#FF8C00"]argb[/COLOR]** to set the transparency

Thanks, I didn't know about that value.  But this seems only to work for transparency, not the drop shadow I'm looking for...

---

### Post by tango_ninja on 2014-11-08
I'm also running into a problem autostarting conky upon login.  I have created a text file **~/.config/autostart/Conky** which contains:

```
[Desktop Entry]
Type=Application
Exec=conky
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name[en_CA]=Conky Launcher
Name=Conky
Comment[en_CA]=Conky!
Comment=Conky!
```

I believe this should run whatever follows **Exec=** but I have restarted numerous times and conky does not autostart.  I have no problem starting with:
```
conky
```

---

### Post by deadflowr on 2014-11-08
You might look at whether conky's builtin delay option will help
Conky has an option -p(pause) that you can use to delay it's launch
a simple look
```
conky -p 20
```
will delay conky from starting for 20 seconds.

I do not know if it'll help with elementary, but I know that if you run unity, conky and unity both, for some odd reason and from time to time, mangle each other at start up causing the conky window to appear overlapping the top panel or other little things. The pause option helps prevent this.

---

### Post by tango_ninja on 2014-11-08
> **deadflowr said:**
> You might look at whether conky's builtin delay option will help
Conky has an option -p(pause) that you can use to delay it's launch
a simple look
```
conky -p 20
```
will delay conky from starting for 20 seconds.

That worked like a charm, thank you.

---

