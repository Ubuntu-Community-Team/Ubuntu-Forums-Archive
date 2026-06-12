---
title: "Conky Hardcore blog relaunch!"
date: 2010-08-15
forum: The Cafe
---

### Post by Mahngiel on 2010-08-15
[COLOR=Red][[Conky Harcore]("http://conkyhardcore.com/")][/COLOR]
  
  Greetings *conki*stadors!
  
  If you have been developing Conky for any amount of time, you've surely  heard of the Conky Hardcore! site.  This site was graciously provided  the server space by Linux Hardcore!.  Over the past several weeks,  conversations regarding the stagnant website of lore concluded with the  efforts of a few turning it the site into a modern encyclopedia of Conky  goodness across all platforms of linux and all languages !
  
  We have many ideas we are looking forward to bringing to the community -  such as contests (and possibly even rewards!), best of's, and easier  resource searching.  Alone this task is daunting, so we reach out to all  of our communities to help us - this IS, after all, a collection of  public works.
  
  We have ambassadors scouring the forums in which they play looking for shining examples of the conky community for postage on the site.   What I am asking of you all from Ubuntu Forums is to post your favorite  scripts, rc's, and screenshots.  This thread borders on the edge of  :recurring discussion: due to some of the posts belonging to several  thread already.  To wit, I am requesting that this **does not **become a discussion thread, but solely limited to responses showcasing the ability of the community.
  
  We are looking for the most: bizzare, artistic, obscene, impractical,  clean, and though-provoking conkys the community can provide!  
 
 When submitting, be sure to ensure each script and rc have proper  declination at the head giving credit to the author and permission for [Creative Commons License]("http://creativecommons.org/")  for replication.  The best of the best, most original, and most  thought-provoking work's authors will be contacted by a CH! admin giving  awareness to their works being accepted and posted on the site.
 
 Help return the #5 google search site for 'conky' reach #1! 

[COLOR=Magenta]How to submit:[/COLOR]
It's as easy as replying to this thread with the content of your conkyrc  and script files along with a screenshot!  Make sure your screenie  shows your conkyrc adequately and clearly.

Again, please **do not** request assistance in this thread.  If you seek  assistance with your works, quote the code and create a post [[here]("http://ubuntuforums.org/showthread.php?t=281865")].

---

