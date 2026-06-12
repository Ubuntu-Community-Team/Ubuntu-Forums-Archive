---
title: "Help wanted with Conky on Elementary OS"
date: 2017-05-21
forum: Ubuntu/Debian BASED
---

### Post by LastDino on 2017-05-21
Need some help guys, I'm starting to have a headache and no real success ~.~

I've eOs + Variety (with rotating wise quotes and wallpapers) setuped

Now, I want to add few elements to the conky setup that I liked and also doesn't have problem with these settings

Here is the file

```

background yes
double_buffer yes

alignment top_left

border_width 1
cpu_avg_samples 2
default_color white
default_outline_color white
default_shade_color white
draw_borders no
draw_graph_borders yes
draw_outline no
draw_shades no

gap_x 0
gap_y 50
net_avg_samples 2
no_buffers yes
out_to_console no
out_to_stderr no
extra_newline no

own_window yes
own_window_type normal
own_window_transparent yes
own_window_colour 000000
own_window_argb_visual yes
own_window_argb_value 0
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

minimum_size 170 0
stippled_borders 0
update_interval 2.0
uppercase no
use_spacer none

show_graph_scale no
show_graph_range no

use_xft yes
xftalpha 0.1
xftfont Droid Sans:size=10
color0 white
color1 EAEAEA
color2 FFA300
color3 grey

TEXT
${color2}CPU ${color0}${alignr}${cpu cpu0}%
${cpubar cpu0 5,}
${top name 1} $alignr ${top cpu 1}%
${top name 2} $alignr ${top cpu 2}%
${top name 3} $alignr ${top cpu 3}%
${top name 4} $alignr ${top cpu 4}%
${top name 5} $alignr ${top cpu 5}%

${color2}RAM ${color0}${alignr}${mem}
${membar 5,}
${top_mem name 1} $alignr ${top_mem mem_res 1}
${top_mem name 2} $alignr ${top_mem mem_res 2}
${top_mem name 3} $alignr ${top_mem mem_res 3}
${top_mem name 4} $alignr ${top_mem mem_res 4}
${top_mem name 5} $alignr ${top_mem mem_res 5}


```

Now, I wan to add few elements to this like: Swap usage along with RAM, Network DL/UP speed and total DL and UP over given period (or uptime) & IP info of system, number of processes being run below the process coloumn, H/W temperature and weather forecast

Please help, I've tried lot of codes and setting already and haven't managed to get it function properly <.<

At least point me to tutorials as to where these changes can be done from..[ATTACH=CONFIG]275200[/ATTACH]

---

### Post by again? on 2017-05-21
How much do you need help with?
Do you understand conky configs at all.

I've attached a standard conky config which has most of the elements you want.
It also contains the fonts used. Place fonts in ~/.fonts
After extracting the archive, show hidden files to reveal the .conkyrc.

You can run that config with **conky -c /path/to/config**
May need to change the network interface.
I have a wired network. Search for "enp3s0" and change for your device.

"man conky" explains the config settings and variables.

---

### Post by again? on 2017-05-21
Here is an example using your config and adding swap and a network section from the config I attached previously.
```
background yes
double_buffer yes

alignment top_left

border_width 1
cpu_avg_samples 2
default_color white
default_outline_color white
default_shade_color white
draw_borders no
draw_graph_borders yes
draw_outline no
draw_shades no

gap_x 0
gap_y 50
net_avg_samples 2
no_buffers yes
out_to_console no
out_to_stderr no
extra_newline no

own_window yes
own_window_type normal
own_window_transparent yes
own_window_colour 000000
own_window_argb_visual yes
own_window_argb_value 0
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

minimum_size 170 0
maximum_width 170
stippled_borders 0
update_interval 2.0
uppercase no
use_spacer none

show_graph_scale no
show_graph_range no

use_xft yes
xftalpha 0.1
xftfont Droid Sans:size=10
color0 white
color1 EAEAEA
color2 FFA300
color3 grey

TEXT
${color2}CPU ${color0}${alignr}${cpu cpu0}%
${cpubar cpu0 5,}
${top name 1} $alignr ${top cpu 1}%
${top name 2} $alignr ${top cpu 2}%
${top name 3} $alignr ${top cpu 3}%
${top name 4} $alignr ${top cpu 4}%
${top name 5} $alignr ${top cpu 5}%

${color2}RAM ${color0}${alignr}${mem}
${membar 5,}
${top_mem name 1} $alignr ${top_mem mem_res 1}
${top_mem name 2} $alignr ${top_mem mem_res 2}
${top_mem name 3} $alignr ${top_mem mem_res 3}
${top_mem name 4} $alignr ${top_mem mem_res 4}
${top_mem name 5} $alignr ${top_mem mem_res 5}

${color2}SWAP ${color0}${alignr}${swap}
${swapbar 5,}

${color2}NETWORK ${color0}${alignr}${execi 3600 curl -s --retry 3 icanhazip.com}
${voffset}${font VariShapes Solid:size=14}q${font}${goto 32}${voffset -6}Up: ${upspeed enp3s0}${font} ${alignr}${upspeedgraph enp3s0 8,60 F57900 FCAF3E}
${goto 32}Total: ${totalup enp3s0}
${voffset -2}${font VariShapes Solid:size=14}Q${font}${goto 32}${voffset -6}Down: ${downspeed enp3s0}${font} ${alignr}${downspeedgraph enp3s0 8,60 F57900 FCAF3E}
${goto 32}Total: ${totaldown enp3s0}


```

---

### Post by LastDino on 2017-05-21
Okay, you're amazing, solved half of my problems.

1) Now, I've no reading from the network, I'm assuming it is because I'm using Wireless (WiFi), what settings need to be changed?

2) I've managed to gather conkeyrc files for 3 different instances with different functions, I want them to run at the same time to make one theme complete. I could do this from Conky manager, but is there more cleaner way?

3) I also need to add weather and temperature info to the conkey you modified, could you show me how to in the file you modified? 
I ran your config (not one you made with mine), it gave me error saying /dev/sda access permission denied.
I wonder why that is, but probably one of the functions needs root accesses and since I simply ran the sh file it is considering it to be "threat" and denying access(?) <that is just me thinking loud

Sorry if I'm not very clear, but today things have been little hectic for me >.>

Here is where I'm atm

Let me install conky manager too to show those different conkeys, I'll post them in some time

right now I'm here[ATTACH=CONFIG]275211[/ATTACH]

---

### Post by #&amp;thj^% on 2017-05-21
I use this to find the name that some conky's will use.
```
$ ls /sys/class/net
enp4s0  lo  tun0  wlp3s0



```
I'm on a VPN now so I use the "tun0" in my .conkyrc
The wlp3s0 is my wireless device.
Hope that makes sense.

---

### Post by LastDino on 2017-05-21
> **1fallen said:**
> I use this to find the name that some conky's will use.
```
$ ls /sys/class/net
enp4s0  lo  tun0  wlp3s0



```
I'm on a VPN now so I use the "tun0" in my .conkyrc
The wlp3s0 is my wireless device.
Hope that makes sense.

Yes, yes, it did. I replaced enp3s0 with wlp9s0 as that seems to be my wireless. And boom! It is getting readings..

Thanks, 2 more problems left :D

This is where I'm at atm

[ATTACH=CONFIG]275214[/ATTACH]

---

### Post by #&amp;thj^% on 2017-05-21
I can only see one problem...The pre_exec showing can be solved with editing the conkyrc file and removing the "pre_" portion. For example "pre_exec" to "exec" if you have any other problems show them again and I will do my best to help.

---

### Post by again? on 2017-05-21
> **LastDino said:**
> Okay, you're amazing, solved half of my problems.

1) Now, I've no reading from the network, I'm assuming it is because I'm using Wireless (WiFi), what settings need to be changed?

2) I've managed to gather conkeyrc files for 3 different instances with different functions, I want them to run at the same time to make one theme complete. I could do this from Conky manager, but is there more cleaner way?

3) I also need to add weather and temperature info to the conkey you modified, could you show me how to in the file you modified? 
I ran your config (not one you made with mine), it gave me error saying /dev/sda access permission denied.
I wonder why that is, but probably one of the functions needs root accesses and since I simply ran the sh file it is considering it to be "threat" and denying access(?) <that is just me thinking loud

Sorry if I'm not very clear, but today things have been little hectic for me >.>

Here is where I'm atm

Let me install conky manager too to show those different conkeys, I'll post them in some time

right now I'm here[ATTACH=CONFIG]275211[/ATTACH]

