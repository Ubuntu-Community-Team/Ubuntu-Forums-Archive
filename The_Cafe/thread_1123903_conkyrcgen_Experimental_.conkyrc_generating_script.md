---
title: "conkyrcgen: Experimental .conkyrc generating script"
date: 2009-04-12
forum: The Cafe
---

### Post by PacSci on 2009-04-12
I wrote this experimental script, called conkyrcgen, to automatically build a .conkyrc from Jinja2 macros. So far, it's incredibly alpha, but I thought that the Ubuntu Forums would be a good place to share this, considering that there are a lot of nice people, I'd get feedback quickly, and there's a really long thread for people's .conkyrcs.

I've attached a .tar.gz with the Python script, a collection of default macros, my example .conkyrcrc, and a README. Please read the README, as it tells you everything you need to do to set it up.

What I'm looking for here is feedback, suggestions on how to fix the five to ten macros I'm shipping that have not been tested or have serious problems, maybe some more macros and styles to include, etc. If you have feedback or a contribution, by all means, post it.

Just to show you what it can do, it transformed this .conkyrcrc (that's the name of the file it uses as input):

```
{% import 'orangestyle' as style -%}
{% from 'sysbase' import sysname, cpu, ram, filesystems %}
{% from 'sysmisc' import who, kernellog %}
{% from 'music' import xmms2 -%}
{% from 'fun' import fortune, rss -%}
{% from 'network' import ifaceinfo, netuse -%}

{{ style.styleinfo() }}
{{ position() }}

TEXT
{{ sysname(style) }}
{{ cpu(style, 4) }}
{{ ram(style) }}
{{ filesystems(style, '/', '/stor') }}
{{ ifaceinfo(style, "eth0") }}
{{ kernellog(style) }}
{{ who(style) }}
{{ netuse(style, 3) }}
{{ xmms2(style) }}
{{ rss(style, "http://rss.slashdot.org/Slashdot/slashdot") }}
{{ fortune(style) }}

Updated $updates times
```

Into this .conkyrc:

```


# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
 
# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes
 
# fiddle with window
use_spacer right

# Use Xft?
use_xft yes
xftfont Kochi Gothic:size=8
xftalpha 0.8
text_buffer_size 2048

# Maximum width of window
minimum_size 250,5
maximum_width 250
 
# Draw shades?
draw_shades no
 
# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase
 
# Stippled borders?
stippled_borders 3
 
# border margins
border_margin 9
 
# border width
border_width 10
 
# Default colors and also border colors, grey90 == #e5e5e5
default_color grey
color1 orange
 
own_window_colour brown
own_window_transparent yes
alignment top_right

    # Gap between borders of screen and text
    gap_x 10
    gap_y 40

TEXT
${color1}SYSTEM  ${hr 2}$color
$nodename $sysname $kernel on $machine

${color1}CPU ($freq MHz) ${hr 2}$color
Load: ${loadavg}   Temp: ${acpitemp}
${cpubar 8}
${cpugraph 000000 ffffff}
PID       NAME ${alignr}CPU%   MEM%
${top pid 1}   ${top name 1} ${alignr}${top cpu 1} ${top mem 1}
${top pid 2}   ${top name 2} ${alignr}${top cpu 2} ${top mem 2}
${top pid 3}   ${top name 3} ${alignr}${top cpu 3} ${top mem 3}
${top pid 4}   ${top name 4} ${alignr}${top cpu 4} ${top mem 4}

${color1}MEMORY ($mem) ${hr 2}$color
RAM:   $memperc%   $alignr${membar 8,150}
Swap:  $swapperc%   $alignr${swapbar 8,150}
PID       NAME ${alignr}CPU%   MEM%
${top_mem pid 1}   ${top_mem name 1} $alignr${top_mem mem 1} ${top_mem cpu 1}
${top_mem pid 2}   ${top_mem name 2} $alignr${top_mem mem 2} ${top_mem cpu 2}
${top_mem pid 3}   ${top_mem name 3} $alignr${top_mem mem 3} ${top_mem cpu 3}


${color1}FILESYSTEMS  ${hr 2}$color
/ %{fs_used //${fs_size /} $alignr${fs_bar 8,150 /}
/stor %{fs_used /stor/${fs_size /stor} $alignr${fs_bar 8,150 /stor}

${color1}NETWORK ETH0 (${addr {{iface}}}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,125.0 000000 ff0000} ${alignr}${upspeedgraph eth0
25,125.0 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}


${color1}KERNEL MESSAGES  ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | awk '{print " ",$5,$6,$7,$8,$9,$10}' | fold -sw52}

${color1}LOGGED IN ($uptime_short) ${hr 2}$color
${execi 60 who}

${color1}NETWORK USAGE  ${hr 2}$color
${execi 30 netstat -ept | grep ESTAB | awk '$9 ~ /-/ {print $4, "=>", $5} $9 ~ /\// { print $9, "=>", $5}' | sort | head -n3 - }

${color1}MUSIC ($xmms2_status) ${hr 2}$color
$xmms2_title
$xmms2_artist
$xmms2_album
${xmms2_bar 8}

${color1}FEED (${rss http://rss.slashdot.org/Slashdot/slashdot 1 feed_title}) ${hr 2}$color
${rss http://rss.slashdot.org/Slashdot/slashdot 1 item_titles}

${color1}FORTUNE  ${hr 2}$color
${execi 60 fortune -s | fold -sw52}


Updated $updates times
```

This is release 1. I'm numbering my releases in binary.

P.S. Please back up your current .conkyrc first. Also, remember that I am not responsible for anything bad that happens - but nothing really bad should happen.

P.P.S. Also, make sure you read the Jinja2 docs (see [http://jinja.pocoo.org/2/documentation/templates](http://jinja.pocoo.org/2/documentation/templates)). A .conkyrcrc is essentially a giant template, so reading the docs for the template language might clear up some confusion.

---

### Post by PacSci on 2009-04-12
Sorry for the double post, but I discovered a couple of bugs in release 1, related to the filesystems and ifaceinfo macros. Now, I'm posting release 10 to make up for it.

---

### Post by ghostandmachine on 2009-04-13
hey!

someone heard about my idea!!

[http://ubuntuforums.org/showthread.php?t=1067596](http://ubuntuforums.org/showthread.php?t=1067596)

I'm excited about the app. keep up the good work.

---

### Post by omns on 2009-04-13
Looks like a very promising concept. I wish you well with it and hope it gets some interest from the community.

---