### Post by Mahngiel on 2010-08-15
Wifi Config calling images
```
#! /bin/bash
#Written by Mahngiel to call images
#Dependant upon on quality of 
#Network Connection
function on()
{
    if [ $lq -lt 100 ] && [ $lq -gt 50 ]; then
    echo '${image ~/Conky/images/nm-100.png -p 0,60 -s 24x24}'
    fi
    if [ $lq -lt 51 ] && [ $lq -gt 35 ]; then
    echo '${image ~/Conky/images/nm-75.png -p 0,60 -s 24x24}'
    fi
    if [ $lq -lt 36 ] && [ $lq -gt 19 ]; then
    echo '${image ~/Conky/images/nm-50.png -p 0,60 -s 24x24}'
    fi
    if [ $lq -lt 20 ] && [ $lq -gt 5 ]; then
    echo '${image ~/Conky/images/nm-25.png -p 0,60 -s 24x24}'
    fi
}
function off()
{
echo '${image ~/Conky/images/nm-00.png -p 0,60 -s 24x24}'
}
 
lq=$(iwconfig wlan0|grep 'Link Quality='|grep '='|grep --max-count=1 -o '\=\([0-9]\+\)'|grep --max-count=1 -o '\([0-9]\+\)')
 
if [ $lq -lt 5 ]
then
    off
else
    on
fi
 
exit 0
```Horizontal Calendar
```

#!/bin/bash
# horizontal calendar for conky by ans
# Updated by: mobilediesel, dk75, Bruce, Crinos512, et al.
#     Adjusted by Mahngiel for larger today and Day name only
# locale depend week day names
lang=$1
case ${lang:=$LANG} in
        en*  ) Sun="Su";   Mon="Mo";   Tue="Tu";   Wed="We";   Thu="Th";   Fri="Fr";   Sat="Sa" ;;
esac

 
COLOROLD="8996B3" #LightBlue
COLORTODAY="FFFFFF" #Darkorange
COLORREST="8996B3" #MidSlateGrey
COLORNEXT="778899" #LightSlateGrey
 
TODAY=$(date +%d)
LASTDAY=$(date -d "-$TODAY days +1 month" +%d)
FIRSTDAY=$(date -d "-$[${TODAY/#0/}-1] days" +%u)
TODAYC="\${color $COLORTODAY}\${font Secret Code:size=18} $TODAY\${font}\${color}"
 
# Build $TOPLINE
j=31
k=$FIRSTDAY
while [ $j -gt 0 ]; do
  case "$k" in
    1) TOPLINE="$TOPLINE $Mon";;
    2) TOPLINE="$TOPLINE $Tue";;
    3) TOPLINE="$TOPLINE $Wed";;
    4) TOPLINE="$TOPLINE $Thu";;
    5) TOPLINE="$TOPLINE $Fri";;
    6) TOPLINE="$TOPLINE \${color FF8C00}$Sat\${color}";;
    7) TOPLINE="$TOPLINE \${color FFFF00}$Sun\${color}"
       k=0
       ;;
  esac
  j=$[$j-1]
  k=$[$k+1]
done
 
# Build $OVER
i=1
OVER="\${color $COLOROLD}"
while [ $i -lt $TODAY ]; do
  case $i in
    [1-9])   OVER="$OVER 0$i" ;;
    *)       OVER="$OVER $i"  ;;
  esac
  i=$[$i+1]
done
OVER="$OVER\${color}"
 
# skip i where value of i=$TODAY
i=$[$i+1] 
 
# Build $REST
REST="\${color $COLORREST}"
while [ $i -le $LASTDAY ]; do
  case $i in
    [1-9])   REST="$REST 0$i" ;;
    *)       REST="$REST $i"  ;;
  esac
  i=$[$i+1]
done
REST="$REST\${color}"
 
# Build $NEXTMONTH
i=$LASTDAY
j=1
NEXTMONTH=""
if [ $i -ne 31 ] ; then
  NEXTMONTH="\${color $COLORNEXT}"
  while [ $i -lt 31 ] ; do
     NEXTMONTH="$NEXTMONTH 0$j"
     i=$[$i+1]
     j=$[$j+1]
  done
  NEXTMONTH="$NEXTMONTH\${color}"
fi
 
#echo "$TOPLINE\${tab 20}"
#echo "\${offset 40}\${offset 30}\${color $COLORTODAY}\${time %A}\${font}\${color}"
echo "\${offset 12}$OVER$TODAYC\${voffset -5}$REST$NEXTMONTH\${tab 20}"
echo "\${image ~/Conky/Blue2/images/bluecal.png -s 100x80 -p -14,10}"
```Count items in trash:
```
${execi 60 ~/.local/share/Trash/files/* | wc -l}
```

---

