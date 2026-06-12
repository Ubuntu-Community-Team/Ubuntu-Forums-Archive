---
title: "Problem conky (size window height)"
date: 2008-08-06
forum: The Cafe
---

### Post by bombe on 2008-08-06
I'm trying configure conkyrc.conf, because i'm changing my configuration file but the window's doesnt have more height .  If erase few lines for example about NETWORK then i can view the last block with feeds news.

Is possible configure the conky as auto_size window?, if i want to add more information

Paste mi conkyrc.conf
background no
font Zekton:size=6
xftfont Zekton:size=6
use_xft yes
xftalpha 0.1
update_interval 2.0
total_run_times 0
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
minimum_size 400 20 
maximum_width 300 
default_color d7d7d7
default_shade_color black
default_outline_color black
alignment top_right
gap_x 6
gap_y 30
no_buffers yes
cpu_avg_samples 2
override_utf8_locale no
uppercase no # set to yes if you want all text to be in uppercase
use_spacer yes

TEXT


${font Zekton:style=Bold:pixelsize=42}${alignc}${time %H:%M:%S}${font Zekton:size=10}
${alignc}${time %d de %B}${font Zekton:size=7}

SYSTEM ${hr 1 }
Hostname: $alignr$nodename
Kernel: $alignr$kernel
Uptime: $alignr$uptime
Processes: ${alignr}$processes ($running_processes running)
Load: ${alignr}$loadavg
CPU ${alignc} ${freq}MHz ${alignr}(${cpu cpu1}%)
${cpubar 4 cpu1}
${cpugraph}
RAM ${alignr}$mem / $memmax ($memperc%)
${membar 4}
SWAP ${alignr}$swap / $swapmax ($swapperc%)
${swapbar 4}
Highest CPU $alignr CPU% MEM%
${top name 1}$alignr${top cpu 1}${top mem 1}
${top name 2}$alignr${top cpu 2}${top mem 2}
Highest MEM $alignr CPU% MEM%
${top_mem name 1}$alignr${top_mem cpu 1}${top_mem mem 1}
${top_mem name 2}$alignr${top_mem cpu 2}${top_mem mem 2}

FILESYSTEM ${hr 1}${color}
Home: ${alignr}${fs_free /} / ${fs_size /}
${fs_bar 4 /}

NETWORK ${hr 1}${color}
Down ${downspeed eth0} k/s ${alignr}Up ${upspeed eth0} k/s
${downspeedgraph eth0 25,107} ${alignr}${upspeedgraph eth0 25,107}
Total ${totaldown eth0} ${alignr}Total ${totalup eth0)


NOTICIAS ${hr 1}${color}
${color #5b6dad}Marca:
${color #7f8ed3}${execi 300 /home/oscar/scripts/conky-rss.sh http://feeds.marca.com/marca/ultimahora}

---

### Post by billgoldberg on 2008-08-06
I don't get what you mean.

Could you be a little more specific?

---

