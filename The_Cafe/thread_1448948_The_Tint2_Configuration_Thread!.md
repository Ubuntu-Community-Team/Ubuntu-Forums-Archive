---
title: "The Tint2 Configuration Thread!"
date: 2010-04-07
forum: The Cafe
---

### Post by BslBryan on 2010-04-07
Many Linux users do not bother with huge desktop environments, but choose instead to just use a window manager.  These window managers do not compile lists of programs, features, or wizards.  You, for the most part, have to research and do everything yourself.  I have been a long time fan of Openbox on top of Ubuntu minimal.  For quite some time pypanel, a popular panel, has been out of the repos, but I found a way to make it work and I was happy.  But now I think it's time that we showcase another great panel, tint2. :-)  So, post your tint2rc and a screenshot.  Woot!
```
#---------------------------------------------
# TINT2 CONFIG FILE
#---------------------------------------------

#---------------------------------------------
# BACKGROUND AND BORDER
#---------------------------------------------

rounded = 0
border_width = 1
background_color = #ffffff 0
border_color = #ffffff 40

rounded = 0
border_width = 1
background_color = #333333 50
#background_color = #719B69 50
border_color = #ffffff 40


rounded = 0
border_width = 0
#background_color = #A6B384 20
background_color = #ffffff 20
border_color = #ffffff 


#---------------------------------------------
# PANEL
#---------------------------------------------
panel_monitor = all
#panel_mode = single_monitor
panel_position = bottom center
panel_size = 95% 30
panel_margin = 0 0
panel_padding = 3 3 3 3
font_shadow = 0
panel_background_id = 3


#---------------------------------------------
# TASKS
#---------------------------------------------
task_icon = 0
task_text = 1
task_width = 100
task_centered = 1
task_margin = 4
task_padding = 5
#task_icon_size = 13
task_font = Aller 9
task_font_color = #151515 60
task_active_font_color = #ffffff 70
task_background_id = 1
task_active_background_id = 2


#---------------------------------------------
# TASKBAR
#---------------------------------------------
taskbar_mode = single_monitor
taskbar_padding = 0 0 5
taskbar_background_id = 0

#---------------------------------------------
# SYSTRAYBAR
#---------------------------------------------
#systray_padding = 0 0 0
#systray_background_id = 0
#---------------------------------------------
# CLOCK
#---------------------------------------------
time1_format = %H:%M / %a %d %b
#time1_font = Museo 8
time1_font = Aller 8
#time2_format = %A %d %B
#time2_font = Aller 6
clock_font_color = #151515 60
clock_padding = 4 0

#---------------------------------------------
# MOUSE ACTION ON TASK
#---------------------------------------------
mouse_middle = none
mouse_right = close
mouse_scroll_up = toggle
mouse_scroll_down = iconify
```

---