**1)** Try this config which has settings for whatever network connection is up.
```
background no
double_buffer yes

alignment top_left

border_width 1
cpu_avg_samples 2
default_color white
default_outline_color white
default_shade_color white
draw_borders no
draw_graph_borders yes
draw_outline no
draw_shades no

gap_x 0
gap_y 50
net_avg_samples 2
no_buffers yes
out_to_console no
out_to_stderr no
extra_newline no

own_window yes
own_window_type normal
own_window_transparent yes
own_window_colour 000000
own_window_argb_visual yes
own_window_argb_value 0
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

minimum_size 170 500
maximum_width 170
stippled_borders 0
update_interval 2.0
uppercase no
use_spacer none

show_graph_scale no
show_graph_range no

use_xft yes
xftalpha 0.1
xftfont Droid Sans:size=10
color0 white
color1 EAEAEA
color2 FFA300
color3 grey

TEXT
${color2}CPU ${color0}${alignr}${cpu cpu0}%
${cpubar cpu0 5,}
${top name 1} $alignr ${top cpu 1}%
${top name 2} $alignr ${top cpu 2}%
${top name 3} $alignr ${top cpu 3}%
${top name 4} $alignr ${top cpu 4}%
${top name 5} $alignr ${top cpu 5}%

${color2}RAM ${color0}${alignr}${mem}
${membar 5,}
${top_mem name 1} $alignr ${top_mem mem_res 1}
${top_mem name 2} $alignr ${top_mem mem_res 2}
${top_mem name 3} $alignr ${top_mem mem_res 3}
${top_mem name 4} $alignr ${top_mem mem_res 4}
${top_mem name 5} $alignr ${top_mem mem_res 5}

${color2}SWAP ${color0}${alignr}${swap}
${swapbar 5,}

${color2}NETWORK ${color0}${alignr}${execi 3600 curl -s --retry 3 icanhazip.com}
${if_up wlan0}
${font Poky:size=14}Y${font}${goto 32}${voffset -8}SSID: ${wireless_essid wlan0}
${goto 32}Signal: ${wireless_link_qual wlan0}% ${alignr}${wireless_link_bar 8,60 wlan0}
${voffset 4}${font VariShapes Solid:size=14}q${font}${goto 32}${voffset -6}Up: ${upspeed wlan0}${font} ${alignr}${upspeedgraph wlan0 8,60 F57900 FCAF3E}
${goto 32}Total: ${totalup wlan0}
${voffset 4}${font VariShapes Solid:size=14}Q${font}${goto 32}${voffset -6}Down: ${downspeed wlan0}${font} ${alignr}${downspeedgraph wlan0 8,60 F57900 FCAF3E}
${goto 32}Total: ${totaldown wlan0}
${voffset 4}${font Poky:size=13}w${font}${goto 32}${voffset -8}Local IP: ${alignr}${addr wlan0}
${goto 32}Public IP: ${alignr}${execi 3600 curl -s --retry 3 icanhazip.com}
# |--eth0
${else}${if_up eth0}
${voffset -13}${font VariShapes Solid:size=14}q${font}${goto 32}${voffset -6}Up: ${upspeed eth0}${font} ${alignr}${upspeedgraph eth0 8,60 F57900 FCAF3E}
${goto 32}Total: ${totalup eth0}
${voffset -2}${font VariShapes Solid:size=14}Q${font}${goto 32}${voffset -6}Down: ${downspeed eth0}${font} ${alignr}${downspeedgraph eth0 8,60 F57900 FCAF3E}
${goto 32}Total: ${totaldown eth0}
${voffset -2}${font Poky:size=13}w${font}${goto 32}${voffset -4}Local IP: ${alignr}${addr eth0}
${goto 32}Public IP: ${alignr}${execi 3600 curl -s --retry 3 icanhazip.com}
# |--PPP0
${endif}${else}${if_up ppp0}
${voffset -13}${font VariShapes Solid:size=14}q${font}${goto 32}${voffset -6}Up: ${upspeed ppp0}${font} ${alignr}${upspeedgraph ppp0 8,60 F57900 FCAF3E}
${goto 32}Total: ${totalup ppp0}
${voffset -2}${font VariShapes Solid:size=14}Q${font}${goto 32}${voffset -6}Down: ${downspeed ppp0}${font} ${alignr}${downspeedgraph ppp0 8,60 F57900 FCAF3E}
${goto 32}Total: ${totaldown ppp0}
${voffset -2}${font Poky:size=13}w${font}${goto 32}${voffset -4}Local IP: ${alignr}${addr ppp0}
${endif}${else}${voffset 4}${font PizzaDude Bullets:size=12}4${font}${goto 32}Network Unavailable${endif}${endif}
${hr 2}
```
Just use the command 1fallen gave you to replace wlan0 with your wifi device.
eth0 can be replaced with a wired device if you have or just leave as is.
[ATTACH=CONFIG]275215[/ATTACH]

**2)** Conky manager is just some scripts to start and stop various conky configs.
To run one conky config, you save a config as .conkyrc in your home directory and just use "conky" to start.
To run 2 or more configs use the **-c** option to specify a config.
```
conky -c */path/to/config*
```
give your configs names like sysinfo.conkyrc and weather.conkyrc.
I keep all my configs in ~/conky/configs
You can use a bash script in autostart.
My start script
```
#!/bin/bash

# click to start, click to stop
sleep 5

if pidof conky | grep [0-9] > /dev/null
then
   killall conky 
else
   
conky -c /home/glen/conky/configs/gnome-panel.conkyrc &
conky -c /home/glen/conky/configs/weather-waters-gnome.conkyrc &  

fi
exit 0
```
The script can also be used to toggle the conkys on/off