### Post by djyoung4 on 2010-08-15
Heres probably my most original one
conkyrc:
```
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
mail_spool $MAIL

# Update interval in seconds
update_interval 5.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window no

# If own_window is yes, you may use type normal, desktop or override
own_window_type desktop

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window_transparent is set to no, you can set the background colour here
own_window_colour black

# If own_window is yes, these window manager hints may be used
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 280 5

# Maximum width
maximum_width 10

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Draw borders around graphs
draw_graph_borders no

# Stippled borders?
stippled_borders 8

# border margins
border_inner_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color black

# Text alignment, other possible values are commented
alignment top_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right
#alignment top_middle
#alignment bottom_middle
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 1
gap_y 1

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer none

# Shows the maximum value in scaled graphs.
show_graph_scale no

# Shows the time range covered by a graph.
show_graph_range no

# Allow each port monitor to track at most this many connections (if 0 or not set, default is 256)
#max_port_monitor_connections 256

# Maximum number of special things, e.g. fonts, offsets, aligns, etc.
#max_specials 512

# Maximum size of buffer for user text, i.e. below TEXT line.
#max_user_text 16384

# Timing interval for music player thread, e.g. mpd, audacious
#music_player_interval (update_interval is default)

# Strictness of if_up. One of: up, link or address. The later ones imply the further ones.
# Defaults to up.
#if_up_strictness address
  #-d DATATYPE, --datatype=DATATYPE
                        #[default: HT] The data type options are: DW (Day of
                        #Week), WF (Weather Font output), WI (Weather Icon
                        #Path), LT (Forecast:Low Temp,Current:Feels Like Temp),
                        #HT (Forecast:High Temp,Current:Current Temp), CC
                        #(Current Conditions), CT (Conditions Text), PC
                        #(Precipitation Chance), HM (Humidity), VI
                        #(Visibility), WD (Wind Direction), WA (Wind Angle - in
                        #degrees), WS (Wind Speed), WG (Wind Gusts), BF
                        #(Bearing Font), BI (Bearing Icon Path), BS (Bearing
                        #font with Speed), CN (City Name), CO (Country), OB
                        #(Observatory), SR (SunRise), SS (SunSet), DL
                        #(DayLight), MP (Moon Phase), MF (Moon Font), MI (Moon
                        #Icon Path), BR (Barometer Reading), BD (Barometer
                        #Description), UI (UV Index), UT (UV Text), DP (Dew
                        #Point), LU (Last Update at weather.com), LF (Last
                        #Fetch from weather.com). Not applicable at command
                        #line when using templates.


# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen
# -- Lua Load -- #
lua_load ~/Documents/code/luarings
lua_draw_hook_pre load_widgets

TEXT
${goto 320}${voffset 500}
```
luarings:
```
--[[
Conky Widgets by londonali1010 (2009)

Call this script in Conky using the following before TEXT (assuming you save this script to ~/scripts/conky_widgets.lua):
    lua_load ~/Scripts/conky_widgets.lua
    lua_draw_hook_pre load_widgets ]]

require 'cairo'
function draw_atext()
    if conky_window==nil then return end
    local w=conky_window.width
    local h=conky_window.height
    local cs=cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, w, h)
    cr=cairo_create(cs)

    
        
-- Font
cairo_select_font_face (cr, "Dejavu Sans", CAIRO_FONT_SLANT_NORMAL, CAIRO_FONT_WEIGHT_NORMAL);

-- font size
cairo_set_font_size (cr, 20.0);

--font color
cairo_set_source_rgba (cr, 0.9, 0.4, 0.3, 0.6);

cairo_translate (cr, 128.0, 128.0);
-- angle
cairo_rotate(cr,0.4);

-- text position
cairo_move_to (cr, 270.0, 295.0);

-- shown text
cairo_show_text (cr, conky_parse('${time %H:%M}'))


cairo_rotate(cr,-0.9);
cairo_set_font_size (cr, 12.0);
cairo_move_to (cr, -97.0, 520.0);
cairo_show_text (cr, conky_parse('${time %A}'))

cairo_rotate(cr,0.0);
cairo_set_font_size (cr, 14.0);
cairo_move_to (cr, -115.0, 568.0);
cairo_show_text (cr, conky_parse('${time  %h %d}'))

cairo_rotate(cr,0.3);
cairo_set_font_size (cr, 10.0);
cairo_move_to (cr, 360, 490);
 cairo_show_text (cr, conky_parse('Gmail: ${execi 600 conkyEmail --servertype=IMAP --servername=imap.googlemail.com --username=xyz --password=xyz --ssl}'))

cairo_rotate(cr,0.3);
cairo_set_font_size (cr, 10.0);
cairo_move_to (cr, 140, 187);
cairo_show_text (cr, conky_parse('${if_match ${acpitemp} > 60}${color red}${acpitemp}$color$else${acpitemp}$endif°C'))

cairo_rotate(cr,0.05);
cairo_set_font_size (cr, 10.0);
cairo_move_to (cr, 405, 190);
cairo_show_text (cr, conky_parse('${if_match ${execi 5 ~/Documents/code/hddmonit.sh} > 60}${color red}${execi 5 ~/Documents/code/hddmonit.sh}$color$else${execi 5 ~/Documents/code/hddmonit.sh}$endif°C'))

cairo_stroke (cr);




end


--[[
Ring Meters by londonali1010 (2009)
 
This script draws percentage meters as rings. It is fully customisable; all options are described in the script.
 
IMPORTANT: if you are using the 'cpu' function, it will cause a segmentation fault if it tries to draw a ring straight away. The if statement on line 145 uses a delay to make sure that this doesn't happen. It calculates the length of the delay by the number of updates since Conky started. Generally, a value of 5s is long enough, so if you update Conky every 1s, use update_num > 5 in that if statement (the default). If you only update Conky every 2s, you should change it to update_num > 3; conversely if you update Conky every 0.5s, you should use update_num > 10. ALSO, if you change your Conky, is it best to use "killall conky; conky" to update it, otherwise the update_num will not be reset and you will get an error.
 
To call this script in Conky, use the following (assuming that you save this script to ~/scripts/rings.lua):
    lua_load ~/scripts/rings-v1.2.1.lua
    lua_draw_hook_pre ring_stats
 
Changelog:
+ v1.2.1 -- Fixed minor bug that caused script to crash if conky_parse() returns a nil value (20.10.2009)
+ v1.2 -- Added option for the ending angle of the rings (07.10.2009)
+ v1.1 -- Added options for the starting angle of the rings, and added the "max" variable, to allow for variables that output a numerical value rather than a percentage (29.09.2009)
+ v1.0 -- Original release (28.09.2009)
]]
 
settings_table = {
    {
        name='cpu',
        arg='cpu1',
        max=100,
        bg_colour=0xff0000,
        bg_alpha=0.2,
        fg_colour=0xff0000,
        fg_alpha=0.6,
        x=1125, y=150,
        radius=900,
        thickness=11,
        start_angle=224,
        end_angle=230.5
    },
    {
        name='cpu',
        arg='cpu2',
        max=100,
        bg_colour=0xff0000,
        bg_alpha=0.2,
        fg_colour=0xff0000,
        fg_alpha=0.6,
        x=492, y=685,
        radius=70,
        thickness=10,
        start_angle=239,
        end_angle=298
    },
    	{
		name='battery_percent',
		arg='BAT0',
		max=100,
		bg_colour=0xff0000,
		bg_alpha=0.2,
		fg_colour=0xff0000,
		fg_alpha=0.6,
		x=-1500, y=-400,
		radius=2200,
		thickness=9,
		start_angle=115.3,
		end_angle=118.5
	},

    {
        name='fs_free_perc',
        arg='/',
        max=100,
        bg_colour=0xff0000,
        bg_alpha=0.2,
        fg_colour=0xff0000,
        fg_alpha=0.6,
        x=398, y=513,
        radius=95,
        thickness=8,
        start_angle=45,
        end_angle=105
    },
    {
        name='memperc',
        arg='',
        max=100,
        bg_colour=0xff0000,
        bg_alpha=0.2,
        fg_colour=0xff0000,
        fg_alpha=0.6,
        x=-1300, y=2490,
        radius=2700,
        thickness=5,
        start_angle=39,
        end_angle=40.75
    },
    {
        name='swap',
        arg='',
        max=100,
        bg_colour=0xff0000,
        bg_alpha=0.2,
        fg_colour=0xff0000,
        fg_alpha=0.6,
        x=472, y=334,
        radius=90,
        thickness=6,
        start_angle=234,
        end_angle=303
    },
}
 
require 'cairo'
 
function rgb_to_r_g_b(colour,alpha)
    return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
end
 
function draw_ring(cr,t,pt)
    local w,h=conky_window.width,conky_window.height
 
    local xc,yc,ring_r,ring_w,sa,ea=pt['x'],pt['y'],pt['radius'],pt['thickness'],pt['start_angle'],pt['end_angle']
    local bgc, bga, fgc, fga=pt['bg_colour'], pt['bg_alpha'], pt['fg_colour'], pt['fg_alpha']
 
    local angle_0=sa*(2*math.pi/360)-math.pi/2
    local angle_f=ea*(2*math.pi/360)-math.pi/2
    local t_arc=t*(angle_f-angle_0)
 
    -- Draw background ring
 
    cairo_arc(cr,xc,yc,ring_r,angle_0,angle_f)
    cairo_set_source_rgba(cr,rgb_to_r_g_b(bgc,bga))
    cairo_set_line_width(cr,ring_w)
    cairo_stroke(cr)
 
    -- Draw indicator ring
 
    cairo_arc(cr,xc,yc,ring_r,angle_0,angle_0+t_arc)
    cairo_set_source_rgba(cr,rgb_to_r_g_b(fgc,fga))
    cairo_stroke(cr)        
end
 
function conky_ring_stats()
    local function setup_rings(cr,pt)
        local str=''
        local value=0
 
        str=string.format('${%s %s}',pt['name'],pt['arg'])
        str=conky_parse(str)
 
        value=tonumber(str)
        if value == nil then value = 0 end
        pct=value/pt['max']
 
        draw_ring(cr,pct,pt)
    end
 
    if conky_window==nil then return end
    local cs=cairo_xlib_surface_create(conky_window.display,conky_window.drawable,conky_window.visual, conky_window.width,conky_window.height)
 
    local cr=cairo_create(cs)    
 
    local updates=conky_parse('${updates}')
    update_num=tonumber(updates)
 
    if update_num>5 then
        for i in pairs(settings_table) do
            setup_rings(cr,settings_table[i])
        end
    end
end

function conky_load_widgets()
 if conky_window==nil then return end
    local cs=cairo_xlib_surface_create(conky_window.display,conky_window.drawable,conky_window.visual, conky_window.width,conky_window.height)
    
    local cr=cairo_create(cs)    
    
    local updates=conky_parse('${updates}')
    update_num=tonumber(updates)
    
    if update_num>5 then
       draw_atext()
       conky_ring_stats()
    end
end
```
hddmonit:
```
#!/bin/bash
echo "$(nc localhost 7634 | cut -d'|' -f4)"
```

