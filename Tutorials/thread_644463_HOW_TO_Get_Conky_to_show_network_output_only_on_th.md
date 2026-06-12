---
title: "HOW TO: Get Conky to show network output only on the active interface (scriptless)"
date: 2007-12-18
forum: Tutorials
---

### Post by HDave on 2007-12-18
I love the network speed and graphs in conky.  However, I have a laptop that has 5 different interfaces:

1) eth0 - built in ethernet
2) eth1 - Gigabit PC card for work
3) eth2 - Gigabit PC card for home
4) ppp0 -- verizon wireless card
5) wlan0 -- wireless lan (wifi)

I want Conky to only show the 1 or 2 interfaces that are UP and in use at any given point in time.  By up and in-use I mean that the interface has an active IP address.

I found a way to do this by running a script from within ${if_empty ..} variable, but it tripled the cpu resource to run.  Apparently even if you use ${execi 30 ...} if you use it within an "if" clause it runs every second, not every 30 seconds.

At any rate, the way I got it to work was to use an execi command to create a temp file in my home directory named after the interface (.conky_eth0, .conky_ppp0, etc.).  Conky creates these ever 30 seconds. I then use the ${if_existing ...} variable to conky to check for the file every second.

The result is a low-resource, non-script way to only show the networking data for the interface I care about.   Here's my entire conky...note the networking section at the end.  Its a bit crowded because I jammed all the text onto one line, but you get the drift.  I used the ifconfig -s command to see if the interface exists at all and then I used the ifconfig -a command to see if the interface has an IP address.

Obviously, you'll need to edit to have it work with your specific interfaces.

```
background yes
use_xft yes
xftfont Trebuchet MS:size=10
xftalpha 0.9
update_interval 1.0
total_run_times 0
own_window yes
# own_window_type normal=(minimizes with minimize all)
# own_window_type desktop=(dissapears when clicking on desktop)
# own_window_type override=(has border and shows up on top of everything after reboot)
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
# own_window_hints below (for override)
double_buffer yes
minimum_size 180 5
maximum_width 180
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no

# Stippled borders?
# stippled_borders 8
# border margins
# border_margin 2
# border width
# border_width 1

default_color white
default_shade_color red
default_outline_color green

# alignment top_left
alignment top_right
# alignment bottom_left
# alignment bottom_right
# alignment none

gap_x 12
gap_y 30
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no

# WISH LIST
# single IP-network stuff set (auto uses the right one)
# trim processor name ${execi 5 cat /proc/cpuinfo | grep 'model name' | sed -e 's/model name.*: //' | tail -n1}
# fan speed (sensors??)
# battery only if discharging (${battery} says discharging....)
# space of /sda1 only if mounted  !!! if_mounted(mountpoint)....
# $ platform devices????
# Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}



TEXT
System $hr
Name:$alignr$nodename
Arch:$alignr$machine
Kernel:$alignr$kernel
Uptime:$alignr$uptime

Processor $hr
CPU1: ${cpu cpu1}% ${color lightgray}${cpubar cpu1}$color
CPU2: ${cpu cpu2}% ${color lightgray}${cpubar cpu2}$color
Processes: ${processes}$alignr Running: ${running_processes}
Temperature:$alignr${acpitemp} C

Memory $hr
RAM: $memperc% ${color lightgray}$membar$color
Usage:$alignr$mem/$memmax

Battery $hr
Power: ${battery_percent}% ${color lightgray}${battery_bar BAT0}$color
Time:$alignr${battery_time BAT0}

Disk Space $hr
Root: ${fs_used_perc /}% ${color lightgray}${fs_bar /}$color
Usage:$alignr$fs_used/$fs_size
Temperature: $alignr${execi 300 nc localhost 7634 | cut -d"|" -f4 ;} C

Network $hr
${execi 30 rm -f .conky_eth0; ifconfig -s | grep eth0 > /dev/null && ifconfig -a eth0 | grep 'inet addr:' > /dev/null && touch .conky_eth0}${execi 30 rm -f .conky_eth1; ifconfig -s | grep eth1 > /dev/null && ifconfig -a eth1 | grep 'inet addr:' > /dev/null && touch .conky_eth1}${execi 30 rm -f .conky_eth2; ifconfig -s | grep eth2 > /dev/null && ifconfig -a eth2 | grep 'inet addr:' > /dev/null > /dev/null && touch .conky_eth2}${execi 30 rm -f .conky_ppp0; ifconfig -s | grep ppp0 > /dev/null && ifconfig -a ppp0 | grep 'inet addr:' > /dev/null && touch .conky_ppp0}${execi 30 rm -f .conky_wlan0; ifconfig -s | grep wlan0 > /dev/null && ifconfig -a wlan0 | grep 'inet addr:' > /dev/null && touch .conky_wlan0}${if_existing /home/username/.conky_eth0}IP (eth0):$alignr${addr eth0}
Down: ${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${color lightgray}${downspeedgraph eth0 20,80 444444 eeeeee} ${alignr}${upspeedgraph eth0 20,80 444444 eeeeee}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
${endif}${if_existing /home/username/.conky_eth1}IP (eth1):$alignr${addr eth1}
Down: ${downspeed eth1} k/s ${alignr}Up: ${upspeed eth1} k/s
${color lightgray}${downspeedgraph eth1 20,80 444444 eeeeee} ${alignr}${upspeedgraph eth1 20,80 444444 eeeeee}$color
Total: ${totaldown eth1} ${alignr}Total: ${totalup eth1}
${endif}${if_existing /home/username/.conky_eth2}IP (eth2):$alignr${addr eth2}
Down: ${downspeed eth2} k/s ${alignr}Up: ${upspeed eth2} k/s
${color lightgray}${downspeedgraph eth2 20,80 444444 eeeeee} ${alignr}${upspeedgraph eth2 20,80 444444 eeeeee}$color
Total: ${totaldown eth2} ${alignr}Total: ${totalup eth2}
${endif}${if_existing /home/username/.conky_ppp0}IP (ppp0):$alignr${addr ppp0}
Down: ${downspeed ppp0} k/s ${alignr}Up: ${upspeed ppp0} k/s
${color lightgray}${downspeedgraph ppp0 20,80 444444 eeeeee} ${alignr}${upspeedgraph ppp0 20,80 444444 eeeeee}$color
Total: ${totaldown ppp0} ${alignr}Total: ${totalup ppp0}
${endif}${if_existing /home/username/.conky_wlan0}IP (wlan0):$alignr${addr wlan0}
Down: ${downspeed wlan0} k/s ${alignr}Up: ${upspeed wlan0} k/s
${color lightgray}${downspeedgraph wlan0 20,80 444444 eeeeee} ${alignr}${upspeedgraph ppp0 20,80 444444 eeeeee}$color
Total: ${totaldown wlan0} ${alignr}Total: ${totalup wlan0}
${endif}

```

Enjoy.

---

### Post by matsch on 2008-01-04
Hi HDave,

from your inspiration I followed two different approach, where no exec-statements are needed at all.

1. approach: Create the files in a script in /etc/network/if-up.d/conky and delete them in /etc/network/if-down.d/conky
If you do this you can just delete all the "${execi 30 rm -f .conky_eth0; [...]"-statements in your .conkyrc.

2. (better) approach: Check in /etc/network/run/ifstate if the interface is up
In /etc/network/run/ifstate those network interfaces are listet, which are currently up and running. Conky can check this.

In your .conkyrc delete all the "${execi 30 rm -f .conky_eth0; [...]"-statements.
Then for all interfaces replace ```
${if_existing /home/username/.conky_eth0}
``` with ```
${if_existing /etc/network/run/ifstate eth0=eth0}
```

(You should check if your ifstate-file has the same syntax. (eth0=eth0))

With this the .conkyrc of HDave from above would look like this:

```
background yes
use_xft yes
xftfont Trebuchet MS:size=10
xftalpha 0.9
update_interval 1.0
total_run_times 0
own_window yes
# own_window_type normal=(minimizes with minimize all)
# own_window_type desktop=(dissapears when clicking on desktop)
# own_window_type override=(has border and shows up on top of everything after reboot)
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
# own_window_hints below (for override)
double_buffer yes
minimum_size 180 5
maximum_width 180
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no

# Stippled borders?
# stippled_borders 8
# border margins
# border_margin 2
# border width
# border_width 1

default_color white
default_shade_color red
default_outline_color green

# alignment top_left
alignment top_right
# alignment bottom_left
# alignment bottom_right
# alignment none

gap_x 12
gap_y 30
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no

# WISH LIST
# single IP-network stuff set (auto uses the right one)
# trim processor name ${execi 5 cat /proc/cpuinfo | grep 'model name' | sed -e 's/model name.*: //' | tail -n1}
# fan speed (sensors??)
# battery only if discharging (${battery} says discharging....)
# space of /sda1 only if mounted  !!! if_mounted(mountpoint)....
# $ platform devices????
# Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}



TEXT
System $hr
Name:$alignr$nodename
Arch:$alignr$machine
Kernel:$alignr$kernel
Uptime:$alignr$uptime

Processor $hr
CPU1: ${cpu cpu1}% ${color lightgray}${cpubar cpu1}$color
CPU2: ${cpu cpu2}% ${color lightgray}${cpubar cpu2}$color
Processes: ${processes}$alignr Running: ${running_processes}
Temperature:$alignr${acpitemp} C

Memory $hr
RAM: $memperc% ${color lightgray}$membar$color
Usage:$alignr$mem/$memmax

Battery $hr
Power: ${battery_percent}% ${color lightgray}${battery_bar BAT0}$color
Time:$alignr${battery_time BAT0}

Disk Space $hr
Root: ${fs_used_perc /}% ${color lightgray}${fs_bar /}$color
Usage:$alignr$fs_used/$fs_size
Temperature: $alignr${execi 300 nc localhost 7634 | cut -d"|" -f4 ;} C

Network $hr
${if_existing /etc/network/run/ifstate eth0=eth0}IP (eth0):$alignr${addr eth0}
Down: ${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${color lightgray}${downspeedgraph eth0 20,80 444444 eeeeee} ${alignr}${upspeedgraph eth0 20,80 444444 eeeeee}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
${endif}${if_existing /etc/network/run/ifstate eth1=eth1}IP (eth1):$alignr${addr eth1}
Down: ${downspeed eth1} k/s ${alignr}Up: ${upspeed eth1} k/s
${color lightgray}${downspeedgraph eth1 20,80 444444 eeeeee} ${alignr}${upspeedgraph eth1 20,80 444444 eeeeee}$color
Total: ${totaldown eth1} ${alignr}Total: ${totalup eth1}
${endif}${if_existing /etc/network/run/ifstate eth2=eth2}IP (eth2):$alignr${addr eth2}
Down: ${downspeed eth2} k/s ${alignr}Up: ${upspeed eth2} k/s
${color lightgray}${downspeedgraph eth2 20,80 444444 eeeeee} ${alignr}${upspeedgraph eth2 20,80 444444 eeeeee}$color
Total: ${totaldown eth2} ${alignr}Total: ${totalup eth2}
${endif}${if_existing /etc/network/run/ifstate ppp0=ppp0}IP (ppp0):$alignr${addr ppp0}
Down: ${downspeed ppp0} k/s ${alignr}Up: ${upspeed ppp0} k/s
${color lightgray}${downspeedgraph ppp0 20,80 444444 eeeeee} ${alignr}${upspeedgraph ppp0 20,80 444444 eeeeee}$color
Total: ${totaldown ppp0} ${alignr}Total: ${totalup ppp0}
${endif}${if_existing /etc/network/run/ifstate wlan0=wlan0}IP (wlan0):$alignr${addr wlan0}
Down: ${downspeed wlan0} k/s ${alignr}Up: ${upspeed wlan0} k/s
${color lightgray}${downspeedgraph wlan0 20,80 444444 eeeeee} ${alignr}${upspeedgraph ppp0 20,80 444444 eeeeee}$color
Total: ${totaldown wlan0} ${alignr}Total: ${totalup wlan0}
${endif}
```

Regards,
matsch

---

### Post by HDave on 2008-01-12
Hi Matsch -- Thanks for the info.   I like the idea of checking this ifstate file, but I don't have a /etc/network/run directory?  Where does this come from?  A package?

Also, I am unsure about the if-up.d and if-down.d idea.  Check out the result an "ifconfig":

```
eth0      Link encap:Ethernet  HWaddr 00:18:8B:BD:2B:4A  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 

eth2      Link encap:Ethernet  HWaddr 00:00:5A:00:04:55  
          inet addr:192.168.1.124  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::200:5aff:fe00:455/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15404 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12123 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7001255 (6.6 MB)  TX bytes:1511105 (1.4 MB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:294 errors:0 dropped:0 overruns:0 frame:0
          TX packets:294 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:237964 (232.3 KB)  TX bytes:237964 (232.3 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:192.168.141.1  Bcast:192.168.141.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:192.168.175.1  Bcast:192.168.175.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:19:7D:8E:93:35  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Memory:ecffc000-ed000000 

```

Note that all 6 interfaces indicate they are "UP".  Would a script in if-up.d really work?

Thanks again!

---

### Post by kjbuente on 2008-01-13
Okay, third time editing this...

I found out how to make it only show the OPERATIONAL network device! FINALLY!!! :guitar:

Okay, We need to find out where the system mapped our network devices. My wired connection was located at "/sys/devices/pci0000:00/0000:00:1e.0/0000:02:0e.0". (I used the "Hardware Information"  under Preferences to find it. It's located under the advanced tab).
We need now to look for a folder that has the name of the ethernet device. Mine was called "net:eth0", in there is a file called "operstate". This is the file we want conky to point to.
So now, let's edit our conkyrc file.
```
${if_existing /sys/devices/pci0000:00/0000:00:1e.0/0000:02:0e.0/net:eth0/operstate up} [blablabla] ${endif}
```

I did have issues with conky resizing to allow the new stuff to get on the screen. Changing "own_window_type override" seemed to fix it.

Here is my copy of conkyrc for an example...

```
# Conky sample configuration
#
# the list of variables has been removed from this file in favour
# of keeping the documentation more maintainable.
# Check http://conky.sf.net for an up-to-date-list.

# set to yes if you want Conky to be forked in the background
background no

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

# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono:size=8

# Text alpha when using Xft
xftalpha 0.8

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
update_interval 1.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes

# If own_window is yes, you may use type normal, desktop or override
own_window_type override

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window_transparent is set to no, you can set the background colour here
own_window_colour black

# If own_window is yes, these window manager hints may be used
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

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

# Draw borders around graphs
draw_graph_borders yes

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color black

#dexter_client no
#dexter_server no
#config file for libdexter (default search path: $HOME/.dexterrc; /etc/libdexter/dexter.conf)
#dexter_config

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
#alignment bottom_left
alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 12
gap_y 12

# Subtract file system buffers from used memory?
no_buffers no

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

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer no

# Allow each port monitor to track at most this many connections (if 0 or not set, default is 256)
#max_port_monitor_connections 0

# Maximum number of special things, e.g. fonts, offsets, aligns, etc.
#max_specials 512

# Maximum size of buffer for user text, i.e. below TEXT line.
#max_user_text 16384

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

TEXT

NC8000 - $sysname $kernel on $machine
${color lightgrey}AC Power:$color $acpiacadapter
${color lightgrey}Battery 1 Status:$color ${battery C137}  ${battery_time C137}
${color lightgrey}Battery 2 Status:$color ${battery C136}  ${battery_time C136}
$stippled_hr
${color lightgrey}Uptime:$color $uptime ${color lightgrey}- Load:$color $loadavg
${color lightgrey}CPU Usage:${color #cc2222} $cpu% ${cpubar}
${color} ${cpugraph}
${color lightgrey}CPU Speed:$color $freq_dyn Mhz ${color lightgrey}CPU Temp:$color $acpitempf Degrees
${color lightgrey}Processes:$color $processes  ${color grey}Running:$color $running_processes
${color}Name              PID     CPU%   MEM%
${color #ddaa00} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color lightgrey} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color lightgrey} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color lightgrey} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}
$color$stippled_hr
${color lightgrey}File Systems:
${color lightgrey} Root   $color${fs_free /}/${fs_size /}   ${fs_bar /}
${color lightgrey} Home   $color${fs_free /home}/${fs_size /home}   ${fs_bar /home}${if_mounted /media/disk}
${color lightgrey} MS    ${color} ${fs_free /media/disk}/${fs_size /media/disk}   ${fs_bar /media/disk}${endif}
${color lightgrey} RAM    $color $mem/$memmax    ${membar}
${color lightgrey} Swap  $color $swap/$swapmax    ${swapbar}
${color lightgrey}Disk Read-Write IO$color	          $diskio_read - $diskio_write
$stippled_hr
${color lightgrey}Wireless Mode: $color ${wireless_mode ath0}
${if_existing /sys/devices/pci0000:00/0000:00:1e.0/0000:02:04.0/net:ath0/operstate up}${color lightgrey}Wireless Rate:$color ${wireless_bitrate ath0} ${color lightgrey}Link Quality: $color ${wireless_link_qual_perc ath0}
${color lightgrey}IP Address:$color ${addr ath0} ${color lightgrey}Associated With:$color ${wireless_essid ath0}
 Down:${color #8844ee} ${downspeed ath0} k/s${color lightgrey} ${offset 80}Up:${color #22ccff} ${upspeed ath0} k/s
${color #000000}${downspeedgraph ath0 32,150 ffffff ffffff} ${color #000000}${upspeedgraph ath0 32,150 ffffff ffffff}${endif}
${if_existing /sys/devices/pci0000:00/0000:00:1e.0/0000:02:0e.0/net:eth0/operstate up}${color lightgrey}Wired IP Address: $color${addr eth0}
 Down:${color #8844ee} ${downspeed eth0} k/s${color lightgrey} ${offset 80}Up:${color #22ccff} ${upspeed eth0} k/s
${color #000000}${downspeedgraph eth0 32,150 ffffff ffffff} ${color #000000}${upspeedgraph eth0 32,150 ffffff ffffff}${endif}
```

---

### Post by HDave on 2008-01-13
Brilliant Work kjbuente!!!!!!

It works like a charm! And is soooo much simpler.  I did notice however that the directories you indicated were all linked directories to the **/sys/class/net/** directory.

So you can end up with a shorter path if you just do this:

```
${if_existing /sys/class/net/eth0/operstate up} [blablabla] ${endif}
```

Now I am motivated to also find a simpler way to determine if my Verizon modem is operational.   It's a USB device, not PCI, so the approach may need to be different...

Ahhh...sweet victory...

---

### Post by kjbuente on 2008-01-14
LOL, I just noticed that they are in that directory as well. (I went to post it here, but you got to it first). It's a lot easier then trying to find were the device is mapped.

I actually just added my verizon connection in conky right now. (via bluetooth, not usb. But should will work the some, also pcmcia would work too). When you create a connection, in /sys/class/net there will be a folder that will be created. (It  is removed when the connection is closed).   Just do the same as the other devices, but with one difference. Instead of it checking the file to see if it is up. It has to just check if it is there. The status stays at unknown...

Some conky code:

```
${if_existing /sys/class/net/ppp0/operstate}
```

Thats it! Enjoy! :guitar:

---

### Post by HDave on 2008-01-14
kjbuente -- thats good to know...thanks.

An offtopic point here -- The fact that our ppp0 connection always has operstate  "unknown" got me wondering if that is why the gnome network manager notification applet "nm-applet" never seems to indicate the state of my verizon dial-up connection.

It's a small annoyance, but something I wish I could fix.  Does it work for you?

If not, check out this bug:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/82335]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/82335")

---

### Post by kjbuente on 2008-01-14
I use gnome-ppp to connect to the internet. Works nicely exept the fact that it always say that it is dialing even though it is connected.

I think that the operstate at unkown has a something to do with it, but not the only thing. I think it also has something to do with the fact that there is no ppp entry at /etc/networking/interfaces. (Not 100% sure that is a valid path since I'm on a friends windows machine). I wonder if we make one for it, how nm-applet would  it react. I'm sure it would not be a fix, but be interesting none the less. I'll try this latter tonight when I can get my laptop again and fudge a ppp entry.

Till then...

Update: for thoese who use static. You can disable NetworkManager from handling a specific devices. Just comment out the device in the file mentioned above. I do not know if the connection status is sent though the dbus for apps to know if it is connected.

---

### Post by LauraSakura on 2008-01-15
eth0 (my ethernet connection)'s operstate file always reports as unknown. any idea of any work arounds?

edit:
Actually it looks like both eth0 and eth1's operstate files report as unknown :(

---

### Post by kjbuente on 2008-01-15
Honestly, I have no clue. Sorry... :(

But that does not mean I won't try. Few questions...

Are you using DHCP or static network connections? I noticed that the operstate just happens to go up when a DHCP address as been assigned. I have not tried static yet to see if it works, just low on time.

What NIC are you using? Is it wired, wireless? What chipset?

It is always at unknown if you shut down the device? (sudo ifconfig eth0 down)


Just a though off the top of my head. It may have something to do with how the drivers communicate with the system. (That and there might be a difference between 32 and 64 bit system. I have no clue though, but I'm using 32bit for the record). I'm curently looking for another place to see if the connection is active. But not having much luck, I'm still learning how device are set as active.

---

### Post by kjbuente on 2008-03-16
HA! Took me forever but I found it!

Instead of the path that I have above. Use this instead...

{if_existing /proc/net/route eth0}.

I think this is what the computer uses to see if there is a active connection.

Can anyone test? Working great for me!

---

### Post by HDave on 2008-03-17
kjbuente -- I tried your new approach and it works...including support for ppp connections.

I am not sure what the advantage is over the previous approach though.  I've been happy with it for the past few months...no issues...

---

### Post by wanchai on 2008-04-22
Great stuff, but it seems that in conky 1.5.1 which we will get with Hardy you can use something like this:

```
if_up 	(interface)
if INTERFACE exists and is up, display everything between $if_up and the matching $endif
```

source: [http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)

---

### Post by kevdog on 2008-04-22
This if_up feature is currently being worked on and in fact a user has submitted a patch to make it work in the manner everyone would like:

[http://sourceforge.net/mailarchive/forum.php?thread_name=18acc6960804081951ta37bab9l1531e42ff93b075a%40mail.gmail.com&forum_name=conky-development](http://sourceforge.net/mailarchive/forum.php?thread_name=18acc6960804081951ta37bab9l1531e42ff93b075a%40mail.gmail.com&forum_name=conky-development)

Although I have not personally upgraded to 1.51 (DISCLAIMER), it does not appear to be functional or produce the desired behaivor as of today.

---

### Post by HDave on 2008-06-04
Just tested this under Hardy and indeed it works...even for me ppp0 connection.  Nice! :)

Now if only network manager could recognize my ppp0 connections...:(

---

### Post by HDave on 2008-08-15
Must have spoken to soon, or something broke along the way.  Using "if_up" always shows eth0 even if it is not active. I am reverting back to what I had before:

```
${if_existing /sys/class/net/eth0/operstate up}IP (eth0):$alignr${addr eth0}
Down: ${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${color lightgray}${downspeedgraph eth0 20,80 444444 eeeeee} ${alignr}${upspeedgraph eth0 20,80 444444 eeeeee}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
${endif}${if_existing /sys/class/net/eth1/operstate up}IP (eth1):$alignr${addr eth1}
Down: ${downspeed eth1} k/s ${alignr}Up: ${upspeed eth1} k/s
${color lightgray}${downspeedgraph eth1 20,80 444444 eeeeee} ${alignr}${upspeedgraph eth1 20,80 444444 eeeeee}$color
Total: ${totaldown eth1} ${alignr}Total: ${totalup eth1}
${endif}${if_existing /sys/class/net/eth2/operstate up}IP (eth2):$alignr${addr eth2}
Down: ${downspeed eth2} k/s ${alignr}Up: ${upspeed eth2} k/s
${color lightgray}${downspeedgraph eth2 20,80 444444 eeeeee} ${alignr}${upspeedgraph eth2 20,80 444444 eeeeee}$color
Total: ${totaldown eth2} ${alignr}Total: ${totalup eth2}
${endif}${if_existing /sys/class/net/wlan0/operstate up}IP (wlan0):$alignr${addr wlan0}
Down: ${downspeed wlan0} k/s ${alignr}Up: ${upspeed wlan0} k/s
${color lightgray}${downspeedgraph wlan0 20,80 444444 eeeeee} ${alignr}${upspeedgraph wlan0 20,80 444444 eeeeee}$color
Total: ${totaldown wlan0} ${alignr}Total: ${totalup wlan0}
${endif}${if_existing /sys/class/net/ppp0/operstate}IP (ppp0):$alignr${addr ppp0}
Down: ${downspeed ppp0} k/s ${alignr}Up: ${upspeed ppp0} k/s
${color lightgray}${downspeedgraph ppp0 20,80 444444 eeeeee} ${alignr}${upspeedgraph ppp0 20,80 444444 eeeeee}$color
Total: ${totaldown ppp0} ${alignr}Total: ${totalup ppp0}
${endif}

```

---

### Post by sagara on 2011-01-22
I can confirm that as of ubuntu 10.10 with conky 1.8.0, the ${if_up interface} variable in conky does not work as intended.

The 
```
${if_existing /sys/class/net/eth0/operstate up} [blablabla] ${endif}
```
work around in this thread is the way to go :)

---

### Post by nigelnomates on 2011-03-18
Thanks to those who posted here, this has been very useful :)

---

### Post by Clicksights on 2011-03-24
Thanks all for testing and trying, 
i finally got my conky working!
My wlan0 and eth0 only show if there is a connection!
was trying it for days! :-P

now i want my AP ip and external ip also gone when not connected..
so a new challenge awaits...
;-)

---

### Post by Clicksights on 2011-03-25
well hate too say it, but the displaying of the eth0 doesn't work anymore today.
I did get some updates and now my operstate file doesn't change to up or down anymore, just stays on unknown...

Is this due too the update? Running ubuntu netbook.
Or did i screw up something?
Wlan works fine...

please help?!
thanks!

---

### Post by azertyh on 2011-03-27
hello,

i connect to internet with the wifi (wlan0) or the ethernet (eth0) or a 3G+ (ppp0).

my conkyrc :
```
${font DejaVu Sans Mono:size=24}&#9850;${font} Internet : ${if_existing /proc/net/route wlan0}WIFI
${font DejaVu Sans Mono:size=24}&#8679;${font} Up : ${upspeedf wlan0}k/s
${upspeedgraph wlan0 24,360 66ffff 6600ff scale -l -t}
${font DejaVu Sans Mono:size=24}&#8681;${font} Down : ${downspeedf wlan0}k/s
${downspeedgraph wlan0 24,360 66ffff 6600ff scale -l -t}${else}${if_existing /proc/net/route eth0}4G
${font DejaVu Sans Mono:size=24}&#8679;${font} Up : ${upspeedf eth0}k/s
${upspeedgraph eth0 24,360 66ffff 6600ff scale -l -t}
${font DejaVu Sans Mono:size=24}&#8681;${font} Down : ${downspeedf eth0}k/s
${downspeedgraph eth0 24,360 66ffff 6600ff scale -l -t}${else}${if_existing /proc/net/route ppp0}3G+
${font DejaVu Sans Mono:size=24}&#8679;${font} Up : ${upspeedf ppp0}k/s
${upspeedgraph ppp0 24,360 66ffff 6600ff scale -l -t}
${font DejaVu Sans Mono:size=24}&#8681;${font} Down : ${downspeedf ppp0}k/s
${downspeedgraph ppp0 24,360 66ffff 6600ff scale -l -t}${else}Not connected${endif}${endif}${endif}
```

---

### Post by b8e5n on 2011-04-01
> **sagara said:**
> I can confirm that as of ubuntu 10.10 with conky 1.8.0, the ${if_up interface} variable in conky does not work as intended.

The 
```
${if_existing /sys/class/net/eth0/operstate up} [blablabla] ${endif}
```work around in this thread is the way to go :)

Thank you, i did as you said, and it works perfectly on my ubuntu 10.10.

---

### Post by Saur0m on 2011-08-08
I also have three interfaces in my laptop: eth0 (wired), wlan0 (wifi) and ppp0 (3g USB).

Ethernet interface always is UP, no matter it has cable plugged in or not. This is the way to work in every OS, so checking it state doesn't work. My approach is to check if it has an IP address assigned. Here is my conky config file part:

```
${if_match "${addr eth0}"!="No Address"}eth0:${GOTO 120}${addr eth0}
Up (${upspeedf eth0}):${GOTO 120}${upspeedgraph eth0 15,110 330099 cc0099 -t}
Down (${downspeedf eth0}):${GOTO 120}${downspeedgraph eth0 15,110 330099 cc0099 -t}${endif}
${if_up wlan0}wlan0:${GOTO 120}${addr wlan0}
$wireless_essid   $wireless_bitrate
${GOTO 60}${wireless_link_bar 10,140} $wireless_link_qual_perc %
Up (${upspeedf wlan0}):${GOTO 120}${upspeedgraph wlan0 15,110 330099 cc0099 -t}
Down (${downspeedf wlan0}):${GOTO 120}${downspeedgraph wlan0 15,110 330099 cc0099 -t}${endif}
${if_up ppp0}ppp0:${GOTO 120}${addr ppp0}
Up (${upspeedf ppp0}):${GOTO 120}${upspeedgraph ppp0 15,110 330099 cc0099 -t}
Down (${downspeedf ppp0}):${GOTO 120}${downspeedgraph ppp0 15,110 330099 cc0099 -t}
Total Up: ${totalup ppp0}  Total Down: ${totaldown ppp0}${endif}
```

The problem is that the "hidden" section is replaced with an empty line, so there is a gap in between. It's somewhat annoying, but I could live with that :)

---

### Post by Saur0m on 2011-08-09
I found a better solution.

Conky has an option: **if_up_strictness**. Accorditng to the [documentation]("http://conky.sourceforge.net/config_settings.html"):
> _if_up_strictness_: How strict should if_up be when testing an interface for being up? The value is one of up, link or address, to check for the interface being solely up, being up and having link or being up, having link and an assigned IP address.

In other words, before the TEXT section of the config file, I put
```
if_up_strictness link
```
and voilá! the interface doesn't appears if it hasn't the cable pluged in.

My modified config file is (search for *if_up*):
```
# Default Fonts
use_xft yes
xftfont Ubuntu:size=8
override_utf8_locale yes

# Performance Settings
update_interval 1
total_run_times 0
double_buffer yes
no_buffers yes
net_avg_samples 2
text_buffer_size 1024

# Window Settings
own_window yes
own_window_transparent yes
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Window border
draw_borders no
draw_shades no

# Default Color
default_color E0DFDE

# Color Title.
color0 DD3A21

# Size and position
minimum_size 245 735
gap_x 1
gap_y 24
alignment top_right

short_units
if_up_strictness link

TEXT
${image ~/.ConkyWizardTheme/pix/background.png -p 0,0 -s 245x735}


${GOTO 36}Host:${GOTO 100}${nodename}   ($machine)
${GOTO 36}Kernel:${GOTO 100}${kernel}
{GOTO 36}Battery:${GOTO 100}${battery BAT0} ${battery_time BAT0}
${GOTO 36}$hr
${GOTO 36}${font Ubuntu:bold:size=9}${color0}CPU${font}${color}${GOTO 150}${running_processes}/${processes} Procs
${GOTO 36}CPU 0: ${GOTO 80} ${cpu cpu1}%  ${GOTO 160}${freq_g 1} GHz
${GOTO 60}${cpugraph cpu1 20,170 104E8B ff0000 -t}
${GOTO 36}CPU 1: ${GOTO 80} ${cpu cpu2}%  ${GOTO 160}${freq_g 2} GHz
${GOTO 60}${cpugraph cpu2 20,170 104E8B ff0000 -t}
${GOTO 36}$hr
${GOTO 36}${font Ubuntu:bold:size=9}${color0}Memory${font}${color}
${GOTO 36}RAM: ${GOTO 120}$mem / $memmax
${GOTO 60}${membar 10,140} ${memperc}%
${GOTO 36}SWAP:${GOTO 120}${swapbar 10,80} ${swapperc}%
${GOTO 36}$hr
${GOTO 36}${font Ubuntu:bold:size=9}${color0}Disks${font}${color}
${GOTO 36}I/O read:${GOTO 90}${diskiograph_read 20,150 008e00 ffb200 -t}
${GOTO 36}${voffset -20}${diskio_read}
${GOTO 36}I/O write:${GOTO 90}${diskiograph_write 20,150 008e00 ffb200 -t}
${GOTO 36}${voffset -20}${diskio_write}

${GOTO 36}root (/):${GOTO 120}${fs_used /} / ${fs_size /}
${GOTO 36}${GOTO 60}${fs_bar 10,140 /} ${fs_used_perc /}%
${GOTO 36}Sistema:${GOTO 120}${fs_used /media/win7} / ${fs_size /media/win7}
${GOTO 36}${GOTO 60}${fs_bar 10,140 /media/win7} ${fs_used_perc /media/win7}%
${GOTO 36}Datos:${GOTO 120}${fs_used /media/datos} / ${fs_size /media/datos}
${GOTO 36}${GOTO 60}${fs_bar 10,140 /media/datos} ${fs_used_perc /media/datos}%
${GOTO 36}$hr
${GOTO 36}${font Ubuntu:bold:size=9}${color0}Network${font}${color}${if_gw}${GOTO 130}GW: ${gw_ip}${endif}
${if_up eth0}${GOTO 36}eth0:${GOTO 120}${addr eth0}
${GOTO 36}Up (${upspeedf eth0}):${GOTO 120}${upspeedgraph eth0 15,110 330099 cc0099 -t}
${GOTO 36}Down (${downspeedf eth0}):${GOTO 120}${downspeedgraph eth0 15,110 330099 cc0099 -t}${endif}
${if_up wlan0}${GOTO 36}wlan0:${GOTO 120}${addr wlan0}
${GOTO 60}$wireless_essid   $wireless_bitrate
${GOTO 60}${wireless_link_bar 10,140} $wireless_link_qual_perc %
${GOTO 36}Up (${upspeedf wlan0}):${GOTO 120}${upspeedgraph wlan0 15,110 330099 cc0099 -t}
${GOTO 36}Down (${downspeedf wlan0}):${GOTO 120}${downspeedgraph wlan0 15,110 330099 cc0099 -t}${endif}
${if_up ppp0}${GOTO 36}ppp0:${GOTO 120}${addr ppp0}
${GOTO 36}Up (${upspeedf ppp0}):${GOTO 120}${upspeedgraph ppp0 15,110 330099 cc0099 -t}
${GOTO 36}Down (${downspeedf ppp0}):${GOTO 120}${downspeedgraph ppp0 15,110 330099 cc0099 -t}
${GOTO 36}Total Up: ${totalup ppp0}  Total Down: ${totaldown ppp0}${endif}
${GOTO 36}$hr
${GOTO 36}${font Ubuntu:bold:size=9}${color0}Connections${font}${color}
${GOTO 36}sshd: ${tcp_portmon 22 22 count}${GOTO 120}portmap: ${tcp_portmon 111 111 count}
${GOTO 36}$hr
${GOTO 80}${font Ubuntu:bold:size=9}${color0}Temperatures${font}${color}
${GOTO 80}Core1:${GOTO 150}${hwmon 1 temp 1} ºC
${GOTO 80}Core2:${GOTO 150}${hwmon 2 temp 1} ºC
${GOTO 80}Hard disk:${GOTO 150}${hddtemp /dev/sda} ºC
```

---

### Post by TheeMahn2003 on 2012-01-07
I know this is an old thread, perhaps the info I provide will help someone else.

I am writing a conky builder, what it does is build a conky skelaton based on end users hardware.  Network detection / Active is no exception:
[[IMG]http://img36.imageshack.us/img36/5571/cbuilder.png[/IMG]](http://imageshack.us/photo/my-images/36/cbuilder.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

Code for network detection / active:
```
#Advance network detection to perfection scan all interfaces:
ls /sys/class/net/ > /tmp/ifaces.txt
if test -f /tmp/ifaces.txt
then
echo 'Network interfaces detected:'
echo '============================'
cat /tmp/ifaces.txt
echo '============================'
echo 'Scanning for active...'
cat /tmp/ifaces.txt | while read FILE
do
  target=$(echo "$FILE" | sed -e "s/ /_/")
  echo -n "Interface $FILE: "
  ACT=$(cat /sys/class/net/$FILE/operstate)
  echo $ACT
  if [[ $ACT == 'up' ]]; then
	ACTIVE=$FILE
	echo $FILE > /tmp/tmpo.txt
	echo 'Active Network: '$ACTIVE
  fi
done
else
echo 'No Active network.'
fi
if test -f /tmp/tmpo.txt
then
ACTIVE=$(cat /tmp/tmpo.txt)
else
ACTIVE='No Inet'
fi
echo -n 'Active Monitoring Connection: '
echo $ACTIVE
echo '============================'
if test -f /tmp/tmpo.txt
then
WIRELESS=$(cat /tmp/tmpo.txt|grep 'wlan')
fi
if [[ $WIRELESS != '' ]]
then
wlan='up'
fi

#Clean up.
if test -f /tmp/ifaces.txt
then
rm /tmp/ifaces.txt
fi
if test -f /tmp/tmpo.txt
then
rm /tmp/tmpo.txt
fi
```

If it detects wireless propagates access point, connection strength and throughput.

Fullcode as of 1.07:
```

#!/bin/bash
#written via TheeMahn
VERSION='1.07'
# Changelog:
# 1.0 - initial public release
# 1.1 - internal release
# 1.2 - internal release
# 1.3 - internal release
# 1.4 - Added distro detection, added resolution detection to set fonts and sizes.
# 1.05- Added version compliance for deb based releases
#       Added better networking detection / wireless support.
#       Added memory output to compare against pae based kernels.
#       Added 800 X 600 support, how did I miss this res?
#       Added initial support for Ultimate Player (dynamically)
#       Added support for all network interface detection / Active.
#	Never have I seen this implementation, I try to think outside of
#	the box please report issues.
#       Added support for Ultimate Edition 2.6.4 and 3.1 detection
#       Added dynamic Wireless support.
#	Added CPU Temp / Fan speeds also dynamic.
# 1.06- Added Radio tray to the mix
#	Initiated the anti-cron job mode of thinking, execi can be executed
#	w/o the need for a cron job.  Let's base this on the end users CPU.
#	Added no inet means do not propigate - includes wireless.
#	The same across the board when I am done and hopefully will not
#	require a cron job.
# 1.07	Initiated realtime information, across issues I have set forth.
#	Set CPU Temp to display info realtime based on end users processor. A
#	single core cpu will not be updated as fast as a quad for example
#	please see timeslices in my code.
#	Set fan speed accordingly as above.

#	Am I done?  No, dynamic screen resources then becomes an issue.  I am going
#	to take the information I / users view as important and make sure you recieve
#	that info until you run out of "screen resources".

#	I am going to try and explain.  I have a monitor that is 1920 X 1200 resolution
#	1200 is the number I am currently paying attention to.  1200 pixels is a ton of
#	info, however 800 X 600.  Well I guess half of what I can see.  The CPU once
#	again steps into the mix, typically go hand in hand.  The script is smart enough
#	to see the difference.  I do not want to rob your CPU of needed cycles,
#	if you do not know what I refer to please do not run it ;)

#	I have looked into generating weather reports as per your IP to resolve where you
#	live & have shyed away on the thought.  Proxy's etc. provide false reports.
#	Something I could fix?  Sure.  Conky builder, when I am done please understand.
#
#	Everything I do is in the best interests of the user & the Ultimate Edition
#	community. Do I care if ubuntu, mint, etc. picks it up? Nope, they will
# 	pay me in the end ;)  Progression, is my means.  Let's have a bash session:

echo "Ultimate Edition Conky builder version "$VERSION
echo "Please report errors / issues to TheeMahn <TheeMahn@ultimateedition.info>"
echo "========================================================================="
OS='Ultimate Edition'

#Detect codebase
CODEBASE=`cat /etc/lsb-release | grep 'DISTRIB_CODENAME=' | sed 's/DISTRIB_CODENAME=//g'`

echo "Codebase detected: "$CODEBASE

# detect if release is odd or even.
EVENODD=`dpkg -l | grep kubuntu-desktop`

   if [[ $EVENODD != "" ]]; then
  echo "Kubuntu base: detected - odd number release"
   else
  echo "Kubuntu base not detected - even number release"
   fi


echo -n "Distro detected: "
case "$CODEBASE" in
natty)
   if [[ $EVENODD != "" ]]; then
  OS=$OS" 3.1"
   else
  OS=$OS" 3.0"
   fi
   echo $OS ;;
maverick)
   if [[ $EVENODD != "" ]]; then
  OS=$OS" 2.9"
   else
  OS=$OS" 2.8"
   fi
   echo $OS ;;
lucid)
   if [[ $EVENODD != "" ]]; then
  OS=$OS" 2.7"
   else
  OS=$OS" 2.6.4"
   fi
   echo $OS ;;

*)  echo "Unknown O/S using $CODEBASE"
esac


# Attempt to advance the script.  No sense having the user edit this script if we can obtain the information.

res=`xrandr -q | grep 'current' | cut -d"," -f2 | sed 's/current//g' | sed 's/ //g'`

# set default in case user has an unknown resolution.
GRAPHWIDTH=320 #size of box in pixels
FONTSIZE=12

echo "Detected current resolution:" $res

case "$res" in
1920x1200)
   AHW=75
   AARTY=101
   GRAPHWIDTH=400
   FONTSIZE=14
   echo "Setting Font size to 14 and graph width to 480" ;;
1920X1080)
   AHW=75
   AARTY=101
   GRAPHWIDTH=400
   FONTSIZE=14
   echo "Setting Font size to 14 and graph width to 480" ;;
1680x1050)
   AHW=75
   AARTY=101
   GRAPHWIDTH=400
   FONTSIZE=14
   echo "Setting Font size to 14 and graph width to 480" ;;
1440x900)
   GRAPHWIDTH=310
   FONTSIZE=12
   echo "Setting Font size to 12 and graph width to 310" ;;
1400x1050)
   AHW=75
   AARTY=102
   GRAPHWIDTH=310
   FONTSIZE=14
   echo "Setting Font size to 12 and graph width to 280" ;;
1280x1024)
   AHW=75
   AARTY=104
   GRAPHWIDTH=310
   FONTSIZE=13
   echo "Setting Font size to 13 and graph width to 310" ;;
1280x960)
   GRAPHWIDTH=300
   FONTSIZE=12
   echo "Setting Font size to 12 and graph width to 300" ;;
1152x864)
   GRAPHWIDTH=240
   FONTSIZE=9
   echo "Setting Font size to 9 and graph width to 240" ;;
1024x768)
   AARTY=81
   AHW=65
   GRAPHWIDTH=240
   FONTSIZE=9
   echo "Setting Font size to 9 and graph width to 240" ;;
800x600)
   GRAPHWIDTH=220
   FONTSIZE=8
   echo "Setting Font size to 8 and graph width to 220" ;;
832x624)
   GRAPHWIDTH=220
   FONTSIZE=8
   echo "Setting Font size to 8 and graph width to 220" ;;
720x400)
   GRAPHWIDTH=180
   FONTSIZE=6
   echo "Setting Font size to 6 and graph width to 180" ;;
640x480)
   GRAPHWIDTH=180
   FONTSIZE=6
   echo "Setting Font size to 6 and graph width to 180" ;;
*) 
   GRAPHWIDTH=320
   FONTSIZE=12
   echo "Resolution unprogramed defaulting, please report detected resolution above to <theemahn@ultimateedition.info>" ;;
esac

#set Base, hilight color & header please adjust colors in hex and font to your liking
BASE='${color #ffffff}${font Liberation Liberation:style=normal:pixelsize='$FONTSIZE'}'
HILIGHT='${color #00ff00}${font Liberation Liberation:style=normal:pixelsize='$FONTSIZE'}'
HEADER='${color #aaaaaa}${font Liberation:style=Bold:pixelsize='$FONTSIZE'}'
BAR='${color #ffff00}'

############### You Should not have to edit anything below #############

#Calculate v offset based on Fonts / pixelsize
VOFF=$((FONTSIZE+6))
ALEFT=$((FONTSIZE/4))
INDENT=$((FONTSIZE/2))
BARZ=$((GRAPHWIDTH/2))
BOFFSET=$((FONTSIZE/3))
TICON=$((FONTSIZE/5))
BPER=$((GRAPHWIDTH/100*75))
SBAR=$((GRAPHWIDTH/100*20))
LOGO=$((FONTSIZE*4))
BPER=`expr $BPER - 10`
AARTX=`expr $GRAPHWIDTH - $AHW`

#Get CPU model
PROC=`cat /proc/cpuinfo | grep 'model name' | sed -e 's/.*: //' | uniq`
echo "Detected Processor:" $PROC

#check Architecture set 32 bit default
ARCHITECTURE='32 Bit'

#
# Check for x86_64 (Test 1) - some O/S's use the -i switch
#
if [ "`uname -i|grep x86_64`" == "x86_64" ]; then
   ARCHITECTURE='64 Bit'
fi

#
# Check for x86_64 (Test 2) - some OSs (ie. Gentoo) return Processor manufacturer
#rather than architecture with "uname -i"
#
if [ "`uname -a|grep x86_64`" != "" ]; then
   ARCHITECTURE='64 Bit'
fi


echo $ARCHITECTURE 'O/S detected.'

#Count number of processor cores
CORES=1
CORES=`cat /proc/cpuinfo | grep "processor" | wc -l`
TIMESLICES=`expr 12 / $CORES`
echo $CORES "Cpu core(s) Detected."
echo 'Update interval: '$TIMESLICES
cat /proc/meminfo | grep 'MemTotal'
#Advance network detection to perfection scan all interfaces:
ls /sys/class/net/ > /tmp/ifaces.txt
if test -f /tmp/ifaces.txt
then
echo 'Network interfaces detected:'
echo '============================'
cat /tmp/ifaces.txt
echo '============================'
echo 'Scanning for active...'
cat /tmp/ifaces.txt | while read FILE
do
  target=$(echo "$FILE" | sed -e "s/ /_/")
  echo -n "Interface $FILE: "
  ACT=$(cat /sys/class/net/$FILE/operstate)
  echo $ACT
  if [[ $ACT == 'up' ]]; then
	ACTIVE=$FILE
	echo $FILE > /tmp/tmpo.txt
	echo 'Active Network: '$ACTIVE
  fi
done
else
echo 'No Active network.'
fi
if test -f /tmp/tmpo.txt
then
ACTIVE=$(cat /tmp/tmpo.txt)
else
ACTIVE='No Inet'
fi
echo -n 'Active Monitoring Connection: '
echo $ACTIVE
echo '============================'
if test -f /tmp/tmpo.txt
then
WIRELESS=$(cat /tmp/tmpo.txt|grep 'wlan')
fi
if [[ $WIRELESS != '' ]]
then
wlan='up'
fi

#Clean up.
if test -f /tmp/ifaces.txt
then
rm /tmp/ifaces.txt
fi
if test -f /tmp/tmpo.txt
then
rm /tmp/tmpo.txt
fi
#Detect "Active" network and propigate Network Xfer bar
#ACTIVE=`ifconfig | grep -B 1 inet | head -1 | awk '{print $1}'`
#Wireless?
#wlan=$(cat /sys/class/net/wlan0/operstate)
#enet=$(cat /sys/class/net/eth0/operstate)

#Hardline?
#if [[ $enet == 'up' ]]; then
#$ACTIVE='eth0'
#fi

#Wireless
#if [[ $wlan == 'up' ]]; then
#ACTIVE='wlan0'
#fi

#Create conky skelaton
echo '#Use XFT?
use_xft yes
xftfont Liberation Sans:size=10
xftalpha 0.8
text_buffer_size 2048

# Update interval in seconds
update_interval 1

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_type override
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area -adjust if you would like to user smaller fonts etc.
minimum_size '$GRAPHWIDTH' 0
maximum_width '$GRAPHWIDTH'
max_specials 1024

# Draw shades?
draw_shades no
default_color 00ff00 #000000
# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border width
border_width 1

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 15
gap_y 45

# -- Lua Load -- #
lua_load ~/.draw_bg.lua
lua_draw_hook_pre draw_bg

' > ~/.conkyrc

echo 'TEXT
${goto '$INDENT'}${image /usr/share/ultimate_edition/logo.png -p '$BARZ','$LOGO' -s 32x32}'$HEADER'SYSTEM ${hr 2 }
'$HILIGHT'${alignr}'$OS' - $alignr$kernel '$ARCHITECTURE'
'$HILIGHT'${alignr}'$USER'@$nodename
'$BASE'${goto '$INDENT'}${voffset '$TICON'}${font StyleBats:pixelsize='$FONTSIZE'}k${font}${voffset -'$ALEFT'}${goto '$VOFF'}'$BASE'Processes: ${alignr}'$HILIGHT'$processes ($running_processes running)
'$BASE'${goto '$INDENT'}${voffset '$TICON'}${font StyleBats:pixelsize='$FONTSIZE'}q${font}${voffset -'$ALEFT'}${goto '$VOFF'}'$BASE'Uptime: '$HILIGHT'${alignr}${uptime}' >> ~/.conkyrc
#Jamming?
echo 'Jamming Check:'
echo '=============='
#Ultimate Player Cranking?
JCHK=`qdbus | grep 'org.mpris.clementine'`
if [[ $JCHK != '' ]]
then
UPLAYER=`qdbus org.mpris.MediaPlayer2.clementine /Player GetMetadata`
fi
if [[ $UPLAYER == '' ]]; then
echo 'Ultimate Player Running: No'
else 
echo 'Ultimate Player Running: Yes'
ARTIST=$(echo $UPLAYER | grep "artist" | cut -c9- | cut -d: -f1 | sed 's/arturl//')
ARTIST=`qdbus org.mpris.MediaPlayer2.clementine /Player GetMetadata | grep artist | cut -c9-`
TITLE=$(echo $UPLAYER | grep title | cut -d: -f10 | sed 's/ //1')
TITLE=`qdbus org.mpris.MediaPlayer2.clementine /Player GetMetadata | grep title | cut -c8-`
cover="$(qdbus org.mpris.MediaPlayer2.clementine /Player GetMetadata | grep arturl)"
ART=$(echo $UPLAYER | grep "arturl" | cut -d: -f4 | sed 's/ audio-bitrate//g' | sed "s/\/\///1")
ART=$(echo $cover | cut -c16- | sed "s/%20/\\\ /g")


#ART=$cover
#echo $BASE'${voffset 2}${font VariShapes Solid:pixelsize='$FONTSIZE'}q${font}${goto '$VOFF'}${voffset -'$ALEFT'}${font}'$BASE'Artist: '$HILIGHT'${alignr}'$ARTIST >> ~/.conkyrc
#echo ${goto '$INDENT'}${image '$ART' '$BARZ','$LOGO' -s 32x32}'$HEADER'SYSTEM ${hr 2 }' >> ~/.conkyrc
echo '${goto '$INDENT'}${image /usr/share/ultimate_edition/logo.png -p '$BARZ','$LOGO' -s 32x32}'$HEADER'ULTIMATE PLAYER ${hr 2 }' >> ~/.conkyrc
echo $BASE'${voffset 2}${font Poky:pixelsize='$FONTSIZE'}k${font}${goto '$VOFF'}${voffset -'$ALEFT'}${font}'$BASE'Playing: '$HILIGHT $ARTIST' - '$TITLE'

' >> ~/.conkyrc
echo 'Artist: '$ARTIST
echo 'Title: '$TITLE
echo 'Album art: '$ART
echo '${goto 7}${image '$ART' -p '$AARTX','$AARTY' -s '$AHW'x'$AHW}'' >> ~/.conkyrc
fi
JCHK=''
JCHK=`qdbus | grep 'net.sourceforge.radiotray'`
if [[ $JCHK != '' ]]
then
RPLAYER=`qdbus net.sourceforge.radiotray /net/sourceforge/radiotray getCurrentMetaData`
STATION=`qdbus net.sourceforge.radiotray /net/sourceforge/radiotray net.sourceforge.radiotray.getCurrentRadio`
fi
if [[ $RPLAYER == '' ]]; then
echo 'Radio Tray Running: No'
else 
echo 'Radio Tray Running: Yes'
echo 'Artist - Song: '$RPLAYER
echo $HEADER'RADIO TRAY ${hr 2 }' >> ~/.conkyrc
echo $BASE'${voffset 2}${font Poky:pixelsize='$FONTSIZE'}k${font}${goto '$VOFF'}${voffset -'$ALEFT'}${font}'$BASE'Playing: '$HILIGHT $RPLAYER >> ~/.conkyrc
echo $BASE'${font StyleBats:pixelsize='$FONTSIZE'}q${font}${voffset -'$ALEFT'}${goto '$VOFF'}${voffset -'$ALEFT'}${font}'$BASE'Station: '$HILIGHT $STATION >> ~/.conkyrc
fi


#Core(s) info
echo $HILIGHT'${goto '$INDENT'}${voffset '$TICON'}${font Stylebats:pixelsize='$FONTSIZE'}A${font}${voffset -'$ALEFT'}${goto '$VOFF'}'$HEADER'${goto '$VOFF'}CPU${hr 1 }
'$HILIGHT$PROC'
${goto '$INDENT'}${font StyleBats:pixelsize='$FONTSIZE'}A${font}${voffset -'$ALEFT'}${goto '$VOFF'}'$BASE'CPU Usage: '$HILIGHT' ${freq}MHz X '$CORES'${alignr}${cpu cpu0}% '$BAR' ${cpubar cpu0 '$INDENT','$SBAR'}' >> ~/.conkyrc
CPUTEMP=$(sensors -f |grep 'CPU Temp' |awk '{print $3}'|cut -b2,3,4,4)
if [[ $CPUTEMP != '' ]]
then
echo -n '${goto '$INDENT'}${font StyleBats:pixelsize='$FONTSIZE'}A${font}${voffset -'$ALEFT'}${goto '$VOFF'}'$BASE'CPU Temp: '$HILIGHT >> ~/.conkyrc
echo -n '${execi '$TIMESLICES' sensors -f|grep "CPU Temperature"|cut -d: -f2|sed "s/ //g"|sed "s/+//g" | cut -d"(" -f1}' >> ~/.conkyrc
#echo -n '${goto '$INDENT'}${font StyleBats:pixelsize='$FONTSIZE'}A${font}${voffset -'$ALEFT'}${goto '$VOFF'}'$BASE'CPU Fan Speed: '$HILIGHT >> ~/.conkyrc
#echo '${execi '$TIMESLICES' sensors -f |grep "CPU Fan Speed" |awk '{print $4}'RPM' >> ~/.conkyrc
echo -n $BASE'${alignr}Fan Speed: '$HILIGHT >> ~/.conkyrc
echo '${execi '$TIMESLICES' sensors -f|grep "CPU Fan Speed"|cut -d: -f2|sed "s/ //g"|sed "s/+//g" | cut -d"(" -f1}' >> ~/.conkyrc
#echo '${execi '$TIMESLICES' sensors -f |grep "CPU Fan Speed" |awk "'"{print '$4'}"'"RPM' >> ~/.conkyrc
echo 'CPU Temp detected as: '$CPUTEMP
else
echo 'CPU Temp not detected / reported.'
fi
echo $BASE'Cores: ${hr 1 }' >> ~/.conkyrc

#Create a cpubar for each core
COUNTER=0
 while [  $COUNTER != $CORES ]; do
  let COUNTER=COUNTER+1
  echo '${goto '$INDENT'}${voffset '$TICON'}${font StyleBats:pixelsize='$FONTSIZE'}A${font}${voffset -'$ALEFT'}${goto '$VOFF'}'$BASE'Core '$COUNTER':' $HILIGHT'${cpu cpu'$COUNTER'}% '$BAR'${alignr}${cpubar cpu'$COUNTER' '$INDENT','$BPER'}'$BASE >> ~/.conkyrc
 done

#Output disk I/O bar top processes memory useage etc.
echo $HILIGHT'${goto '$INDENT'}${voffset '$TICON'}${font Stylebats:pixelsize='$FONTSIZE'}g${font}${voffset -'$ALEFT'}${goto '$VOFF'}'$HEADER'${goto '$VOFF'}RAM${hr 1 }'$BASE'
'$BASE'${voffset 2}${font VariShapes Solid:pixelsize='$FONTSIZE'}N'$BASE'Useage: '$HILIGHT'$mem / $memmax ${alignr}'$HILIGHT'$memperc% '$BAR'${membar '$INDENT','$SBAR'}'$BASE'
'$BASE'${goto '$INDENT'}${voffset '$TICON'}${font Stylebats:pixelsize='$FONTSIZE'}j${font}${voffset -'$ALEFT'}${goto '$VOFF'}'$BASE'Swap: '$HILIGHT'$swap/$swapmax${alignr}$swapperc% '$BAR'${swapbar '$INDENT','$SBAR'}
'$BASE'${goto '$INDENT'}${voffset '$TICON'}${font Poky:pixelsize='$FONTSIZE'}a${font}${voffset -'$ALEFT'}${goto '$VOFF'}'$BASE'${goto '$VOFF'}Highest: ${alignr}CPU     RAM
${goto '$VOFF'}${voffset -5.5}${hr 1}
'$HILIGHT'${voffset -1}${goto '$VOFF'}${top name 1}${alignr}${top cpu 1}  ${top mem 1}
${goto '$VOFF'}${top name 2}${alignr}${top cpu 2}  ${top mem 2}
${goto '$VOFF'}${top name 3}${alignr}${top cpu 3}  ${top mem 3}
${goto '$VOFF'}${top name 4}${alignr}${top cpu 4}  ${top mem 4}
'$HILIGHT'${goto '$INDENT'}${voffset '$TICON'}${font Poky:pixelsize='$FONTSIZE'}H${font}${voffset -'$ALEFT'}${goto '$VOFF'}'$HEADER'${goto '$VOFF'}FILESYSTEM${hr 1 }'$BASE'
'$BASE'${goto '$INDENT'}${voffset '$TICON'}${font Poky:pixelsize='$FONTSIZE'}Y${font}${voffset -'$ALEFT'}${goto '$VOFF'}'$BASE'Disk I/O: '$HILIGHT'${diskio}${alignr}'$BAR'${diskiograph 20,'$BARZ'}
'$BASE'${goto '$INDENT'}${voffset '$TICON'}${font Poky:pixelsize='$FONTSIZE'}H${font}${voffset -'$ALEFT'}${goto '$VOFF'}'$BASE'Root: '$HILIGHT'${fs_free /} / ${fs_size /}${alignr}${fs_used_perc /}% '$BAR'${fs_bar '$INDENT','$SBAR' /}'$BASE >> ~/.conkyrc

#Detect hard disks & create a bar for each mount point
echo "====================================="
echo "Internal / External storage detected:"
echo "====================================="
echo "/ - Root"
ls /media/ > /tmp/tmp.txt
cat /tmp/tmp.txt | while read FILE
do
target=$(echo "$FILE" | sed -e "s/ /_/")
echo ''$BASE'${goto '$INDENT'}${voffset '$TICON'}${font Poky:pixelsize='$FONTSIZE'}H${font}${voffset -'$ALEFT'}${goto '$VOFF'}'$BASE$FILE': '$HILIGHT'${fs_free /media/'$FILE'} / ${fs_size /media/'$FILE'}${alignr}${fs_used_perc /media/'$FILE'}% '$BAR'${fs_bar '$INDENT','$SBAR' /media/'$FILE'}'$BASE >> ~/.conkyrc
echo $FILE
done
rm /tmp/tmp.txt
if [[ $ACTIVE != 'No Inet' ]]
then
echo $HILIGHT'${goto '$INDENT'}${voffset '$TICON'}${font Stylebats:pixelsize='$FONTSIZE'}5${font}${voffset -'$ALEFT'}${goto '$VOFF'}'$HEADER'${goto '$VOFF'}ACTIVE NETWORK: '$ACTIVE'${hr 1}' >> ~/.conkyrc


#Propigate networking information based on active connection
echo $BASE'${voffset 2}${font VariShapes Solid:pixelsize='$FONTSIZE'}q${font}${goto '$VOFF'}${voffset -'$ALEFT'}${font}'$BASE'Up: ${upspeed '$ACTIVE'} '$BAR'${alignr}${upspeedgraph '$ACTIVE' 20,'$BARZ' '$BASE' '$BAR' }
'$BASE'${voffset -24}${goto '$VOFF'}Total: ${totalup '$ACTIVE'}
${voffset -'$ALEFT'}${font VariShapes Solid:pixelsize='$FONTSIZE'}Q${font}${goto '$VOFF'}${voffset -'$ALEFT'}'$BASE'Down: ${downspeed '$ACTIVE'}${font} '$BAR'${alignr}${downspeedgraph '$ACTIVE' 20,'$BARZ' '$BASE' '$BAR'}
'$BASE'${voffset -24}${goto '$VOFF'}Total: ${totaldown '$ACTIVE'}' >> ~/.conkyrc

#Provide wireless info if user is using wireless actively.
if [[ $wlan == 'up' ]]; then
#Wireless header
echo $BASE'Wireless: ${hr 1 }' >> ~/.conkyrc
#ACCESS POINT
echo $BASE'${voffset 2}${font VariShapes Solid:pixelsize='$FONTSIZE'}-${font}${goto '$VOFF'}${voffset -'$ALEFT'}${font}'$BASE'Wireless Access Point: '$HILIGHT'${alignr}${wireless_essid '$ACTIVE'}' >> ~/.conkyrc
#Connection strength / signal
echo $BASE'${voffset 2}${font Stylebats:pixelsize='$FONTSIZE'}Z${font}${goto '$VOFF'}${voffset -'$ALEFT'}${font}'$BASE'Connection strength: '$HILIGHT'${alignr}${wireless_link_qual_perc '$ACTIVE'}%' >> ~/.conkyrc
#Connection speed
echo $BASE'${voffset 2}${font Stylebats:pixelsize='$FONTSIZE'}C${font}${goto '$VOFF'}${voffset -'$ALEFT'}${font}'$BASE'Connection max throughput: '$HILIGHT'${alignr}${wireless_bitrate '$ACTIVE'}' >> ~/.conkyrc
fi

echo $HEADER'${voffset -'$ALEFT'}${hr 2}' >> ~/.conkyrc

# Provide general connection info
echo $BASE'${voffset -'$ALEFT'}${font Poky:pixelsize='$FONTSIZE'}w${font}${goto '$VOFF'}${voffset -'$ALEFT'}'$BASE'Local IP: '$HILIGHT'${alignr}${addr '$ACTIVE'}' >> ~/.conkyrc
echo $BASE'${voffset 2}${font Stylebats:pixelsize='$FONTSIZE'}M'$BASE'TCP Connections: '$HILIGHT'${tcp_portmon 1 65535 count}' >> ~/.conkyrc
fi
#close out with a thin line at the bottom
echo $HEADER'${voffset -'$ALEFT'}${hr 2}
'$HILIGHT'${goto '$INDENT'}${voffset '$TICON'}${font Poky:pixelsize='$FONTSIZE'}d${font}${voffset -'$ALEFT'}${goto '$VOFF'}'$HEADER'${goto '$VOFF'}${alignc}${time %H:%M}, ${time %A %d %B}' >> ~/.conkyrc
echo $HEADER'${voffset -'$ALEFT'}${hr 2}' >> ~/.conkyrc
echo $HEADER'${voffset -'$ALEFT'}${hr 2}' >> ~/.conkyrc

```

---