**3)** How much weather info do you want?
Do you want a separate weather conky?
For temperatures you need to install hddtemp and sensors.
hddtemp needs to be configured for access without root.
sensors also needs to be configured.
See [**[COLOR="#FF0000"]HERE[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=281865&p=12700126&viewfull=1#post12700126")

---

### Post by again? on 2017-05-21
> **1fallen said:**
> I can only see one problem...The pre_exec showing can be solved with editing the conkyrc file and removing the "pre_" portion. For example "pre_exec" to "exec" if you have any other problems show them again and I will do my best to help.
Yes pre_exec no longer works.
pre_exec was used for info that only needed to be ran once at startup.
Replace with execi and a long interval like **execi 3600**

---

### Post by #&amp;thj^% on 2017-05-21
> **guber2 said:**
> **1)** Try this config which has settings for whatever network connection is up.
```
background no
double_buffer yes

alignment top_left

border_width 1
cpu_avg_samples 2
default_color white
default_outline_color white
default_shade_color white
draw_borders no
draw_graph_borders yes
draw_outline no
draw_shades no

gap_x 0
gap_y 50
net_avg_samples 2
no_buffers yes
out_to_console no
out_to_stderr no
extra_newline no

own_window yes
own_window_type normal
own_window_transparent yes
own_window_colour 000000
own_window_argb_visual yes
own_window_argb_value 0
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

minimum_size 170 500
maximum_width 170
stippled_borders 0
update_interval 2.0
uppercase no
use_spacer none

show_graph_scale no
show_graph_range no

use_xft yes
xftalpha 0.1
xftfont Droid Sans:size=10
color0 white
color1 EAEAEA
color2 FFA300
color3 grey

TEXT
${color2}CPU ${color0}${alignr}${cpu cpu0}%
${cpubar cpu0 5,}
${top name 1} $alignr ${top cpu 1}%
${top name 2} $alignr ${top cpu 2}%
${top name 3} $alignr ${top cpu 3}%
${top name 4} $alignr ${top cpu 4}%
${top name 5} $alignr ${top cpu 5}%

${color2}RAM ${color0}${alignr}${mem}
${membar 5,}
${top_mem name 1} $alignr ${top_mem mem_res 1}
${top_mem name 2} $alignr ${top_mem mem_res 2}
${top_mem name 3} $alignr ${top_mem mem_res 3}
${top_mem name 4} $alignr ${top_mem mem_res 4}
${top_mem name 5} $alignr ${top_mem mem_res 5}

${color2}SWAP ${color0}${alignr}${swap}
${swapbar 5,}

${color2}NETWORK ${color0}${alignr}${execi 3600 curl -s --retry 3 icanhazip.com}
${if_up wlan0}
${font Poky:size=14}Y${font}${goto 32}${voffset -8}SSID: ${wireless_essid wlan0}
${goto 32}Signal: ${wireless_link_qual wlan0}% ${alignr}${wireless_link_bar 8,60 wlan0}
${voffset 4}${font VariShapes Solid:size=14}q${font}${goto 32}${voffset -6}Up: ${upspeed wlan0}${font} ${alignr}${upspeedgraph wlan0 8,60 F57900 FCAF3E}
${goto 32}Total: ${totalup wlan0}
${voffset 4}${font VariShapes Solid:size=14}Q${font}${goto 32}${voffset -6}Down: ${downspeed wlan0}${font} ${alignr}${downspeedgraph wlan0 8,60 F57900 FCAF3E}
${goto 32}Total: ${totaldown wlan0}
${voffset 4}${font Poky:size=13}w${font}${goto 32}${voffset -8}Local IP: ${alignr}${addr wlan0}
${goto 32}Public IP: ${alignr}${execi 3600 curl -s --retry 3 icanhazip.com}
# |--eth0
${else}${if_up eth0}
${voffset -13}${font VariShapes Solid:size=14}q${font}${goto 32}${voffset -6}Up: ${upspeed eth0}${font} ${alignr}${upspeedgraph eth0 8,60 F57900 FCAF3E}
${goto 32}Total: ${totalup eth0}
${voffset -2}${font VariShapes Solid:size=14}Q${font}${goto 32}${voffset -6}Down: ${downspeed eth0}${font} ${alignr}${downspeedgraph eth0 8,60 F57900 FCAF3E}
${goto 32}Total: ${totaldown eth0}
${voffset -2}${font Poky:size=13}w${font}${goto 32}${voffset -4}Local IP: ${alignr}${addr eth0}
${goto 32}Public IP: ${alignr}${execi 3600 curl -s --retry 3 icanhazip.com}
# |--PPP0
${endif}${else}${if_up ppp0}
${voffset -13}${font VariShapes Solid:size=14}q${font}${goto 32}${voffset -6}Up: ${upspeed ppp0}${font} ${alignr}${upspeedgraph ppp0 8,60 F57900 FCAF3E}
${goto 32}Total: ${totalup ppp0}
${voffset -2}${font VariShapes Solid:size=14}Q${font}${goto 32}${voffset -6}Down: ${downspeed ppp0}${font} ${alignr}${downspeedgraph ppp0 8,60 F57900 FCAF3E}
${goto 32}Total: ${totaldown ppp0}
${voffset -2}${font Poky:size=13}w${font}${goto 32}${voffset -4}Local IP: ${alignr}${addr ppp0}
${endif}${else}${voffset 4}${font PizzaDude Bullets:size=12}4${font}${goto 32}Network Unavailable${endif}${endif}
${hr 2}
```
Just use the command 1fallen gave you to replace wlan0 with your wifi device.
eth0 can be replaced with a wired device if you have or just leave as is.
[ATTACH=CONFIG]275215[/ATTACH]

**2)** Conky manager is just some scripts to start and stop various conky configs.
To run one conky config, you save a config as .conkyrc in your home directory and just use "conky" to start.
To run 2 or more configs use the **-c** option to specify a config.
```
conky -c */path/to/config*
```
give your configs names like sysinfo.conkyrc and weather.conkyrc.
I keep all my configs in ~/conky/configs
You can use a bash script in autostart.
My start script
```
#!/bin/bash

# click to start, click to stop
sleep 5

if pidof conky | grep [0-9] > /dev/null
then
   killall conky 
else
   
conky -c /home/glen/conky/configs/gnome-panel.conkyrc &
conky -c /home/glen/conky/configs/weather-waters-gnome.conkyrc &  

fi
exit 0
```
The script can also be used to toggle the conkys on/off

**3)** How much weather info do you want?
Do you want a separate weather conky?
For temperatures you need to install hddtemp and sensors.
hddtemp needs to be configured for access without root.
sensors also needs to be configured.
See [**[COLOR=#FF0000]HERE[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=281865&p=12700126&viewfull=1#post12700126")

Very Nice I like it..;)
However if using smaller area like this:
```
gap_x 25
gap_y 142
minimum_size 300 740
maximum_width 300
###End Position###
```
does not show as pretty as with a bigger window define.
Just a heads up is all.
Thanks guber2 :)

---

### Post by again? on 2017-05-21
> **1fallen said:**
> Very Nice I like it..;)
However if using smaller area like this:
```
gap_x 25
gap_y 142
minimum_size 300 740
maximum_width 300
###End Position###
```
does not show as pretty as with a bigger window define.
Just a heads up is all.
Thanks guber2 :)
Yeah thanks, I haven't really tested yet. 8-[
I'm just adding to LastDino's original config.

---

### Post by LastDino on 2017-05-21
Okay, both of you are brilliant people. 

@guber2

All the corrections made as per recommended 

> current progress

[ATTACH=CONFIG]275216[/ATTACH]


As per your suggestion I'll also make script for all the conky's

As per the problem of weather info and hardware temp, I would like to at least get current location and current weather, maximum one week not more than that. 

I'm on to installing those sensors you mentioned, if there is any particular configuration that needs to be done, please let me know.

And I'm mentioning this bit late, but would it be possible to also get fan speed up there? If not, no worries. You have already helped quite a lot ;)


@1fallen

I've like 15" laptop screen sadly >.<!

Both of you, thanks a lot!

---

### Post by again? on 2017-05-21
> **LastDino said:**
> Okay, both of you are brilliant people. 

@guber2

All the corrections made as per recommended 

> current progress

[ATTACH=CONFIG]275216[/ATTACH]


As per your suggestion I'll also make script for all the conky's

As per the problem of weather info and hardware temp, I would like to at least get current location and current weather, maximum one week not more than that. 

I'm on to installing those sensors you mentioned, if there is any particular configuration that needs to be done, please let me know.

And I'm mentioning this bit late, but would it be possible to also get fan speed up there? If not, no worries. You have already helped quite a lot ;)


@1fallen

I've like 15" laptop screen sadly >.<!

Both of you, thanks a lot!
Once you have followed the the link I gave for installing sensors you need to cobble together an awk/sed command to get your specific
sensors info into conky.
Sensors output differs according to your hardware.
For example my sensors output.
```
glen@GU17:~$ sensors
fam15h_power-pci-00c4
Adapter: PCI adapter
power1:       42.77 W  (crit =  95.06 W)

it8728-isa-0228
Adapter: ISA adapter
in0:          +0.84 V  (min =  +0.00 V, max =  +3.06 V)
in1:          +1.49 V  (min =  +0.00 V, max =  +3.06 V)
in2:          +1.99 V  (min =  +0.00 V, max =  +3.06 V)
+3.3V:        +3.22 V  (min =  +0.00 V, max =  +6.12 V)
in4:          +1.93 V  (min =  +0.00 V, max =  +3.06 V)
in5:          +2.21 V  (min =  +0.00 V, max =  +3.06 V)
in6:          +2.22 V  (min =  +0.00 V, max =  +3.06 V)
3VSB:         +3.26 V  (min =  +0.00 V, max =  +6.12 V)
Vbat:         +3.31 V  
fan1:        2115 RPM  (min =   10 RPM)
fan2:        1076 RPM  (min =   10 RPM)
fan3:           0 RPM  (min =    0 RPM)
temp1:        +31.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:        +34.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermal diode
temp3:        +26.0°C  (low  = +127.0°C, high = +70.0°C)  sensor = Intel PECI
intrusion0:  ALARM

k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +10.6°C  (high = +70.0°C)
                       (crit = +80.0°C, hyst = +77.0°C)
```
So to get my CPU temp I can run
```
glen@GU17:~$ **sensors | awk '/temp2:/{print $2}' | cut -c2-3**
34
```

Then the line in conky would be
```
${execi 3 sensors | awk '/temp2:/{print $2}' | cut -c2-3}°C
```
You can see this in the favconky I attached earlier.

If you are not familiar with awk/sed, post your "sensors" output.
There should be fan speed you can grab as well.

---

### Post by LastDino on 2017-05-21
sensors out put 

