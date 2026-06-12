---
title: "Conky Battery help"
date: 2011-03-10
forum: The Cafe
---

### Post by OCPIMP on 2011-03-10
I am fairly new to Ubuntu but so far I am loving every min of it. I have recently set up conky but I am having trouble getting the remaining battery time to be displayed. 

here is my .conkyrc file 
> 

#set to yes if you want Conky to be forked in the background
background no

#Xft font
xftfont Terminus:size=8
xftalpha 1

#Update interval in sec
update_interval 1
total_run_times 0

#Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

#Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes
minimum_size 220 5
maximum_width 300

#Draws shades
draw_shades no

#Text stuff
draw_outline no #amplifies text if yes
draw_borders no
uppercase yes #set to yes if you want all caps

draw_graph_borders yes
default_color white
default_shade_color black

#Text alignment (remove to # to change it)
#alignmnet top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

#Gap between borders of screen and text
gap_x 12
gap_y 35

#subtract file system buffers from ubsed memory
no_buffers yes

#number of cpu samples to average
#set to 1 o disable averaging
cpu_avg_samples 2

#force UTF8 (note that utf8 support rquired XFT)
override_utf8_locale no
total_run_times 0

#Stuff after TEXT will be formatted on screen!!!!

TEXT
SYSTEM ${hr 2}
${time %G %B %e} ${alignr} ${time %H:%M}
Host: $alignr $nodename
Kernel: $alignr $kernel
Uptime: $alignr $uptime
${color #ddaa00} CPU: ${alignr}${acpitemp}C$color
${hr 2} 
Battery: 
    $tab $tab Adapter Stat: $alignr ${acpiacadapter}
    $tab $tab Info: $alignr ${battery}
    $tab $tab Time Remaining:${battery_time}

CPU ${hr 2}
CPU1: ${alignr} ${cpu cpu1}%
CPU2: ${alignr} ${cpu cpu2}%
${cpugraph 25,140 00FFFF 00ff00}
Processes: $alignr $processes
Running: $alignr $running_processes
TOP

Name $alignr PID     CPU%   MEM%
${color #ddaa00} ${top name 1} $alignr ${top pid 1} ${top cpu 1} ${top mem 1}$color
${top name 2} $alignr ${top pid 2} ${top cpu 2} ${top mem 2}

Mem usage$color
${color #ddaa00} ${top_mem name 1} $alignr ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}$color
${top_mem name 2} $alignr ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}


RAM: $alignr $mem/$memmax
${membar 3}
Swap: $alignr $swap / $swapmax
${swapbar 3}
HDD1: $alignr ${fs_free /} / ${fs_size /}
${fs_bar 3 /}

Network ${hr 2}
Wireless Facts
    $tab $tab Singal: $alignr ${wireless_link_qual_perc wlan0}%
    $tab $tab ESSID: $alignr ${wireless_essid wlan0}
    $tab $tab AP MAC: $alignr ${wireless_ap wlan0}
    $tab $tab IP address: $alignr ${addr wlan0}
$stippled_hr
Down: ${color #ddaa00} $alignr ${downspeed wlan0} $color
${downspeedgraph wlan0 25,140 00FFFF 00FFFF}
Up: ${color #ddaa00} $alignr ${upspeed wlan0} $color
${upspeedgraph wlan0 25,140 00FFFF 00ff00}
Security log ${hr 2}
${execi 10 /usr/bin/tail -n 5 /var/log/auth.log | cut -c 27-}
This is what my Conky looks like
[IMG]http://ubuntuforums.org/home/edward/conky.png[/IMG]

---

### Post by DZoom on 2011-09-16
how is the solution for this problem?
still can't figure out how to get the remaining battery time from my macbook pro 8,1

---