### Post by urukrama on 2010-04-07
You might be interested in this thread: [http://ubuntuforums.org/showthread.php?t=510528](http://ubuntuforums.org/showthread.php?t=510528)

---

### Post by Berk on 2010-04-07
```
# Tint2 config file

# Background definitions
# ID 1
rounded = 2
border_width = 0
background_color = #000000 0
border_color = #989898 100

# ID 2
rounded = 2
border_width = 0
background_color = #FFFFFF 5
border_color = #FFFFFF 100

# Panel
panel_monitor = all
panel_position = top center horizontal
panel_size = 1000 20
panel_margin = 0 0
panel_padding = 0 0
panel_dock = 0
wm_menu = 0
panel_background_id = 0

# Taskbar
taskbar_mode = single_desktop
taskbar_padding = 0 0 0
taskbar_background_id = 1
#taskbar_active_background_id = 0

# Tasks
urgent_nb_of_blink = 7
task_icon = 0
task_text = 1
task_centered = 1
task_maximum_size = 914 22
task_padding = 0 0
task_background_id = 0
task_active_background_id = 2
task_icon_asb = 0 0 0
task_active_icon_asb = 0 0 0

# Fonts
task_font = Bauhaus Md BT Bold 10
task_font_color = #993300 50
task_active_font_color = #993300 100
font_shadow = 0

# Systray
systray_padding = 0 0 0
systray_sort = ascending
systray_background_id = 0

# Clock
time1_format = %H:%M
time1_font = Bauhaus Md BT Bold 9
time2_format = %a %d
time2_font = Bauhaus Lt BT Bold 8
clock_font_color = #993300 100
clock_padding = 0 0
clock_background_id = 0
clock_lclick_command = orage
clock_rclick_command = orage


# Tooltips
tooltip = 1
tooltip_padding = 0 0
tooltip_show_timeout = 0
tooltip_hide_timeout = 0
tooltip_background_id = 0
tooltip_font = Sans 12
tooltip_font_color = #FFFFFF 100

# Mouse
mouse_middle = none
mouse_right = none
mouse_scroll_up = none
mouse_scroll_down = none

# Battery
battery = 0
battery_low_status = 20
battery_low_cmd = notify-send "battery low"
bat1_font = Sans 12
bat2_font = Sans 12
battery_font_color = #FFFFFF 100
battery_padding = 0 0
battery_background_id = 0

# End of config
```

[IMG]http://omploader.org/vNDJ2Mg[/IMG]
Minus the black lines that seem to have appeared, silly scrot.

---

### Post by BslBryan on 2010-04-07
What process do you have to run to get the volume controller into the panel?  If it was preconfigured, if you could look into your autostart.sh?

---

### Post by Berk on 2010-04-07
```
# Start volwheel after a slight delay
(sleep 3s && volwheel) &
```

Seems to be the one. I'm running the new Crunchbang statler alpha.

---

### Post by the dsc on 2010-07-20
Here's mine, albeit not quite how I want it to be yet:

[IMG]http://i25.tinypic.com/2rqyamp.png[/IMG]

I'm trying to do something kde4/oxygenesque regarding the looks.

```
# Tint2 config file
# Generated by tintwizard (http://code.google.com/p/tintwizard/)
# For information on manually configuring tint2 see http://code.google.com/p/tint2/wiki/Configure

# To use this as default tint2 config: save as $HOME/.config/tint2/tint2rc

# Background definitions
# ID 1
rounded = 0
border_width = 0
background_color = #CCCBCA 255
border_color = #FFFFFF 255

# ID 2
rounded = 4
border_width = 1
background_color = #BCBCBC 255
border_color = #FFFFFF 255

# ID 3
rounded = 5
border_width = 1
background_color = #E8E7E7 255
border_color = #FFFFFF 255

# Panel
panel_monitor = all
panel_position = bottom center horizontal
panel_size = 100% 30
panel_margin = 0 0
panel_padding = 7 0 0
panel_dock = 0
wm_menu = 0
panel_layer = top
panel_background_id = 1

# Panel Autohide
autohide = 1
autohide_show_timeout = 0.3
autohide_hide_timeout = 0.3
autohide_height = 4
strut_policy = minimum

# Taskbar
taskbar_mode = single_desktop
taskbar_padding = 2 3 2
taskbar_background_id = 3
taskbar_active_background_id = 3

# Tasks
urgent_nb_of_blink = 8
task_icon = 1
task_text = 1
task_centered = 1
task_maximum_size = 140 35
task_padding = 6 3
task_background_id = 3
task_active_background_id = 2
task_urgent_background_id = 0
task_iconified_background_id = 0

# Task Icons
task_icon_asb = 100 0 0
task_active_icon_asb = 100 0 0
task_urgent_icon_asb = 100 0 0
task_iconified_icon_asb = 100 0 0

# Fonts
task_font = DejaVu Sans Condensed 8
task_font_color = #000000 255
task_active_font_color = #000000 84
task_urgent_font_color = #FFFFFF 255
task_iconified_font_color = #FFFFFF 100
font_shadow = 0

# System Tray
systray = 1
systray_padding = 0 4 5
systray_sort = left2right
systray_background_id = 0
systray_icon_size = 0
systray_icon_asb = 100 0 0

# Clock
time1_format = %H:%M
time1_font = DejaVu Sans Condensed 8
time2_format = %A %d %B
time2_font = DejaVu Sans Condensed 6
clock_font_color = #000000 75
clock_padding = 1 0
clock_background_id = 0
clock_rclick_command = orage

# Tooltips
tooltip = 0
tooltip_padding = 2 2
tooltip_show_timeout = 0.7
tooltip_hide_timeout = 0.3
tooltip_background_id = 1
tooltip_font = DejaVu Sans Condensed 10
tooltip_font_color = #FFFFFF 80

# Mouse
mouse_middle = none
mouse_right = close
mouse_scroll_up = prev_task
mouse_scroll_down = next_task

# Battery
battery = 0
battery_low_status = 10
battery_low_cmd = notify-send "battery low"
battery_hide = 98
bat1_font = DejaVu Sans Condensed 8
bat2_font = DejaVu Sans Condensed 6
battery_font_color = #FFFFFF 75
battery_padding = 1 0
battery_background_id = 0

# End of config
```



Anyone knows if is it possible to have mouse actions to move between tasks, when it is over a task, and move between desktops, when the cursor is on the borders? I had the impression that it was possible, when I was trying other tint2rc's I've found, but I'm not sure if it did both really. I'm suspicious that it occupied less than 100% of the width and I was just rolling over the desktop, which is not how I want to do it.

Other question: is it possible to create a custom menu, like in fbpanel? I used to have a menu for mpc/mpd, somewhat mimicking a menu you'd have with most other audio players when right-clicking its menu on the system tray.

---

### Post by murderslastcrow on 2010-07-20
Lol, tint2. Those were the good old days. I really should forget about all the shiny stuff and get back to the basics. The sweet, minimal, transparent, rounded basics. Damn, tint2 is cool. XD

---

### Post by the dsc on 2010-07-20
Answering myself: "wm_menu = 1" on the panel section will make the padding react to mouse actions as if it was the plain desktop background, thus, if it's configured to change desktop by moving the will, that's what it will do. Rootmenu and whatever else as well. Great!

---