> acpitz-virtual-0
Adapter: Virtual device
temp1:        +47.0°C  (crit = +110.0°C)
temp2:        +47.0°C  (crit = +110.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +48.0°C  (high = +105.0°C, crit = +105.0°C)
Core 0:         +48.0°C  (high = +105.0°C, crit = +105.0°C)
Core 1:         +47.0°C  (high = +105.0°C, crit = +105.0°C)




---

### Post by LastDino on 2017-05-21
It appears fan speed is not detected, therefore I did lot of googling and came around this

> sudo sensors-detect



But even after saying "yes" to all, I've had no success with output of "sensors"

I'll try to see output again after restart.

---

### Post by ajgreeny on 2017-05-21
Just in case this might help here is the .conkyrc I use to get a conky output as shown in pic.
i think this includes a lot of what you are after and it may give you clues about how to proceed for other output as well.

I have always found conky can be incredibly frustrating getting exactly what you want, but also it is very satisfying, often after a lot of trial and error, to get what you want to show.
```
# set to yes if you want Conky to be forked in the background
background yes

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Ubuntu:size=11

# Text alpha when using Xft
xftalpha 0.9

# Update interval in seconds
update_interval 2.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes

# If own_window is yes, you may use type normal, desktop or override
own_window_type desktop

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window is yes, these window manager hints may be used
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 320

# Maximum width
maximum_width 320

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Draw borders around graphs
draw_graph_borders yes

# Stippled borders?
# stippled_borders 8

# border margins
# border_margin 2

# border width
# border_width 1

# Default colors and also border colors
default_color white
# default_shade_color red
# default_outline_color green

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
#alignment bottom_left
alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 25
gap_y 50

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 4

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no

# variable is given either in format $variable or in ${variable}

# stuff after 'TEXT' will be formatted on screen

TEXT
${color #FF0000}${font Ubuntu:size=20} ${alignc}${time %A %b %d %Y}
${font Ubuntu:size=40} ${alignc}${time %k:%M}${font Ubuntu:size=16}
${font Ubuntu:size=12}${color #FFFFFF}$nodename${alignr}Uptime:  $uptime
Kernel:${alignr}${exec uname -r # | cut -c 15-31}${font Ubuntu:size=11}

${color #FFFFFF}CPU1	${cpu cpu0}% ${color #FFA500}${cpubar cpu0}${color #FFFFFF}
CPU2	${cpu cpu1}% ${color #FFA500}${cpubar cpu1}${color #FFFFFF}
CPU3	${cpu cpu2}% ${color #FFA500}${cpubar cpu2}${color #FFFFFF}
CPU4	${cpu cpu3}% ${color #FFA500}${cpubar cpu3}
${cpugraph 20,320}${color #FFFFFF}
#Process CPU & MEM Usage${hr 2}        
Processes $alignr CPU%   MEM%   PID
 ${top name 1}  $alignr ${top cpu 1}  ${top mem 1}  ${top pid 1}
 ${top name 2}  $alignr ${top cpu 2}  ${top mem 1}  ${top pid 2}

Root$alignr ${fs_used /}/${fs_size /}
${fs_used_perc /}% ${color #FFA500}${fs_bar /}${color #FFFFFF}
Home$alignr ${fs_used /home}/${fs_size /home}
${fs_used_perc /home}% ${color #FFA500}${fs_bar /home}${color #FFFFFF}

RAM Used:$alignr$mem of $memmax = $memperc%
Swap:${alignr}$swapperc%     $swap of $swapmax

NETWORK IP: $alignr enp4s0 -  ${addr enp4s0}
DOWN: ${downspeed enp4s0}/s$alignr UP: ${upspeed enp4s0}/s
${color #FFA500}${downspeedgraph enp4s0 40,158}$alignr${upspeedgraph enp4s0 40,158}${color #FFFFFF}
#
# To make hddtemp run as user use command "sudo chmod u+s /usr/sbin/hddtemp"
# To make vnstat run as user use command "sudo chmod u+s /usr/bin/vnstat"
# "${execi 60 vnstat" updates figures every 60 seconds.
     DOWN:							${alignr}UP:     
TODAY: ${execi 60 vnstat | grep "today" | awk '{print $2 $3}'}${alignr}TODAY: ${execi 60 vnstat | grep "today" | awk '{print $5 $6}'}
Week:  ${execi 60 vnstat -w | grep "current week" | awk '{print $3 $4}'}${alignr}Week:  ${execi 60 vnstat -w | grep "current week" | awk '{print $6 $7}'}
Month: ${execi 60 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $3 $4}'}${alignr}Month: ${execi 60 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $6 $7}'}

CPU Temperature:                         ${alignr}${acpitemp} C
Disk Temperature:              ${alignr}${execi 60 hddtemp /dev/sda | cut -c 31-32} C

```

---

### Post by LastDino on 2017-05-21
> **ajgreeny said:**
> Just in case this might help here is the .conkyrc I use to get a conky output as shown in pic.
i think this includes a lot of what you are after and it may give you clues about how to proceed for other output as well.

I have always found conky can be incredibly frustrating getting exactly what you want, but also it is very satisfying, often after a lot of trial and error, to get what you want to show.


Thank you for sharing your conky settings. It will help me to compare and learn more.

Right now I'm stuck with weather and fanspeed functions, it would be wrong to say that I'm doing the heavy lifting but this is certainly enriching experience. I have never had to go through so many pages ever since coming over to Linux and I'm still mostly being handhold by 2 good samaritans.  

:)

---

### Post by #&amp;thj^% on 2017-05-21
Not sure then from the output from running sensors-detect that MB (Motherboard) supports
showing fanspeeds,
As far as weather on conky sadly this is or can be very frustrating as they the weather providers stop or change how they work with conky.
Now if you want to really give yourself a headache you can try this thread: [https://ubuntuforums.org/showthread.php?t=1771033](https://ubuntuforums.org/showthread.php?t=1771033)
Or there is other options as well like a simple conky like app. Named gis-weather
Found Here: [https://sourceforge.net/projects/gis-weather/](https://sourceforge.net/projects/gis-weather/)
I have been using it for over a year,  is reliable and has multiple providers.
IE:
1.) Gismeteo.com 
2.) AccuWeather.com
3.) OpenWeatherMap.org
See my screenshot for how it looks...and you can make it smaller by choosing 3 days instead of a 7 day forcast

---

### Post by again? on 2017-05-21
Just had a look at gis-weather and agree with 1fallen that this is a better
option than conky as access to API's is continually changed and configs lay dormant.
gis-weather is easy to setup, with nice presets and is generally well constructed.

