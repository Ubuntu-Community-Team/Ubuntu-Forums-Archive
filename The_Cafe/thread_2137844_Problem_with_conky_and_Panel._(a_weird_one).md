---
title: "Problem with conky and Panel. (a weird one)"
date: 2013-04-22
forum: The Cafe
---

### Post by baillou2 on 2013-04-22
So I run conky on the brand new Ubuntu 13.04. Everything seems to work great except for one small thing. When I close the last window on a workspace - so that there are no open applications - I notice that the Panel stil shows the name of the application I just closed in the upper left corner. This has the effect of not allowing any of the keyboard navigation buttons to work until I click somewhere on the empty desktop, at which point everything works normally.

So what I've figured out is that conky somehow causes this. If I'm not running it none of these problems occur. I can close a terminal and slide over to another workspace, or turn up the volume etc. But if I'm running conky I have to first click on the desktop to get navigation buttons working.

So why is the panel keeping the name of a window I closed when conky is running?

Has anyone had a problem like this before??

Thanks for any help.

---

### Post by ajgreeny on 2013-04-22
Let's see your conky configuration file, .conkyrc by default, unless you have changed it to something else.  That may give a clue to what's going on.

---

### Post by baillou2 on 2013-04-22
> **ajgreeny said:**
> Let's see your conky configuration file, .conkyrc by default, unless you have changed it to something else.  That may give a clue to what's going on.


I actually run a bunch of individual scripts ( I have an elaborate set-up ). Anyway here is what the conf looks like for all of them except for the alignments and such which changes the locations on the screen.


# UBUNTU-CONKY
# Create own window instead of using desktop (required in nautilus)
own_window yes # create a separate XWindow over the one from Xfdesktop
own_window_type normal # the window cannot be moved or resized
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager # make it behave like it belongs to the desktop
own_window_argb_visual yes
own_window_argb_value 255
 
# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes
 
# fiddle with window
use_spacer none


# Use Xft?
use_xft yes
xftfont DejaVu Sans:size=8
xftalpha 0.8
text_buffer_size 2048
 
# Update interval in seconds
update_interval 3.0
 
# Draw shades?
draw_shades no

---

### Post by ajgreeny on 2013-04-22
Apart from the layout and formatting your config looks very like mine, so that was not much help, I'm afraid.

Keep searching, I think.  Sorry I can't help!

---

### Post by baillou2 on 2013-04-22
> **ajgreeny said:**
> Apart from the layout and formatting your config looks very like mine, so that was not much help, I'm afraid.

Keep searching, I think.  Sorry I can't help!


Thanks for looking anyway.

Are you running Ubuntu 12.10 or 13.04?

If so I wonder if you can reproduce the problem. You might have never noticed it since it's not that big of a deal.

---

### Post by ajgreeny on 2013-04-22
No, I can't replicate your problem at all.  When my last window is closed the desktop becomes fully focused, which I think is what you're suggesting does not happen for you.

Have a look in the settings-manager and check the focus setting in **Window-manager** and **Window-manager-tweaks**.  Apart from that I have no other ideas.

I am using Xubuntu 12.04 64bit system, by the way, so things may be very different for me.

---

### Post by baillou2 on 2013-04-22
Yeah, this seems to be a Unity specific problem.

---

