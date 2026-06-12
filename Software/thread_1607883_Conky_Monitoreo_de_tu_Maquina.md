---
title: "Conky Monitoreo de tu Maquina"
date: 2010-10-28
forum: Software
---

### Post by RafaelG on 2010-10-28
Estimados,

Bueno para todos aquellos que les interese mantener monitoriada su maquina utilizando Conky en Ubuntu. Dejo mi **.conkyrc** aunque es muy basico pero cumple con mis necesidades actuales en mi Notebook.

[HTML]
# Conky sample configuration
#
# the list of variables has been removed from this file in favour
# of keeping the documentation more maintainable.
# Check http://conky.sf.net for an up-to-date-list.

# set to yes if you want Conky to be forked in the background
background yes

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*


# Use Xft?
use_xft yes

# Set conky on the bottom of all other applications
own_window_hints below

# Xft font when Xft is enabled
xftfont Sans:style=Bold:size=8

# Text alpha when using Xft
xftalpha 1

# Print everything to stdout?
# out_to_console no

# MPD host/port
# mpd_host localhost
# mpd_port 6600
# mpd_password tinker_bell

# Print everything to console?
# out_to_console no

# mail spool
#mail_spool $MAIL

# Update interval in seconds
update_interval 1qq

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_hints undecorated,below,skip_taskbar
own_window_type override

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window_transparent is set to no, you can set the background colour here
#own_window_colour hotpink

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 280 5

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 8

# border margins
border_margin 10

# border width
border_width 10

# Default colors and also border colors
#default_color white
#default_shade_color black
#default_outline_color black

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 30
gap_y 30

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 1

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 1

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no


# Add spaces to keep things from moving about? This only affects certain objects.
use_spacer yes

# mldonkey_hostname Hostname for mldonkey stuff, defaults to localhost
# mldonkey_port Mldonkey port, 4001 default
# mldonkey_login Mldonkey login, default none
# mldonkey_password Mldonkey password, default none

# boinc (seti) dir
# seti_dir /opt/seti

# Allow for the creation of at least this number of port monitors (if 0 or not set, default is 16)
min_port_monitors 16

# Allow each port monitor to track at least this many connections (if 0 or not set, default is 256)
min_port_monitor_connections 256

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

TEXT

${color red}UBUNTU MAVERICK 10.10 

${color blue}Load Average: ${color white}$loadavg% 
${color blue}CPU:   ${color white}$cpu%  ${freq} MHz 
${color blue}RAM:   ${color white}$memperc%  ${mem}B / ${memmax}B$color
${color blue}Swap:  ${color white}$swapperc%  ${swap}B / ${swapmax}B${color black}

${color blue}CPU Usage      PID     CPU%   MEM%
${color blue} ${top name 1} ${color white}${top pid 1} ${top cpu 1} ${top mem 1}
${color blue} ${top name 2} ${color white}${top pid 2} ${top cpu 2} ${top mem 2}
${color blue} ${top name 3} ${color white}${top pid 3} ${top cpu 3} ${top mem 3}

${color blue}Mem Usage
${color blue} ${top_mem name 1} ${color white}${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
${color blue} ${top_mem name 2} ${color white}${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
${color blue} ${top_mem name 3} ${color white}${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}

${color blue}Hard Drives:
${color blue} Root ${color white}${fs_used /}/${fs_size /}${alignr}${color black}${fs_bar 5,120 /}
${color blue} Home ${color white}${fs_used /home}/${fs_size /home}${alignr}${color black}${fs_bar 5,120 /home}
[/HTML]Post donde muestran muchos **.conkyrc         **[ http://ubuntuforums.org/showthread.php?t=281865&highlight=show+conky]("http://ubuntuforums.org/showthread.php?t=281865&highlight=show+conky")

---