I installed using the deb file from the sourceforge page 1fallen linked to.
Once you sign in to [https://openweathermap.org](https://openweathermap.org) you'll find an API  key at [https://home.openweathermap.org/api_keys](https://home.openweathermap.org/api_keys).
Search for your city and copy the code from the address bar.
Once you have copied and pasted the API  key and city code hit the "Add" button.

---

### Post by LastDino on 2017-05-22
Okay, I've checked the "sensors" output after reboot and it is same, so I'm giving up on fan speed as it does not seem to be worth that much hassle. 

Also, will install this weather widget.

Now, I've one more doubt of sort..

Are there different type of conky mechanisms (not themes), like I saw VNsdl one thread, what is the difference? Developers?

---

### Post by again? on 2017-05-22
No it's all conky just different configs that use scripts and images.
Conky changed to using lua scripting rather than what we have been using here.
Conky converts old style configs to lua on the fly.
If you start an old style config in terminal you will see something like
```
glen@GU17:~$ conky -c /home/glen/conky/configs/gotham-conkyrc
[B]conky: Syntax error (/home/glen/conky/configs/gotham-conkyrc:1: '=' expected near 'yes') while reading config file. 
conky: Assuming it's in old syntax and attempting conversion.[/B]
conky: desktop window (800033) is subwindow of root window (295)
conky: window type - desktop
conky: drawing to created window (0x4c00002)
conky: drawing to double buffer
```

The conky options/variables are very similar, just wrapped in lua syntax.
The start of a conky config in lua would look similar to this
```
**conky.config = {**

--  Basic Settings

	background = false,
	use_xft = true,
	font = 'monofur:size=9.5',
	xftalpha = 0.8,
	update_interval = 1,
	total_run_times = 0,
```

When you run 
```
sudo sensors-detect
```
make sure you're answering "yes" to all. Some default to "no".

You can also install inxi and compare the output it gives.
Inxi is a sysinfo script and is in the Ubuntu repos or get from [https://github.com/smxi/inxi](https://github.com/smxi/inxi)
```
glen@GU17:~$ **inxi -s**
Sensors:   System Temperatures: cpu: 30.0C mobo: 27.0C gpu: 32C
           Fan Speeds (in rpm): cpu: 1059 fan-1: 2191 fan-3: 0

```

---

### Post by LastDino on 2017-05-22
I see, thanks for explaination.

I've tried "sudo sensors-detect" and marked "yes" to every question thrown there.

Also tried inxi

Here is out put
>  System Temperatures: cpu: 46.0C mobo: 46.0C
           Fan Speeds (in rpm): cpu: N/A



---

### Post by again? on 2017-05-22
> **LastDino said:**
> I see, thanks for explaination.

I've tried "sudo sensors-detect" and marked "yes" to every question thrown there.

Also tried inxi

Here is out put
Maybe just out of luck.
Results from lm_sensors is bit iffy and depends on your hardware.
At least you have a CPU temp you can use.
That'll let you know if your fan isn't working. ;)

Here's some more info on lua config differences.
[https://forum.siduction.org/index.php?topic=5709.0](https://forum.siduction.org/index.php?topic=5709.0)

Conky installs a convert script that you can use to manually convert old conky configs to lua.
Not necessary but will show differences.
Requires luaxx
```
sudo apt install lua5.2
```

 find the  convert.lua file which is installed by conky.
```
locate convert.lua
```

Copy the convert.lua script and your conky config to a working directory. I use ~/Desktop 
```
cd ~/Desktop
cp /usr/share/doc/conky-all/convert.lua ~/Desktop/
```

Make executable
```
chmod +x convert.lua
```

Copy conky config to ~/Desktop and run (Overwrites config)

```
./convert.lua 'configname'
```

Or

```
./convert.lua 'configname' 'converted_name'
```

---

### Post by LastDino on 2017-05-22
Okay, so lua is not necessary atm? Are there any performance and appearance differences?

only one problem left then
On right top corner below kernel and OS info, there is update packs info
> color }${font caviar dreams:size=8}Updates: ${execi 360 aptitude search "~U" | wc -l | tail} Packs

it is not getting updated, what to change?

[ATTACH=CONFIG]275236[/ATTACH]


also, just wondering, is it possible to have update ticker, of lets say stock market or particular index looped in conky?

---

### Post by LastDino on 2017-05-22
After doing lot of searching I found out that with apt the following command gives out numerical output in terms of "upgradeable" packages

```

LANG=C apt-get upgrade -s |grep -P '^\d+ upgraded'|cut -d" " -f1 
```

example run

```
owl@owl-Lenovo-E40-80:~$ LANG=C apt-get upgrade -s |grep -P '^\d+ upgraded'|cut -d" " -f1
0


```

---

### Post by LastDino on 2017-05-22
Alright, everything I could think till now is there in conky, will be waiting for anyone who has any addition to suggest. 

Meanwhile will mark the thread as solved, as the initial problem is solved.

**Thanks and regards @guber2 @1fallen and @ajgreeny**

---

### Post by again? on 2017-05-22
The aptitude command would work but aptitude is not installed by default here.
It will not show updates until your sources are updated. When this happens depends on your settings.
[ATTACH=CONFIG]275237[/ATTACH]

As you have found you can simulate an upgrade but that will not change (same as aptitude) until an update runs according to your settings
or you manually run
```
sudo apt update
```

This command also shows updates but as before requires "apt update" having been run before true number of updates are shown.
```
/usr/lib/update-notifier/apt-check --human-readable | awk 'NR==1'
```

```
glen@GU17:~$ **/usr/lib/update-notifier/apt-check --human-readable | awk 'NR==1'**
41 packages can be updated.
```

---

### Post by LastDino on 2017-05-22
> **guber2 said:**
> The aptitude command would work but aptitude is not installed by default here.
It will not show updates until your sources are updated. When this happens depends on your settings.
[ATTACH=CONFIG]275237[/ATTACH]

As you have found you can simulate an upgrade but that will not change (same as aptitude) until an update runs according to your settings
or you manually run
```
sudo apt update
```

This command also shows updates but as before requires "apt update" having been run before true upgrades are shown.
```
/usr/lib/update-notifier/apt-check --human-readable | awk 'NR==1'
```



```
glen@GU17:~$ **/usr/lib/update-notifier/apt-check --human-readable | awk 'NR==1'**
41 packages can be updated.
```


I see, thank you again. But wouldn't it work if I installed aptitude? 

And yes, came across that code too, looks useful. :D

---

### Post by again? on 2017-05-22
> **LastDino said:**
> I see, thank you again. But wouldn't it work if I installed aptitude? 

And yes, came across that code too, looks useful. :D
No, it's the same thing. Will only show the current updates available after
"sudo apt update" is run either manually or according to your system update settings.
None of the commands actually perform an update, just check local info.

---

### Post by LastDino on 2017-05-22
So, is it possible to have it functioning in the conky? I haven't had opportunity to check if it works or not as my system is fully updated >.>

Edit: So, technically if I've one more script at the start up of the pc running/simulating update, it will show up in conky? Till then not?

---

### Post by again? on 2017-05-22
All the commands discussed should work.
Make your system check for updates every day as in [**post#27**]("https://ubuntuforums.org/showthread.php?t=2361842&p=13647827#post13647827") pic , then the info the commands retrieve will be relatively up to date.

---

### Post by LastDino on 2017-05-22
Awesome! I feel I've been through quick computer course. :lolflag:

Thanks!

---

### Post by again? on 2017-05-22
Conky 101 ....coming to a forum near you.
Don't forget to enrol next semester where we'll be discussing ways to cure the addiction. :p

---

### Post by LastDino on 2017-05-22
> **guber2 said:**
> Conky 101 ....coming to a forum near you.
Don't forget to enrol next semester where we'll be discussing ways to cure the addiction. :p

Aye, sir! 

Just wondering, is it also possible to have live feed of lets say "news" or stock ticker update in your conky? I'm thinking yes, and process should be as abusing as setting up weather manually? right? :D

---

### Post by again? on 2017-05-22
> **LastDino said:**
> Aye, sir! 

Just wondering, is it also possible to have live feed of lets say "news" or stock ticker update in your conky? I'm thinking yes, and process should be as abusing as setting up weather manually? right? :D
Abusing and/or amusing.

Yes, from "man conky"
> **rss uri interval_in_seconds action (num_par (spaces_in_front))**
Download and parse RSS feeds. The interval may be a (floating point) value greater than 0. Action may be one of the following: feed_title, item_title (with num par), item_desc (with num par) and item_titles (when using this action and spaces_in_front is given conky places that many spaces in front of each item). This object is threaded, and once a thread is created it can't be explicitly destroyed. One thread will run for each URI specified. You can use any protocol that Curl supports.

**stock symbol data**
Displays the data of a stock symbol. The following data is supported: adv(Average Daily Volume), ask, asksize, bid, askrt(ask realtime), bidrt(bid realtime), bookvalue, bidsize, change, commission, changert(change realtime), ahcrt(After Hours Change realtime), ds(dividend/share), ltd(Last Trade Date), tradedate, es(earnings/share), ei(error indication), epsecy(EPS Estimate Current Year), epseny(EPS Estimate Next Year), epsenq(EPS Estimate Next Quarter), floatshares, dayslow, dayshigh, 52weeklow, 52weekhigh, hgp(Holdings Gain Percent), ag(Annualized Gain), hg(Holdings Gain), hgprt(Holdings Gain Percent realtime), hgrt(Holdings Gain realtime), moreinfo, obrt(Order Book realtime), mc(Market Capitalization), mcrt(Market Cap realtime), ebitda, c52wlow(Change From 52-week Low), pc52wlow(Percent Change From 52-week Low), cprt(change percent realtime), lts(Last Trade Size), c52whigh(Change from 52-week high), pc52whigh(percent change from 52-week high), ltp(last trade price), hl(high limit), ll(low limit), dr(day's range), drrt(day's range realtime), 50ma(50-day Moving Average), 200ma(200-day Moving Average), c200ma(Change From 200-day Moving Average), pc200ma(Percent Change From 200-day Moving Average), c50ma(Change From 50-day Moving Average), pc50ma(Percent Change From 50-day Moving Average), name, notes, open, pc(previous close), pricepaid, cip(change in percent), ps(price/sales), pb(price/book), edv(Ex-Dividend Date), per(P/E Ratio), dpd(Dividend Pay Date), perrt(P/E Ratio realtime), pegr(PEG Ratio), pepsecy(Price/EPS Estimate Current Year), pepseny(Price/EPS Estimate Next Year), symbol, sharesowned, shortratio, ltt(Last Trade Time), tradelinks, tt(Ticker Trend), 1ytp(1 yr Target Price), volume, hv(Holdings Value), hvrt(Holdings Value realtime), 52weekrange, dvc(Day's Value Change), dvcrt(Day's Value Change realtime), se(Stock Exchange), dy(Dividend Yield)

$rss I haven't looked at in a long time and $stock I have never looked at because I don't have any money. :eek: #-o
Google "rss feed conky" and "stock ticker conky" and try some configs.

---

### Post by LastDino on 2017-05-22
> **guber2 said:**
> Abusing and/or amusing.

Yes, from "man conky"


$rss I haven't looked at in a long time and $stock I have never looked at because **I don't have any money.** :eek: #-o
Google "rss feed conky" and "stock ticker conky" and try some configs.

neither do I, but have to work for people who do so..#-o

I'll get on it, and now I see what people meant when they said it can be addictive :D

---

### Post by #&amp;thj^% on 2017-05-22
> **guber2 said:**
> Conky 101 ....coming to a forum near you.
Don't forget to enrol next semester where we'll be discussing ways _**to cure the addiction.**_ :p
:lolflag: Yes indeed...we need a sub forum for CA (Conky Anonymous)
Hi I'm 1fallen and I've been conky free for 30 days....LOL
BTW Great work here in this thread.=d>

> **LastDino said:**
> Aye, sir! 

Just wondering, is it also possible to have live feed of lets say "news" or stock ticker update in your conky? I'm thinking yes, and process should be as abusing as setting up weather manually? right? :D
It can be done but not sure it is worth the trouble.
Something like this in the terminal:
```
curl -s http://feeds.bbci.co.uk/news/world/rss.xml | grep "<title" | grep -o -P '(?<=CDATA\[).*(?=\]\])'| tail -n +2 | head -n 5


```
You can use the execi command in conky in conjunction with curl and some line editing to get anything you want out of a website
or write a bash script and run it using execi, or a lua script and load it up into conky

the tricky part is the data extraction
you will need some basic knowledge of grep sed awk or even curl... that kind of stuff to get the bits you want out of the html

---

### Post by LastDino on 2017-05-22
Thank you 1fallen

I've noticed something new
```

conky: desktop window (1200011) is subwindow of root window (f4)
conky: window type - normal
conky: drawing to created window (0x2c00002)
conky: drawing to double buffer
conky: Syntax error (/home/owl/.conky/configs/kernel.conkyrc:2: unexpected symbol near '#') while reading config file. 
conky: Assuming it's in old syntax and attempting conversion.
conky: forked to background, pid is 7535
conky: Syntax error (/home/owl/.conky/configs/process.conkyrc:1: '=' expected near 'yes') while reading config file. 
conky: Assuming it's in old syntax and attempting conversion.
conky: desktop window (1200011) is subwindow of root window (f4)
conky: window type - normal
conky: drawing to created window (0x2e00002)

conky: drawing to double buffer
conky: desktop window (1200011) is subwindow of root window (f4)
conky: window type - normal
conky: forked to background, pid is 7536
conky: drawing to created window (0x3400002)
conky: drawing to double buffer
conky: forked to background, pid is 7537


conky: can't load Xft font 'Ubuntu:size=14,weight:normal'
conky: can't load Xft font 'Ubuntu:size=12,weight:bold'
conky: can't load Xft font 'Ubuntu:size=10,weight:normal'
conky: can't load Xft font 'Ubuntu:size=10,weight:normal'
conky: can't load Xft font 'Ubuntu:size=10,weight:normal'
conky: can't load Xft font 'Ubuntu:size=10,weight:normal'
conky: can't load Xft font 'Ubuntu:size=10,weight:normal'
conky: can't load Xft font 'Ubuntu:size=10,weight:normal'
conky: can't load Xft font 'Ubuntu:size=10,weight:normal'
conky: can't load Xft font 'Ubuntu:size=10,weight:normal'
conky: can't load Xft font 'Ubuntu:size=10,weight:normal'
conky: can't load Xft font 'Ubuntu:size=10,weight:normal'



```

xft font is not loading? Why? Don't know how to install them on eOS >.>

---

### Post by #&amp;thj^% on 2017-05-22
Well that is a mystery!?
What conky version are you using?
```
apt policy conky-all
```

---

### Post by LastDino on 2017-05-22
> **1fallen said:**
> Well that is a mystery!?
What conky version are you using?
```
apt policy conky-all
```

```

~$ apt policy conky-all
conky-all:
  Installed: 1.10.1-3
  Candidate: 1.10.1-3
  Version table:
 *** 1.10.1-3 500
        500 http://in.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
        100 /var/lib/dpkg/status


```

---

### Post by #&amp;thj^% on 2017-05-22
> **LastDino said:**
> ```

~$ apt policy conky-all
conky-all:
  Installed: 1.10.1-3
  Candidate: 1.10.1-3
  Version table:
 *** 1.10.1-3 500
        500 http://in.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
        100 /var/lib/dpkg/status


```
Ok! Try removing the weight in your font conf.
IE:"Ubuntu:bold:size=8" but of course leave the size you want...8/9/10 yada yada
Where yours shows "'Ubuntu:size=14,weight:normal'"

---

### Post by LastDino on 2017-05-22
> **1fallen said:**
> Ok! Try removing the weight in your font conf.
IE:"Ubuntu:bold:size=8" but of course leave the size you want...8/9/10 yada yada
Where yours shows "'Ubuntu:size=14,weight:normal'"

Okay that problem is solved.

But I've another issue now. <.<

I can't seem to get that script to run on bootup automatically

I can run it manually by double clicking which executes all 3 conky's fine and it is working fine and executing fine. It is just that I've tried various solutions online to have script start automatically, but non of them is working. I tried adding file to init, init.d, adding line to rc.local even tried to add manual command to system startup saying conky.sh or something. Read somewhere that you could do it by putting script in /mnt/flash on eOs, tried that too. But no luck! 

What am I doing wrong here? :confused:

---

### Post by #&amp;thj^% on 2017-05-22
Well lets take a look at the startup script then...seems like a good place to start.Paste it here please.:)

---

### Post by LastDino on 2017-05-22
```

#!/bin/bash

# click to start, click to stop
sleep 5

if pidof conky | grep [0-9] > /dev/null
then
   killall conky 
else
   
conky -c /home/owl/.conky/configs/kernel.conkyrc &
conky -c /home/owl/.conky/configs/port.conkyrc &
conky -c /home/owl/.conky/configs/process.conkyrc &  

fi
exit 0
```

Any ideas?

---

### Post by #&amp;thj^% on 2017-05-22
For my setup I have all my .conkyrc's files in a folder named ".conky" along with any other stuff like images, xml, etc etc.
So my entry to put in the autostart is as follow's
```
sleep 30s
killall conky
cd "/home/me/.conky"  ###Replace me with your username###
conky -c "/home/me/.conky/.vindsl-conkyrc" &
cd "/home/me/.conky/Red Blocks Conky"
conky -c "/home/me/.conky/Red Blocks Conky/.conkyrc" &
cd "/home/me/.conky/TeejeeTech"
conky -c "/home/me/.conky/TeejeeTech/Network Panel" &

```
The above I named "conky-startup.sh"
 so do you notice the differences?

---

### Post by LastDino on 2017-05-22
> **1fallen said:**
> For my setup I have all my .conkyrc's files in a folder named ".conky" along with any other stuff like images, xml, etc etc.
So my entry to put in the autostart is as follow's
```
sleep 30s
killall conky
cd "/home/me/.conky"
conky -c "/home/me/.conky/.vindsl-conkyrc" &
cd "/home/me/.conky/Red Blocks Conky"
conky -c "/home/me/.conky/Red Blocks Conky/.conkyrc" &
cd "/home/me/.conky/TeejeeTech"
conky -c "/home/me/.conky/TeejeeTech/Network Panel" &

```
The above I named "conky-startup.sh"
 so do you notice the differences?

Changed the name to the "conky-startup.sh"

also, took out the files from config folder and put them out in .conky (parent one)
adjusted the path in script as well
```

#!/bin/bash

# click to start, click to stop
sleep 5

if pidof conky | grep [0-9] > /dev/null
then
   killall conky 
else
   
conky -c /home/owl/.conky/kernel.conkyrc &
conky -c /home/owl/.conky/port.conkyrc &
conky -c /home/owl/.conky/process.conkyrc &  

fi
exit 0


```

Now, whats next sir? :o

---

### Post by #&amp;thj^% on 2017-05-22
Dose that script work for you?
Hard for me to tell where all your folders (if any needed)  and configs reside 
Seems to me that it's lacking the initial start function...and I may be wrong. 
I would also give it more time to start...that way the first boot-up with 5 seconds on conky might be helpful. (less loading on boot-up);)