---

### Post by wlourf on 2010-08-30
Hi, it looks like this thread is asleep :(

Here is my most customizable conky (It would be nice to see it on CH!)
It includes two lua scripts (text+rings) and a script from larryni to display image from amarok.
Set-up is explained in the README, fell free to ask by MP if you have any question. (I've already posted it in the [conky thread)]("http://ubuntuforums.org/showpost.php?p=9694362&postcount=13278")

---

### Post by Concrete Pants on 2010-09-11
Here is one that I've had for a month or so now:

```
own_window yes
own_window_transparent yes
own_window_type override
own_window_hints sticky,undecorated,below,skip_taskbar,skip_pager

background yes

double_buffer yes
no_buffers

use_xft yes
xftfont Sawasdee:size=10
xftalpha 1

draw_outline no
draw_graph_borders no
draw_shades no

default_bar_size 100 5

update_interval 1

border_width 0

minimum_size 1280 800

alignment tr
gap_x 0
gap_y 0

TEXT
${voffset 670}${offset 20}${font Sawasdee:size=64}${color #000000}${execi 2 ~/.conkyScripts/./sayTime2.sh}
${voffset -50}${offset 25}${execibar 2 ~/.conkyScripts/./queryWireless.sh}${offset 10}${battery_bar}${offset 10}${cpubar}${offset 10}${membar}
```The time is returned from this:

```
#! /bin/bash

# HOURPAST=""
# HOURTO=""
# HOURCAP=""
# MINUTES=""
# TOPAST=""
# OUTPUT=""

HOURTEMP=`date +%l`
MINTEMP=`date +%M`

# get hour
if [ $HOURTEMP -eq 1 ]; then
    HOURCAP="One"
    HOURCAP2="Two"
    HOURPAST="one"
    HOURTO="two"
fi
if [ $HOURTEMP -eq 2 ]; then
    HOURCAP="Two"
    HOURCAP2="Three"
    HOURPAST="two"
    HOURTO="three"
fi
if [ $HOURTEMP -eq 3 ]; then
    HOURCAP="Three"
    HOURCAP2="Four"
    HOURPAST="three"
    HOURTO="four"
fi
if [ $HOURTEMP -eq 4 ]; then
    HOURCAP="Four"
    HOURCAP2="Five"
    HOURPAST="four"
    HOURTO="five"
fi
if [ $HOURTEMP -eq 5 ]; then
    HOURCAP="Five"
    HOURCAP2="Six"
    HOURPAST="five"
    HOURTO="six"
fi
if [ $HOURTEMP -eq 6 ]; then
    HOURCAP="Six"
    HOURCAP2="Seven"
    HOURPAST="six"
    HOURTO="seven"
fi
if [ $HOURTEMP -eq 7 ]; then
    HOURCAP="Seven"
    HOURCAP2="Eight"
    HOURPAST="seven"
    HOURTO="eight"
fi
if [ $HOURTEMP -eq 8 ]; then
    HOURCAP="Eight"
    HOURCAP2="Nine"
    HOURPAST="eight"
    HOURTO="nine"
fi
if [ $HOURTEMP -eq 9 ]; then
    HOURCAP="Nine"
    HOURCAP2="Ten"
    HOURPAST="nine"
    HOURTO="ten"
fi
if [ $HOURTEMP -eq 10 ]; then
    HOURCAP="Ten"
    HOURCAP2="Eleven"
    HOURPAST="ten"
    HOURTO="eleven"
fi
if [ $HOURTEMP -eq 11 ]; then
    HOURCAP="Eleven"
    HOURCAP2="Twelve"
    HOURPAST="eleven"
    HOURTO="twelve"
fi
if [ $HOURTEMP -eq 12 ]; then
    HOURCAP="Twelve"
    HOURCAP2="One"
    HOURPAST="twelve"
    HOURTO="one"
fi

# get minute
if [ $MINTEMP -eq 58 ] || [ $MINTEMP -eq 59 ]; then
    MINUTES="$HOURCAP2 o'clock"
fi

if [ $MINTEMP -eq 0 ] || [ $MINTEMP -eq 1 ] || [ $MINTEMP -eq 2 ]; then
    MINUTES="$HOURCAP o'clock"
fi

if [ $MINTEMP -eq 3 ] || [ $MINTEMP -eq 4 ] || [ $MINTEMP -eq 5 ] || [ $MINTEMP -eq 6 ] || [ $MINTEMP -eq 7 ]; then
    MINUTES="Five past $HOURPAST"
fi

if [ $MINTEMP -eq 8 ] || [ $MINTEMP -eq 9 ] || [ $MINTEMP -eq 10 ] || [ $MINTEMP -eq 11 ] || [ $MINTEMP -eq 12 ]; then
    MINUTES="Ten past $HOURPAST"
fi

if [ $MINTEMP -eq 13 ] || [ $MINTEMP -eq 14 ] || [ $MINTEMP -eq 15 ] || [ $MINTEMP -eq 16 ] || [ $MINTEMP -eq 17 ]; then
    MINUTES="Quarter past $HOURPAST"
fi

if [ $MINTEMP -eq 18 ] || [ $MINTEMP -eq 19 ] || [ $MINTEMP -eq 20 ] || [ $MINTEMP -eq 21 ] || [ $MINTEMP -eq 22 ]; then
    MINUTES="Twenty past $HOURPAST"
fi

if [ $MINTEMP -eq 23 ] || [ $MINTEMP -eq 24 ] || [ $MINTEMP -eq 25 ] || [ $MINTEMP -eq 26 ] || [ $MINTEMP -eq 27 ]; then
    MINUTES="Twenty five past $HOURPAST"
fi

if [ $MINTEMP -eq 28 ] || [ $MINTEMP -eq 29 ] || [ $MINTEMP -eq 30 ] || [ $MINTEMP -eq 31 ] || [ $MINTEMP -eq 32 ]; then
    MINUTES="Half past $HOURPAST"
fi

if [ $MINTEMP -eq 33 ] || [ $MINTEMP -eq 34 ] || [ $MINTEMP -eq 35 ] || [ $MINTEMP -eq 36 ] || [ $MINTEMP -eq 37 ]; then
    MINUTES="Twenty five to $HOURTO"
fi

if [ $MINTEMP -eq 38 ] || [ $MINTEMP -eq 39 ] || [ $MINTEMP -eq 40 ] || [ $MINTEMP -eq 41 ] || [ $MINTEMP -eq 42 ]; then
    MINUTES="Twenty to $HOURTO"
fi

if [ $MINTEMP -eq 43 ] || [ $MINTEMP -eq 44 ] || [ $MINTEMP -eq 45 ] || [ $MINTEMP -eq 46 ] || [ $MINTEMP -eq 47 ]; then
    MINUTES="Quarter to $HOURTO"
fi

if [ $MINTEMP -eq 48 ] || [ $MINTEMP -eq 49 ] || [ $MINTEMP -eq 50 ] || [ $MINTEMP -eq 51 ] || [ $MINTEMP -eq 52 ]; then
    MINUTES="Ten to $HOURTO"
fi

if [ $MINTEMP -eq 53 ] || [ $MINTEMP -eq 54 ] || [ $MINTEMP -eq 55 ] || [ $MINTEMP -eq 56 ] || [ $MINTEMP -eq 57 ]; then
    MINUTES="Five to $HOURTO"
fi

echo $MINUTES
```and the result is:

---

### Post by gamamoto on 2013-01-08
It seems that the website doesn't exist anymore, is it anywhere else or is it just down forever ?

---

### Post by lisati on 2013-01-08
Looks like the domain registration has lapsed some time in the last couple of years.

Old thread closed.

---

