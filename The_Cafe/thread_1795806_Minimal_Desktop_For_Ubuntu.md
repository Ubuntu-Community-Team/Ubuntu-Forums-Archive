---
title: "Minimal Desktop For Ubuntu"
date: 2011-07-03
forum: The Cafe
---

### Post by coolglobal on 2011-07-03
I'm building a new system and used The Minimal Desktop for Ubuntu script by aveilleux. It does it's job really well. The instructions and script worked flawlessly on my Lucid build, and on reboot the system was on amphetamines. I did a Gnome install, as that is the base of my current build. There is a choice of DE in the script, Gnome, KDE, Fluxbox, Blackbox and Openbox. It was different for me to do a minimal install using Gnome as a usual choice would be one of the boxes. I was quite impressed with how responsive Gnome 2 can be as a minimal install.

It looks like the script is on hold until the many dependencies of the newest release of Ubuntu are sorted. It's good to go for Lucid and Maverick which is great for me!

I did try the Script Generator, to customize my script, thereby sidestepping the question and answer. This script failed in the final lines. It seems there may be a bug in the generator. This doesn't affect the main script described on the website.

Anyway, it was a great solution to creating a minimal Ubuntu as a base to build upon.

The website: [http://minimal-desktop.blogspot.com/](http://minimal-desktop.blogspot.com/)

I wonder if it will fork?

*I'll post a link to the website of my new build when I've finished. It's a step by step Ubuntu build project.*

---

### Post by Sef on 2011-07-03
[s]Locked. Not a Testimonial nor Experience.[/s]

Update: Moved to Community Cafe and re-opened.

---

### Post by coolglobal on 2011-07-04
Thanks Sef, I appreciate the move, much better location.

---

### Post by Aquix on 2011-07-04
Why the fork?
I'm for mint, crunchbang or debian myself.

---

### Post by coolglobal on 2011-07-04
#! is great.

With the fork, I'm referring to the minimal script by aveilleux. It seems that it has been discontinued on the blog here:  [http://minimal-desktop.blogspot.com/](http://minimal-desktop.blogspot.com/)

I guess I'm wondering if anyone is going to pick up the torch and run with it.
The script works great as a way to start building an Ubuntu system from scratch.

My thoughts on the matter to keep it alive.
- Update the script for LTS releases only.
- Drop the online generator.

If there is a genuine interest in forking/continuing, I'd be willing to build and maintain the website for the script. (Might regret I said that! :))

---

### Post by Chesamo on 2011-07-04
This is aveilleux (I never got my name changed). This project has my full support. I'll link your project in a new post once you get rolling.

MDU as released by me and my team is effectively dead. Feel free to fork the project on Github and etc. and create a new project on LaunchPad. (Call it Ubuntu from Scratch, perhaps?)

I look forward to seeing what you create. Happy coding!

---

### Post by Paqman on 2011-07-05
> **coolglobal said:**
> I was quite impressed with how responsive Gnome 2 can be as a minimal install.


Me too, it's actually pretty good.

I like the minimal ISO too, and maintain a similar script (check my sig). I'll check out the script when I get the chance, always stuff to learn from someone else's work!

---

### Post by coolglobal on 2011-07-05
Thanks for the positive responses, I truly hope the script can move forward.

I've whipped up a website to house the script, (a work in progress!), I made a blog post also.

Website: [http://ubuntu-mdis.weebly.com/index.html](http://ubuntu-mdis.weebly.com/index.html)

---

### Post by Lucradia on 2011-07-05
You don't really need a complete new script to make a minimal desktop. All you need is the mini.iso: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

a network connection (even if it is wireless, your wireless device may be supported by generic drivers in the mini.iso kernel.)

and install these: xorg openbox openbox-themes obmenu menu sakura

A note, I never like to include a panel on an absolute minimal desktop, as the panel is one of the BIGGEST contributors to CPU usage, next to firefox, whatever browser you use. As for browser, I REALLY do not suggest chrome, opera, or any of the big boys (yes, this includes firefox.) You may not agree on midori, but it DOES use less resources, at least on idle (just not with plugins like java or flash.)

Get conky, and use this conkyrc:

```
    # Conky, a system monitor, based on torsmo
    #
    # Any original torsmo code is licensed under the BSD license
    #
    # All code written since the fork of torsmo is licensed under the GPL
    #
    # Please see COPYING for details
    #
    # Copyright (c) 2004, Hannu Saransaari and Lauri Hakkarainen
    # Copyright (c) 2005-2009 Brenden Matthews, Philip Kovacs, et. al. (see AUTHORS)
    # All rights reserved.
    #
    # This program is free software: you can redistribute it and/or modify
    # it under the terms of the GNU General Public License as published by
    # the Free Software Foundation, either version 3 of the License, or
    # (at your option) any later version.
    #
    # This program is distributed in the hope that it will be useful,
    # but WITHOUT ANY WARRANTY; without even the implied warranty of
    # MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    # GNU General Public License for more details.
    # You should have received a copy of the GNU General Public License
    # along with this program.  If not, see <http://www.gnu.org/licenses/>.
    #

    # Create own window instead of using desktop (required in nautilus)
    own_window yes
    own_window_hints sticky,undecorated,below,skip_taskbar,skip_pager
    background no
    # Use double buffering (reduces flicker, may not work for everyone)
    double_buffer yes
    # fiddle with window
    use_spacer yes
    use_xft yes
    # Update interval in seconds
    update_interval 0.5
    # Minimum size of text area
    #minimum_size 5 5
    # Draw shades?
    draw_shades yes
    # Text stuff
    draw_outline no # amplifies text if yes
    draw_borders no
    uppercase no # set to yes if you want all text to be in uppercase
    # Stippled borders?
    stippled_borders 8

    # border margins
    border_margin 4
    # border width
    border_width 1
    # Default colors and also border colors, grey90 == #e5e5e5
    default_color white
    default_shade_color black
    default_outline_color white
    own_window_colour brown
    own_window_transparent yes
    # Text alignment, other possible values are commented
    #alignment top_left
    #alignment top_right
    alignment bottom_left
    #alignment bottom_right
    # Gap between borders of screen and text
    gap_x 10
    gap_y 10
    # stuff after 'TEXT' will be formatted on screen
    override_utf8_locale no
    xftfont Terminus:size=8
    xftalpha 0.8

    TEXT
    ${offset 0}${color lightgrey}Kern:${color }$kernel ][ ${offset 0}${color lightgrey}${time %a, } ${color }${time %e %B %G} ][ ${offset 0}${color lightgrey}${time %Z,    }${color }${time %H:%M:%S} ][ ${offset 0}${color lightgrey}CPU:${color } $cpu% ${acpitemp}C ${offset 0}${cpubar 3,100} ][ ${offset 0}${color lightgrey}MEM:  ${color } $memperc% $mem/$memmax ${offset 0}${membar 3,100} ][ ${offset 0}${color lightgrey}SWAP: ${color }$swapperc% $swap/$swapmax ${offset 0}${swapbar 3,100} ][ ${offset 0}${color lightgrey}NET: ${offset 0}${color}Up: ${color }${upspeed eth0} ${offset 0}${color}Down: ${color }${downspeed eth0}${color}
```

edit to suit your needs, but this makes conky appear horizontally at the bottom, where the panel normally would be.

Use stalonetray if you REALLY need a notification tray for programs like pidgin, with it up in the upper right (grow W)

Never use a display manager if you want a minimal desktop, they are another big CPU eater.

---

### Post by zer010 on 2011-07-05
Nice suggestions. I've been thinking of doing a minimalistic setup similar to this.

---