---

### Post by LastDino on 2017-05-22
If I would to add start function, how would you like me to  frame it in command? 

/I've no knowledge of scripting, sorry.

Also, script does run if you right click and click on run and conky starts. 

Not sure where that file needs to be linked to make it automated boot process. Any particular process you follow to make it part of automated process on each startup?

---

### Post by #&amp;thj^% on 2017-05-22
Oh ok I see...Open System-Settings>> then navigate to Applictios>> the Tabs at the top you will see "**Default** and** Startup**"click the **Startup** tab and point to your script "conky-startup.sh"
Now just to be sure everything will work as you want them now,,,,We need to check permissions on that (conky-startup.sh) and double check that it is set to be executable. (Right click "Properties Permissions")
And next boot you should have a conky starting for you now.
Fingers Crossed.

---

### Post by LastDino on 2017-05-22
Hurreeyy!!

I figured it out finally.

```

#!/bin/bash

#
sleep 20

if pidof conky | grep [0-9] > /dev/null
then
   killall conky 
else
cd "/home/me/.conky"   
conky -c /home/owl/.conky/kernel.conkyrc &
conky -c /home/owl/.conky/port.conkyrc &
conky -c /home/owl/.conky/process.conkyrc &  

fi
exit 0


```

I followed the startup app method as tried before and well explained by 1fallen in above post

