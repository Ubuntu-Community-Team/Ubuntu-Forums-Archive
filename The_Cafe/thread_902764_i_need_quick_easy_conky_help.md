---
title: "i need quick easy conky help"
date: 2008-08-27
forum: The Cafe
---

### Post by BlackLLama on 2008-08-27
i just need the amarok part removed, i can't find anything about a now playing in my conky file.

background no
font Sans:size=7
#xftfont Sans:size=10
use_xft yes
xftalpha 0.9
update_interval 1.0
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 220 5
maximum_width 250
draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders yes
default_color white
default_shade_color black
default_outline_color green
alignment top_right
gap_x 12
gap_y 35
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no
uppercase no # set to yes if you want all text to be in uppercase

TEXT
${color white}SYSTEM ${hr 1}${color}
${color #0077ff}$sysname $kernel $machine - $nodename
${color #FFE303}Uptime: $alignr$uptime${color}${color red}
CPU: ${alignr}${freq} MHz
Processes: ${alignr}$processes ($running_processes running)
Load: ${alignr}$loadavg${color}${color #0077ff}

CPU 1: ${cpu cpu1}% ${alignr}
${cpubar cpu1}${cpubar 4 cpu1}
CPU 2: ${cpu cpu2}% ${alignr}
${cpubar cpu2}${cpubar 4 cpu2}
${color #0077ff}${cpugraph 000000 0077ff}
${color #0077ff}Proces:${color lightgrey} $processes ${color #0077ff}Run:${color lightgrey} $running_processes ${color #0077ff}CPU:${color lightgrey} ${acpitemp} C ${color lightgrey}${color #ffffff}
Ram ${alignr}$mem / $memmax ($memperc%)
${membar 4}
swap ${alignr}$swap / $swapmax ($swapperc%)
${swapbar 4}${color red}
Highest CPU $alignr CPU% MEM%${color}
${color #ff9900}${top name 1}$alignr${top cpu 1}${top mem 1}
${top name 2}$alignr${top cpu 2}${top mem 2}
${top name 3}$alignr${top cpu 3}${top mem 3}
${color red}Highest MEM $alignr CPU% MEM%
${color #ff9900}${top_mem name 1}$alignr${top_mem cpu 1}${top_mem mem 1}
${top_mem name 2}$alignr${top_mem cpu 2}${top_mem mem 2}
${top_mem name 3}$alignr${top_mem cpu 3}${top_mem mem 3}
${color}${color #0077ff}Filesystem ${hr 1}${color}
${fs_free /} free out of ${fs_size /}
${fs_bar 4 /}${color}

---

### Post by cpetercarter on 2008-08-27
Sorry, I don't understand. There is no Amarok part in your .conkyrc file, so obviously you cannot remove it. 
Maybe you mean, how can you add a "now playing" section. If so, have a look at [http://ubuntuforums.org/showthread.php?t=481720]("http://ubuntuforums.org/showthread.php?t=481720")

---

### Post by habtool on 2008-08-27
Have you kill the conky process?
You need to kill and re-start conky to ensure any changes to the conky config file are loaded.

---

### Post by ~LoKe on 2008-08-27
```
killall conky && conky
```

---

### Post by tshearman on 2008-08-27
I don't want to take away from his question... but I have another conky question (hopefully with a quick answer).

I want to display my HDD space in this fashion (for example):

WDP1: 74.51 / 140.00 GiB
as opposed to this
WDP1: 74.51GiB / 140.00GiB

However, I don't know how to get ride of the units on the first variable.  Code looks like this:

```
WDP1:  ${fs_free /media/WDP1}/ ${fs_size /media/WDP1}  ${fs_bar 6 /media/WDP1}
```

---

