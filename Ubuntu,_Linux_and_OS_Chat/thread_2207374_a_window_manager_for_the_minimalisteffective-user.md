---
title: "a window manager for the minimalist/effective-user"
date: 2014-02-23
forum: Ubuntu, Linux and OS Chat
---

### Post by knpoe on 2014-02-23
visit [http://awesome.naquadah.org/](http://awesome.naquadah.org/)   take a quick look around, familiarize yourself with the hotkeys, they won't take long to get used to.... very vi like.

then install it... if you're running a recent ubuntu revision then simply:
 ```
apt-get install awesome*
```

you may want to customize a few things... i personally think gnome-terminal is too bulky... i've been pointed to urxvt '*rxvt-unicode*' -- and it's about all that i ever expect or want from a terminal *(customize your ~/.Xdefaults file to color it.. *deviant art has several nice presets to get you started there)

the default awesome look is a bit bland... it doesn't take long to recolor it... just edit the config-file @```
sudo gedit /usr/share/awesome/themes/default/theme.lua 
```
here's the way i've customized mine to give you something to start with that's not going to put you to sleep while you learn the hotKeys... and which programs you're going to want to ```
awful.util.spawn_with_shell("wmname LG3D") 
```. for example... to fix java things *(i like minecraft) that don't have a clue what WindowManager they're running *( from '*suckless-tools*').. *(they're all defined and customizeable in ```
/etc/xdg/awesome/rc.lua
``` )
*(you'll notice alot of calls to **.png files** ... well, those are the icons all around the screen- you can customize all of them as you please... 'sudo gimp' if you're super lazy, like me... just keep backups of all the files you leave in the default locations ... as apt-get upgrade {awesome*} will sometimes replace the config files... and images if they're updated... . . this caused me a lot of head ache early on... )

```

---------------------------
-- Default awesome theme --
---------------------------


theme = {}


theme.font          = "sans 8"


theme.bg_normal     = "#FFFF00"
theme.bg_focus      = "#14F200"
theme.bg_urgent     = "#ff0000"
theme.bg_minimize   = "#444444"


theme.fg_normal     = "#1A4501"
theme.fg_focus      = "#000000"
theme.fg_urgent     = "#000000"
theme.fg_minimize   = "#121212"


theme.border_width  = "2"
theme.border_normal = "#FFFB00"
theme.border_focus  = "#33FF00"
theme.border_marked = "#91231c"


-- There are other variable sets
-- overriding the default one when
-- defined, the sets are:
-- [taglist|tasklist]_[bg|fg]_[focus|urgent]
-- titlebar_[bg|fg]_[normal|focus]
-- tooltip_[font|opacity|fg_color|bg_color|border_width|border_color]
-- mouse_finder_[color|timeout|animate_timeout|radius|factor]
-- Example:
--theme.taglist_bg_focus = "#ff0000"


-- Display the taglist squares
theme.taglist_squares_sel   = "/usr/share/awesome/themes/default/taglist/squarefw.png"
theme.taglist_squares_unsel = "/usr/share/awesome/themes/default/taglist/squarew.png"


theme.tasklist_floating_icon = "/usr/share/awesome/themes/default/tasklist/floatingw.png"


-- Variables set for theming the menu:
-- menu_[bg|fg]_[normal|focus]
-- menu_[border_color|border_width]
theme.menu_submenu_icon = "/usr/share/awesome/themes/default/submenu.png"
theme.menu_height = "15"
theme.menu_width  = "100"


-- You can add as many variables as
-- you wish and access them by using
-- beautiful.variable in your rc.lua
--theme.bg_widget = "#cc0000"


-- Define the image to load
theme.titlebar_close_button_normal = "/usr/share/awesome/themes/default/titlebar/close_normal.png"
theme.titlebar_close_button_focus  = "/usr/share/awesome/themes/default/titlebar/close_focus.png"


theme.titlebar_ontop_button_normal_inactive = "/usr/share/awesome/themes/default/titlebar/ontop_normal_inactive.png"
theme.titlebar_ontop_button_focus_inactive  = "/usr/share/awesome/themes/default/titlebar/ontop_focus_inactive.png"
theme.titlebar_ontop_button_normal_active = "/usr/share/awesome/themes/default/titlebar/ontop_normal_active.png"
theme.titlebar_ontop_button_focus_active  = "/usr/share/awesome/themes/default/titlebar/ontop_focus_active.png"


theme.titlebar_sticky_button_normal_inactive = "/usr/share/awesome/themes/default/titlebar/sticky_normal_inactive.png"
theme.titlebar_sticky_button_focus_inactive  = "/usr/share/awesome/themes/default/titlebar/sticky_focus_inactive.png"
theme.titlebar_sticky_button_normal_active = "/usr/share/awesome/themes/default/titlebar/sticky_normal_active.png"
theme.titlebar_sticky_button_focus_active  = "/usr/share/awesome/themes/default/titlebar/sticky_focus_active.png"


theme.titlebar_floating_button_normal_inactive = "/usr/share/awesome/themes/default/titlebar/floating_normal_inactive.png"
theme.titlebar_floating_button_focus_inactive  = "/usr/share/awesome/themes/default/titlebar/floating_focus_inactive.png"
theme.titlebar_floating_button_normal_active = "/usr/share/awesome/themes/default/titlebar/floating_normal_active.png"
theme.titlebar_floating_button_focus_active  = "/usr/share/awesome/themes/default/titlebar/floating_focus_active.png"


theme.titlebar_maximized_button_normal_inactive = "/usr/share/awesome/themes/default/titlebar/maximized_normal_inactive.png"
theme.titlebar_maximized_button_focus_inactive  = "/usr/share/awesome/themes/default/titlebar/maximized_focus_inactive.png"
theme.titlebar_maximized_button_normal_active = "/usr/share/awesome/themes/default/titlebar/maximized_normal_active.png"
theme.titlebar_maximized_button_focus_active  = "/usr/share/awesome/themes/default/titlebar/maximized_focus_active.png"


-- You can use your own command to set your wallpaper
theme.wallpaper_cmd = { "awsetbg /usr/share/awesome/themes/default/background.png" }


-- You can use your own layout icons like this:
theme.layout_fairh = "/usr/share/awesome/themes/default/layouts/fairhw.png"
theme.layout_fairv = "/usr/share/awesome/themes/default/layouts/fairvw.png"
theme.layout_floating  = "/usr/share/awesome/themes/default/layouts/floatingw.png"
theme.layout_magnifier = "/usr/share/awesome/themes/default/layouts/magnifierw.png"
theme.layout_max = "/usr/share/awesome/themes/default/layouts/maxw.png"
theme.layout_fullscreen = "/usr/share/awesome/themes/default/layouts/fullscreenw.png"
theme.layout_tilebottom = "/usr/share/awesome/themes/default/layouts/tilebottomw.png"
theme.layout_tileleft   = "/usr/share/awesome/themes/default/layouts/tileleftw.png"
theme.layout_tile = "/usr/share/awesome/themes/default/layouts/tilew.png"
theme.layout_tiletop = "/usr/share/awesome/themes/default/layouts/tiletopw.png"
theme.layout_spiral  = "/usr/share/awesome/themes/default/layouts/spiralw.png"
theme.layout_dwindle = "/usr/share/awesome/themes/default/layouts/dwindlew.png"


theme.awesome_icon = "/usr/share/awesome/icons/awesome16.png"


return theme
-- vim: filetype=lua:expandtab:shiftwidth=4:tabstop=8:softtabstop=4:textwidth=80

```


**xbattbar** is nice as well... just make sure to run with the **-a** (above-all) and **-c** (acpi) flags, you can change its charging

---

### Post by lykwydchykyn on 2014-02-24
I've been using awesome on all my personal systems for ~2.5 years now.  It's definitely fun for those who (like me) like to tinker around.  Probably not for everyone.  Your poll choices are very confusing.

Here's some fun tips I blogged on:

[http://www.alandmoore.com/blog/tag/awesome-wm/](http://www.alandmoore.com/blog/tag/awesome-wm/)

---