The only real problem I had was the command that was being used in that startup app

after trying various combo's
```
 sh ".conky/conky-startup.sh" 
```

this one worked for me with current user log in.

I tried root with same command but it didn't work, for root I had to further specify the current users home directory and give a complete path. So, this will work for the user at a time I guess. Would have to have different setting for each user.

Though, would've loved to get directly running from system scripts rather than this app, but I'll leave that for some other day.

Thanks 1fallen, you've been great help. :)

---

### Post by #&amp;thj^% on 2017-05-22
Great Work LastDino and Thank You for your kind words. :)
I had a lot of fun here....Cheers and Kind Regards

---

### Post by again? on 2017-05-22
The script I gave should work.
Needs to be executable and use the full path in startup applications.
Eg for me the entry in startup applications is:
/home/glen/conky/startconky-gnome-zesty

Looking at post#50 your command to use in startups would be:
```
/home/owl/.conky/conky-startup.sh
```
To make a script executable via terminal you can: (chmod +x /path/to/script)
```
chmod +x /home/owl/.conky/conky-startup.sh
```


You may need to extend the sleep time in the script if you have a slow loading desktop.
The actual location of the script doesn't matter as long as you use the correct full path.
To run an executable script at startup all you need do is right click on the script in your file browser and "copy".
Then paste the path into the startup command.

---

### Post by again? on 2017-05-22
> **LastDino said:**
> Hurreeyy!!

I figured it out finally.

```

#!/bin/bash

#
sleep 20

if pidof conky | grep [0-9] > /dev/null
then
   killall conky 
else
[COLOR="#FF0000"]cd "/home/me/.conky" [/COLOR]  
conky -c /home/owl/.conky/kernel.conkyrc &
conky -c /home/owl/.conky/port.conkyrc &
conky -c /home/owl/.conky/process.conkyrc &  

fi
exit 0


```


**cd "/home/me/.conky" ** means **c**hange **d**irectory to /home/me/.conky
When copying, be aware of what you're copying to avoid stuffups. #-o :cry:
Unless you have a $USER named "me" it's not going to do anything.
For you it would be **cd "/home/owl/.conky"**
```
glen@GU17:~$ cd "/home/me/.conky"
bash: cd: /home/me/.conky: No such file or directory

glen@GU17:~$ cd "/home/glen/.conky"
glen@GU17:~/.conky$
```

A cd command is not required in the script anyway.

---

### Post by LastDino on 2017-05-23
@1fallen, Thanks! :D


@guber2, Lmao, sorry, it was 1am and was half sleepy when I made that change to script. Will change it right away! Thanks for pointing out! Thank you again sir!

---

### Post by again? on 2017-05-24
Hi LastDino,
Noticing one of your screenshots and as you are using Variety you may like some semi-transparency of your conky window so your 
conky is readable on light wallpapers.

Conky variables provide for 2 types of transparency.
1. A pseudo transparency  
[LIST]
[*]own_window_transparent yes
[/LIST]
2. RGB or real transparency.
[LIST]
[*]own_window_argb_visual yes
[*]own_window_argb_value 0       
[/LIST]
(own_window_argb_value can be 0-255 where 0 is totally transparent)
 
To make your window semi-transparent, you turn off pseudo transparency and use rgb transparency with a value around 150.
```
own_window_transparent no
own_window_argb_visual yes
own_window_argb_value 150
```

Another method to achieve semi-transparency is to use a lua script which can give nice rounded corners.
Save as **draw_bg_v3.lua**
```
--[[	Background by londonali1010 (2009)
	VinDSL Background Hack (2010-2011)

This script draws a background to the Conky window. It covers the whole of the Conky window, but you can specify rounded corners, if you wish.

To call this script in Conky, use (assuming you have saved this script to ~/scripts/):
	lua_load ~/scripts/draw_bg.lua
	lua_draw_hook_pre draw_bg

Changelog:
	+ v3.0	VinDSL Hack (01.28.2011) Killed memory leak.
	+ v2.4	VinDSL Hack (01.25.2011) Declared all variables in local.
	+ v2.3	VinDSL Hack (12.31.2010) Added shading example(s).
	+ v2.2	VinDSL Hack (12.30.2010) Cleaned up the code a bit.
	+ v2.1	VinDSL Hack (12.24.2010) Added cairo destroy function(s).
	+ v2.0	VinDSL Hack (12.21.2010) Added height adjustment variable.
	+ v1.0	Original release (07.10.2009)

]]

--------------START OF PARAMETERS ------------

-- Change these settings to affect your background:

-- "corner_r" is the radius, in pixels, of the rounded corners. If you don't want rounded corners, use 0.

	local corner_r = 30

-- Set the colour and transparency (alpha) of your background (0.00 - 0.99).

--	(Light Shading Example)
--	local bg_colour = 0x4d4d4d
--	local bg_alpha = 0.50

--	(Medium Shading Example)
--	local bg_colour = 0x222222
--	local bg_alpha = 0.50

--	(Dark Shading Example)
--	local bg_colour = 0x000000
--	local bg_alpha = 0.02

--	(Brown Shading Example)
--	local bg_colour = 0x330000
--	local bg_alpha = 0.04

--	(Ivory Black Shading Example)
--	local bg_colour = 0x292421
--	local bg_alpha = 0.22

--	(Navy Blue Shading Example)
--	local bg_colour = 0x33339F
--	local bg_alpha = 0.33

--	(Olive Green Shading Example)
--	local bg_colour = 0x333319
--	local bg_alpha = 0.13

--	(Silver Shading Example)
--	local bg_colour = 0xc0c0c0
--	local bg_alpha = 0.05

	local bg_colour = 0x000000
	local bg_alpha = 0.5

-- Tweaks the height of your background, in pixels. If you don't need to adjust the height, use 0.

--	(Default Setting)
	local vindsl_hack_height = -5

--	local vindsl_hack_height = -228

---------------END OF PARAMETERS -------------

require 'cairo'
local	cs, cr = nil

local function rgb_to_r_g_b(colour,alpha)
	return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
	end

function conky_draw_bg()
	if conky_window == nil then return end
	if cs == nil then cairo_surface_destroy(cs) end
	if cr == nil then cairo_destroy(cr) end
	local w = conky_window.width
	local h = conky_window.height
	local v = vindsl_hack_height
	local cs = cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, conky_window.width, conky_window.height)
	local cr = cairo_create(cs)
	
	cairo_move_to(cr,corner_r,0)
	cairo_line_to(cr,w-corner_r,0)
	cairo_curve_to(cr,w,0,w,0,w,corner_r)
	cairo_line_to(cr,w,h+v-corner_r)
	cairo_curve_to(cr,w,h+v,w,h+v,w-corner_r,h+v)
	cairo_line_to(cr,corner_r,h+v)
	cairo_curve_to(cr,0,h+v,0,h+v,0,h+v-corner_r)
	cairo_line_to(cr,0,corner_r)
	cairo_curve_to(cr,0,0,0,0,corner_r,0)
	cairo_close_path(cr)

	cairo_set_source_rgba(cr,rgb_to_r_g_b(bg_colour,bg_alpha))
	cairo_fill(cr)

	cairo_surface_destroy(cs)
	cairo_destroy(cr)
	end
```


In your conky config, turn both transparencies on and add a section to load the lua script.
```
own_window_transparent yes
own_window_argb_visual yes
own_window_argb_value 0

lua_load [COLOR="#FF0000"]~/conky/lua/draw_bg_v3.lua[/COLOR]
lua_draw_hook_pre draw_bg

```
[COLOR="#FF0000"]Edit[/COLOR] to the path where you saved draw_bg_v3.lua
The two lines to run the lua script can be added to any conky config to auto draw to the dimensions
of the conky window.

---

### Post by LastDino on 2017-05-24
What I had done for total transperency
```
  background yes
    double_buffer yes

    alignment top_left

    border_width 1
    cpu_avg_samples 2
    default_color white
    default_outline_color white
    default_shade_color white
    draw_borders no
    draw_graph_borders yes
    draw_outline no
    draw_shades no

    gap_x 0
    gap_y 50
    net_avg_samples 2
    no_buffers yes
    out_to_console no
    out_to_stderr no
    extra_newline no

    own_window yes
    own_window_type normal
    own_window_transparent yes
    own_window_colour 000000
 [B]   own_window_argb_visual yes
    own_window_argb_value 0[/B]
    own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

    minimum_size 170 0
    maximum_width 170
    stippled_borders 0
    update_interval 2.0
    uppercase no
    use_spacer none

    show_graph_scale no
    show_graph_range no

    use_xft yes
    xftalpha 0.1
    xftfont Droid Sans:size=10
    color0 white
    color1 EAEAEA
    color2 FFA300
    color3 grey

    TEXT
    ${color2}CPU ${color0}${alignr}${cpu cpu0}%
    ${cpubar cpu0 5,}
    ${execi 3 sensors | awk '/temp2:/{print $2}' | cut -c2-3}°C
    ${top name 1} $alignr ${top cpu 1}%
    ${top name 2} $alignr ${top cpu 2}%
    ${top name 3} $alignr ${top cpu 3}%
    ${top name 4} $alignr ${top cpu 4}%
    ${top name 5} $alignr ${top cpu 5}%

    ${color2}RAM ${color0}${alignr}${mem}
    ${membar 5,}
    ${top_mem name 1} $alignr ${top_mem mem_res 1}
    ${top_mem name 2} $alignr ${top_mem mem_res 2}
    ${top_mem name 3} $alignr ${top_mem mem_res 3}
    ${top_mem name 4} $alignr ${top_mem mem_res 4}
    ${top_mem name 5} $alignr ${top_mem mem_res 5}

    ${color2}SWAP ${color0}${alignr}${swap}
    ${swapbar 5,}

    
${color2}NETWORK ${color0}${alignr}${execi 3600 curl -s --retry 3 icanhazip.com}
${if_up wlp9s0}
${font Poky:size=14}Y${font}${goto 32}${voffset -8}SSID: ${wireless_essid wlp9s0}
${goto 32}Signal: ${wireless_link_qual wlp9s0}% ${alignr}${wireless_link_bar 8,60 wlp9s0}
${voffset 4}${font VariShapes Solid:size=14}q${font}${goto 32}${voffset -6}Up: ${upspeed wlp9s0}${font} ${alignr}${upspeedgraph wlp9s0 8,60 F57900 FCAF3E}
${goto 32}Total: ${totalup wlp9s0}
${voffset 4}${font VariShapes Solid:size=14}Q${font}${goto 32}${voffset -6}Down: ${downspeed wlp9s0}${font} ${alignr}${downspeedgraph wlp9s0 8,60 F57900 FCAF3E}
${goto 32}Total: ${totaldown wlp9s0}
${voffset 4}${font Poky:size=13}w${font}${goto 32}${voffset -8}Local IP: ${alignr}${addr wlp9s0}
${goto 32}Public IP: ${alignr}${execi 3600 curl -s --retry 3 icanhazip.com}
# |--eth0
${else}${if_up eth0}
${voffset -13}${font VariShapes Solid:size=14}q${font}${goto 32}${voffset -6}Up: ${upspeed eth0}${font} ${alignr}${upspeedgraph eth0 8,60 F57900 FCAF3E}
${goto 32}Total: ${totalup eth0}
${voffset -2}${font VariShapes Solid:size=14}Q${font}${goto 32}${voffset -6}Down: ${downspeed eth0}${font} ${alignr}${downspeedgraph eth0 8,60 F57900 FCAF3E}
${goto 32}Total: ${totaldown eth0}
${voffset -2}${font Poky:size=13}w${font}${goto 32}${voffset -4}Local IP: ${alignr}${addr eth0}
${goto 32}Public IP: ${alignr}${execi 3600 curl -s --retry 3 icanhazip.com}
# |--PPP0
${endif}${else}${if_up ppp0}
${voffset -13}${font VariShapes Solid:size=14}q${font}${goto 32}${voffset -6}Up: ${upspeed ppp0}${font} ${alignr}${upspeedgraph ppp0 8,60 F57900 FCAF3E}
${goto 32}Total: ${totalup ppp0}
${voffset -2}${font VariShapes Solid:size=14}Q${font}${goto 32}${voffset -6}Down: ${downspeed ppp0}${font} ${alignr}${downspeedgraph ppp0 8,60 F57900 FCAF3E}
${goto 32}Total: ${totaldown ppp0}
${voffset -2}${font Poky:size=13}w${font}${goto 32}${voffset -4}Local IP: ${alignr}${addr ppp0}
${endif}${else}${voffset 4}${font PizzaDude Bullets:size=12}4${font}${goto 32}Network Unavailable${endif}${endif}
${hr 2}

```

Is same as what you have mentioned, though this was done with CM and it edited the script as per my GUI edit instructions to it. But since you have explained to me what it actually means, now I get it.

I'm currently reading "Linuxcommand.org" to learn little bit of scripting, as that seems to integral part if I want to be savvy with this thing. I'm also going through  VinDSL, it sure has some complicated setups. 

Your help with lua scripts is very much appreciated, will try it out as soon as I get home.

---

### Post by again? on 2017-05-24
I love VinDSL's conky and have used his config in the past,
but be aware it is a nightmare to modify as he is a perfectionist using settings like
${font DroidSans:bold:size=[COLOR="#FF0000"]8.25[/COLOR]}
8 isn't good enough ...has to be 8.25 ](*,) 

Have a browse of [Conky Pitstop]("http://conky.pitstop.free.fr/wiki/index.php5?title=Category:Tips_and_tricks_(en)")
Setup a few years back by a regular contributor to this gigantic and once popular thread [**Post your .conkyrc files w/ screenshots**]("https://ubuntuforums.org/showthread.php?t=281865")

---

### Post by LastDino on 2017-05-24
> **guber2 said:**
> I love VinDSL's conky and have used his config in the past,
but be aware it is a nightmare to modify as hes is a perfectionist using settings like
${font DroidSans:bold:size=[COLOR=#FF0000]8.25[/COLOR]}
8 isn't good enough ...has to be 8.25 ](*,) 

Have a browse of [Conky Pitstop]("http://conky.pitstop.free.fr/wiki/index.php5?title=Category:Tips_and_tricks_(en)")
Setup a few years back by a regular contributor to this gigantic and once popular thread [**Post your .conkyrc files w/ screenshots**]("https://ubuntuforums.org/showthread.php?t=281865")

lmao, I'll keep that in mind

Thanks for links, and that thread has over 23k posts ](*,)

---

### Post by again? on 2017-05-24
> **LastDino said:**
> lmao, I'll keep that in mind

Thanks for links, and that thread has over 23k posts ](*,)
Yep and all started from this simple first post.
> **Dylan103 said:**
> Post all you're .conkyrc files with a screenshot please, Im interested in a basic, one liner at the top that has 
CPU Usage, Free space on the hd, Time(12 hour), Ram, and network usage.
:shock: 8-[

---

### Post by LastDino on 2017-05-24
> **guber2 said:**
> Yep and all started from this simple first post.

:shock: 8-[


:D

Must be like me, who ended up with 6 pages and 3 different conky scripts merged to make one theme. And now inspired to learn little bit of bash scripting

---

### Post by again? on 2017-05-24
> **LastDino said:**
> :D

Must be like me, who ended up with 6 pages and 3 different conky scripts merged to make one theme. And now inspired to learn little bit of bash scripting

[http://ryanstutorials.net/](http://ryanstutorials.net/)
[http://www.learnshell.org/](http://www.learnshell.org/)

The conky config is just that, a config file, but is also a fun way to learn linux in general.
That thread was full of advanced and novice linux users alike, of which I was one(novice), learning, questioning 
and bouncing ideas off of each other which just snowballed.

---

### Post by LastDino on 2017-05-24
> **guber2 said:**
> [http://ryanstutorials.net/](http://ryanstutorials.net/)
[http://www.learnshell.org/](http://www.learnshell.org/)

The conky config is just that, a config file, but is also a fun way to learn linux in general.
That thread was full of advanced and novice linux users alike, of which I was one(novice), learning, questioning 
and bouncing ideas off of each other which just snowballed.

My god, you're like a linux santa.  :o

Don't be surprised if I bother you in the future if I have any doubts here and there.

Bookmarked both, and started reading ryans tutorial already. It has lot more than bash, so this is going to be pretty useful.

---

