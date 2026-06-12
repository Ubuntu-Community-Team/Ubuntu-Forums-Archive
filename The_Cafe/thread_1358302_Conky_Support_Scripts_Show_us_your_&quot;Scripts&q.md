---
title: "Conky Support Scripts: Show us your &quot;Scripts&quot; &amp; Screenshots of what they do."
date: 2009-12-18
forum: The Cafe
---

### Post by Bruce M. on 2009-12-18
OK, the mega thread [Post your .conkyrc files w/ screenshots]("http://ubuntuforums.org/showthread.php?t=281865&page=1106") has been hijacked by Conky Calendars, to the point that people asking for help with other aspects of conky are having their requests for help buried in an avalanche.

So today I though why not a Conky "Script" Support Thread?  Obviously if you are showing your Conky screenshot and the files that did it the scripts will accompany it [on the other thread]("http://ubuntuforums.org/showthread.php?t=281865&page=1106").

But if you see a "script", bash, python, perl - who cares, that you can "touch up" copy it here and have at it with various other "script junkies" (meant in a good way), after all we all win!  Or if you have a NEW script for conky you are working on bring it here.  :)

I ask that each post here has a link to [Post your .conkyrc files w/ screenshots]("http://ubuntuforums.org/showthread.php?t=281865&page=1106") if the script came from there or when the "CCCC" script writers agree that it's done as best it can be, a post on the mega thread explaining what the script does with a screenie and a link to the post here to get the script.

What do you think?
Have a nice day.
Bruce

---

### Post by dk75 on 2009-12-18
There could be a BASH script yes?

---

### Post by Bruce M. on 2009-12-18
> **dk75 said:**
> There could be a BASH script yes?

Absolutely for example:

```
${execpi 8 hddtemp /dev/sda | cut --characters 34-37 | xargs ~/Conky/scripts/ColorTempHDD.sh}
```

calls the bash script: **ColorTempHDD.sh** a modified version of Crinos'512's [colorize.sh]("http://conky.linux-hardcore.com/?page_id=747");

```
#!/bin/bash
# colorize.sh
# by: Crinos512

COOL=45
WARM=56

if [[ $1 < $COOL ]]
   then echo "\${color7}"$1    # COOL
elif [[ $1 > $WARM ]]
   then echo "\${color9}"$1    # HOT
else echo "\${color8}"$1       # WARM
fi

exit 0
```

CHIMO!
Bruce

---

### Post by guriinii on 2009-12-18
What a fantastic idea! Bruce you legend. 

Right... curl and rss feeds, can somebody give some me some guides, tips or help?

Thanks in advance

---

### Post by dk75 on 2009-12-18
why... did it need to be curl?

```
sudo apt-get install python-feedparser
```

there is web page with all available commands: [Universal Feedparser]("http://www.feedparser.org/")

and there is my example code
```

#! /usr/bin/env python
# -*- coding: utf-8 -*-
##############################################################
# parse RSS feed
# RSS.py rss.url no._of_entry_to_parse
##############################################################

import sys
import feedparser
d = feedparser.parse(sys.argv[1])
print
print d.entries[int(sys.argv[2])].title.replace('<br />' , '\n').replace('<p>' , '\n\t').replace('</p>' , '\n')
print
print d.entries[int(sys.argv[2])].description.replace('<br />' , '\n').replace('<p>' , '\n\t').replace('</p>' , '\n')
print
e = d.entries[int(sys.argv[2])]
print ('Link: '),e.link
print
print d.entries[int(sys.argv[2])].category
print
print d.entries[int(sys.argv[2])].status
print
quit()

```

---

### Post by mobilediesel on 2009-12-18
Excellent idea! I wish **I'd** thought of it!
 as a reply to one of your [posts]("http://ubuntuforums.org/showpost.php?p=8520172&postcount=11069") in the [conky mega-thread]("http://ubuntuforums.org/showthread.php?t=281865"):

[BASH Beginner's Guide]("http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html")
and
[Writing Shell Scripts]("http://linuxcommand.org/writing_shell_scripts.php")

and this script I'll post here isn't even mine:
[conky-rss.sh]("http://dl.dropbox.com/u/1055489/scripts/conky-rss.sh")
```
#!/bin/bash
# RSS Display Script by Bill Woodford (admin@sdesign.us) v1.0
#
#RSS Setup - Don't change unless you want these values hard-coded!
uri=$1                                                  #URI of RSS Feed
lines=$2                                                #Number of headlines
titlenum=$3                                             #Number of extra titles
#Script start
#Require a uri, as a minimum
if [[ "$uri" == "" ]]; then
        echo "No URI specified, cannot continue!" >&2
        echo "Please read script for more information" >&2
else
        #Set defaults if none specified
        if [[ $lines == "" ]]; then lines=25 ; fi
        if [[ $titlenum == "" ]]; then titlenum=2 ; fi

        #The actual work
        curl -A "Mozilla/5.0" -s --connect-timeout 30 $uri |\
        grep -io "<title>[^<]*"|\
        sed -e 's/<[^>]*>//'|\
        head -n $(($lines + $titlenum)) |\
        tail -n $(($lines))
fi
```

---

### Post by Bruce M. on 2009-12-18
> **mobilediesel said:**
> Excellent idea! I wish **I'd** thought of it!

OK you though of it, no biggie.

THANK YOU for the links.  :)

CHIMO!
Bruce

---

### Post by guriinii on 2009-12-18
> **dk75 said:**
> why... did it need to be curl?



It doesn't, that is all I knew really.
I'll give it a go 
Cheers.

---

### Post by mobilediesel on 2009-12-20
Here's a *fairly* simple script to display a normal calendar with conky. It shows the last few days of the previous month as well as the first few days of the next month.

You can have the month/year line a different color and the days of the week line a different color.

```
#!/bin/bash
date=$(date '+%F')
DAY=${date:8:2}
DAY=${DAY/#0/}
cal=$(cal)
prev=$(cal $(date '+%-m %Y' --date="${date:0:7}-15 -1 month")|sed 's/ *$//;/^$/d'|tail -1)
next=$(cal $(date '+%-m %Y' --date="${date:0:7}-15 +1 month")|sed '/^ *&/d;1,2d;s/^ *//'|head -1)
if [ ${#next} == 19 ] ;then next=$'\n'"\${color9} $next"
else next="\${color9}  $next"
fi
if [ ${#prev} == 20 ]; then prev="$prev"$'\n '
else prev="$prev  "
fi
echo -e "\${color7}${cal:0:21}\${color4}${cal:21:21}\${color9}$prev\${color}$(echo "${cal:42}" | sed -e '/^ *$/d' -e 's/^/ /' -e 's/$/ /' -e 's/^ *1 / 1 /' -e /" $DAY "/s/" $DAY "/" "'${color3}'"$DAY"'${color}'" "/ -e 's/^ //' -e 's/ *$//')$next"
```
[ATTACH]140669[/ATTACH]

I did it this way to limit the number of calls to **cal** as I was calling it a few times. Now it's just 3. :)

---

### Post by guriinii on 2009-12-23
can I put an image on my conky from an RSS feed? For example: [http://xkcd.com/](http://xkcd.com/)

---

### Post by WorldTripping on 2009-12-23
OK, here is mine.

It determines whether or not there is a wi-fi connection present.

If there is it loads '.conkyLeftScreenWIFI.rc', if not it loads '.conkyLeftScreenNOFI.rc'.

Difference between the two conky files is one of layout and the variables they call (eg '.conkyLeftScreenNOFI.rc' does not look for the wireless address).

```

#!/bin/bash
sleep 15
	if ifconfig wlan0 | grep "inet addr"
		then
			conky -d -c /home/simon/.conkyLeftScreenWIFI.rc
			sleep 5
		else
			conky -d -c /home/simon/.conkyLeftScreenNOFI.rc
			sleep 5
	fi
conky -d -c /home/simon/.conkyBottomScreen.rc
sleep 5
conky -d -c /home/simon/.conkyRightScreen.rc
sleep 5
exit

```

Maybe someone can use this sometime.

WorldTripping.

---

### Post by mobilediesel on 2009-12-23
> **guriinii said:**
> can I put an image on my conky from an RSS feed? For example: [http://xkcd.com/](http://xkcd.com/)

Not neatly but this is functional:
```
${execi 7200 wget --quiet $(curl --silent 'http://xkcd.com/rss.xml'|grep -o 'src="[^"]*'|sed 's/src="//'|head -1) -O ~/conky/xkcd.png}
${image ~/conky/xkcd.png}
```

This isn't exactly elegant, someone please help make this purty!

---

### Post by dk75 on 2009-12-25
> **guriinii said:**
> can I put an image on my conky from an RSS feed? For example: [http://xkcd.com/](http://xkcd.com/)

conkyrc
```

background no
update_interval 14400
total_run_times 0
own_window yes
own_window_type override
own_window_transparent yes
own_window_colour black
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 637 205
maximum_width 637
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
stippled_borders 0
#border_inner_margin 0
#border_outer_margin 0
#border_width 0
default_color white
default_shade_color black
default_outline_color black
alignment bottom_left
gap_x 100
gap_y 100
no_buffers yes
uppercase no
override_utf8_locale yes
use_spacer right
max_port_monitor_connections 10
max_specials 64
max_user_text 64
imlib_cache_size 0
lua_load ~/.conky/lua/xkcd-rss.lua
lua_draw_hook_pre conky_main
TEXT

```


xkcd.lua
```

do
	require 'cairo'
	local http = require('socket.http')
	local url = 'http://xkcd.com/rss.xml'
	local comicW, comicH = 0, 0
	local CONKYRC = "/home/kitsune/.conky/.conkyrc-test19"

	function conky_cairo_window_hook()
		if conky_window == nil then return end
		if cs == nil or cairo_xlib_surface_get_width(cs) ~= conky_window.width or cairo_xlib_surface_get_height(cs) ~= conky_window.height then
			if cs then cairo_surface_destroy(cs) end
			cs = cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, conky_window.width, conky_window.height)
		end
		if cr then cairo_destroy(cr) end
		cr = cairo_create(cs)
	end

	function conky_main()
		conky_cairo_window_hook()
		if conky_window == nil then return end
		local w, h = conky_window.width, conky_window.height
		if w == nil or h == nil then return end
		
		local rss = http.request(url)
		rss = rss:gsub("><", ">\n<")
		for line in rss:gmatch("[^\r\n]+")
		do
			if line:match("^<description>.+img src+") then rss = line:gsub(".+src=\"", ""):gsub("\" title=.+", ""); break end
		end
		local img_tmp = http.request(rss)
		local out = assert(io.open("/tmp/comic_strip.png", "wb"))
		out:write(img_tmp)
		assert(out:close())
		
		local comic_strip = cairo_image_surface_create_from_png("/tmp/comic_strip.png")
		--[[comicW = cairo_image_surface_get_width(comic_strip)
		comicH = cairo_image_surface_get_height(comic_strip)
		
		if comicW ~= conky_window.width or comicH ~= conky_window.height then
			local tmp3 = ""
			local tmp = assert(io.open(CONKYRC, "r"))
			local tmp2 = tmp:read("*a")
			assert(tmp:close())
			for line in tmp2:gmatch("[^\r\n]+")
			do
				if line:match("^minimum_size") then tmp3 = tmp3 .. "minimum_size " .. comicW .. " " .. comicH .. "\n"
				elseif line:match("^maximum_width") then tmp3 = tmp3 .. "maximum_width " .. comicW .. "\n"
				else tmp3 = tmp3 .. line .. "\n" end
			end
			local tmp = assert(io.open(CONKYRC, "w"))
			tmp:write(tmp3)
			assert(tmp:close())
		end
		]]
		cairo_set_source_surface(cr, comic_strip, 0, 0)
		cairo_paint(cr)
	end
end
```

as you can see there is a code to resize Conky window and it actually works except for that it makes my conky window black for another Conky window update ( 4 hour at this conkyrc ) ](*,)

---

### Post by guriinii on 2009-12-28
Thank you so very much dk75 for making this for me, really impressed, not that I understand much of it. Now how do I get it to work?

I think I need them in separated files? I don't know how to use lua. Also is cairo a program I need. I'm out of my depth here, but I really want to learn this.

---

### Post by guriinii on 2009-12-28
> **mobilediesel said:**
> Not neatly but this is functional:
```
${execi 7200 wget --quiet $(curl --silent 'http://xkcd.com/rss.xml'|grep -o 'src="[^"]*'|sed 's/src="//'|head -1) -O ~/conky/xkcd.png}
${image ~/conky/xkcd.png}
```This isn't exactly elegant, someone please help make this purty!

This didn't work, I got this in terminal
```

richard@richard-desktop:/$ conky -c ~/Conky/conkyquote
Conky: forked to background, pid is 14615

richard@richard-desktop:/$ Conky: desktop window (18000aa) is subwindow of root window (f1)
Conky: window type - normal
Conky: drawing to created window (0x4200001)
Conky: drawing to double buffer
/home/richard/conky/xkcd.png: No such file or directory
Conky: not implemented obj type 44
Conky: not implemented obj type 44

```

---

### Post by slakkie on 2009-12-28
> **WorldTripping said:**
> OK, here is mine.

It determines whether or not there is a wi-fi connection present.

If there is it loads '.conkyLeftScreenWIFI.rc', if not it loads '.conkyLeftScreenNOFI.rc'.

Difference between the two conky files is one of layout and the variables they call (eg '.conkyLeftScreenNOFI.rc' does not look for the wireless address).

```

#!/bin/bash
sleep 15
	if ifconfig wlan0 | grep "inet addr"
		then
			conky -d -c /home/simon/.conkyLeftScreenWIFI.rc
			sleep 5
		else
			conky -d -c /home/simon/.conkyLeftScreenNOFI.rc
			sleep 5
	fi
conky -d -c /home/simon/.conkyBottomScreen.rc
sleep 5
conky -d -c /home/simon/.conkyRightScreen.rc
sleep 5
exit

```

Maybe someone can use this sometime.

WorldTripping.

I have something similar:

```

# In my lua script
function conky_show_net(int, desc, is_wlan)
    net_is = sprintf("${if_up %s}%s ", int, int);
    net_ip = sprintf("$alignr ${addrs %s}", int);
    net_not  = sprintf("${else}%s [%s] is not configured $endif", int, desc);
    net_graph="14,185";

    net_up_icon   = "${font PizzaDude Bullets:size=6}N${font}${voffset -2} ";
    net_up        = sprintf("${totalup %s}/${upspeed %s} $alignr ${upspeedgraph %s %s}", int, int, int, net_graph);
    net_up = net_up_icon .. net_up;

    net_down_icon = "${font PizzaDude Bullets:size=6}T${font}${voffset -2} ";
    net_down = sprintf("${totaldown %s}/${downspeed %s} $alignr ${downspeedgraph %s %s }", int, int, int, net_graph);
    net_down = net_down_icon .. net_down;

    if is_wlan == '1' then
        wifi_info = sprintf("${wireless_ap %s} $alignr ${wireless_bitrate %s}", int, int);
        wifi_ssid = sprintf("[${wireless_mode %s}] ${wireless_essid %s}", int, int);
        wifi_link = sprintf("${wireless_link_qual %s}/${wireless_link_qual_max %s}", int, int);
        wifi_perc = sprintf("${wireless_link_qual_perc %s}", int);
        wifi_bar  = sprintf("${wireless_link_bar %s}", int);

        net_info = sprintf("${alignc} %s $alignr %s\n%s ${alignr}%s %s%%\n%s\n",
        wifi_ssid, net_ip, wifi_info, wifi_link, wifi_perc, wifi_bar);
    else
        net_info = sprintf("%s $alignr %s\n", desc, net_ip);
    end
    return net_is .. net_info .. net_up .. "\n" .. net_down .. net_not;
end

```

```

# Conkyrc
${font Poky:size=12}w${font}${voffset -5} NETWORK ${hr 2}
${lua_parse show_net eth0 LAN 0}
${lua_parse show_net wlan0 WLAN 1}
${lua_parse show_net tun0 VPN 0}

```

And then this is the output:

[img]http://opperschaap.net/~wesleys/ubuntu/conky-nw.png[/img]

I have a similar function for disk mounts, which shows disk info or tells me something is not mounted.

---

### Post by mobilediesel on 2009-12-28
> **guriinii said:**
> This didn't work, I got this in terminal
```

richard@richard-desktop:/$ conky -c ~/Conky/conkyquote
Conky: forked to background, pid is 14615

richard@richard-desktop:/$ Conky: desktop window (18000aa) is subwindow of root window (f1)
Conky: window type - normal
Conky: drawing to created window (0x4200001)
Conky: drawing to double buffer
/home/richard/conky/xkcd.png: No such file or directory
Conky: not implemented obj type 44
Conky: not implemented obj type 44

```

It looks like it tried to show the picture before it was downloaded.

Try running this from a terminal before running conky:
```
curl --silent 'http://xkcd.com/rss.xml'|grep -o 'src="[^"]*'|sed 's/src="//'|head -1) -O ~/conky/xkcd.png
```
so it grabs a copy of the image first. Then there will be something for the ${image ~/conky/xkcd.png} to display.

---

### Post by guriinii on 2009-12-28
> **mobilediesel said:**
> 
Try running this from a terminal before running conky:
```
curl --silent 'http://xkcd.com/rss.xml'|grep -o 'src="[^"]*'|sed 's/src="//'|head -1) -O ~/conky/xkcd.png
```

Didn't work, I ran it and got this:
```

bash: syntax error near unexpected token `)'

```

Cheers for the very quick reply

---

### Post by mobilediesel on 2009-12-28
> **guriinii said:**
> Didn't work, I ran it and got this:
```

bash: syntax error near unexpected token `)'

```

Cheers for the very quick reply

Yeah I screwed up the copy and paste, try this:
```
wget --quiet $(curl --silent 'http://xkcd.com/rss.xml'|grep -o 'src="[^"]*'|sed 's/src="//'|head -1) -O ~/conky/xkcd.png
```

**Now** it will download the latest picture so that conky has something to display.

---

### Post by guriinii on 2009-12-28
Right, its downloaded the image and now its giving me this over and over until I kill conky:

```

Conky: not implemented obj type 44

```

---

### Post by mobilediesel on 2009-12-28
> **guriinii said:**
> Right, its downloaded the image and now its giving me this over and over until I kill conky:

```

Conky: not implemented obj type 44

```

Ah, what version of conky are you using? Run this in the terminal:
```
conky -V
```
You should see **Imlib2** in the output somewhere near the end. If not, you'll have to install a newer version of conky.

---

### Post by guriinii on 2009-12-28
I'm going to put my conky learning on hold for now. I need to do a fresh install of Jaunty, Karmic is p*ss*ng me off. I'll be back at some point.

---

### Post by Bruce M. on 2009-12-28
> **guriinii said:**
> I'm going to put my conky learning on hold for now. I need to do a fresh install of Jaunty, Karmic is p*ss*ng me off. I'll be back at some point.

Oh I know that feeling, I went from JJ to KK to #!.

#! at the moment (unless something happened in the last 8 days without Internet) is based on JJ v9.04.01 and OpenBox and is soooooooo slick! What can I say.

Have a nice day.
Bruce

---

### Post by guriinii on 2009-12-28
> **Bruce M. said:**
> Oh I know that feeling, I went from JJ to KK to #!.

#! at the moment (unless something happened in the last 8 days without Internet) is based on JJ v9.04.01 and OpenBox and is soooooooo slick! What can I say.

Have a nice day.
Bruce

What is #!

Enlighten me

---

### Post by dmillerct on 2009-12-28
> **guriinii said:**
> What is #!

Enlighten me

Crunch Bang Linux [http://crunchbanglinux.org/]("http://crunchbanglinux.org/")

I gave it a shot but did not care for it too much. Others swear by it.

---

### Post by mobilediesel on 2009-12-28
> **dmillerct said:**
> Crunch Bang Linux [http://crunchbanglinux.org/]("http://crunchbanglinux.org/")

I gave it a shot but did not care for it too much. Others swear by it.

Some swear by it, others swear AT it. :D

I've never tried it myself but I'll probably try that or Arch when I get another hard drive.

---

### Post by dmillerct on 2009-12-28
> **mobilediesel said:**
> Some swear by it, others swear AT it. :D

I've never tried it myself but I'll probably try that or Arch when I get another hard drive.

I know its off topic but you could use virtual box and try it without any regret.

---

### Post by mobilediesel on 2009-12-28
> **dmillerct said:**
> I know its off topic but you could use virtual box and try it without any regret.

I forgot about virtual box. I ran FreeDOS that way before just to mess with it. It ought to handle Crunchbang or Arch well enough.

and back on topic, the [calendar script]("http://ubuntuforums.org/showpost.php?p=8532568&postcount=9") I posted before can now highlight holidays and birthdays!
[ATTACH]141491[/ATTACH]
```
date=$(date '+%F')
DAY=${date:8:2}
DAY=${DAY/#0/}
cal=$(cal)
prev=$(cal $(date '+%-m %Y' --date="${date:0:7}-15 -1 month")|sed 's/ *$//;/^$/d'|tail -1)
next=$(cal $(date '+%-m %Y' --date="${date:0:7}-15 +1 month")|sed '/^ *&/d;1,2d;s/^ *//'|head -1)
if [ ${#next} == 19 ] ;then next=$'\n'"\${color9} $next"
else next="\${color9}  $next"
fi
if [ ${#prev} == 20 ]; then prev="$prev"$'\n '
else prev="$prev  "
fi
dates=$(remind -s|cut -d ' ' -f1|uniq|cut -d '/' -f3[COLOR="Blue"]|sed "/$DAY/d"[/COLOR])
current=$(echo "${cal:42}"|sed -e '/^ *$/d' -e 's/^/ /' -e 's/$/ /' -e 's/^ *1 / 1 /' )
for i in $dates; do
current=$(echo "$current"|sed -e /" ${i/#0/} "/s/" ${i/#0/} "/" "'${color green}'"${i/#0/}"'${color}'" "/)
done
current=$(echo "$current"|sed -e /" $DAY "/s/" $DAY "/" "'${color3}'"$DAY"'${color}'" "/ -e 's/^ //' -e 's/ *$//')
echo -e "\${color7}${cal:0:21}\${color4}${cal:21:21}\${color9}$prev\${color}$current$next"
```

[COLOR="Blue"]|sed "/$DAY/d"[/COLOR] was added so that the current day will still get colored white.

to get the dates for holidays, I use **[remind]("http://wiki.43folders.com/index.php/Remind")** along with a file I found [here]("http://wiki.43folders.com/index.php/User:JamesRifkin/defs.rem") that has the U.S. holidays as well as Jewish holidays.

If you use this script to win the [Conky of the Month]("http://blog.conky.be/2009/12/16/the-lines-are-now-closed/") be sure to mention me! The theme for this one is calendars! This script should be useful.

You can also go to [http://dl.dropbox.com/u/1055489/mobilediesel/index.html](http://dl.dropbox.com/u/1055489/mobilediesel/index.html)
to see various scripts I use with conky. That's only a list of scripts. They're each small enough that they should be easy enough to see what they do. I'll have to get a proper description of them all on there and here.

I also wrote a small script that keeps [http://dl.dropbox.com/u/1055489/mobilediesel/index.html](http://dl.dropbox.com/u/1055489/mobilediesel/index.html) up to date with whatever code I come up with for conky.

---

### Post by markp1989 on 2009-12-28
> **mobilediesel said:**
> Excellent idea! I wish **I'd** thought of it!
 as a reply to one of your [posts]("http://ubuntuforums.org/showpost.php?p=8520172&postcount=11069") in the [conky mega-thread]("http://ubuntuforums.org/showthread.php?t=281865"):

[BASH Beginner's Guide]("http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html")
and
[Writing Shell Scripts]("http://linuxcommand.org/writing_shell_scripts.php")

and this script I'll post here isn't even mine:
[conky-rss.sh]("http://dl.dropbox.com/u/1055489/scripts/conky-rss.sh")
```
#!/bin/bash
# RSS Display Script by Bill Woodford (admin@sdesign.us) v1.0
#
#RSS Setup - Don't change unless you want these values hard-coded!
uri=$1                                                  #URI of RSS Feed
lines=$2                                                #Number of headlines
titlenum=$3                                             #Number of extra titles
#Script start
#Require a uri, as a minimum
if [[ "$uri" == "" ]]; then
        echo "No URI specified, cannot continue!" >&2
        echo "Please read script for more information" >&2
else
        #Set defaults if none specified
        if [[ $lines == "" ]]; then lines=25 ; fi
        if [[ $titlenum == "" ]]; then titlenum=2 ; fi

        #The actual work
        curl -A "Mozilla/5.0" -s --connect-timeout 30 $uri |\
        grep -io "<title>[^<]*"|\
        sed -e 's/<[^>]*>//'|\
        head -n $(($lines + $titlenum)) |\
        tail -n $(($lines))
fi
```

thanks , i took parts of your script and threw this together to work with dzen2 , hope you dont mind.



```

#!/bin/bash 
FG='#ffffff'
BG='#000000'
#FONT='-*-terminus-*-r-normal-*-*-120-*-*-*-*-iso8859-*'
while true ; do
url=http://www.harrowtimes.co.uk/news/rss/                             #URl of RSS Feed
lines=4                                           #Number of headlines
titlenum=2
newsrss=`curl -A "Mozilla/5.0" -s --connect-timeout 30 $url | grep -io "<title>[^<]*"| sed -e 's/<[^>]*>//'| head -n $(($lines + $titlenum)) | tail -n $(($lines))|tr '\n' ':'`

    printf "%s\n" "$newsrss"
    sleep 20
done | dzen2 -e '' -y '885' -h '15' -sa 'r'  -ta c -fg $FG -bg $BG -fn $FONT

```

the y value will have to be changed depending on the size of your screen (mine is set to go across the bottom of a screen 900px high)

---

### Post by mobilediesel on 2009-12-28
> **markp1989 said:**
> thanks , i took parts of your script and threw this together to work with dzen2 , hope you dont mind.

the y value will have to be changed depending on the size of your screen (mine is set to go across the bottom of a screen 900px high)

I don't mind at all! I haven't heard of dzen2. That'll be neat to play with.

---

### Post by WorldTripping on 2009-12-28
> **Bruce M. said:**
> Oh I know that feeling, I went from JJ to KK to #!.

#! at the moment (unless something happened in the last 8 days without Internet) is based on JJ v9.04.01 and OpenBox and is soooooooo slick! What can I say.

Have a nice day.
Bruce

Hey Bruce,

Many Happy Returns !

I'm afraid that I'm in the same boat.

Went from ubuntu kk back to #! jj.

kk would not recognise my USB GSM dongle or my USB GPS and it was easier to revert than figure it out (my problem I know) !

Started with a minimal install (just terminal apps that I used for a week or two) before I started to add all of the X apps that I needed.

(Must say that I got quite use to using elinks as a web browser.)

The only thing that I don't like about #! is the lack of an encrypted lvm as I always used to install via the 'alternate CD' and opt for that. Guess that I'll have to investigate how to do that using LUKS etc. post install.

Gotta say though that #! with all its simplicity and speed; combined with the ability to configure openbox ad infinitum, with all of the Ubuntu repos is the the happiest that I've felt with a distro for a while.

Obligatory screenshot attached.

---

### Post by WorldTripping on 2009-12-29
> **dmillerct said:**
> Crunch Bang Linux [http://crunchbanglinux.org/]("http://crunchbanglinux.org/")

I gave it a shot but did not care for it too much. Others swear by it.

Having spent a week with it I guess that I fall into that camp.

Must admit though that I like tinkering and the thought of a completely (terminal apps only) install that I then add to, with the backing of all the repos that I'm used to appeals to me.

But hey, I've not stopped messing with conky for the last few years so why would I stop being a distro whore. :)

(loving #! tho !)

---

### Post by Bruce M. on 2009-12-29
**Off Topic**
> **guriinii said:**
> What is #!

Enlighten me

Ok, by now you've seen dmillerct's comment, below.  See my desktop below as well.  :)

> **dmillerct said:**
> Crunch Bang Linux [http://crunchbanglinux.org/]("http://crunchbanglinux.org/")

I gave it a shot but did not care for it too much. Others swear by it.

I'm one of them, but I don't use bad words, just good words to describe #!.  One has to like OpenBox to like Crunchbang.  And I really do like it.

> **mobilediesel said:**
> Some swear by it, others swear AT it. :D

Bite your tongue. :lolflag:

**On Topic!**
Now to continue:

On Conky Hardcore! there is a script by TeoBigusGeekus to get weather from [Weather Underground]("http://conky.linux-hardcore.com/?page_id=2381") - and I'm playing with it.  It looks like it's set up for 5, 7 or 9 days. and uses "fake" files to determine what one downloads.

Anyway the script is: **wunderground-script.sh** (so I call it):
```
#!/bin/bash
wget -O ~/conky_wunderground/ics1 http://ical.wunderground.com/auto/ical/global/stations/87582.ics?units=metric
sed  's/\./\n/g' ~/conky_wunderground/ics1 > ~/conky_wunderground/ics
egrep -i 'description|monday|tuesday|wednesday|thursday|friday|saturday|sunday|high|low|wind' ~/conky_wunderground/ics >~/conky_wunderground/messages.wun
sed -i 's/DESCRIPTION://g' ~/conky_wunderground/messages.wun
sed -i 's/\\n/\n/g' ~/conky_wunderground/messages.wun
sed -i 's/ - /\n/g' ~/conky_wunderground/messages.wun
sed -i 's/High/\nHigh/g' ~/conky_wunderground/messages.wun
sed -i 's/Low/\nLow/g' ~/conky_wunderground/messages.wun
cp ~/conky_wunderground/messages.wun ~/conky_wunderground/temp1.wun
sed -i 's/Wind /\n/g' ~/conky_wunderground/messages.wun
sed -i '/^ /d' ~/conky_wunderground/messages.wun
sed -i '/^$/d' ~/conky_wunderground/messages.wun
sed -i 's/Wind/\nWind/g' ~/conky_wunderground/temp1.wun
sed -i 's/\./\n/g' ~/conky_wunderground/temp1.wun
grep -i Wind ~/conky_wunderground/temp1.wun>~/conky_wunderground/wind-icons-messages.wun
sed -i 's/Wind //g' ~/conky_wunderground/wind-icons-messages.wun
sed -i 's/ km\/h//g' ~/conky_wunderground/wind-icons-messages.wun
cut -c1-3 ~/conky_wunderground/wind-icons-messages.wun >~/conky_wunderground/icons.wun
rm ~/conky_wunderground/14
rm ~/conky_wunderground/13
rm ~/conky_wunderground/12
a=`sed -n '$=' ~/conky_wunderground/wind-icons-messages.wun`
if  [ $a -eq "13" ];
then sed -i '1s/^/Today\n   -\n       -                \n        -                \n/' ~/conky_wunderground/messages.wun
sed -i '1s/^/\n/' ~/conky_wunderground/icons.wun
echo $a>~/conky_wunderground/13
elif [ $a -eq "12" ];
then sed -i '12s/$/\n\n/' ~/conky_wunderground/icons.wun
sed -i '48s/$/\n\n   -\n       -                \n        -                \n\n   -\n       -                \n        -                \n/' ~/conky_wunderground/messages.wun
echo $a>~/conky_wunderground/12
elif [ $a -eq "14" ];
then echo $a>~/conky_wunderground/14
fi;
a=`sed -n '2p' ~/conky_wunderground/messages.wun`
if test "$a" = "Chance of Flurries"
then sed -i '14s/$/\np/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Rain"
then sed -i '14s/$/\nh/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Freezing Rain"
then sed -i '14s/$/\nv/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Sleet"
then sed -i '14s/$/\nw/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Snow"
then sed -i '14s/$/\nq/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Thunderstorms"
then sed -i '14s/$/\nn/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of a Thunderstorm"
then sed -i '14s/$/\nm/' ~/conky_wunderground/icons.wun
elif test "$a" = "Clear"
then sed -i '14s/$/\na/' ~/conky_wunderground/icons.wun
elif test "$a" = "Cloudy"
then sed -i '14s/$/\nd/' ~/conky_wunderground/icons.wun
elif test "$a" = "Flurries"
then sed -i '14s/$/\np/' ~/conky_wunderground/icons.wun
elif test "$a" = "Fog"
then sed -i '14s/$/\n0/' ~/conky_wunderground/icons.wun
elif test "$a" = "Hazy"
then sed -i '14s/$/\n0/' ~/conky_wunderground/icons.wun
elif test "$a" = "Mostly Cloudy"
then sed -i '14s/$/\nc/' ~/conky_wunderground/icons.wun
elif test "$a" = "Mostly Sunny"
then sed -i '14s/$/\nb/' ~/conky_wunderground/icons.wun
elif test "$a" = "Partly Cloudy"
then sed -i '14s/$/\nc/' ~/conky_wunderground/icons.wun
elif test "$a" = "Partly Sunny"
then sed -i '14s/$/\nc/' ~/conky_wunderground/icons.wun
elif test "$a" = "Freezing Rain"
then sed -i '14s/$/\nv/' ~/conky_wunderground/icons.wun
elif test "$a" = "Rain"
then sed -i '14s/$/\ni/' ~/conky_wunderground/icons.wun
elif test "$a" = "Sleet"
then sed -i '14s/$/\nw/' ~/conky_wunderground/icons.wun
elif test "$a" = "Snow"
then sed -i '14s/$/\nr/' ~/conky_wunderground/icons.wun
elif test "$a" = "Sunny"
then sed -i '14s/$/\na/' ~/conky_wunderground/icons.wun
elif test "$a" = "Thunderstorms" || test "$a" = "Thunderstorm"
then sed -i '14s/$/\nn/' ~/conky_wunderground/icons.wun
elif test "$a" = "Overcast"
then sed -i '14s/$/\ne/' ~/conky_wunderground/icons.wun
elif test "$a" = "Scattered Clouds"
then sed -i '14s/$/\nb/' ~/conky_wunderground/icons.wun
else sed -i '14s/$/\n-/' ~/conky_wunderground/icons.wun
fi;
a=`sed -n '6p' ~/conky_wunderground/messages.wun`
if test "$a" = "Chance of Flurries"
then sed -i '15s/$/\nO/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Rain"
then sed -i '15s/$/\nG/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Freezing Rain"
then sed -i '15s/$/\nG/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Sleet"
then sed -i '15s/$/\nG/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Snow"
then sed -i '15s/$/\nO/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Thunderstorms"
then sed -i '15s/$/\nK/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of a Thunderstorm"
then sed -i '15s/$/\nK/' ~/conky_wunderground/icons.wun
elif test "$a" = "Clear"
then sed -i '15s/$/\nA/' ~/conky_wunderground/icons.wun
elif test "$a" = "Cloudy"
then sed -i '15s/$/\nD/' ~/conky_wunderground/icons.wun
elif test "$a" = "Flurries"
then sed -i '15s/$/\nO/' ~/conky_wunderground/icons.wun
elif test "$a" = "Fog"
then sed -i '15s/$/\n0/' ~/conky_wunderground/icons.wun
elif test "$a" = "Hazy"
then sed -i '15s/$/\n0/' ~/conky_wunderground/icons.wun
elif test "$a" = "Mostly Cloudy"
then sed -i '15s/$/\nC/' ~/conky_wunderground/icons.wun
elif test "$a" = "Mostly Sunny"
then sed -i '15s/$/\nB/' ~/conky_wunderground/icons.wun
elif test "$a" = "Partly Cloudy"
then sed -i '15s/$/\nC/' ~/conky_wunderground/icons.wun
elif test "$a" = "Partly Sunny"
then sed -i '15s/$/\nC/' ~/conky_wunderground/icons.wun
elif test "$a" = "Freezing Rain"
then sed -i '15s/$/\nG/' ~/conky_wunderground/icons.wun
elif test "$a" = "Rain"
then sed -i '15s/$/\nG/' ~/conky_wunderground/icons.wun
elif test "$a" = "Sleet"
then sed -i '15s/$/\nG/' ~/conky_wunderground/icons.wun
elif test "$a" = "Snow"
then sed -i '15s/$/\nO/' ~/conky_wunderground/icons.wun
elif test "$a" = "Sunny"
then sed -i '15s/$/\nA/' ~/conky_wunderground/icons.wun
elif test "$a" = "Thunderstorms" || test "$a" = "Thunderstorm"
then sed -i '15s/$/\nK/' ~/conky_wunderground/icons.wun
elif test "$a" = "Overcast"
then sed -i '15s/$/\nD/' ~/conky_wunderground/icons.wun
elif test "$a" = "Scattered Clouds"
then sed -i '15s/$/\nB/' ~/conky_wunderground/icons.wun
else sed -i '15s/$/\n-/' ~/conky_wunderground/icons.wun
fi;
a=`sed -n '10p' ~/conky_wunderground/messages.wun`
if test "$a" = "Chance of Flurries"
then sed -i '16s/$/\np/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Rain"
then sed -i '16s/$/\nh/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Freezing Rain"
then sed -i '16s/$/\nv/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Sleet"
then sed -i '16s/$/\nw/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Snow"
then sed -i '16s/$/\nq/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Thunderstorms"
then sed -i '16s/$/\nn/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of a Thunderstorm"
then sed -i '16s/$/\nm/' ~/conky_wunderground/icons.wun
elif test "$a" = "Clear"
then sed -i '16s/$/\na/' ~/conky_wunderground/icons.wun
elif test "$a" = "Cloudy"
then sed -i '16s/$/\nd/' ~/conky_wunderground/icons.wun
elif test "$a" = "Flurries"
then sed -i '16s/$/\np/' ~/conky_wunderground/icons.wun
elif test "$a" = "Fog"
then sed -i '16s/$/\n0/' ~/conky_wunderground/icons.wun
elif test "$a" = "Hazy"
then sed -i '16s/$/\n0/' ~/conky_wunderground/icons.wun
elif test "$a" = "Mostly Cloudy"
then sed -i '16s/$/\nc/' ~/conky_wunderground/icons.wun
elif test "$a" = "Mostly Sunny"
then sed -i '16s/$/\nb/' ~/conky_wunderground/icons.wun
elif test "$a" = "Partly Cloudy"
then sed -i '16s/$/\nc/' ~/conky_wunderground/icons.wun
elif test "$a" = "Partly Sunny"
then sed -i '16s/$/\nc/' ~/conky_wunderground/icons.wun
elif test "$a" = "Freezing Rain"
then sed -i '16s/$/\nv/' ~/conky_wunderground/icons.wun
elif test "$a" = "Rain"
then sed -i '16s/$/\ni/' ~/conky_wunderground/icons.wun
elif test "$a" = "Sleet"
then sed -i '16s/$/\nw/' ~/conky_wunderground/icons.wun
elif test "$a" = "Snow"
then sed -i '16s/$/\nr/' ~/conky_wunderground/icons.wun
elif test "$a" = "Sunny"
then sed -i '16s/$/\na/' ~/conky_wunderground/icons.wun
elif test "$a" = "Thunderstorms" || test "$a" = "Thunderstorm"
then sed -i '16s/$/\nn/' ~/conky_wunderground/icons.wun
elif test "$a" = "Overcast"
then sed -i '16s/$/\ne/' ~/conky_wunderground/icons.wun
elif test "$a" = "Scattered Clouds"
then sed -i '16s/$/\nb/' ~/conky_wunderground/icons.wun
else sed -i '16s/$/\n-/' ~/conky_wunderground/icons.wun
fi;
a=`sed -n '14p' ~/conky_wunderground/messages.wun`
if test "$a" = "Chance of Flurries"
then sed -i '17s/$/\nO/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Rain"
then sed -i '17s/$/\nG/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Freezing Rain"
then sed -i '17s/$/\nG/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Sleet"
then sed -i '17s/$/\nG/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Snow"
then sed -i '17s/$/\nO/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Thunderstorms"
then sed -i '17s/$/\nK/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of a Thunderstorm"
then sed -i '17s/$/\nK/' ~/conky_wunderground/icons.wun
elif test "$a" = "Clear"
then sed -i '17s/$/\nA/' ~/conky_wunderground/icons.wun
elif test "$a" = "Cloudy"
then sed -i '17s/$/\nD/' ~/conky_wunderground/icons.wun
elif test "$a" = "Flurries"
then sed -i '17s/$/\nO/' ~/conky_wunderground/icons.wun
elif test "$a" = "Fog"
then sed -i '17s/$/\n0/' ~/conky_wunderground/icons.wun
elif test "$a" = "Hazy"
then sed -i '17s/$/\n0/' ~/conky_wunderground/icons.wun
elif test "$a" = "Mostly Cloudy"
then sed -i '17s/$/\nC/' ~/conky_wunderground/icons.wun
elif test "$a" = "Mostly Sunny"
then sed -i '17s/$/\nB/' ~/conky_wunderground/icons.wun
elif test "$a" = "Partly Cloudy"
then sed -i '17s/$/\nC/' ~/conky_wunderground/icons.wun
elif test "$a" = "Partly Sunny"
then sed -i '17s/$/\nC/' ~/conky_wunderground/icons.wun
elif test "$a" = "Freezing Rain"
then sed -i '17s/$/\nG/' ~/conky_wunderground/icons.wun
elif test "$a" = "Rain"
then sed -i '17s/$/\nG/' ~/conky_wunderground/icons.wun
elif test "$a" = "Sleet"
then sed -i '17s/$/\nG/' ~/conky_wunderground/icons.wun
elif test "$a" = "Snow"
then sed -i '17s/$/\nO/' ~/conky_wunderground/icons.wun
elif test "$a" = "Sunny"
then sed -i '17s/$/\nA/' ~/conky_wunderground/icons.wun
elif test "$a" = "Thunderstorms" || test "$a" = "Thunderstorm"
then sed -i '17s/$/\nK/' ~/conky_wunderground/icons.wun
elif test "$a" = "Overcast"
then sed -i '17s/$/\nD/' ~/conky_wunderground/icons.wun
elif test "$a" = "Scattered Clouds"
then sed -i '17s/$/\nB/' ~/conky_wunderground/icons.wun
else sed -i '17s/$/\n-/' ~/conky_wunderground/icons.wun
fi;
a=`sed -n '18p' ~/conky_wunderground/messages.wun`
if test "$a" = "Chance of Flurries"
then sed -i '18s/$/\np/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Rain"
then sed -i '18s/$/\nh/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Freezing Rain"
then sed -i '18s/$/\nv/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Sleet"
then sed -i '18s/$/\nw/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Snow"
then sed -i '18s/$/\nq/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Thunderstorms"
then sed -i '18s/$/\nn/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of a Thunderstorm"
then sed -i '18s/$/\nm/' ~/conky_wunderground/icons.wun
elif test "$a" = "Clear"
then sed -i '18s/$/\na/' ~/conky_wunderground/icons.wun
elif test "$a" = "Cloudy"
then sed -i '18s/$/\nd/' ~/conky_wunderground/icons.wun
elif test "$a" = "Flurries"
then sed -i '18s/$/\np/' ~/conky_wunderground/icons.wun
elif test "$a" = "Fog"
then sed -i '18s/$/\n0/' ~/conky_wunderground/icons.wun
elif test "$a" = "Hazy"
then sed -i '18s/$/\n0/' ~/conky_wunderground/icons.wun
elif test "$a" = "Mostly Cloudy"
then sed -i '18s/$/\nc/' ~/conky_wunderground/icons.wun
elif test "$a" = "Mostly Sunny"
then sed -i '18s/$/\nb/' ~/conky_wunderground/icons.wun
elif test "$a" = "Partly Cloudy"
then sed -i '18s/$/\nc/' ~/conky_wunderground/icons.wun
elif test "$a" = "Partly Sunny"
then sed -i '18s/$/\nc/' ~/conky_wunderground/icons.wun
elif test "$a" = "Freezing Rain"
then sed -i '18s/$/\nv/' ~/conky_wunderground/icons.wun
elif test "$a" = "Rain"
then sed -i '18s/$/\ni/' ~/conky_wunderground/icons.wun
elif test "$a" = "Sleet"
then sed -i '18s/$/\nw/' ~/conky_wunderground/icons.wun
elif test "$a" = "Snow"
then sed -i '18s/$/\nr/' ~/conky_wunderground/icons.wun
elif test "$a" = "Sunny"
then sed -i '18s/$/\na/' ~/conky_wunderground/icons.wun
elif test "$a" = "Thunderstorms" || test "$a" = "Thunderstorm"
then sed -i '18s/$/\nn/' ~/conky_wunderground/icons.wun
elif test "$a" = "Overcast"
then sed -i '18s/$/\ne/' ~/conky_wunderground/icons.wun
elif test "$a" = "Scattered Clouds"
then sed -i '18s/$/\nb/' ~/conky_wunderground/icons.wun
else sed -i '18s/$/\n-/' ~/conky_wunderground/icons.wun
fi;
a=`sed -n '22p' ~/conky_wunderground/messages.wun`
if test "$a" = "Chance of Flurries"
then sed -i '19s/$/\nO/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Rain"
then sed -i '19s/$/\nG/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Freezing Rain"
then sed -i '19s/$/\nG/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Sleet"
then sed -i '19s/$/\nG/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Snow"
then sed -i '19s/$/\nO/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Thunderstorms"
then sed -i '19s/$/\nK/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of a Thunderstorm"
then sed -i '19s/$/\nK/' ~/conky_wunderground/icons.wun
elif test "$a" = "Clear"
then sed -i '19s/$/\nA/' ~/conky_wunderground/icons.wun
elif test "$a" = "Cloudy"
then sed -i '19s/$/\nD/' ~/conky_wunderground/icons.wun
elif test "$a" = "Flurries"
then sed -i '19s/$/\nO/' ~/conky_wunderground/icons.wun
elif test "$a" = "Fog"
then sed -i '19s/$/\n0/' ~/conky_wunderground/icons.wun
elif test "$a" = "Hazy"
then sed -i '19s/$/\n0/' ~/conky_wunderground/icons.wun
elif test "$a" = "Mostly Cloudy"
then sed -i '19s/$/\nC/' ~/conky_wunderground/icons.wun
elif test "$a" = "Mostly Sunny"
then sed -i '19s/$/\nB/' ~/conky_wunderground/icons.wun
elif test "$a" = "Partly Cloudy"
then sed -i '19s/$/\nC/' ~/conky_wunderground/icons.wun
elif test "$a" = "Partly Sunny"
then sed -i '19s/$/\nC/' ~/conky_wunderground/icons.wun
elif test "$a" = "Freezing Rain"
then sed -i '19s/$/\nG/' ~/conky_wunderground/icons.wun
elif test "$a" = "Rain"
then sed -i '19s/$/\nG/' ~/conky_wunderground/icons.wun
elif test "$a" = "Sleet"
then sed -i '19s/$/\nG/' ~/conky_wunderground/icons.wun
elif test "$a" = "Snow"
then sed -i '19s/$/\nO/' ~/conky_wunderground/icons.wun
elif test "$a" = "Sunny"
then sed -i '19s/$/\nA/' ~/conky_wunderground/icons.wun
elif test "$a" = "Thunderstorms" || test "$a" = "Thunderstorm"
then sed -i '19s/$/\nK/' ~/conky_wunderground/icons.wun
elif test "$a" = "Overcast"
then sed -i '19s/$/\nD/' ~/conky_wunderground/icons.wun
elif test "$a" = "Scattered Clouds"
then sed -i '19s/$/\nB/' ~/conky_wunderground/icons.wun
else sed -i '19s/$/\n-/' ~/conky_wunderground/icons.wun
fi;
a=`sed -n '26p' ~/conky_wunderground/messages.wun`
if test "$a" = "Chance of Flurries"
then sed -i '20s/$/\np/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Rain"
then sed -i '20s/$/\nh/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Freezing Rain"
then sed -i '20s/$/\nv/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Sleet"
then sed -i '20s/$/\nw/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Snow"
then sed -i '20s/$/\nq/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Thunderstorms"
then sed -i '20s/$/\nn/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of a Thunderstorm"
then sed -i '20s/$/\nm/' ~/conky_wunderground/icons.wun
elif test "$a" = "Clear"
then sed -i '20s/$/\na/' ~/conky_wunderground/icons.wun
elif test "$a" = "Cloudy"
then sed -i '20s/$/\nd/' ~/conky_wunderground/icons.wun
elif test "$a" = "Flurries"
then sed -i '20s/$/\np/' ~/conky_wunderground/icons.wun
elif test "$a" = "Fog"
then sed -i '20s/$/\n0/' ~/conky_wunderground/icons.wun
elif test "$a" = "Hazy"
then sed -i '20s/$/\n0/' ~/conky_wunderground/icons.wun
elif test "$a" = "Mostly Cloudy"
then sed -i '20s/$/\nc/' ~/conky_wunderground/icons.wun
elif test "$a" = "Mostly Sunny"
then sed -i '20s/$/\nb/' ~/conky_wunderground/icons.wun
elif test "$a" = "Partly Cloudy"
then sed -i '20s/$/\nc/' ~/conky_wunderground/icons.wun
elif test "$a" = "Partly Sunny"
then sed -i '20s/$/\nc/' ~/conky_wunderground/icons.wun
elif test "$a" = "Freezing Rain"
then sed -i '20s/$/\nv/' ~/conky_wunderground/icons.wun
elif test "$a" = "Rain"
then sed -i '20s/$/\ni/' ~/conky_wunderground/icons.wun
elif test "$a" = "Sleet"
then sed -i '20s/$/\nw/' ~/conky_wunderground/icons.wun
elif test "$a" = "Snow"
then sed -i '20s/$/\nr/' ~/conky_wunderground/icons.wun
elif test "$a" = "Sunny"
then sed -i '20s/$/\na/' ~/conky_wunderground/icons.wun
elif test "$a" = "Thunderstorms" || test "$a" = "Thunderstorm"
then sed -i '20s/$/\nn/' ~/conky_wunderground/icons.wun
elif test "$a" = "Overcast"
then sed -i '20s/$/\ne/' ~/conky_wunderground/icons.wun
elif test "$a" = "Scattered Clouds"
then sed -i '20s/$/\nb/' ~/conky_wunderground/icons.wun
else sed -i '20s/$/\n-/' ~/conky_wunderground/icons.wun
fi;
a=`sed -n '30p' ~/conky_wunderground/messages.wun`
if test "$a" = "Chance of Flurries"
then sed -i '21s/$/\nO/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Rain"
then sed -i '21s/$/\nG/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Freezing Rain"
then sed -i '21s/$/\nG/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Sleet"
then sed -i '21s/$/\nG/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Snow"
then sed -i '21s/$/\nO/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Thunderstorms"
then sed -i '21s/$/\nK/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of a Thunderstorm"
then sed -i '21s/$/\nK/' ~/conky_wunderground/icons.wun
elif test "$a" = "Clear"
then sed -i '21s/$/\nA/' ~/conky_wunderground/icons.wun
elif test "$a" = "Cloudy"
then sed -i '21s/$/\nD/' ~/conky_wunderground/icons.wun
elif test "$a" = "Flurries"
then sed -i '21s/$/\nO/' ~/conky_wunderground/icons.wun
elif test "$a" = "Fog"
then sed -i '21s/$/\n0/' ~/conky_wunderground/icons.wun
elif test "$a" = "Hazy"
then sed -i '21s/$/\n0/' ~/conky_wunderground/icons.wun
elif test "$a" = "Mostly Cloudy"
then sed -i '21s/$/\nC/' ~/conky_wunderground/icons.wun
elif test "$a" = "Mostly Sunny"
then sed -i '21s/$/\nB/' ~/conky_wunderground/icons.wun
elif test "$a" = "Partly Cloudy"
then sed -i '21s/$/\nC/' ~/conky_wunderground/icons.wun
elif test "$a" = "Partly Sunny"
then sed -i '21s/$/\nC/' ~/conky_wunderground/icons.wun
elif test "$a" = "Freezing Rain"
then sed -i '21s/$/\nG/' ~/conky_wunderground/icons.wun
elif test "$a" = "Rain"
then sed -i '21s/$/\nG/' ~/conky_wunderground/icons.wun
elif test "$a" = "Sleet"
then sed -i '21s/$/\nG/' ~/conky_wunderground/icons.wun
elif test "$a" = "Snow"
then sed -i '21s/$/\nO/' ~/conky_wunderground/icons.wun
elif test "$a" = "Sunny"
then sed -i '21s/$/\nA/' ~/conky_wunderground/icons.wun
elif test "$a" = "Thunderstorms" || test "$a" = "Thunderstorm"
then sed -i '21s/$/\nK/' ~/conky_wunderground/icons.wun
elif test "$a" = "Overcast"
then sed -i '21s/$/\nD/' ~/conky_wunderground/icons.wun
elif test "$a" = "Scattered Clouds"
then sed -i '21s/$/\nB/' ~/conky_wunderground/icons.wun
else sed -i '21s/$/\n-/' ~/conky_wunderground/icons.wun
fi;
a=`sed -n '34p' ~/conky_wunderground/messages.wun`
if test "$a" = "Chance of Flurries"
then sed -i '22s/$/\np/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Rain"
then sed -i '22s/$/\nh/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Freezing Rain"
then sed -i '22s/$/\nv/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Sleet"
then sed -i '22s/$/\nw/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Snow"
then sed -i '22s/$/\nq/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Thunderstorms"
then sed -i '22s/$/\nn/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of a Thunderstorm"
then sed -i '22s/$/\nm/' ~/conky_wunderground/icons.wun
elif test "$a" = "Clear"
then sed -i '22s/$/\na/' ~/conky_wunderground/icons.wun
elif test "$a" = "Cloudy"
then sed -i '22s/$/\nd/' ~/conky_wunderground/icons.wun
elif test "$a" = "Flurries"
then sed -i '22s/$/\np/' ~/conky_wunderground/icons.wun
elif test "$a" = "Fog"
then sed -i '22s/$/\n0/' ~/conky_wunderground/icons.wun
elif test "$a" = "Hazy"
then sed -i '22s/$/\n0/' ~/conky_wunderground/icons.wun
elif test "$a" = "Mostly Cloudy"
then sed -i '22s/$/\nc/' ~/conky_wunderground/icons.wun
elif test "$a" = "Mostly Sunny"
then sed -i '22s/$/\nb/' ~/conky_wunderground/icons.wun
elif test "$a" = "Partly Cloudy"
then sed -i '22s/$/\nc/' ~/conky_wunderground/icons.wun
elif test "$a" = "Partly Sunny"
then sed -i '22s/$/\nc/' ~/conky_wunderground/icons.wun
elif test "$a" = "Freezing Rain"
then sed -i '22s/$/\nv/' ~/conky_wunderground/icons.wun
elif test "$a" = "Rain"
then sed -i '22s/$/\ni/' ~/conky_wunderground/icons.wun
elif test "$a" = "Sleet"
then sed -i '22s/$/\nw/' ~/conky_wunderground/icons.wun
elif test "$a" = "Snow"
then sed -i '22s/$/\nr/' ~/conky_wunderground/icons.wun
elif test "$a" = "Sunny"
then sed -i '22s/$/\na/' ~/conky_wunderground/icons.wun
elif test "$a" = "Thunderstorms" || test "$a" = "Thunderstorm"
then sed -i '22s/$/\nn/' ~/conky_wunderground/icons.wun
elif test "$a" = "Overcast"
then sed -i '22s/$/\ne/' ~/conky_wunderground/icons.wun
elif test "$a" = "Scattered Clouds"
then sed -i '22s/$/\nb/' ~/conky_wunderground/icons.wun
else sed -i '22s/$/\n-/' ~/conky_wunderground/icons.wun
fi;
a=`sed -n '38p' ~/conky_wunderground/messages.wun`
if test "$a" = "Chance of Flurries"
then sed -i '23s/$/\nO/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Rain"
then sed -i '23s/$/\nG/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Freezing Rain"
then sed -i '23s/$/\nG/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Sleet"
then sed -i '23s/$/\nG/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Snow"
then sed -i '23s/$/\nO/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Thunderstorms"
then sed -i '23s/$/\nK/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of a Thunderstorm"
then sed -i '23s/$/\nK/' ~/conky_wunderground/icons.wun
elif test "$a" = "Clear"
then sed -i '23s/$/\nA/' ~/conky_wunderground/icons.wun
elif test "$a" = "Cloudy"
then sed -i '23s/$/\nD/' ~/conky_wunderground/icons.wun
elif test "$a" = "Flurries"
then sed -i '23s/$/\nO/' ~/conky_wunderground/icons.wun
elif test "$a" = "Fog"
then sed -i '23s/$/\n0/' ~/conky_wunderground/icons.wun
elif test "$a" = "Hazy"
then sed -i '23s/$/\n0/' ~/conky_wunderground/icons.wun
elif test "$a" = "Mostly Cloudy"
then sed -i '23s/$/\nC/' ~/conky_wunderground/icons.wun
elif test "$a" = "Mostly Sunny"
then sed -i '23s/$/\nB/' ~/conky_wunderground/icons.wun
elif test "$a" = "Partly Cloudy"
then sed -i '23s/$/\nC/' ~/conky_wunderground/icons.wun
elif test "$a" = "Partly Sunny"
then sed -i '23s/$/\nC/' ~/conky_wunderground/icons.wun
elif test "$a" = "Freezing Rain"
then sed -i '23s/$/\nG/' ~/conky_wunderground/icons.wun
elif test "$a" = "Rain"
then sed -i '23s/$/\nG/' ~/conky_wunderground/icons.wun
elif test "$a" = "Sleet"
then sed -i '23s/$/\nG/' ~/conky_wunderground/icons.wun
elif test "$a" = "Snow"
then sed -i '23s/$/\nO/' ~/conky_wunderground/icons.wun
elif test "$a" = "Sunny"
then sed -i '23s/$/\nA/' ~/conky_wunderground/icons.wun
elif test "$a" = "Thunderstorms" || test "$a" = "Thunderstorm"
then sed -i '23s/$/\nK/' ~/conky_wunderground/icons.wun
elif test "$a" = "Overcast"
then sed -i '23s/$/\nD/' ~/conky_wunderground/icons.wun
elif test "$a" = "Scattered Clouds"
then sed -i '23s/$/\nB/' ~/conky_wunderground/icons.wun
else sed -i '23s/$/\n-/' ~/conky_wunderground/icons.wun
fi;
a=`sed -n '42p' ~/conky_wunderground/messages.wun`
if test "$a" = "Chance of Flurries"
then sed -i '24s/$/\np/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Rain"
then sed -i '24s/$/\nh/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Freezing Rain"
then sed -i '24s/$/\nv/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Sleet"
then sed -i '24s/$/\nw/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Snow"
then sed -i '24s/$/\nq/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Thunderstorms"
then sed -i '24s/$/\nn/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of a Thunderstorm"
then sed -i '24s/$/\nm/' ~/conky_wunderground/icons.wun
elif test "$a" = "Clear"
then sed -i '24s/$/\na/' ~/conky_wunderground/icons.wun
elif test "$a" = "Cloudy"
then sed -i '24s/$/\nd/' ~/conky_wunderground/icons.wun
elif test "$a" = "Flurries"
then sed -i '24s/$/\np/' ~/conky_wunderground/icons.wun
elif test "$a" = "Fog"
then sed -i '24s/$/\n0/' ~/conky_wunderground/icons.wun
elif test "$a" = "Hazy"
then sed -i '24s/$/\n0/' ~/conky_wunderground/icons.wun
elif test "$a" = "Mostly Cloudy"
then sed -i '24s/$/\nc/' ~/conky_wunderground/icons.wun
elif test "$a" = "Mostly Sunny"
then sed -i '24s/$/\nb/' ~/conky_wunderground/icons.wun
elif test "$a" = "Partly Cloudy"
then sed -i '24s/$/\nc/' ~/conky_wunderground/icons.wun
elif test "$a" = "Partly Sunny"
then sed -i '24s/$/\nc/' ~/conky_wunderground/icons.wun
elif test "$a" = "Freezing Rain"
then sed -i '24s/$/\nv/' ~/conky_wunderground/icons.wun
elif test "$a" = "Rain"
then sed -i '24s/$/\ni/' ~/conky_wunderground/icons.wun
elif test "$a" = "Sleet"
then sed -i '24s/$/\nw/' ~/conky_wunderground/icons.wun
elif test "$a" = "Snow"
then sed -i '24s/$/\nr/' ~/conky_wunderground/icons.wun
elif test "$a" = "Sunny"
then sed -i '24s/$/\na/' ~/conky_wunderground/icons.wun
elif test "$a" = "Thunderstorms" || test "$a" = "Thunderstorm"
then sed -i '24s/$/\nn/' ~/conky_wunderground/icons.wun
elif test "$a" = "Overcast"
then sed -i '24s/$/\ne/' ~/conky_wunderground/icons.wun
elif test "$a" = "Scattered Clouds"
then sed -i '24s/$/\nb/' ~/conky_wunderground/icons.wun
else sed -i '24s/$/\n-/' ~/conky_wunderground/icons.wun
fi;
a=`sed -n '46p' ~/conky_wunderground/messages.wun`
if test "$a" = "Chance of Flurries"
then sed -i '25s/$/\nO/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Rain"
then sed -i '25s/$/\nG/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Freezing Rain"
then sed -i '25s/$/\nG/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Sleet"
then sed -i '25s/$/\nG/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Snow"
then sed -i '25s/$/\nO/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Thunderstorms"
then sed -i '25s/$/\nK/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of a Thunderstorm"
then sed -i '25s/$/\nK/' ~/conky_wunderground/icons.wun
elif test "$a" = "Clear"
then sed -i '25s/$/\nA/' ~/conky_wunderground/icons.wun
elif test "$a" = "Cloudy"
then sed -i '25s/$/\nD/' ~/conky_wunderground/icons.wun
elif test "$a" = "Flurries"
then sed -i '25s/$/\nO/' ~/conky_wunderground/icons.wun
elif test "$a" = "Fog"
then sed -i '25s/$/\n0/' ~/conky_wunderground/icons.wun
elif test "$a" = "Hazy"
then sed -i '25s/$/\n0/' ~/conky_wunderground/icons.wun
elif test "$a" = "Mostly Cloudy"
then sed -i '25s/$/\nC/' ~/conky_wunderground/icons.wun
elif test "$a" = "Mostly Sunny"
then sed -i '25s/$/\nB/' ~/conky_wunderground/icons.wun
elif test "$a" = "Partly Cloudy"
then sed -i '25s/$/\nC/' ~/conky_wunderground/icons.wun
elif test "$a" = "Partly Sunny"
then sed -i '25s/$/\nC/' ~/conky_wunderground/icons.wun
elif test "$a" = "Freezing Rain"
then sed -i '25s/$/\nG/' ~/conky_wunderground/icons.wun
elif test "$a" = "Rain"
then sed -i '25s/$/\nG/' ~/conky_wunderground/icons.wun
elif test "$a" = "Sleet"
then sed -i '25s/$/\nG/' ~/conky_wunderground/icons.wun
elif test "$a" = "Snow"
then sed -i '25s/$/\nO/' ~/conky_wunderground/icons.wun
elif test "$a" = "Sunny"
then sed -i '25s/$/\nA/' ~/conky_wunderground/icons.wun
elif test "$a" = "Thunderstorms" || test "$a" = "Thunderstorm"
then sed -i '25s/$/\nK/' ~/conky_wunderground/icons.wun
elif test "$a" = "Overcast"
then sed -i '25s/$/\nD/' ~/conky_wunderground/icons.wun
elif test "$a" = "Scattered Clouds"
then sed -i '25s/$/\nB/' ~/conky_wunderground/icons.wun
else sed -i '25s/$/\n-/' ~/conky_wunderground/icons.wun
fi;
a=`sed -n '50p' ~/conky_wunderground/messages.wun`
if test "$a" = "Chance of Flurries"
then sed -i '26s/$/\np/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Rain"
then sed -i '26s/$/\nh/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Freezing Rain"
then sed -i '26s/$/\nv/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Sleet"
then sed -i '26s/$/\nw/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Snow"
then sed -i '26s/$/\nq/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Thunderstorms"
then sed -i '26s/$/\nn/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of a Thunderstorm"
then sed -i '26s/$/\nm/' ~/conky_wunderground/icons.wun
elif test "$a" = "Clear"
then sed -i '26s/$/\na/' ~/conky_wunderground/icons.wun
elif test "$a" = "Cloudy"
then sed -i '26s/$/\nd/' ~/conky_wunderground/icons.wun
elif test "$a" = "Flurries"
then sed -i '26s/$/\np/' ~/conky_wunderground/icons.wun
elif test "$a" = "Fog"
then sed -i '26s/$/\n0/' ~/conky_wunderground/icons.wun
elif test "$a" = "Hazy"
then sed -i '26s/$/\n0/' ~/conky_wunderground/icons.wun
elif test "$a" = "Mostly Cloudy"
then sed -i '26s/$/\nc/' ~/conky_wunderground/icons.wun
elif test "$a" = "Mostly Sunny"
then sed -i '26s/$/\nb/' ~/conky_wunderground/icons.wun
elif test "$a" = "Partly Cloudy"
then sed -i '26s/$/\nc/' ~/conky_wunderground/icons.wun
elif test "$a" = "Partly Sunny"
then sed -i '26s/$/\nc/' ~/conky_wunderground/icons.wun
elif test "$a" = "Freezing Rain"
then sed -i '26s/$/\nv/' ~/conky_wunderground/icons.wun
elif test "$a" = "Rain"
then sed -i '26s/$/\ni/' ~/conky_wunderground/icons.wun
elif test "$a" = "Sleet"
then sed -i '26s/$/\nw/' ~/conky_wunderground/icons.wun
elif test "$a" = "Snow"
then sed -i '26s/$/\nr/' ~/conky_wunderground/icons.wun
elif test "$a" = "Sunny"
then sed -i '26s/$/\na/' ~/conky_wunderground/icons.wun
elif test "$a" = "Thunderstorms" || test "$a" = "Thunderstorm"
then sed -i '26s/$/\nn/' ~/conky_wunderground/icons.wun
elif test "$a" = "Overcast"
then sed -i '26s/$/\ne/' ~/conky_wunderground/icons.wun
elif test "$a" = "Scattered Clouds"
then sed -i '26s/$/\nb/' ~/conky_wunderground/icons.wun
else sed -i '26s/$/\n-/' ~/conky_wunderground/icons.wun
fi;
a=`sed -n '54p' ~/conky_wunderground/messages.wun`
if test "$a" = "Chance of Flurries"
then sed -i '27s/$/\nO/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Rain"
then sed -i '27s/$/\nG/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Freezing Rain"
then sed -i '27s/$/\nG/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Sleet"
then sed -i '27s/$/\nG/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Snow"
then sed -i '27s/$/\nO/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of Thunderstorms"
then sed -i '27s/$/\nK/' ~/conky_wunderground/icons.wun
elif test "$a" = "Chance of a Thunderstorm"
then sed -i '27s/$/\nK/' ~/conky_wunderground/icons.wun
elif test "$a" = "Clear"
then sed -i '27s/$/\nA/' ~/conky_wunderground/icons.wun
elif test "$a" = "Cloudy"
then sed -i '27s/$/\nD/' ~/conky_wunderground/icons.wun
elif test "$a" = "Flurries"
then sed -i '27s/$/\nO/' ~/conky_wunderground/icons.wun
elif test "$a" = "Fog"
then sed -i '27s/$/\n0/' ~/conky_wunderground/icons.wun
elif test "$a" = "Hazy"
then sed -i '27s/$/\n0/' ~/conky_wunderground/icons.wun
elif test "$a" = "Mostly Cloudy"
then sed -i '27s/$/\nC/' ~/conky_wunderground/icons.wun
elif test "$a" = "Mostly Sunny"
then sed -i '27s/$/\nB/' ~/conky_wunderground/icons.wun
elif test "$a" = "Partly Cloudy"
then sed -i '27s/$/\nC/' ~/conky_wunderground/icons.wun
elif test "$a" = "Partly Sunny"
then sed -i '27s/$/\nC/' ~/conky_wunderground/icons.wun
elif test "$a" = "Freezing Rain"
then sed -i '27s/$/\nG/' ~/conky_wunderground/icons.wun
elif test "$a" = "Rain"
then sed -i '27s/$/\nG/' ~/conky_wunderground/icons.wun
elif test "$a" = "Sleet"
then sed -i '27s/$/\nG/' ~/conky_wunderground/icons.wun
elif test "$a" = "Snow"
then sed -i '27s/$/\nO/' ~/conky_wunderground/icons.wun
elif test "$a" = "Sunny"
then sed -i '27s/$/\nA/' ~/conky_wunderground/icons.wun
elif test "$a" = "Thunderstorms" || test "$a" = "Thunderstorm"
then sed -i '27s/$/\nK/' ~/conky_wunderground/icons.wun
elif test "$a" = "Overcast"
then sed -i '27s/$/\nD/' ~/conky_wunderground/icons.wun
elif test "$a" = "Scattered Clouds"
then sed -i '27s/$/\nB/' ~/conky_wunderground/icons.wun
else sed -i '27s/$/\n-/' ~/conky_wunderground/icons.wun
fi;
a=`sed -n '4p' ~/conky_wunderground/messages.wun|cut -c1-3 `
if test "$a" = "Sou"
then sed -i '1s/Sou/1/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SSW"
then sed -i '1s/SSW/2/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SW "
then sed -i '1s/SW /3/g' ~/conky_wunderground/icons.wun
elif test "$a" = "WSW"
then sed -i '1s/WSW/4/g' ~/conky_wunderground/icons.wun
elif test "$a" = "Wes"
then sed -i '1s/Wes/5/g' ~/conky_wunderground/icons.wun
elif test "$a" = "WNW"
then sed -i '1s/WNW/6/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NW "
then sed -i '1s/NW /7/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NNW"
then sed -i '1s/NNW/8/g' ~/conky_wunderground/icons.wun
elif test "$a" = "Nor"
then sed -i '1s/Nor/9/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NNE"
then sed -i '1s/NNE/:/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NE "
then sed -i '1s/NE /;/g' ~/conky_wunderground/icons.wun
elif test "$a" = "ENE"
then sed -i '1s/ENE/</g' ~/conky_wunderground/icons.wun
elif test "$a" = "Eas"
then sed -i '1s/Eas/=/g' ~/conky_wunderground/icons.wun
elif test "$a" = "ESE"
then sed -i '1s/ESE/>/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SE "
then sed -i '1s/SE /?/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SSE"
then sed -i '1s/SSE/@/g' ~/conky_wunderground/icons.wun
else sed -i '1s/$/-/' ~/conky_wunderground/icons.wun
fi;
a=`sed -n '8p' ~/conky_wunderground/messages.wun|cut -c1-3 `
if test "$a" = "Sou"
then sed -i '2s/Sou/1/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SSW"
then sed -i '2s/SSW/2/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SW "
then sed -i '2s/SW /3/g' ~/conky_wunderground/icons.wun
elif test "$a" = "WSW"
then sed -i '2s/WSW/4/g' ~/conky_wunderground/icons.wun
elif test "$a" = "Wes"
then sed -i '2s/Wes/5/g' ~/conky_wunderground/icons.wun
elif test "$a" = "WNW"
then sed -i '2s/WNW/6/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NW "
then sed -i '2s/NW /7/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NNW"
then sed -i '2s/NNW/8/g' ~/conky_wunderground/icons.wun
elif test "$a" = "Nor"
then sed -i '2s/Nor/9/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NNE"
then sed -i '2s/NNE/:/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NE "
then sed -i '2s/NE /;/g' ~/conky_wunderground/icons.wun
elif test "$a" = "ENE"
then sed -i '2s/ENE/</g' ~/conky_wunderground/icons.wun
elif test "$a" = "Eas"
then sed -i '2s/Eas/=/g' ~/conky_wunderground/icons.wun
elif test "$a" = "ESE"
then sed -i '2s/ESE/>/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SE "
then sed -i '2s/SE /?/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SSE"
then sed -i '2s/SSE/@/g' ~/conky_wunderground/icons.wun
else sed -i '2s/$/-/' ~/conky_wunderground/icons.wun
fi;
a=`sed -n '12p' ~/conky_wunderground/messages.wun|cut -c1-3 `
if test "$a" = "Sou"
then sed -i '3s/Sou/1/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SSW"
then sed -i '3s/SSW/2/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SW "
then sed -i '3s/SW /3/g' ~/conky_wunderground/icons.wun
elif test "$a" = "WSW"
then sed -i '3s/WSW/4/g' ~/conky_wunderground/icons.wun
elif test "$a" = "Wes"
then sed -i '3s/Wes/5/g' ~/conky_wunderground/icons.wun
elif test "$a" = "WNW"
then sed -i '3s/WNW/6/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NW "
then sed -i '3s/NW /7/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NNW"
then sed -i '3s/NNW/8/g' ~/conky_wunderground/icons.wun
elif test "$a" = "Nor"
then sed -i '3s/Nor/9/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NNE"
then sed -i '3s/NNE/:/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NE "
then sed -i '3s/NE /;/g' ~/conky_wunderground/icons.wun
elif test "$a" = "ENE"
then sed -i '3s/ENE/</g' ~/conky_wunderground/icons.wun
elif test "$a" = "Eas"
then sed -i '3s/Eas/=/g' ~/conky_wunderground/icons.wun
elif test "$a" = "ESE"
then sed -i '3s/ESE/>/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SE "
then sed -i '3s/SE /?/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SSE"
then sed -i '3s/SSE/@/g' ~/conky_wunderground/icons.wun
else sed -i '3s/$/-/' ~/conky_wunderground/icons.wun
fi;
a=`sed -n '16p' ~/conky_wunderground/messages.wun|cut -c1-3 `
if test "$a" = "Sou"
then sed -i '4s/Sou/1/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SSW"
then sed -i '4s/SSW/2/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SW "
then sed -i '4s/SW /3/g' ~/conky_wunderground/icons.wun
elif test "$a" = "WSW"
then sed -i '4s/WSW/4/g' ~/conky_wunderground/icons.wun
elif test "$a" = "Wes"
then sed -i '4s/Wes/5/g' ~/conky_wunderground/icons.wun
elif test "$a" = "WNW"
then sed -i '4s/WNW/6/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NW "
then sed -i '4s/NW /7/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NNW"
then sed -i '4s/NNW/8/g' ~/conky_wunderground/icons.wun
elif test "$a" = "Nor"
then sed -i '4s/Nor/9/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NNE"
then sed -i '4s/NNE/:/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NE "
then sed -i '4s/NE /;/g' ~/conky_wunderground/icons.wun
elif test "$a" = "ENE"
then sed -i '4s/ENE/</g' ~/conky_wunderground/icons.wun
elif test "$a" = "Eas"
then sed -i '4s/Eas/=/g' ~/conky_wunderground/icons.wun
elif test "$a" = "ESE"
then sed -i '4s/ESE/>/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SE "
then sed -i '4s/SE /?/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SSE"
then sed -i '4s/SSE/@/g' ~/conky_wunderground/icons.wun
else sed -i '4s/$/-/' ~/conky_wunderground/icons.wun
fi;
a=`sed -n '20p' ~/conky_wunderground/messages.wun|cut -c1-3 `
if test "$a" = "Sou"
then sed -i '5s/Sou/1/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SSW"
then sed -i '5s/SSW/2/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SW "
then sed -i '5s/SW /3/g' ~/conky_wunderground/icons.wun
elif test "$a" = "WSW"
then sed -i '5s/WSW/4/g' ~/conky_wunderground/icons.wun
elif test "$a" = "Wes"
then sed -i '5s/Wes/5/g' ~/conky_wunderground/icons.wun
elif test "$a" = "WNW"
then sed -i '5s/WNW/6/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NW "
then sed -i '5s/NW /7/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NNW"
then sed -i '5s/NNW/8/g' ~/conky_wunderground/icons.wun
elif test "$a" = "Nor"
then sed -i '5s/Nor/9/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NNE"
then sed -i '5s/NNE/:/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NE "
then sed -i '5s/NE /;/g' ~/conky_wunderground/icons.wun
elif test "$a" = "ENE"
then sed -i '5s/ENE/</g' ~/conky_wunderground/icons.wun
elif test "$a" = "Eas"
then sed -i '5s/Eas/=/g' ~/conky_wunderground/icons.wun
elif test "$a" = "ESE"
then sed -i '5s/ESE/>/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SE "
then sed -i '5s/SE /?/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SSE"
then sed -i '5s/SSE/@/g' ~/conky_wunderground/icons.wun
else sed -i '5s/$/-/' ~/conky_wunderground/icons.wun
fi;
a=`sed -n '24p' ~/conky_wunderground/messages.wun|cut -c1-3 `
if test "$a" = "Sou"
then sed -i '6s/Sou/1/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SSW"
then sed -i '6s/SSW/2/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SW "
then sed -i '6s/SW /3/g' ~/conky_wunderground/icons.wun
elif test "$a" = "WSW"
then sed -i '6s/WSW/4/g' ~/conky_wunderground/icons.wun
elif test "$a" = "Wes"
then sed -i '6s/Wes/5/g' ~/conky_wunderground/icons.wun
elif test "$a" = "WNW"
then sed -i '6s/WNW/6/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NW "
then sed -i '6s/NW /7/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NNW"
then sed -i '6s/NNW/8/g' ~/conky_wunderground/icons.wun
elif test "$a" = "Nor"
then sed -i '6s/Nor/9/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NNE"
then sed -i '6s/NNE/:/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NE "
then sed -i '6s/NE /;/g' ~/conky_wunderground/icons.wun
elif test "$a" = "ENE"
then sed -i '6s/ENE/</g' ~/conky_wunderground/icons.wun
elif test "$a" = "Eas"
then sed -i '6s/Eas/=/g' ~/conky_wunderground/icons.wun
elif test "$a" = "ESE"
then sed -i '6s/ESE/>/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SE "
then sed -i '6s/SE /?/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SSE"
then sed -i '6s/SSE/@/g' ~/conky_wunderground/icons.wun
else sed -i '6s/$/-/' ~/conky_wunderground/icons.wun
fi;
a=`sed -n '28p' ~/conky_wunderground/messages.wun|cut -c1-3 `
if test "$a" = "Sou"
then sed -i '7s/Sou/1/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SSW"
then sed -i '7s/SSW/2/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SW "
then sed -i '7s/SW /3/g' ~/conky_wunderground/icons.wun
elif test "$a" = "WSW"
then sed -i '7s/WSW/4/g' ~/conky_wunderground/icons.wun
elif test "$a" = "Wes"
then sed -i '7s/Wes/5/g' ~/conky_wunderground/icons.wun
elif test "$a" = "WNW"
then sed -i '7s/WNW/6/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NW "
then sed -i '7s/NW /7/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NNW"
then sed -i '7s/NNW/8/g' ~/conky_wunderground/icons.wun
elif test "$a" = "Nor"
then sed -i '7s/Nor/9/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NNE"
then sed -i '7s/NNE/:/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NE "
then sed -i '7s/NE /;/g' ~/conky_wunderground/icons.wun
elif test "$a" = "ENE"
then sed -i '7s/ENE/</g' ~/conky_wunderground/icons.wun
elif test "$a" = "Eas"
then sed -i '7s/Eas/=/g' ~/conky_wunderground/icons.wun
elif test "$a" = "ESE"
then sed -i '7s/ESE/>/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SE "
then sed -i '7s/SE /?/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SSE"
then sed -i '7s/SSE/@/g' ~/conky_wunderground/icons.wun
else sed -i '7s/$/-/' ~/conky_wunderground/icons.wun
fi;
a=`sed -n '32p' ~/conky_wunderground/messages.wun|cut -c1-3 `
if test "$a" = "Sou"
then sed -i '8s/Sou/1/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SSW"
then sed -i '8s/SSW/2/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SW "
then sed -i '8s/SW /3/g' ~/conky_wunderground/icons.wun
elif test "$a" = "WSW"
then sed -i '8s/WSW/4/g' ~/conky_wunderground/icons.wun
elif test "$a" = "Wes"
then sed -i '8s/Wes/5/g' ~/conky_wunderground/icons.wun
elif test "$a" = "WNW"
then sed -i '8s/WNW/6/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NW "
then sed -i '8s/NW /7/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NNW"
then sed -i '8s/NNW/8/g' ~/conky_wunderground/icons.wun
elif test "$a" = "Nor"
then sed -i '8s/Nor/9/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NNE"
then sed -i '8s/NNE/:/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NE "
then sed -i '8s/NE /;/g' ~/conky_wunderground/icons.wun
elif test "$a" = "ENE"
then sed -i '8s/ENE/</g' ~/conky_wunderground/icons.wun
elif test "$a" = "Eas"
then sed -i '8s/Eas/=/g' ~/conky_wunderground/icons.wun
elif test "$a" = "ESE"
then sed -i '8s/ESE/>/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SE "
then sed -i '8s/SE /?/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SSE"
then sed -i '8s/SSE/@/g' ~/conky_wunderground/icons.wun
else sed -i '8s/$/-/' ~/conky_wunderground/icons.wun
fi;
a=`sed -n '36p' ~/conky_wunderground/messages.wun|cut -c1-3 `
if test "$a" = "Sou"
then sed -i '9s/Sou/1/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SSW"
then sed -i '9s/SSW/2/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SW "
then sed -i '9s/SW /3/g' ~/conky_wunderground/icons.wun
elif test "$a" = "WSW"
then sed -i '9s/WSW/4/g' ~/conky_wunderground/icons.wun
elif test "$a" = "Wes"
then sed -i '9s/Wes/5/g' ~/conky_wunderground/icons.wun
elif test "$a" = "WNW"
then sed -i '9s/WNW/6/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NW "
then sed -i '9s/NW /7/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NNW"
then sed -i '9s/NNW/8/g' ~/conky_wunderground/icons.wun
elif test "$a" = "Nor"
then sed -i '9s/Nor/9/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NNE"
then sed -i '9s/NNE/:/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NE "
then sed -i '9s/NE /;/g' ~/conky_wunderground/icons.wun
elif test "$a" = "ENE"
then sed -i '9s/ENE/</g' ~/conky_wunderground/icons.wun
elif test "$a" = "Eas"
then sed -i '9s/Eas/=/g' ~/conky_wunderground/icons.wun
elif test "$a" = "ESE"
then sed -i '9s/ESE/>/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SE "
then sed -i '9s/SE /?/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SSE"
then sed -i '9s/SSE/@/g' ~/conky_wunderground/icons.wun
else sed -i '9s/$/-/' ~/conky_wunderground/icons.wun
fi;
a=`sed -n '40p' ~/conky_wunderground/messages.wun|cut -c1-3 `
if test "$a" = "Sou"
then sed -i '10s/Sou/1/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SSW"
then sed -i '10s/SSW/2/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SW "
then sed -i '10s/SW /3/g' ~/conky_wunderground/icons.wun
elif test "$a" = "WSW"
then sed -i '10s/WSW/4/g' ~/conky_wunderground/icons.wun
elif test "$a" = "Wes"
then sed -i '10s/Wes/5/g' ~/conky_wunderground/icons.wun
elif test "$a" = "WNW"
then sed -i '10s/WNW/6/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NW "
then sed -i '10s/NW /7/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NNW"
then sed -i '10s/NNW/8/g' ~/conky_wunderground/icons.wun
elif test "$a" = "Nor"
then sed -i '10s/Nor/9/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NNE"
then sed -i '10s/NNE/:/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NE "
then sed -i '10s/NE /;/g' ~/conky_wunderground/icons.wun
elif test "$a" = "ENE"
then sed -i '10s/ENE/</g' ~/conky_wunderground/icons.wun
elif test "$a" = "Eas"
then sed -i '10s/Eas/=/g' ~/conky_wunderground/icons.wun
elif test "$a" = "ESE"
then sed -i '10s/ESE/>/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SE "
then sed -i '10s/SE /?/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SSE"
then sed -i '10s/SSE/@/g' ~/conky_wunderground/icons.wun
else sed -i '10s/$/-/' ~/conky_wunderground/icons.wun
fi;
a=`sed -n '44p' ~/conky_wunderground/messages.wun|cut -c1-3 `
if test "$a" = "Sou"
then sed -i '11s/Sou/1/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SSW"
then sed -i '11s/SSW/2/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SW "
then sed -i '11s/SW /3/g' ~/conky_wunderground/icons.wun
elif test "$a" = "WSW"
then sed -i '11s/WSW/4/g' ~/conky_wunderground/icons.wun
elif test "$a" = "Wes"
then sed -i '11s/Wes/5/g' ~/conky_wunderground/icons.wun
elif test "$a" = "WNW"
then sed -i '11s/WNW/6/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NW "
then sed -i '11s/NW /7/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NNW"
then sed -i '11s/NNW/8/g' ~/conky_wunderground/icons.wun
elif test "$a" = "Nor"
then sed -i '11s/Nor/9/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NNE"
then sed -i '11s/NNE/:/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NE "
then sed -i '11s/NE /;/g' ~/conky_wunderground/icons.wun
elif test "$a" = "ENE"
then sed -i '11s/ENE/</g' ~/conky_wunderground/icons.wun
elif test "$a" = "Eas"
then sed -i '11s/Eas/=/g' ~/conky_wunderground/icons.wun
elif test "$a" = "ESE"
then sed -i '11s/ESE/>/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SE "
then sed -i '11s/SE /?/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SSE"
then sed -i '11s/SSE/@/g' ~/conky_wunderground/icons.wun
else sed -i '11s/$/-/' ~/conky_wunderground/icons.wun
fi;
a=`sed -n '48p' ~/conky_wunderground/messages.wun|cut -c1-3 `
if test "$a" = "Sou"
then sed -i '12s/Sou/1/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SSW"
then sed -i '12s/SSW/2/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SW "
then sed -i '12s/SW /3/g' ~/conky_wunderground/icons.wun
elif test "$a" = "WSW"
then sed -i '12s/WSW/4/g' ~/conky_wunderground/icons.wun
elif test "$a" = "Wes"
then sed -i '12s/Wes/5/g' ~/conky_wunderground/icons.wun
elif test "$a" = "WNW"
then sed -i '12s/WNW/6/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NW "
then sed -i '12s/NW /7/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NNW"
then sed -i '12s/NNW/8/g' ~/conky_wunderground/icons.wun
elif test "$a" = "Nor"
then sed -i '12s/Nor/9/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NNE"
then sed -i '12s/NNE/:/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NE "
then sed -i '12s/NE /;/g' ~/conky_wunderground/icons.wun
elif test "$a" = "ENE"
then sed -i '12s/ENE/</g' ~/conky_wunderground/icons.wun
elif test "$a" = "Eas"
then sed -i '12s/Eas/=/g' ~/conky_wunderground/icons.wun
elif test "$a" = "ESE"
then sed -i '12s/ESE/>/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SE "
then sed -i '12s/SE /?/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SSE"
then sed -i '12s/SSE/@/g' ~/conky_wunderground/icons.wun
else sed -i '12s/$/-/' ~/conky_wunderground/icons.wun
fi;
a=`sed -n '52p' ~/conky_wunderground/messages.wun|cut -c1-3 `
if test "$a" = "Sou"
then sed -i '13s/Sou/1/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SSW"
then sed -i '13s/SSW/2/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SW "
then sed -i '13s/SW /3/g' ~/conky_wunderground/icons.wun
elif test "$a" = "WSW"
then sed -i '13s/WSW/4/g' ~/conky_wunderground/icons.wun
elif test "$a" = "Wes"
then sed -i '13s/Wes/5/g' ~/conky_wunderground/icons.wun
elif test "$a" = "WNW"
then sed -i '13s/WNW/6/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NW "
then sed -i '13s/NW /7/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NNW"
then sed -i '13s/NNW/8/g' ~/conky_wunderground/icons.wun
elif test "$a" = "Nor"
then sed -i '13s/Nor/9/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NNE"
then sed -i '13s/NNE/:/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NE "
then sed -i '13s/NE /;/g' ~/conky_wunderground/icons.wun
elif test "$a" = "ENE"
then sed -i '13s/ENE/</g' ~/conky_wunderground/icons.wun
elif test "$a" = "Eas"
then sed -i '13s/Eas/=/g' ~/conky_wunderground/icons.wun
elif test "$a" = "ESE"
then sed -i '13s/ESE/>/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SE "
then sed -i '13s/SE /?/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SSE"
then sed -i '13s/SSE/@/g' ~/conky_wunderground/icons.wun
else sed -i '13s/$/-/' ~/conky_wunderground/icons.wun
fi;
a=`sed -n '56p' ~/conky_wunderground/messages.wun|cut -c1-3 `
if test "$a" = "Sou"
then sed -i '14s/Sou/1/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SSW"
then sed -i '14s/SSW/2/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SW "
then sed -i '14s/SW /3/g' ~/conky_wunderground/icons.wun
elif test "$a" = "WSW"
then sed -i '14s/WSW/4/g' ~/conky_wunderground/icons.wun
elif test "$a" = "Wes"
then sed -i '14s/Wes/5/g' ~/conky_wunderground/icons.wun
elif test "$a" = "WNW"
then sed -i '14s/WNW/6/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NW "
then sed -i '14s/NW /7/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NNW"
then sed -i '14s/NNW/8/g' ~/conky_wunderground/icons.wun
elif test "$a" = "Nor"
then sed -i '14s/Nor/9/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NNE"
then sed -i '14s/NNE/:/g' ~/conky_wunderground/icons.wun
elif test "$a" = "NE "
then sed -i '14s/NE /;/g' ~/conky_wunderground/icons.wun
elif test "$a" = "ENE"
then sed -i '14s/ENE/</g' ~/conky_wunderground/icons.wun
elif test "$a" = "Eas"
then sed -i '14s/Eas/=/g' ~/conky_wunderground/icons.wun
elif test "$a" = "ESE"
then sed -i '14s/ESE/>/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SE "
then sed -i '14s/SE /?/g' ~/conky_wunderground/icons.wun
elif test "$a" = "SSE"
then sed -i '14s/SSE/@/g' ~/conky_wunderground/icons.wun
else sed -i '14s/$/-/' ~/conky_wunderground/icons.wun
fi;
```
The part I'm concerned with is:
```
rm ~/conky_wunderground/14
rm ~/conky_wunderground/13
rm ~/conky_wunderground/12
```
that creates and error in terminal if the files do not exist.

```
0 bruloo@bruloo: ~
Tue Dec 29, 12:45 $ conky -c ~/Conky/OB_Wunder
Conky: desktop window (1a7) is root window
Conky: window type - normal
Conky: drawing to created window (0x1800001)
Conky: drawing to double buffer
--2009-12-29 12:45:30--  http://ical.wunderground.com/auto/ical/global/stations/87582.ics?units=metric
Resolving ical.wunderground.com... 38.102.136.104
Connecting to ical.wunderground.com|38.102.136.104|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/calendar]
Saving to: `/home/bruloo/Conky/Wunderground/ics1'

    [  <=>                                                                       ] 4,228       16.1K/s   in 0.3s    

2009-12-29 12:45:31 (16.1 KB/s) - `/home/bruloo/Conky/Wunderground/ics1' saved [4228]

rm: cannot remove `/home/bruloo/Conky/Wunderground/13': No such file or directory
rm: cannot remove `/home/bruloo/Conky/Wunderground/12': No such file or directory
```

Is there a "if exist" command that can be applied in a bash script?  I checked "man rm" and didn't see anything.

{thinking out loud ... errrr typing -. template for that would be nice}

On boot-up in the morning I see all my conkys:
[CENTER][[IMG]http://conky.linux-hardcore.com/wp-content/uploads/2009/12/All_Conky-300x240.png[/IMG]]("http://conky.linux-hardcore.com/wp-content/uploads/2009/12/All_Conky.png")[/CENTER]
That Spanish Calendar near the bottom is just nostalgia.  :)

Have a nice day.
Bruce

---

### Post by mobilediesel on 2009-12-29
> **Bruce M. said:**
> **Off Topic**

Bite your tongue. :lolflag:

**On Topic!**
heh. :D
> **Bruce M. said:**
> Now to continue:
...
The part I'm concerned with is:
```
rm ~/conky_wunderground/14
rm ~/conky_wunderground/13
rm ~/conky_wunderground/12
```
that creates and error in terminal if the files do not exist.
...

Have a nice day.
Bruce

```
[ -e ~/conky_wunderground/14 ] && rm ~/conky_wunderground/14
[ -e ~/conky_wunderground/13 ] && rm ~/conky_wunderground/13
[ -e ~/conky_wunderground/12 ] && rm ~/conky_wunderground/12
```

it will only try to delete when the files exist. Then you don't have to try to tell rm to force it and possibly delete more than you want.

---

### Post by Bruce M. on 2009-12-29
> **mobilediesel said:**
> heh. :D

Did it hurt? :lolflag:

> **mobilediesel said:**
> ```
[ -e ~/conky_wunderground/14 ] && rm ~/conky_wunderground/14
[ -e ~/conky_wunderground/13 ] && rm ~/conky_wunderground/13
[ -e ~/conky_wunderground/12 ] && rm ~/conky_wunderground/12
```

it will only try to delete when the files exist. Then you don't have to try to tell rm to force it and possibly delete more than you want.

Did not work:
```
rm: cannot remove `/home/bruloo/Conky/Wunderground/13': No such file or directory
rm: cannot remove `/home/bruloo/Conky/Wunderground/12': No such file or directory

```
so I did a man bash (DUH!!) and tried -a
```
[ -a ~/conky_wunderground/14 ] && rm ~/conky_wunderground/14
[ -a ~/conky_wunderground/13 ] && rm ~/conky_wunderground/13
[ -a ~/conky_wunderground/12 ] && rm ~/conky_wunderground/12
```
and that didn't work either - same results.

Both look like they should work.

:(
C H I M O!!
Bruce

---

### Post by mobilediesel on 2009-12-29
> **Bruce M. said:**
> Did it hurt? :lolflag:



Did not work:
```
rm: cannot remove `/home/bruloo/Conky/Wunderground/13': No such file or directory
rm: cannot remove `/home/bruloo/Conky/Wunderground/12': No such file or directory

```
so I did a man bash (DUH!!) and tried -a
```
[ -a ~/conky_wunderground/14 ] && rm ~/conky_wunderground/14
[ -a ~/conky_wunderground/13 ] && rm ~/conky_wunderground/13
[ -a ~/conky_wunderground/12 ] && rm ~/conky_wunderground/12
```
and that didn't work either - same results.

Both look like they should work.

:(
C H I M O!!
Bruce

It seems to work on mine. I've had trouble using the "**~**" character in .conkyrc files before. Change them all to "**$HOME**" and see if it still gives the error.

---

### Post by The Real Dave on 2009-12-29
Here's my little contribution, a little script that pings an IP address, and returns a statement. I'm using it to monitor what computers on my LAN are currently on or off. The full explanation and script is [here]("http://linuxexpresso.wordpress.com/2009/12/20/conky-ip-monitor/"), in reality, its extremely simple :) Here's a screenshot so you know what I'm talking about :)

[IMG]http://linuxexpresso.files.wordpress.com/2009/12/20-dec-2009-1.png[/IMG]

---

### Post by The Real Dave on 2009-12-29
> **mobilediesel said:**
> Some swear by it, others swear AT it. :D

I've never tried it myself but I'll probably try that or Arch when I get another hard drive.

Apologies for the double post, but I love #!. Most of the benefits of a minimal OpenBox desktop, with very little effort :)

---

### Post by dmillerct on 2009-12-29
> **The Real Dave said:**
> Here's my little contribution, a little script that pings an IP address, and returns a statement. I'm using it to monitor what computers on my LAN are currently on or off. The full explanation and script is [here]("http://linuxexpresso.wordpress.com/2009/12/20/conky-ip-monitor/"), in reality, its extremely simple :) Here's a screenshot so you know what I'm talking about :)

[IMG]http://linuxexpresso.files.wordpress.com/2009/12/20-dec-2009-1.png[/IMG]

Love it, gonna use it. Thanks.

---

### Post by The Real Dave on 2009-12-29
> **dmillerct said:**
> Love it, gonna use it. Thanks.

Enjoy :) I was hoping someone would find it useful :)

---

### Post by dmillerct on 2009-12-30
> **The Real Dave said:**
> Enjoy :) I was hoping someone would find it useful :)

It would be great if someone could figure out how to "colorize" the script so that if the connection was down it displayed the echo in a different color.

I tried the following but that obviously did not work:

```
#!/bin/bash

if ping -c 1 -W 2 $1 > /dev/null; then
echo UP
else
echo ${color3}DOWN${color}
fi
```

---

### Post by mobilediesel on 2009-12-30
> **dmillerct said:**
> It would be great if someone could figure out how to "colorize" the script so that if the connection was down it displayed the echo in a different color.

I tried the following but that obviously did not work:

```
#!/bin/bash

if ping -c 1 -W 2 $1 > /dev/null; then
echo UP
else
echo ${color3}DOWN${color}
fi
```

You have to escape the **$**:
```
#!/bin/bash

if ping -c 1 -W 2 $1 > /dev/null; then
echo UP
else
echo "\${color3}DOWN\${color}"
fi
```

---

### Post by dmillerct on 2009-12-30
> **mobilediesel said:**
> You have to escape the **$**:
```
#!/bin/bash

if ping -c 1 -W 2 $1 > /dev/null; then
echo UP
else
echo "\${color3}DOWN\${color}"
fi
```

It is sill returning ${color3}DOWN${color} in the conky. I think this is because of execi.

---

### Post by mobilediesel on 2009-12-30
> **dmillerct said:**
> It is sill returning ${color3}DOWN${color} in the conky. I think this is because of execi.

Yeah, you have to use **execpi**, the **p** makes it interpret the color codes.

---

### Post by dmillerct on 2009-12-30
> **mobilediesel said:**
> Yeah, you have to use **execpi**, the **p** makes it interpret the color codes.

Yup that did it. :P

---

### Post by mobilediesel on 2010-01-01
> **dmillerct said:**
> Quite cool. You should post this in Bruce's thread here: [http://ubuntuforums.org/showthread.php?p=8582781]("http://ubuntuforums.org/showthread.php?p=8582781")
I meant to. :D

Three simple calendar scripts that have been tweaked a bit since I last posted them.

This one shows the current day with the three previous and three following days with current day highlighted:
```
#!/bin/bash

font=("\${font vera:size=8}" "\${voffset -4}\${font vera:size=12}" "\${voffset -5}\${font vera:size=18}" "\${voffset -8}\${font vera:size=27}\${color ffffff}" "\${font vera:size=18}" "\${font vera:size=12}" "\${font vera:size=8}")
color=("" "" "" "\${color}" "" "" "")

for i in $(seq -3 3); do
echo -n "${font[$[i+3]]}$(date '+%d' -d "$i days")${color[3]}\${offset 3}"
done

```
[ATTACH]142011[/ATTACH]

This one just shows the current week with current day highlighted:
```
#!/bin/bash

#m=-1 # uncomment this line for starting the week on Monday instead of Sunday.
DAY=$(date +%_d)
bow=$(date -d "-$[$(date +%u)$m] days")
week="$(date '+%_d' -d "$bow")"
for i in $(seq 1 6); do
week="$week $(date +%_d -d "$bow $i days")"
done
echo "$week"|sed "s/$DAY/\${color ffffff}&\${color}/"
```
[ATTACH]142012[/ATTACH]

This is the normal calendar that highlights the current day plus holidays and birthdays depending on what the **remind** command has:
```
date=$(date '+%F')
DAY=${date:8:2}
# m="-m" # uncomment this line for starting the week on Monday instead of Sunday.
cal=$(cal $m)
prev=$(cal $m $(date '+%-m %Y' --date="${date:0:7}-15 -1 month")|sed 's/ *$//;/^$/d'|tail -1)
next=$(cal $m $(date '+%-m %Y' --date="${date:0:7}-15 +1 month")|sed '/^ *&/d;1,2d;s/^ *//'|head -1)
if [ ${#next} == 19 ] ;then next=$'\n'"\${color9} $next"
else next="\${color9}  $next"
fi
if [ ${#prev} == 20 ]; then prev="$prev"$'\n '
else prev="$prev  "
fi
dates=$(remind -s|cut -d ' ' -f1|uniq|cut -d '/' -f3|sed "/$DAY/d")
current=$(echo "${cal:42}"|sed -e '/^ *$/d' -e 's/^/ /' -e 's/$/ /' -e 's/^ *1 / 1 /' )
for i in $dates; do
current=$(echo "$current"|sed -e /" ${i/#0/} "/s/" ${i/#0/} "/" "'${color green}'"${i/#0/}"'${color}'" "/)
done
current=$(echo "$current"|sed -e /" ${DAY/#0/} "/s/" ${DAY/#0/} "/" "'${color3}'"${DAY/#0/}"'${color}'" "/ -e 's/^ //' -e 's/ *$//')
echo -e "\${color7}${cal:0:21}\${color4}${cal:21:21}\${color9}$prev\${color}$current$next"
```
[ATTACH]142013[/ATTACH]

and here's another one from **[here]("http://ubuntuforums.org/showthread.php?p=8519422#post8519422")**
```
#! /bin/bash
COLORTODAY="red"
COLORNUMBER="orange"

DAY="Su Mo Tu We Th Fr Sa"
NUM_FIRST="0 1 2 3"
NUM_SECOND="0 1 2 3 4 5 6 7 8 9"
DATE=$(date '+%a%d')

echo ${DAY/${DATE:0:2}/\$\{color $COLORTODAY\}${DATE:0:2}\$\{color\}}
echo ${NUM_FIRST/${DATE:3:1}/\$\{color $COLORNUMBER\}${DATE:3:1}\$\{color\}}
echo ${NUM_SECOND/${DATE:4:1}/\$\{color $COLORNUMBER\}${DATE:4:1}\$\{color\}}
```
[ATTACH]142016[/ATTACH]

---

### Post by markp1989 on 2010-01-01
> **mobilediesel said:**
> I meant to. :D

Three simple calendar scripts that have been tweaked a bit since I last posted them.

This one shows the current day with the three previous and three following days with current day highlighted:
```
#!/bin/bash

font=("\${font vera:size=8}" "\${voffset -4}\${font vera:size=12}" "\${voffset -5}\${font vera:size=18}" "\${voffset -8}\${font vera:size=27}\${color ffffff}" "\${font vera:size=18}" "\${font vera:size=12}" "\${font vera:size=8}")
color=("" "" "" "\${color}" "" "" "")

for i in $(seq -3 3); do
echo -n "${font[$[i+3]]}$(date '+%d' -d "$i days")${color[3]}\${offset 3}"
done

```
[ATTACH]142011[/ATTACH]




this one looks cool, one of the most minimal calendar scripts i have seen in a while

---

### Post by mobilediesel on 2010-01-01
> **markp1989 said:**
> this one looks cool, one of the most minimal calendar scripts i have seen in a while

I like having the full calendar myself but I also have that particular script on my desktop. Sometimes minimalist just plain looks good. I think that's actually the one calendar script I came up with myself. The others were edits of other people's work.

Actually someone came up with a mock-up for that calendar so the idea was still not mine. I just figured out how to do it. :D

---

### Post by Bruce M. on 2010-01-02
> **mobilediesel said:**
> 
This is the normal calendar that highlights the current day plus holidays and birthdays depending on what the **remind** command has:


remind command? Can you show a sample?

Will it accept 20 or 30 birthdays?

Are the "holidays" flexible - not every country has the same holidays.

ie: Thanksgiving is celebrated on the fourth Thursday of November in the United States and on the second Monday of October in Canada.  Does this calendar accept dates like:

fourth Thursday of November
second Monday of October

Easter will be a tough one.  :)

I can hear ya now: *get off my case Bruce!!!!* :lolflag:

Have a GREAT 2010
Bruce

---

### Post by Bruce M. on 2010-01-02
ummmmmmmmm Oops!  HELP!

Here we go again with another round of:

**[CENTER]Fix that calendar![/CENTER]**

The code in question:
```
#!/bin/bash
cd $(dirname $0)
# horizontal calendar for conky by ans
# Updated by: mobilediesel, dk75, Bruce, Crinos512, et al.
# locale depend week day names
DOW=("Lu" "Ma" "Mi" "Ju" "Vi" "Sá" "Do")
if [ -f lang ]; then
    . lang
fi
COLOROLD="778899" #LightSlateGrey
COLORTODAY="FF8C00" #Darkorange
COLORREST="778899" #LightSlateGrey
COLORNEXT="445566" #MidSlateGrey
COLORSATURDAY="FFFF00"
COLORSUNDAY="FF8C00"
COLOR=("" "" "" "" "" "\${color $COLORSATURDAY}" "\${color $COLORSUNDAY}")
COLOREND=("" "" "" "" "" "\${color}" "\${color}")

TODAY=$(date +%-d)
LASTDAY=$(date -d "-$TODAY days +1 month" +%d)
FIRSTDAY=$(date -d "-$[$TODAY-1] days" +%u)

# Build $TOPLINE
k=$FIRSTDAY
for j in $(seq 31); do
  x=$[j+LASTDAY/j]
  case $j in
  	${j/#$x})	TOPLINE="$TOPLINE ${COLOR[$[k-1]]}${DOW[$[k-1]]}${COLOREND[$[k-1]]}";;
  	$[LASTDAY+1])	TOPLINE="$TOPLINE \${color $COLORNEXT}${DOW[$[k-1]]}";;
  	*)		TOPLINE="$TOPLINE ${DOW[$[k-1]]}";;
  esac
  k=$[${k/#7/0}+1]
done


BOTTOM=" \${color $COLOROLD}$(seq -w -s ' ' $LASTDAY|sed "s/.$TODAY \?/\${color $COLORTODAY}&\${color $COLORREST}/") \${color $COLORNEXT}$(seq -w -s ' ' 0$[31-$LASTDAY])"

echo "\${goto 240}$TOPLINE\${tab 20}"
echo "\${goto 240}$BOTTOM\${color}\${tab 20}"
```
and attached is the **[COLOR="DarkRed"]6 - "Oops!"[/COLOR]**

That **[COLOR="DarkOrchid"]6[/COLOR]** isn't suppose to be there

Have a nice day,
Bruce

PS: I gotta learn #! - crunchbang - shebang - bash scripting - whatever! :lolflag:

---

### Post by mobilediesel on 2010-01-02
> **Bruce M. said:**
> remind command? Can you show a sample?

Will it accept 20 or 30 birthdays?

Are the "holidays" flexible - not every country has the same holidays.

ie: Thanksgiving is celebrated on the fourth Thursday of November in the United States and on the second Monday of October in Canada.  Does this calendar accept dates like:

fourth Thursday of November
second Monday of October

Easter will be a tough one.  :)

I can hear ya now: *get off my case Bruce!!!!* :lolflag:

Have a GREAT 2010
Bruce

remind will handle pretty much any and all of that! It can be complicated to set up but you can do some tricky math with dates to figure out Easter and any other dates that change.

A few examples can be found at [http://wiki.43folders.com/index.php/Remind_Include_Files](http://wiki.43folders.com/index.php/Remind_Include_Files)
and [http://wiki.43folders.com/index.php/User:JamesRifkin/defs.rem](http://wiki.43folders.com/index.php/User:JamesRifkin/defs.rem)
There's even a section in there for all the Jewish holidays.
remind reads the **.reminders** file in your home directory. To keep holidays, birthdays and reminders separate you can keep them in separate files and **include** them in **.reminders**
**~/.reminders**:
```
include /home/mobilediesel/.remind/reminders.txt
include /home/mobilediesel/.remind/birthdays.txt
include /home/mobilediesel/.remind/holidays.txt

```
That points to a separate directory so I can easily synchronize them with my other computer.
**holidays.txt**:
```
SET Week_1 1
SET Week_2 8
SET Week_3 15
SET Week_4 22
FSET _last(mo) "1 " + MON((mo%12)+1)+" --7"
FSET _trig() TRIGGER(TRIGDATE())
FSET _back(days) TRIGGER(TODAY()-days)
SET SaveTrig $NumTrig
SET easter EASTERDATE(YEAR(TODAY()))
REM Jan 1 +5 MSG New Years Day %b
REM Mon Jan [Week_3] +5 MSG Martin Luther King - Day %b
REM Feb 2 +5 MSG Ground hog day %b
REM Feb 14 +5 MSG Valentines Day %b
REM mon feb [Week_3] +5 MSG Presidents Day %b
REM Mar 17 +5 MSG St Patricks Day %b
REM Sun Mar 8 ++5 MSG Daylight Saving Time starts %b
REM [TRIGGER(easter)] MSG Easter Sunday %b
REM Apr 1 +5 MSG April Fools Day %b
REM Apr 22 +14 MSG Earth Day %b
REM 5 may +5 MSG Cinco De Mayo %b
REM Sun May [Week_2] +7 MSG Mother's Day %b
REM mon Jun 1 -7 +5 MSG Memorial Day %b
REM Jun 14 +5 MSG Flag Day %b
REM Sun Jun [Week_3] +7 MSG Father's Day %b
REM Jul 4 +7 MSG Independence Day %b
REM Mon sep [Week_1] +5 MSG Labor Day %b
REM Mon Oct [Week_2] +5 MSG %"Columbus Day%" %b
REM Oct 31 +7 MSG Halloween %b
REM SUN Nov 1 ++5 MSG Daylight Saving Time ends %b
REM thu nov [Week_4] +7 MSG Thanksgiving Day %b
REM Nov 11 +5 MSG Veterans Day %b
REM Dec 24 MSG Christmas Eve %b
REM Dec 25 +25 MSG Christmas %b
REM Dec 31 MSG New Year's Eve %b
```
That list isn't complete yet.

**reminders.txt** can be set up with whatever reminders in the same way as the holidays.
**birthdays.txt**:
```
FSET _yr_num(yr) ORD(YEAR(TRIGDATE()) - yr)
REM Jan 2 MSG Taye Diggs' [_yr_num(1971)] birthday
```
Taye Diggs was put there as an example because he was the first to pop up on IMDB.com. Using that bit of extra code with the date, it will tell you how old the person is when it tells you about their birthday!

Damn right I make the computer remember stuff so I don't have to... :D

---

### Post by mobilediesel on 2010-01-02
> **Bruce M. said:**
> ummmmmmmmm Oops!  HELP!

Here we go again with another round of:

**[CENTER]Fix that calendar![/CENTER]**

The code in question:
...
and attached is the **[COLOR="DarkRed"]6 - "Oops!"[/COLOR]**

That **[COLOR="DarkOrchid"]6[/COLOR]** isn't suppose to be there

Have a nice day,
Bruce

PS: I gotta learn #! - crunchbang - shebang - bash scripting - whatever! :lolflag:

That 6 doesn't show up when I run that calendar. I copied/pasted the version from your post here, too. Now you'll have to show us the .conkyrc since I now believe that is the location of the errant **6**. :D

---

### Post by na12 on 2010-01-02
> **mobilediesel said:**
> I meant to. :D

Three simple calendar scripts that have been tweaked a bit since I last posted them.

This one shows the current day with the three previous and three following days with current day highlighted:
```
#!/bin/bash

font=("\${font vera:size=8}" "\${voffset -4}\${font vera:size=12}" "\${voffset -5}\${font vera:size=18}" "\${voffset -8}\${font vera:size=27}\${color ffffff}" "\${font vera:size=18}" "\${font vera:size=12}" "\${font vera:size=8}")
color=("" "" "" "\${color}" "" "" "")

for i in $(seq -3 3); do
echo -n "${font[$[i+3]]}$(date '+%d' -d "$i days")${color[3]}\${offset 3}"
done

```
[ATTACH]142011[/ATTACH]


Can you make vertical version?

---

### Post by mobilediesel on 2010-01-02
> **na12 said:**
> Can you make vertical version?

With a bit less tweaking than I thought:
```
#!/bin/bash

font=("\${font vera:size=8}" "\${font vera:size=12}" "\${font vera:size=18}" "\${font vera:size=27}\${color ffffff}" "\${font vera:size=18}" "\${font vera:size=12}" "\${font vera:size=8}")
color=("" "" "" "\${color}" "" "" "")

for i in $(seq -3 3); do
echo "${font[$[i+3]]}$(date '+%d' -d "$i days")${color[3]}\${font}"
done

```

---

### Post by Bruce M. on 2010-01-02
> **mobilediesel said:**
> That 6 doesn't show up when I run that calendar. I copied/pasted the version from your post here, too. Now you'll have to show us the .conkyrc since I now believe that is the location of the errant **6**. :D

:(  **This isn't good!** Not only does that colour ***NOT*** exist in my conky, I cannot find the six anywhere.  It has to be in the script somewhere.

```
background no
own_window no
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
use_xft yes
xftfont DejaVu Sans Mono:bold:size=8
xftalpha 1.0 #0.2
override_utf8_locale yes
update_interval 1
total_run_times 0
double_buffer yes
no_buffers yes
cpu_avg_samples 2
net_avg_samples 2
use_spacer none
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders yes
alignment tm
uppercase no
imlib_cache_size 0
# minimum_size 1280 1024 # minimum_size width & height
gap_x 0 # left-right
gap_y 20 # up-down
border_inner_margin 0
border_outer_margin 0
border_width 0

# Colors
default_color DCDCDC #Gainsboro
color0 FFD700 #Gold
color1 FFA07A #LightSalmon
color2 FF8C00 #Darkorange
color3 7FFF00 #Chartreuse
color4 778899 #LightSlateGrey
color5 FFDEAD #NavajoWhite
color6 00BFFF #DeepSkyBlue
#	colours below used by colorize script
color7 48D1CC #MediumTurquoise
color8 FFFF00 #Yellow
color9 FF0000 #Red
text_buffer_size 512 # Default
short_units yes
pad_percents 2
imlib_cache_size 0

TEXT
${goto 100}The Calendar:${color}${font DejaVu Sans Mono:Bold:size=10}${execpi 3600 /home/bruloo/Conky/scripts/conky_calhoriz.sh}${color}



${voffset -32}${goto 100}Mo & Yr:${goto 180}${font LCDMono:bold:size=24}${color6}${time %b}${goto 1000}${color3}${time %y}${font}${color}


${goto 100}My conky colors:${goto 240}${color}Default ${color0}0 ${color1}1 ${color2}2 ${color3}3 ${color4}4 ${color5}5 ${color6}6 ${color7}7 ${color8}8 ${color9}9 ${color}Default - Notice that color does NOT exist in my conky!

${goto 100}Default font:${execpi 3600 /home/bruloo/Conky/scripts/conky_calhoriz.sh} <<---  the SIX${color}

${goto 100}Default font:${execpi 3600 /home/bruloo/Conky/scripts/conky_calhoriz.sh}${color} <<---  the SIX

```

and */home/bruloo/Conky/scripts/conky_calhoriz.sh* one more time:

```
#!/bin/bash
cd $(dirname $0)
# horizontal calendar for conky by ans
# Updated by: mobilediesel, dk75, Bruce, Crinos512, et al.
# locale depend week day names
DOW=("Lu" "Ma" "Mi" "Ju" "Vi" "Sá" "Do")
if [ -f lang ]; then
    . lang
fi
COLOROLD="778899" #LightSlateGrey
COLORTODAY="FF8C00" #Darkorange
COLORREST="778899" #LightSlateGrey
COLORNEXT="445566" #MidSlateGrey
COLORSATURDAY="FFFF00"
COLORSUNDAY="FF8C00"
COLOR=("" "" "" "" "" "\${color $COLORSATURDAY}" "\${color $COLORSUNDAY}")
COLOREND=("" "" "" "" "" "\${color}" "\${color}")

TODAY=$(date +%-d)
LASTDAY=$(date -d "-$TODAY days +1 month" +%d)
FIRSTDAY=$(date -d "-$[$TODAY-1] days" +%u)

# Build $TOPLINE
k=$FIRSTDAY
for j in $(seq 31); do
  x=$[j+LASTDAY/j]
  case $j in
  	${j/#$x})	TOPLINE="$TOPLINE ${COLOR[$[k-1]]}${DOW[$[k-1]]}${COLOREND[$[k-1]]}";;
  	$[LASTDAY+1])	TOPLINE="$TOPLINE \${color $COLORNEXT}${DOW[$[k-1]]}";;
  	*)		TOPLINE="$TOPLINE ${DOW[$[k-1]]}";;
  esac
  k=$[${k/#7/0}+1]
done


BOTTOM=" \${color $COLOROLD}$(seq -w -s ' ' $LASTDAY|sed "s/.$TODAY \?/\${color $COLORTODAY}&\${color $COLORREST}/") \${color $COLORNEXT}$(seq -w -s ' ' 0$[31-$LASTDAY])"

echo "\${goto 240}$TOPLINE\${tab 20}"
echo "\${goto 240}$BOTTOM\${color}\${tab 20}"
```

Have a nice day.
Bruce

---

### Post by mobilediesel on 2010-01-02
> **Bruce M. said:**
> :(  **This isn't good!** Not only does that colour ***NOT*** exist in my conky, I cannot find the six anywhere.  It has to be in the script somewhere.


and */home/bruloo/Conky/scripts/conky_calhoriz.sh* one more time:


Have a nice day.
Bruce

I can't get it to do that without actually typing a 6 myself. Maybe one of the others that helped with the script can check it out.

Or try this one:
```
#!/bin/bash
cd $(dirname $0)
# horizontal and vertical calendar for conky by ans
# Updated by: mobilediesel, dk75, Bruce, Crinos512, et al.
# locale depend week day names
DOW=("Mo" "Tu" "We" "Th" "Fr" "Sa" "Su")
while getopts ":vl:" opts; do
case "$opts" in
l) lang=$OPTARG;;
v) orientation="$opts";;
esac
done
if [ -f lang ]; then
    . lang
fi
COLOROLD="445566" #MidSlateGrey
COLORTODAY="FF8C00" #Darkorange
COLORREST="445566" #MidSlateGrey
COLORNEXT="778899" #LightSlateGrey
COLORSATURDAY="FFFF00"
COLORSUNDAY="FF8C00"
COLOR=("" "" "" "" "" "\${color $COLORSATURDAY}" "\${color $COLORSUNDAY}")
COLOREND=("" "" "" "" "" "\${color}" "\${color}")

TODAY=$(date +%-d)
LASTDAY=$(date -d "-$TODAY days +1 month" +%d)
FIRSTDAY=$(date -d "-$[$TODAY-1] days" +%u)

# horizontal function
h () {
# Build $TOPLINE
k=$FIRSTDAY
for j in {1..31}; do
  x=$[j+LASTDAY/j]
  case $j in
  	${j/#$x})	TOPLINE="$TOPLINE ${COLOR[$[k-1]]}${DOW[$[k-1]]}${COLOREND[$[k-1]]}";;
  	$[LASTDAY+1])	TOPLINE="$TOPLINE \${color $COLORNEXT}${DOW[$[k-1]]}";;
  	*)		TOPLINE="$TOPLINE ${DOW[$[k-1]]}";;
  esac
  k=$[${k/#7/0}+1]
done

BOTTOM=" \${color $COLOROLD}$(seq -w -s ' ' $LASTDAY|sed "s/.$TODAY \?/\${color $COLORTODAY}&\${color $COLORREST}/") \${color $COLORNEXT}$(seq -w -s ' ' 0$[31-$LASTDAY])"

echo "\${goto 20}$TOPLINE\${tab 20}"
echo "\${goto 20}$BOTTOM\${color}\${tab 20}"
}

#vertical function
v () {
for i in $(seq 1 $[TODAY-1]); do
    TODAYC[$i]="\${color $COLOROLD}"
done
TODAYC[$TODAY]="\${color $COLORTODAY}"
for i in $(seq $[TODAY+1] $LASTDAY); do
    TODAYC[$i]="\${color $COLORREST}"
done

k=$FIRSTDAY
for j in $(seq $LASTDAY); do
  	echo  "${COLOR[$[k-1]]}${DOW[$[k-1]]} ${TODAYC[$j]}$(printf "%02d" $j)\${color}"
  k=$[${k/#7/0}+1]
done
}

# call function based on "$orientation"
${orientation:-h}
```

I named it conkycal.sh
call it with **-l es** for Spanish.
```
./conkycal.sh -l es
```
See if it does it with that version.

---

### Post by na12 on 2010-01-02
> **mobilediesel said:**
> With a bit less tweaking than I thought:
```
#!/bin/bash

font=("\${font vera:size=8}" "\${font vera:size=12}" "\${font vera:size=18}" "\${font vera:size=27}\${color ffffff}" "\${font vera:size=18}" "\${font vera:size=12}" "\${font vera:size=8}")
color=("" "" "" "\${color}" "" "" "")

for i in $(seq -3 3); do
echo "${font[$[i+3]]}$(date '+%d' -d "$i days")${color[3]}\${font}"
done

```
I think there is a problem with this script.

---

### Post by Bruce M. on 2010-01-02
> **mobilediesel said:**
> See if it does it with that version.

No 6 but ...

---

### Post by drpjkurian on 2010-01-03
Hi everybody

I have been trying to figure out what is conky for the past few days.

I was able to understand that it stands for wonderful graphics for desktop which is powered by several lines of codes.

May I know where shall I paste those codes in my machine?
Is it in terminal?

Thanks in advance

Dr Kurian

---

### Post by dk75 on 2010-01-03
All the scripts you must copy&paste to your text editor and save to a specific location.

Things with "own_window" and "TEXT" inside is configuration file for conky binnary itself.
You could save it whenever you like with any name but for convenience we save it in ~/conky or ~/.conky directory with names that tells us what for it is, like I have my config in file "~/.conky/.conkyrc-mrclock" since it is configuration file to run my MovingRingsCLOCK LUA script.

Character "~" is for your home directory and it is escape character for most Linux shells so if you type "cd ~" in your terminal it will brings you to your home directory. It's easier that way because it works for everyone (no need to explain why "/home/rosario/conky/myultrasuperduperconfig.txt" won't work with "antonio" user).

Then there are BASH scripts, usually with "#!/bin/sh" or "#!/bin/bash" at the beginning and these should be saved to files that is suggested in a post that contain it because config files depednds on it and have it's location hardcoded.

Personally I store all my conky BASH scripts in "~/.conky/conyparts" directory and I change every conky config file to point out bash script to that directory. But that is me.

There are PERL and PYTHON scripts also and again if they are used in conky configure file then there is hardcoded file path to them inside config file and thus it's better to save it in that specific location (unless you are experienced Linux and Conky user and you kow what are you doing when modificating others scripts/configuration).

And there are LUA script and again in conky config files posted here it have it's names and location where you must to save them.

After that you run
```
conky -c ~/conky/MyExtraLootOfWorkDoneConfig.hurray
```
to run Conky with that specified config file

---

### Post by mobilediesel on 2010-01-03
> **Bruce M. said:**
> No 6 but ...

?!?

Are you running more than one conky? I can't think of why there is extra characters after the end of the calendar. a **6** with the other script and **${}c** with this one.

Here's what it looks like here:
[ATTACH]142250[/ATTACH]

and no I didn't just crop out extra characters. :D

---

### Post by mobilediesel on 2010-01-03
> **na12 said:**
> I think there is a problem with this script.

That's really weird. It doesn't look like that on my machine. I'm not sure why it would output the **i** instead of the date...

Here's what it looks like on mine:
[ATTACH]142248[/ATTACH]

---

### Post by Bruce M. on 2010-01-03
> **drpjkurian said:**
> Hi everybody

I have been trying to figure out what is conky for the past few days.

I was able to understand that it stands for wonderful graphics for desktop which is powered by several lines of codes.

May I know where shall I paste those codes in my machine?
Is it in terminal?

Thanks in advance

Dr Kurian
Start here at [Conky Hardcore!]("http://conky.linux-hardcore.com/") and check out the [HowTo: A Beginners Guide to Setting up Conky]("http://conky.linux-hardcore.com/?page_id=1289")

If you need more, just ask.
Bruce

---

### Post by Bruce M. on 2010-01-03
> **mobilediesel said:**
> ?!?

Are you running more than one conky? I can't think of why there is extra characters after the end of the calendar. a **6** with the other script and **${}c** with this one.

Here's what it looks like here:
[ATTACH]142250[/ATTACH]

and no I didn't just crop out extra characters. :D

Trust me, I believe you.  I'm back to using calendar **[COLOR="DarkOrchid"]#6[/COLOR]**, for the sake of a name.

Yesterday I played with the Time/Date Manager quite a bit and it happens for the Month of January only - for any year!  My computer is bewitched.

C H I M O!
Bruce

---

### Post by dmillerct on 2010-01-03
> **Bruce M. said:**
> Trust me, I believe you.  I'm back to using calendar **[COLOR="DarkOrchid"]#6[/COLOR]**, for the sake of a name.

Yesterday I played with the Time/Date Manager quite a bit and it happens for the Month of January only - for any year!  My computer is bewitched.

C H I M O!
Bruce

The calendar configuration you are currently using is labeled #6? and the reason you are not using a different calender is because there is a rogue number 6 showing up? That sounds a bit too coincidental to me. 

How about checking the script where you call these from, perhaps it is possible the #6 configuration slipped into a section of the file it shouldn't have?

---

### Post by Bruce M. on 2010-01-03
> **dmillerct said:**
> The calendar configuration you are currently using is labeled #6? and the reason you are not using a different calender is because there is a rogue number 6 showing up? That sounds a bit too coincidental to me. 

How about checking the script where you call these from, perhaps it is possible the #6 configuration slipped into a section of the file it shouldn't have?

NO NO NO --- this is tooo funny.  Tha calendar script I am using is located at and called: /home/bruloo/Conky/scripts/conky_calhoriz.sh

I said I'm using the "#6" calendar as it displays that 6 for any year during the month of January.  I have others here I will try but this is one strange "Rod Sterling" type thing here.

Ummmm, I sent the script to mobilediesel, and he tried it and no 6 appeared, I posted my conky that uses it and the script in post: [#55]("http://ubuntuforums.org/showpost.php?p=8598332&postcount=55").  Have a look see.

The other script MD gave me left a group of characters: [Post #58]("http://ubuntuforums.org/showpost.php?p=8599137&postcount=58")

I'm telling you: **my computer it living in the [COLOR="DarkRed"]Twilight Zone[/COLOR].**

Have a nice day.
Bruce

---

### Post by mobilediesel on 2010-01-03
> **Bruce M. said:**
> NO NO NO --- this is tooo funny.  Tha calendar script I am using is located at and called: /home/bruloo/Conky/scripts/conky_calhoriz.sh

I said I'm using the "#6" calendar as it displays that 6 for any year during the month of January.  I have others here I will try but this is one strange "Rod Sterling" type thing here.

Ummmm, I sent the script to mobilediesel, and he tried it and no 6 appeared, I posted my conky that uses it and the script in post: [#55]("http://ubuntuforums.org/showpost.php?p=8598332&postcount=55").  Have a look see.

The other script MD gave me left a group of characters: [Post #58]("http://ubuntuforums.org/showpost.php?p=8599137&postcount=58")

I'm telling you: **my computer it living in the [COLOR="DarkRed"]Twilight Zone[/COLOR].**

Have a nice day.
Bruce

Well, I fixed a calendar script that no one was complaining about. :lol:
```
#!/bin/bash

# uncomment the following line for starting the week on Monday instead of Sunday.
#t=u;m=-1
DAY=$(date +%_d)
bow=$(date -d "-$[$(date +%${t:-w})$m] days")
week="$(date '+%_d' -d "$bow")"
for i in $(seq 1 6); do
week="$week $(date +%_d -d "$bow $i days")"
done
echo "$week"|sed "s/$DAY\>/\${color ffffff}&\${color}/"
```
For week starting on Sunday:
[ATTACH]142304[/ATTACH]
For week starting on Monday:
[ATTACH]142305[/ATTACH]

Now if I can figure out what's wrong with the script you're trying to use... :D

You already gave the .conkyrc for it and that didn't make it display wrong on my system either. You're just a bit too far south to be near the Bermuda Triangle..

At the moment I'm out of ideas on that.

---

### Post by na12 on 2010-01-03
> **mobilediesel said:**
> That's really weird. It doesn't look like that on my machine. I'm not sure why it would output the **i** instead of the date...

Here's what it looks like on mine:
[ATTACH]142248[/ATTACH]
Show up your conkyrc

---

### Post by mobilediesel on 2010-01-03
> **na12 said:**
> Show up your conkyrc

```
override_utf8_locale yes
own_window_title middle
use_xft yes
background yes
xftfont vera:size=10
alignment top_middle
xftalpha 1
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
stippled_borders 10
border_margin 4
border_width 1
default_shade_color grey
default_outline_color black
use_spacer none
no_buffers yes
uppercase no
default_color 99ccff #Light Blue
color0 4040ff #Blue
color1 40ff40 #Green
color2 ff4040 #Red
color3 ffffff #White
color4 aa40aa #Purple
color5 c08040 #Brown
color6 ffff40 #Yellow
color7 aaaaaa #Gray
color8 808080 #Dark Gray
color9 4040aa #Dark Blue
text_buffer_size 4096
minimum_size 285
TEXT
${execpi 3600 $HOME/conky/week_vert.sh}

```
week_vert.sh:
```
#!/bin/bash

font=("\${font vera:size=8}" "\${font vera:size=12}" "\${font vera:size=18}" "\${font vera:size=27}\${color ffffff}" "\${font vera:size=18}" "\${font vera:size=12}" "\${font vera:size=8}")
color=("" "" "" "\${color}" "" "" "")

for i in $(seq -3 3); do
echo "${font[$[i+3]]}$(date '+%d' -d "$i days")${color[3]}\${font}"
done

```

---

### Post by Defiant Rat on 2010-01-03
Hi guys, I just started playing around with conky (its kind of addictive isnt it :D )And was wondering if anyone could help me get my CPU temp showing in conky.

This is the lm_sensors output:
```
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:     +1.34 V  (min =  +0.85 V, max =  +1.60 V)
 +3.3 Voltage:     +3.36 V  (min =  +2.97 V, max =  +3.63 V)
 +5 Voltage:       +4.92 V  (min =  +4.50 V, max =  +5.50 V)
 +12 Voltage:     +12.22 V  (min = +10.20 V, max = +13.80 V)
CPU FAN Speed:    3125 RPM  (min =  600 RPM)
CHASSIS FAN Speed:1201 RPM  (min =  600 RPM)
POWER FAN Speed:  1315 RPM  (min =  600 RPM)
CPU Temperature:   +45.0°C  (high = +60.0°C, crit = +95.0°C)  
MB Temperature:    +33.0°C  (high = +45.0°C, crit = +75.0°C)  
```

But how do i get that into conky?

If it makes a difference, im using lm_sensors 3.1.1

Cheers :)

---

### Post by dmillerct on 2010-01-03
> **Defiant Rat said:**
> Hi guys, I just started playing around with conky (its kind of addictive isnt it :D )And was wondering if anyone could help me get my CPU temp showing in conky.

This is the lm_sensors output:
```
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:     +1.34 V  (min =  +0.85 V, max =  +1.60 V)
 +3.3 Voltage:     +3.36 V  (min =  +2.97 V, max =  +3.63 V)
 +5 Voltage:       +4.92 V  (min =  +4.50 V, max =  +5.50 V)
 +12 Voltage:     +12.22 V  (min = +10.20 V, max = +13.80 V)
CPU FAN Speed:    3125 RPM  (min =  600 RPM)
CHASSIS FAN Speed:1201 RPM  (min =  600 RPM)
POWER FAN Speed:  1315 RPM  (min =  600 RPM)
CPU Temperature:   +45.0°C  (high = +60.0°C, crit = +95.0°C)  
MB Temperature:    +33.0°C  (high = +45.0°C, crit = +75.0°C)  
```

But how do i get that into conky?

If it makes a difference, im using lm_sensors 3.1.1

Cheers :)

Welcome. Conky Hardcore is probably the best place for you to get acquainted will all the wondrous things conky can do. Here is the section on using sensors:

[http://conky.linux-hardcore.com/?page_id=393]("http://conky.linux-hardcore.com/?page_id=393")

---

### Post by na12 on 2010-01-04
> **mobilediesel said:**
> ```
override_utf8_locale yes
own_window_title middle
use_xft yes
background yes
xftfont vera:size=10
alignment top_middle
xftalpha 1
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
stippled_borders 10
border_margin 4
border_width 1
default_shade_color grey
default_outline_color black
use_spacer none
no_buffers yes
uppercase no
default_color 99ccff #Light Blue
color0 4040ff #Blue
color1 40ff40 #Green
color2 ff4040 #Red
color3 ffffff #White
color4 aa40aa #Purple
color5 c08040 #Brown
color6 ffff40 #Yellow
color7 aaaaaa #Gray
color8 808080 #Dark Gray
color9 4040aa #Dark Blue
text_buffer_size 4096
minimum_size 285
TEXT
${execpi 3600 $HOME/conky/week_vert.sh}

```
week_vert.sh:
```
#!/bin/bash

font=("\${font vera:size=8}" "\${font vera:size=12}" "\${font vera:size=18}" "\${font vera:size=27}\${color ffffff}" "\${font vera:size=18}" "\${font vera:size=12}" "\${font vera:size=8}")
color=("" "" "" "\${color}" "" "" "")

for i in $(seq -3 3); do
echo "${font[$[i+3]]}$(date '+%d' -d "$i days")${color[3]}\${font}"
done

```
Now is ok. I need to put "text_buffer_size 4096" in conkyrc.

---

### Post by djyoung4 on 2010-01-04
> **Bruce M. said:**
> NO NO NO --- this is tooo funny.  Tha calendar script I am using is located at and called: /home/bruloo/Conky/scripts/conky_calhoriz.sh

I said I'm using the "#6" calendar as it displays that 6 for any year during the month of January.  I have others here I will try but this is one strange "Rod Sterling" type thing here.

Ummmm, I sent the script to mobilediesel, and he tried it and no 6 appeared, I posted my conky that uses it and the script in post: [#55]("http://ubuntuforums.org/showpost.php?p=8598332&postcount=55").  Have a look see.

The other script MD gave me left a group of characters: [Post #58]("http://ubuntuforums.org/showpost.php?p=8599137&postcount=58")

I'm telling you: **my computer it living in the [COLOR="DarkRed"]Twilight Zone[/COLOR].**

Have a nice day.
Bruce
all i have to say is wtf.  I ran ur config on my comp and there was no 6.  maybe you should get a witch doctor or something for your comp.

---

### Post by Bruce M. on 2010-01-04
> **mobilediesel said:**
> 
For week starting on Sunday:
[ATTACH]142304[/ATTACH]
For week starting on Monday:
[ATTACH]142305[/ATTACH]

But they don line up.  Notice how the one with the days 3 to 9 ia a shorter image than the one with the days from 28 to three.

Needs a leading 0 in there.

Actutally coming from a "non" programmer that would be good for a "Get lost!" answer. {keeping in mind the family flavour of the forums} :)

> **mobilediesel said:**
> 
Now if I can figure out what's wrong with the script you're trying to use... :D

You already gave the .conkyrc for it and that didn't make it display wrong on my system either. You're just a bit too far south to be near the Bermuda Triangle..

At the moment I'm out of ideas on that.

I told you: My Computer is either:

[LIST=1]
[*]bewitched,
[*]living in "The Twilight Zone",
[*]came from "The Outer Limits", or
[*]all of the above
[/LIST]

It's not the script, if it was "everyone" would see the: [SIZE="6"]6[/SIZE].

CHIMO!
Bruce

---

### Post by mobilediesel on 2010-01-04
> **Bruce M. said:**
> But they don line up.  Notice how the one with the days 3 to 9 ia a shorter image than the one with the days from 28 to three.

Needs a leading 0 in there.

Actutally coming from a "non" programmer that would be good for a "Get lost!" answer. {keeping in mind the family flavour of the forums} :)

This'll get the leading zeros in there:
```
#!/bin/bash

# uncomment the following line for starting the week on Monday instead of Sunday.
#t=u;m=-1
DAY=$(date +%d)
bow=$(date -d "-$[$(date +%${t:-w})$m] days")
week="$(date '+%d' -d "$bow")"
for i in $(seq 1 6); do
week="$week $(date +%d -d "$bow $i days")"
done
echo "$week"|sed "s/$DAY\>/\${color ffffff}&\${color}/"
```

> **Bruce M. said:**
> I told you: My Computer is either:

[LIST=1]
[*]bewitched,
[*]living in "The Twilight Zone",
[*]came from "The Outer Limits", or
[*]all of the above
[/LIST]

It's not the script, if it was "everyone" would see the: [SIZE="6"]6[/SIZE].

CHIMO!
Bruce

Bewitched in the Outer Limits of The Twilight Zone.
I've probably seen nearly all episodes of all three of those shows! :lol:

---

### Post by PuddingKnife on 2010-01-04
I was thinking of trying Conky out.. 

I was wondering if it was possible to replicate this using Conky:

[http://drewman702.files.wordpress.com/2009/03/rainmeter.jpg](http://drewman702.files.wordpress.com/2009/03/rainmeter.jpg)

?

---

### Post by Bruce M. on 2010-01-04
> **mobilediesel said:**
> Bewitched in the Outer Limits of The Twilight Zone.

Now that would be a show:

**Bewitched in the Outer Limits of The Twilight Zone broadcasted live from the Bermuda Triangle!**

---

### Post by Bruce M. on 2010-01-04
> **PuddingKnife said:**
> I was thinking of trying Conky out.. 

I was wondering if it was possible to replicate this using Conky:

[http://drewman702.files.wordpress.com/2009/03/rainmeter.jpg](http://drewman702.files.wordpress.com/2009/03/rainmeter.jpg)

?

For the stuff on the right and left - YES.

The stuff in the middle, id those folder are "interactive" NO.  At least not yet.  :)

Have a nice day.
Bruce

---

### Post by mobilediesel on 2010-01-05
> **Bruce M. said:**
> Now that would be a show:

**Bewitched in the Outer Limits of The Twilight Zone broadcasted live from the Bermuda Triangle!**

I would totally watch that!

---

### Post by PuddingKnife on 2010-01-05
> **Bruce M. said:**
> For the stuff on the right and left - YES.

The stuff in the middle, id those folder are "interactive" NO.  At least not yet.  :)

Have a nice day.
Bruce

Excellent. Conky appears to be quite complicated, so it'll probably be a few days for me to read up on it, but it looks really interesting. 

I just kind of wish there a GUI to configure it.

---

### Post by mobilediesel on 2010-01-05
> **PuddingKnife said:**
> Excellent. Conky appears to be quite complicated, so it'll probably be a few days for me to read up on it, but it looks really interesting. 

I just kind of wish there a GUI to configure it.

[http://sourceforge.net/projects/conkygui/](http://sourceforge.net/projects/conkygui/)

I haven't used that myself but it looks like a good place to start. Then you can look at the config file it puts out and learn how to tweak from there.

---

### Post by Bruce M. on 2010-01-05
> **mobilediesel said:**
> I would totally watch that!

And I'd be fighting with you for the :popcorn:

---

### Post by darco on 2010-01-05
Is there anyway to stop outputs from shifting back and forth? For example, my  cpu (quad core) outputs will update then it will  shift my horizontal conky script back and forth. 
Trying to  make these readings more static like.

thxs

---

### Post by mobilediesel on 2010-01-05
> **darco said:**
> Is there anyway to stop outputs from shifting back and forth? For example, my  cpu (quad core) outputs will update then it will  shift my horizontal conky script back and forth. 
Trying to  make these readings more static like.

thxs

Use a mono-spaced font. add this in front:
```
${font monospace}
```
cuz that's the only one I could think of. That would keep things lined up better.

---

### Post by mobilediesel on 2010-01-05
> **Bruce M. said:**
> And I'd be fighting with you for the :popcorn:

Is conkycal_horiz.sh still showing a **6** or other weirdness after it? I've been messing with the script a bit and can't make it do that without typing a **6** in there myself.

I think I may have figured a way to make the script even a bit smaller. I don't know if it'll work yet. Good thing I keep working backups of things like that. :D

---

### Post by darco on 2010-01-05
> **mobilediesel said:**
> Use a mono-spaced font. add this in front:
```
${font monospace}
```
cuz that's the only one I could think of. That would keep things lined up better.

Ok I was hoping that using mono fonts wasnt the answer. Yes it does seem to work along with  the user_spacer right but the fonts are super ugly!
Using the Bitstream Vera Sans Mono but before was using Liberation Sans. Any better looking mono fonts?

thxs

---

### Post by mobilediesel on 2010-01-05
> **darco said:**
> Ok I was hoping that using mono fonts wasnt the answer. Yes it does seem to work along with  the user_spacer right but the fonts are super ugly!
Using the Bitstream Vera Sans Mono but before was using Liberation Sans. Any better looking mono fonts?

thxs

Most of the default mono spaced fonts do suck.
You could try [http://www.1001fonts.com/fonts_overview.html?page=1&category_id=7](http://www.1001fonts.com/fonts_overview.html?page=1&category_id=7)
or [http://www.urbanfonts.com/fonts/monospaced-fonts.htm](http://www.urbanfonts.com/fonts/monospaced-fonts.htm)
There's bound to be a couple you like.

---

### Post by Bruce M. on 2010-01-05
> **mobilediesel said:**
> Is conkycal_horiz.sh still showing a **6** or other weirdness after it? I've been messing with the script a bit and can't make it do that without typing a **6** in there myself.

I think I may have figured a way to make the script even a bit smaller. I don't know if it'll work yet. Good thing I keep working backups of things like that. :D

Yup, still showing the 6 - when I get around to ot I'll try an "eralier" version of it, I have most of them here - they were coming so fast and furious I thought it was a movie.  have to do it before Feb though as it works well other than January (any year)

CHIMO!
Bruce

---

### Post by Bruce M. on 2010-01-05
> **darco said:**
> Ok I was hoping that using mono fonts wasnt the answer. Yes it does seem to work along with  the user_spacer right but the fonts are super ugly!
Using the Bitstream Vera Sans Mono but before was using Liberation Sans. Any better looking mono fonts?

thxs

That are a LOT of nice looking mono fonts look at the bottom of the page: [Spacing]("http://conky.linux-hardcore.com/?page_id=87")

Also if it's what I think it is it may not be necessary.  Put your old font back and take a couple of screenshots with the differences.

Ahhhh heck, maybe you can find the answer [here]("http://conky.linux-hardcore.com/?page_id=3651") using ${gotos} or ${offsets}

Have a nice day.
Bruce

---

### Post by PuddingKnife on 2010-01-05
Just so I can be done hijacking this thread  :)

[http://ubuntuforums.org/showthread.php?t=1373211](http://ubuntuforums.org/showthread.php?t=1373211)

---

### Post by The Real Dave on 2010-01-05
> **Bruce M. said:**
> For the stuff on the right and left - YES.

The stuff in the middle, id those folder are "interactive" NO.  At least not yet.  :)

Have a nice day.
Bruce

Wait, can I ask, in the link you were talking about, left hand side, how do you get the CPU and RAM details to look like that, the border? 

And, the folders in the middle are from a dock such as AWN or Cario and are called stacks :)

---

### Post by darco on 2010-01-05
> **Bruce M. said:**
> That are a LOT of nice looking mono fonts look at the bottom of the page: [Spacing]("http://conky.linux-hardcore.com/?page_id=87")

Also if it's what I think it is it may not be necessary.  Put your old font back and take a couple of screenshots with the differences.

Ahhhh heck, maybe you can find the answer [here]("http://conky.linux-hardcore.com/?page_id=3651") using ${gotos} or ${offsets}

Have a nice day.
Bruce

Well, I somewhat succeededin what I want my scrip to do. On my second line, the HDD activity no longer shifts to the right but the CPU next to it still shifts over. I tried adding the same line that is in front of the HDD but it didnt work.
```
 
#background yes
double_buffer yes
use_xft yes
xftalpha 0.8
xftfont Liberation Mono:style=Bold:size=9
update_interval 0.5
own_window_type normal
own_window_transparent yes
own_window yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
draw_shades no
draw_outline no
draw_borders no
border_inner_margin 0
border_outer_margin 3
border_width 1
default_color white
alignment top_middle
#no_buffers yes
use_spacer right
minimum_size 1680 1050
# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 4

TEXT

${goto 30}${color #FFFFFF}Computer:${color #32CD32} ${nodename} ${color #FFFFFF}|  Kernel:${color  #32CD32} $kernel on $machine${color  #FFFFFF}   |   Mem: ${color #32CD32}${font}${mem} ${color} ${color #06FF00} ${color #FFFFFF}|  Local IP: ${color #32CD32}${addr eth0}  ${color} |  Up: ${color #32CD32}${font}${uptime_short}${color}  | ${color} Net: ${color #32CD32}${font}${downspeed eth0}Kb/s ${color} ${totaldown eth0} down${color} | ${color} ${color #32CD32}${upspeed eth0}Kb/s ${color} ${totalup eth0} up${color}  |  Home: ${color #32CD32}${fs_free /home} ${color white}|  GPU Temp: ${color green}${execi 60 nvidia-settings -query GPUCoreTemp | perl -ne 'print $1 if /GPUCoreTemp.*?: (\d+)./;'}°C$voffset  ${color #FFFFFF}

${font monospace}${goto 600}${font Liberation Mono:bold:size=9} HDD Activity:${color #32CD32} ${diskio}${color #FFFFFF} |  Q6600: ${color #FF0707}${cpu cpu1},${cpu cpu2},${cpu cpu3},${cpu cpu4} ${color} | ${exec sensors| grep 'Core 0'|cut -c1-20|sed '/^$/d'}

```

---

### Post by Bruce M. on 2010-01-05
Well, since this thread is about *"Supports Scripts"* for Conky as the scripts were over running the "[Post your .conkyrc files w/ screenshots]("http://ubuntuforums.org/showthread.php?t=281865&page=1134")" I think I, for one anyway, will stop talking conky here and stop talking scripts over there to help keep things on topic.

**NOTE:** I talk conky in any conky thread in any distro (that I have found)

And **my home** Conky Support Thread can be found here: [Conky Hardcore! Support Forum]("http://linux-hardcore.com/index.php?board=80.0").

Have a nice day.
Bruce

---

### Post by londonali1010 on 2010-01-05
I've been playing around with Cairo text extents and the new ARGB feature (proper transparency!), and I've come up with this...Although I'm not entirely sure why you'd want to use Conky to do it; it's kind of like using a sledgehammer to crack a nut!  Still, it *can* be done!  Not an altogether elegant script, but it does the trick!

**EDIT**: I should mention that you will need at least v1.8.0_rc1 for these features to work!
```
--[[ SHINY CALENDAR PAGE WIDGET ]]
--[[ v1.0 by londonali1010 (2009) ]]
--[[ Options (xc, yc, size, bg_colour, fg_colour, alpha)
	"xc" and "yc" are the x and y coordinates of the centre of the widget, in pixels, relative to the top left of the Conky window.
	"size" is the width of the widget (which is square).
	"bg_colour" is the colour, in format 0xRRGGBB, of the widget's background.
	"fg_colour" is the colour of the widget's text.
	"alpha" is the opacity (0.0 -> 1.0) of the widget. ]]

function calpage(xc, yc, size, bgc, fgc, alpha)
	local function rgb_to_r_g_b(colour, alpha)
		return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
	end
	
	local function rrect()
		cairo_move_to(cr, x0 + 0.1*size, y0)
		cairo_line_to(cr, x0 + 0.9*size, y0)
		cairo_curve_to(cr, x0 + size, y0, x0 + size, y0, x0 + size, y0 + 0.1*size)
		cairo_line_to(cr, x0 + size, y0 + 0.9*size)
		cairo_curve_to(cr, x0 + size, y0 + size, x0 + size, y0 + size, x0 + 0.9*size, y0 + size)
		cairo_line_to(cr, x0 + 0.1*size, y0 + size)
		cairo_curve_to(cr, x0, y0 + size, x0, y0 + size, x0, y0 + 0.9*size)
		cairo_line_to(cr, x0, y0 + 0.1*size)
		cairo_curve_to(cr, x0, y0, x0, y0, x0 + 0.1*size, y0)
		cairo_close_path(cr)	
	end

	local function background()
		local r, g, b, a = rgb_to_r_g_b(bgc, alpha)
		rrect()
		cairo_set_source_rgba(cr, r, g, b, a)
		cairo_fill_preserve(cr)

		linpat = cairo_pattern_create_linear(xc, yc, xc, yc + size)
		cairo_pattern_add_color_stop_rgba(linpat, 0, 1.0, 1.0, 1.0, 0.2*a)
		cairo_pattern_add_color_stop_rgba(linpat, 1, 1.0, 1.0, 1.0, 0)
		cairo_set_source(cr, linpat)
		cairo_fill_preserve(cr)
		cairo_clip(cr)		

		rrect()
		cairo_set_source_rgba(cr, r, g, b, a)
		cairo_set_line_width(cr, 0.05*size)
		cairo_stroke_preserve(cr)
		
		cairo_new_path(cr)
		cairo_arc(cr, xc, yc - size, size, 0, 2*math.pi)

		radpat = cairo_pattern_create_radial(xc, yc - size, 0, xc, yc - size, size)
		cairo_pattern_add_color_stop_rgba(radpat, 0, 1.0, 1.0, 1.0, a)
		cairo_pattern_add_color_stop_rgba(radpat, 1, 1.0, 1.0, 1.0, 0.2*a)
		cairo_set_source(cr, radpat)
		cairo_fill(cr)
	end

	local function set_font_sizes()
		day_size = 1000.0
		date_size = 1000.0
		month_size = 1000.0
		
		local extents = cairo_text_extents_t:create()
		cairo_select_font_face(cr, "Petita Medium", CAIRO_FONT_SLANT_NORMAL, CAIRO_FONT_WEIGHT_NORMAL)
		cairo_set_font_size(cr, day_size)
		cairo_text_extents(cr, day, extents)
		local w = math.abs(extents.width)
		local h = math.abs(extents.y_bearing)
		local scale_w = 0.8*size / w
		local scale_h = 0.1*size / h
		local scale
		if scale_w < scale_h then scale = scale_w else scale = scale_h end
		day_size = scale * day_size

		cairo_set_font_size(cr, date_size)
		cairo_text_extents(cr, date, extents)
		w = math.abs(extents.width)
		h = math.abs(extents.y_bearing)
		scale_w = 0.6*size / w
		scale_h = 0.6*size / h
		if scale_w < scale_h then scale = scale_w else scale = scale_h end
		date_size = scale * date_size

		cairo_set_font_size(cr, month_size)
		cairo_text_extents(cr, month, extents)
		w = math.abs(extents.width)
		h = math.abs(extents.y_bearing)
		scale_w = 0.8*size / w
		scale_h = 0.1*size / h
		if scale_w < scale_h then scale = scale_w else scale = scale_h end
		month_size = scale * month_size
			
		return day_size, date_size, month_size
	end

	local function draw_text()
		local extents = cairo_text_extents_t:create()
		cairo_set_source_rgba(cr, rgb_to_r_g_b(fgc, alpha))

		cairo_set_font_size(cr, day_size)
		cairo_text_extents(cr, day, extents)
		cairo_move_to(cr, x0 + size/2 - extents.x_advance/2, y0 + 0.2*size)
		cairo_show_text(cr, day)

		cairo_set_font_size(cr, date_size)
		cairo_text_extents(cr, date, extents)
		cairo_move_to(cr, x0 + size/2 - extents.x_advance/2, y0 + 0.5*size - extents.y_bearing/2)
		cairo_show_text(cr, date)

		cairo_set_font_size(cr, month_size)
		cairo_text_extents(cr, month, extents)
		cairo_move_to(cr, x0 + size/2 - extents.x_advance/2, y0 + 0.9*size)
		cairo_show_text(cr, month)
	end

	x0, y0 = xc - size/2, yc - size/2	
	day = os.date("%A")
	date = os.date("%d")
	month = os.date("%B")

	background()
	day_size, date_size, month_size = set_font_sizes()
	draw_text(day_size, date_size, month_size)
end

--[[ END SHINY CALENDAR WIDGET ]]
```
[ATTACH]142594[/ATTACH]

---

### Post by dmillerct on 2010-01-05
> **londonali1010 said:**
> I've been playing around with Cairo text extents and the new ARGB feature (proper transparency!), and I've come up with this...Although I'm not entirely sure why you'd want to use Conky to do it; it's kind of like using a sledgehammer to crack a nut!  Still, it *can* be done!  Not an altogether elegant script, but it does the trick!
```
--[[ SHINY CALENDAR PAGE WIDGET ]]
--[[ v1.0 by londonali1010 (2009) ]]
--[[ Options (xc, yc, size, bg_colour, fg_colour, alpha)
	"xc" and "yc" are the x and y coordinates of the centre of the widget, in pixels, relative to the top left of the Conky window.
	"size" is the width of the widget (which is square).
	"bg_colour" is the colour, in format 0xRRGGBB, of the widget's background.
	"fg_colour" is the colour of the widget's text.
	"alpha" is the opacity (0.0 -> 1.0) of the widget. ]]

function calpage(xc, yc, size, bgc, fgc, alpha)
	local function rgb_to_r_g_b(colour, alpha)
		return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
	end
	
	local function rrect()
		cairo_move_to(cr, x0 + 0.1*size, y0)
		cairo_line_to(cr, x0 + 0.9*size, y0)
		cairo_curve_to(cr, x0 + size, y0, x0 + size, y0, x0 + size, y0 + 0.1*size)
		cairo_line_to(cr, x0 + size, y0 + 0.9*size)
		cairo_curve_to(cr, x0 + size, y0 + size, x0 + size, y0 + size, x0 + 0.9*size, y0 + size)
		cairo_line_to(cr, x0 + 0.1*size, y0 + size)
		cairo_curve_to(cr, x0, y0 + size, x0, y0 + size, x0, y0 + 0.9*size)
		cairo_line_to(cr, x0, y0 + 0.1*size)
		cairo_curve_to(cr, x0, y0, x0, y0, x0 + 0.1*size, y0)
		cairo_close_path(cr)	
	end

	local function background()
		local r, g, b, a = rgb_to_r_g_b(bgc, alpha)
		rrect()
		cairo_set_source_rgba(cr, r, g, b, a)
		cairo_fill_preserve(cr)

		linpat = cairo_pattern_create_linear(xc, yc, xc, yc + size)
		cairo_pattern_add_color_stop_rgba(linpat, 0, 1.0, 1.0, 1.0, 0.2*a)
		cairo_pattern_add_color_stop_rgba(linpat, 1, 1.0, 1.0, 1.0, 0)
		cairo_set_source(cr, linpat)
		cairo_fill_preserve(cr)
		cairo_clip(cr)		

		rrect()
		cairo_set_source_rgba(cr, r, g, b, a)
		cairo_set_line_width(cr, 0.05*size)
		cairo_stroke_preserve(cr)
		
		cairo_new_path(cr)
		cairo_arc(cr, xc, yc - size, size, 0, 2*math.pi)

		radpat = cairo_pattern_create_radial(xc, yc - size, 0, xc, yc - size, size)
		cairo_pattern_add_color_stop_rgba(radpat, 0, 1.0, 1.0, 1.0, a)
		cairo_pattern_add_color_stop_rgba(radpat, 1, 1.0, 1.0, 1.0, 0.2*a)
		cairo_set_source(cr, radpat)
		cairo_fill(cr)
	end

	local function set_font_sizes()
		day_size = 1000.0
		date_size = 1000.0
		month_size = 1000.0
		
		local extents = cairo_text_extents_t:create()
		cairo_select_font_face(cr, "Petita Medium", CAIRO_FONT_SLANT_NORMAL, CAIRO_FONT_WEIGHT_NORMAL)
		cairo_set_font_size(cr, day_size)
		cairo_text_extents(cr, day, extents)
		local w = math.abs(extents.width)
		local h = math.abs(extents.y_bearing)
		local scale_w = 0.8*size / w
		local scale_h = 0.1*size / h
		local scale
		if scale_w < scale_h then scale = scale_w else scale = scale_h end
		day_size = scale * day_size

		cairo_set_font_size(cr, date_size)
		cairo_text_extents(cr, date, extents)
		w = math.abs(extents.width)
		h = math.abs(extents.y_bearing)
		scale_w = 0.6*size / w
		scale_h = 0.6*size / h
		if scale_w < scale_h then scale = scale_w else scale = scale_h end
		date_size = scale * date_size

		cairo_set_font_size(cr, month_size)
		cairo_text_extents(cr, month, extents)
		w = math.abs(extents.width)
		h = math.abs(extents.y_bearing)
		scale_w = 0.8*size / w
		scale_h = 0.1*size / h
		if scale_w < scale_h then scale = scale_w else scale = scale_h end
		month_size = scale * month_size
			
		return day_size, date_size, month_size
	end

	local function draw_text()
		local extents = cairo_text_extents_t:create()
		cairo_set_source_rgba(cr, rgb_to_r_g_b(fgc, alpha))

		cairo_set_font_size(cr, day_size)
		cairo_text_extents(cr, day, extents)
		cairo_move_to(cr, x0 + size/2 - extents.x_advance/2, y0 + 0.2*size)
		cairo_show_text(cr, day)

		cairo_set_font_size(cr, date_size)
		cairo_text_extents(cr, date, extents)
		cairo_move_to(cr, x0 + size/2 - extents.x_advance/2, y0 + 0.5*size - extents.y_bearing/2)
		cairo_show_text(cr, date)

		cairo_set_font_size(cr, month_size)
		cairo_text_extents(cr, month, extents)
		cairo_move_to(cr, x0 + size/2 - extents.x_advance/2, y0 + 0.9*size)
		cairo_show_text(cr, month)
	end

	x0, y0 = xc - size/2, yc - size/2	
	day = os.date("%A")
	date = os.date("%d")
	month = os.date("%B")

	background()
	day_size, date_size, month_size = set_font_sizes()
	draw_text(day_size, date_size, month_size)
end

--[[ END SHINY CALENDAR WIDGET ]]
```
[ATTACH]142594[/ATTACH]

Wow thats cool! Obviously requires 1.8 correct?

---

### Post by londonali1010 on 2010-01-05
> **dmillerct said:**
> Wow thats cool! Obviously requires 1.8 correct?

Ah, yes, should have mentioned that in my post...Will do so now!

---

### Post by Bruce M. on 2010-01-05
> **londonali1010 said:**
> Although I'm not entirely sure why you'd want to use Conky to do it; it's kind of like using a sledgehammer to crack a nut!

That is so good - powdered nuts.  :)

I tried 1.8.0-rc1 with #! - [IMG]http://conky.linux-hardcore.com/wp-content/uploads/2010/01/My_Custom.gif[/IMG] - back to 1.7.2

Have a GREAT day.
Bruce

---

### Post by mobilediesel on 2010-01-11
I updated the horizontal/vertical calendar script a bit.
Just a bit of tweaking.
[conkycal.sh]("http://dl.dropbox.com/u/1055489/scripts/conkycal.sh"):
```
#!/bin/bash
cd $(dirname $0)
# horizontal and vertical calendar for conky by ans
# Updated by: mobilediesel, dk75, Bruce, Crinos512, et al.
# locale depend week day names
DOW=("Mo" "Tu" "We" "Th" "Fr" "Sa" "Su")
while getopts ":vl:" opts; do
case "$opts" in
l) lang=$OPTARG;;
v) orientation="$opts";;
esac
done
if [ -f lang ]; then
    . lang
fi
COLOROLD="445566" #MidSlateGrey
COLORTODAY="FF8C00" #Darkorange
COLORREST="445566" #MidSlateGrey
COLORNEXT="778899" #LightSlateGrey
COLORSATURDAY="FFFF00"
COLORSUNDAY="FF8C00"
COLOR=("" "" "" "" "" "\${color $COLORSATURDAY}" "\${color $COLORSUNDAY}")
COLOREND="\${color}"

TODAY=$(date +%-d)
LASTDAY=$(date -d "-$TODAY days +1 month" +%d)
FIRSTDAY=$(date -d "-$[$TODAY-1] days" +%u)

k=$FIRSTDAY
for j in $(seq 1 $LASTDAY); do
  days[$j]="${COLOR[$[k-1]]}${DOW[$[k-1]]}"
  k=$[${k/#7/0}+1]
done
for j in $(seq $[$LASTDAY+1] 31); do
  days[$j]="${DOW[$[k-1]]}"
  k=$[${k/#7/0}+1]
done

# horizontal function
h () {
for i in $(seq 1 $LASTDAY); do
  echo -n "${days[$i]/${DOW[6]}/${DOW[6]}$COLOREND} "
done
echo -n "\${color $COLORREST}"
for i in $(seq $[$LASTDAY+1] 31); do
  echo -n "${days[$i]} "
done
echo $'\n'"\${color $COLOROLD}$(seq -w -s ' ' $LASTDAY|sed "0,/[0-3]*$TODAY \?/s//\${color $COLORTODAY}&\${color $COLORREST}/") \${color $COLORNEXT}$(seq -w -s ' ' 0$[31-$LASTDAY])"
}

#vertical function
v () {
for i in $(seq 1 $[TODAY-1]); do
    TODAYC[$i]="\${color $COLOROLD}"
done
TODAYC[$TODAY]="\${color $COLORTODAY}"
for i in $(seq $[TODAY+1] $LASTDAY); do
    TODAYC[$i]="\${color $COLORREST}"
done
for j in $(seq $LASTDAY); do
  	echo  "${days[$j]} ${TODAYC[$j]}$(printf "%02d" $j)\${color}"
done
}
# call function based on "$orientation" - default is horizontal
${orientation:-h}
```
The **lang** file didn't change, it's just here for completeness.
[lang]("http://dl.dropbox.com/u/1055489/scripts/lang"):
```
case ${lang:-$LANG} in
	af* )  DOW=("Ma" "Di" "Wo" "Do" "Vr" "Sa" "So");;			# Afrikaans (Afrikaans)
	be* )  DOW=("&#1055;&#1072;" "&#1040;&#1118;" "&#1057;&#1077;" "&#1063;&#1072;" "&#1055;&#1103;" "&#1057;&#1091;" "&#1053;&#1103;");;			# Belarusian (&#1041;&#1077;&#1083;&#1072;&#1088;&#1091;&#1089;&#1082;&#1072;&#1103;)
	bs* )  DOW=("Po" "Ut" "Sr" "&#268;e" "Pe" "Su" "Ne");;			# Bosnian (Bosanac)
	bg* )  DOW=("&#1055;&#1086;" "&#1042;&#1090;" "&#1057;&#1088;" "&#1063;&#1077;" "&#1055;&#1077;" "&#1057;&#1098;" "&#1053;&#1077;");;			# Bulgarian (&#1041;&#1098;&#1083;&#1075;&#1072;&#1088;&#1089;&#1082;&#1080;)
	zh* )  DOW=("&#21608;&#19968;" "&#21608;&#20108;" "&#21608;&#19977;" "&#21608;&#22235;" "&#21608;&#20116;" "&#21608;&#20845;" "&#21608;&#22825;");;		# Chinese (&#20013;&#25991;)
	hr* )  DOW=("Po" "Ut" "Ut" "Sr" "&#268;e" "Su" "Ne");;			# Croatian (Hrvatska)
	cs* )  DOW=("Po" "Út" "St" "&#268;t" "Pá" "So" "Ne");;			# Czech (&#268;eština)
	da* )  DOW=("Ma" "Ti" "On" "To" "Fr" "Lø" "Sø");;			# Danish (Dánština)
	nl* )  DOW=("Ma" "Di" "Wo" "Do" "Vr" "Za" "Zo");;			# Dutch (Nederlandse)
	de* )  DOW=("Mo" "Di" "Mi" "Do" "Fr" "Sa" "So");;			# German (Deutche)
	el* )  DOW=("&#916;&#949;" "&#932;&#961;" "&#932;&#949;" "&#928;&#941;" "&#928;&#945;" "&#931;&#940;" "&#922;&#965;");;			# Greek (&#917;&#955;&#955;&#951;&#957;&#953;&#954;&#940;)
	et* )  DOW=("Es" "Te" "Ko" "Ne" "Re" "La" "Pü");;			# Estonian (Eesti)
	tl* )  DOW=("Lu" "Ma" "Mi" "Hu" "Bi" "Sa" "Li");;			# Filipino (Filipino)
	fi* )  DOW=("Ma" "Ti" "Ke" "To" "Pe" "La" "Su");;			# Finnish (Suomen)
	fr* )  DOW=("Lu" "Ma" "Me" "Je" "Ve" "Sa" "Di");;			# French (Français)
	gl* )  DOW=("Lu" "Ma" "Mé" "Xo" "Ve" "Sá" "Do");;			# Galician (Galego)
	hi* )  DOW=("&#2360;&#2379;&#2350;" "&#2350;&#2306;&#2327;&#2354;" "&#2348;&#2369;&#2343;" "&#2327;&#2369;&#2352;&#2369;" "&#2358;&#2369;&#2325;&#2381;&#2352;" "&#2358;&#2344;&#2367;" "&#2360;&#2370;&#2352;&#2381;&#2351;")	;;			# Hindi (&#2361;&#2367;&#2344;&#2381;&#2342;&#2368;)
	hu* )  DOW=("Hé" "Ke" "Se" "Cü" "Pé" "So" "Va");;			# Hungarian (Magyar)
	is* )  DOW=("Má" "Þr" "Mi" "Fi" "Fö" "La" "Su");;			# Icelandic (Íslenska)
	id* )  DOW=("Se" "Se" "Ra" "Ka" "Ju" "Sa" "Mi");;			# Indonesian (Indonesia)
	it* )  DOW=("Lu" "Ma" "Me" "Gi" "Ve" "Sa" "Do");;			# Italian (Italiano)
	ja* )  DOW=("&#26376;&#26332;" "&#28779;&#26332;" "&#27700;&#26332;" "&#26408;&#26332;" "&#37329;&#26332;" "&#22303;&#26332;" "&#26085;&#26332;");;		# Japanese (&#26085;&#26412;&#35486;) x
	ko* )  DOW=("&#50900;&#50836;" "&#54868;&#50836;" "&#49688;&#50836;" "&#47785;&#50836;" "&#44552;&#50836;" "&#53664;&#50836;" "&#51068;&#50836;");;		# Korean (&#54620;&#44397;&#50612;) x
	lv* )  DOW=("Pr" "Ot" "Tr" "Ce" "Pe" "Se" "Sv");;			# Latvian (Latviešu)
	lt* )  DOW=("pi" "an" "tr" "ke" "pe" "še" "se");;			# Lithuanian (Lietuviškai)
	mk* )  DOW=("&#1055;&#1086;" "&#1042;&#1090;" "&#1057;&#1088;" "&#1063;&#1077;" "&#1055;&#1077;" "&#1057;&#1072;" "&#1053;&#1077;");;			# Macedonian (&#1052;&#1072;&#1082;&#1077;&#1076;&#1086;&#1085;&#1089;&#1082;&#1080;)
	ml* )  DOW=("Is" "Se" "Ra" "Ra" "Ju" "Sa" "Mi");;			# Malayam (Bahasa Melayu)
	nb* )  DOW=("ma" "ti" "on" "to" "fr" "lø" "sø");;			# Norwegian (Norsk)
	pl* )  DOW=("Po" "Wt" "&#346;r" "Cz" "Pt" "So" "Nd");;			# Polish (Polska)
	pt* )  DOW=("Sq" "Te" "Qa" "Qi" "Se" "Sá" "Do");;			# Portuguese (Português)
	ro* )  DOW=("Lu" "Ma" "Mi" "Jo" "Vi" "Sa" "Du");;			# Romanian (Român)
	ru* )  DOW=("&#1055;&#1086;" "&#1042;&#1090;" "&#1057;&#1088;" "&#1063;&#1077;" "&#1055;&#1103;" "&#1057;&#1091;" "&#1042;&#1086;");;			# Russian (&#1056;&#1091;&#1089;&#1089;&#1082;&#1080;&#1081;)
	sr* )  DOW=("Po" "Ut" "Sr" "&#268;e" "Pe" "Su" "Ne");;			# Serbian (&#1057;&#1088;&#1087;&#1089;&#1082;&#1080;)
	sk* )  DOW=("Po" "Ut" "St" "Št" "Pi" "So" "Ne");;			# Slovak (Sloven&#269;ina)
	sl* )  DOW=("Po" "To" "Sr" "&#268;e" "Pe" "So" "Ne");;			# Slovenian (Slovenski)
	es* )  DOW=("Lu" "Ma" "Mi" "Ju" "Vi" "Sá" "Do");;			# Spanish (Español)
	sv* )  DOW=("Må" "Ti" "On" "To" "Fr" "Lö" "Sö");;			# Swedish (Svenska)
	tr* )  DOW=("Pa" "Sa" "Ça" "Pe" "Cu" "Cu" "Pa");;			# Turkish (Türkçe)
	uk* )  DOW=("&#1055;&#1086;" "&#1042;&#1110;" "&#1057;&#1077;" "&#1063;&#1077;" "&#1055;&#1103;" "&#1057;&#1091;" "&#1053;&#1077;");;			# Ukrainian (&#1059;&#1082;&#1088;&#1072;&#1111;&#1085;&#1089;&#1100;&#1082;&#1072;)
        * ) DOW=("Mo" "Tu" "We" "Th" "Fr" "Sa" "Su") ;;
esac

```
Horizontal and English are the defaults. [ATTACH]143347[/ATTACH]
```
conkycal.sh
```
make it vertical: [ATTACH]143348[/ATTACH]
```
conkycal.sh -v
```
change the language to Spanish:
```
conkycal.sh -l es
```
or both at once:
```
conkycal.sh -v -l es
```
The order of the arguments doesn't matter:
```
conkycal.sh -l es -v
```

---

### Post by Bruce M. on 2010-01-11
> **mobilediesel said:**
> I updated the horizontal/vertical calendar script a bit.

BUT - will it get rid of my January 6 Error?

I'll be right back to let you know.[-o<

CHIMO!
Bruce

[COLOR="DarkRed"]**I'm Baaaaack:**[/COLOR] **[COLOR="Blue"]YES![/COLOR]**  #6 gone - BUT where do I put the goto to move it to the right?

---

### Post by mobilediesel on 2010-01-11
> **Bruce M. said:**
> BUT - will it get rid of my January 6th Error?

I'll be right back to let you know.[-o<

CHIMO!
Bruce

[COLOR="DarkRed"]**I'm Baaaaack:**[/COLOR] **[COLOR="Blue"]YES![/COLOR]**  #6 gone - BUT where do I put the goto to move it to the right?

I dunno why that would have fixed the number 6 problem.
to add the goto:
```
conkycal.sh -l es|sed 's/^/\${goto [COLOR="Blue"]xx[/COLOR]}/'
```
Change the [COLOR="Blue"]xx[/COLOR] to whatever number you were using that I forgot. :D

That should work even when using **-v** for vertical.

---

### Post by Bruce M. on 2010-01-11
> **mobilediesel said:**
> I dunno why that would have fixed the number 6 problem.
to add the goto:
```
conkycal.sh -l es|sed 's/^/\${goto [COLOR="Blue"]xx[/COLOR]}/'
```
Change the [COLOR="Blue"]xx[/COLOR] to whatever number you were using that I forgot. :D

That should work even when using **-v** for vertical.

Well that works.  :)

```
${voffset 5}${font DejaVu Sans Mono:Bold:size=10}${execpi 3600 ~/Conky/scripts/conkycal.sh -l es|sed 's/^/\${goto 240}/'}${color}
${voffset -32}${goto 180}${font LCDMono:bold:size=24}${color6}${time %b}${goto 980}${color3}${time %y}${font}${color}
```

Gotta play with the vertical part now.  :)


C H I M O!
Bruce

---

### Post by mobilediesel on 2010-01-11
> **Bruce M. said:**
> Well that works.  :)

```
${voffset 5}${font DejaVu Sans Mono:Bold:size=10}${execpi 3600 ~/Conky/scripts/conkycal.sh -l es|sed 's/^/\${goto 240}/'}${color}
${voffset -32}${goto 180}${font LCDMono:bold:size=24}${color6}${time %b}${goto 980}${color3}${time %y}${font}${color}
```

Gotta play with the vertical part now.  :)


C H I M O!
Bruce

The vertical part is neat, too. I can't decide between the different calendar scripts. The main one is the regular calendar formatted one that now highlights holidays. Hmmm.. I'll have to add the holiday highlighting to this one now. Shouldn't be too hard to add. except that I've been awake for 20 hours now.. heh I'll do that when I get up later

---

### Post by Bruce M. on 2010-01-11
> **mobilediesel said:**
> The vertical part is neat, too. I can't decide between the different calendar scripts. The main one is the regular calendar formatted one that now highlights holidays. Hmmm.. I'll have to add the holiday highlighting to this one now. Shouldn't be too hard to add. except that I've been awake for 20 hours now.. heh I'll do that when I get up later

Wait - Holidays? For what country? What religion?

I made a change to the script already - nothing big but might come in handy 6 months from now when someone can't find the previous posts:

```
#!/bin/bash
cd $(dirname $0)
# horizontal and vertical calendar for conky by ans
# Updated by: mobilediesel, dk75, Bruce, Crinos512, et al.
# locale depend week day names

# The 'lang' file must be in the same directory as this script.
# Horizontal and English are the defaults:
# 	conkycal.sh
# Make it vertical:
# 	conkycal.sh -v
# Change the language to Spanish:
# 	conkycal.sh -l es
# Or both at once:
# 	conkycal.sh -v -l es
# The order of the arguments doesn't matter:
# 	conkycal.sh -l es -v
# Need to use a goto:
# 	conkycal.sh -l es|sed 's/^/\${goto 240}/'
# or a goto and a tab:
# 	conkycal.sh |sed -e 's/^/\${goto 240}/' -e 's/$/\${tab 20}/'

DOW=("Mo" "Tu" "We" "Th" "Fr" "Sa" "Su")
```

Really great work there Mr. Diesel, really great!!!
C H I M O!
Bruce

---

### Post by mobilediesel on 2010-01-12
> **Bruce M. said:**
> Wait - Holidays? For what country? What religion?

I made a change to the script already - nothing big but might come in handy 6 months from now when someone can't find the previous posts:

...

Really great work there Mr. Diesel, really great!!!
C H I M O!
Bruce

Ah, yes. Descriptive comments. I added that to the [script]("http://dl.dropbox.com/u/1055489/scripts/conkycal.sh"). Excellent idea!

and as for the holidays, most are U.S. holidays. Using the [remind]("http://wiki.43folders.com/index.php/Remind_FAQ") command you can put in any holidays or birthdays you want. It can handle the holidays like Thanksgiving in the U.S. being on the 4th Thursday of November. It even handles the different days and months that Easter falls on every year.
```
SET Week_1 1
SET Week_2 8
SET Week_3 15
SET Week_4 22
SET easter EASTERDATE(YEAR(TODAY()))
REM [TRIGGER(easter)] MSG Easter Sunday %b
REM thu nov [Week_4] MSG Thanksgiving Day %b

```
My current holiday file for remind:
```
SET Week_1 1
SET Week_2 8
SET Week_3 15
SET Week_4 22
FSET _last(mo) "1 " + MON((mo%12)+1)+" --7"
FSET _trig() TRIGGER(TRIGDATE())
FSET _back(days) TRIGGER(TODAY()-days)
SET SaveTrig $NumTrig
SET easter EASTERDATE(YEAR(TODAY()))
REM Jan 1 +5 MSG New Years Day %b
REM Mon Jan [Week_3] +5 MSG Martin Luther King Day %b
REM Feb 2 +5 MSG Ground Hog Day %b
REM Feb 14 +5 MSG Valentines Day %b
REM Mon Feb [Week_3] +5 MSG Presidents Day %b
REM Mar 17 +5 MSG St Patricks Day %b
REM Sun Mar 8 ++5 MSG Daylight Saving Time starts %b
REM [TRIGGER(easter)] MSG Easter Sunday %b
REM Apr 1 +5 MSG April Fools Day %b
REM Apr 22 +14 MSG Earth Day %b
REM May 5th +5 MSG Cinco De Mayo %b
REM Sun May [Week_2] +7 MSG Mother's Day %b
REM Mon Jun 1 -7 +5 MSG Memorial Day %b
REM Jun 14 +5 MSG Flag Day %b
REM Sun Jun [Week_3] +7 MSG Father's Day %b
REM Jul 4 +7 MSG Independence Day %b
REM Mon Sep [Week_1] +5 MSG Labor Day %b
REM Mon Oct [Week_2] +5 MSG %"Columbus Day%" %b
REM Oct 31 +7 MSG Halloween %b
REM SUN Nov 1 ++5 MSG Daylight Saving Time ends %b
REM Thu Nov [Week_4] +7 MSG Thanksgiving Day %b
REM Nov 11 +5 MSG Veterans Day %b
REM Dec 24 MSG Christmas Eve %b
REM Dec 25 +25 MSG Christmas %b
REM Dec 31 MSG New Year's Eve %b
```

A few examples can be found at [http://wiki.43folders.com/index.php/Remind_Include_Files](http://wiki.43folders.com/index.php/Remind_Include_Files)
and [http://wiki.43folders.com/index.php/User:JamesRifkin/defs.rem](http://wiki.43folders.com/index.php/User:JamesRifkin/defs.rem)
There's even a section in there for all the Jewish holidays.
remind reads the **.reminders** file in your home directory. To keep holidays, birthdays and reminders separate you can keep them in separate files and **include** them in **.reminders**
**~/.reminders**:
```
include /home/username/.remind/reminders.txt
include /home/username/.remind/birthdays.txt
include /home/username/.remind/holidays.txt

```

---

### Post by mobilediesel on 2010-01-12
And a new one for no reason:
```
#!/usr/bin/env bash

DAY=$(date +%d)
for i in {-15..15}; do
DOW=$(date +%a -d "$i days")
days="$days ${DOW:0:2}"
week="$week $(date +%d -d "$i days")"
done
echo "${days#* }"
echo "${week#* }"|sed "s/$DAY\>/\${color ffffff}&\${color}/"
```
Current day highlighted and in the center, with 15 days before and after for a full 31 days. Just uses default locale's abbreviated day names. Probably could make it use the [lang]("http://dl.dropbox.com/u/1055489/scripts/lang") file to give a choice of language.
[ATTACH]143381[/ATTACH]

---

### Post by Rodney9 on 2010-01-12
My Conky - [http://farm5.static.flickr.com/4043/4268767450_a3110322c3_o.png]("http://farm5.static.flickr.com/4043/4268767450_a3110322c3_o.png")

> # UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages 
# - netstat connections to your computer
#
# -- Pengo (conky@pengo.us)
#

# Create own window instead of using desktop (required in nautilus)
own_window yes

background no

own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window

use_xft yes

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
minimum_size 400 5

# Draw shades?
draw_shades yes

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no

uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 8

# border margins
border_margin 2

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
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 1
gap_y 20

# stuff after 'TEXT' will be formatted on screen

override_utf8_locale no
xftfont Terminus:size=10
xftalpha 0.8

use_spacer right




TEXT


${offset 240}${font georgia :size=39}${color white}${alignc} ${time %l:%M %p}
${font}
#${color slate grey}{font Times:size=33}$hr
${offset 240}${color slate grey}${time %a, } ${color }${time %e %B %G}
${offset 240}${color slate grey}${time %Z,    }${color }${time %H:%M:%S}
${offset 240}${color slate grey}UpTime: ${color }$uptime
${offset 240}${color slate grey}Kern:${color }$kernel
${offset 240}${color slate grey}CPU:${color } $cpu% ${acpitemp}C
${offset 240}${cpugraph 20,130 000000 ffffff}
${offset 240}CPU:1  ${cpu cpu1}% ${cpubar cpu1}
${offset 240}CPU:2  ${cpu cpu2}% ${cpubar cpu2}
${offset 240}${color slate grey}Load: ${color }$loadavg
${offset 240}${color slate grey}Processes: ${color }$processes  
${offset 240}${color slate grey}Running:   ${color }$running_processes

${offset 240}${color slate grey}Highest CPU:
${offset 240}${color #ddaa00} ${top name 1}${top_mem cpu 1}
${offset 240}${color lightgrey} ${top name 2}${top cpu 2}
${offset 240}${color lightgrey} ${top name 3}${top cpu 3}
${offset 240}${color lightgrey} ${top name 4}${top cpu 4}

${offset 240}${color slate grey}Highest MEM:
${offset 240}${color #ddaa00} ${top_mem name 1}${top_mem mem 1}
${offset 240}${color lightgrey} ${top_mem name 2}${top_mem mem 2}
${offset 240}${color lightgrey} ${top_mem name 3}${top_mem mem 3}
${offset 240}${color lightgrey} ${top_mem name 4}${top_mem mem 4}

${offset 240}${color slate grey}MEM:  ${color } $memperc% $mem/$memmax
${offset 240}${membar 3,100}
${offset 240}${color slate grey}SWAP: ${color }$swapperc% $swap/$swapmax
${offset 240}${swapbar 3,100}

${offset 240}${color slate grey}ROOT:    ${color }${fs_free /}/${fs_size /}
${offset 240}${fs_bar 3,100 /}
${offset 240}${color slate grey}HOME:  ${color }${fs_free /home}/${fs_size /home}
${offset 240}${fs_bar 3,100 /home}
${offset 240}${color slate grey}NET: 
${offset 240}${color}Up: ${color }${upspeed eth0} k/s
${offset 240}${upspeedgraph eth0 20,130 000000 ffffff}
${offset 240}${color}Down: ${color }${downspeed eth0}k/s${color}
${offset 240}${downspeedgraph eth0 20,130 000000 ffffff}

${offset 240}${color Cyan}Brisbane WEATHER ${hr 2}$color${execi 600 sh /home/puss/conky_weather/weather_script.sh }
${offset 240}${font conkyweather:size=35}${execi 600  sed -n '4p' /home/puss/conky_weather/weather1}${font} ${voffset -20}${execi 600 sed -n '1p' /home/puss/conky_weather/weather1}


${offset 240}${rss [http://rss.accuweather.com/rss/liveweather_rss.asp?metric=1&locCode=OCN|AU|QLD|BRISBANE](http://rss.accuweather.com/rss/liveweather_rss.asp?metric=1&locCode=OCN|AU|QLD|BRISBANE) 10 item_title 1}
${offset 240}${font conkyweather:size=35}${execi 600  sed -n '5p' /home/puss/conky_weather/weather1}${font} ${voffset -20}${execi 600 sed -n '2p' /home/puss/conky_weather/weather1}


${offset 240}${rss [http://rss.accuweather.com/rss/liveweather_rss.asp?metric=1&locCode=OCN|AU|QLD|BRISBANE](http://rss.accuweather.com/rss/liveweather_rss.asp?metric=1&locCode=OCN|AU|QLD|BRISBANE) 10 item_title 2}
${offset 240}${font conkyweather:size=35}${execi 600  sed -n '6p' /home/puss/conky_weather/weather1}${font} ${voffset -20}${execi 600 sed -n '3p' /home/puss/conky_weather/weather1}

---

### Post by Bruce M. on 2010-01-12
> **mobilediesel said:**
> Ah, yes. Descriptive comments. I added that to the [script]("http://dl.dropbox.com/u/1055489/scripts/conkycal.sh"). Excellent idea!

See, I ain't just a pretty face here ya know.

Now all that "Martian talk" that followed is really nice. but ...
How do you use it in conky?

Guess my face ain't so pretty after all.:lolflag:

CHIMO!
Bruce

---

### Post by mobilediesel on 2010-01-13
> **Bruce M. said:**
> See, I ain't just a pretty face here ya know.

Now all that "Martian talk" that followed is really nice. but ...
How do you use it in conky?

Guess my face ain't so pretty after all.:lolflag:

CHIMO!
Bruce

Well, first you set up remind to give you all your holiday and birthday reminders. That's what all the "Martian talk" was. :lol:

[ATTACH]143479[/ATTACH]
New year's day and Martin Luther King day are highlighted green, current day in white. Here's the calendar code:
```
date=$(date '+%F')
DAY=${date:8:2}
[COLOR="Blue"]# m="-m" # uncomment this line for starting the week on Monday instead of Sunday.[/COLOR]
cal=$(cal $m)
prev=$(cal $m $(date '+%-m %Y' --date="${date:0:7}-15 -1 month")|sed 's/ *$//;/^$/d'|tail -1)
next=$(cal $m $(date '+%-m %Y' --date="${date:0:7}-15 +1 month")|sed '/^ *&/d;1,2d;s/^ *//'|head -1)
if [ ${#next} == 19 ] ;then next=$'\n'"\${color9} $next"
else next="\${color9}  $next"
fi
if [ ${#prev} == 20 ]; then prev="$prev"$'\n '
else prev="$prev  "
fi
[COLOR="Green"]dates=$(remind -s|cut -d ' ' -f1|uniq|cut -d '/' -f3|sed "/$DAY/d")
current=$(echo "${cal:42}"|sed -e '/^ *$/d' -e 's/^/ /' -e 's/$/ /' -e 's/^ *1 / 1 /' )
for i in $dates; do
current=$(echo "$current"|sed -e /" ${i/#0/} "/s/" ${i/#0/} "/" "'${color green}'"${i/#0/}"'${color}'" "/)
done[/COLOR]
current=$(echo "$current"|sed -e /" ${DAY/#0/} "/s/" ${DAY/#0/} "/" "'${color3}'"${DAY/#0/}"'${color}'" "/ -e 's/^ //' -e 's/ *$//')
echo -e "\${color7}${cal:0:21}\${color4}${cal:21:21}\${color9}$prev\${color}$current$next"
```
The section in [COLOR="Green"]green[/COLOR] is what colors the holidays and birthdays green according to information returned by **remind**.

---

### Post by dmillerct on 2010-01-13
With all these calendar scripts floating around I am quite surprised that no one has entered the January conky of the month contest.

[http://blog.conky.be/2009/12/16/the-lines-are-now-closed/]("http://blog.conky.be/2009/12/16/the-lines-are-now-closed/")

---

### Post by mobilediesel on 2010-01-13
> **dmillerct said:**
> With all these calendar scripts floating around I am quite surprised that no one has entered the January conky of the month contest.

[http://blog.conky.be/12/16/2009/the-lines-are-now-closed/]("http://blog.conky.be/12/16/2009/the-lines-are-now-closed/")

I entered but I was looking to see if one can enter the contest multiple times in the same month. Maybe Londonali1010 can clear that up for us.

---

### Post by dmillerct on 2010-01-13
> **mobilediesel said:**
> I entered but I was looking to see if one can enter the contest multiple times in the same month. Maybe Londonali1010 can clear that up for us.

Oh, you entered? am I not linking the correct post to place entries?

---

### Post by mobilediesel on 2010-01-13
> **dmillerct said:**
> Oh, you entered? am I not linking the correct post to place entries?

I entered after you posted about no one entering. :D

---

### Post by dmillerct on 2010-01-13
> **mobilediesel said:**
> I entered after you posted about no one entering. :D

Too funny. =D

---

### Post by mobilediesel on 2010-01-13
> **dmillerct said:**
> Too funny. =D

I was going to enter yesterday but ended up having a migraine. I never really believed that "migraines" were a real thing. Then several months ago I woke up with a migraine. I usually have to sleep it off which means I sometimes end up sleeping about 18 to 20 hours. Then I got up today and found that a mouse **** on some of my clean dishes. I poured boiling water all over the counter and the dishes to make sure they were sterile and cleaned up everything again.

Ah, good old Michigan where it's 25 freakin degrees Fahrenheit right now. Living in a house that would never pass an inspection if it were to be sold. Ants in the summer. Mice in the winter. Moths and spiders continuously throughout the year. I've dealt with fewer pests while camping.

At least the internet work#(^&%(^&#!(&$#(&#((RR

[FONT="Fixedsys"]NO CARRIER[/FONT]





Heh, most people born after 1978 probably wouldn't get that.

---

### Post by londonali1010 on 2010-01-13
> **mobilediesel said:**
> I was going to enter yesterday but ended up having a migraine. I never really believed that "migraines" were a real thing. Then several months ago I woke up with a migraine. I usually have to sleep it off which means I sometimes end up sleeping about 18 to 20 hours. Then I got up today and found that a mouse **** on some of my clean dishes. I poured boiling water all over the counter and the dishes to make sure they were sterile and cleaned up everything again.

Ah, good old Michigan where it's 25 freakin degrees Fahrenheit right now. Living in a house that would never pass an inspection if it were to be sold. Ants in the summer. Mice in the winter. Moths and spiders continuously throughout the year. I've dealt with fewer pests while camping.

At least the internet work#(^&%(^&#!(&$#(&#((RR

[FONT="Fixedsys"]NO CARRIER[/FONT]





Heh, most people born after 1978 probably wouldn't get that.

Dude, that sounds fun :S

Anyway, sorry taking a while to respond, yes, you guys are posting in the right place.

Also, straw poll of (2) people: would it be better or worse if I made it publicly votable?

---

### Post by mobilediesel on 2010-01-13
> **londonali1010 said:**
> Dude, that sounds fun :S

Anyway, sorry taking a while to respond, yes, you guys are posting in the right place.

Also, straw poll of (2) people: would it be better or worse if I made it publicly votable?

"Fun" yeah I used a different word starting with the same first two letters. :D

Yeah, make it publicly votable!

---

### Post by dmillerct on 2010-01-13
> **londonali1010 said:**
> Dude, that sounds fun :S

Anyway, sorry taking a while to respond, yes, you guys are posting in the right place.

Also, straw poll of (2) people: would it be better or worse if I made it publicly votable?

Either publicly votable or committee, It doesn't matter to me either way.

As long as people can't vote for thier own config like umpfteen thousand times. :twisted:

---

### Post by TeoBigusGeekus on 2010-01-13
Congrats Bruce!!!
I just found out about your thread - awesome!
My contribution to it will be the weather scripts I've written
[http://ubuntuforums.org/showthread.php?t=1156383]("http://ubuntuforums.org/showthread.php?t=1156383")
As a civil engineer I'm always concerned about the weather...
Here's me desktop.

---

### Post by londonali1010 on 2010-01-13
> **mobilediesel said:**
> I entered but I was looking to see if one can enter the contest multiple times in the same month. Maybe Londonali1010 can clear that up for us.

Oh, and I meant to say, yeah, go for it, enter as many times as you like! I don't have a problem with it as long as no one takes the mick :D

---

### Post by mobilediesel on 2010-01-13
> **londonali1010 said:**
> Oh, and I meant to say, yeah, go for it, enter as many times as you like! I don't have a problem with it as long as no one takes the mick :D

I had to look up "takes the mick" as that wasn't one of the many sayings I picked up watching BBC shows. :D

For two countries that speak English we sure don't speak the same language sometimes! That's more the fault of the U.S. though, I'll totally admit that. :lol:

---

### Post by Bruce M. on 2010-01-14
> **dmillerct said:**
> With all these calendar scripts floating around I am quite surprised that no one has entered the January conky of the month contest.

[http://blog.conky.be/2009/12/16/the-lines-are-now-closed/]("http://blog.conky.be/2009/12/16/the-lines-are-now-closed/")

:(  And I thought is was a good idea too.  That's why I suggested it.

January was coming, a new year, twenty and a half (2010)  and a million (OK, I exaggerate) post about calendars.  {sigh}

---

### Post by Bruce M. on 2010-01-14
> **mobilediesel said:**
> I was going to enter yesterday but ended up having a migraine. I never really believed that "migraines" were a real thing.

Oh my.  I remember discovering the truth about migraines. had this headache all day that would NOT go away, just getting worse.  Finally tried ice, cold shower, hot shower... nada! ... {blank}

Woke up at 10AM the next morning in a hospital with a nurse taking my pulse.
N: "How do you feel?"
Me "Fine."
N: "Do you remember coming here?"
Me: "No, why?"
N: "Take a look at how you are dressed, other than taking your boots off, we did nothing except put you to sleep."

Getting up I checked; tie draped around my neck, shirt buttoned with two buttons in the wrong holes, not tucked in, pants completely undone, just the belt done up. (Thank God for underwear) I looked at the Nurse who just added,
"That's not the scary part, you drove 12 miles to get here." Don't remember a thing.

That nurse told me a "migraine" was like birth pains in your head that just do NOT go away!  Being a guy, I wouldn't know.  :)

> **mobilediesel said:**
> At least the internet work#(^&%(^&#!(&$#(&#((RR

[FONT="Fixedsys"]NO CARRIER[/FONT]

Heh, most people born after 1978 probably wouldn't get that.

Ohhhhhhhhhhhh, I HATE THAT SOUND!!!!

CHIMO!
Bruce

---

### Post by Bruce M. on 2010-01-14
> **mobilediesel said:**
> Well, first you set up remind to give you all your holiday and birthday reminders. That's what all the "Martian talk" was. :lol:

Oh, OK.  Clear as mud.
{psst, Tom, does that do it for you? I didn't think so, back to reading}

They couldn't do something simple like:

**remind.txt**
```
1 Jan
15 Feb
12 May
18 Jun
22 Oct
```
for remind to read ...  nooooooooooooo that would be too easy.  :)

> **mobilediesel said:**
> 
[ATTACH]143479[/ATTACH]
New year's day and Martin Luther King day are highlighted green, current day in white. Here's the calendar code:
```
date=$(date '+%F')
DAY=${date:8:2}
[COLOR="Blue"]# m="-m" # uncomment this line for starting the week on Monday instead of Sunday.[/COLOR]
cal=$(cal $m)
prev=$(cal $m $(date '+%-m %Y' --date="${date:0:7}-15 -1 month")|sed 's/ *$//;/^$/d'|tail -1)
next=$(cal $m $(date '+%-m %Y' --date="${date:0:7}-15 +1 month")|sed '/^ *&/d;1,2d;s/^ *//'|head -1)
if [ ${#next} == 19 ] ;then next=$'\n'"\${color9} $next"
else next="\${color9}  $next"
fi
if [ ${#prev} == 20 ]; then prev="$prev"$'\n '
else prev="$prev  "
fi
[COLOR="Green"]dates=$(remind -s|cut -d ' ' -f1|uniq|cut -d '/' -f3|sed "/$DAY/d")
current=$(echo "${cal:42}"|sed -e '/^ *$/d' -e 's/^/ /' -e 's/$/ /' -e 's/^ *1 / 1 /' )
for i in $dates; do
current=$(echo "$current"|sed -e /" ${i/#0/} "/s/" ${i/#0/} "/" "'${color green}'"${i/#0/}"'${color}'" "/)
done[/COLOR]
current=$(echo "$current"|sed -e /" ${DAY/#0/} "/s/" ${DAY/#0/} "/" "'${color3}'"${DAY/#0/}"'${color}'" "/ -e 's/^ //' -e 's/ *$//')
echo -e "\${color7}${cal:0:21}\${color4}${cal:21:21}\${color9}$prev\${color}$current$next"
```
The section in [COLOR="Green"]green[/COLOR] is what colors the holidays and birthdays green according to information returned by **remind**.

Now that language I understand perfectly, it's called: *copy/paste*. :lolflag:

Seriously:  Gotta read up on Remind, I like it.

CHIMO
Bruce

---

### Post by dmillerct on 2010-01-14
> **Bruce M. said:**
> Oh my.  I remember discovering the truth about migraines. had this headache all day that would NOT go away, just getting worse.  Finally tried ice, cold shower, hot shower... nada! ... {blank}

Woke up at 10AM the next morning in a hospital with a nurse taking my pulse.
N: "How do you feel?"
Me "Fine."
N: "Do you remember coming here?"
Me: "No, why?"
N: "Take a look at how you are dressed, other than taking your boots off, we did nothing except put you to sleep."

Getting up I checked; tie draped around my neck, shirt buttoned with two buttons in the wrong holes, not tucked in, pants completely undone, just the belt done up. (Thank God for underwear) I looked at the Nurse who just added,
"That's not the scary part, you drove 12 miles to get here." Don't remember a thing.

That nurse told me a "migraine" was like birth pains in your head that just do NOT go away!  Being a guy, I wouldn't know.  :)



Ohhhhhhhhhhhh, I HATE THAT SOUND!!!!

CHIMO!
Bruce

That reminds me of my night out in Manhattan last Friday. Except in my case my lack of memory was caused by Beer and warm Slivovitz. :(

---

### Post by Bruce M. on 2010-01-14
> **dmillerct said:**
> That reminds me of my night out in Manhattan last Friday. Except in my case my lack of memory was caused by Beer and warm Slivovitz. :(

Ah yes:
```
#!/bin/bash
blackout=beer+warmSlivovitz
```

In my case it got to:
```
#!/bin/bash
blackout=bruce+alcohol
```

But that was years after the migraines stopped.

CHIMO!
Bruce

---

### Post by londonali1010 on 2010-01-14
> **Bruce M. said:**
> :(  And I thought is was a good idea too.  That's why I suggested it.

January was coming, a new year, twenty and a half (2010)  and a million (OK, I exaggerate) post about calendars.  {sigh}

I haven't seen *your* entry yet, Bruce :) /offtopic

---

### Post by wlourf on 2010-01-14
Hi folks !

Here is my entry for the calendar contest (is here the right place to post it ?)

Well as you can see, it's a circular calendar (wheel of time, you know ...) associated with a text file where you can set your bank holiday and adding some text inside the circle. All is drawn with lua !

There is some paramaters (colors, size ...) that you can change in the lua script

I hope you like it, 10 more screenshots are here: [URL="http://picasaweb.google.com/wlourf/WheelCalendar#"]http://picasaweb.google.com/wlourf/WheelCalendar#
[/URL] 
Il was designed for a 800*1024 screen but will work with other resolutions ...

Any comments are welcome, of course :P

Edit :
As this calendar won the contest (thanks to all), the updated script is now on this post : [http://ubuntuforums.org/showpost.php?p=8782789&postcount=147](http://ubuntuforums.org/showpost.php?p=8782789&postcount=147)

---

### Post by dmillerct on 2010-01-14
> **wlourf said:**
> Hi folks !

Here is my entry for the calendar contest (is here the right place to post it ?)

Well as you can see, it's a circular calendar (wheel of time, you know ...) associated with a text file where you can set your bank holiday and adding some text inside the circle. All is drawn with lua !

There is some paramaters (colors, size ...) that you can change in the lua script

I hope you like it, 10 more screenshots are here: [URL="http://picasaweb.google.com/wlourf/WheelCalendar#"]http://picasaweb.google.com/wlourf/WheelCalendar#
[/URL] 
Il was designed for a 800*1024 screen but will work with other resolutions ...

Any comments are welcome, of course :P

Here's the lua script, the (simple) conkyrc is in the archive ..
```
--[[
calendar wheel by Wlourf (14 jan. 2010)

This script is designed to draw dates on a circular way on the left of the screen.
Some text can be added in the circle with the file calendar.txt (see below)
Some parameters (colors, sizes ... ) can be adjusted (see below).

As this script draw a lot of things, a short update of the conky is not necessary.

Call this script in Conky using the following before TEXT (assuming you save this script to ~/scripts/calendar.lua):
    lua_load ~/scripts/calendar.lua
    lua_draw_hook_pre draw_calendar
]]

require 'cairo'
require 'imlib2'



function string:split(delimiter)
--source for the split function : http://www.wellho.net/resources/ex.php4?item=u108/split
  local result = { }
  local from  = 1
  local delim_from, delim_to = string.find( self, delimiter, from  )
  while delim_from do
    table.insert( result, string.sub( self, from , delim_from-1 ) )
    from  = delim_to + 1
    delim_from, delim_to = string.find( self, delimiter, from  )
  end
  table.insert( result, string.sub( self, from  ) )
  return result
end


function conky_draw_calendar()
    if conky_window==nil then return end
    local width=conky_window.width
    local height=conky_window.height
    local cs=cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, width, height)
    cr=cairo_create(cs)
    
    -------------------------- parameters are set here -----------------------------------
    
    -- vertical center of the circle (height/2 for centered circle)
    yc=height/2
    
    --number of days to display before and after today (i.e. with range = 30 --> 60 days are displayed)
    --even number between 20 and 30 for nice effect
    range = 20
    
    --not sure of the engish words so I leave then in french !    
    --fleche (arrow) is the segment from x=0 to x=radius-xc (with xc =center of the circle) 
    --fleche for the external circle
    --fleche2 for the internal circle
    --fleche2 must be < fleche
    fleche=125
    fleche2=fleche*.75
    
    --corde (chord) is the vertical segment (where x=0) of the external circle
    --if 'corde' too close to 'height', imlib will display some warnings 
    corde=height-200
            
    --colors RGB (0-255)
    --week day
    wday={51,51,255}
    --week-end and bank holidays
    eday={255,255,153}
    --color of today
    dday={0,255,255}
    
    --vertical gradient (both circle and dates)? (true/false)
    vgradient=true
    
    --horizontal gradient for the circle? (0 to 1, 0 is the best choice for "moon like" circle )
    hgradient=0
    
    
    --you can change the font here
    font="Japan"
    --font_size (of dates) must be less than delta (= heigth of a day)
    delta = yc/(range+0.5)
    --the font-size has to be adjusted depending on the font used
    font_size=delta-1
    
    --file calendar (absolute path, can be "" if no file used)
    calendar_file="/home/wlourf/scripts/calendar.txt"
    --format of in this text file
    --MMDD;N;TEXT
    --MMDD = month day
    --N    = 0 or 1 (1 to display same colors as week-ends)
    --TEXT = Text to display (use * for multiline)

    --information text (from calendar.txt)
    info_color={255,255,204}
    --font size of text infos
    font_size_info=font_size

    
    --need to write a little image, didn't fiond a way to use a buffer
    image_tmp="/tmp/img_cal.png"
    
    
    -------------------------- end of the parameters, ouf -----------------------------------
    
    --some calculations
    --radius for external circle
    --radius2 for internal circle
    --delta = number of arcs in the circle
    radius=(corde^2+4*fleche^2)/(8*fleche)
    radius2=(corde^2+4*fleche2^2)/(8*fleche2)
     decal=2*(delta-font_size)
    wday[1]=wday[1]/255
    wday[2]=wday[2]/255
    wday[3]=wday[3]/255    
    eday[1]=eday[1]/255
    eday[2]=eday[2]/255
    eday[3]=eday[3]/255    


    --xc =x center of external circle
    --xc2=x center of internal circle
    xc = fleche - radius    
    xc2 = fleche2 - radius2
    
    --local cs=cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, w, h)
    h_txt = height/(2*range+1)
    --local cs2=cairo_image_surface_create(CAIRO_FORMAT_ARGB32, 100, h_txt)
    
    -- conky_window.drawable
    cr2=cairo_create(cs2)
    
    t = os.date('*t') -- date in table

    --read the calendar file
    file = io.open(calendar_file,"r")    
    tabcal={}    
    idx=1
    if file ~= nil then
        while true do
             line = file:read("*l")
            if line == nil then break end
            lineok = string.split(line,";") --text = line .. "\n" .. text
            if (#lineok)==3 then
                tabcal[idx]={lineok[1],lineok[2],lineok[3]}
                idx=idx+1
            end
        end
    end    
    angmini=math.atan((corde/2)/(radius-fleche))

    for i=-range,range do
        --get the date
        s = os.time(t) -- date in seconds
        --dd= os.date("%a-%d-%y")
        s2 = s + 3600*24*i --date diff in seconds
        --t2 = os.date('*t',s2) --date diff in table
        wd = os.date("%w",s2)
        md = os.date("%m%d",s2)
        dt = os.date("%a. %d %b.",s2),os.date("%d",s2),os.date("%b",s2)

        --percentage of vertical gradient
        pc=(range-math.abs(i))/range
        if not vgradient then pc=1 end

        --angle min et max of one block
        ang0=angmini*((i-0.5)/range)
        ang1=angmini*(i+0.5)/range
        angm=(ang0+ang1)/2
        
        --read the calendar.txt array
        flag = false
        for idy=1,idx-1 do
            if tabcal[idy][1] == md then
                if i == 0 then
                    today = tabcal[idy]
                end
                if tabcal[idy][2] == "1" then
                    flag = true
                end
                break
            end
            
        end

        --colors
        if wd=="6" or wd=="0" or flag == true then
            colR,colG,colB=eday[1],eday[2],eday[3]
        else
            colR,colG,colB=wday[1],wday[2],wday[3]
        end
        
        cairo_set_source_rgba (cr,colR, colG, colB,pc);
        pat = cairo_pattern_create_radial (xc, yc, radius,
                                               xc2,yc,radius2);
        cairo_pattern_add_color_stop_rgba (pat, 0, colR, colG, colB, pc);
        cairo_pattern_add_color_stop_rgba (pat, 1, colR, colG, colB, hgradient);
        cairo_set_source (cr, pat);

        --draw the arcs
        x1,y1=radius*math.cos(ang0)+xc,radius*math.sin(ang0)+yc
        x2,y2=radius*math.cos(ang1)+xc,radius*math.sin(ang1)+yc
        xm,ym=radius*math.cos(angm)+xc,radius*math.sin(angm)+yc
    --    am=(ym-yc)/(xm-xc)
    --    bm=ym-am*xm

        cairo_move_to(cr,x1,y1)
        cairo_line_to(cr,x2,y2)
        cairo_line_to(cr,xc,yc)
        cairo_fill(cr)
        
        --lenght of the arc
        dx,dy=math.abs(x2-x1),math.abs(y2-y1)
        h_txt=math.sqrt(dx*dx+dy*dy)
        w_txt=font_size*10
        
        --write text in another image
        --didn't find to work in memory only
        local cs2=cairo_image_surface_create(CAIRO_FORMAT_ARGB32, w_txt, h_txt)
        cr2=cairo_create(cs2)
        cairo_set_font_size (cr2, font_size);
        if i==0 then 
            --weight = CAIRO_FONT_WEIGHT_BOLD
            colR, colG, colB = dday[1]/255,dday[2]/255,dday[3]/255
        --else
        --    weight = CAIRO_FONT_WEIGHT_NORMAL    
        end
        cairo_select_font_face(cr2, font, CAIRO_FONT_SLANT_NORMAL, CAIRO_FONT_WEIGHT_NORMAL)

        cairo_move_to(cr,xc+(delta+radius)*math.cos(ang0),corde/2+(radius-fleche)*math.tan(ang0))

        cairo_move_to(cr2,0,h_txt-decal)
        cairo_set_source_rgba (cr2, colR, colG, colB,pc)
        cairo_show_text(cr2, " " .. dt)
        cairo_stroke(cr2)

        cairo_surface_write_to_png(cs2,image_tmp)
        cairo_destroy(cr2)
        
        --put date text on cairo surface
        imageTmp = imlib_load_image(image_tmp)
        imlib_context_set_image(imageTmp)

        rot_img = imlib_create_rotated_image(angm)
        imlib_free_image()

        imlib_context_set_image(rot_img)

        w_img0, h_img0 = imlib_image_get_width(), imlib_image_get_height()
        
        ---look for center of text
        rt=radius+w_txt/2
        xt=rt*math.cos(angm)+xc-w_img0/2
        yt=rt*math.sin(angm)+yc-h_img0/2
        imlib_render_image_on_drawable(xt,yt)
        imlib_free_image()


        --write text info if needed
        have=""
        if today ~= nil then
            cairo_select_font_face(cr, font, CAIRO_FONT_SLANT_NORMAL, CAIRO_FONT_WEIGHT_NORMAL    )
            cairo_set_line_width(cr,0)
            cairo_set_font_size(cr,font_size_info)
            cairo_set_source_rgba (cr, info_color[1]/255, info_color[2]/255, info_color[3]/255,1);

            have = string.split(today[3],"*")
            for i=1,#have do 
                cairo_move_to(cr,10,height/2+(i-#have/2)*font_size_info)
                cairo_show_text(cr, have[i])
                cairo_fill(cr)
            end
        end    

    end
end 

```

Looks awesome!! I think to officially enter you need to post the entry on the conky blog located [Here]("http://blog.conky.be")

---

### Post by wlourf on 2010-01-14
> **dmillerct said:**
> Looks awesome!! I think to officially enter you need to post the entry on the conky blog located [Here]("http://blog.conky.be")
thanks last month winner ! , I've done it too ! Did you entry for this month ?

---

### Post by dmillerct on 2010-01-14
> **wlourf said:**
> thanks last month winner ! , I've done it too ! Did you entry for this month ?

No, I am just swamped with work and family issues this month. I probably could of slapped something together however I really wanted to make something special and just ran out of time.

On a related note, I wanted to use the prize money to some how give back to the conky community. After discussing this with a few buds here, there really wasn't anything that could be purchased from amazon to benefit everyone (directly anyway).

So I did what I thought was the next best thing and got the following:
[IMG]http://ecx.images-amazon.com/images/I/31S6MZ1DCVL._BO2,204,203,200_PIsitb-sticker-arrow-click,TopRight,35,-76_AA240_SH20_OU01_.jpg[/IMG]

and
[IMG]http://ecx.images-amazon.com/images/I/51gUR%2Bt6K6L._BO2,204,203,200_PIsitb-sticker-arrow-click,TopRight,35,-76_AA240_SH20_OU01_.jpg[/IMG]

I figure with these at least I can help in-directly help the community. :P

---

### Post by Bruce M. on 2010-01-14
> **londonali1010 said:**
> I haven't seen *your* entry yet, Bruce :) /offtopic

I do believe that I said because I suggested it I wouldn't send one in.  Besides mine would be a copy/paste jobe as I can't write a script worth a dime.  :(

C H I M O!!
Bruce

---

### Post by Bruce M. on 2010-01-14
> **wlourf said:**
> Hi folks !

Here is my entry for the calendar contest (is here the right place to post it ?)

Well as you can see, it's a circular calendar (wheel of time, you know ...) associated with a text file where you can set your bank holiday and adding some text inside the circle. All is drawn with lua !

There is some paramaters (colors, size ...) that you can change in the lua script

I hope you like it, 10 more screenshots are here: [URL="http://picasaweb.google.com/wlourf/WheelCalendar#"]http://picasaweb.google.com/wlourf/WheelCalendar#
[/URL] 
Il was designed for a 800*1024 screen but will work with other resolutions ...

Any comments are welcome, of course :P

Here's the lua script, the (simple) conkyrc is in the archive ..
```
--[[
calendar wheel by Wlourf (14 jan. 2010)

This script is designed to draw dates on a circular way on the left of the screen.
Some text can be added in the circle with the file calendar.txt (see below)
Some parameters (colors, sizes ... ) can be adjusted (see below).

As this script draw a lot of things, a short update of the conky is not necessary.

Call this script in Conky using the following before TEXT (assuming you save this script to ~/scripts/calendar.lua):
    lua_load ~/scripts/calendar.lua
    lua_draw_hook_pre draw_calendar
]]

require 'cairo'
require 'imlib2'



function string:split(delimiter)
--source for the split function : http://www.wellho.net/resources/ex.php4?item=u108/split
  local result = { }
  local from  = 1
  local delim_from, delim_to = string.find( self, delimiter, from  )
  while delim_from do
    table.insert( result, string.sub( self, from , delim_from-1 ) )
    from  = delim_to + 1
    delim_from, delim_to = string.find( self, delimiter, from  )
  end
  table.insert( result, string.sub( self, from  ) )
  return result
end


function conky_draw_calendar()
    if conky_window==nil then return end
    local width=conky_window.width
    local height=conky_window.height
    local cs=cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, width, height)
    cr=cairo_create(cs)
    
    -------------------------- parameters are set here -----------------------------------
    
    -- vertical center of the circle (height/2 for centered circle)
    yc=height/2
    
    --number of days to display before and after today (i.e. with range = 30 --> 60 days are displayed)
    --even number between 20 and 30 for nice effect
    range = 20
    
    --not sure of the engish words so I leave then in french !    
    --fleche (arrow) is the segment from x=0 to x=radius-xc (with xc =center of the circle) 
    --fleche for the external circle
    --fleche2 for the internal circle
    --fleche2 must be < fleche
    fleche=125
    fleche2=fleche*.75
    
    --corde (chord) is the vertical segment (where x=0) of the external circle
    --if 'corde' too close to 'height', imlib will display some warnings 
    corde=height-200
            
    --colors RGB (0-255)
    --week day
    wday={51,51,255}
    --week-end and bank holidays
    eday={255,255,153}
    --color of today
    dday={0,255,255}
    
    --vertical gradient (both circle and dates)? (true/false)
    vgradient=true
    
    --horizontal gradient for the circle? (0 to 1, 0 is the best choice for "moon like" circle )
    hgradient=0
    
    
    --you can change the font here
    font="Japan"
    --font_size (of dates) must be less than delta (= heigth of a day)
    delta = yc/(range+0.5)
    --the font-size has to be adjusted depending on the font used
    font_size=delta-1
    
    --file calendar (absolute path, can be "" if no file used)
    calendar_file="/home/wlourf/scripts/calendar.txt"
    --format of in this text file
    --MMDD;N;TEXT
    --MMDD = month day
    --N    = 0 or 1 (1 to display same colors as week-ends)
    --TEXT = Text to display (use * for multiline)

    --information text (from calendar.txt)
    info_color={255,255,204}
    --font size of text infos
    font_size_info=font_size

    
    --need to write a little image, didn't fiond a way to use a buffer
    image_tmp="/tmp/img_cal.png"
    
    
    -------------------------- end of the parameters, ouf -----------------------------------
    
    --some calculations
    --radius for external circle
    --radius2 for internal circle
    --delta = number of arcs in the circle
    radius=(corde^2+4*fleche^2)/(8*fleche)
    radius2=(corde^2+4*fleche2^2)/(8*fleche2)
     decal=2*(delta-font_size)
    wday[1]=wday[1]/255
    wday[2]=wday[2]/255
    wday[3]=wday[3]/255    
    eday[1]=eday[1]/255
    eday[2]=eday[2]/255
    eday[3]=eday[3]/255    


    --xc =x center of external circle
    --xc2=x center of internal circle
    xc = fleche - radius    
    xc2 = fleche2 - radius2
    
    --local cs=cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, w, h)
    h_txt = height/(2*range+1)
    --local cs2=cairo_image_surface_create(CAIRO_FORMAT_ARGB32, 100, h_txt)
    
    -- conky_window.drawable
    cr2=cairo_create(cs2)
    
    t = os.date('*t') -- date in table

    --read the calendar file
    file = io.open(calendar_file,"r")    
    tabcal={}    
    idx=1
    if file ~= nil then
        while true do
             line = file:read("*l")
            if line == nil then break end
            lineok = string.split(line,";") --text = line .. "\n" .. text
            if (#lineok)==3 then
                tabcal[idx]={lineok[1],lineok[2],lineok[3]}
                idx=idx+1
            end
        end
    end    
    angmini=math.atan((corde/2)/(radius-fleche))

    for i=-range,range do
        --get the date
        s = os.time(t) -- date in seconds
        --dd= os.date("%a-%d-%y")
        s2 = s + 3600*24*i --date diff in seconds
        --t2 = os.date('*t',s2) --date diff in table
        wd = os.date("%w",s2)
        md = os.date("%m%d",s2)
        dt = os.date("%a. %d %b.",s2),os.date("%d",s2),os.date("%b",s2)

        --percentage of vertical gradient
        pc=(range-math.abs(i))/range
        if not vgradient then pc=1 end

        --angle min et max of one block
        ang0=angmini*((i-0.5)/range)
        ang1=angmini*(i+0.5)/range
        angm=(ang0+ang1)/2
        
        --read the calendar.txt array
        flag = false
        for idy=1,idx-1 do
            if tabcal[idy][1] == md then
                if i == 0 then
                    today = tabcal[idy]
                end
                if tabcal[idy][2] == "1" then
                    flag = true
                end
                break
            end
            
        end

        --colors
        if wd=="6" or wd=="0" or flag == true then
            colR,colG,colB=eday[1],eday[2],eday[3]
        else
            colR,colG,colB=wday[1],wday[2],wday[3]
        end
        
        cairo_set_source_rgba (cr,colR, colG, colB,pc);
        pat = cairo_pattern_create_radial (xc, yc, radius,
                                               xc2,yc,radius2);
        cairo_pattern_add_color_stop_rgba (pat, 0, colR, colG, colB, pc);
        cairo_pattern_add_color_stop_rgba (pat, 1, colR, colG, colB, hgradient);
        cairo_set_source (cr, pat);

        --draw the arcs
        x1,y1=radius*math.cos(ang0)+xc,radius*math.sin(ang0)+yc
        x2,y2=radius*math.cos(ang1)+xc,radius*math.sin(ang1)+yc
        xm,ym=radius*math.cos(angm)+xc,radius*math.sin(angm)+yc
    --    am=(ym-yc)/(xm-xc)
    --    bm=ym-am*xm

        cairo_move_to(cr,x1,y1)
        cairo_line_to(cr,x2,y2)
        cairo_line_to(cr,xc,yc)
        cairo_fill(cr)
        
        --lenght of the arc
        dx,dy=math.abs(x2-x1),math.abs(y2-y1)
        h_txt=math.sqrt(dx*dx+dy*dy)
        w_txt=font_size*10
        
        --write text in another image
        --didn't find to work in memory only
        local cs2=cairo_image_surface_create(CAIRO_FORMAT_ARGB32, w_txt, h_txt)
        cr2=cairo_create(cs2)
        cairo_set_font_size (cr2, font_size);
        if i==0 then 
            --weight = CAIRO_FONT_WEIGHT_BOLD
            colR, colG, colB = dday[1]/255,dday[2]/255,dday[3]/255
        --else
        --    weight = CAIRO_FONT_WEIGHT_NORMAL    
        end
        cairo_select_font_face(cr2, font, CAIRO_FONT_SLANT_NORMAL, CAIRO_FONT_WEIGHT_NORMAL)

        cairo_move_to(cr,xc+(delta+radius)*math.cos(ang0),corde/2+(radius-fleche)*math.tan(ang0))

        cairo_move_to(cr2,0,h_txt-decal)
        cairo_set_source_rgba (cr2, colR, colG, colB,pc)
        cairo_show_text(cr2, " " .. dt)
        cairo_stroke(cr2)

        cairo_surface_write_to_png(cs2,image_tmp)
        cairo_destroy(cr2)
        
        --put date text on cairo surface
        imageTmp = imlib_load_image(image_tmp)
        imlib_context_set_image(imageTmp)

        rot_img = imlib_create_rotated_image(angm)
        imlib_free_image()

        imlib_context_set_image(rot_img)

        w_img0, h_img0 = imlib_image_get_width(), imlib_image_get_height()
        
        ---look for center of text
        rt=radius+w_txt/2
        xt=rt*math.cos(angm)+xc-w_img0/2
        yt=rt*math.sin(angm)+yc-h_img0/2
        imlib_render_image_on_drawable(xt,yt)
        imlib_free_image()


        --write text info if needed
        have=""
        if today ~= nil then
            cairo_select_font_face(cr, font, CAIRO_FONT_SLANT_NORMAL, CAIRO_FONT_WEIGHT_NORMAL    )
            cairo_set_line_width(cr,0)
            cairo_set_font_size(cr,font_size_info)
            cairo_set_source_rgba (cr, info_color[1]/255, info_color[2]/255, info_color[3]/255,1);

            have = string.split(today[3],"*")
            for i=1,#have do 
                cairo_move_to(cr,10,height/2+(i-#have/2)*font_size_info)
                cairo_show_text(cr, have[i])
                cairo_fill(cr)
            end
        end    

    end
end 

```

To quote you:
> **wlourf said:**
> Any comments are welcome, of course :P

As soon as I get my lower jaw off the floor, and have the doc wire it into place, I'll be back make a comment.

**[SIZE="6"][COLOR="Blue"]WoW![/COLOR][/SIZE]** Simply does NOT cut it!

---

### Post by Bruce M. on 2010-01-14
> **dmillerct said:**
> No, I am just swamped with work and family issues this month. I probably could of slapped something together however I really wanted to make something special and just ran out of time.

On a related note, I wanted to use the prize money to some how give back to the conky community. After discussing this with a few buds here, there really wasn't anything that could be purchased from amazon to benefit everyone (directly anyway).

So I did what I thought was the next best thing and got the following:
[IMG]http://ecx.images-amazon.com/images/I/31S6MZ1DCVL._BO2,204,203,200_PIsitb-sticker-arrow-click,TopRight,35,-76_AA240_SH20_OU01_.jpg[/IMG]

and
[IMG]http://ecx.images-amazon.com/images/I/51gUR%2Bt6K6L._BO2,204,203,200_PIsitb-sticker-arrow-click,TopRight,35,-76_AA240_SH20_OU01_.jpg[/IMG]

I figure with these at least I can help in-directly help the community. :P

Looks good on you.
CHIMO!
Bruce

---

### Post by mobilediesel on 2010-01-15
> **Bruce M. said:**
> Oh, OK.  Clear as mud.
{psst, Tom, does that do it for you? I didn't think so, back to reading}

They couldn't do something simple like:

**remind.txt**
```
Jan 1
Feb 15 May 12th Jun 18 Oct 22
```
for remind to read ...  nooooooooooooo that would be too easy.  :)



Now that language I understand perfectly, it's called: *copy/paste*. :lolflag:

Seriously:  Gotta read up on Remind, I like it.

CHIMO
Bruce

Remind can be pretty powerful. When you set up birthdays you can have it tell you how old someone will be! I also have it set to tell me when Daylight Saving Time begins and ends.

---

### Post by Bruce M. on 2010-01-15
> **mobilediesel said:**
> Remind can be pretty powerful. When you set up birthdays you can have it tell you how old someone will be! I also have it set to tell me when Daylight Saving Time begins and ends.

${grumble grumble} darned script junkies!
I'll get it ... someday when I have time.

CHIMO!
Bruce

---

### Post by abumaia on 2010-01-30
> **wlourf said:**
> Well as you can see, it's a circular calendar (wheel of time, you know ...) associated with a text file where you can set your bank holiday and adding some text inside the circle. All is drawn with lua!

Nice calendar!  Wish I could get it to work on my computer. I keep getting
> ***** Imlib2 Developer Warning ***** :
	This program is calling the Imlib call:

	imlib_free_image();

	With the parameter:

	image

	being NULL. Please fix your program. (among many others) whenever I try to use it

---

### Post by wlourf on 2010-01-31
> **abumaia said:**
> Nice calendar!  Wish I could get it to work on my computer. I keep getting
 (among many others) whenever I try to use it
please post your conky -v (because you need at least conky 1.7.2 with imlib)

Did you setup a correct path in the lua script ? image_tmp="/tmp/img_cal.png"

Also, you should post the beginning of the error message that will say on which line is the error.
At least, you can try the last version of the script [here]("http://u-scripts.blogspot.com/2010/01/calendar-wheel-v12.html").  If you have no deviant art account, I can post it here.

hth

---

### Post by abumaia on 2010-01-31
> **wlourf said:**
> please post your conky -v (because you need at least conky 1.7.2 with imlib)

Did you setup a correct path in the lua script ? image_tmp="/tmp/img_cal.png"

Also, you should post the beginning of the error message that will say on which line is the error.
At least, you can try the last version of the script [here]("http://u-scripts.blogspot.com/2010/01/calendar-wheel-v12.html").  If you have no deviant art account, I can post it here.

hth

```
$ conky -v
Conky 1.7.2 compiled Fri Oct 23 15:55:48 UTC 2009 for Linux 2.6.24-23-server (i686)

Compiled in features:

System config file: /etc/conky/conky.conf
Package library path: /usr/lib/conky

 X11:
  * Xdamage extension
  * XDBE (double buffer extension)
  * Xft

 Music detection:
  * MPD
  * MOC

 General:
  * math
  * hddtemp
  * portmon
  * Curl
  * RSS
  * Weather (METAR)
  * Weather (XOAP)
  * wireless
  * support for IBM/Lenovo notebooks
  * nvidia
  * eve-online
  * config-output
  * Imlib2
  * ALSA mixer support
  * apcupsd
  * iostats
  * Lua

  Lua bindings:
   * Cairo
   * Imlib2
```path is a correct, full path: /home/abumaia/ConkyScripts/img_cal.png

cannot reach the beginning of the error messages, they scroll beyond the capacity of my terminal buffer.  here is the full section of errors, this group repeats itself over and over:
> ***** Imlib2 Developer Warning ***** :
    This program is calling the Imlib call:

    imlib_create_rotated_image();

    With the parameter:

    image

    being NULL. Please fix your program.
***** Imlib2 Developer Warning ***** :
    This program is calling the Imlib call:

    imlib_free_image();

    With the parameter:

    image

    being NULL. Please fix your program.
***** Imlib2 Developer Warning ***** :
    This program is calling the Imlib call:

    imlib_image_get_width();

    With the parameter:

    image

    being NULL. Please fix your program.
***** Imlib2 Developer Warning ***** :
    This program is calling the Imlib call:

    imlib_image_get_height();

    With the parameter:

    image

    being NULL. Please fix your program.
***** Imlib2 Developer Warning ***** :
    This program is calling the Imlib call:

    imlib_render_image_on_drawable();

    With the parameter:

    image

    being NULL. Please fix your program.
***** Imlib2 Developer Warning ***** :
    This program is calling the Imlib call:

    imlib_free_image();

    With the parameter:

    image

    being NULL. Please fix your program.

I did try yours, downloaded from DA.  It works when I call your script from your conky file, but not when I call your script from my conky file, and they both call the lua file exactly the same.
****

---

### Post by wlourf on 2010-02-01
> **abumaia said:**
> 
I did try yours, downloaded from DA.  It works when I call your script from your conky file, but not when I call your script from my conky file, and they both call the lua file exactly the same.

Interesting! in the conkyrc you need at least one line (empty or not) after the word **TEXT**.
Just check that or post your conkyrc

---

### Post by abumaia on 2010-02-01
> **wlourf said:**
> Interesting! in the conkyrc you need at least one line (empty or not) after the word **TEXT**.
Just check that or post your conkyrc

Yup, I have just an "A" after text, as it's a test conkyrc, and not my main one.  
****

---

### Post by dk75 on 2010-02-01
interesting, that in dev version or in 1.8.x it is no longer true ;P

---

### Post by Bruce M. on 2010-02-04
Since I can't write a script - I need help.

> if_match - - expression - - - Evaluates the given boolean expression, printing everything between $if_match and the matching $endif depending on whether the evaluation returns true or not. Valid expressions consist of a left side, an operator and a right side. Left and right sides are being parsed for contained text objects before evaluation. Recognised left and right side types are:

    * double - Argument consists of only digits and a single dot.
    * long - Argument consists of only digits.
    * string - Argument is enclosed in quotation mark or the checks for double and long failed before.

Valid operands are: '>', '<', '>=', '<=', '==', '!='. 

Unfortunately, if_match does NOT evaluate "><" (greater than or less than)

Sooooooooooo:

${if_match ${time %y} == 00}${color}${else}${color4}
${if_match ${time %y} == 01}${color}${else}${color4}
${if_match ${time %y} == 02}${color}${else}${color4}
${if_match ${time %y} == 03}${color}${else}${color4}
${if_match ${time %y} == 04}${color}${else}${color4}
- - - {snip a whole bunch}
${if_match ${time %y} == 94}${color}${else}${color4}
${if_match ${time %y} == 95}${color}${else}${color4}
${if_match ${time %y} == 96}${color}${else}${color4}
${if_match ${time %y} == 97}${color}${else}${color4}
${if_match ${time %y} == 98}${color}${else}${color4}
${if_match ${time %y} == 99}${color}${else}${color4}

all on one line and ending with 100 ${endif} statements is a tad much

Any scripter out the that can take:

${time %y}/10 = I.D (Intiger point Deciaml)

Then I could do

${if_match ${I} == 0}${color}${else}${color4}
${if_match ${I} == 1}${color}${else}${color4}
${if_match ${I} == 2}${color}${else}${color4}
${if_match ${I} == 3}${color}${else}${color4}
${if_match ${I} == 4}${color}${else}${color4}
${if_match ${I} == 5}${color}${else}${color4}
${if_match ${I} == 6}${color}${else}${color4}
${if_match ${I} == 7}${color}${else}${color4}
${if_match ${I} == 8}${color}${else}${color4}
${if_match ${I} == 9}${color}${else}${color4}
on one line with 9 ${endif} statements
and continue with${else}
${if_match ${D} == 0}${color}${else}${color4}
${if_match ${D} == 1}${color}${else}${color4}
${if_match ${D} == 2}${color}${else}${color4}
${if_match ${D} == 3}${color}${else}${color4}
${if_match ${D} == 4}${color}${else}${color4}
${if_match ${D} == 5}${color}${else}${color4}
${if_match ${D} == 6}${color}${else}${color4}
${if_match ${D} == 7}${color}${else}${color4}
${if_match ${D} == 8}${color}${else}${color4}
${if_match ${D} == 9}${color}${else}${color4}
on one line with 9 ${endif} statements

Anyone up to a challange?

Thanks, Have a nice day.
Bruce

---

### Post by mobilediesel on 2010-02-04
> **Bruce M. said:**
> Since I can't write a script - I need help.



Unfortunately, if_match does NOT evaluate "><" (greater than or less than)

Sooooooooooo:

Anyone up to a challange?

Thanks, Have a nice day.
Bruce

Hmmm... possibly.. 
> Unfortunately, if_match does NOT evaluate "><" (greater than or less than)
Do you mean it doesn't evaluate them both at the same time or either one of them separate?

---

### Post by Bruce M. on 2010-02-04
> **mobilediesel said:**
> Hmmm... possibly.. 

Do you mean it doesn't evaluate them both at the same time or either one of them separate?

Valid operands are: '>', '<', '>=', '<=', '==', '!='. 

There are 100 years in a century, if I use '==' I need 100 ${if_matching}, 100 ${else} and 100 ${endif} statements.

If I use '>=' it's the same because I'll need 100 >= statements.

I need the "Decades" and the "Years" ie: 61/10 = 6.1 filter the 6 and the 1 as two separate variables and I'm down to 18 of eaxt ${ifmatching ${else} and ${endif}  A lot less computer intensive.

I want to fill the space.
CHIMO!
Bruce

---

### Post by dk75 on 2010-02-05
> **Bruce M. said:**
> Unfortunately, if_match does NOT evaluate "><" (greater than or less than)

Bruce, wasn't "greater than or less than" is equal to "not equal"?
If it is then "!=" is your "bingo!" :roll:

PS: ${execi 3600 echo $[$(date +%C)+1]} for century

---

### Post by mobilediesel on 2010-02-05
> **Bruce M. said:**
> Valid operands are: '>', '<', '>=', '<=', '==', '!='. 

There are 100 years in a century, if I use '==' I need 100 ${if_matching}, 100 ${else} and 100 ${endif} statements.

If I use '>=' it's the same because I'll need 100 >= statements.

I need the "Decades" and the "Years" ie: 61/10 = 6.1 filter the 6 and the 1 as two separate variables and I'm down to 18 of eaxt ${ifmatching ${else} and ${endif}  A lot less computer intensive.

I want to fill the space.
CHIMO!
Bruce

Lemme see the rest of the code you have so far.

> **dk75 said:**
> Bruce, wasn't "greater than or less than" is equal to "not equal"?
If it is then "!=" is your "bingo!" :roll:

PS: ${execi 3600 echo $[$(date +%C)+1]} for century

That looks like it's on the right track!

---

### Post by wlourf on 2010-02-06
As I post my entry for the January's CotM here, I just want to say [FONT=Comic Sans MS]**[COLOR=Red]THANKS[/COLOR]**[/FONT] to all people who vote for my conky script because I won this contest !!
Also I updated this script, with :
- today's date can now be set anywere in the arc : **yoffset**
- today's date can now have an offset (positive or negative) : **xoffset**
- the main thing is that** the calendar is draw only at the start of the conky and when the date change** (i.e. the calendar is saved in a PNG file and this is this file that will be displayed in the conky) or if the PNG file is deleted : so the conky become really really fast ...
- it can be drawn on the right side of the screen
(more info on my blog)


Edit  22 Feb 2010, new version (1.3) with minor changes can be downloaded in the attachments
Edit 01 April 2010, version 1.3a : updatedREADME with some feedbacks I received
Edit 6 april 2010 - v1.4 : This calendar is now a widget and it can be call with a simple function with some parameters. To use the calendar, you don't need to copy/paste the code in your lua script, just import the script file with his path (more infos in the README):
```
dofile("/home/wlourf/calendar/calendar.lua")
```Edit 7 april 2010 - v1.4.1 : new parameters for font and alpha of text info and for calendar.txt file

---

### Post by varsamakos on 2010-02-06
Hey wlourf,

Congrats for your conky.

I was trying to make it work in my desktop (latest version)
and I've got a problem.

Things are doing fine and calendar is working
but when I click out of its layer, it disappears.
(see attachment, the layer's end is visible on the right)

(btw, I don't know if it matters but I changed the size to 300x800 for other conky's sake)

---

### Post by Bruce M. on 2010-02-06
> **dk75 said:**
> Bruce, wasn't "greater than or less than" is equal to "not equal"?
If it is then "!=" is your "bingo!" :roll:

PS: ${execi 3600 echo $[$(date +%C)+1]} for century

Don't want the century, just the "decade" and the "year" number For example next year will be 2011 so I need it to look like:

> X O O    X 0 0
0 0 0    0 0 0
0 0 0    0 0 0

and in 2012

```
X 0 0    0 X 0
0 0 0    0 0 0
0 0 0    0 0 0
```

and "!=" would be a case of another 100 commands.  :(

Have a nice day
Bruce

---

### Post by dk75 on 2010-02-06
```
echo $(date +%y) |cut -c1
```
will give you decade

```
echo $(date +%y) |cut -c2
```
will give you year in that decade

---

### Post by Bruce M. on 2010-02-06
> **mobilediesel said:**
> Lemme see the rest of the code you have so far.

That looks like it's on the right track!

I'm not so sure.  Here is the code I have, it only has **1 line** for the years but I'm getting errors already, and I need two more.  That's why I was wondering is a bash script could take the %y command and divide by 10 and somehow saving the "Decade" and "Year" as seperate variable I cna use.

```
0 bruloo@bruloo: ~
Sat Feb 06, 11:51 $ killall conky
0 bruloo@bruloo: ~
Sat Feb 06, 11:53 $ conky -c $HOME/Conky/OB_Dots
Conky: unknown variable e
Conky: one or more $endif's are missing
Conky: desktop window (1a7) is root window
Conky: window type - normal
Conky: drawing to created window (0xc00001)
Conky: drawing to double buffer
```

EDIT: I counted if_matching and endif's. They are equal.

Here's the code with the one line between **[COLOR="Green"]years[/COLOR]**:

```
background no
own_window yes
own_window_type normal
own_window_transparent no
own_window_hints skip_taskbar,skip_pager
own_window_title DotsBox
use_xft yes
xftfont webdings:size=12
xftalpha 1
update_interval 1.0
total_run_times 0
double_buffer yes
minimum_size 100 100
maximum_width 200
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders yes
default_color white
default_shade_color black
default_outline_color white
alignment br
gap_x 30
gap_y 65
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no

# Colors
default_color 7FFF00 #Chartreuse
color0 FFFFF0 #Ivory
color1 FFA07A #LightSalmon
color2 FF8C00 #Darkorange
color3 7FFF00 #Chartreuse
color4 778899 #LightSlateGrey
color5 FFDEAD #NavajoWhite
color6 00BFFF #DeepSkyBlue
#	colours below used by colorize script
color7 48D1CC #MediumTurquoise
color8 FFFF00 #Yellow
color9 FF0000 #Red


TEXT
${font dodger:size=12}${color3}TOTA ${color0}Linux
${goto 25}${color3}ALMINAC${COLOR}${font}
${font webdings: size=12}${if_match ${time %I} == 1}${color}${else}${color4}${endif}= ${if_match ${time %I} == 2}${color}${else}${color4}${endif}= ${if_match ${time %I} == 3}${color}${else}${color4}${endif}=   ${goto 101}${if_match ${time %m} == 1}${color}${else}${color4}${endif}= ${if_match ${time %m} == 2}${color}${else}${color4}${endif}= ${if_match ${time %m} == 3}${color}${else}${color4}${endif}=
${if_match ${time %I} == 4}${color}${else}${color4}${endif}= ${if_match ${time %I} == 5}${color}${else}${color4}${endif}= ${if_match ${time %I} == 6}${color}${else}${color4}${endif}=   ${goto 101}${if_match ${time %m} == 4}${color}${else}${color4}${endif}= ${if_match ${time %m} == 5}${color}${else}${color4}${endif}= ${if_match ${time %m} == 6}${color}${else}${color4}${endif}=
${if_match ${time %I} == 7}${color}${else}${color4}${endif}= ${if_match ${time %I} == 8}${color}${else}${color4}${endif}= ${if_match ${time %I} == 9}${color}${else}${color4}${endif}=   ${goto 101}${if_match ${time %m} == 7}${color}${else}${color4}${endif}= ${if_match ${time %m} == 8}${color}${else}${color4}${endif}= ${if_match ${time %m} == 9}${color}${else}${color4}${endif}=
${if_match ${time %I} == 10}${color}${else}${color4}${endif}= ${if_match ${time %I} == 11}${color}${else}${color4}${endif}= ${if_match ${time %I} == 12}${color}${else}${color4}${endif}=   ${goto 101}${if_match ${time %m} == 10}${color}${else}${color4}${endif}= ${if_match ${time %m} == 11}${color}${else}${color4}${endif}= ${if_match ${time %m} == 12}${color}${else}${color4}${endif}=
${color7}${font DejaVu Sans Mono:bold:size=8}${goto 25}Hour${goto 115}Month${font}${color}
${if_match ${time %M} == 10}${color}${else}${color4}${if_match ${time %M} == 11}${color}${else}${color4}${if_match ${time %M} == 12}${color}${else}${color4}${if_match ${time %M} == 13}${color}${else}${color4}${if_match ${time %M} == 14}${color}${else}${color4}${if_match ${time %M} == 15}${color}${else}${color4}${if_match ${time %M} == 16}${color}${else}${color4}${if_match ${time %M} == 17}${color}${else}${color4}${if_match ${time %M} == 18}${color}${else}${color4}${if_match ${time %M} == 19}${color}${else}${color4}${endif}${endif}${endif}${endif}${endif}${endif}${endif}${endif}${endif}${endif}= ${if_match ${time %M} == 20}${color}${else}${color4}${if_match ${time %M} == 21}${color}${else}${color4}${if_match ${time %M} == 22}${color}${else}${color4}${if_match ${time %M} == 23}${color}${else}${color4}${if_match ${time %M} == 24}${color}${else}${color4}${if_match ${time %M} == 25}${color}${else}${color4}${if_match ${time %M} == 26}${color}${else}${color4}${if_match ${time %M} == 27}${color}${else}${color4}${if_match ${time %M} == 28}${color}${else}${color4}${if_match ${time %M} == 29}${color}${else}${color4}${endif}${endif}${endif}${endif}${endif}${endif}${endif}${endif}${endif}${endif}= ${if_match ${time %M} == 30}${color}${else}${color4}${if_match ${time %M} == 31}${color}${else}${color4}${if_match ${time %M} == 32}${color}${else}${color4}${if_match ${time %M} == 33}${color}${else}${color4}${if_match ${time %M} == 34}${color}${else}${color4}${if_match ${time %M} == 35}${color}${else}${color4}${if_match ${time %M} == 36}${color}${else}${color4}${if_match ${time %M} == 37}${color}${else}${color4}${if_match ${time %M} == 38}${color}${else}${color4}${if_match ${time %M} == 39}${color}${else}${color4}${endif}${endif}${endif}${endif}${endif}${endif}${endif}${endif}${endif}${endif}=   ${goto 101}${if_match ${time %d} == 10}${color}${else}${color4}${if_match ${time %d} == 11}${color}${else}${color4}${if_match ${time %d} == 12}${color}${else}${color4}${if_match ${time %d} == 13}${color}${else}${color4}${if_match ${time %d} == 14}${color}${else}${color4}${if_match ${time %d} == 15}${color}${else}${color4}${if_match ${time %d} == 16}${color}${else}${color4}${if_match ${time %d} == 17}${color}${else}${color4}${if_match ${time %d} == 18}${color}${else}${color4}${if_match ${time %d} == 19}${color}${else}${color4}${endif}${endif}${endif}${endif}${endif}${endif}${endif}${endif}${endif}${endif}= ${if_match ${time %d} == 20}${color}${else}${color4}${if_match ${time %d} == 21}${color}${else}${color4}${if_match ${time %d} == 22}${color}${else}${color4}${if_match ${time %d} == 23}${color}${else}${color4}${if_match ${time %d} == 24}${color}${else}${color4}${if_match ${time %d} == 25}${color}${else}${color4}${if_match ${time %d} == 26}${color}${else}${color4}${if_match ${time %d} == 27}${color}${else}${color4}${if_match ${time %d} == 28}${color}${else}${color4}${if_match ${time %d} == 29}${color}${else}${color4}${endif}${endif}${endif}${endif}${endif}${endif}${endif}${endif}${endif}${endif}= ${if_match ${time %d} == 30}${color}${else}${color4}${if_match ${time %d} == 31}${color}${else}${color4}${if_match ${time %d} == 32}${color}${else}${color4}${if_match ${time %d} == 33}${color}${else}${color4}${if_match ${time %d} == 34}${color}${else}${color4}${if_match ${time %d} == 35}${color}${else}${color4}${if_match ${time %d} == 36}${color}${else}${color4}${if_match ${time %d} == 37}${color}${else}${color4}${if_match ${time %d} == 38}${color}${else}${color4}${if_match ${time %d} == 39}${color}${else}${color4}${endif}${endif}${endif}${endif}${endif}${endif}${endif}${endif}${endif}${endif}=
${if_match ${time %M} == 40}${color}${else}${color4}${if_match ${time %M} == 41}${color}${else}${color4}${if_match ${time %M} == 42}${color}${else}${color4}${if_match ${time %M} == 43}${color}${else}${color4}${if_match ${time %M} == 44}${color}${else}${color4}${if_match ${time %M} == 45}${color}${else}${color4}${if_match ${time %M} == 46}${color}${else}${color4}${if_match ${time %M} == 47}${color}${else}${color4}${if_match ${time %M} == 48}${color}${else}${color4}${if_match ${time %M} == 49}${color}${else}${color4}${endif}${endif}${endif}${endif}${endif}${endif}${endif}${endif}${endif}${endif}= ${if_match ${time %M} == 50}${color}${else}${color4}${if_match ${time %M} == 51}${color}${else}${color4}${if_match ${time %M} == 52}${color}${else}${color4}${if_match ${time %M} == 53}${color}${else}${color4}${if_match ${time %M} == 54}${color}${else}${color4}${if_match ${time %M} == 55}${color}${else}${color4}${if_match ${time %M} == 56}${color}${else}${color4}${if_match ${time %M} == 57}${color}${else}${color4}${if_match ${time %M} == 58}${color}${else}${color4}${if_match ${time %M} == 59}${color}${else}${color4}${endif}${endif}${endif}${endif}${endif}${endif}${endif}${endif}${endif}${endif}= ${color4}=
${color7}${font DejaVu Sans Mono:bold:size=8}${goto 18}Min x10${goto 110}Day x10${font}${color}
${if_match ${time %M} == 01}${color}${else}${color4}${if_match ${time %M} == 11}${color}${else}${color4}${if_match ${time %M} == 21}${color}${else}${color4}${if_match ${time %M} == 31}${color}${else}${color4}${if_match ${time %M} == 41}${color}${else}${color4}${if_match ${time %M} == 51}${color}${else}${color4}${endif}${endif}${endif}${endif}${endif}${endif}= ${if_match ${time %M} == 02}${color}${else}${color4}${if_match ${time %M} == 12}${color}${else}${color4}${if_match ${time %M} == 22}${color}${else}${color4}${if_match ${time %M} == 32}${color}${else}${color4}${if_match ${time %M} == 42}${color}${else}${color4}${if_match ${time %M} == 52}${color}${else}${color4}${endif}${endif}${endif}${endif}${endif}${endif}= ${if_match ${time %M} == 03}${color}${else}${color4}${if_match ${time %M} == 13}${color}${else}${color4}${if_match ${time %M} == 23}${color}${else}${color4}${if_match ${time %M} == 33}${color}${else}${color4}${if_match ${time %M} == 43}${color}${else}${color4}${if_match ${time %M} == 53}${color}${else}${color4}${endif}${endif}${endif}${endif}${endif}${endif}=   ${goto 101}${if_match ${time %d} == 01}${color}${else}${color4}${if_match ${time %d} == 11}${color}${else}${color4}${if_match ${time %d} == 21}${color}${else}${color4}${if_match ${time %d} == 31}${color}${else}${color4}${if_match ${time %d} == 41}${color}${else}${color4}${if_match ${time %d} == 51}${color}${else}${color4}${endif}${endif}${endif}${endif}${endif}${endif}= ${if_match ${time %d} == 02}${color}${else}${color4}${if_match ${time %d} == 12}${color}${else}${color4}${if_match ${time %d} == 22}${color}${else}${color4}${if_match ${time %d} == 32}${color}${else}${color4}${if_match ${time %d} == 42}${color}${else}${color4}${if_match ${time %d} == 52}${color}${else}${color4}${endif}${endif}${endif}${endif}${endif}${endif}= ${if_match ${time %d} == 03}${color}${else}${color4}${if_match ${time %d} == 13}${color}${else}${color4}${if_match ${time %d} == 23}${color}${else}${color4}${if_match ${time %d} == 33}${color}${else}${color4}${if_match ${time %d} == 43}${color}${else}${color4}${if_match ${time %d} == 53}${color}${else}${color4}${endif}${endif}${endif}${endif}${endif}${endif}=
${if_match ${time %M} == 04}${color}${else}${color4}${if_match ${time %M} == 14}${color}${else}${color4}${if_match ${time %M} == 24}${color}${else}${color4}${if_match ${time %M} == 34}${color}${else}${color4}${if_match ${time %M} == 44}${color}${else}${color4}${if_match ${time %M} == 54}${color}${else}${color4}${endif}${endif}${endif}${endif}${endif}${endif}= ${if_match ${time %M} == 05}${color}${else}${color4}${if_match ${time %M} == 15}${color}${else}${color4}${if_match ${time %M} == 25}${color}${else}${color4}${if_match ${time %M} == 35}${color}${else}${color4}${if_match ${time %M} == 45}${color}${else}${color4}${if_match ${time %M} == 55}${color}${else}${color4}${endif}${endif}${endif}${endif}${endif}${endif}= ${if_match ${time %M} == 06}${color}${else}${color4}${if_match ${time %M} == 16}${color}${else}${color4}${if_match ${time %M} == 26}${color}${else}${color4}${if_match ${time %M} == 36}${color}${else}${color4}${if_match ${time %M} == 46}${color}${else}${color4}${if_match ${time %M} == 56}${color}${else}${color4}${endif}${endif}${endif}${endif}${endif}${endif}=   ${goto 101}${if_match ${time %d} == 04}${color}${else}${color4}${if_match ${time %d} == 14}${color}${else}${color4}${if_match ${time %d} == 24}${color}${else}${color4}${if_match ${time %d} == 34}${color}${else}${color4}${if_match ${time %d} == 44}${color}${else}${color4}${if_match ${time %d} == 54}${color}${else}${color4}${endif}${endif}${endif}${endif}${endif}${endif}= ${if_match ${time %d} == 05}${color}${else}${color4}${if_match ${time %d} == 15}${color}${else}${color4}${if_match ${time %d} == 25}${color}${else}${color4}${if_match ${time %d} == 35}${color}${else}${color4}${if_match ${time %d} == 45}${color}${else}${color4}${if_match ${time %d} == 55}${color}${else}${color4}${endif}${endif}${endif}${endif}${endif}${endif}= ${if_match ${time %d} == 06}${color}${else}${color4}${if_match ${time %d} == 16}${color}${else}${color4}${if_match ${time %d} == 26}${color}${else}${color4}${if_match ${time %d} == 36}${color}${else}${color4}${if_match ${time %d} == 46}${color}${else}${color4}${if_match ${time %d} == 56}${color}${else}${color4}${endif}${endif}${endif}${endif}${endif}${endif}=
${if_match ${time %M} == 07}${color}${else}${color4}${if_match ${time %M} == 17}${color}${else}${color4}${if_match ${time %M} == 27}${color}${else}${color4}${if_match ${time %M} == 37}${color}${else}${color4}${if_match ${time %M} == 47}${color}${else}${color4}${if_match ${time %M} == 57}${color}${else}${color4}${endif}${endif}${endif}${endif}${endif}${endif}= ${if_match ${time %M} == 08}${color}${else}${color4}${if_match ${time %M} == 18}${color}${else}${color4}${if_match ${time %M} == 28}${color}${else}${color4}${if_match ${time %M} == 38}${color}${else}${color4}${if_match ${time %M} == 48}${color}${else}${color4}${if_match ${time %M} == 58}${color}${else}${color4}${endif}${endif}${endif}${endif}${endif}${endif}= ${if_match ${time %M} == 09}${color}${else}${color4}${if_match ${time %M} == 19}${color}${else}${color4}${if_match ${time %M} == 29}${color}${else}${color4}${if_match ${time %M} == 39}${color}${else}${color4}${if_match ${time %M} == 49}${color}${else}${color4}${if_match ${time %M} == 59}${color}${else}${color4}${endif}${endif}${endif}${endif}${endif}${endif}=   ${goto 101}${if_match ${time %d} == 07}${color}${else}${color4}${if_match ${time %d} == 17}${color}${else}${color4}${if_match ${time %d} == 27}${color}${else}${color4}${if_match ${time %d} == 37}${color}${else}${color4}${if_match ${time %d} == 47}${color}${else}${color4}${if_match ${time %d} == 57}${color}${else}${color4}${endif}${endif}${endif}${endif}${endif}${endif}= ${if_match ${time %d} == 08}${color}${else}${color4}${if_match ${time %d} == 18}${color}${else}${color4}${if_match ${time %d} == 28}${color}${else}${color4}${if_match ${time %d} == 38}${color}${else}${color4}${if_match ${time %d} == 48}${color}${else}${color4}${if_match ${time %d} == 58}${color}${else}${color4}${endif}${endif}${endif}${endif}${endif}${endif}= ${if_match ${time %d} == 09}${color}${else}${color4}${if_match ${time %d} == 19}${color}${else}${color4}${if_match ${time %d} == 29}${color}${else}${color4}${if_match ${time %d} == 39}${color}${else}${color4}${if_match ${time %d} == 49}${color}${else}${color4}${if_match ${time %d} == 59}${color}${else}${color4}${endif}${endif}${endif}${endif}${endif}${endif}=
${color7}${font DejaVu Sans Mono:bold:size=8}${goto 28}Min${goto 125}Day${font}${color}

${font DejaVu Sans Mono:bold:size=8}years${font}${color}
${if_match ${time %y} == 10}${color}${else}${color4}${if_match ${time %y} == 11}${color}${else}${color4}${if_match ${time %y} == 21}${color}${else}${color4}${if_match ${time %y} == 31}${color}${else}${color4}${if_match ${time %y} == 41}${color}${else}${color4}${if_match ${time %y} == 51}${color}${else}${color4}${if_match ${time %y} == 61}${color}${else}${color4}${if_match ${time %y} == 71}${color}${else}${color4}${if_match ${time %y} == 81}${color}${else}${color4}${if_match ${time %y} == 91}${color}${else}${color4}${endif}${endif}${endif}${endif}${endif}${endif}${endif}${endif}${endif}${endif}= ${if_match ${time %y} == 02}${color}${else}${color4}${if_match ${time %y} == 12}${color}${else}${color4}${if_match ${time %y} == 22}${color}${else}${color4}${if_match ${time %y} == 32}${color}${else}${color4}${if_match ${time %y} == 42}${color}${else}${color4}${if_match ${time %y} == 52}${color}${else}${color4}${if_match ${time %y} == 62}${color}${else}${color4}${if_match ${time %y} == 72}${color}${else}${color4}${if_match ${time %y} == 82}${color}${else}${color4}${if_match ${time %y} == 92}${color}${else}${color4}${endif}${endif}${endif}${endif}${endif}${endif}${endif}${endif}${endif}${endif}= ${if_match ${time %y} == 03}${color}${else}${color4}${if_match ${time %y} == 13}${color}${else}${color4}${if_match ${time %y} == 23}${color}${else}${color4}${if_match ${time %y} == 33}${color}${else}${color4}${if_match ${time %y} == 43}${color}${else}${color4}${if_match ${time %y} == 53}${color}${else}${color4}${if_match ${time %y} == 63}${color}${else}${color4}${if_match ${time %y} == 73}${color}${else}${color4}${if_match ${time %y} == 83}${color}${else}${color4}${if_match ${time %y} == 93}${color}${else}${color4}${endif}${endif}${endif}${endif}${endif}${endif}${endif}${endif}${endif}${endif}= ${goto 101}${if_match ${time %y} == 01}${color}${else}${color4}${if_match ${time %y} == 11}${color}${else}${color4}${if_match ${time %y} == 21}${color}${else}${color4}${if_match ${time %y} == 31}${color}${else}${color4}${if_match ${time %y} == 41}${color}${else}${color4}${if_match ${time %y} == 51}${color}${else}${color4}${if_match ${time %y} == 61}${color}${else}${color4}${if_match ${time %y} == 71}${color}${else}${color4}${if_match ${time %y} == 81}${color}${else}${color4}${if_match ${time %y} == 91}${color}${else}${color4}${endif}${endif}${endif}${endif}${endif}${endif}${endif}${endif}${endif}${endif}= ${if_match ${time %y} == 02}${color}${else}${color4}${if_match ${time %y} == 12}${color}${else}${color4}${if_match ${time %y} == 32}${color}${else}${color4}${if_match ${time %y} == 32}${color}${else}${color4}${if_match ${time %y} == 42}${color}${else}${color4}${if_match ${time %y} == 52}${color}${else}${color4}${if_match ${time %y} == 62}${color}${else}${color4}${if_match ${time %y} == 72}${color}${else}${color4}${if_match ${time %y} == 82}${color}${else}${color4}${if_match ${time %y} == 92}${color}${else}${color4}${endif}${endif}${endif}${endif}${endif}${endif}${endif}${endif}${endif}${endif}= ${if_match ${time %y} == 03}${color}${else}${color4}${if_match ${time %y} == 13}${color}${else}${color4}${if_match ${time %y} == 23}${color}${else}${color4}${if_match ${time %y} == 33}${color}${else}${color4}${if_match ${time %y} == 43}${color}${else}${color4}${if_match ${time %y} == 53}${color}${else}${color4}${if_match ${time %y} == 63}${color}${else}${color4}${if_match ${time %y} == 73}${color}${else}${color4}${if_match ${time %y} == 83}${color}${else}${color4}${if_match ${time %y} == 93}${color}${else}${color4}${endif}${endif}${endif}${endif}${endif}${endif}${endif}${endif}${endif}${endif}= 
${font DejaVu Sans Mono:bold:size=8}years${font}${color}

${color7}${font DejaVu Sans Mono:bold:size=8}${goto 28}Yr x10${goto 125}Yr${font}${color}
${if_match ${cpu cpu1} >0}${color}${else}${color4}${endif}=${if_match ${cpu cpu1} >10}${color}${else}${color4}${endif}=${if_match ${cpu cpu1} >20}${color}${else}${color4}${endif}=${if_match ${cpu cpu1} >30}${color}${else}${color4}${endif}=${if_match ${cpu cpu1} >40}${color}${else}${color4}${endif}=${if_match ${cpu cpu1} >50}${color}${else}${color4}${endif}=${if_match ${cpu cpu1} >60}${color}${else}${color4}${endif}=${if_match ${cpu cpu1} >70}${color}${else}${color4}${endif}=${if_match ${cpu cpu1} >80}${color}${else}${color4}${endif}=${if_match ${cpu cpu1} >90}${color}${else}${color4}${endif}=
${color7}${font DejaVu Sans Mono:bold:size=8}${goto 28}C P U${font}${color} 
${if_match ${memperc} >0}${color}${else}${color4}${endif}=${if_match ${memperc} >10}${color}${else}${color4}${endif}=${if_match ${memperc} >20}${color}${else}${color4}${endif}=${if_match ${memperc} >30}${color}${else}${color4}${endif}=${if_match ${memperc} >40}${color}${else}${color4}${endif}=${if_match ${memperc} >50}${color}${else}${color4}${endif}=${if_match ${memperc} >60}${color}${else}${color4}${endif}=${if_match ${memperc} >70}${color}${else}${color4}${endif}=${if_match ${memperc} >80}${color}${else}${color4}${endif}=${if_match ${memperc} >90}${color}${else}${color4}${endif}=
${color7}${font DejaVu Sans Mono:bold:size=8}${goto 28}MEMORY${font}${color}

```

As you can see it's very heavy on "if_matching" even for the time it's a lot..

Any help appreciated.
Bruce

---

### Post by wlourf on 2010-02-06
> **varsamakos said:**
> Hey wlourf,

Congrats for your conky.

I was trying to make it work in my desktop (latest version)
and I've got a problem.

Things are doing fine and calendar is working
but when I click out of its layer, it disappears.
(see attachment, the layer's end is visible on the right)

(btw, I don't know if it matters but I changed the size to 300x800 for other conky's sake)

I think you have changed some things in your conkyrc, especially in the window block :
```
own_window yes
own_window_type desktop
own_window_transparent yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below
```can you check or post your conkyrc?

---

### Post by wlourf on 2010-02-06
> **Bruce M. said:**
> As you can see it's very heavy on "if_matching" even for the time it's a lot..

Any help appreciated.
Bruce

Hi Bruce, I don't answer to your question but as your conky seems very hard to read, did you try to use Lua to achieve what you want.
Here is a small example for a clock that is more readable !

The conkyrc (just set the path at the line lua_load ~/scripts/test/dots.lua):
```
background no
own_window yes
own_window_type normal
own_window_transparent no
own_window_hints skip_taskbar,skip_pager
own_window_title DotsBox
use_xft yes
xftalpha 1
update_interval 1.0
total_run_times 0
double_buffer yes
minimum_size 200 100
maximum_width 200
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders yes
default_color white
default_shade_color black
default_outline_color white
alignment br
gap_x 30
gap_y 65
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no

# Colors
default_color 7FFF00 #Chartreuse

# -- Lua load -- #
lua_load ~/scripts/test/dots.lua
lua_draw_hook_pre main

TEXT
${time}




       H      Mx10     S
```the lua script :
```
require 'cairo'

function draw_block(nb_cols,nb_rows,off_x,off_y,delta_x,delta_y,value)
    local idx=-1
    for yi=1,nb_rows do  
        for xi=1,nb_cols do
            idx=idx+1
            if idx==value then
                cairo_set_source_rgba(cr,1,0,0,1)
            else
                cairo_set_source_rgba(cr,0,0,1,1)
            end
            cairo_move_to(cr,off_x+xi*delta_x,off_y+yi*delta_y)
            cairo_show_text(cr,"=")
        end
    end
end

function conky_main()
    if conky_window==nil then return end
    local w=conky_window.width
    local h=conky_window.height
    local cs=cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, w, h)
    cr=cairo_create(cs)

    cairo_set_source_rgba(cr,1,0,0,1)
    cairo_select_font_face(cr,"webdings",
        CAIRO_FONT_SLANT_NORMAL, CAIRO_FONT_WEIGHT_BOLD)
    
    local hours=tonumber(os.date("%H"))
    if hours>12 then hours=hours-12 end --another way to do this
    local mins=math.floor(os.date("%M")/10,0)    
    local secs=math.floor(os.date("%S")/5,0)
    draw_block(3,4,10,30,15,15,hours)
    draw_block(3,2,60,30,15,15,mins)    
    draw_block(3,4,110,30,15,15,secs)

    cairo_stroke(cr)
    cairo_destroy(cr)
end
```hth !

---

### Post by varsamakos on 2010-02-06
> **wlourf said:**
> I think you have changed some things in your conkyrc, especially in the window block :
```
own_window yes
own_window_type desktop
own_window_transparent yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below
```can you check or post your conkyrc?

I didn't. I took it directly from your files.
Here it is :

```
# -- Conky settings -- #
background no
update_interval 5

cpu_avg_samples 2
net_avg_samples 2

override_utf8_locale yes

double_buffer yes
no_buffers yes

text_buffer_size 2048
imlib_cache_size 0

# -- Window specifications -- #

own_window yes
own_window_type desktop
own_window_transparent yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below

border_inner_margin 0
border_outer_margin 0

minimum_size 300 800

alignment tl
gap_y 0
gap_x 0

# -- Graphics settings -- #
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no

# -- Text settings -- #
use_xft yes
xftfont Santana:size=12
xftalpha 0.8

uppercase yes

default_color FFFFFF

# -- Lua load -- #
lua_load ~/.scripts/calendar.lua
lua_draw_hook_pre main

TEXT

```

---

### Post by wlourf on 2010-02-06
hi varsamakos
Sorry, I tried the script with gnome and openbox but didn't manage to reproduce your problem. (with conky 1.7.2).:-(

---

### Post by varsamakos on 2010-02-06
I'm running conky in version 1.8.0
maybe I should downgrade ?

**Edit**:
Just tested with 1.7.2.
Same problem :/

a click out of layer and ...
[http://www.youtube.com/watch?v=i71Gg1njyTQ](http://www.youtube.com/watch?v=i71Gg1njyTQ)

---

### Post by Bruce M. on 2010-02-06
> **wlourf said:**
> Hi Bruce, I don't answer to your question but as your conky seems very hard to read, did you try to use Lua to achieve what you want.
Here is a small example for a clock that is more readable !

I've seen that somewhere, but can's figure out the seconds on that one.  :)

Besides, I didn't want to use LUA for this.

Have a nice day.
Bruce

---

### Post by Bruce M. on 2010-02-06
> **dk75 said:**
> ```
echo $(date +%y) |cut -c1
```
will give you decade

```
echo $(date +%y) |cut -c2
```
will give you year in that decade

Thanks dk75, it works great in a terminal.  :)

I REALLY REALLY hate being "script deficient" and having too much on my plate at this stage of my life to learn.

```
# Colors
default_color 7FFF00 #Chartreuse
color0 FFFFF0 #Ivory
color1 FFA07A #LightSalmon
color2 FF8C00 #Darkorange
color3 7FFF00 #Chartreuse
color4 778899 #LightSlateGrey
color5 FFDEAD #NavajoWhite
color6 00BFFF #DeepSkyBlue
#	colours below used by colorize script
color7 48D1CC #MediumTurquoise
color8 FFFF00 #Yellow
color9 FF0000 #Red

TEXT
${font webdings: size=12}
${color}= ${color4}= =${goto 101}= = =
= = =${goto 101}= = =
= = =${goto 101}= = =${color}
${color7}${font DejaVu Sans Mono:bold:size=8}${goto 28}Yr x10${goto 125}Yr${font}${color}

=
${if_match {echo $(date +%y) |cut -c1} == 1}${color}${else}${color4}${endif}=
${if_match {echo $(date +%y) |cut -c1} == 2}${color}${else}${color4}${endif}=
${font}
```

Hard coded above just to display (20)10

That first = should be green and is,
the second should be green and is
the third should be grey, it's green  :(

Maybe that command doesn't work inside an "if_matching" command.

Did I say that I hate being "script deficient"?

Any ideas?

Have a nice day
Bruce

PS  Have to run, back tomorrow

---

### Post by mobilediesel on 2010-02-07
> **Bruce M. said:**
> Don't want the century, just the "decade" and the "year" number For example next year will be 2011 so I need it to look like:



and in 2012

```
X 0 0    0 X 0
0 0 0    0 0 0
0 0 0    0 0 0
```

and "!=" would be a case of another 100 commands.  :(

Have a nice day
Bruce

Is this possibly what you are looking for?
[ATTACH]146298[/ATTACH]
If so, for lack of a better name, [dotdatetime.sh]("http://dl.dropbox.com/u/1055489/scripts/dotdatetime.sh") is what I called it. It might still need some tweaking to the text alignment.
```
#!/bin/bash
############################################################
# This work is licensed under the Creative Commons         #
# Attribution-Share Alike 3.0 Unported License.            #
# To view a copy of this license, visit                    #
# http://creativecommons.org/licenses/by-sa/3.0/           #
# or send a letter to Creative Commons, 171 Second Street, #
# Suite 300, San Francisco, California, 94105, USA.        #
############################################################
cd $(dirname $0)
DATE=$(date +%y%m%d%I%M)
CURRENT="\${color 7FFF00}"
DEFAULT="\${color 778899}"
TEXT="\${color 48D1CC}"
MONTH=${DATE:2:2}
HOUR=${DATE:6:2}
YEAR10C[${DATE:0:1}]="$CURRENT"
YEARC[${DATE:1:1}]="$CURRENT"
MONTHC[${MONTH/#0/}]="$CURRENT"
DAY10C[${DATE:4:1}]="$CURRENT"
DAYC[${DATE:5:1}]="$CURRENT"
HOURC[${HOUR/#0/}]="$CURRENT"
MIN10C[${DATE:8:1}]="$CURRENT"
MINC[${DATE:9:1}]="$CURRENT"
YEAR10R[${DATE:0:1}]="$DEFAULT"
YEARR[${DATE:1:1}]="$DEFAULT"
MONTHR[${MONTH/#0/}]="$DEFAULT"
DAY10R[${DATE:4:1}]="$DEFAULT"
DAYR[${DATE:5:1}]="$DEFAULT"
HOURR[${HOUR/#0/}]="$DEFAULT"
MIN10R[${DATE:8:1}]="$DEFAULT"
MINR[${DATE:9:1}]="$DEFAULT"
echo -n "\${font webdings:size=12}$DEFAULT"
for n in 1 4 7 10; do
    for i in $(seq $n $[n+2]); do
        echo -n "${HOURC[$i]}=${HOURR[$i]} "
    done
echo -n "\${goto 101}"
    for i in $(seq $n $[n+2]); do
        echo -en "${MONTHC[$i]}=${MONTHR[$i]} "
    done
echo
done
echo "$TEXT\${font DejaVu Sans Mono:bold:size=8}\${goto 25}Hour\${goto 115}Month\${font webdings:size=12}$DEFAULT"
for n in 1 2 3; do
    echo -n "${MIN10C[$n]}=${MIN10R[$n]} "
done
echo -n "\${goto 101}"
for n in 1 2 3; do
    echo -n "${DAY10C[$n]}=${DAY10R[$n]} "
done
echo
for n in 4 5 6; do
    echo -n "${MIN10C[$n]}=${MIN10R[$n]} "
done
echo -e "\n$TEXT\${font DejaVu Sans Mono:bold:size=8}\${goto 18}Min x10\${goto 110}Day x10\${font webdings:size=12}$DEFAULT"
for n in 1 4 7; do
    for i in $(seq $n $[n+2]); do
        echo -n "${MINC[$i]}=${MINR[$i]} "
    done
echo -n "\${goto 101}"
    for i in $(seq $n $[n+2]); do
        echo -en "${DAYC[$i]}=${DAYR[$i]} "
    done
echo
done
echo "$TEXT\${font DejaVu Sans Mono:bold:size=8}\${goto 28}Min\${goto 125}Day\${font webdings:size=12}$DEFAULT"
for n in 1 4 7; do
    for i in $(seq $n $[n+2]); do
        echo -n "${YEAR10C[$i]}=${YEAR10R[$i]} "
    done
echo -n "\${goto 101}"
    for i in $(seq $n $[n+2]); do
        echo -en "${YEARC[$i]}=${YEARR[$i]} "
    done
echo
done
echo "$TEXT\${font DejaVu Sans Mono:bold:size=8}\${goto 28}Year x10\${goto 110}Year$DEFAULT"
```

---

### Post by wlourf on 2010-02-07
> **varsamakos said:**
> I'm running conky in version 1.8.0
maybe I should downgrade ?

**Edit**:
Just tested with 1.7.2.
Same problem :/

a click out of layer and ...
[http://www.youtube.com/watch?v=i71Gg1njyTQ](http://www.youtube.com/watch?v=i71Gg1njyTQ)
this is a private video, it seems that I can't play it, even with my youtube account ...

Edit : I saw the video, and I already understood the problem but I can't fix it since I can't reproduce it, sorry about that, try google with "conky disappear click"

---

### Post by varsamakos on 2010-02-07
My bad. It's ok now.
Note : @0.12 I just clicked in destkop.

---

### Post by mobilediesel on 2010-02-07
> **mobilediesel said:**
> ${font webdings:size=12}

I should point out that the webdings font is part of the [**msttcorefonts**]("http://packages.ubuntu.com/search?searchon=names&keywords=msttcorefonts") package which is in the Ubuntu Multiverse repositories.

I discovered that when I tried the script on my wife's computer and it showed a bunch of equal signs instead of dots.

[dotdatetime.sh]("http://dl.dropbox.com/u/1055489/scripts/dotdatetime.sh") has been updated a couple times since I first posted it. Minor stuff.

---

### Post by dk75 on 2010-02-08
> **varsamakos said:**
> I'm running conky in version 1.8.0
maybe I should downgrade ?

**Edit**:
Just tested with 1.7.2.
Same problem :/

a click out of layer and ...
[http://www.youtube.com/watch?v=i71Gg1njyTQ](http://www.youtube.com/watch?v=i71Gg1njyTQ)

set some variables in conkyrc to
```
own_window_type normal
```
```
own_window_class Conky
```
```
own_window_title Conky
```

install Compiz configuration
```
sudo apt-get install compizconfig-settings-manager
```

go to "General Options" and there to "Focus & Raise Behaviour", disable "Auto raise" and set "Focus Prevention Window" to
```
!(class=Polkit-gnome-authentication-agent-1) | class=Nautilus | class=Conky
```

and if you use "Add Helper" plugin then go to it's settings, "Misc. Options", then in "Window Types" add this to default string
```
& !(class=Gimp-2.6 | class=Conky)
```

---

### Post by varsamakos on 2010-02-08
It works :)
Thanks dk75 !

I've added the variables and changed *Focus Prevention Window* value.

One last question. Which variable makes calendar's layer
look like it's a bit above the rest of my desktop ?
I mean, the line where each layer ends.

---

### Post by wlourf on 2010-02-09
well done dk75 !
@varsamakos, I'm not sure to understand your question, did you try to change hgradient (like in picture attached) ?

---

### Post by varsamakos on 2010-02-09
Here it is :
[[img]http://www.ubuntu-pics.de/thumb/41787/screenshot_001_OxdJaI.png[/img]](http://www.ubuntu-pics.de/bild/41787/screenshot_001_OxdJaI.png)

It looks like it's above the desktop.
You can see the difference in wallpaper.

---

### Post by wlourf on 2010-02-09
Hello again varsamakos,

In your conky you have :
```
alignment tl
gap_y 0
gap_x 0
```which mean top-left alignment, but you have also a taskbar in the top of your window, so you probably should add a gap greater than the height of your taskbar.
And if your screen is 800 pixels height, just reduce the minimum_size and use alignment bl

At least, you should have :

```
alignment tl
gap_y 50
gap_x 0
minimum_size 300 750

```or 

```
alignment bl
 gap_y 00
 gap_x 0
minimum_size 300 750

```Way to perfection is not so easy :p
I don't use taskbar so I didn't notice this behaviour, but I reproduced after adding some taskbars, maybe dk75 has a trick to change this behaviour!

PS. I've tested that with own_window_type set to desktop or normal

---

### Post by dmillerct on 2010-02-09
> **varsamakos said:**
> Here it is :
[[img]http://www.ubuntu-pics.de/thumb/41787/screenshot_001_OxdJaI.png[/img]](http://www.ubuntu-pics.de/bild/41787/screenshot_001_OxdJaI.png)

It looks like it's above the desktop.
You can see the difference in wallpaper.

Try this:

[http://conky.linux-hardcore.com/?page_id=3744]("http://conky.linux-hardcore.com/?page_id=3744")

---

### Post by dk75 on 2010-02-09
strange, I have shadow for any window but Conky don't have it... could it be
```
own_window_argb_visual yes
```
in conkyrc v1.8.0rc1?

---

### Post by varsamakos on 2010-02-09
A change in gap_y (30px in my case) variable did the trick :)
Before that, the change in compiz's shadow didn't make any change.

Thank you guys :)

---

### Post by wlourf on 2010-02-11
Hello again.

I wrote a new widget (a bar graph like on old equalizers) but fully configurable as you can see on the pictures.
Any feedback is welcome if you try it (or don't !)

Edit 28 Feb 2010 : the widget is renamed to bargraph
Edit 03 March 2010 : the bargraph can be drawn on a circular way
Edit 14 July 2010 : add reflection parameter and set-u are now made in a table, it's more easy to configure.

Last version of the script can be downloaded on deviantArt : [http://wlourf.deviantart.com/gallery/?offset=0#/d2jj1rz](http://wlourf.deviantart.com/gallery/?offset=0#/d2jj1rz)

---

### Post by Bruce M. on 2010-02-11
> **wlourf said:**
> Hello again.

I wrote a new widegt (a bar graph like on old equalizers) but fully configurable as you can see on the pictures.
Any feedback is welcome if you try it (or don't !)

w.

Now that's GREAT!

Very nice work.

+1 for you.

Have a nice day.
Bruce

---

### Post by dmillerct on 2010-02-11
> **wlourf said:**
> Hello again.

I wrote a new widegt (a bar graph like on old equalizers) but fully configurable as you can see on the pictures.
Any feedback is welcome if you try it (or don't !)

w.

Very impressive!

---

### Post by wlourf on 2010-02-12
thanks ! if you try it on your own, it would be nice to see a capture !

Edit : just for fun (because it can use too much cpu) , a moving equalizer : [video here]("http://www.youtube.com/watch?v=qv7IvnRWdvo")

---

### Post by wlourf on 2010-02-21
Hi all,

While I was working on an equalizer widget, I tried an audio equalizer for conky. Well, it was easy because the work was already done for a screenlet for gnome (Impulse):
[https://launchpad.net/impulse.bzr](https://launchpad.net/impulse.bzr)

So the work was only to adapt scripts from python to lua. I've done it for two "themes" default and circle like on the picture.

If you want to try it, you have to set the path in the conkyrc (all variables are set in conkyrc so there is no need to make any changes in the lua script)

And you need to download the C library from the Impulse web site :
[http://gnome-look.org/content/show.php/?content=99383](http://gnome-look.org/content/show.php/?content=99383)
just copy impulse.so and libimpulse.so into the script folder.

the Lua script call the python script, in fact I use this line because i didn't find a better way to do it, so if you have any ideas !
conky_parse('${exec python impulse.py'}')

In the tar.gz, there is the conkyrc, the lua and python scripts and the two librairies .so.

If you have any question, don't hesitate.

Edit 28 Feb. 2010 : with the help of the auhor of Impulse, I managed to make something faster ! You can see [here]("http://www.youtube.com/watch?v=hP9Wt7YKoHM") in action but the sound is crap, sorry for your ears...
I also added peaks like on the video and it is possible to use this widget with the bargraph widget I made a few weeks ago

Edit 10 March 2010 : the conkyrc can be called with an absolute path.
I added last version of the bargraph widget which can be drawn on a circular way.
And another [video]("http://www.youtube.com/watch?v=rcM9nTKeC74&feature=channel") with better sound

---

### Post by airtonix on 2010-02-21
> **wlourf said:**
> As I post my entry for the January's CotM here, I just want to say [FONT=Comic Sans MS]**[COLOR=Red]THANKS[/COLOR]**[/FONT] to all people who vote for my conky script because I won this contest !!
Also I updated this script, with :
- today's date can now be set anywere in the arc : **yoffset**
- today's date can now have an offset (positive or negative) : **xoffset**
- the main thing is that** the calendar is draw only at the start of the conky and when the date change** (i.e. the calendar is saved in a PNG file and this is this file that will be displayed in the conky) or if the PNG file is deleted : so the conky become really really fast ...
- it can be drawn on the right side of the screen
(more info on my blog)

See you in February maybe :p
Some great work , but unfortunately it does not work without some fixing : 

```
~/Desktop/calendar_wheel_1.2a$ conky -c conky-calendar 
>>>>>> Conky: conky-calendar: 19: config file error
>1. >> Conky: llua_load: cannot open /home/airtonix/scripts/cal1.2/calendar.lua: No such file or directory
Conky: desktop window (1e00276) is subwindow of root window (157)
Conky: window type - normal
Conky: drawing to created window (0x5000001)
Conky: drawing to double buffer
> 2. >> Conky: llua_do_call: function conky_main execution failed: attempt to call a nil value
Conky: llua_do_call: function conky_main execution failed: attempt to call a nil value
...
etc
etc
etc
...

``````
$ conky -v
Conky 1.7.2 compiled Fri Oct 23 15:55:48 UTC 2009 for Linux 2.6.24-23-server (i686)

Compiled in features:

System config file: /etc/conky/conky.conf
Package library path: /usr/lib/conky

 X11:
  * Xdamage extension
  * XDBE (double buffer extension)
  * Xft

 Music detection:
  * MPD
  * MOC

 General:
  * math
  * hddtemp
  * portmon
  * Curl
  * RSS
  * Weather (METAR)
  * Weather (XOAP)
  * wireless
  * support for IBM/Lenovo notebooks
  * nvidia
  * eve-online
  * config-output
  * Imlib2
  * ALSA mixer support
  * apcupsd
  * iostats
  * Lua

  Lua bindings:
   * Cairo
   * Imlib2

```also two things : 

1. conky-calendar
@line48 :  
```
lua_load ~/scripts/cal1.2/calendar.lua
```change to : 
```
lua_load ./calendar.lua
```>> assume the lua file will sit in the same place as the conky script.
>> otherwise you'll need to start creating a README file. to explain why the files need to be split all over the drive and what happens if you do or don't.

2. calendar.lua
@ line31 :```
     calendar_file="/home/wlourf/scripts/cal1.2/calendar.txt" 
```change to : 
```

    local current_directory=assert( io.popen('pwd'):read("*l") )
    calendar_file= current_directory .. "/calendar.txt"

```>> again, assume all required files to make mod/addon/widget/etc work are to be in the same directory. 



all the required files in the same place make the thing more portable... with these changes I was able to get it working.

---

### Post by wlourf on 2010-02-22
Thanks airtonix, I updated the tar.gz on this post, and added a README ;-):
[http://ubuntuforums.org/showpost.php?p=8782789&postcount=147](http://ubuntuforums.org/showpost.php?p=8782789&postcount=147)

Also I would like to show you a nice use of this calendar on ubuntu.ru forums:
[http://forum.ubuntu.ru/index.php?topic=63273.msg638103#msg638103](http://forum.ubuntu.ru/index.php?topic=63273.msg638103#msg638103)
the widgets used for this picture are :
Conky Widgets by londonali1010 (2009) - &#1095;&#1072;&#1089;&#1099; &#1080; &#1082;&#1086;&#1083;&#1100;&#1094;&#1072;
Conky vertical bar graph by iggykoopa - &#1075;&#1086;&#1088;&#1080;&#1079;&#1086;&#1085;&#1090;&#1072;&#1083;&#1100;&#1085;&#1099;&#1081; &#1080; &#1074;&#1077;&#1088;&#1090;&#1080;&#1082;&#1072;&#1083;&#1100;&#1085;&#1099;&#1081; &#1073;&#1072;&#1088;&#1099;
Shadowed clock by wlourf (10 jan. 2010) - &#1089;&#1090;&#1088;&#1077;&#1083;&#1082;&#1080; &#1095;&#1072;&#1089;&#1086;&#1074; &#1089; &#1090;&#1077;&#1085;&#1100;&#1102;
calendar wheel by Wlourf (14 jan. 2010) - &#1082;&#1072;&#1083;&#1077;&#1085;&#1076;&#1072;&#1088;&#1100;

and the result is this nice picture, isn't it ?
[[IMG]http://static.itmages.ru/i/10/0220/h_1266658020_47855c759d.png[/IMG]]("http://itmages.ru/")

---

### Post by mobilediesel on 2010-02-22
> **wlourf said:**
> Thanks airtonix, I updated the tar.gz on this post, and added a README ;-):
[http://ubuntuforums.org/showpost.php?p=8782789&postcount=147](http://ubuntuforums.org/showpost.php?p=8782789&postcount=147)

Also I would like to show you a nice use of this calendar on ubuntu.ru forums:
and the result is this nice picture, isn't it ?
[[IMG]http://static.itmages.ru/i/10/0220/h_1266658020_47855c759d.png[/IMG]]("http://itmages.ru/")

Now I gotta go and upgrade my system so it will support Lua so the newr conky will work. That is just *awesome*

---

### Post by miegiel on 2010-02-22
> **wlourf said:**
> ...

and the result is this nice picture, isn't it ?
[[IMG]http://static.itmages.ru/i/10/0220/h_1266658020_47855c759d.png[/IMG]]("http://itmages.ru/")

Definitely, I was really impressed by the one you posted on the conky blog for conky of the month. Well, impressed by the innovative way to make the calender. To be honest I did think it looked a bit ... euhm ... ugly (sorry :roll:). This one is innovative _and_ looks great. :D

---

### Post by wlourf on 2010-02-22
> **miegiel said:**
> Definitely, I was really impressed by the one you posted on the conky blog for conky of the month. Well, impressed by the innovative way to make the calender. To be honest I did think it looked a bit ... euhm ... ugly (sorry :roll:). This one is innovative _and_ looks great. :D

lol !
Don't be sorry, tastes and colors, you know ... but in changing a few parameters you can adjust it to your taste! if you like the circular shape of course ! :D
Have a nice day

---

### Post by mrpeachy on 2010-02-22
I thought I would share some of the things I've been working on.
I do my conky tinkering on the backwaters of the crunchbanglinux website :D

anyway, a couple of things you might be interested in:

circlewriting
[[IMG]http://omploader.org/tM2w4NQ[/IMG]]("http://omploader.org/vM2w4NQ")
details on my blog: [http://thepeachyblog.blogspot.com/2010/02/i-have-improved-my-circlewriting.html](http://thepeachyblog.blogspot.com/2010/02/i-have-improved-my-circlewriting.html)
(EDIT - I see this has already been put to good use in previous posts :) .  I really ought to start writing intros for my scripts)

alternate graphs
[[IMG]http://omploader.org/tM21qaA[/IMG]]("http://omploader.org/vM21qaA")
you can change the direction that the graph moves in, colors, bar thickness and spacing, have gridlines on or off and graph height and you can edit a setting to get either bars up only, bars down only or bars up and down
[http://thepeachyblog.blogspot.com/2010/02/alternate-graphs.html](http://thepeachyblog.blogspot.com/2010/02/alternate-graphs.html)

You can also see my flower conky entry for the valentines conky of the month via the comments on the conky blog
[http://blog.conky.be/2010/02/03/februarys-cotm-competition-st-valentines-daymassacre/#comments](http://blog.conky.be/2010/02/03/februarys-cotm-competition-st-valentines-daymassacre/#comments)

---

### Post by degan on 2010-02-24
Hi boys....:D

I would want to make a conky.lua as this.

[[IMG]http://upload.centerzone.it/images/73369541832206811637_thumb.jpg[/IMG]](http://upload.centerzone.it/viewer.php?file=73369541832206811637.png)

Instead of visualizing the various dates, I would want to visualize departing from the tall one:

root
home
cpu
ram
ecc
ecc............ 

Can you help me?

Sets the conky & the  .lua to be modified...

Thanks

................

**.conkyrc**

```
# -- Conky settings -- #
background no
update_interval 5

cpu_avg_samples 2
net_avg_samples 2

override_utf8_locale yes

double_buffer yes
no_buffers yes

text_buffer_size 2048
imlib_cache_size 0

# -- Window specifications -- #

own_window yes
own_window_type desktop
own_window_transparent yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below

border_inner_margin 0
border_outer_margin 0

minimum_size 300 800

alignment tl
gap_y 0
gap_x 0

# -- Graphics settings -- #
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no

# -- Text settings -- #
use_xft yes
xftfont Santana:size=12
xftalpha 0.8

uppercase yes

default_color FFFFFF

# -- Lua load -- #
lua_load /Scrivania/deegan.lua
lua_draw_hook_pre main

TEXT
```

**.lua**

```
--[[
calendar wheel by Wlourf (14 jan. 2010)

This script is designed to draw dates on a circular way on the left of the screen.
Some text info can be added in the circle with the file calendar.txt (see below)
Some parameters (colors, sizes ... ) can be adjusted (see below).

As this script draw a png file only if necessary, a short update of the conky can be used.

Call this script in Conky using the following before TEXT (assuming you save this script to ~/scripts/calendar.lua):
	lua_load ~/scripts/calendar.lua
	lua_draw_hook_pre main
	
	
v1.0 - 14 jan. 2010 - Original release
v1.1 - 19 jan. 2010 - Calendar are now drawn in an PNG file and this file 
	is called at every conky call, when day change, a new PNG file is created.
	- An x offset can be added to "Today's block"
	- An y offset can be added too to "Today's block"
v1.2 - 28 jan. 2010 - Calendar can be drawn on the right side of the conky (but without text info)
	- Calendar is drawn after the second conky refresh only
v1.2a - 29 jan. 2010 - Minor update, picture was refresh every second instead of every day
v1.3 - 22 Feb. 2010 - calendar.txt is now relative to this script path


]]

require 'cairo'
require 'imlib2'

-------------------------- parameters (part one) are set here -----------------------------------

	--text file calendar (in the folder of this script
	local current_directory=assert( io.popen('pwd'):read("*l") )
    calendar_file= current_directory .. "/calendar.txt"	
	--format of in this text file
	--MMDD;N;TEXT
	--MMDD = month day
	--N    = 0 or 1 (1 to display same colors as week-ends)
	--TEXT = Text to display (use * for multiline)

	--some paths to images created (absolutes paths)
	image_tmp="/tmp/img_tmp.png" --used to rotate a single date
	image_calendar="/tmp/conky-calendar-arc.png"
	image_dates="/tmp/conky-calendar-dates.png"

	--more parameters below
-------------------------- end of parameters (part one) -----------------------------------	
	

function string:split(delimiter)
--source for the split function : http://www.wellho.net/resources/ex.php4?item=u108/split
  local result = { }
  local from  = 1
  local delim_from, delim_to = string.find( self, delimiter, from  )
  while delim_from do
    table.insert( result, string.sub( self, from , delim_from-1 ) )
    from  = delim_to + 1
    delim_from, delim_to = string.find( self, delimiter, from  )
  end
  table.insert( result, string.sub( self, from  ) )
  return result
end


function conky_draw_calendar()
	if conky_window==nil then return end
	local width=conky_window.width
	local height=conky_window.height
	
	--sometimes, there is problem with init and width & height are set to 0 or 2 !!
	if width<3 or height<3 then return end
	
	local cs=cairo_image_surface_create(CAIRO_FORMAT_ARGB32, width, height)
	local cr=cairo_create(cs)
	
	-------------------------- parameters (part two) are set here -----------------------------------
	
	-- vertical center of the circle (height/2 for centered circle)
	local yc=height/2
	
	--number of days to display before and after today (i.e. with range = 30 --> 60 days are displayed)
	--even number between 20 and 30 for nice effect
	local range = 20
	
	--not sure of the engish words so I leave then in french !	
	--fleche (arrow) is the segment from x=0 to x=radius-xc (with xc =center of the circle) 
	--fleche for the external circle
	--fleche2 for the internal circle
	--fleche2 must be < fleche
	local fleche=150
	local fleche2=fleche*.5
	
	--corde (chord) is the vertical segment (where x=0) of the external circle
	local corde = height
			
	--colors RGB (0-255)
	--week day
	local wday={50,50,255}
	--week-end and bank holidays defined in calendar.txt
	local eday={255,255,126}
	--color of today
	local dday={255,0,0}
	
	--vertical gradient (both circle and dates)? (true/false)
	local vgradient=true
	
	--horizontal gradient for the circle? (0 to 1, 0 is the best choice for "moon like" circle )
	local hgradient=0
	
	--you can change the font here
	local font="Japan"
	--font_size (of dates) must be less than delta (= heigth of a day)
	local delta = yc/(range+0.5)
	--the font-size has to be adjusted depending on the font used
	local font_size=delta-2
	
	--information text (from calendar.txt)
	local info_color={0,255,204}
	--font size of text infos
	local font_size_info=font_size

	--today_xoffset is the offset for the date of today (can be positive/null/negative, in pixels)
	local today_xoffset=10
	
	--today_yoffset where today will be displayed (value between -range to + range)?
	-- 0 = center of the arc
	-- -range =  top of the arc
	-- +range = bottom of the arc
	local today_yoffset=-9
	
	--display on right side of the screen (true/false)
	local align_right = false
	
	-------------------------- end of the parameters, ouf -----------------------------------

	--some calculations
	--radius for external circle
	--radius2 for internal circle
	--delta = number of arcs in the circle
	local radius=(corde^2+4*fleche^2)/(8*fleche)
	local radius2=(corde^2+4*fleche2^2)/(8*fleche2)
 	local decal=2*(delta-font_size)
	wday[1]=wday[1]/255
	wday[2]=wday[2]/255
	wday[3]=wday[3]/255	
	eday[1]=eday[1]/255
	eday[2]=eday[2]/255
	eday[3]=eday[3]/255	

	--xc =x center of external circle
	--xc2=x center of internal circle
	local xc = fleche - radius	
	local xc2 = fleche2 - radius2
	
	if align_right then 
		xc = width-xc
		xc2 = width-xc2
	end

	local h_txt = height/(2*range+1)
	
	local t = os.date('*t') -- date in table
	--get the date
	local s = os.time(t) -- date in seconds

	--read the calendar file
	local file = io.open(calendar_file,"r")	
	local tabcal={}	
	local idx=1
	local line,lineok="",""
	if file ~= nil then
		while true do
		 	line = file:read("*l")
		    if line == nil then break end
			lineok = string.split(line,";")
			if (#lineok)==3 then
				tabcal[idx]={lineok[1],lineok[2],lineok[3]}
				idx=idx+1
			end
		end
	end	
	io.close()
	local angmini=math.atan((corde/2)/(radius-fleche))

	local imageDates=imlib_create_image(width,height)
	imlib_context_set_image(imageDates)
	imlib_image_set_has_alpha(1)
	imlib_save_image(image_dates)

	for i=-range,range do
		local s2 = s + 3600*24*(i-today_yoffset) --date diff in seconds

		local wd = os.date("%w",s2)
		local md = os.date("%m%d",s2)
		local dt = os.date("%a. %d %b.",s2),os.date("%d",s2),os.date("%b",s2)

		--percentage of vertical gradient
		local pc = (range-math.abs(i))/range
		if not vgradient then pc=1 end

		--angle min et max of one block
		local ang0 = angmini*(i-0.5)/range
		local ang1 = angmini*(i+0.5)/range
		if align_right then 
			ang0=math.pi-ang0
			ang1=math.pi-ang1
		end
		local angm = (ang0+ang1)/2
		
		--read the calendar.txt array
		local flag = false
		for idy=1,idx-1 do
			if tabcal[idy][1] == md then
				if (i-today_yoffset) == 0 then
					today = tabcal[idy]
				end
				if tabcal[idy][2] == "1" then
					flag = true
				end
				break
			end
		end

		--colors
		local colR,colG,colB=0,0,0
		if wd=="6" or wd=="0" or flag == true then
			colR,colG,colB=eday[1],eday[2],eday[3]
		else
			colR,colG,colB=wday[1],wday[2],wday[3]
		end
		
		--offset of today 
		local offset_x=0
		local way = 1
		if (i-today_yoffset)==0 then 
			if align_right then way =-1 end
			offset_x=today_xoffset*way 
		end

		local pat = cairo_pattern_create_radial (xc+offset_x, yc, radius,
         			xc2+offset_x,yc,radius2);
		
		cairo_pattern_add_color_stop_rgba (pat, 0, colR, colG, colB, pc);
		cairo_pattern_add_color_stop_rgba (pat, 1, colR, colG, colB, hgradient);
		
		cairo_set_source (cr, pat);
		--draw the portion of arc
		if align_right then
			x1,y1=radius*math.cos(ang0)+xc+offset_x,(radius-offset_x)*math.sin(ang0)+yc
			x2,y2=radius*math.cos(ang1)+xc+offset_x,(radius-offset_x)*math.sin(ang1)+yc
		else
			x1,y1=radius*math.cos(ang0)+xc+offset_x,(radius+offset_x)*math.sin(ang0)+yc
			x2,y2=radius*math.cos(ang1)+xc+offset_x,(radius+offset_x)*math.sin(ang1)+yc
		end
		cairo_move_to(cr,x1,y1)
		cairo_line_to(cr,x2,y2)
		cairo_line_to(cr,xc,yc)
		cairo_fill(cr)
		
		--for tests
		if (i-today_yoffset)==0 then
		--cairo_set_source_rgba (cr,1, 0,0,1);
		--cairo_arc(cr,x1,y1,1,0,2*math.pi)
		--cairo_stroke(cr)
		--cairo_arc(cr,xc,yc,radius,0,2*math.pi)
		--cairo_stroke(cr)
		--cairo_set_source_rgba (cr,0, 1, 0,pc);
		--cairo_arc(cr,x2,y2,1,0,2*math.pi)
		--cairo_stroke(cr)
		end

		--write text info if needed, for left-side calendar only
		local have=""
		if (today ~= nil) and (align_right ~= true) then
			cairo_select_font_face(cr, font, CAIRO_FONT_SLANT_NORMAL, CAIRO_FONT_WEIGHT_NORMAL	)
			cairo_set_line_width(cr,0)
			cairo_set_font_size(cr,font_size_info)
			cairo_set_source_rgba (cr, info_color[1]/255, info_color[2]/255, info_color[3]/255,1);

			have = string.split(today[3],"*")
			for i=1,#have do 
				cairo_move_to(cr,10,height/2+(i-#have/2)*font_size_info)
				cairo_show_text(cr, have[i])
				cairo_fill(cr)
			end
		end	

		--lenght of the arc
		local dx,dy=math.abs(x2-x1),math.abs(y2-y1)
		local h_txt=math.sqrt(dx*dx+dy*dy)
		local w_txt=font_size*10

		--write text in another image for working (rotate) on it
		--didn't find to work in memory only
		local cs2=cairo_image_surface_create(CAIRO_FORMAT_ARGB32, w_txt, h_txt)
		local cr2=cairo_create(cs2)
		cairo_set_font_size (cr2, font_size);
		if (i-today_yoffset)==0 then 
			colR, colG, colB = dday[1]/255,dday[2]/255,dday[3]/255
			pc=1
		end
		cairo_select_font_face(cr2, font, CAIRO_FONT_SLANT_NORMAL, CAIRO_FONT_WEIGHT_NORMAL)

		--write ONE date in ONE picture		
		local txt_date = " " .. dt .. " "
		--start the drawing date here in order to get the lenght of the text
		--for right alignement
		cairo_move_to(cr2,0,h_txt-decal)--+offset_x*math.atan(ang0))
		cairo_set_source_rgba (cr2, colR, colG, colB,pc)
		cairo_show_text(cr2, txt_date)

		if align_right then
			local xmax,ymax=cairo_get_current_point(cr2,0,0)
			--don't use local for cs2fit cause local will be just for if .. end section
			--and then surface will not be deleted --> memory leak
			cs2fit = cairo_image_surface_create(CAIRO_FORMAT_ARGB32, xmax, h_txt)
			cr2fit = cairo_create(cs2fit)
			

			cairo_set_font_size (cr2fit, font_size);
			cairo_select_font_face(cr2fit, font, CAIRO_FONT_SLANT_NORMAL, CAIRO_FONT_WEIGHT_NORMAL)
			cairo_move_to(cr2fit,0,h_txt -decal)
			cairo_set_source_rgba (cr2fit, colR, colG, colB,pc)
			cairo_show_text(cr2fit, txt_date)

			cairo_stroke(cr2fit)
			cairo_surface_write_to_png(cs2fit,image_tmp)
			
		else
			cairo_stroke(cr2)
			cairo_surface_write_to_png(cs2,image_tmp)
		end
	
		--blend date image on cairo surface
		local imageTmp = imlib_load_image(image_tmp)
		imlib_context_set_image(imageTmp)

		if align_right then
			rot_img = imlib_create_rotated_image(angm+math.pi)
		else
			rot_img = imlib_create_rotated_image(angm)
		end

		imlib_context_set_image(imageTmp)
		imlib_free_image()
	
		--image is now a  square
		imlib_context_set_image(rot_img)
		local w_img0, h_img0 = imlib_image_get_width(), imlib_image_get_height()
		
		---look for center of text
		local rt=radius+w_img0/2
		if align_right then	
			rt=rt-offset_x
		else
			rt=rt+offset_x
		end
		local xt=rt*math.cos(angm)+xc-w_img0/2
		local yt=rt*math.sin(angm)+yc-h_img0/2

		imlib_context_set_image(imageDates)
		imlib_blend_image_onto_image(rot_img, 1, 0, 0, w_img0, h_img0, xt,yt, w_img0, h_img0)
		imageDates=imlib_context_get_image()
		imlib_context_set_image(rot_img)
		imlib_free_image()




		if align_right then 
			
			cairo_destroy(cr2fit)
			cairo_surface_destroy(cs2fit)
		end
	
		cairo_destroy(cr2)
		cairo_surface_destroy(cs2)

		cairo_pattern_destroy(pat)
	end --of loop

	--write to disk images with dates only
	imlib_context_set_image(imageDates)
	imlib_save_image(image_dates)	

	--write to disk image with arc only
	cairo_surface_write_to_png(cs,image_calendar)
	
	--make final image
	local imageCal = imlib_load_image(image_calendar)
	imlib_context_set_image(imageCal)
	imlib_blend_image_onto_image(imageDates, 1, 0, 0, width, height, 0,0, width, height)
	
	imlib_save_image(image_calendar)
	imlib_free_image()

	imlib_context_set_image(imageDates)
	imlib_free_image()

	--free memory
	cairo_destroy(cr)
	cairo_surface_destroy(cs)
	
end 


function conky_main()
	--last_date is global 
	local actual_date  = os.date("%Y%m%d") --os.date("%Y%m%d")
	local actual_cal = imlib_load_image(image_calendar)
	if (conky_parse('${updates}')+0) <2  then return end
	if  last_date ~= actual_date or actual_cal == nil then
		--print (os.date("%H%M%S"),'new picture')
		conky_draw_calendar()
		last_date = actual_date
	else
		--print (os.date("%H%M%S"),'use old picture')
	end
	if actual_cal == nil then
		actual_cal = imlib_load_image(image_calendar)
	end
	imlib_context_set_image(actual_cal)
	imlib_render_image_on_drawable(0,0)
	imlib_free_image()
end
```

---

### Post by wlourf on 2010-02-24
Yes, it's possible but the script will need to redraw all the stuff at each update of the conky (the actual script draw all the stuff when conky start and when day change). It may use some cpu (you have to try on your computer) except if you rewrite the script to draw only changed values, which will be more difficult :P

Well, I wrote a quick thing which will draw all the stuff with some conky variables.


Replace the main function with this one :
```
function conky_main()

    --last_date is global 
    --local actual_date  = os.date("%Y%m%d") --os.date("%Y%m%d")
    --local actual_cal = imlib_load_image(image_calendar)
    if (conky_parse('${updates}')+0) <3  then return end
    my_array={
        {-5,conky_parse(' cpu0 ${cpu cpu0}')},
        {5,conky_parse(' cpu1 ${cpu cpu1}')},
    }    


    --if  last_date ~= actual_date or actual_cal == nil then
        conky_draw_calendar()
    --    last_date = actual_date
    --else
        --print (os.date("%H%M%S"),'use old picture')
    --end
--    if actual_cal == nil then
        local actual_cal = imlib_load_image(image_calendar)
--    end
    

    imlib_context_set_image(actual_cal)
    imlib_render_image_on_drawable(0,0)
    imlib_free_image()
end
```As you see, I write the conky variables I want in the array my_array, 
-5 et 5 are the positions of the variables in the arc. You can add more variables if you want of course

And in the function conky_draw_calendar, just add 
```
        for aa = 1,#my_array do
            if my_array[aa][1] == i then
                txt_date = my_array[aa][2]
            end
        end

``` after the line :
local txt_date = " " .. dt .. " "

HTH

---

### Post by mrpeachy on 2010-02-25
here are a couple of other things 
more alternate graphs
[[img]http://omploader.org/tM25keQ[/img]](http://omploader.org/vM25keQ)
[http://thepeachyblog.blogspot.com/2010/02/i-was-having-some-trouble-with-getting.html](http://thepeachyblog.blogspot.com/2010/02/i-was-having-some-trouble-with-getting.html)
Using these graphs, and with some tweaking I produced this:
[[img]http://omploader.org/tM25qNw[/img]](http://omploader.org/vM25qNw)

textblur and shadow effect
[[img]http://omploader.org/tM255Mg[/img]](http://omploader.org/vM255Mg)
[http://thepeachyblog.blogspot.com/2010/02/text-blur-and-shadow.html](http://thepeachyblog.blogspot.com/2010/02/text-blur-and-shadow.html)

---

### Post by wlourf on 2010-02-25
very nice blur, thanks Mr Peachy !

---

### Post by mrpeachy on 2010-02-25
> **wlourf said:**
> very nice blur, thanks Mr Peachy !
you are welcome :D

---

### Post by andreino on 2010-02-25
hy boys
can see the day week
this lua for language Italian?
thanks for the help
[http://forum.ubuntu.ru/index.php?topic=63273.msg638103#msg638103](http://forum.ubuntu.ru/index.php?topic=63273.msg638103#msg638103)

---

### Post by DoeRayMe on 2010-02-25
Still playing around with it, but mostly done

But just wondered, what would be the best way to add cpu temp and anyone know if you can have a hotmail email checker on conky at all?

```
background yes
use_xft yes
xftfont HandelGotD:size=9
xftalpha 0.5
update_interval 1.0
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 200 5
maximum_width 200
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color white
default_shade_color red
default_outline_color green
alignment top_right
gap_x 12
gap_y 48
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no

##The number of samples to average for CPU monitoring
cpu_avg_samples 2

TEXT
${color dark red}SYSTEM ${hr 2}$color
${font sans-serif:bold:size=8}${exec cat /proc/cpuinfo | grep "model name" -m1 | cut -d ":" -f2 | tr -s [:space:] | tr -d [\(TMR\)]}'}
 OS $alignr ${exec lsb_release -is} ${exec lsb_release -rs}
 Uptime $alignr $uptime
 Kernel $alignr $kernel
 GPU $alignr ${exec lspci | grep VGA | cut -c68-81 | head -n1}
 Processes $alignr $processes ($running_processes running)

 CPU $alignr ${cpu cpu0}%
 ${cpubar cpu0}

 MEM $alignc $mem / $memmax $alignr $memperc%
 $membar

 / $alignc ${fs_used /} / ${fs_size /} $alignr ${fs_free_perc /}%
 ${fs_bar /}

 swap $alignc $swap / $swapmax $alignr $swapperc%
 ${swapbar}${font}

${color dark red}INTERNET ${hr 2}$color${font sans-serif:bold:size=8}
 Hostname $alignr $nodename
 IP Address $alignr ${addr wlan1}

 Inbound $alignr ${downspeed wlan1} kb/s
 Outbound $alignr ${upspeed wlan1} kb/s${font}

${color dark red}EMAIL ${hr 2}$color
${font sans-serif:bold:size=8} ${execi 300 python ~/Scripts/conkyEmail.py -e -m IMAP -s imap.aol.com -u wshand4@aol.com -p bouncer -i 10}${font}
```

---

### Post by mrpeachy on 2010-02-25
> **DoeRayMe said:**
> 
But just wondered, what would be the best way to add cpu temp

You can try using ${acpitemp}

or you could install and configure lm-sensors, then try something like:${execi 300 sensors | grep Core}
or look here  [http://conky.linux-hardcore.com/?page_id=393](http://conky.linux-hardcore.com/?page_id=393) for other sensor stuff

I've seen this kind of thing too (1 cpu and lm-sensors installed):
${hwmon temp 1}

lots of ways! :D

---

### Post by HangukMiguk on 2010-02-26
Ugh

So conky is not rendering my font colors when I put them in hex.

Here is my conky config file.  There's only one hex in there, and it's at the top of the TEXT area.

Can anyone tell me if my syntax looks wrong?

```

use_xft yes
xftfont sans Bold:size=9
double_buffer yes

update_interval 1

draw_borders 0
draw_shades yes

no_buffers yes

default_color black
default_shade_color black
default_outline_color black

alignment top_left
maximum_width 325

uppercase no

override_utf8_locale yes

use_spacer yes

TEXT

${color #0C1F22}${font Twelve Ton Sushi:size=15}SYSTEM${hr 2}
$font${color red}$nodename $kernel (Linux Mint 8)
Uptime ${color grey}$uptime
${color red}CPU: ${color grey}$cpu% ${color red}                 RAM: ${color grey}$mem/$memmax
${color red}HD: ${color grey}${fs_used /}/${fs_free /} ${color red}Swap: ${color grey}$swap/$swapmax
${color red}Processes: ${color grey}$processes ${color red}        Running: ${color grey}$running_processes
${color red}Battery: ${color grey}${battery BAT1}
$color${font Twelve Ton Sushi:size=15}NETWORK${hr 2}
$font${color red}SSID: ${color grey}${wireless_essid wlan0} ${color red}(${color grey}${addr wlan0}${color red})
${color red}Download: ${color grey}${downspeedf wlan0}      $font${color red}Upload: ${color grey}${upspeedf wlan0}
$color}${font Twelve Ton Sushi:size=15}TWITTER${hr 2}
$font${color grey}$font${color grey}${rss http://xxx:xxx@twitter.com/statuses/friends_timeline/35138760.rss 20 item_titles 5}
$color${font Twelve Ton Sushi:size=15}PERSONAL${hr 2}
$font${color red}Gmail: ${color grey}${execi 60 python ~/.scripts/gmail.py} message(s)
$font${color red}Currently: ${color grey}${execi 60 conkyForecast --location=USIL0514 --datatype=CC} ${execi 60 conkyForecast --location=USIL0514 --datatype=HT --imperial}
$font${color red}Rhythmbox: ${color grey}${exec conkyRhythmbox --template=~/.scripts/rhythmbox.template}
```

---

### Post by mrpeachy on 2010-02-26
@ HangukMiguk

# is the symbol conky uses to denote a comment, remove the # and it will work

also heres an idea for colors...

set them before the "TEXT

color1 000000
color2 111111

TEXT

${color1}text${color2}text

---

### Post by miegiel on 2010-02-26
> **mrpeachy said:**
> @ HangukMiguk

# is the symbol conky uses to denote a comment, remove the # and it will work

also heres an idea for colors...

set them before the "TEXT

color1 000000
color2 111111

TEXT

${color1}text${color2}text
```
...
TEXT

...
default color [COLOR="Blue"]${color CCCCCC}[/COLOR] color=cccccc [COLOR="Blue"]${color}[/COLOR] default color
...
```

Should work just as well. But you're right don't use a **[COLOR="Blue"]#[/COLOR]** in the hex color code.

---

### Post by wlourf on 2010-02-26
Hi all,

Here is my entry for this CotM contest : St Valentine's Day /Massacre ! Nice choice by the way :-). [**If you like it, you can vote for it here**]("http://blog.conky.be/2010/03/01/please-vote-on-februarys-cotm-entries/") 

For this, I made a simple blooding heart like on this image:
[[IMG]http://img192.imageshack.us/img192/7800/bloodyg.th.png[/IMG]]("http://img192.imageshack.us/i/bloodyg.png/")
The seven vertical "lines" are linked to conky, from left to right we have:
memperc, cpu0, uploadspeed, mixer volume, download speed, cpu1, running processes.

For better vizualisation, you should see it in action, on this [video]("http://www.youtube.com/watch?v=oeNTK7_20wk").

The same used with a wallpaper from dA : for_a_rainy_day_by_fusiom
[[IMG]http://img695.imageshack.us/img695/1174/withwallpaperd.th.png[/IMG]]("http://img695.imageshack.us/i/withwallpaperd.png/")


With the same script, I can choose other shapes, for example, a heart breathing :
[[IMG]http://img534.imageshack.us/img534/729/hearthm.th.png[/IMG]]("http://img534.imageshack.us/i/hearthm.png/")
This one is linked to cpu usage on this [video]("http://www.youtube.com/watch?v=zuf6IBtS-Hs").

But, if you don't care with heart and things like that, you can draw your own shape.
This one for example :
[[IMG]http://img692.imageshack.us/img692/5288/eightcorners.th.png[/IMG]]("http://img692.imageshack.us/i/eightcorners.png/")
In action [here]("http://www.youtube.com/watch?v=bJxDKyd3UJs") (top and bottom = cpu0 and cpu1, left and right are upload and dowload speed).

If you want to try it, make sure the variables used in the Lua script fit your system (mines are wlan0, cpu0, cpu1 ...).
The option to choose the shape to draw is written in the conkyrc.

Well, now, if you are rash, you can try to draw your own shape. I will try to explain how with this simple example ;-)
Image :
[[IMG]http://img63.imageshack.us/img63/7338/exampleg.th.png[/IMG]]("http://img63.imageshack.us/i/exampleg.png/")
All the shapes are drawn with Bezier curves. Here is the code for the picture :
```

function theme_test()
    local xc,yc,r=100,100,20
    local points = {
    --    Px        Py,        Cx,        Cy,        Radius,        Start side
        {xc-2*r,    yc-r,    xc,    yc,    r,        1},        --top left
        {xc+100+2*r,    yc-r,    xc+100,    yc,    r,        1},        --top right
    }
    return points
end

```**Cx and Cy** are center coordinates of the circles
**Radius** are the radius of the circles
**Px and Py** are the center point of the Bezier Curve

First, the script calculate the tangeants points for each circle (0 and 1 on the picture)
"**Start side**" is the side where start the next bezier curve. It is one here
When Px,Py is above the circle, left side is always 0, right side is always 1. (And this it an absolute position, it means when Px,Py is bellow the circle, 0 is still left side but you will see it on the right because it's now upside down...)
After that, the script calculate the intersecion points of the tangeants (I1 and I2)

then the script draw curves with:
(Circle1,P0), P1 ,(Circle1,P1)
(Circle1,P1), I1 ,(Circle2,P0)
(Circle2,P0), P2 ,(Circle2,P1)
(Circle2,P1), I2 ,(Circle1,P0)

Well, it's not easy to explain, I hope you understood a little bit ! It's more an (art) script than a ready-to-use widget, and it's not very readable but it was not what I was looking for! ... If you have questions, don't hesitate ! 

It was fun to make it, I hope you like it ;)
(conkyrc and script are in the attachments)

---

### Post by mrpeachy on 2010-02-26
@wlourf

thats a nice idea.  
I wish I had the energy (or indeed the time) to learn how to apply shading effects to cairo graphics.  I think my flowers entry for the competition would benefit greatly from a bit of extra graphical flair.

--- well shading turned out to be pretty straightforward :)

---

### Post by wlourf on 2010-02-26
> **andreino said:**
> hy boys
can see the day week
this lua for language Italian?
thanks for the help
[http://forum.ubuntu.ru/index.php?topic=63273.msg638103#msg638103](http://forum.ubuntu.ru/index.php?topic=63273.msg638103#msg638103)

Thanks for asking! I'm french and I didn't managed to get dates in french till now.

Here is what I've done for having dates according to my locale settings:
It your conkyrc, in the TEXT section, write 
```
${time}
```If you want to hide this date , ```

use_xft yes
xftalpha 0
default_color 000000
```It seems it works only for the black color .

Can you check on your system if it also works and I will update the script if it's ok.
I didn't find a better way in Lua script with os.setlocale() for example...
@mrpeachy:
you made an electroencephalogram and I made a pulsing heart, that's funny !

---

### Post by HangukMiguk on 2010-02-26
> **miegiel said:**
> ```
...
TEXT

...
default color [COLOR="Blue"]${color CCCCCC}[/COLOR] color=cccccc [COLOR="Blue"]${color}[/COLOR] default color
...
```

Should work just as well. But you're right don't use a **[COLOR="Blue"]#[/COLOR]** in the hex color code.

took the pound sign out, still not working.  still showing up as black.

---

### Post by degan on 2010-02-27
Hi boys....

How do I do to remove the shade that I have in the conky?


[[IMG]http://upload.centerzone.it/images/48821683483617706559_thumb.jpg[/IMG]](http://upload.centerzone.it/viewer.php?file=48821683483617706559.png)

```
--[[
&#1055;&#1088;&#1080; &#1089;&#1073;&#1086;&#1088;&#1082;&#1077; &#1089;&#1082;&#1088;&#1080;&#1087;&#1090;&#1072; &#1080;&#1089;&#1087;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1085;&#1099; &#1076;&#1072;&#1085;&#1085;&#1099;&#1077; &#1080;&#1079; &#1089;&#1083;&#1077;&#1076;&#1091;&#1102;&#1097;&#1080;&#1093; &#1089;&#1082;&#1088;&#1080;&#1087;&#1090;&#1086;&#1074;

Conky Widgets by londonali1010 (2009) - &#1095;&#1072;&#1089;&#1099; &#1080; &#1082;&#1086;&#1083;&#1100;&#1094;&#1072;
Conky vertical bar graph by iggykoopa - &#1075;&#1086;&#1088;&#1080;&#1079;&#1086;&#1085;&#1090;&#1072;&#1083;&#1100;&#1085;&#1099;&#1081; &#1080; &#1074;&#1077;&#1088;&#1090;&#1080;&#1082;&#1072;&#1083;&#1100;&#1085;&#1099;&#1081; &#1073;&#1072;&#1088;&#1099;
Shadowed clock by wlourf (10 jan. 2010) - &#1089;&#1090;&#1088;&#1077;&#1083;&#1082;&#1080; &#1095;&#1072;&#1089;&#1086;&#1074; &#1089; &#1090;&#1077;&#1085;&#1100;&#1102;
calendar wheel by Wlourf (14 jan. 2010) - &#1082;&#1072;&#1083;&#1077;&#1085;&#1076;&#1072;&#1088;&#1100;

&#1057;&#1086;&#1073;&#1088;&#1072;&#1083; &#1074;&#1089;&#1077; &#1101;&#1090;&#1086; &#1041;&#1086;&#1088;&#1080;&#1089; &#1050;&#1088;&#1080;&#1085;&#1082;&#1077;&#1083;&#1100; <olgmen> krinkel@rambler.ru

&#1044;&#1083;&#1103; &#1101;&#1090;&#1086;&#1075;&#1086; &#1089;&#1077;&#1088;&#1080;&#1087;&#1090;&#1072; &#1090;&#1088;&#1077;&#1073;&#1091;&#1077;&#1090;&#1089;&#1103; CONKY &#1074;&#1077;&#1088;&#1089;&#1080;&#1080; 1.7.2

&#1044;&#1083;&#1103; &#1074;&#1099;&#1079;&#1086;&#1074;&#1072; &#1101;&#1090;&#1086;&#1075;&#1086; &#1089;&#1082;&#1088;&#1080;&#1087;&#1090;&#1072; &#1074; Conky &#1074;&#1089;&#1090;&#1072;&#1074;&#1100;&#1090;&#1077; &#1089;&#1083;&#1077;&#1076;&#1091;&#1102;&#1097;&#1080;&#1077; &#1089;&#1090;&#1088;&#1086;&#1082;&#1080; &#1076;&#1086; TEXT (&#1087;&#1088;&#1080; &#1091;&#1089;&#1083;&#1086;&#1074;&#1080;&#1080;, &#1095;&#1090;&#1086; &#1089;&#1082;&#1088;&#1080;&#1087;&#1090; &#1089;&#1086;&#1093;&#1088;&#1072;&#1085;&#1077;&#1085; &#1074; ~/scripts/conky_widgets.lua):
    lua_load ~/scripts/widgets.lua
    lua_draw_hook_pre widgets
]]

require 'cairo'
require 'imlib2'

--[[ AIR CLOCK WIDGET ]]
--[[ &#1042;&#1080;&#1076;&#1078;&#1077;&#1090; &#1074;&#1099;&#1074;&#1086;&#1076;&#1080;&#1090; &#1080;&#1079;&#1086;&#1073;&#1088;&#1072;&#1078;&#1077;&#1085;&#1080;&#1077; &#1095;&#1072;&#1089;&#1086;&#1074; &#1089; &#1086;&#1073;&#1098;&#1077;&#1084;&#1085;&#1099;&#1084;&#1080; &#1089;&#1090;&#1088;&#1077;&#1083;&#1082;&#1072;&#1084;&#1080; &#1080; &#1090;&#1077;&#1085;&#1100;&#1102; &#1086;&#1090; &#1089;&#1090;&#1088;&#1077;&#1083;&#1086;&#1082;.
	&#1063;&#1072;&#1089;&#1090;&#1100; &#1085;&#1072;&#1089;&#1090;&#1088;&#1086;&#1077;&#1082; &#1085;&#1072;&#1093;&#1086;&#1076;&#1080;&#1090;&#1089;&#1103; &#1074; &#1074;&#1080;&#1076;&#1078;&#1077;&#1090;&#1077;
]]

function clock(cr, x, y, s, bgc, bga, fgc, fga)

-- &#1092;&#1091;&#1085;&#1082;&#1094;&#1080;&#1103; &#1087;&#1077;&#1088;&#1077;&#1082;&#1086;&#1076;&#1080;&#1088;&#1086;&#1074;&#1082;&#1080; &#1094;&#1074;&#1077;&#1090;&#1072;

	function rgb_to_r_g_b(colour,alpha)
		return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
	end

-- &#1085;&#1072;&#1079;&#1085;&#1072;&#1095;&#1072;&#1077;&#1084; &#1090;&#1086;&#1083;&#1097;&#1080;&#1085;&#1091; &#1074;&#1099;&#1074;&#1086;&#1076;&#1080;&#1084;&#1099;&#1093; &#1083;&#1080;&#1085;&#1080;&#1081;

		local s_th = 2

-- &#1088;&#1080;&#1089;&#1091;&#1077;&#1084; &#1094;&#1080;&#1092;&#1077;&#1088;&#1073;&#1083;&#1072;&#1090;

		local radius = s/2	
		local m_x,m_y = x + s/2, y + s/2
		cairo_set_line_width(cr,6)
		cairo_arc(cr, m_x,m_y, radius, 0, math.rad(360))
		cairo_set_source_rgba(cr,rgb_to_r_g_b(fgc,fga))
		cairo_stroke(cr)

-- &#1087;&#1088;&#1086;&#1079;&#1088;&#1072;&#1095;&#1085;&#1099;&#1081; "&#1082;&#1086;&#1088;&#1087;&#1091;&#1089; &#1095;&#1072;&#1089;&#1086;&#1074;"
	
		cairo_arc(cr, m_x, m_y, radius*1.25, 0, 2*math.pi)
		cairo_set_source_rgba(cr, 0.5, 0.5, 0.5, 0.8)
		cairo_set_line_width(cr,1)
		cairo_stroke(cr)
	
		local border_pat=cairo_pattern_create_linear(m_x, m_y - radius*1.25, m_x, m_y + radius*1.25)
	
		cairo_pattern_add_color_stop_rgba(border_pat,0,0,0,0,0.7)
		cairo_pattern_add_color_stop_rgba(border_pat,0.3,1,1,1,0)
		cairo_pattern_add_color_stop_rgba(border_pat,0.5,1,1,1,0)
		cairo_pattern_add_color_stop_rgba(border_pat,0.7,1,1,1,0)
		cairo_pattern_add_color_stop_rgba(border_pat,1,0,0,0,0.7)
		cairo_set_source(cr,border_pat)
		cairo_arc(cr, m_x, m_y, radius*1.125, 0, 2*math.pi)
		cairo_close_path(cr)
		cairo_set_line_width(cr, radius*0.25)
		cairo_stroke(cr)

-- &#1074;&#1099;&#1074;&#1086;&#1076; &#1095;&#1072;&#1089;&#1086;&#1074;&#1099;&#1093; &#1076;&#1077;&#1083;&#1077;&#1085;&#1080;&#1081;

		local i = 0
		local winkel = math.rad(30)		
		
		for i=0,11,1 do
		cairo_set_line_width(cr,s_th*1.5)
		cairo_move_to(cr, m_x-math.sin(winkel*i)*radius, m_y-math.cos(winkel*i)*radius)
		cairo_line_to(cr, m_x-math.sin(winkel*i)*(radius*0.9), m_y-math.cos(winkel*i)*(radius*0.9))
		cairo_fill_preserve(cr)
		cairo_set_source_rgba(cr,rgb_to_r_g_b(fgc,fga))
		cairo_stroke(cr)
		end

-- &#1074;&#1099;&#1074;&#1086;&#1076; &#1084;&#1080;&#1085;&#1091;&#1090;&#1085;&#1099;&#1093; &#1076;&#1077;&#1083;&#1077;&#1085;&#1080;&#1081;

		local i = 0
		local winkel = math.rad(6)

		for i=0,59,1 do
		cairo_set_line_width(cr,1)
		cairo_move_to(cr, m_x-math.sin(winkel*i)*radius, m_y-math.cos(winkel*i)*radius)
		cairo_line_to(cr, m_x-math.sin(winkel*i)*(radius*0.9), m_y-math.cos(winkel*i)*(radius*0.9))
		cairo_stroke(cr)
		end

-- &#1088;&#1080;&#1089;&#1091;&#1077;&#1084; &#1076;&#1077;&#1083;&#1077;&#1085;&#1080;&#1103; 3, 6, 9 &#1080; 12 &#1095;&#1072;&#1089;&#1086;&#1074;&#1099;&#1077;

		cairo_set_line_width(cr,s_th/2)		-- &#1091;&#1089;&#1090;&#1072;&#1085;&#1072;&#1074;&#1083;&#1080;&#1074;&#1072;&#1077;&#1084; &#1090;&#1086;&#1083;&#1097;&#1080;&#1085;&#1091; &#1083;&#1080;&#1085;&#1080;&#1081;

		cairo_move_to (cr, x + 0.15*s, y + 0.5*s)
		cairo_line_to (cr, x + 0.45*s, y + 0.5*s)
		cairo_move_to (cr, x + 0.55*s, y + 0.5*s)
		cairo_line_to (cr, x + 0.85*s, y + 0.5*s)
		cairo_move_to (cr, x + 0.5*s, y + 0.15*s)
		cairo_line_to (cr, x + 0.5*s, y + 0.45*s)
		cairo_move_to (cr, x + 0.5*s, y + 0.55*s)
		cairo_line_to (cr, x + 0.5*s, y + 0.85*s)
		cairo_stroke(cr)

-- &#1095;&#1072;&#1089;&#1086;&#1074;&#1099;&#1077; &#1089;&#1090;&#1088;&#1077;&#1083;&#1082;&#1080; &#1089; &#1090;&#1077;&#1085;&#1100;&#1102;, &#1074;&#1079;&#1103;&#1090;&#1086; &#1080;&#1079; Shadowed clock by wlourf (10 jan. 2010)

		function draw_hand(a_trame,arc,arc0,arc1,lg,r,border,rgb)
		xx = xc + clock_r*math.sin(arc)*lg
		yy = yc - clock_r*math.cos(arc)*lg
		x0 = xc + r*math.sin(arc0)
		y0 = yc - r*math.cos(arc0)
		x1 = xc + r*math.sin(arc1)
		y1 = yc - r*math.cos(arc1)

		if border ~= nil then
		cairo_set_line_width(cr,1)
		cairo_set_source_rgba(cr,border[1],border[2],border[3],0.5)
		cairo_move_to (cr, x0, y0)
		cairo_curve_to (cr, x0, y0, xx, yy, x1, y1)
		cairo_arc(cr,xc,yc,r,arc1-math.pi/2,arc0-math.pi/2)
		cairo_stroke(cr)
		end

-- &#1088;&#1080;&#1089;&#1091;&#1077;&#1084; &#1090;&#1077;&#1085;&#1100;

		cairo_move_to (cr, x0, y0)
		cairo_curve_to (cr, x0, y0, xx+shadow_xoffset, yy+shadow_yoffset, x1, y1)
		cairo_arc(cr,xc,yc,r,arc1-math.pi/2,arc0-math.pi/2)
		pat = cairo_pattern_create_radial (xc, yc, 0, xc, yc, clock_r)
		cairo_pattern_add_color_stop_rgba (pat, 0, 0, 0, 0, shadow_opacity)
		cairo_pattern_add_color_stop_rgba (pat, 1, 0, 0, 0, 0)
		cairo_set_source (cr, pat)
		cairo_fill (cr)

-- &#1088;&#1080;&#1089;&#1091;&#1077;&#1084; &#1089;&#1090;&#1088;&#1077;&#1083;&#1082;&#1080;

		cairo_move_to (cr, x0, y0)
		cairo_curve_to (cr, x0, y0, xx, yy, x1, y1)
		cairo_arc(cr,xc,yc,r,arc1-math.pi/2,arc0-math.pi/2)
		pat = cairo_pattern_create_radial (xc, yc, clock_r/10, xc, yc, clock_r*lg)
		cairo_pattern_add_color_stop_rgba (pat,0, rgb[1], rgb[2], rgb[3], 1)
		cairo_pattern_add_color_stop_rgba (pat, 1, 0, 0, 0, 1)
		cairo_set_source (cr, pat)
		cairo_fill (cr)
		cairo_pattern_destroy (pat)
		end

-- &#1047;&#1076;&#1077;&#1089;&#1100; &#1074;&#1074;&#1086;&#1076;&#1103;&#1090;&#1089;&#1103; &#1086;&#1089;&#1085;&#1086;&#1074;&#1085;&#1099;&#1077; &#1076;&#1072;&#1085;&#1085;&#1099;&#1077;

-- &#1088;&#1072;&#1076;&#1080;&#1091;&#1089; &#1095;&#1072;&#1089;&#1086;&#1074; &#1074; &#1087;&#1080;&#1082;&#1089;&#1077;&#1083;&#1103;&#1093;, &#1079;&#1072;&#1076;&#1072;&#1077;&#1084; &#1087;&#1086;&#1083;&#1086;&#1074;&#1080;&#1085;&#1091; &#1076;&#1080;&#1072;&#1084;&#1077;&#1090;&#1088;&#1072; &#1095;&#1072;&#1089;&#1086;&#1074;

		clock_r=s/2

-- &#1082;&#1086;&#1086;&#1088;&#1076;&#1080;&#1085;&#1072;&#1090;&#1099; &#1094;&#1077;&#1085;&#1090;&#1088;&#1072; &#1095;&#1072;&#1089;&#1086;&#1074;

		xc = x+s/2
		yc = y+s/2

-- &#1082;&#1086;&#1086;&#1088;&#1076;&#1080;&#1085;&#1072;&#1090;&#1099; &#1080;&#1089;&#1090;&#1086;&#1095;&#1085;&#1080;&#1082;&#1072; &#1089;&#1074;&#1077;&#1090;&#1072; &#1086;&#1090;&#1085;&#1086;&#1089;&#1080;&#1090;&#1077;&#1083;&#1100;&#1085;&#1086; &#1094;&#1077;&#1085;&#1090;&#1088;&#1072; &#1095;&#1072;&#1089;&#1086;&#1074;, 0 - &#1080;&#1089;&#1090;&#1086;&#1095;&#1085;&#1080;&#1082; &#1089;&#1074;&#1077;&#1090;&#1072; &#1085;&#1072;&#1076; &#1094;&#1077;&#1085;&#1090;&#1088;&#1086;&#1084;
-- &#1084;&#1086;&#1078;&#1077;&#1090; &#1073;&#1099;&#1090;&#1100; &#1087;&#1086;&#1083;&#1086;&#1078;&#1080;&#1090;&#1077;&#1083;&#1100;&#1085;&#1099;&#1084;, &#1080;&#1089;&#1090;&#1086;&#1095;&#1085;&#1080;&#1082; &#1089;&#1074;&#1077;&#1090;&#1072; &#1074;&#1099;&#1096;&#1077; &#1094;&#1077;&#1085;&#1090;&#1088;&#1072;, &#1080;&#1083;&#1080; &#1086;&#1090;&#1088;&#1080;&#1094;&#1072;&#1090;&#1077;&#1083;&#1100;&#1085;&#1099;&#1084;

		shadow_xoffset=70
		shadow_yoffset=70

-- &#1087;&#1088;&#1086;&#1079;&#1088;&#1072;&#1095;&#1085;&#1086;&#1089;&#1090;&#1100; &#1090;&#1077;&#1085;&#1080;, &#1079;&#1085;&#1072;&#1095;&#1077;&#1085;&#1080;&#1103; &#1086;&#1090; 0 &#1076;&#1086; 1

		shadow_opacity=0.5

-- &#1042;&#1099;&#1074;&#1086;&#1076;&#1080;&#1090;&#1100; &#1089;&#1077;&#1082;&#1091;&#1085;&#1076;&#1085;&#1091;&#1102; &#1089;&#1090;&#1088;&#1077;&#1083;&#1082;&#1091;, &#1044;&#1072; - true, &#1053;&#1077;&#1090; - false.
-- &#1055;&#1088;&#1080; &#1074;&#1099;&#1074;&#1086;&#1076;&#1077; &#1089;&#1077;&#1082;&#1091;&#1085;&#1076;&#1085;&#1086;&#1081; &#1089;&#1090;&#1088;&#1077;&#1083;&#1082;&#1080; update_interval &#1074; .conkyrc &#1076;&#1086;&#1083;&#1078;&#1077;&#1085; &#1073;&#1099;&#1090;&#1100; &#1084;&#1077;&#1085;&#1077;&#1077; 1 &#1089;&#1077;&#1082;.

		show_seconds=true

-- &#1042;&#1099;&#1074;&#1086;&#1076;&#1080;&#1090;&#1100; &#1086;&#1089;&#1100; &#1089;&#1090;&#1088;&#1077;&#1083;&#1086;&#1082; &#1074; &#1094;&#1077;&#1085;&#1090;&#1088;&#1077; &#1095;&#1072;&#1089;&#1086;&#1074;, &#1044;&#1072; - true, &#1053;&#1077;&#1090; - false.

		show_dot = true

-- &#1088;&#1072;&#1079;&#1084;&#1077;&#1088;&#1099; &#1089;&#1090;&#1088;&#1077;&#1083;&#1086;&#1082;, &#1087;&#1077;&#1088;&#1074;&#1072;&#1103; &#1094;&#1080;&#1092;&#1088;&#1072; &#1096;&#1080;&#1088;&#1080;&#1085;&#1072;, &#1074;&#1090;&#1086;&#1088;&#1072;&#1103; - &#1076;&#1083;&#1080;&#1085;&#1072;

		rh,lgh=3,1.2	-- &#1095;&#1072;&#1089;&#1086;&#1074;&#1072;&#1103; &#1089;&#1090;&#1088;&#1077;&#1083;&#1082;&#1072;
		rm,lgm=2,1.75	-- &#1084;&#1080;&#1085;&#1091;&#1090;&#1085;&#1072;&#1103; &#1089;&#1090;&#1088;&#1077;&#1083;&#1082;&#1072;
		rs,lgs=1,1.9	-- &#1089;&#1077;&#1082;&#1091;&#1085;&#1076;&#1085;&#1072;&#1103; &#1089;&#1090;&#1088;&#1077;&#1083;&#1082;&#1072;

-- &#1079;&#1072;&#1073;&#1080;&#1088;&#1072;&#1077;&#1084; &#1076;&#1072;&#1085;&#1085;&#1099;&#1077; &#1080;&#1079; &#1054;&#1057;

		local hours=os.date("%I")
		local mins=os.date("%M")
		local secs=os.date("%S")

-- &#1088;&#1072;&#1089;&#1095;&#1077;&#1090; &#1091;&#1075;&#1083;&#1072; &#1076;&#1074;&#1080;&#1078;&#1077;&#1085;&#1080;&#1103; &#1089;&#1090;&#1088;&#1077;&#1083;&#1086;&#1082;

		gamma = math.pi/2-math.atan(rs/(clock_r*lgs))
		secs_arc=(2*math.pi/60)*secs
		secs_arc0=secs_arc-gamma
		secs_arc1=secs_arc+gamma

		gamma = math.pi/2-math.atan(rm/(clock_r*lgm))
		mins_arc=(2*math.pi/60)*mins + secs_arc/60
		mins_arc0=mins_arc-gamma
		mins_arc1=mins_arc+gamma

		gamma = math.pi/2-math.atan(rh/(clock_r*lgh))
		hours_arc=(2*math.pi/12)*hours+mins_arc/12
		hours_arc0=hours_arc-gamma
		hours_arc1=hours_arc+gamma

-- &#1074;&#1099;&#1074;&#1086;&#1076; &#1089;&#1090;&#1088;&#1077;&#1083;&#1086;&#1082;

		draw_hand(alpha_trame,hours_arc,hours_arc0,hours_arc1,lgh,rh,{0,0,0},{1,1,1})
		draw_hand(alpha_trame,mins_arc,mins_arc0,mins_arc1,lgm,rm,{0,0,0},{.9,.9,.9})
		if show_seconds then
		draw_hand(alpha_trame,secs_arc,secs_arc0,secs_arc1,lgs,rs,{0,0,0},{.8,.8,.8})
		end

-- &#1088;&#1080;&#1089;&#1091;&#1077;&#1084; &#1086;&#1089;&#1100; &#1089;&#1090;&#1088;&#1077;&#1083;&#1086;&#1082;

		if show_dot then

		lg_shadow_center=3
		radius=math.min(rh,rm,rs)*0.75
		if radius<1 then radius=1 end
		ang = math.atan(shadow_yoffset/shadow_xoffset)

-- &#1090;&#1077;&#1085;&#1100; &#1086;&#1090; &#1086;&#1089;&#1080;

		gamma = -math.atan(1/lg_shadow_center)
		ang0=ang-gamma
		ang1=ang+gamma

-- &#1090;&#1077;&#1085;&#1100; &#1086;&#1090; &#1089;&#1090;&#1088;&#1077;&#1083;&#1086;&#1082;

		if shadow_xoffset<0 and shadow_yoffset>0 then
		ang0=ang0+math.pi
		ang1=ang1+math.pi
		ang=ang+math.pi
		end

		if shadow_yoffset<0 and shadow_xoffset>0 then
		ang0=ang0-math.pi/2
		ang1=ang1-math.pi/2
		ang=ang-math.pi/2
		end

		if shadow_yoffset<0 and shadow_xoffset<0 then
		ang0=ang0-math.pi/2
		ang1=ang1-math.pi/2
		ang=ang-math.pi/2
		end

		x0 = xc + radius*math.sin(ang0)
		y0 = yc - radius*math.cos(ang0)
		xx = xc + radius*math.sin(ang+math.pi/2)*lg_shadow_center
		yy = yc - radius*math.cos(ang+math.pi/2)*lg_shadow_center
		x1 = xc - radius*math.sin(ang1)
		y1 = yc + radius*math.cos(ang1)

		cairo_move_to(cr,x0,y0)
		cairo_curve_to(cr,x0,y0,xx,yy,x1,y1)
		pat = cairo_pattern_create_radial (xc, yc, 0, xc, yc, radius*4)
		cairo_pattern_add_color_stop_rgba (pat, 0, 0, 0,0, shadow_opacity)
		cairo_pattern_add_color_stop_rgba (pat, 1, 0,0,0, 0)
		cairo_set_source (cr, pat)
		cairo_fill (cr)

		ang = ang-math.pi/2
		xshad = xc + radius*math.sin(ang)*.5
		yshad = yc - radius*math.cos(ang)*.5

		local ds_pat=cairo_pattern_create_radial(xc, yc, 0, xshad, yshad, radius)
		cairo_pattern_add_color_stop_rgba(ds_pat,0,.9,.9,.9,1)
		cairo_pattern_add_color_stop_rgba(ds_pat,1,0,0,0,1)
		cairo_arc(cr,xc,yc,radius,0,2*math.pi)
		cairo_set_source(cr,ds_pat)
		cairo_fill(cr)

-- &#1088;&#1080;&#1089;&#1091;&#1077;&#1084; &#1075;&#1083;&#1103;&#1085;&#1077;&#1094; &#1085;&#1072; &#1089;&#1090;&#1077;&#1082;&#1083;&#1077;

		pat = cairo_pattern_create_radial (115.2, 102.4, 25.6, 102.4, 102.4, 128)
		cairo_pattern_add_color_stop_rgba (pat, 0, 1, 1, 1, 0.1)
		cairo_pattern_add_color_stop_rgba (pat, 1, 0, 0, 0, 0.4)
		cairo_set_source (cr, pat)
		cairo_arc (cr, xc, yc, s/2, 0, 2 * math.pi)
		cairo_fill (cr)
		cairo_pattern_destroy (pat)
end

--[[ END AIR CLOCK WIDGET ]]

-- ----------------------------------------------------------------------------------

--[[
calendar wheel by Wlourf (14 jan. 2010)

This script is designed to draw dates on a circular way on the left of the screen.
Some text info can be added in the circle with the file calendar.txt (see below)
Some parameters (colors, sizes ... ) can be adjusted (see below).

As this script draw a png file only if necessary, a short update of the conky can be used.

Call this script in Conky using the following before TEXT (assuming you save this script to ~/scripts/calendar.lua):
	lua_load ~/scripts/calendar.lua
	lua_draw_hook_pre main
	
	
v1.0 - 14 jan. 2010 - Original release
v1.1 - 19 jan. 2010 - Calendar are now drawn in an PNG file and this file 
	is called at every conky call, when day change, a new PNG file is created.
	- An x offset can be added to "Today's block"
	- An y offset can be added too to "Today's block"
v1.2 - 28 jan. 2010 - Calendar can be drawn on the right side of the conky (but without text info)
	- Calendar is drawn after the second conky refresh only
v1.2a - 29 jan. 2010 - Minor update, picture was refresh every second instead of every day!
]]

--require 'cairo'
--require 'imlib2'

-------------------------- parameters (part one) are set here -----------------------------------

	--text file calendar (absolute path, can be "" if no file used)
	calendar_file="/home/boris/scripts/calendar.txt"
	--format of in this text file
	--MMDD;N;TEXT
	--MMDD = month day
	--N    = 0 or 1 (1 to display same colors as week-ends)
	--TEXT = Text to display (use * for multiline)

	--some paths to images created (absolutes paths)
	image_tmp="/tmp/img_tmp.png" --used to rotate a single date
	image_calendar="/tmp/conky-calendar-arc.png"
	image_dates="/tmp/conky-calendar-dates.png"

	--more parameters below
-------------------------- end of parameters (part one) -----------------------------------	


function string:split(delimiter)
--source for the split function : http://www.wellho.net/resources/ex.php4?item=u108/split
  local result = { }
  local from  = 1
  local delim_from, delim_to = string.find( self, delimiter, from  )
  while delim_from do
    table.insert( result, string.sub( self, from , delim_from-1 ) )
    from  = delim_to + 1
    delim_from, delim_to = string.find( self, delimiter, from  )
  end
  table.insert( result, string.sub( self, from  ) )
  return result
end



function conky_draw_calendar()
--	if conky_window==nil then return end
	local width=conky_window.width
	local height=conky_window.height
--local height = s
--local width = s	
	--sometimes, there is problem with init and width & height are set to 0 or 2 !!
--	if width<3 or height<3 then return end
	
local cs=cairo_image_surface_create(CAIRO_FORMAT_ARGB32, width, height)
	local cr=cairo_create(cs)
	
	-------------------------- parameters (part two) are set here -----------------------------------

	
	-- vertical center of the circle (height/2 for centered circle)
	local yc=s/2+y
	
	--number of days to display before and after today (i.e. with range = 30 --> 60 days are displayed)
	--even number between 20 and 30 for nice effect
	local range = 11
	
	--not sure of the engish words so I leave then in french !	
	--fleche (arrow) is the segment from x=0 to x=radius-xc (with xc =center of the circle) 
	--fleche for the external circle
	--fleche2 for the internal circle
	--fleche2 must be < fleche
	local fleche=125
	local fleche2=fleche*.85
	
	--corde (chord) is the vertical segment (where x=0) of the external circle
	local corde = 1.5*s--height+s/2
			
	--colors RGB (0-255)
	--week day
	local wday={150,150,150}
	--week-end and bank holidays defined in calendar.txt
	local eday={255,200,0}
	--color of today
	local dday={255,255,255}
	
	--vertical gradient (both circle and dates)? (true/false)
	local vgradient=true
	
	--horizontal gradient for the circle? (0 to 1, 0 is the best choice for "moon like" circle )
	local hgradient=0
	
	--you can change the font here
	local font="PT Sans"
	--font_size (of dates) must be less than delta (= heigth of a day)
	local delta = yc/(range+0.5)
	--the font-size has to be adjusted depending on the font used
	local font_size=delta-1
	
	--information text (from calendar.txt)
	local info_color={255,200,0}
	--font size of text infos
	local font_size_info=font_size

	--today_xoffset is the offset for the date of today (can be positive/null/negative, in pixels)
	local today_xoffset=5
	
	--today_yoffset where today will be displayed (value between -range to + range)?
	-- 0 = center of the arc
	-- -range =  top of the arc
	-- +range = bottom of the arc
	local today_yoffset=0	-- -9
	
	--display on right side of the screen (true/false)
	local align_right = true

	
	-------------------------- end of the parameters, ouf -----------------------------------

	--some calculations
	--radius for external circle
	--radius2 for internal circle
	--delta = number of arcs in the circle
	local radius=(corde^2+4*fleche^2)/(8*fleche)
	local radius2=(corde^2+4*fleche2^2)/(8*fleche2)
 	local decal=2*(delta-font_size)
	wday[1]=wday[1]/255
	wday[2]=wday[2]/255
	wday[3]=wday[3]/255	
	eday[1]=eday[1]/255
	eday[2]=eday[2]/255
	eday[3]=eday[3]/255	

	--xc =x center of external circle
	--xc2=x center of internal circle
	local xc = fleche - radius	
	local xc2 = fleche2 - radius2
	
	if align_right then 
		xc = width-xc-1.5*s/2
		xc2 = width-xc2-1.5*s/2
	end

	local h_txt = height/(2*range+1)
	
	local t = os.date('*t') -- date in table
	--get the date
	local s = os.time(t) -- date in seconds

	--read the calendar file
	local file = io.open(calendar_file,"r")	
	local tabcal={}	
	local idx=1
	local line,lineok="",""
	if file ~= nil then
		while true do
		 	line = file:read("*l")
		    if line == nil then break end
			lineok = string.split(line,";")
			if (#lineok)==3 then
				tabcal[idx]={lineok[1],lineok[2],lineok[3]}
				idx=idx+1
			end
		end
	end	
	io.close()
	local angmini=math.atan((corde/2)/(radius-fleche))

	local imageDates=imlib_create_image(width,height)
	imlib_context_set_image(imageDates)
	imlib_image_set_has_alpha(1)
	imlib_save_image(image_dates)

	for i=-range,range do
		local s2 = s + 3600*24*(i-today_yoffset) --date diff in seconds

		local wd = os.date("%w",s2)
		local md = os.date("%m%d",s2)
		local dt = os.date("%a. %d %b.",s2),os.date("%d",s2),os.date("%b",s2)

		--percentage of vertical gradient
		local pc = (range-math.abs(i))/range
		if not vgradient then pc=1 end

		--angle min et max of one block
		local ang0 = angmini*(i-0.5)/range
		local ang1 = angmini*(i+0.5)/range
		if align_right then 
			ang0=math.pi-ang0
			ang1=math.pi-ang1
		end
		local angm = (ang0+ang1)/2
		
		--read the calendar.txt array
		local flag = false
		for idy=1,idx-1 do
			if tabcal[idy][1] == md then
				if (i-today_yoffset) == 0 then
					today = tabcal[idy]
				end
				if tabcal[idy][2] == "1" then
					flag = true
				end
				break
			end
		end

		--colors
		local colR,colG,colB=0,0,0
		if wd=="6" or wd=="0" or flag == true then
			colR,colG,colB=eday[1],eday[2],eday[3]
		else
			colR,colG,colB=wday[1],wday[2],wday[3]
		end
		
		--offset of today 
		local offset_x=0
		local way = 1
		if (i-today_yoffset)==0 then 
			if align_right then way =-1 end
			offset_x=today_xoffset*way 
		end

		local pat = cairo_pattern_create_radial (xc+offset_x, yc, radius,
         			xc2+offset_x,yc,radius2);
		
		cairo_pattern_add_color_stop_rgba (pat, 0, colR, colG, colB, pc);
		cairo_pattern_add_color_stop_rgba (pat, 1, colR, colG, colB, hgradient);
		
		cairo_set_source (cr, pat);
		--draw the portion of arc
		if align_right then
			x1,y1=radius*math.cos(ang0)+xc+offset_x,(radius-offset_x)*math.sin(ang0)+yc
			x2,y2=radius*math.cos(ang1)+xc+offset_x,(radius-offset_x)*math.sin(ang1)+yc
		else
			x1,y1=radius*math.cos(ang0)+xc+offset_x,(radius+offset_x)*math.sin(ang0)+yc
			x2,y2=radius*math.cos(ang1)+xc+offset_x,(radius+offset_x)*math.sin(ang1)+yc
		end
		cairo_move_to(cr,x1,y1)
		cairo_line_to(cr,x2,y2)
		cairo_line_to(cr,xc,yc)
		cairo_fill(cr)
		
		--for tests
		if (i-today_yoffset)==0 then

		end

		--write text info if needed, for left-side calendar only
		local have=""
local height = 20 -- &#1088;&#1072;&#1089;&#1087;&#1086;&#1083;&#1086;&#1078;&#1077;&#1085;&#1080;&#1077; &#1090;&#1077;&#1082;&#1089;&#1090;&#1072; &#1080;&#1079; calendar.txt &#1087;&#1086; &#1074;&#1077;&#1088;&#1090;&#1080;&#1082;&#1072;&#1083;&#1080;

if today ~= nil then
--		if (today ~= nil) and (align_right ~= true) then
			cairo_select_font_face(cr, font, CAIRO_FONT_SLANT_NORMAL, CAIRO_FONT_WEIGHT_NORMAL)
			cairo_set_line_width(cr,0)
			cairo_set_font_size(cr,font_size_info)
			cairo_set_source_rgba (cr, info_color[1]/255, info_color[2]/255, info_color[3]/255,1);

			have = string.split(today[3],"*")
			for i=1,#have do 
				cairo_move_to(cr,10,height+(i-#have/2)*font_size_info)
				cairo_show_text(cr, have[i])
				cairo_fill(cr)
			end
		end	

		--lenght of the arc
		local dx,dy=math.abs(x2-x1),math.abs(y2-y1)
		local h_txt=math.sqrt(dx*dx+dy*dy)
		local w_txt=font_size*10

		--write text in another image for working (rotate) on it
		--didn't find to work in memory only
		local cs2=cairo_image_surface_create(CAIRO_FORMAT_ARGB32, w_txt, h_txt)
		local cr2=cairo_create(cs2)
		cairo_set_font_size (cr2, font_size);
		if (i-today_yoffset)==0 then 
			colR, colG, colB = dday[1]/255,dday[2]/255,dday[3]/255
			pc=1
		end
		cairo_select_font_face(cr2, font, CAIRO_FONT_SLANT_NORMAL, CAIRO_FONT_WEIGHT_NORMAL)

		--write ONE date in ONE picture		
		local txt_date = " " .. dt .. " "
		--start the drawing date here in order to get the lenght of the text
		--for right alignement
		cairo_move_to(cr2,0,h_txt-decal)--+offset_x*math.atan(ang0))
		cairo_set_source_rgba (cr2, colR, colG, colB,pc)
		cairo_show_text(cr2, txt_date)

		if align_right then
			local xmax,ymax=cairo_get_current_point(cr2,0,0)
			--don't use local for cs2fit cause local will be just for if .. end section
			--and then surface will not be deleted --> memory leak
			cs2fit = cairo_image_surface_create(CAIRO_FORMAT_ARGB32, xmax, h_txt)
			cr2fit = cairo_create(cs2fit)
			

			cairo_set_font_size (cr2fit, font_size);
			cairo_select_font_face(cr2fit, font, CAIRO_FONT_SLANT_NORMAL, CAIRO_FONT_WEIGHT_NORMAL)
			cairo_move_to(cr2fit,0,h_txt -decal)
			cairo_set_source_rgba (cr2fit, colR, colG, colB,pc)
			cairo_show_text(cr2fit, txt_date)

			cairo_stroke(cr2fit)
			cairo_surface_write_to_png(cs2fit,image_tmp)
			
		else
			cairo_stroke(cr2)
			cairo_surface_write_to_png(cs2,image_tmp)
		end
	
		--blend date image on cairo surface
		local imageTmp = imlib_load_image(image_tmp)
		imlib_context_set_image(imageTmp)

		if align_right then
			rot_img = imlib_create_rotated_image(angm+math.pi)
		else
			rot_img = imlib_create_rotated_image(angm)
		end

		imlib_context_set_image(imageTmp)
		imlib_free_image()
	
		--image is now a  square
		imlib_context_set_image(rot_img)
		local w_img0, h_img0 = imlib_image_get_width(), imlib_image_get_height()
		
		---look for center of text
		local rt=radius+w_img0/2
		if align_right then	
			rt=rt-offset_x
		else
			rt=rt+offset_x
		end
		local xt=rt*math.cos(angm)+xc-w_img0/2
		local yt=rt*math.sin(angm)+yc-h_img0/2

		imlib_context_set_image(imageDates)
		imlib_blend_image_onto_image(rot_img, 1, 0, 0, w_img0, h_img0, xt,yt, w_img0, h_img0)
		imageDates=imlib_context_get_image()
		imlib_context_set_image(rot_img)
		imlib_free_image()




		if align_right then 
			
			cairo_destroy(cr2fit)
			cairo_surface_destroy(cs2fit)
		end
	
		cairo_destroy(cr2)
		cairo_surface_destroy(cs2)

		cairo_pattern_destroy(pat)
	end --of loop

	--write to disk images with dates only
	imlib_context_set_image(imageDates)
	imlib_save_image(image_dates)	

	--write to disk image with arc only
	cairo_surface_write_to_png(cs,image_calendar)
	
	--make final image
	local imageCal = imlib_load_image(image_calendar)
	imlib_context_set_image(imageCal)
	imlib_blend_image_onto_image(imageDates, 1, 0, 0, width, height, 0,0, width, height)
	
	imlib_save_image(image_calendar)
	imlib_free_image()

	imlib_context_set_image(imageDates)
	imlib_free_image()

	--free memory
	cairo_destroy(cr)
	cairo_surface_destroy(cs)
	
end 
-- ------------------------------------------------------------------------------------------

function calendar()
	--last_date is global 
	local actual_date  = os.date("%Y%m%d") --os.date("%Y%m%d")
	local actual_cal = imlib_load_image(image_calendar)
	if (conky_parse('${updates}')+0) <2  then return end
	if  last_date ~= actual_date or actual_cal == nil then
		--print (os.date("%H%M%S"),'new picture')
		conky_draw_calendar()
		last_date = actual_date
	else
		--print (os.date("%H%M%S"),'use old picture')
	end
	if actual_cal == nil then
		actual_cal = imlib_load_image(image_calendar)
	end
	imlib_context_set_image(actual_cal)
	imlib_render_image_on_drawable(0,0)
	imlib_free_image()
	end
end
-- [[ END CALENDAR WIDGET ]]
-- -----------------------------------------------------------------------------------
--[[ PIE WIDGET ]]
--[[
Conky Cairo Lua scripting example

Copyright (c) 2009 Brenden Matthews, all rights reserved.

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

You can tweak the settings_table below to suit your preferences.  You can draw
as many pies as you want, by simply adding more entries in the settings_table.

Load this in your conkyrc like so (assuming you save this script to
~/cairo_pie.lua):

lua_load ~/scripts/cairo-pie.lua
lua_draw_hook_pre pie_time
lua_draw_hook_post cairo_cleanup

]]

settings_table = {
	{
		-- Can be one of 'top', 'top_mem', or 'top_io' (requires iostats
		-- support in Conky).  This is the top stat we're basing our pie on.
		name='top',
		-- Draw a background pie? Can be true or false.
		draw_bg=true,
		-- Background pie colour, RGB value.
		bg_colour=0xffffee,
		-- Foreground pie colour, RGB value.
		fg_colour=0xffdf00,
		-- X and Y coordinates, relative to the centre of Conky, in pixels.
		x=65, y=40,
		-- Radius of our pie, in pixels.
		radius=79,
		-- Angle to rotate the pie, in degrees.
		angle=90,
		-- Reverse pie? Can be true or false.
		reverse=false,
		-- Shade each pie slice relative to the others.
		shade=true,
	},
	{
		name='top_mem',
		draw_bg=false,
		bg_colour=0x071672,
		fg_colour=0xff8700,
		x=65, y=40,
		radius=79,
		angle=90,
		reverse=true,
		shade=true,
	},
}

require 'cairo'
-- &#1092;&#1091;&#1085;&#1082;&#1094;&#1080;&#1103; &#1087;&#1077;&#1088;&#1077;&#1082;&#1086;&#1076;&#1080;&#1088;&#1086;&#1074;&#1082;&#1080; &#1094;&#1074;&#1077;&#1090;&#1072;
function rgb_to_r_g_b(colour, alpha)
	return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
end
-- &#1089;&#1073;&#1088;&#1072;&#1089;&#1099;&#1074;&#1072;&#1077;&#1084; &#1079;&#1085;&#1072;&#1095;&#1077;&#1085;&#1080;&#1103;
cs, cr = nil
--
function draw_pie(t, pt)

-- &#1077;&#1089;&#1083;&#1080; &#1085;&#1077;&#1090; &#1086;&#1082;&#1085;&#1072; &#1082;&#1086;&#1085;&#1100;&#1082;&#1086;&#1074;, &#1090;&#1086; &#1074;&#1099;&#1093;&#1086;&#1076;&#1080;&#1084; &#1080;&#1079; &#1087;&#1088;&#1086;&#1075;&#1088;&#1072;&#1084;&#1084;&#1099;
	if conky_window == nil then return end

-- &#1077;&#1089;&#1083;&#1080; cs &#1088;&#1072;&#1074;&#1085;&#1103;&#1077;&#1090;&#1089;&#1103; nil &#1080;&#1083;&#1080; cairo_xlib_surface_get_width(cs) &#1085;&#1077; &#1088;&#1072;&#1074;&#1085;&#1086; &#1096;&#1080;&#1088;&#1080;&#1085;&#1077; &#1086;&#1082;&#1085;&#1072; &#1082;&#1086;&#1085;&#1100;&#1082;&#1086;&#1074; &#1080;&#1083;&#1080; cairo_xlib_surface_get_height(cs) &#1085;&#1077; &#1088;&#1072;&#1074;&#1085;&#1086; &#1074;&#1099;&#1089;&#1086;&#1090;&#1077; &#1086;&#1082;&#1085;&#1072; &#1082;&#1086;&#1085;&#1100;&#1082;&#1086;&#1074; &#1090;&#1086;&#1075;&#1076;&#1072;
	if cs == nil or cairo_xlib_surface_get_width(cs) ~= conky_window.width or cairo_xlib_surface_get_height(cs) ~= conky_window.height then
-- &#1077;&#1089;&#1083;&#1080; cs &#1089;&#1091;&#1097;&#1077;&#1089;&#1090;&#1074;&#1091;&#1077;&#1090;, &#1090;&#1086; &#1089;&#1073;&#1088;&#1072;&#1089;&#1099;&#1074;&#1072;&#1077;&#1084; cs &#1080; &#1074;&#1099;&#1093;&#1086;&#1076;&#1080;&#1084;
		if cs then cairo_surface_destroy(cs) end
-- &#1089;&#1086;&#1079;&#1076;&#1072;&#1077;&#1084; cs &#1089; &#1087;&#1072;&#1088;&#1072;&#1084;&#1077;&#1090;&#1088;&#1072;&#1084;&#1080; &#1086;&#1082;&#1085;&#1072; &#1082;&#1086;&#1085;&#1100;&#1082;&#1086;&#1074;
		cs = cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, conky_window.width, conky_window.height)
	end

-- &#1077;&#1089;&#1083;&#1080; cr &#1089;&#1091;&#1097;&#1077;&#1089;&#1090;&#1074;&#1091;&#1077;&#1090;, &#1090;&#1086; &#1089;&#1073;&#1088;&#1072;&#1089;&#1099;&#1074;&#1072;&#1077;&#1084; cr
	if cr then cairo_destroy(cr) end

-- &#1089;&#1086;&#1079;&#1076;&#1072;&#1077;&#1084; cr &#1089; &#1087;&#1072;&#1088;&#1072;&#1084;&#1077;&#1090;&#1088;&#1072;&#1084;&#1080; cs - &#1087;&#1072;&#1088;&#1072;&#1084;&#1077;&#1090;&#1088;&#1072;&#1084;&#1080; &#1086;&#1082;&#1085;&#1072; &#1082;&#1086;&#1085;&#1100;&#1082;&#1086;&#1074;
	cr = cairo_create(cs)

-- &#1079;&#1072;&#1073;&#1080;&#1088;&#1072;&#1077;&#1084; &#1076;&#1072;&#1085;&#1085;&#1099;&#1077;

	local xi, yi, radius, angle, draw_bg, bg_colour, fg_colour, reverse, shade = pt['x'], pt['y'], pt['radius'], pt['angle'], pt['draw_bg'], pt['bg_colour'], pt['fg_colour'], pt['reverse'], pt['shade']

-- &#1088;&#1072;&#1089;&#1095;&#1080;&#1090;&#1072;&#1074;&#1072;&#1077;&#1084; &#1084;&#1077;&#1089;&#1090;&#1086; &#1074;&#1099;&#1074;&#1086;&#1076;&#1072; &#1076;&#1080;&#1072;&#1075;&#1088;&#1072;&#1084;&#1084;

	local x, y = 0, 0	--conky_window.text_start_x, conky_window.text_start_y
	local w, h = 350, 350	--conky_window.text_width, conky_window.text_height
	local xc = x + w / 2. + xi
	local yc = y + h / 2. + yi
	local two_pi = 2 * math.pi

-- &#1074;&#1099;&#1074;&#1086;&#1076;&#1080;&#1084; &#1076;&#1080;&#1072;&#1075;&#1088;&#1072;&#1084;&#1084;&#1099;

	local function draw_dat_pie(start, stop, radius, colour, alpha, str)

-- &#1077;&#1089;&#1083;&#1080; &#1085;&#1072;&#1087;&#1088;&#1072;&#1074;&#1083;&#1077;&#1085;&#1080;&#1077; &#1076;&#1080;&#1072;&#1075;&#1088;&#1072;&#1084;&#1084;&#1099; &#1087;&#1088;&#1086;&#1090;&#1080;&#1074; &#1095;&#1072;&#1089;&#1086;&#1074;&#1086;&#1081; &#1089;&#1090;&#1088;&#1077;&#1083;&#1082;&#1080;, &#1090;&#1086;&#1075;&#1076;&#1072;

		if reverse then
-- start, stop &#1084;&#1077;&#1085;&#1103;&#1077;&#1084; &#1085;&#1072; -start, -stop
			start, stop = -start, -stop
		end

-- &#1089;&#1086;&#1093;&#1088;&#1072;&#1085;&#1103;&#1077;&#1084; &#1087;&#1072;&#1088;&#1072;&#1084;&#1077;&#1090;&#1088;&#1099; cr

		cairo_save(cr)

-- &#1087;&#1077;&#1088;&#1077;&#1085;&#1086;&#1089;&#1080;&#1084; &#1094;&#1077;&#1085;&#1090;&#1088; &#1076;&#1080;&#1072;&#1075;&#1088;&#1072;&#1084;&#1084;&#1099; &#1074; &#1088;&#1072;&#1089;&#1095;&#1080;&#1090;&#1072;&#1085;&#1085;&#1091;&#1102; &#1090;&#1086;&#1095;&#1082;&#1091;

		cairo_translate(cr, xc, yc)

-- &#1088;&#1072;&#1079;&#1074;&#1086;&#1088;&#1072;&#1095;&#1080;&#1074;&#1072;&#1077;&#1084; &#1076;&#1080;&#1072;&#1075;&#1088;&#1072;&#1084;&#1084;&#1091;

		cairo_rotate(cr, math.pi / 2 + math.rad(angle))

-- &#1076;&#1077;&#1083;&#1072;&#1077;&#1084; &#1075;&#1088;&#1072;&#1076;&#1080;&#1077;&#1085;&#1090;&#1085;&#1091;&#1102; &#1086;&#1082;&#1088;&#1072;&#1089;&#1082;&#1091; &#1076;&#1080;&#1072;&#1075;&#1088;&#1072;&#1084;&#1084;&#1099;

		pattern = cairo_pattern_create_radial(0, 0, radius * 0.95, 0, 0, radius)
		cairo_pattern_add_color_stop_rgba(pattern, 0, rgb_to_r_g_b(colour, alpha))
		cairo_pattern_add_color_stop_rgba(pattern, 1, 0, 0, 0, 0)

-- &#1088;&#1072;&#1089;&#1095;&#1080;&#1090;&#1099;&#1074;&#1072;&#1077;&#1084; &#1093;&#1086;&#1088;&#1076;&#1091; &#1076;&#1080;&#1072;&#1075;&#1088;&#1072;&#1084;&#1084;&#1099;

		local function coords()
			local x = radius * math.cos(two_pi * start)
			local y = radius * math.sin(two_pi * start)
			return x, y
		end

-- &#1085;&#1072;&#1095;&#1072;&#1083;&#1100;&#1085;&#1072;&#1103; &#1090;&#1086;&#1095;&#1082;&#1072; &#1076;&#1080;&#1072;&#1075;&#1088;&#1072;&#1084;&#1084;&#1099;

		cairo_move_to(cr, 0, 0)

-- &#1087;&#1088;&#1086;&#1074;&#1086;&#1076;&#1080;&#1084; &#1083;&#1080;&#1085;&#1080;&#1102;

		cairo_line_to(cr, coords())

-- &#1077;&#1089;&#1083;&#1080; &#1076;&#1080;&#1072;&#1075;&#1088;&#1072;&#1084;&#1084;&#1072; &#1074;&#1099;&#1074;&#1086;&#1076;&#1080;&#1090;&#1089;&#1103; &#1087;&#1086; &#1095;&#1072;&#1089;&#1086;&#1074;&#1086;&#1081; &#1089;&#1090;&#1088;&#1077;&#1083;&#1082;&#1077;, &#1090;&#1086;&#1075;&#1076;&#1072;

		if not reverse then

-- &#1088;&#1080;&#1089;&#1091;&#1077;&#1084; &#1076;&#1091;&#1075;&#1091; &#1087;&#1086; &#1095;&#1072;&#1089;&#1086;&#1074;&#1086;&#1081; &#1089;&#1090;&#1088;&#1077;&#1083;&#1082;&#1077;

			cairo_arc(cr, 0, 0, radius, two_pi * start, two_pi * stop)

-- &#1080;&#1085;&#1072;&#1095;&#1077;, &#1077;&#1089;&#1083;&#1080; &#1076;&#1080;&#1072;&#1075;&#1088;&#1072;&#1084;&#1084;&#1072; &#1074;&#1099;&#1074;&#1086;&#1076;&#1080;&#1090;&#1089;&#1103; &#1087;&#1088;&#1086;&#1090;&#1080;&#1074; &#1095;&#1072;&#1089;&#1086;&#1074;&#1086;&#1081; &#1089;&#1090;&#1088;&#1077;&#1083;&#1082;&#1077;

		else

-- &#1088;&#1080;&#1089;&#1091;&#1077;&#1084; &#1076;&#1091;&#1075;&#1091; &#1087;&#1088;&#1086;&#1090;&#1080;&#1074; &#1095;&#1072;&#1089;&#1086;&#1074;&#1086;&#1081; &#1089;&#1090;&#1088;&#1077;&#1083;&#1082;&#1077;

			cairo_arc_negative(cr, 0, 0, radius, two_pi * start, two_pi * stop)
		end

-- &#1079;&#1072;&#1082;&#1072;&#1085;&#1095;&#1080;&#1074;&#1072;&#1077;&#1084; &#1074;&#1099;&#1074;&#1086;&#1076; &#1089;&#1077;&#1082;&#1090;&#1086;&#1088;&#1072; &#1076;&#1080;&#1072;&#1075;&#1088;&#1072;&#1084;&#1084;&#1099;

		cairo_line_to(cr, 0, 0)
		cairo_close_path(cr)
-- &#1086;&#1082;&#1088;&#1072;&#1096;&#1080;&#1074;&#1072;&#1077;&#1084; &#1089;&#1077;&#1082;&#1090;&#1086;&#1088;
		cairo_set_source(cr, pattern)
		cairo_pattern_destroy(pattern)
		cairo_fill(cr)
		cairo_set_source(cr, pattern)
-- ------------------------------------------------- &#1074;&#1099;&#1074;&#1086;&#1076; &#1090;&#1077;&#1082;&#1089;&#1090;&#1072; ---------------------
-- &#1077;&#1089;&#1083;&#1080; str &#1089;&#1091;&#1097;&#1077;&#1089;&#1090;&#1074;&#1091;&#1077;&#1090;, &#1090;&#1086;&#1075;&#1076;&#1072;
		if str then
-- &#1079;&#1072;&#1076;&#1077;&#1081;&#1089;&#1090;&#1074;&#1091;&#1077;&#1084; extents
			local extents = cairo_text_extents_t
-- &#1088;&#1072;&#1079;&#1074;&#1086;&#1088;&#1072;&#1095;&#1080;&#1074;&#1072;&#1077;&#1084; &#1090;&#1077;&#1082;&#1089;&#1090;
			cairo_rotate(cr, (start + (stop - start) / 2) * two_pi + math.pi)
-- &#1085;&#1072;&#1079;&#1085;&#1072;&#1095;&#1072;&#1077;&#1084; &#1094;&#1074;&#1077;&#1090; &#1090;&#1077;&#1082;&#1089;&#1090;&#1072; - &#1074; &#1076;&#1072;&#1085;&#1085;&#1086;&#1084; &#1089;&#1083;&#1091;&#1095;&#1072;&#1077; &#1073;&#1077;&#1083;&#1099;&#1081;
			cairo_set_source_rgba(cr, 0, 0, 0, alpha)
-- &#1085;&#1072;&#1079;&#1085;&#1072;&#1095;&#1072;&#1077;&#1084; &#1096;&#1088;&#1080;&#1092;&#1090;
			cairo_select_font_face(cr, "PT Sans", CAIRO_FONT_SLANT_NORMAL, CAIRO_FONT_WEIGHT_NORMAL)
-- &#1085;&#1072;&#1079;&#1085;&#1072;&#1095;&#1072;&#1077;&#1084; &#1088;&#1072;&#1079;&#1084;&#1077;&#1088; &#1096;&#1088;&#1080;&#1092;&#1090;&#1072;
			cairo_set_font_size(cr, radius * 0.10)
-- &#1085;&#1072;&#1079;&#1085;&#1072;&#1095;&#1072;&#1077;&#1084; &#1084;&#1077;&#1089;&#1090;&#1086; &#1074;&#1099;&#1074;&#1086;&#1076;&#1072; &#1090;&#1077;&#1082;&#1089;&#1090;&#1072;
			cairo_move_to (cr, -radius + radius * 0.075, radius * 0.03)
-- &#1074;&#1099;&#1074;&#1086;&#1076;&#1080;&#1084; &#1090;&#1077;&#1082;&#1089;&#1090;
			cairo_show_text(cr, str)
		end
-- &#1074;&#1086;&#1089;&#1089;&#1090;&#1072;&#1085;&#1072;&#1074;&#1083;&#1080;&#1074;&#1072;&#1077;&#1084; cr
		cairo_restore(cr)
	end
-- ------------------------------------ &#1082;&#1086;&#1085;&#1077;&#1094; &#1074;&#1099;&#1074;&#1086;&#1076;&#1072; &#1090;&#1077;&#1082;&#1089;&#1090;&#1072; ----------------------------

-- &#1077;&#1089;&#1083;&#1080; &#1080;&#1089;&#1087;&#1086;&#1083;&#1100;&#1079;&#1091;&#1077;&#1084; &#1092;&#1086;&#1085;, &#1090;.&#1077;. &#1086;&#1082;&#1088;&#1091;&#1078;&#1085;&#1086;&#1089;&#1090;&#1100; &#1085;&#1072; &#1082;&#1086;&#1090;&#1086;&#1088;&#1091;&#1102; &#1074;&#1099;&#1074;&#1086;&#1076;&#1080;&#1090;&#1089;&#1103; &#1076;&#1080;&#1072;&#1075;&#1088;&#1072;&#1084;&#1084;&#1072;, &#1090;&#1086;&#1075;&#1076;&#1072; &#1079;&#1072;&#1075;&#1088;&#1091;&#1078;&#1072;&#1077;&#1084; &#1076;&#1072;&#1085;&#1085;&#1099;&#1077; &#1092;&#1086;&#1085;&#1072;

	if draw_bg then	draw_dat_pie(0, 1, radius, bg_colour, 1) end
-- &#1089;&#1073;&#1088;&#1072;&#1089;&#1099;&#1074;&#1072;&#1077;&#1084; &#1079;&#1085;&#1072;&#1095;&#1077;&#1085;&#1080;&#1077; p &#1085;&#1072; 0
	local p = 0
-- &#1079;&#1072;&#1075;&#1088;&#1091;&#1078;&#1072;&#1077;&#1084; &#1074; f &#1079;&#1085;&#1072;&#1095;&#1077;&#1085;&#1080;&#1077; 
	local f = t[1]['value'] / 100

	for i in pairs(t) do
		local v = t[i]['value']
		local str = string.format('%.1f %s', v, t[i]['name'])
		v = v / 100
-- &#1077;&#1089;&#1083;&#1080; &#1080;&#1089;&#1087;&#1086;&#1083;&#1100;&#1079;&#1091;&#1077;&#1084; &#1090;&#1077;&#1085;&#1100;, &#1090;&#1086;&#1075;&#1076;&#1072; &#1079;&#1072;&#1075;&#1088;&#1091;&#1078;&#1072;&#1077;&#1084; &#1076;&#1072;&#1085;&#1085;&#1099;&#1077; &#1090;&#1077;&#1085;&#1080;
		if shade then
			draw_dat_pie(p, p + v, radius * 0.94, fg_colour, v / p, str)
-- &#1080;&#1085;&#1072;&#1095;&#1077; &#1079;&#1072;&#1075;&#1088;&#1091;&#1078;&#1072;&#1077;&#1084; &#1076;&#1072;&#1085;&#1085;&#1099;&#1077; &#1073;&#1077;&#1079; &#1090;&#1077;&#1085;&#1080;
		else
			draw_dat_pie(p, p + v, radius * 0.94, fg_colour, 1, str)
		end


		p = p + v
	end
-- &#1089;&#1073;&#1088;&#1072;&#1089;&#1099;&#1074;&#1072;&#1077;&#1084; cr
	cairo_destroy(cr)
	cr = nil
end

function conky_cairo_cleanup()
-- &#1089;&#1073;&#1088;&#1072;&#1089;&#1099;&#1074;&#1072;&#1077;&#1084; &#1079;&#1085;&#1072;&#1095;&#1077;&#1085;&#1080;&#1103; cs
	cairo_surface_destroy(cs)
	cs = nil
end

-- Compatibility: Lua-5.1
-- thanks to Lua users wiki for this
function split(str, pat)
	local t = {}  -- NOTE: use {n = 0} in Lua-5.0
	local fpat = "(.-)" .. pat
	local last_end = 1
	local s, e, cap = str:find(fpat, 1)
	while s do
		if s ~= 1 or cap ~= "" then
			table.insert(t, cap)
		end
		last_end = e+1
		s, e, cap = str:find(fpat, last_end)
	end
	if last_end <= #str then
		cap = str:sub(last_end)
		table.insert(t, cap)
	end
	return t
end

function tablify_top(t)
	local ret = {}
	for i in pairs(t) do
		table.insert(ret, {
			value=tonumber(string.match(t[i], '(%d+%.%d+)')), name=string.match(t[i], '%d+%.%d+ ([%w_]+)')
		})
	end
	return ret
end

function conky_pie_time()
	local function pie_me(pt)
		local str = ''
		local sort_key = ''
		if pt['name'] == 'top' then
			sort_key = 'cpu'
		elseif pt['name'] == 'top_mem' then
			sort_key = 'mem'
		elseif pt['name'] == 'top_io' then
			sort_key = 'io_perc'
		else
			print('Invalid top type')
			return
		end
-- &#1073;&#1091;&#1076;&#1077;&#1084; &#1074;&#1099;&#1074;&#1086;&#1076;&#1080;&#1090;&#1100; 10 &#1089;&#1077;&#1082;&#1090;&#1086;&#1088;&#1086;&#1074;
		for i=1,10 do
			str = str .. string.format('${%s %s %i} ${%s name %i}\n', pt['name'], sort_key, i, pt['name'], i)
		end


		str = conky_parse(str)
		local tbl = split(str, '\n')
		tbl = tablify_top(tbl)
		draw_pie(tbl, pt)
	end

	for i in pairs(settings_table) do
		pie_me(settings_table[i])
	end
end
--[[ END PIE WIDGET ]]
-- ------------------------------------------------------------------------------------

--function rgb_to_r_g_b(colour,alpha)
--  return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
--end

--[[ BACKGROUND WIDGET by londonali1010 (2009)]]
function background(cr)
  local w=conky_window.width
  local h=conky_window.height
-- "corner_r" is the radius, in pixels, of the rounded corners. If you don't want rounded corners, use 0.
  local corner_r=45
-- Set the colour of your background.
  local bg_colour=0x000000
-- Set the transparency (alpha) of your background.
  local bg_alpha=0.4

  cairo_move_to(cr,corner_r,0)
  cairo_line_to(cr,w-corner_r,0)
  cairo_curve_to(cr,w,0,w,0,w,corner_r)
  cairo_line_to(cr,w,h-corner_r)
  cairo_curve_to(cr,w,h,w,h,w-corner_r,h)
  cairo_line_to(cr,corner_r,h)
  cairo_curve_to(cr,0,h,0,h,0,h-corner_r)
  cairo_line_to(cr,0,corner_r)
  cairo_curve_to(cr,0,0,0,0,corner_r,0)
  cairo_close_path(cr)

  cairo_set_source_rgba(cr,rgb_to_r_g_b(bg_colour,bg_alpha))
  cairo_fill(cr)
end
--[[ END BACKGROUND WIDGET ]]
-- ----------------------------------------------------------------------
--[[ TEXT WIDGET ]]

	function addzero100(num)

		if tonumber(num) < 10 then
		return "00" .. num
		elseif tonumber(num) <100 then
		return "0" .. num
		else
		return num
		end
	end

	function string:split(delimiter)

		local result = { }
		local from  = 1
		local delim_from, delim_to = string.find( self, delimiter, from  )
		while delim_from do
		table.insert( result, string.sub( self, from , delim_from-1 ) )
		from  = delim_to + 1
		delim_from, delim_to = string.find( self, delimiter, from  )
		end
		table.insert( result, string.sub( self, from  ) )
		return result
	end

	function circlewriting(cr, text, font, fsize, radi, horiz, verti, tred, tgreen, tblue, talpha, start, finish, var1)

		local inum=string.len(text)
		range=finish
		deg=(finish-start)/(inum-1)
		degrads=1*(math.pi/180)
		local textcut=string.gsub(text, ".", "%1@@@")
		texttable=string.split(textcut, "@@@")
		for i = 1,inum do
			ival=i
			interval=(degrads*(start+(deg*(i-1))))+var1
			interval2=degrads*(start+(deg*(i-1)))
			txs=0+radi*(math.sin(interval))
			tys=0-radi*(math.cos(interval))
			cairo_select_font_face (cr, font, CAIRO_FONT_SLANT_NORMAL, CAIRO_FONT_WEIGHT_NORMAL);
			cairo_set_font_size (cr, fsize);
			cairo_set_source_rgba (cr, tred, tgreen, tblue, talpha);
			cairo_move_to (cr, txs+horiz, tys+verti);
			cairo_rotate (cr, interval2)
			cairo_show_text (cr, (texttable[i]))
			cairo_rotate (cr, -interval2)
		end
	end

	function circlewritingdown(cr, text, font, fsize, radi, horiz, verti, tred, tgreen, tblue, talpha, start, finish, var1)

		local inum=string.len(text)
		deg=(start-finish)/(inum-1)
		degrads=1*(math.pi/180)
		local textcut=string.gsub(text, ".", "%1@@@")
		texttable=string.split(textcut, "@@@")
		for i = 1,inum do
			ival=i
			interval=(degrads*(start-(deg*(i-1))))+var1
			interval2=degrads*(start-(deg*(i-1)))
			txs=0+radi*(math.sin(interval))
			tys=0-radi*(math.cos(interval))
			cairo_select_font_face (cr, font, CAIRO_FONT_SLANT_NORMAL, CAIRO_FONT_WEIGHT_NORMAL);
			cairo_set_font_size (cr, fsize);
			cairo_set_source_rgba (cr, tred, tgreen, tblue, talpha);
			cairo_move_to (cr, txs+horiz, tys+verti);
			cairo_rotate (cr, interval2+(180*math.pi/180))
			cairo_show_text (cr, (texttable[i]))
			cairo_rotate (cr, -interval2-(180*math.pi/180))
		end
	end

	function conky_draw_text()

		local updates=conky_parse('${updates}')
		update_num=tonumber(updates)
		if update_num > 5 then
			if conky_window==nil then return end
			local w=conky_window.width
			local h=conky_window.height
			local cs=cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, w, h)
			cr=cairo_create(cs)



--circlewriting variable
cpu=tonumber(conky_parse('${CPU}'))
--text must be in quotes
text=("CPU " .. (addzero100(cpu)) .. "%") 
--font name must be in quotes
font="PT Sans"
fontsize=12
radius=82
positionx=240
positiony=215
colorred=1
colorgreen=0.7
colorblue=0
coloralpha=1
--to set start and finish values for circlewriting, if the text will cross 0 degrees then you must calculate for 360+finish degrees
--eg if you want to go from 270 to 90, then you will input 270 to 450.  Finish has to be greater than start.
start=280
finish=350
letterposition=0
circlewriting(cr, text, font, fontsize, radius, positionx, positiony, colorred, colorgreen, colorblue, coloralpha, start, finish, letterposition)

--circlewritingdown variables
hdd=tonumber(conky_parse('${fs_used_perc /}'))
--text must be in quotes
text=("FILESYS " .. (addzero100(hdd)) .. "%") 
--font name must be in quotes
font="PT Sans"
fontsize=12
radius=82
positionx=240
positiony=215
colorred=1
colorgreen=0.7
colorblue=0
coloralpha=1
--to set start and finish values for circlewritingdown, if the text will cross 0 degrees then you must calculate for 0-finish degrees
--eg if you want to go from 90 to 270, then you will input 90 to -90.  Start has to be greater than finish
start=10
finish=80
letterposition=0
circlewriting(cr, text, font, fontsize, radius, positionx, positiony, colorred, colorgreen, colorblue, coloralpha, start, finish, letterposition)

--circlewritingdown variable
mem=tonumber(conky_parse('${memperc}'))
--text must be in quotes
text=("MEMORY " .. (addzero100(mem)) .. "%")
--font name must be in quotes
font="PT Sans"
fontsize=12
radius=90
positionx=240
positiony=215
colorred=1
colorgreen=0.7
colorblue=0
coloralpha=1
--to set start and finish values for circlewritingdown, if the text will cross 0 degrees then you must calculate for 0-finish degrees
--eg if you want to go from 90 to 270, then you will input 90 to -90.  Start has to be greater than finish
start=260
finish=190
letterposition=0.06
circlewritingdown(cr, text, font, fontsize, radius, positionx, positiony, colorred, colorgreen, colorblue, coloralpha, start, finish, letterposition)

--circlewriting variables
swap=tonumber(conky_parse('${swapperc}'))
--text must be in quotes
text=("SWAP " .. (addzero100(swap)) .. "% ") 
--font name must be in quotes
font="PT Sans"
fontsize=12
radius=90
positionx=240
positiony=215
colorred=1
colorgreen=0.7
colorblue=0
coloralpha=1
--to set start and finish values for circlewriting, if the text will cross 0 degrees then you must calculate for 360+finish degrees
--eg if you want to go from 270 to 90, then you will input 270 to 450.  Finish has to be greater than start.
start=170
finish=100
letterposition=0
circlewritingdown(cr, text, font, fontsize, radius, positionx, positiony, colorred, colorgreen, colorblue, coloralpha, start, finish, letterposition)


		end
	end
--[[ END TEXT WIDGET ]]
-- ---------------------------------------------------------------
--[[ EQUALIZER WIDGET
	v1.0 by wlourf (10 Feb. 2010)
	This widget draw a simple bar like (old) equalizers on hi-fi systems.
	http://u-scripts.blogspot.com/
	
	The arguments are :
	- "name" is the type of stat to display; you can choose from 'cpu', 'memperc', 'fs_used_perc', 'battery_used_perc'.
    - "arg" is the argument to the stat type, e.g. if in Conky you would write ${cpu cpu0}, 'cpu0' would be the argument. 
    	If you would not use an argument in the Conky variable, use ''.
	- "max" is the maximum value of the bar. If the Conky variable outputs a percentage, use 100.
	- "nb_blocks" is the umber of block to draw
	- "cap" id the cap of a block, possibles values are CAIRO_LINE_CAP_ROUND , CAIRO_LINE_CAP_SQUARE or CAIRO_LINE_CAP_BUTT
	  see http://www.cairographics.org/samples/set_line_cap/
	- "xb" and "yb" are the coordinates of the bottom left point of the bar
	- "w" and "h" are the width and the height of a block (without caps)
	- "space" is the space betwwen two blocks, can be null or negative
	- "bgc" and "bga" are background colors and alpha when the block is not LIGHT OFF
	- "fgc" and "fga" are foreground colors and alpha when the block is not LIGHT ON
	- "alc" and "ala" are foreground colors and alpha when the block is not LIGHT ON and ALARM ON
	- "alarm" is the value where blocks LIGHT ON are in a different color (values from 0 to 100)
	- "led_effect" true or false : to show a block with a led effect
	- "led_alpha" alpha of the center of the led (values from 0 to 1)
	- "smooth" true or false : colors in the bar has a smooth effect
	- "mid_color",mid_alpha" : colors of the center of the bar (mid_color can to be set to nil)
	- "rotation" : angle of rotation of the bar (values are 0 to 360 degrees). 0 = vertical bar, 90 = horizontal bar
	
]]

function equalizer(cr, name, arg, max, nb_blocks, cap, xb, yb, w, h, space, bgc, bga, fgc, fga,alc,ala,alarm,led_effect,led_alpha,smooth,mid_color,mid_alpha,rotation)
 	local function rgb_to_r_g_b(colour, alpha)
		return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
	end
local cap_round = CAIRO_LINE_CAP_ROUND
	local cap_square = CAIRO_LINE_CAP_SQUARE
	local cap_butt = CAIRO_LINE_CAP_BUTT	

	local function setup_equalizer()
		
		local str = conky_parse(string.format('${%s %s}', name, arg))
		
		local value = tonumber(str)
		if value == nil then value = 0 end
if value <= 100 then max = 50 end
		local pct = 100*value/max
		local pcb = 100/nb_blocks
		
		cairo_set_line_width (cr, h)
		cairo_set_line_cap  (cr, cap)
		
		local angle= rotation*math.pi/180
		for pt = 1,nb_blocks do  
			local light_on=false
			--set colors
			local col,alpha = bgc,bga
			if pct>=(100/nb_blocks/2) then --start after an half bloc
				if pct>=(pcb*(pt-1)) then 
					light_on=true
					col,alpha = fgc,fga
					if pct>=alarm and (pcb*pt)>alarm then col,alpha = alc,ala end
				end
			end

			--vertical points
			local x1=xb
			local y1=yb-pt*(h+space)
			local radius0 = yb-y1
	
			local x2=xb+radius0*math.sin(angle)
			local y2=yb-radius0*math.cos(angle)
			
			--line on angle
			local a1=(y2-yb)/(x2-xb)
			local b1=y2-a1*x2

			--line perpendicular to angle
			local a2=-1/a1
			local b2=y2-a2*x2
			
			--dots on perpendicular
			local xx0,xx1,yy0,yy1=0,0,0,0
			if rotation == 90  or rotation == 270 then
				xx0,xx1=x2,x2
				yy0=yb
				yy1=yb+w
			else
				xx0,xx1=x2,x2+w*math.cos(angle)
				yy0=xx0*a2+b2
				yy1=xx1*a2+b2
			end

			--perpendicular segment
			cairo_move_to (cr, xx0 ,yy0)
			cairo_line_to (cr, xx1 ,yy1)
		
			--colors
			local xc,yc=(xx0+xx1)/2,(yy0+yy1)/2
			if light_on and led_effect then
				local pat = cairo_pattern_create_radial (xc, yc, 0, xc,yc,w/1.5)
				cairo_pattern_add_color_stop_rgba (pat, 0, rgb_to_r_g_b(col,led_alpha))
				cairo_pattern_add_color_stop_rgba (pat, 1, rgb_to_r_g_b(col,alpha))
				cairo_set_source (cr, pat)
				cairo_pattern_destroy(pat)
			else
				cairo_set_source_rgba(cr, rgb_to_r_g_b(col,alpha))
			end 

			if light_on and smooth then
				local radius = (nb_blocks+1)*(h+space)
				if pt==1 then 
					xc0,yc0=xc,yc --remember the center of first block
				end
				cairo_move_to(cr,xc0,yc0)
				local pat = cairo_pattern_create_radial (xc0, yc0, 0, xc0,yc0,radius)
				cairo_pattern_add_color_stop_rgba (pat, 0, rgb_to_r_g_b(fgc,fga))
				cairo_pattern_add_color_stop_rgba (pat, 1, rgb_to_r_g_b(alc,ala))
				if mid_color ~=nil then
					cairo_pattern_add_color_stop_rgba (pat, 0.5,rgb_to_r_g_b(mid_color,mid_alpha))
				end
				cairo_set_source (cr, pat)
				cairo_pattern_destroy(pat)
			end 
		
			cairo_stroke (cr);

		end
	end	
	--prevent segmentatioon error
	local updates=tonumber(conky_parse('${updates}'))
	if updates> 3 then
		setup_equalizer()
	end
end

-- -------------------------------------------------------------------------------------
	function conky_widgets()
		if conky_window == nil then return end
		local cs = cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, conky_window.width, conky_window.height)
-- -------------------------------------------------------------------------------------

	cr = cairo_create(cs)
	background(cr)
	cairo_destroy(cr)
-- ---------------------------------------
	cr = cairo_create(cs)
	conky_pie_time()
	cairo_destroy(cr)

--[[ &#1042;&#1099;&#1074;&#1086;&#1076; &#1095;&#1072;&#1089;&#1086;&#1074; ]]
  
	cr = cairo_create(cs)
	clock(cr, 165, 140, 150, 0xffffff, 1, 0x606070, 1)
	cairo_destroy(cr)
-- ---------------------------------------------------------------------------------

	cr = cairo_create(cs)
	calendar()
	cairo_destroy(cr)

-- -------------------------------------------------------------------
	cr = cairo_create(cs)
	conky_draw_text()
	cairo_destroy(cr)
-- ------------------------------------------------------------


cr = cairo_create(cs)

equalizer(cr, 'downspeedf', 'eth0', 1000, 10, CAIRO_LINE_CAP_ROUND, 215, 111, 1, 12, 2, 0x606070, 0.5, 0xffdf00, 0.5, 0xff8700, 1, 80, true, 1, true, 0xff0000, 0.5, 90)

equalizer(cr, 'upspeedf', 'eth0', 100, 10, CAIRO_LINE_CAP_ROUND, 215, 317, 1, 12, 2, 0x606070, 0.5, 0xffdf00, 0.5, 0xff8700, 1, 80, true, 1, true, 0xff0000, 0.5, 90)

	cairo_destroy(cr)


end
```

---

### Post by wlourf on 2010-02-27
> **degan said:**
> Hi boys....

How do I do to remove the shade that I have in the conky?


hi, it's very simple : don't call the background widget in the conky_widgets() function
delete or comment theses three lines :
```
    cr = cairo_create(cs)
    background(cr)
    cairo_destroy(cr)

```

---

### Post by degan on 2010-02-27
This:

--[[ &#1042;&#1099;&#1074;&#1086;&#1076; &#1095;&#1072;&#1089;&#1086;&#1074; ]]
  
	cr = cairo_create(cs)
	clock(cr, 165, 140, 150, 0xffffff, 1, 0x606070, 1)
	cairo_destroy(cr)
-- ---------------------------------------------------------------------------------

	cr = cairo_create(cs)
	calendar()
	cairo_destroy(cr)

-- -------------------------------------------------------------------
	#cr = cairo_create(cs)
	#conky_draw_text()
	#cairo_destroy(cr)
-- ------------------------------------------------------------


cr = cairo_create(cs)

equalizer(cr, 'downspeedf', 'eth0', 1000, 10, CAIRO_LINE_CAP_ROUND, 215, 111, 1, 12, 2, 0x606070, 0.5, 0xffdf00, 0.5, 0xff8700, 1, 80, true, 1, true, 0xff0000, 0.5, 90)

equalizer(cr, 'upspeedf', 'eth0', 100, 10, CAIRO_LINE_CAP_ROUND, 215, 317, 1, 12, 2, 0x606070, 0.5, 0xffdf00, 0.5, 0xff8700, 1, 80, true, 1, true, 0xff0000, 0.5, 90)

	cairo_destroy(cr)


end

---

### Post by miegiel on 2010-02-27
> **HangukMiguk said:**
> took the pound sign out, still not working.  still showing up as black.

Ok, didn't want to complain about it earlier, since it looked like a easy problem. But your question is kind of off-topic in this thread. This thread is for scripts people use in combination with conky (like weather scripts, calendar scripts) and not about the .conkyrc configuration script you use with conky.

The [Post your .conkyrc files w/ screenshots]("http://ubuntuforums.org/showthread.php?t=281865") mega thread is a better place to ask help.

Ok, that's enough nagging :D

Colors are working fine here. Try my test conky if you like:
```
# Info on stuff above TEXT here : http://conky.sourceforge.net/config_settings.html
# Info on stuff below TEXT here : http://conky.sourceforge.net/variables.html
#
minimum_size 256 512
maximum_width 1366
gap_x 1
gap_y 1
#alignment bm
update_interval 2.0
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
uppercase no
own_window yes
own_window_type normal # normal desktop override
own_window_transparent no # yes no
own_window_hints skip_taskbar,skip_pager # undecorated,below,above,sticky,skip_taskbar,skip_pager
own_window_colour black
double_buffer yes
use_xft yes
xftfont Radio Space Bold:size=8 # get font at http://www.dafont.com/radio-space.font
default_color white
text_buffer_size 1024 # The size of this buffer cannot be smaller than the default value of 256 bytes. 

#${color green}1 / TRUE / YES${color}${else}${color red}0 / FALSE / NO${color}${endif}
#no test ${font sans:size=8}^_^${font}

TEXT
${color yellow}build_arch ${conky_build_arch}
build_date ${conky_build_date}
conky_version ${conky_version}${color}

${color green}start test${color}

[COLOR="Blue"]default color ${color 00CCCC} color=00CCCC ${color} default color[/COLOR]

${color red}end test${color}

${color yellow}${kernel}
${machine}${if_match "${battery}" != "not present"}${if_match "${execi 60 cat /proc/acpi/battery/BAT0/state | grep charged | awk '{print $3}'}" != "charged"}

${execi 60 cat /proc/acpi/battery/BAT0/state | grep capacity: | awk '{print $3 $4}'}
${execi 60 cat /proc/acpi/battery/BAT0/state | grep rate: | awk '{print $3 $4}'}
${battery_time}${endif}${endif}${color}
```

---

### Post by wannabegeek on 2010-02-27
hi everyone,
I'm a noob to shell scripting and programming in general...but I really want a conky
that has my wireless connection speed.

I cut and paste a script and got conky to work. I deleted a few things, but don't understand very much of what the code means. 

thank you,
wbg 


[PHP]# set to yes if you want Conky to be forked in the background
background yes

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Trebuchet MS:size=10

# Text alpha when using Xft
xftalpha 0.9

# Update interval in seconds
update_interval 1.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes

# If own_window is yes, you may use type normal, desktop or override
own_window_type normal

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window is yes, these window manager hints may be used
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 160 5

# Maximum width
maximum_width 160

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Draw borders around graphs
draw_graph_borders no

# Stippled borders?
# stippled_borders 8

# border margins
# border_margin 2

# border width
# border_width 1

# Default colors and also border colors
default_color white
default_shade_color red
default_outline_color green

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 12
gap_y 12

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no

# variable is given either in format $variable or in ${variable}

# stuff after 'TEXT' will be formatted on screen

#  unused text
#  Current:${alignr}${execi 20 /home/tonyt/scripts/.conky_eth2} Mbits/sec
#  hda Temp:${alignr}${execi 1800 /home/tonyt/scripts/.hdtemp}

TEXT
$sysname $kernel
Uptime:$alignr$uptime
${time %A}$alignr${time %F}

Hostname:$alignr$nodename
ath0:$alignr${addr ath0}
Signal:$alignr${linkstatus  ath0}
Current:${alignr}${execi 20 /home/tonyt/scripts/.conky_ath0} Mbits/sec
eth2:$alignr${addr eth2}
Signal:$alignr${linkstatus  eth2}
eth0:$alignr${addr eth0}
 
RAM: $mem/$memmax ${color lightgray}$membar$color
CPU0 ${cpu cpu1}% ${color lightgray}${cpubar cpu1}$color
CPU1 ${cpu cpu2}% ${color lightgray}${cpubar cpu2}$color

hda3: ${fs_used_perc /}% ${color lightgray}${fs_bar /}$color
hda5: ${fs_used_perc /mnt/FILES}% ${color lightgray}${fs_bar /mnt/FILES/}$color
Swap: $swapperc% ${color lightgray}$swapbar$color

Processes: $processes ${alignr}Running: $running_processes[/PHP]

---

### Post by miegiel on 2010-02-27
> **wannabegeek said:**
> hi everyone,
I'm a noob to shell scripting and programming in general...but I really want a conky
that has my wireless connection speed.

I cut and paste a script and got conky to work. I deleted a few things, but don't understand very much of what the code means. 

thank you,
wbg 


...

Read post above yours or just [klick and post again here]("http://ubuntuforums.org/showthread.php?t=281865").

---

### Post by wannabegeek on 2010-02-27
Hi Miegiel,
I figured these lines are the pertinent ones:

${offset 240}${color}Up: ${color }${upspeed eth0} k/s
${offset 240}${upspeedgraph eth0 20,130 000000 ffffff}
${offset 240}${color}Down: ${color }${downspeed eth0}k/s${color}
${offset 240}${downspeedgraph eth0 20,130 000000 ffffff}

Is upspeed a function call ? and the {} prints the return of upspeed to the screen ?
I would need the name of my wireless, instead of  'eth0'
is that just the name of my network that I see under the network manager ?

thanks !
wbg

---

### Post by miegiel on 2010-02-27
> **wannabegeek said:**
> Hi Miegiel,
I figured these lines are the pertinent ones:

${offset 240}${color}Up: ${color }${upspeed eth0} k/s
${offset 240}${upspeedgraph eth0 20,130 000000 ffffff}
${offset 240}${color}Down: ${color }${downspeed eth0}k/s${color}
${offset 240}${downspeedgraph eth0 20,130 000000 ffffff}

Is upspeed a function call ? and the {} prints the return of upspeed to the screen ?
I would need the name of my wireless, instead of  'eth0'
is that just the name of my network that I see under the network manager ?

thanks !
wbg

Yeah, use *wlan0* instead of *eth0*. But, in this thread, you are off-topic ;)

[The mega conky thread is here]("http://ubuntuforums.org/showthread.php?t=281865") (for showing off and asking help regarding conky).

---

### Post by wlourf on 2010-02-28
Hi folks,

I just updated the audio spectrum analyzer I posted some days ago. My work in this project is nothing comparing to the author of Impulse who made the library used for analyzing the audio output. Because it's not all my work, I can advise you to see the conky in action [here]("http://www.youtube.com/watch?v=hP9Wt7YKoHM") (I managed to record sound but it is crap and not synchrone with the video, sorry about that).
In this version , I add some "peak" effect and include my bargraph widget in it, so the spectrum can be more colorize, and it is faster !
The updated version is on the post [175]("http://ubuntuforums.org/showpost.php?p=8861782&postcount=175") of this thread.

Bye !

---

### Post by wannabegeek on 2010-03-01
Hi everyone

My friend is getting the Conky bug and is looking for the script used in Parted Magic.
We searched around Parted for it but since we're newbies, and haven't got a handle on grep yet, weren't able to find it.

If you have the script and can post it that is great. Any grep tips are welcome too...

peace,
wbg

---

### Post by andreino on 2010-03-01
> **wlourf said:**
> Thanks for asking! I'm french and I didn't managed to get dates in french till now.

Here is what I've done for having dates according to my locale settings:
It your conkyrc, in the TEXT section, write 
```
${time}
```If you want to hide this date , ```

use_xft yes
xftalpha 0
default_color 000000
```It seems it works only for the black color .

Can you check on your system if it also works and I will update the script if it's ok.
I didn't find a better way in Lua script with os.setlocale() for example...
@mrpeachy:
you made an electroencephalogram and I made a pulsing heart, that's funny !
thank so much wlourt
andreino:D

---

### Post by andreino on 2010-03-01
I ask again, help
wlourf
to see pictures of this
lua in my pc
What should I change in the lua and  script

for the zip pas1.1

[http://ubuntuforums.org/showthread.php?t=1280453&page=13](http://ubuntuforums.org/showthread.php?t=1280453&page=13)

---

### Post by wlourf on 2010-03-01
I am not sure to understand your question ;-)

If you want photos from your computer, in the conkyrc use
```
lua_load /path/to/the/script/photo_album_stack.lua
lua_draw_hook_pre photo_album
```and in the lua script (line 33), set the folder you want to use
```
album_dir = "/home/wlourf/pictures/"
```If you want random photos from deviant art website,  in the conkyrc use
```
lua_load /path/to/the/script/photo_album_stack.lua
lua_draw_hook_pre photo_album /tmp/img-deviant
TEXT
${exec /path/to/the/script/get_deviation.sh /tmp/img-deviant}

```**Don't forget to set the path to fit your system in the conkyrc**. If you have any errors messages, post them


HTH

---

### Post by andreino on 2010-03-02
where I put
script photo_album_stack.lua?
where this path?
/ path / to / the
not work in my
path
lua_load ~ / pas1.1/photo_album_stack.lua
pictures not seen


[[IMG]http://upload.centerzone.it/images/63954394191211212651_thumb.jpg[/IMG]](http://upload.centerzone.it/viewer.php?file=63954394191211212651.png)

---

### Post by andreino on 2010-03-02
The lua
  work only

this script

lua_load /path/to/the/script/photo_album_stack.lua
lua_draw_hook_pre photo_album /tmp/img-deviant
TEXT
${exec /path/to/the/script/get_deviation.sh /tmp/img-deviant}

---

### Post by wlourf on 2010-03-02
show us the errors messages please

---

### Post by andreino on 2010-03-02
hy wlourf
the terminal is not error -
I do not see the pictures of conky
 and does not load the images
Lua[LEFT][IMG]http://www.google.it/images/cleardot.gif[/IMG][/LEFT]

bye

---

### Post by wlourf on 2010-03-02
> **andreino said:**
> hy wlourf
the terminal is not error -
I do not see the pictures of conky
 and does not load the images
Lua[LEFT][IMG]http://www.google.it/images/cleardot.gif[/IMG][/LEFT]

bye
for the bash script, you have to do that
```
chmod +x /path/to/the/script/get_deviation.sh
```before using it.
I you have still troubles, send me the files you use on your computer in a Private Message, I will try to help you, or use the conky mega-thread for getting more help, thanks !

---

### Post by dk75 on 2010-03-02
> **andreino said:**
> where I put
script photo_album_stack.lua?
wherever you wan't
> **andreino said:**
> where this path?
/ path / to / the
not work in my
path
lua_load ~ / pas1.1/photo_album_stack.lua
pictures not seen

it is because You passed "/home/your_login" as your path to the scirpt where it should be "/home/your_login/path/to/the/script.lua"

character "~" is evaluated by shell and Conky as "/home/your_login" and as you passed "space" character after "~" then the rest was ommited and not passed to "lua_load"
It should be ( that if "/home/your_login/pas1.1./photo_album_stack.lua" is a real path to the script )
```
lua_load ~/pas1.1/photo_album_stack.lua
```

so not
```
~<space>/<space>pas1.1/photo_album_stack.lua
```
but
```
~/pas1.1/photo_album_stack.lua
```

---

### Post by andreino on 2010-03-02
lua
```
--[[
Photo Album Stack by wlourf based on Photo Album by londonali1010 (2009)

This script draws a photo album of the files in a specified directory.
Files will be displayed randomized. Each time the script is called, a photo is added on the previous one.
Some parameters bellow control how the photo is drawn (position, angle ...).
A file /tmp/photo_album.png is created to keep history of the files displayed.

To call this script in Conky (assuming that you have saved it as ~/scripts/pas1.1/photo_album_stack.lua), use the following before TEXT:
lua_load ~/scripts/photo_album_stack.lua
lua_draw_hook_pre photo_album

Before calling the conky, use
rm /tmp/photo_album.png & conky -c ~/scripts/pas1.1/conkyrc
to start with a blank screen


Changelog:
v1.0 -- Original release (03/01/2010)
v1.1 -- Add a gray shadow on the bottom right side of each image (optional) (31/01/2010)
     -- Littles images are no more enlarged 
     -- Filename can be written in the frame and/or a special area 
     -- A specific image (instead of a random image) can be use, so we can get random image from the web
]]


require 'imlib2'

-- OPTIONS
-- "album_dir" is the directory containing the images for your photo album;
-- please note that the path must be absolute (e.g. no "~")
-- don't forget the last /
album_dir = "/home/ettore/photo_album"

-- "w_max" and "h_max" are the maximum dimensions, in pixels, that you want the widget to be.
-- The script will ensure that the photo album fits inside the box bounded by w_max and h_max
-- this is the "drop zone"
w_max, h_max = 300, 300

-- can images go out the drop zone (0=no, else =yes)? i.e; cutted on the border of the drop zone
out_l = 0 --left
out_r = 0 --right
out_b = 0 --bottom
out_t = 0 --top

-- "xc" and "yc" are the coordinates of the center of the photo album,
-- relative to the top left corner of the Conky window, in pixels
xc, yc = w_max/2, h_max/2

-- dispersion of the images around xc,yc (in pixels)
disp_x = w_max
disp_y = h_max

--pictures are resized to fit the drop zone, but they can be smaller than
--the drop zone if pc <=100
pc = 75

-- "t" is the thickness of the frame, in % of the photo (0 = no frame)
t = 1

-- "s" is to draw a shadow on the bottom right side of the image (true/false)
-- has to be improve with rotation of picture
s = true

-- "update_interval" is the number of Conky updates between refreshes
update_interval = 1

-- angle is the maximum angle of rotation of the image, in degrees (0-180).
angle = 20

-- filename of the image created by the script
image_tmp="/tmp/photo_album.png"

-- filename can be written in the frame if it exists
show_filename = false
font_path = '/usr/share/fonts/truetype/thai'
font_name = 'Purisa'

--and/or at xt,yt of  the conky window if font_size>0
--height of text area is twice font_size
font_size = 0
bgcolor={0,0,0}
fgcolor={255,255,255}
xt = 0
yt = 0--800-font_size*2



function get_file_to_use()
    num_files = tonumber(conky_parse("${exec ls -A " .. album_dir .. " | wc -l}"))

    if num_files == nil then num_files = 0 end
    if num_files == 0 then return "none" end

    updates = tonumber(conky_parse("${updates}"))
    whole = math.ceil(updates/update_interval)
    math.randomseed( os.time() )
    num_file_to_show = math.random(num_files)

    return conky_parse("${exec ls " .. album_dir .. " | sed -n " .. num_file_to_show .. "p}")
end


function init_drawing_surface()
    imlib_set_cache_size(406 * 524)
    imlib_context_set_dither(1)
end


function draw_image(fixed_image)
    --load fixed image or random image
    if fixed_image == nil then
        image = imlib_load_image(album_dir .. filename)
    else
        image = imlib_load_image(fixed_image)
    end
    if image == nil then 
        print ("can't open image")
        return 
    end
    imlib_context_set_image(image)
    w_img0, h_img0 = imlib_image_get_width(), imlib_image_get_height()
    
    --draw a border (frame) ?
    bsize = 0
    if t>0 then
        bsize = math.floor(math.max(w_img0,h_img0)*t/100)
        fm=imlib_create_image(w_img0, h_img0)
        imlib_context_set_image(fm)
        imlib_image_set_has_alpha(1)
        imlib_context_set_color(255, 255,255,255);
        imlib_image_fill_rectangle(0, 0, w_img0, h_img0);
        
        imlib_blend_image_onto_image(image,1, 0,0, w_img0, h_img0,
            bsize,bsize,w_img0-2*bsize, h_img0-2*bsize)
        imlib_context_set_image(image)
        imlib_free_image()
        imlib_context_set_image(fm)
        image=fm
    else
        imlib_context_set_image(image)
    end

    --draw a shadow ?
    ssize=0
    if s then
        ssize = math.floor(math.max(w_img0,h_img0)/100)
        w_img0, h_img0 = imlib_image_get_width(), imlib_image_get_height()
        shad=imlib_create_image(w_img0+ssize, h_img0+ssize)
        imlib_context_set_image(shad)
        imlib_image_set_has_alpha(1)

        range = imlib_create_color_range();
        imlib_context_set_color_range(range);
      --  imlib_context_set_color(0, 0, 255, 255)
       --         imlib_add_color_to_color_range(0);
        --imlib_context_set_color(255, 0, 0, 255);
        imlib_context_set_color(0, 0, 0, 255);
        imlib_add_color_to_color_range(0);
        imlib_context_set_color(0, 0, 0, 0)        
        imlib_add_color_to_color_range(100);

        imlib_context_set_image(shad);
        imlib_image_fill_color_range_rectangle( w_img0,0, w_img0+ssize, h_img0+ssize,180);
        imlib_image_fill_color_range_rectangle( 0,h_img0, w_img0+ssize, h_img0+ssize,90);
        
        imlib_blend_image_onto_image(image, 1, 0,0, w_img0, h_img0,
            0,0,w_img0, h_img0)
        imlib_context_set_image(image)
        imlib_free_image()
        imlib_context_set_image(shad)
        
    end        
    
    --add filename in the frame ?
    if show_filename and t>0 then
        imlib_add_path_to_font_path(font_path)
        font = imlib_load_font(font_name .. '/' .. bsize/2)
        imlib_context_set_font(font)
        imlib_context_set_color(0, 0, 0, 255);
        imlib_text_draw(bsize,h_img0-bsize,filename); 
        imlib_free_font();
    end

    --add filename in the text area ?
    if font_size>0 then    
        actual_image=imlib_context_get_image()
        imlib_add_path_to_font_path(font_path)
        font = imlib_load_font(font_name .. '/' .. font_size)    
        imlib_context_set_font(font)    
        
        text_img=imlib_create_image(w_max, font_size*2)
        imlib_context_set_image(text_img)
        imlib_image_set_has_alpha(0)
        imlib_context_set_color(bgcolor[1],bgcolor[2],bgcolor[3],255);
        imlib_image_fill_rectangle(0, 0, w_max, font_size*2);        
        imlib_context_set_color(fgcolor[1],fgcolor[2],fgcolor[3], 255);
        imlib_text_draw(font_size/4,font_size/4,filename); 
        imlib_context_set_image(actual_image)
    end

    --rotate image
    math.randomseed( os.time() )
    if angle == 0 then
        angle_rad=0
    else
        angle_rad = (math.random(angle*2)-angle)*math.pi/180
    end
    rot_img = imlib_create_rotated_image(angle_rad)
    imlib_free_image()
    imlib_context_set_image(rot_img)

    --after rotation, image is a square
    w_img, h_img = imlib_image_get_width(), imlib_image_get_height()
    if h_max >= w_max then
        width = (w_max - 2*bsize - ssize)
        height = width
    else
        height = (h_max - 2*bsize - ssize)
        width = height
    end
        
    --prevent enlarge of small images
    if width>w_img0 or height>h_img0 then
        if h_img0 >= w_img0 then
            width = w_img0
            height = w_img0
        else
            width = h_img0
            height = h_img0
        end 
    else
        width = pc*width/100
        height = pc*height/100
    end

    --create or open final image for the conky
    file = io.open(image_tmp, "r")
    io.close()
    if file == nil then
        x=imlib_create_image(w_max,h_max)
        imlib_context_set_image(x)
        imlib_image_set_has_alpha(1)
        imlib_save_image(image_tmp)
        imlib_free_image()
    end
    imageTmp = imlib_load_image(image_tmp)
    imlib_context_set_image(imageTmp)
    rand_x = 0
    if disp_x ~= 0 then
        rand_x = math.random(2*disp_x)-disp_x
    end
    rand_y = 0
    if disp_y ~= 0 then
        rand_y = math.random(2*disp_y)-disp_y
    end

    dx = xc - width/2 + rand_x
    dy = yc - height/2 + rand_y

    --fit in window if asked
    -- abs and random values are here to avoid stacks close to the corners
    if out_l == 0 then
        dx = math.max(0, math.abs(dx))
    end
    if out_r == 0 then
        if dx>(w_max-width) then
            dx=math.random(w_max-width)
        end
    end
    if out_t == 0 then
        dy = math.max(0,math.abs(dy))
    end
    if out_b == 0 then
        if dy>(h_max-height) then
            dy = math.random(h_max-height)
        end
    end

    --add picture (filename) to the final image
    imlib_blend_image_onto_image(rot_img, 1, 0,0, w_img, h_img,dx,dy,width,height)

    --add text (filename) to the final image    
    if font_size>0 then
        imlib_blend_image_onto_image(text_img, 1, 0,0, w_max,font_size*2,
                                                xt,yt,w_max,font_size*2)    
        imlib_context_set_image(text_img)
        imlib_save_image(image_tmp)
    end
    
    -- free memory
    imlib_context_set_image(imageTmp)
    imlib_save_image(image_tmp)

    imlib_render_image_on_drawable(0,0)
    imlib_free_image()

    imlib_context_set_image(rot_img)
    imlib_free_image()
    
end


function conky_photo_album( fixed_image)
    if tonumber(conky_parse("${updates}"))<1 then return end
    if conky_window == nil then return end
    if fixed_image == nil then
        filename = get_file_to_use()
    else
        filename = fixed_image
    end
    if filename == "none" then
        print(album_dir .. ": No files found ... ")
    else
        draw_image(fixed_image)
    end
end


```
conky

```
# -- Conky settings -- #
background no
update_interval 15

cpu_avg_samples 2
net_avg_samples 2

override_utf8_locale yes

double_buffer yes
no_buffers yes

text_buffer_size 2048
imlib_cache_size 0

# -- Window specifications -- #
own_window yes
own_window_type desktop
own_window_transparent yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below

border_inner_margin 0
border_outer_margin 0

minimum_size 800 800

alignment tr
gap_x 0
gap_y 0

# -- Graphics settings -- #
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no


default_color FFFFFF

#For pictures on hard drive folder :

# -- Lua Load -- #
lua_load ~/pas1.1/photo_album_stack.lua
lua_draw_hook_pre photo_album



TEXT




```I corrected the lua and conky,my images are in the folder photo_album.
but conky not working

---

### Post by andreino on 2010-03-02
my terminal error

Conky: desktop window (20000b5) is subwindow of root window (13c)
Conky: window type - desktop
Conky: drawing to created window (0x1800001)
Conky: drawing to double buffer
can't open image
can't open image
can't open image
can't open image
can't open image
can't open image

---

### Post by wlourf on 2010-03-02
Andreino, you see you have errors in the terminal!

In the Lua script, just before the line :

```
album_dir = "/home/ettore/photo_album"
```It is written :
> **-- don't forget the last /**so you have to  write
```
album_dir = "/home/ettore/photo_album/"
```I know English is not your native language (like me ;)) but well, what can I say ... ? Hmm, I know ... I will add a routine to check if the path is correct ! this time it should works fine (I hope to see your capture on italians forums) !

@dk75, if conkyrc and lua script are in the same folder and if you call the script from this folder in a terminal, you can use
```
lua_load ./photo_album_stack.lua
``` but I'm sure you knew that. But it seems more complicated when Lua call a python script, if you read this [message]("http://ubuntuforums.org/showpost.php?p=8901473&postcount=179") and if you have ay idea ... thanks

---

### Post by andreino on 2010-03-02
wlourf
is all ok thank so much
my englis is poor

ronnie wood in los angeles

thank @dk75

[[IMG]http://upload.centerzone.it/images/64501429557404907634_thumb.jpg[/IMG]]("http://upload.centerzone.it/viewer.php?file=64501429557404907634.png")

---

### Post by wlourf on 2010-03-04
rock'n roll andreino ;)

this post to says that the voting is now open for the conky of the month competition over on the conky blog. And the vote is very short because it will close on sunday!
[http://blog.conky.be/2010/03/01/please- … m-entries/]("http://blog.conky.be/2010/03/01/please-vote-on-februarys-cotm-entries/")
[URL="http://blog.conky.be/2010/03/01/please-vote-on-februarys-cotm-entries/"]
[/URL]
So go there and pick the one that fit whit that :


[LIST=1]
[*]**Visual composition**
[*]**Conky innovation**
[*]**Adherence to theme, "St. Valentine's Day/Massacre"**
[/LIST]

I hope its okay to post this... (It's not my intention to try and solicit votes for myself of course ...:P)

Happy Conkying !

---

### Post by wlourf on 2010-03-10
Hi all !

I am an Openbox + Ubuntu user  but sometimes, I can't remember some shortcuts. So I wrote a script to display the shorcuts (keyboard+mouse) from rc.xml in a conky window, and this window is called with a shortcut (!) only when I need it. Maybe this kind of script already exist but I didn't find it :P.

First I need a conkyrc template . The python script will use this file to create a conkyrc in a new file.
The only thing to do in this file is to choose yours colors.
The name of the file is **conky_template.**

The python script **shortcuts.py** read the openbox's rc.xml file.
There are some parameters to set at the beginning of the script :
```
#!/usr/bin/env python
# coding=utf-8

#this script read the file rc.xml for OpenBox configuration
#and returns the shortcuts for Mouse ou Keyboard in a file called by conky
#wlourf 07/03/2010  http://u-scripts.blogspot.com/

import sys
import xml.etree.ElementTree as etree

#full path and name of the rc.xml file
rc_path_file="/home/ll/.config/openbox/rc.xml"
#template of conkyrc to use
conkytemplate_path_file ="/home/ll/scripts/raccourcis/conky_template"

#column width (Ms = souris, Kb= clavier)
lgColMs=50
lgColKb=40

#Number of lines per Column (Ms = souris, Kb= clavier)
nbLnMs=30
nbLnKb=30

#in "Keyboard" array, "appliFirst" will display application name before shorcut
appliFirst=True

#END OF THE PARAMETERS !


```Next, a little bash script **launcher.sh** needed to run the python script and to call conky. Don't forget to make it executable.

The 3 files are in the attchment.

In your rc.xml, you have to add two shortcuts to run launcher.sh with parameters

```
    <keybind key="W-r">
      <action name="Execute">
        <name>shortcuts for desktop</name>
        <command>/home/ll/scripts/raccourcis/launcher.sh /tmp/conky_kb k</command>
      </action>
    </keybind>    
    <keybind key="W-s">
      <action name="Execute">
        <name>shortcuts for mouse</name>
        <command>/home/ll/scripts/raccourcis/launcher.sh /tmp/conky_ms m</command>
      </action>
    </keybind>    

```And the output, for the keyboard :
[[IMG]http://img294.imageshack.us/img294/5571/sckb.th.png[/IMG]]("http://img294.imageshack.us/i/sckb.png/")

and the output for the mouse :
[[IMG]http://img251.imageshack.us/img251/1161/scms.th.png[/IMG]]("http://img251.imageshack.us/i/scms.png/")

Edit : 29/04/2010, v1.1 :
Keyboard shortcuts without commands are no more displayed.
Long command lines are shortened in the dispay to fit the column width.
Edit : 02/05/2010 v1.2 thanks buttate_la _pasta  :)
In keyboard section, when a command string hold the full path to the executable,
it keeps only the name of the executable itself

---

### Post by vickoxy on 2010-03-21
> **mobilediesel said:**
> Here's a *fairly* simple script to display a normal calendar with conky. It shows the last few days of the previous month as well as the first few days of the next month.

You can have the month/year line a different color and the days of the week line a different color.

```
#!/bin/bash
date=$(date '+%F')
DAY=${date:8:2}
DAY=${DAY/#0/}
cal=$(cal)
prev=$(cal $(date '+%-m %Y' --date="${date:0:7}-15 -1 month")|sed 's/ *$//;/^$/d'|tail -1)
next=$(cal $(date '+%-m %Y' --date="${date:0:7}-15 +1 month")|sed '/^ *&/d;1,2d;s/^ *//'|head -1)
if [ ${#next} == 19 ] ;then next=$'\n'"\${color9} $next"
else next="\${color9}  $next"
fi
if [ ${#prev} == 20 ]; then prev="$prev"$'\n '
else prev="$prev  "
fi
echo -e "\${color7}${cal:0:21}\${color4}${cal:21:21}\${color9}$prev\${color}$(echo "${cal:42}" | sed -e '/^ *$/d' -e 's/^/ /' -e 's/$/ /' -e 's/^ *1 / 1 /' -e /" $DAY "/s/" $DAY "/" "'${color3}'"$DAY"'${color}'" "/ -e 's/^ //' -e 's/ *$//')$next"
```
[ATTACH]140669[/ATTACH]

I did it this way to limit the number of calls to **cal** as I was calling it a few times. Now it's just 3. :)

According to my problem /to mark all the week days with different color ([http://ubuntuforums.org/showthread.php?t=1433914)/](http://ubuntuforums.org/showthread.php?t=1433914)/) i tried to use this scripts, but output is very odd:

---

### Post by mobilediesel on 2010-03-21
> **vickoxy said:**
> According to my problem /to mark all the week days with different color ([http://ubuntuforums.org/showthread.php?t=1433914)/](http://ubuntuforums.org/showthread.php?t=1433914)/) i tried to use this scripts, but output is very odd:

The script has to be called with **execpi** instead of **execi**.

The simplest calendar to color the current day different is this one:
```
cal|sed -e 's/\<'"$(date +%-d)"'\>/${color white}&${color}/'
```
or for starting the week on Monday:
```
cal -m|sed -e 's/\<'"$(date +%-d)"'\>/${color white}&${color}/'
```

For the making the weekdays different color from weekend, I'm not sure yet how to do that. I might have figured it out using **sed** but I still have to mess with it.

---

### Post by vickoxy on 2010-03-22
> **mobilediesel said:**
> The script has to be called with **execpi** instead of **execi**.

The simplest calendar to color the current day different is this one:
```
cal|sed -e 's/\<'"$(date +%-d)"'\>/${color white}&${color}/'
```
or for starting the week on Monday:
```
cal -m|sed -e 's/\<'"$(date +%-d)"'\>/${color white}&${color}/'
```

For the making the weekdays different color from weekend, I'm not sure yet how to do that. I might have figured it out using **sed** but I still have to mess with it.

Well, i successfully use one line calendar-having no colored days. So i tried to use one of your scripts (there are weekdays colored with different colors). I saved it in /home/cal.sh and executed it with ${execpi 60 ~/cal.sh}, but i got nothing...

---

### Post by vickoxy on 2010-03-28
This is sort of bump again. So this is my cal line:

```
${voffset -72}${font andale mono:size=7}${color ffffff}${execpi 600 DJS=`date +%_d`; cal | sed '1d' | sed '/./!d' | sed 's/$/                     /' | fold -w 21 | sed -n '/^.\{21\}/p' | sed 's/^/${alignc -30} /' | sed /" $DJS "/s/" $DJS "/" "'${color 00A9CB}'"$DJS"'${color ffffff}'" "/}${font}
```

So, if anyone knows how/where to put/ to mark week days with different color, not default one.

Thanks

---

### Post by dgw on 2010-03-28
I made a simple bash script that shows what filesystems are mounted and details about them. I have it refreshed every 10 seconds in my conky, so if I connect a flash drive to my computer or something, I see it show up pretty quickly in conky. It shows / and it shows stuff that's mounted in /media.

```
#!/bin/bash

# change this to reflect your mount point
mountPoint="media"

# root
rootDrive=`df -h | awk '{print $(NF)}' | grep "/" | grep -v "dev" | head -1`
drivePercent=`df -h | awk '{print $(NF-1)}' | grep "%" | head -1`
usedSpace=`df -h | grep "%" | grep -v "Use%" | awk '{print $(NF-3)}' | head -1`
totalSpace=`df -h | grep "%" | grep -v "Use%" | awk '{print $(NF-4)}' | head -1`

printf "%-16s%5s%-10s%-12s\n" "Filesystems:" "Used" " / Total" "Percent"
printf "%-16s%5s%-10s%-12s\n" " $rootDrive" $usedSpace " / $totalSpace" "$drivePercent"

# everything that's mounted in the mount point
for drive in `df -h |grep "/media" | awk '{print $(NF)}' | cut -d"/" -f3 | cut -b -12`
do
  drivePercent=`df -h |grep "$mountPoint/"$drive | awk '{print $(NF-1)}'`
  usedSpace=`df -h |grep "$mountPoint/"$drive | awk '{print $(NF-3)}'`
  totalSpace=`df -h |grep "$mountPoint/"$drive | awk '{print $(NF-4)}'`
  printf "%-16s%5s%-10s%-12s\n" " $drive" $usedSpace " / $totalSpace" $drivePercent
done
```I guess there's probably a better way of doing this, but this does what I wanted it to do.

---

### Post by mobilediesel on 2010-03-28
> **vickoxy said:**
> This is sort of bump again. So this is my cal line:

```
${voffset -72}${font andale mono:size=7}${color ffffff}${execpi 600 DJS=`date +%_d`; cal | sed '1d' | sed '/./!d' | sed 's/$/                     /' | fold -w 21 | sed -n '/^.\{21\}/p' | sed 's/^/${alignc -30} /' | sed /" $DJS "/s/" $DJS "/" "'${color 00A9CB}'"$DJS"'${color ffffff}'" "/}${font}
```

So, if anyone knows how/where to put/ to mark week days with different color, not default one.

Thanks

I **was** working on it when you first posted. I got distracted with other stuff offline. Here's what I came up with:

First, that calendar code can be simplified to:
```
cal | sed 's/\<'"$(date +%-d)"'\>/${color white}&${color}/'
```

To color weekends different from weekdays:
```
cal | sed '/^ *$/d' | sed -r '2,8s/^(.{18})(.{2})/\1${color red}\2${color}/' | sed -r '2,8s/^(.{0})(.{2})/\1${color red}\2${color}/'
```

Add the code for coloring current day:
```
cal | sed '/^ *$/d' | sed -r '2,8s/^(.{18})(.{2})/\1${color red}\2${color}/' | sed -r '2,8s/^(.{0})(.{2})/\1${color red}\2${color}/' | sed 's/\<'"$(date +%-d)"'\>/${color white}&${color}/'
```

Or to start the week on Monday instead of Sunday:
```
cal -m | sed '/^ *$/d' | sed -r '2,8s/^(.{0})(.{5})/\1${color red}\2${color}/' | sed 's/\<'"$(date +%-d)"'\>/${color white}&${color}/'
```

---

### Post by vickoxy on 2010-03-28
> **mobilediesel said:**
> I **was** working on it when you first posted. I got distracted with other stuff offline. Here's what I came up with:

First, that calendar code can be simplified to:
```
cal | sed 's/\<'"$(date +%-d)"'\>/${color white}&${color}/'
```

To color weekends different from weekdays:
```
cal | sed '/^ *$/d' | sed -r '2,8s/^(.{18})(.{2})/\1${color red}\2${color}/' | sed -r '2,8s/^(.{0})(.{2})/\1${color red}\2${color}/'
```

Add the code for coloring current day:
```
cal | sed '/^ *$/d' | sed -r '2,8s/^(.{18})(.{2})/\1${color red}\2${color}/' | sed -r '2,8s/^(.{0})(.{2})/\1${color red}\2${color}/' | sed 's/\<'"$(date +%-d)"'\>/${color white}&${color}/'
```

Or to start the week on Monday instead of Sunday:
```
cal -m | sed '/^ *$/d' | sed -r '2,8s/^(.{0})(.{5})/\1${color red}\2${color}/' | sed 's/\<'"$(date +%-d)"'\>/${color white}&${color}/'
```

Thanks for helping. Actually i just want to have week days names (Mo Tu We Th Fr Sa Su) colored and current day.

The second thing is - i do not need in cal the current month and date above calendar, because i placed it somewhere else.

So, on picture you can see my cal and i just want these week days  names colored.

Thanks a lot

---

### Post by mobilediesel on 2010-03-28
> **vickoxy said:**
> Thanks for helping. Actually i just want to have week days names (Mo Tu We Th Fr Sa Su) colored and current day.

The second thing is - i do not need in cal the current month and date above calendar, because i placed it somewhere else.

So, on picture you can see my cal and i just want these week days  names colored.

Thanks a lot

You're welcome. This will remove the month/year line and only color the day names:
```
cal -m | sed '1d' | sed '/^ *$/d' | sed -r '0,/./s/^(.{0})(.{5})/\1${color red}\2${color}/' | sed 's/\<'"$(date +%-d)"'\>/${color white}&${color}/'
```

---

### Post by vickoxy on 2010-03-28
> **mobilediesel said:**
> You're welcome. This will remove the month/year line and only color the day names:
```
cal -m | sed '1d' | sed '/^ *$/d' | sed -r '0,/./s/^(.{0})(.{5})/\1${color red}\2${color}/' | sed 's/\<'"$(date +%-d)"'\>/${color white}&${color}/'
```

Well, i have some issues-if i add these lines after ${execpi 600 
everything in my conky is dead/invisible after cal line. Other then that-there are only Mo and TU colored, but not the other days (neither current day) ?

---

### Post by wannabegeek on 2010-03-28
Hello all conky fans

I have been cleaning up my desktop and finally got rid of the volume and wireless indicator
icons  in the top right of my panel. 

So, I've been updating my conky to include all that info...

So far it's been easy, but I'm stuck on using ${mixer}   and ${mixerbar}
I've been reading a lot this morning and don't know what I'm missing.

I just want the default master mixer volume # and a simple bar.
I get a '0' and a empty bar that doens't repsond to changes in volumes, although
the sound gui does show a change when I press the short cut keys.



thank you,
wbg

---

### Post by mobilediesel on 2010-03-28
> **vickoxy said:**
> Well, i have some issues-if i add these lines after ${execpi 600 
everything in my conky is dead/invisible after cal line. Other then that-there are only Mo and TU colored, but not the other days (neither current day) ?

Run this in the terminal and paste the output:
```
cal -m | sed '1d' | sed '/^ *$/d' | sed -r '0,/./s/^(.{0})(.{5})/\1${color red}\2${color}/' | sed 's/\<'"$(date +%-d)"'\>/${color white}&${color}/'
```

---

### Post by vickoxy on 2010-03-28
```
mini@mini:~$ cal -m | sed '1d' | sed '/^ *$/d' | sed -r '0,/./s/^(.{0})(.{5})/\1${color red}\2${color}/' | sed 's/\<'"$(date +%-d)"'\>/${color white}&${color}/'
${color red}Mo Di${color} Mi Do Fr Sa So
 1  2  3  4  5  6  7
 8  9 10 11 12 13 14
15 16 17 18 19 20 21
22 23 24 25 26 27 ${color white}28${color}
29 30 31           
```

---

### Post by mobilediesel on 2010-03-29
See if this is closer to what you're looking for:
```
cal -m | sed '1d' | sed '/^ *$/d' | sed -r '1,8s/^(.{15})(.{5})/\1${color red}\2${color}/' | sed 's/\<'"$(date +%-d)"'\>/${color white}&${color}/'
```

---

### Post by yeleek on 2010-03-29
Submitted to Sec as its more for people with that type of interest.  

However incase people find the use of color (colour!) helpful 

[http://ubuntuforums.org/showthread.php?t=1441718](http://ubuntuforums.org/showthread.php?t=1441718)

---

### Post by vickoxy on 2010-03-29
> **mobilediesel said:**
> See if this is closer to what you're looking for:
```
cal -m | sed '1d' | sed '/^ *$/d' | sed -r '1,8s/^(.{15})(.{5})/\1${color red}\2${color}/' | sed 's/\<'"$(date +%-d)"'\>/${color white}&${color}/'
```


Actually this is what i have. Only need to change days names  colors (not the dates...) And after calendar my other stuff in conky are dead-have nothing after calendar...

Could you post what do i have to add in conky (${execpi 600... and till the end)?

---

### Post by mobilediesel on 2010-03-29
> **vickoxy said:**
> Actually this is what i have. Only need to change days names  colors (not the dates...) And after calendar my other stuff in conky are dead-have nothing after calendar...

Could you post what do i have to add in conky (${execpi 600... and till the end)?

To color just the day names:
```
${execpi 3600 cal -m | sed '1d' | sed '/^ *$/d' | sed -r '0,/./s/^(.{15})(.{5})/\1${color red}\2${color}/' | sed 's/\<'"$(date +%-d)"'\>/${color white}&${color}/'}
```

I'm not sure why conky would not display anything after the calendar, though.

---

### Post by vickoxy on 2010-03-29
> **mobilediesel said:**
> To color just the day names:
```
${execpi 3600 cal -m | sed '1d' | sed '/^ *$/d' | sed -r '0,/./s/^(.{15})(.{5})/\1${color red}\2${color}/' | sed 's/\<'"$(date +%-d)"'\>/${color white}&${color}/'}
```

I'm not sure why conky would not display anything after the calendar, though.

Now it is better-it does not crush conky. Still, can i have all names colored, not only weekend?
And second:  how to align it to center (see pict)?

Thanks

---

### Post by mobilediesel on 2010-03-29
> **vickoxy said:**
> Now it is better-it does not crush conky. Still, can i have all names colored, not only weekend?
And second:  how to align it to center (see pict)?

Thanks

```
${execpi 3600 cal -m | sed '1d' | sed '/^ *$/d' | sed -r '0,/./s/^(.{0})(.{20})/\1${color red}\2${color}/' | sed 's/\<'"$(date +%-d)"'\>/${color white}&${color}/'|sed 's/^/${alignc}/'}
```

If that doesn't properly center the calendar, change the **alignc** to **goto 100** and adjust the number from there.

---

### Post by vickoxy on 2010-03-29
> **mobilediesel said:**
> ```
${execpi 3600 cal -m | sed '1d' | sed '/^ *$/d' | sed -r '0,/./s/^(.{0})(.{20})/\1${color red}\2${color}/' | sed 's/\<'"$(date +%-d)"'\>/${color white}&${color}/'|sed 's/^/${alignc}/'}
```

If that doesn't properly center the calendar, change the **alignc** to **goto 100** and adjust the number from there.

Thanks a lot. That did it. :popcorn:

```
${voffset -72}${font andale mono:size=7}${color ffffff}${execpi 3600 cal -m | sed '1d' | sed '/^ *$/d' | sed -r '0,/./s/^(.{0})(.{20})/\1${color BFEEFC}\2${color}/' | sed 's/\<'"$(date +%-d)"'\>/${color 4CD5FF}&${color}/'|sed 's/^/${alignc -30}/'}

```

Just don´t understand those lines and where to put colors and other stuff. Once again, thanks a lot.

---

### Post by mobilediesel on 2010-03-30
> **vickoxy said:**
> Thanks a lot. That did it. :popcorn:

```
${voffset -72}${font andale mono:size=7}${color ffffff}${execpi 3600 cal -m | sed '1d' | sed '/^ *$/d' | sed -r '0,/./s/^(.{0})(.{20})/\1${color BFEEFC}\2${color}/' | sed 's/\<'"$(date +%-d)"'\>/${color 4CD5FF}&${color}/'|sed 's/^/${alignc -30}/'}

```

Just don´t understand those lines and where to put colors and other stuff. Once again, thanks a lot.

I edited the code a little bit. Nothing important so you don't need to edit yours.

Here it is with color coding to explain the different parts:
```
cal -m | [COLOR="Red"]sed '1d'[/COLOR] | [COLOR="Blue"]sed '/^ *$/d'[/COLOR] | [COLOR="Green"]sed -r '0,/./s/.*/${color BFEEFC}&${color}/'[/COLOR] | [COLOR="Brown"]sed 's/\<'"$(date +%-d)"'\>/${color 4CD5FF}&${color}/'[/COLOR]|[COLOR="Orange"]sed 's/^/${alignc -30}/'[/COLOR]
```

[COLOR="Red"]Removes the first line. (Month and year)[/COLOR]
[COLOR="Blue"]Removes any blank lines.[/COLOR]
[COLOR="Green"]The 0 means it'll only change the first line. It adds the color to the beginning and end of the line. (Names of the days of the week.)[/COLOR]
[COLOR="Brown"]Surrounds the current day number with color code.[/COLOR]
[COLOR="Orange"]Adds the alignment code to the beginning of each line.[/COLOR]

---

### Post by vickoxy on 2010-03-30
> **mobilediesel said:**
> I edited the code a little bit. Nothing important so you don't need to edit yours.

Here it is with color coding to explain the different parts:
```
cal -m | [COLOR="Red"]sed '1d'[/COLOR] | [COLOR="Blue"]sed '/^ *$/d'[/COLOR] | [COLOR="Green"]sed -r '0,/./s/.*/${color BFEEFC}&${color}/'[/COLOR] | [COLOR="Brown"]sed 's/\<'"$(date +%-d)"'\>/${color 4CD5FF}&${color}/'[/COLOR]|[COLOR="Orange"]sed 's/^/${alignc -30}/'[/COLOR]
```

[COLOR="Red"]Removes the first line. (Month and year)[/COLOR]
[COLOR="Blue"]Removes any blank lines.[/COLOR]
[COLOR="Green"]The 0 means it'll only change the first line. It adds the color to the beginning and end of the line. (Names of the days of the week.)[/COLOR]
[COLOR="Brown"]Surrounds the current day number with color code.[/COLOR]
[COLOR="Orange"]Adds the alignment code to the beginning of each line.[/COLOR]

Well, thanks-i just have to add this answer to my bookmarks. Still it is hard to know where exactly to put those values. :popcorn:

---

### Post by wannabegeek on 2010-04-01
anyone have a suggestion for making {mixer} and {mixerbar} work...
all I get is a 0 for master volume and an empty bar...

tia
wbg

[PHP]# set to yes if you want Conky to be forked in the background
background yes

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Trebuchet MS:size=10

# Text alpha when using Xft
xftalpha 0.9

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

# If own_window is yes, these window manager hints may be used
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
#minimum_size 150 5

# Maximum width
maximum_width 140

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Draw borders around graphs
draw_graph_borders no

# Stippled borders?
# stippled_borders 8

# border margins
# border_margin 2

# border width
# border_width 1

# Default colors and also border colors
default_color black
default_shade_color red
default_outline_color green

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 12
gap_y 12

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no

# variable is given either in format $variable or in ${variable}

# stuff after 'TEXT' will be formatted on screen

#  unused text
#  $sysname $kernel
#  Uptime:$alignr$uptime
#  ${time %A}$alignr${time %F}
#  hda1: ${fs_used_perc /mnt/FILES}% ${color lightgray}${fs_bar /mnt/FILES/}$color
#  Swap: $swapperc% ${color lightgray}$swapbar$color
#  Signal:$alignr${linkstatus  ath0}
#  Current:${alignr}${execi 20 /home/tonyt/scripts/.conky_ath0} Mbits/sec
#  eth2:$alignr${addr eth2}
#  ${upspeedgraph wlan0 20,130 000000 ffffff}
#  ${downspeedgraph wlan0 20,130 000000 ffffff}

TEXT

${color black}${time %e %B %G}
${color black}${time %I:%M %P}
Up-load ${upspeed wlan0} k/s
Down-Load ${downspeed wlan0}k/s${color}
RAM: $mem/$memmax 
${color darkgray}$membar$color
CPU0 ${cpu cpu1}% ${color darkgray}${cpubar cpu1}$color
CPU1 ${cpu cpu2}% ${color darkgray}${cpubar cpu2}$color
sda1: ${fs_used_perc /}% ${color darkgray}${fs_bar /}$color
Processes: $processes ${alignr}Running: $running_processes
HDD Temp ${execi 5 hddtemp /dev/sda1 | cut -c 34-36}Deg C
Battery: $battery_short
${color black}$battery_bar
Volume:${mixer} 
${color blue}${mixerbar}    [/PHP]

---

### Post by wlourf on 2010-04-07
Hi folks !

For my personal use I wrote a Lua script used to transform square image to "rounded" image (ie circle with transparency).
I also wrote a script to get images from Moon or from Earth...

From this image [[IMG]http://img62.imageshack.us/img62/6329/13851582.th.jpg[/IMG]]("http://img62.imageshack.us/i/13851582.jpg/") to this one (in a conky) [[IMG]http://img215.imageshack.us/img215/6806/earthx.th.png[/IMG]]("http://img215.imageshack.us/i/earthx.png/")


First, the script to get the moon or earth image : **get_moon_earth.sh** (to get the moon you need to pass moon as parameter). The parameters at the beginning of the script are the same as on this page : [http://www.fourmilab.ch/earthview/expert.html](http://www.fourmilab.ch/earthview/expert.html)
```
#!/bin/bash
#This script download image from Earth or from Moon (if first parameter = "moon")
#the parameters are the sames as on this page
#http://www.fourmilab.ch/earthview/expert.html
#version1.0, wlourf 07 avril 2010
#http://u-scripts.blogspot.com/


#===========début des paramètres===============
dir="/tmp/earth"

if [[ "$1" == "moon" ]]; then
    Latitude=46        #number
    NorthSouth=n    #n/s
    Longitude=0        #number
    EastWest=e        #e/w
    Altitude=401725 #altitude in kilometers (max=401725)
    #___Image___
    Image=topo         #topo,albedo
    Size=320        #number (default=320)
    ShowNight=true     #true/false
    file1=$dir/get_moon.txt        #temp file for url
    file2=$dir/moon_image        #final image
else
    #___View___
    Latitude=33       #number
    NorthSouth=n    #n/s
    Longitude=70      #number
    EastWest=e          #e/w
    Altitude=35785     #altitude in kilometers (max=35785)
    #___Image___
    Image=live         #live,marble,nasa,topo,cloudy,ir,cweather,vapour_bg,vapour
    Size=320        #number (default=320)
    ShowNight=true     #true/false
    file1=$dir/get_earth.txt    #temp file for url
    file2=$dir/earth_image        #final image
fi

#===========fin des paramètres===============

base=http://www.fourmilab.ch

#mise en forme des paramètres
if [[ "$NorthSouth" == "s" ]]; then
    NorthSouth="South"
else
    NorthSouth="North"
fi
if [[ "$EastWest" == "e" ]]; then
    EastWest="East"
else
    EastWest="West"
fi

if [[ "$ShowNight" == true ]]; then
    DayNight=""
else
    DayNight="&daynight=d"
fi
if [[ "$1" == "moon" ]]; then
    case $Image in
        "topo")    Image="MoonTopo.evif";;
        *)        Image="Moon.evif";;
    esac
else
    case $Image in
        "marble")    Image="NASA500m.evif";;
        "nasa")        Image="nasa.evif";;
        "topo")        Image="NOAAtopo.evif";;
        "clouds")    Image="cloudy.bmp";;
        "ir")        Image="irsat.bmp";;
        "cweather")    Image="wx-cmap.bmp";;
        "vapour_bg")Image="vapour_bg.bmp";;
        "vapour")    Image="vapour.bmp";;
        *)            Image="learth.evif";;
    esac
fi

#get the url
mkdir -p $dir
cd $dir

GET http://www.fourmilab.ch/cgi-bin/Earth?lat=$Latitude\&ns=l$NorthSouth\&lon=$Longitude\&ew=$EastWest\&alt=$Altitude$DayNight\&img=$Image\&imgsize=$Size > $file1

#extract the line of the image
match="<img src="
url_line=""
while read line
do
    if [[ "$line" =~ "${match}" ]]; then
        url_line=$line
        break
    fi
done <  $file1

if [[ "$url_line" == "" ]]; then
    echo "no url matched"
    exit
fi

#extract the link of the image and save the image
begin="<img src=\""
end="\" ismap"

a=$(($(expr "$url_line" : ".*$begin")))
b=$(($(expr "$url_line" : ".*$end")-$a-${#end}))
url_image=${url_line:$a:$b}
GET $base$url_image > $file2

exit
```The Lua script **square_to_round.lua **: 
```
--[[ SQUARE_TO_ROUND WIDGET by Wlourf (07 April 2010, version 1.0.1)
http://u-scripts.blogspot.com/

This widget display a rounded image on your conky from a square image only.

Parameters are
filename        --name of picture to use
xc,yc           --coordinates of the center of circle relative to top left corner of conky window
radius          --radius of the circle
angle           --angle of rotation in degrees
radius_crop        --percentage of original image to keep (0-100)
period            --convert input image to output image every 'period' seconds

]]

require 'cairo'
require 'imlib2'


function convert_square(fileIn,fileOut,radius,angle,radius_crop)
    --convert Input file from jpg to png, scale it and rotate it
    local imageInput = imlib_load_image(fileIn)
    local out_size = radius*2/(radius_crop/100)
    imlib_context_set_image(imageInput)
    w = imlib_image_get_width();
    h = imlib_image_get_height();
    imlib_image_set_format("png")
    buffer = imlib_create_image(out_size,out_size);
    imlib_context_set_image(buffer);

    imlib_blend_image_onto_image(imageInput, 0, 
                                               0, 0, w, h, 
                                               0,0, out_size,out_size)
    rot_img=imlib_create_rotated_image(angle*math.pi/180)
    imlib_context_set_image(rot_img)  
    imlib_save_image(fileOut)
    imlib_free_image()
    
    imlib_context_set_image(buffer)
    imlib_free_image()
    imlib_context_set_image(imageInput)
    imlib_free_image()
end

function crop_square_to_round(filename,xc,yc,radius)
    local surface = cairo_image_surface_create_from_png(filename)
    local img_w = cairo_image_surface_get_width (surface);
    
    local cw,ch = conky_window.width, conky_window.height
    local cs=cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, cw,ch)
    local cr=cairo_create(cs)
    cairo_translate(cr,xc-img_w/2,yc-img_w/2)
    cairo_arc (cr, img_w/2,img_w/2, radius, 0, 2*math.pi)
    cairo_clip (cr)
    cairo_new_path (cr)    
    cairo_set_source_surface (cr, surface, 0, 0)

    cairo_paint (cr)
    cairo_destroy(cr)
    cairo_surface_destroy (cs)
    cairo_surface_destroy (surface)
    
end

function display_round(filename,xc,yc,radius,angle,radius_crop,period)
    if conky_window == nil then return end

    if tonumber(conky_parse('${updates}')) <2  then return end
    local filepng = filename .. ".png"
    local actual_time  = os.time()
    
    if last_time == nil then last_time=0 end
    local actual_img = io.open(filepng,"r")    
    if  last_time+period < actual_time or last_time == 0 or actual_img == nil then
        print ('convert image ' .. filename)
        convert_square(filename,filepng,radius,angle,radius_crop)
        last_time=actual_time
    end
    crop_square_to_round(filepng,xc,yc,radius)
    io.close()
end


--[[END OF SQUARE TO ROUND WIDGET]]

function conky_main(filename)
    if conky_window == nil then return end
    display_round(filename,
                275,275,120,  --xc,yc,radius
                5,            --angle
                98,              --radius_crop (1-100)
                3600          --period
                
    )
end

```And the **conkyrc** 
```
# -- Conky settings -- #
background no
update_interval 10

cpu_avg_samples 2
net_avg_samples 2

override_utf8_locale yes

double_buffer yes
no_buffers yes

text_buffer_size 2048
imlib_cache_size 0

# -- Window specifications -- #

own_window yes
#own_window_type normal
own_window_transparent yes
#own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below
own_window_colour FFFFFF
own_window_title square to round

border_inner_margin 0
border_outer_margin 0

minimum_size 450 550

alignment tm
gap_y 0
gap_x 0

# -- Graphics settings -- #
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no

# -- Text settings -- #
use_xft yes
xftfont Santana:size=12
xftalpha 0

uppercase no

default_color 000000
text_buffer_size 2048 
imlib_cache_size 0 
#--- LUA ---
lua_load ~/wip/earth/square_to_round.lua 
#first parameter is the square image to use
lua_draw_hook_pre main /tmp/earth/earth_image

TEXT
${execpi 3600 ~/wip/earth/get_moon_earth.sh earth}

```And if you are inspired, you can get amazing conkys like this one :
[[IMG]http://img101.imageshack.us/img101/8289/moon2.th.png[/IMG]]("http://img101.imageshack.us/i/moon2.png/")


Happy conkying :P

EDIT : a more simple way to have rounded images is here, with a script from larryni : [http://wwww.ubuntuforums.org/showpost.php?p=9541241&postcount=13076](http://wwww.ubuntuforums.org/showpost.php?p=9541241&postcount=13076)
You need the 2 masks from the above topic.

I use it now in my script, so it gives that :
```
#!/bin/bash
#This script download image from Earth or from Moon (if first parameter = "moon")
#the parameters are the sames as on this page
#http://www.fourmilab.ch/earthview/expert.html
#version1.1, wlourf 14 sept. 2010
#http://u-scripts.blogspot.com/
#http://ubuntuforums.org/showpost.php?p=9088516&postcount=244

#http://ubuntuforums.org/showpost.php?p=8117609&postcount=9846
#http://wwww.ubuntuforums.org/showpost.php?p=9541241&postcount=13076

#first parameter moon to display moon, other or mssing = earth

#===========début des paramètres===============
dir="/tmp/earth"
dirmasks="/home/ll/conky/earth"

if [[ "$1" == "moon" ]]; then
    Latitude=47.243055556        #number
    NorthSouth=n    #n/s
    Longitude=6.021944444        #number
    EastWest=e        #e/w
    Altitude=401725 #altitude in kilometers (max=401725)
    #___Image___
    Image=topo         #topo,albedo
    Size=100        #number (default=320)
    ShowNight=true     #true/false
    file1=$dir/get_moon.txt        #temp file for url
    file2=$dir/moon_image        #final image
    basename="moon"
else
    #___View___
    Latitude=47.243055556       #number
    NorthSouth=n    #n/s
    Longitude=6.021944444      #number
    EastWest=e          #e/w
    Altitude=35785     #altitude in kilometers (max=35785)
    #___Image___
    Image=live         #live,marble,nasa,topo,cloudy,ir,cweather,vapour_bg,vapour
    Size=100            #number (default=320)
    ShowNight=true     #true/false
    file1=$dir/get_earth.txt    #temp file for url
    file2=$dir/earth_image        #final image
    basename="earth"
fi

#===========fin des paramètres===============

base=http://www.fourmilab.ch

#mise en forme des paramètres
if [[ "$NorthSouth" == "s" ]]; then
    NorthSouth="South"
else
    NorthSouth="North"
fi
if [[ "$EastWest" == "e" ]]; then
    EastWest="East"
else
    EastWest="West"
fi

if [[ "$ShowNight" == true ]]; then
    DayNight=""
else
    DayNight="&daynight=d"
fi
if [[ "$1" == "moon" ]]; then
    case $Image in
        "topo")    Image="MoonTopo.evif";;
        *)        Image="Moon.evif";;
    esac
else
    case $Image in
        "marble")    Image="NASA500m.evif";;
        "nasa")        Image="nasa.evif";;
        "topo")        Image="NOAAtopo.evif";;
        "clouds")    Image="cloudy.bmp";;
        "ir")        Image="irsat.bmp";;
        "cweather")    Image="wx-cmap.bmp";;
        "vapour_bg")Image="vapour_bg.bmp";;
        "vapour")    Image="vapour.bmp";;
        *)            Image="learth.evif";;
    esac
fi

#get the url
mkdir -p $dir
cd $dir

wget -q http://www.fourmilab.ch/cgi-bin/Earth?lat=$Latitude\&ns=l$NorthSouth\&lon=$Longitude\&ew=$EastWest\&alt=$Altitude$DayNight\&img=$Image\&imgsize=$Size -O $file1

#extract the line of the image
url_image="$(cat $file1 | grep "<img src=" | awk -F'\"' '{print $2}' )"

if [[ "$url_image" == "" ]]; then
    echo "no url matched"
    exit
fi

#extract the link of the image and save the image
wget -q  $base$url_image -O $file2

convert $file2 -colorspace Gray $dirmasks/overlay$Size.png -compose HardLight -composite $dirmasks/mask$Size.png -alpha off -compose CopyOpacity -composite $dir/$basename-out.png

#convert $file2  -colorspace Gray $dirmasks/mask$Size.png -alpha off -compose CopyOpacity -composite $dir/$basename-out.png

exit 0 
```

---

### Post by dmillerct on 2010-04-07
> **wlourf said:**
> Hi folks !

For my personal use I wrote a Lua script used to transform square image to "rounded" image (ie circle with transparency).
I also wrote a script to get images from Moon or from Earth...

From this image [[IMG]http://img62.imageshack.us/img62/6329/13851582.th.jpg[/IMG]]("http://img62.imageshack.us/i/13851582.jpg/") to this one (in a conky) [[IMG]http://img215.imageshack.us/img215/6806/earthx.th.png[/IMG]]("http://img215.imageshack.us/i/earthx.png/")


First, the script to get the moon or earth image : **get_moon_earth.sh** (to get the moon you need to pass moon as parameter). The parameters at the beginning of the script are the same as on this page : [http://www.fourmilab.ch/earthview/expert.html]("http://www.fourmilab.ch/earthview/expert.html,")
```
#!/bin/bash
#This script download image from Earth or from Moon (if first parameter = "moon")
#the parameters are the sames as on this page
#http://www.fourmilab.ch/earthview/expert.html
#version1.0, wlourf 07 avril 2010
#http://u-scripts.blogspot.com/


#===========début des paramètres===============
dir="/tmp/earth"

if [[ "$1" == "moon" ]]; then
    Latitude=46        #number
    NorthSouth=n    #n/s
    Longitude=0        #number
    EastWest=e        #e/w
    Altitude=401725 #altitude in kilometers (max=401725)
    #___Image___
    Image=topo         #topo,albedo
    Size=320        #number (default=320)
    ShowNight=true     #true/false
    file1=$dir/get_moon.txt        #temp file for url
    file2=$dir/moon_image        #final image
else
    #___View___
    Latitude=33       #number
    NorthSouth=n    #n/s
    Longitude=70      #number
    EastWest=e          #e/w
    Altitude=35785     #altitude in kilometers (max=35785)
    #___Image___
    Image=live         #live,marble,nasa,topo,cloudy,ir,cweather,vapour_bg,vapour
    Size=320        #number (default=320)
    ShowNight=true     #true/false
    file1=$dir/get_earth.txt    #temp file for url
    file2=$dir/earth_image        #final image
fi

#===========fin des paramètres===============

base=http://www.fourmilab.ch

#mise en forme des paramètres
if [[ "$NorthSouth" == "s" ]]; then
    NorthSouth="South"
else
    NorthSouth="North"
fi
if [[ "$EastWest" == "e" ]]; then
    EastWest="East"
else
    EastWest="West"
fi

if [[ "$ShowNight" == true ]]; then
    DayNight=""
else
    DayNight="&daynight=d"
fi
if [[ "$1" == "moon" ]]; then
    case $Image in
        "topo")    Image="MoonTopo.evif";;
        *)        Image="Moon.evif";;
    esac
else
    case $Image in
        "marble")    Image="NASA500m.evif";;
        "nasa")        Image="nasa.evif";;
        "topo")        Image="NOAAtopo.evif";;
        "clouds")    Image="cloudy.bmp";;
        "ir")        Image="irsat.bmp";;
        "cweather")    Image="wx-cmap.bmp";;
        "vapour_bg")Image="vapour_bg.bmp";;
        "vapour")    Image="vapour.bmp";;
        *)            Image="learth.evif";;
    esac
fi

#get the url
mkdir -p $dir
cd $dir

GET http://www.fourmilab.ch/cgi-bin/Earth?lat=$Latitude\&ns=l$NorthSouth\&lon=$Longitude\&ew=$EastWest\&alt=$Altitude$DayNight\&img=$Image\&imgsize=$Size > $file1

#extract the line of the image
match="<img src="
url_line=""
while read line
do
    if [[ "$line" =~ "${match}" ]]; then
        url_line=$line
        break
    fi
done <  $file1

if [[ "$url_line" == "" ]]; then
    echo "no url matched"
    exit
fi

#extract the link of the image and save the image
begin="<img src=\""
end="\" ismap"

a=$(($(expr "$url_line" : ".*$begin")))
b=$(($(expr "$url_line" : ".*$end")-$a-${#end}))
url_image=${url_line:$a:$b}
GET $base$url_image > $file2

exit
```The Lua script **square_to_round.lua **: 
```
--[[ SQUARE_TO_ROUND WIDGET by Wlourf (07 April 2010, version 1.0.1)
http://u-scripts.blogspot.com/

This widget display a rounded image on your conky from a square image only.

Parameters are
filename        --name of picture to use
xc,yc           --coordinates of the center of circle relative to top left corner of conky window
radius          --radius of the circle
angle           --angle of rotation in degrees
radius_crop        --percentage of original image to keep (0-100)
period            --convert input image to output image every 'period' seconds

]]

require 'cairo'
require 'imlib2'


function convert_square(fileIn,fileOut,radius,angle,radius_crop)
    --convert Input file from jpg to png, scale it and rotate it
    local imageInput = imlib_load_image(fileIn)
    local out_size = radius*2/(radius_crop/100)
    imlib_context_set_image(imageInput)
    w = imlib_image_get_width();
    h = imlib_image_get_height();
    imlib_image_set_format("png")
    buffer = imlib_create_image(out_size,out_size);
    imlib_context_set_image(buffer);

    imlib_blend_image_onto_image(imageInput, 0, 
                                               0, 0, w, h, 
                                               0,0, out_size,out_size)
    rot_img=imlib_create_rotated_image(angle*math.pi/180)
    imlib_context_set_image(rot_img)  
    imlib_save_image(fileOut)
    imlib_free_image()
    
    imlib_context_set_image(buffer)
    imlib_free_image()
    imlib_context_set_image(imageInput)
    imlib_free_image()
end

function crop_square_to_round(filename,xc,yc,radius)
    local surface = cairo_image_surface_create_from_png(filename)
    local img_w = cairo_image_surface_get_width (surface);
    
    local cw,ch = conky_window.width, conky_window.height
    local cs=cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, cw,ch)
    local cr=cairo_create(cs)
    cairo_translate(cr,xc-img_w/2,yc-img_w/2)
    cairo_arc (cr, img_w/2,img_w/2, radius, 0, 2*math.pi)
    cairo_clip (cr)
    cairo_new_path (cr)    
    cairo_set_source_surface (cr, surface, 0, 0)

    cairo_paint (cr)
    cairo_destroy(cr)
    cairo_surface_destroy (cs)
    cairo_surface_destroy (surface)
    
end

function display_round(filename,xc,yc,radius,angle,radius_crop,period)
    if conky_window == nil then return end

    if tonumber(conky_parse('${updates}')) <2  then return end
    local filepng = filename .. ".png"
    local actual_time  = os.time()
    
    if last_time == nil then last_time=0 end
    local actual_img = io.open(filepng,"r")    
    if  last_time+period < actual_time or last_time == 0 or actual_img == nil then
        print ('convert image ' .. filename)
        convert_square(filename,filepng,radius,angle,radius_crop)
        last_time=actual_time
    end
    crop_square_to_round(filepng,xc,yc,radius)
    io.close()
end


--[[END OF SQUARE TO ROUND WIDGET]]

function conky_main(filename)
    if conky_window == nil then return end
    display_round(filename,
                275,275,120,  --xc,yc,radius
                5,            --angle
                98,              --radius_crop (1-100)
                3600          --period
                
    )
end

```And the **conkyrc** 
```
# -- Conky settings -- #
background no
update_interval 10

cpu_avg_samples 2
net_avg_samples 2

override_utf8_locale yes

double_buffer yes
no_buffers yes

text_buffer_size 2048
imlib_cache_size 0

# -- Window specifications -- #

own_window yes
#own_window_type normal
own_window_transparent yes
#own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below
own_window_colour FFFFFF
own_window_title square to round

border_inner_margin 0
border_outer_margin 0

minimum_size 450 550

alignment tm
gap_y 0
gap_x 0

# -- Graphics settings -- #
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no

# -- Text settings -- #
use_xft yes
xftfont Santana:size=12
xftalpha 0

uppercase no

default_color 000000
text_buffer_size 2048 
imlib_cache_size 0 
#--- LUA ---
lua_load ~/wip/earth/square_to_round.lua 
#first parameter is the square image to use
lua_draw_hook_pre main /tmp/earth/earth_image

TEXT
${execpi 3600 ~/wip/earth/get_moon_earth.sh earth}

```And if you are inspired, you can get amazing conkys like this one :
[[IMG]http://img101.imageshack.us/img101/8289/moon2.th.png[/IMG]]("http://img101.imageshack.us/i/moon2.png/")

The 3 files are in the attachment.

Happy conkying :P

You don't cease to amaze me with the stuff you are doing with LUA. Keep it up!

---

### Post by wlourf on 2010-04-07
> **dmillerct said:**
> You don't cease to amaze me with the stuff you are doing with LUA. Keep it up!
Thanks dmillerct, and it's a pleasure to see captures around with some of my scripts:)
And I didn't start to use conky 1.8.0 ... better setup are coming ;-)

---

### Post by zet120 on 2010-04-08
Great script
Thanks.

[[IMG]http://img511.imageshack.us/img511/2259/ziemiad.th.png[/IMG]](http://img511.imageshack.us/i/ziemiad.png/)

---

### Post by Psumi on 2010-04-08
Too bad I can't use lua scripts :(

I can't compile 1.7.2 for debian: [http://ubuntuforums.org/showthread.php?t=1441834](http://ubuntuforums.org/showthread.php?t=1441834)

---

### Post by wlourf on 2010-04-08
> **wannabegeek said:**
> anyone have a suggestion for making {mixer} and {mixerbar} work...
all I get is a 0 for master volume and an empty bar...

tia
wbg


Hi, do you have ALSA mixer  enabled in your conky, type conky -v to check.
I am compiling version 1.8.0 and ALSA is not enabled by default, so ${mixer} doesn't work anymore ...
I tried to compile conky with --enabled-alsa but without success, If someone can help :)

---

### Post by wlourf on 2010-04-08
> **Psumi said:**
> Too bad I can't use lua scripts :(

I can't compile 1.7.2 for debian: [http://ubuntuforums.org/showthread.php?t=1441834](http://ubuntuforums.org/showthread.php?t=1441834)
Did you try last version 1.8.0 :
[http://sourceforge.net/projects/conky/files/conky/](http://sourceforge.net/projects/conky/files/conky/)
there are some deb for Ubuntu if you use it :
[https://launchpad.net/~norsetto/+archive/ppa/+packages]("https://launchpad.net/%7Enorsetto/+archive/ppa/+packages")

(I didn't test them )

---

### Post by ProNux on 2010-04-11
> **wlourf said:**
> Hi all,

While I was working on an equalizer widget, I tried an audio equalizer for conky. Well, it was easy because the work was already done for a screenlet for gnome (Impulse):
[https://launchpad.net/impulse.bzr](https://launchpad.net/impulse.bzr)

So the work was only to adapt scripts from python to lua. I've done it for two "themes" default and circle like on the picture.

If you want to try it, you have to set the path in the conkyrc (all variables are set in conkyrc so there is no need to make any changes in the lua script)

And you need to download the C library from the Impulse web site :
[http://gnome-look.org/content/show.php/?content=99383](http://gnome-look.org/content/show.php/?content=99383)
just copy impulse.so and libimpulse.so into the script folder.

the Lua script call the python script, in fact I use this line because i didn't find a better way to do it, so if you have any ideas !
conky_parse('${exec python impulse.py'}')

In the tar.gz, there is the conkyrc, the lua and python scripts and the two librairies .so.

If you have any question, don't hesitate.

Edit 28 Feb. 2010 : with the help of the auhor of Impulse, I managed to make something faster ! You can see [here]("http://www.youtube.com/watch?v=hP9Wt7YKoHM") in action but the sound is crap, sorry for your ears...
I also added peaks like on the video and it is possible to use this widget with the bargraph widget I made a few weeks ago

Edit 10 March 2010 : the conkyrc can be called with an absolute path.
I added last version of the bargraph widget which can be drawn on a circular way.
And another [video]("http://www.youtube.com/watch?v=rcM9nTKeC74&feature=channel") with better sound
Does this work on karmic 64-bit?  Thanks

---

### Post by wlourf on 2010-04-11
> **ProNux said:**
> Does this work on karmic 64-bit?  Thanks
Don't know, but why not ?! You need pulse audio...

---

### Post by wlourf on 2010-04-13
Hi all, another widget in Lua for Conky :)

I needed it to display available space of all mounted drives on my computer on a fancy way. It's a pie chart and each sector of the pie displays a partition (each sector is proportional to the total space of the mounted drives). And each sector is filled according to the used space of the drive.
Of course, the widget can display some other informations (cpu, ram ...)

I think you will better understand with pictures attached !

You need conky 1.8.0 because the script use the **cairo_text_extents** function for text alignment.
The function takes some parameters :
```
tableV            - table of labels and values {{label1,value,max,convert to Go-Mo-Ko units or unit}, {label2,value,max,convert to Go-Mo-Ko units or unit}, ...}
xc                - x center of the pie
yc                - y center of the pie
int_radius         - internal radius
radius            - external radius
first_angle        - first angle of the pie
last_angle        - last angle of the pie
proportional    - display proportional sectors (true/false)
tablebg            - table of background colours ans alpha {{0xFF0000,1}, {0x00FF00,1}, ...}
tablefg            - table of background colours ans alpha {{0xFF0000,1}, {0x00FF00,1}, ...}
gradient_effect    - gradient effect (true/false)
show_text        - display text (true/false)
line_lgth        - length for horizontal line (from radius to end of line)
line_space        - vertical space between two lines
line_width        - width of line
extend_line        - grow up the line (true/false) if length of text> line_lgth
txt_font        - font
font_size        - font size
font_color        - font color
font_alpha        - font alpha
txt_offset        - space between text and line
txt_format        - string for formatting text, possibles values are
                  &l for label
                  &o for occupied percentage
                  &f for free percentage
                  &v for occupied value
                  &n for free value (non-occupied)    
                  &m for max value
                  &p for percentage value of full graph        
nb_decimals        - number of decimals for numbers
```Theses parameters are explained on this page, with pictures : 
[http://u-scripts.blogspot.com/2010/04/pie-chart-widget.html](http://u-scripts.blogspot.com/2010/04/pie-chart-widget.html)

Voilà !

Edit 15/05/2010 : v1.1 The parameters are set in a table, most of them are optional, it is more easy to set up the script.
Added a parameter "type_arc" to display values like a ring.
With old script, the filling was radial, now it can be also like a ring, as you can see on the two red arcs
Edit 29/05/2010 : v1.2 added some parameters
Edit 26/06/2010 : v1.21 minor corrections
Last version of the script is now available on [deviantArt]("http://wlourf.deviantart.com/gallery/#/d2qo9sz")

---

### Post by Crinos512 on 2010-04-13
> **mobilediesel said:**
> I edited the code a little bit. Nothing important so you don't need to edit yours.

Here it is with color coding to explain the different parts:
```
cal -m | [COLOR="Red"]sed '1d'[/COLOR] | [COLOR="Blue"]sed '/^ *$/d'[/COLOR] | [COLOR="Green"]sed -r '0,/./s/.*/${color BFEEFC}&${color}/'[/COLOR] | [COLOR="Brown"]sed 's/\<'"$(date +%-d)"'\>/${color 4CD5FF}&${color}/'[/COLOR]|[COLOR="Orange"]sed 's/^/${alignc -30}/'[/COLOR]
```

[COLOR="Red"]Removes the first line. (Month and year)[/COLOR]
[COLOR="Blue"]Removes any blank lines.[/COLOR]
[COLOR="Green"]The 0 means it'll only change the first line. It adds the color to the beginning and end of the line. (Names of the days of the week.)[/COLOR]
[COLOR="Brown"]Surrounds the current day number with color code.[/COLOR]
[COLOR="Orange"]Adds the alignment code to the beginning of each line.[/COLOR]

***edited for least number of program calls:**

```
cal | [COLOR="Brown"]sed -r '0,/./s/.*/${color BFEEFC}&${color}/'[/COLOR]| [COLOR="Purple"]sed -e '1d' -e '/^ *$/d' -e 's/\<'"$(date +%-d)"'\>/${color 4CD5FF}&${color}/' -e 's/^/${alignc -30}/'[/COLOR]
```

[COLOR="Brown"]Surrounds the current day number with color code.[/COLOR]
[COLOR="Purple"]Performs all other formating[/COLOR]

---

### Post by mobilediesel on 2010-04-14
> **Crinos512 said:**
> ***edited for least number of program calls:**

```
cal | [COLOR="Brown"]sed -r '0,/./s/.*/${color BFEEFC}&${color}/'[/COLOR]| [COLOR="Purple"]sed -e '1d' -e '/^ *$/d' -e 's/\<'"$(date +%-d)"'\>/${color 4CD5FF}&${color}/' -e 's/^/${alignc -30}/'[/COLOR]
```

[COLOR="Brown"]Surrounds the current day number with color code.[/COLOR]
[COLOR="Purple"]Performs all other formating[/COLOR]

I should have thought of that!

You did make it one too few program calls:
```
cal | sed '1d' | sed -r '0,/./s/.*/${color BFEEFC}&${color}/' | sed -e '/^ *$/d' -e 's/\<'"$(date +%-d)"'\>/${color 4CD5FF}&${color}/' -e 's/^/${alignc -30}/'
```

The **sed -r** was coloring the first line which was then getting deleted by the **-e '1d'**.

If only **-e** and **-r** could be combined in the same command. I've tried and it tells me ```
sed: can't read 0,/./s/.*/${color BFEEFC}&${color}/: No such file or directory
```

---

### Post by Crinos512 on 2010-04-14
oops. :D

---

### Post by radoshow on 2010-04-14
[IMG]http://picasaweb.google.com/radoshow/lofKP#5460072081359410930[/IMG]Bravo script is perfect.
[IMG]http://picasaweb.google.com/radoshow/lofKP#5460072081359410930[/IMG]
how can I show it without this window.

---

### Post by radoshow on 2010-04-14
> **radoshow said:**
> [IMG]http://picasaweb.google.com/radoshow/lofKP#5460072081359410930[/IMG]Bravo script is perfect.
[IMG]http://picasaweb.google.com/radoshow/lofKP#5460072081359410930[/IMG]
how can I show it without this window.

I fix it.Change this line:
```
own_window [COLOR=red]yes[/COLOR] with [COLOR=red]no[/COLOR]
```:lolflag:

---

### Post by wlourf on 2010-04-14
@radoshow

or uncomment theses two lines :
```
own_window_type normal
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below

```and don't forget to set up latitude and longitude in the Lua script :
```
Latitude=46     #number
NorthSouth=n    #n/s
Longitude=0     #number
EastWest=e      #e/w

```hth

---

### Post by mobilediesel on 2010-04-15
> **Crinos512 said:**
> oops. :D

Hey, even with one error it was a big improvement having one sed command run several filters.

---

### Post by wannabegeek on 2010-04-17
@ wlourf

> **wlourf said:**
> Hi, do you have ALSA mixer  enabled in your conky, type conky -v to check.
I am compiling version 1.8.0 and ALSA is not enabled by default, so ${mixer} doesn't work anymore ...
I tried to compile conky with --enabled-alsa but without success, If someone can help :)

thanks for replying...

I ran conky -v  and see ALSA listed...

It seems that a few others have had this problem with Thinkpads....

wbg

---

### Post by Jaa(c) on 2010-05-31
> **wlourf said:**
> Hi all, another widget in Lua for Conky :)
...
Hey,
what all do I need to make this work? I install those conky and lua things, but Im still probably missing sth..
I have openSUSE 11.2 (yeah, I know this is Ubuntu forum :)), KDE 4.3, conky 1.8

If I run concy with your config I end like this
```
Conky: llua_load: cannot open /home/jaa/.config/openbox/bureau/piechart.lua: No such file or directory
Conky: desktop window (4400084) is subwindow of root window (ff)
Conky: window type - desktop
Conky: drawing to created window (0x5c00001)
Conky: drawing to double buffer
Conky: llua_do_call: function conky_main_pie execution failed: attempt to call a nil value

```So I've created the directory and put the file in there, and the problem is:
```
Conky: llua_load: /home/jaa/.config/openbox/bureau/piechart.lua:16: module 'cairo' not found:
        no field package.preload['cairo']
        no file './cairo.lua'
        no file '/usr/local/share/lua/5.1/cairo.lua'
        no file '/usr/local/share/lua/5.1/cairo/init.lua'
        no file '/usr/local/lib/lua/5.1/cairo.lua'
        no file '/usr/local/lib/lua/5.1/cairo/init.lua'
        no file '/usr/lib/conky/libcairo.so'
        no file './cairo.so'
        no file '/usr/local/lib/lua/5.1/cairo.so'
        no file '/usr/local/lib/lua/5.1/loadall.so'
```

Thaks for your advice...

---

### Post by wlourf on 2010-05-31
hello jaa-c !
Obviously you need cairo : you have to compile conky with cairo support. I don't know Suse but you can compile the source from conky site.
Here is the return of conky -v for my PC for example :

```
Conky 1.8.0 compiled Thu Apr  8 23:43:57 CEST 2010 for Linux 2.6.28-18-generic (i686)

Compiled in features:

System config file: /usr/local/etc/conky/conky.conf
Package library path: /usr/local/lib/conky

 X11:
  * Xdamage extension
  * XDBE (double buffer extension)
  * Xft
  * ARGB visual

 Music detection:
  * MPD
  * MOC

 General:
  * math
  * hddtemp
  * portmon
  * Curl
  * RSS
  * nvidia
  * config-output
  * Imlib2
  * apcupsd
  * iostats
  * ncurses
  * Lua

  Lua bindings:
   * Cairo
   * Imlib2

```I just check, you have to compile with this option at least:
```
./configure --enable-lua-cairo
```Here, on ubuntu, we have a package conky-all and it works on first start :)


Goog luck

---

### Post by Jaa(c) on 2010-05-31
> **wlourf said:**
> I just check, you have to compile with this option at least:
```
./configure --enable-lua-cairo
```Here, on ubuntu, we have a package conky-all and it works on first start :)

OK, we dont have this package... so, I tried to compile conky from source and it required tolua++. You need scons to compile tolua++, but that doesn't work for some reason... :D
I found similar problem [here]("http://linux-hardcore.com/forum/index.php?action=printpage;topic=2564.0"), but the solution doesn't work for me... Well, I'll try in the morning :)

---

### Post by ddnev45 on 2010-05-31
> **Jaa(c) said:**
> OK, we dont have this package... so, I tried to compile conky from source and it required tolua++. You need scons to compile tolua++, but that doesn't work for some reason... :D
I found similar problem [here]("http://linux-hardcore.com/forum/index.php?action=printpage;topic=2564.0"), but the solution doesn't work for me... Well, I'll try in the morning :)

This might help you out:

[compile tolua with scons.]("http://ubuntuforums.org/showpost.php?p=8152311&postcount=10010")

---

### Post by wlourf on 2010-06-01
> **Jaa(c) said:**
> OK, we dont have this package... so, I tried to compile conky from source and it required tolua++. You need scons to compile tolua++, but that doesn't work for some reason... :D
I found similar problem [here]("http://linux-hardcore.com/forum/index.php?action=printpage;topic=2564.0"), but the solution doesn't work for me... Well, I'll try in the morning :)
Well it's now out my skills !:???: Maybe, try to ask on a Suse forum.

---

### Post by Jaa(c) on 2010-06-01
OK, so I've solved my conky, cairo and lua problems, yet your script doesn't work :)
Guess problem is somwhere in sensors....
```
jaa@jaa-ntb:~> conky
Conky: desktop window (4400084) is subwindow of root window (ff)
Conky: window type - desktop                                    
Conky: drawing to created window (0x5600001)                    
Conky: drawing to double buffer                                 
ERROR: Can't get value of subfeature temp4_input: Can't read    
ERROR: Can't get value of subfeature temp6_input: Can't read    
ERROR: Can't get value of subfeature temp8_input: Can't read    
ERROR: Can't get value of subfeature temp12_input: Can't read   
ERROR: Can't get value of subfeature temp13_input: Can't read   
ERROR: Can't get value of subfeature temp14_input: Can't read   
ERROR: Can't get value of subfeature temp15_input: Can't read   
ERROR: Can't get value of subfeature temp16_input: Can't read
... 
```

```
jaa@jaa-ntb:~> sensors                                          
acpitz-virtual-0                                                
Adapter: Virtual device                                         
temp1:       +47.0°C  (crit = +127.0°C)                         
temp2:       +41.0°C  (crit = +100.0°C)                         

thinkpad-isa-0000
Adapter: ISA adapter
fan1:       2465 RPM
temp1:       +47.0°C                                    
temp2:       +38.0°C                                    
temp3:       +36.0°C                                    
ERROR: Can't get value of subfeature temp4_input: Can't read
temp4:        +0.0°C                                        
temp5:       +50.0°C                                        
ERROR: Can't get value of subfeature temp6_input: Can't read
temp6:        +0.0°C                                        
temp7:       +28.0°C
ERROR: Can't get value of subfeature temp8_input: Can't read
temp8:        +0.0°C
temp9:       +36.0°C
temp10:      +43.0°C
temp11:      +44.0°C
ERROR: Can't get value of subfeature temp12_input: Can't read
temp12:       +0.0°C
ERROR: Can't get value of subfeature temp13_input: Can't read
temp13:       +0.0°C
ERROR: Can't get value of subfeature temp14_input: Can't read
temp14:       +0.0°C
ERROR: Can't get value of subfeature temp15_input: Can't read
temp15:       +0.0°C
ERROR: Can't get value of subfeature temp16_input: Can't read
temp16:       +0.0°C

```

---

### Post by wlourf on 2010-06-01
> **Jaa(c) said:**
> OK, so I've solved my conky, cairo and lua problems, yet your script doesn't work :)
Guess problem is somwhere in sensors....
```
jaa@jaa-ntb:~> conky
Conky: desktop window (4400084) is subwindow of root window (ff)
Conky: window type - desktop                                    
Conky: drawing to created window (0x5600001)                    
Conky: drawing to double buffer                                 
ERROR: Can't get value of subfeature temp4_input: Can't read    
ERROR: Can't get value of subfeature temp6_input: Can't read    
ERROR: Can't get value of subfeature temp8_input: Can't read    
ERROR: Can't get value of subfeature temp12_input: Can't read   
ERROR: Can't get value of subfeature temp13_input: Can't read   
ERROR: Can't get value of subfeature temp14_input: Can't read   
ERROR: Can't get value of subfeature temp15_input: Can't read   
ERROR: Can't get value of subfeature temp16_input: Can't read
... 
``````
jaa@jaa-ntb:~> sensors                                          
acpitz-virtual-0                                                
Adapter: Virtual device                                         
temp1:       +47.0°C  (crit = +127.0°C)                         
temp2:       +41.0°C  (crit = +100.0°C)                         

thinkpad-isa-0000
Adapter: ISA adapter
fan1:       2465 RPM
temp1:       +47.0°C                                    
temp2:       +38.0°C                                    
temp3:       +36.0°C                                    
ERROR: Can't get value of subfeature temp4_input: Can't read
temp4:        +0.0°C                                        
temp5:       +50.0°C                                        
ERROR: Can't get value of subfeature temp6_input: Can't read
temp6:        +0.0°C                                        
temp7:       +28.0°C
ERROR: Can't get value of subfeature temp8_input: Can't read
temp8:        +0.0°C
temp9:       +36.0°C
temp10:      +43.0°C
temp11:      +44.0°C
ERROR: Can't get value of subfeature temp12_input: Can't read
temp12:       +0.0°C
ERROR: Can't get value of subfeature temp13_input: Can't read
temp13:       +0.0°C
ERROR: Can't get value of subfeature temp14_input: Can't read
temp14:       +0.0°C
ERROR: Can't get value of subfeature temp15_input: Can't read
temp15:       +0.0°C
ERROR: Can't get value of subfeature temp16_input: Can't read
temp16:       +0.0°C

```

OK, if you use the script from post 253, yes it uses sensors, you can look in the Lua script where sensors is used and adapt lines to your config:
Example, my sensors :
```
Case Fan:      0 RPM  (min =   78 RPM, div = 128)  ALARM
CPU Fan:    1081 RPM  (min =  803 RPM, div = 8)
Aux Fan:       0 RPM  (min =  155 RPM, div = 128)  ALARM
fan4:          0 RPM  (min =  219 RPM, div = 128)  ALARM
fan5:          0 RPM  (min =  620 RPM, div = 128)  ALARM
Sys Temp:    +45.0°C  (high =  +9.0°C, hyst = +68.0°C)  sensor = thermistor
CPU Temp:    +23.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
AUX Temp:    +81.0°C  (high = +80.0°C, hyst = +75.0°C)  ALARM  sensor = thermistor
cpu0_vid:   +1.350 V

```If I want to display Sys Temp in my conky I will use this line  :
```
${exec sensors | grep 'Sys Temp' | cut -c15-16}
```and in the Lua script, the above line is here (inside a conky_parse function):
```
 {"Temp.","",conky_parse("[COLOR=Red]${exec sensors | grep 'Sys Temp' | cut -c15-16}[/COLOR]"),100,"°C"},
```**[SIZE=4]But[/SIZE]**, if you are not familiar with Lua scripts and if your are looking just for a clock, I suggest you to start with this script, it is more simple and doesn't require sensors :
```

--[[PIE CHART WIDGET BY WLOURF v1.2 26 may 2010

This widget draw a pie chart or a ring in a conky window.
More info on the parameters with pictures on this page :
http://u-scripts.blogspot.com/2010/04/pie-chart-widget.html


v1.0 10/04/2010  original release
v1.1 15/05/2010  the parameters are in a table (pie_settings), only the values in pie_settings.tableV are mandatory
                 added an option to draw values like a ring (type_arc="l")
v1.2 26/05/2010     add inverse_l parameter (for type_arc="l")
                 bug fix : line_lgth problem
                 read_df function improved
]]

require 'cairo'


--main function
function conky_main_pie()
    if conky_window==nil then return end

    --flag used in this script to display or not text informations
    local file = io.open("/tmp/flag-conky-pie","r")    
    io.close()
    flag_show_text=(file ~= nil)


-- ------------------PARAMETERS TO SET-----------------------
    --all parameters are explained in CIRCLE for RAM bellow
    --theses parameters are called many times so I put them into variables
    local font_name,font_size="FreeSans",14
--    local col0,col1,col2=0x0033FF,0x3300FF,0x6600FF
    local col0,col1,col2=0xFFFFCC,0xCCFF99,0x99FF00
    local colbg=0x99CCFF
        
    --for the clock
    local temp = os.date("*t")
    local hour=temp.hour
    if hour>12 then hour=hour-12 end
    local hpc,mpc,spc=hour/12,temp.min/60,temp.sec/60

    
    pie_settings= {

        {--CIRCLE 3 : DISK SPACE
            tableV=read_df(false,true),
            xc=150,
            yc=400 ,
            int_radius=0,
            radius=45,
            type_arc="r",
            proportional=false,
            first_angle=-90,
            gradient_effect=false,
            last_angle=270,
            show_text=true,
            line_lgth=100,
            txt_format="&l free &n",
            font_color=colbg,    
            tablebg={            
                {colbg,0.5},
                },
            tablefg={            
                {col0,1},
                {col1,1},
                {col2,1},
                },
        },        


        {--CIRCLE 2 : ARCS 1 & 2 INTERNET SPEED
            tableV={
                {"dl","downspeedf","wlan0",2000,"kb/s"},
                {"ul","upspeedf","wlan0",100,"kb/s"},
                },
            xc=100,
            yc=250,
            int_radius=10,
            radius=45,
            first_angle=-30,
            last_angle=210,
            type_arc="r",
            --line_lgth=150,
            line_width=0,
            show_text=true,
            txt_format="&l : &v",
            font_color=colbg,
            tablebg={
                {colbg,0.5},
                },
            tablefg={
                {col0,1},
                {col1,1},
                },
        },        

        
                
        {--CERCLE 2 : ARC 3 = IP ADRESS (invisible circle)
            tableV={
                {conky_parse("${addr wlan0}").."  ","",0,100,""},
--                {conky_parse("192.168.0.1").."  ","",0,100,""},
                },
            xc=100,
            yc=250+5,
            int_radius=0,
            radius=1,
            first_angle=210,
            last_angle=330,
            type_arc="r",
            line_lgth=10,
            line_width=0,
            show_text=true,
            txt_format="&l",
            font_color=colbg,
            tablebg={
                {col2,0},
                },
            tablefg={            
                {col2,1},
                },
                
        },    
        
        
            {--CIRCLE 4 : ARC 1 CPU 0
            tableV={
                {"cpu 0","cpu","cpu 0",100,"%"},
                --{"cpu 1","cpu","cpu 1",100,"%"},
                },
            xc=100,
            yc=550,
            int_radius=30,
            radius=45,
            first_angle=-30,
            last_angle=90,
            type_arc="l",
            --line_lgth=150,
            line_width=0,
            show_text=true,
            txt_format="&l : &v",
            font_color=colbg,
            tablebg={
                {colbg,0.5},
                },
            tablefg={
                {col0,1},
                },
        },        

            {--CIRCLE 4 : ARC 2 CPU 1
            tableV={
                --{"cpu 0","cpu","cpu 0",100,"%"},
                {"cpu 1","cpu","cpu 1",100,"%"},
                },
            xc=100,
            yc=550,
            int_radius=30,
            radius=45,
            first_angle=90,
            last_angle=220,
            type_arc="l",
            inverse_l_arc=true,
            --line_lgth=150,
            line_width=0,
            show_text=true,
            txt_format="&l : &v",
            font_color=colbg,
            tablebg={
                {colbg,0.5},
                },
            tablefg={
                {col0,1},
                },
        },        
        
                

    

        {--CIRCLE  5 : MEMORY : ram
        --I wrote all the possibles parameters available for the script, only tableV is mandatory
            -- table of labels and values {{label,conky_variable,conky_argument,convert to Go-Mo-Ko units (true/false) or unit}, 
            -- this table is mandatory, others parameters are optionals
            tableV={
                {"mem","memperc","",100,"%"},
                },
            --to know disk space, use this line 
            --    tableV=read_df(false,true),    
            --[[ another example
            tableV={ {"cpu0","cpu","cpu0",100,"%"},
                    {"cpu1","cpu","cpu1",100,"%"},
                    {"fan","","${exec sensors | grep 'CPU Fan' | cut -c13-16}",2000," rpm"},
                    {"temp","","${exec sensors | grep 'Sys Temp' | cut -c15-17}",100,"°C"},
                    {"some stuff","",75.5,100,"°C"}
                    },
            ]]                        
            xc=50,                    -- x center of the pie, default = conky_window.width/2
            yc=700,                    -- y center of the pie, default = conky_window.height/2
            int_radius=30,        -- internal radius in pixel, default = conky_window.width/6
            radius=45,            -- external radius in pixel, default = conky_window.width/4
            first_angle=0,        -- first angle of the pie (in degrees), default=0
            last_angle=360,            -- last angle of the pie (in degrees), default=360
            type_arc="l",            -- fill the arc in a linear way (ring) or radial way (pie), values l or r, default=l
            inverse_l_arc=false,    -- inverse arc for rings (true/false), default=false
            proportional=false,        -- display proportional sectors (true/false); default =false
            gradient_effect=true,     -- gradient effect (true/false), default=true
            line_lgth=50,            -- length for horizontal line (from radius to end of line), default=radius
            line_width=0,            -- width of line, default=1
            line_space=10,            -- vertical space between two lines, default=10 pixels
            extend_line=true,       -- grow up the line (true/false) if length of text> line_lgth, default=true
            nb_decimals=0,            -- number of decimals for numbers, default=1
            show_text=true,-- display text (true/false), default=true
            txt_font=font_name,        -- font, default "Japan"
            font_size=12,            -- font size, default=12
            font_color=colbg,    -- font color (for gradient) or nil (for constant color), default = nil
            font_alpha=0.5,            -- font alpha, default=1
            txt_offset=1,            -- space between text and line, default=1
            txt_format="&l &v",        -- string for formatting text, possibles values are :  default = "&l : &v"
                        -- &l for label
                        -- &o for occupied percentage
                        -- &f for free percentage
                        -- &v for value 
                        -- &n for free value (non-occupied)    
                        -- &m for max value
                        -- &p for percentage value of full graph
            tablebg={            -- table of tables of colours for background {colors,alpha}
                {colbg,0.5},
                },
            tablefg={            -- table of tables of colours for foreground {colors,alpha}
                {col2,1},
                },
        },                                
        {--CIRCLE 5 : MEMORY : swap
            tableV={
                {"swap","swapperc",0,100,"%"},
                },
            xc=50,
            yc=700,
            int_radius=15,
            radius=30,
            first_angle=0,
            last_angle=360,
            line_lgth=50+15,
            line_width=0,
            show_text=true,
            font_color=nil,
            nb_decimals=0,
            txt_format="&l &v",
            font_color=colbg,
            font_alpha=0.5,
            tablebg={
                {colbg,0.5},
                },
            tablefg={
                {col2,1},
                },
        },            
        


        





        


    
        {--CLOCK CIRCLE 1 : HOURS
            tableV={
                {"hour.min","",1,1,""},
                {"hour.min","",0,11,""},
                },
            xc=50,yc=100,
            int_radius=0    ,
            radius=15,        
            first_angle=hpc*360,
            last_angle=hpc*360+360,
            show_text=false,
            proportional=true,
            tablebg={
                {colbg,0.5},
                },
            tablefg={
                {col0,1},
                },            
        },                                
        {--CLOCK CIRCLE 2 : MINUTES
            tableV={
                {"hour.min","",1,1,""},
                {"hour.min","",0,59,""},
                },
            xc=50,yc=100,
            int_radius=15    ,
            radius=30,        
            first_angle=hpc*360,
            last_angle=hpc*360+360,
            show_text=false,
            proportional=true,
            tablebg={
                {colbg,0.5},
                },
            tablefg={
                {col1,1},
                },            
        },                                

        {--CLOCK CIRCLE 3 : SECONDS
            tableV={
                {"hour.min","",1,1,""},
                {"hour.min","",0,59,""},
                },
            xc=50,yc=100,
            int_radius=30,        
            radius=45,            
            first_angle=spc*360,
            last_angle=spc*360+360,
            show_text=false,
            proportional=true,
            tablebg={
                {colbg,0.5},
                },
            tablefg={
                {col2,1},
                }
                
        },        



    }
-------------------END OF PARAMETERS ---------------

    local w=conky_window.width
    local h=conky_window.height
    local cs=cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, w, h)
    cr=cairo_create(cs)

    if tonumber(conky_parse('${updates}'))>5 then
        for i in pairs(pie_settings) do
            draw_pie(pie_settings[i])
        end
    end

    cairo_destroy(cr)
end



function string:split(delimiter)
--source for the split function : http://www.wellho.net/resources/ex.php4?item=u108/split
  local result = { }
  local from  = 1
  local delim_from, delim_to = string.find( self, delimiter, from  )
  while delim_from do
    table.insert( result, string.sub( self, from , delim_from-1 ) )
    from  = delim_to + 1
    delim_from, delim_to = string.find( self, delimiter, from  )
  end
  table.insert( result, string.sub( self, from  ) )
  return result
end


function rgb_to_r_g_b(colour, alpha)
    return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
end

function round(num, idp)
    local mult = 10^(idp or 0)
    return math.floor(num * mult + 0.5) / mult
end

function size_to_text(size,nb_dec)
    local txt_v
    if nb_dec<0 then nb_dec=0 end
    size = tonumber(size)
    if size>1024*1024*1024 then
        txt_v=string.format("%."..nb_dec.."f Go",size/1024/1024/1024)
    elseif size>1024*1024 then 
        txt_v=string.format("%."..nb_dec.."f Mo",size/1024/1024)
    elseif size>1024 then 
        txt_v=string.format("%."..nb_dec.."f Ko",size/1024)
    else
        txt_v=string.format("%."..nb_dec.."f o",size)
    end
    return txt_v
end



function read_df(show_media,sort_table)
    --read output of command df and return arrays of value for files systems
    --reurn array of table {file syst, "", occupied space , total space , convert to G, M, K ...}
    
    local f = io.popen("df")

    local results={}

    while true do
         local line = f:read("*l")
         if line == nil then break end
         while string.match(line,"  ") do
             line=string.gsub(line,"  "," ")
         end
        local arr_l=string.split(line," ")
        local match = string.match(arr_l[1],"/")
        
        if string.match(arr_l[1],"/") then
            if not show_media then arr_l[6]=string.gsub(arr_l[6],"/media/","",1) end
            table.insert(results,{arr_l[6],"",(arr_l[2]-arr_l[4])*1024,arr_l[2]*1024,true})
        end
    end

    f:close()
    
    if sort_table then
        --how to sort table into table?
        local flagS=true
        while flagS do
            for k=2, #results do 
                flagS=false
                if tonumber(results[1][3])>tonumber(results[2][3]) then
                    local tmpV = results[1]
                    results[1] = results[2]
                    results[2] = tmpV
                    flagS=true
                end
                if tonumber(results[k][3])<tonumber(results[k-1][3]) then
                    local tmpV = results[k-1]
                    results[k-1] = results[k]
                    results[k] = tmpV
                    flagS=true
                end
            end
        end
    end
    
    return results --array {file syst, occupied space , total space }
end


function draw_pie(t)
    
    if t.tableV==nil then 
        print ("No input values ...") 
        return
    else
        tableV=t.tableV
    end

    if t.xc==nil then t.xc=conky_window.width/2 end
    if t.yc==nil then t.yc=conky_window.height/2 end
    if t.int_radius ==nil then t.int_radius =conky_window.width/6 end
    if t.radius ==nil then t.radius =conky_window.width/4 end
    if t.first_angle==nil then t.first_angle =0 end
    if t.last_angle==nil then t.last_angle=360 end
    if t.proportional==nil then t.proportional=false end
    if t.tablebg==nil then t.tablebg={{0xFFFFFF,0.5},{0xFFFFFF,0.5}} end
    if t.tablefg==nil then t.tablefg={{0xFF0000,1},{0x00FF00,1}} end
    if t.gradient_effect==nil then t.gradient_effect=true end
    if t.show_text==nil then t.show_text=true end
    if t.line_lgth==nil then t.line_lgth=t.int_radius end
    if t.line_space==nil then t.line_space=10 end
    if t.line_width==nil then t.line_width=1 end
    if t.extend_line==nil then t.extend_line=true end
    if t.txt_font==nil then t.txt_font="Japan" end
    if t.font_size==nil then t.font_size=12 end
    --if t.font_color==nil then t.font_color=0xFFFFFF end
    if t.font_alpha==nil then t.font_alpha = 1 end
    if t.txt_offset==nil then t.txt_offset = 1 end
    if t.txt_format==nil then t.txt_format = "&l : &v" end
    if t.nb_decimals==nil then t.nb_decimals=1 end
    if t.type_arc==nil then t.type_arc="l" end
    if t.inverse_l_arc==nil then t.inverse_l_arc=false end
    
    
    local function draw_sector(tablecolor,colorindex,pc,lastAngle,angle,radius,int_radius,gradient_effect,type_arc,inverse_l_arc)
        --draw a portion of arc
        radiuspc=(radius-int_radius)*pc+int_radius
        angle0=lastAngle
        val=1
        if type_arc=="l" then 
            val=pc;radiuspc=radius
        end
        angle1=angle*val

        if type_arc=="l" and inverse_l_arc then 

            cairo_save(cr)
    
            cairo_rotate(cr,angle0+angle)
            
            if gradient_effect then        
                local pat = cairo_pattern_create_radial (0,0, int_radius, 0,0,radius)
                cairo_pattern_add_color_stop_rgba (pat, 0, rgb_to_r_g_b(tablecolor[colorindex][1],0))
                cairo_pattern_add_color_stop_rgba (pat, 0.5, rgb_to_r_g_b(tablecolor[colorindex][1],tablecolor[colorindex][2]))
                cairo_pattern_add_color_stop_rgba (pat, 1, rgb_to_r_g_b(tablecolor[colorindex][1],0))
                cairo_set_source (cr, pat)
                cairo_pattern_destroy(pat)
            else
                cairo_set_source_rgba(cr,rgb_to_r_g_b(tablecolor[colorindex][1],tablecolor[colorindex][2]))
            end
            cairo_move_to(cr,0,-int_radius)
            cairo_line_to(cr,0,-radiuspc)
            cairo_rotate(cr,-math.pi/2)
        
            cairo_arc_negative(cr,0,0,radiuspc,0,-angle1)
            cairo_rotate(cr,-math.pi/2-angle1)
            cairo_line_to(cr,0,int_radius)
            cairo_rotate(cr,math.pi/2)
            cairo_arc(cr,0,0,int_radius,0,angle1)
            cairo_close_path (cr);
            cairo_fill(cr)

            cairo_restore(cr)
        else
        
            cairo_save(cr)
    
            cairo_rotate(cr,angle0)

            if gradient_effect then        
                local pat = cairo_pattern_create_radial (0,0, int_radius, 0,0,radius)
                cairo_pattern_add_color_stop_rgba (pat, 0, rgb_to_r_g_b(tablecolor[colorindex][1],0))
                cairo_pattern_add_color_stop_rgba (pat, 0.5, rgb_to_r_g_b(tablecolor[colorindex][1],tablecolor[colorindex][2]))
                cairo_pattern_add_color_stop_rgba (pat, 1, rgb_to_r_g_b(tablecolor[colorindex][1],0))
                cairo_set_source (cr, pat)
                cairo_pattern_destroy(pat)
            else
                cairo_set_source_rgba(cr,rgb_to_r_g_b(tablecolor[colorindex][1],tablecolor[colorindex][2]))
            end
            cairo_move_to(cr,0,-int_radius)
            cairo_line_to(cr,0,-radiuspc)
            cairo_rotate(cr,-math.pi/2)
        
            cairo_arc(cr,0,0,radiuspc,0,angle1)
            cairo_rotate(cr,angle1-math.pi/2)
            cairo_line_to(cr,0,int_radius)
            cairo_rotate(cr,math.pi/2)
            cairo_arc_negative(cr,0,0,int_radius,0,-angle1)
            cairo_close_path (cr);
            cairo_fill(cr)

            cairo_restore(cr)
        end
        

    end

    function draw_lines(idx,nbArcs,angle,table_colors,idx_color,adjust,line_lgth,length_txt,txt_offset,radius,line_width,line_space,font_color,font_alpha)
        --draw lines
        
        local x0=radiuspc*math.sin(lastAngle+angle/2)
        local y0=-radiuspc*math.cos(lastAngle+angle/2)
        local x1=1.2*radius*math.sin(lastAngle+angle/2)
        local y1=-1.2*radius*math.cos(lastAngle+angle/2)

        local x2=line_lgth
        local y2=y1
        local x3,y3=nil,nil
        if x0<=0 then
            x2=-x2
        end

        if adjust then
            if x0>0 and x2-x1<length_txt then x2=x1+length_txt end
            if x0<=0 and x1-x2<length_txt then x2=x1-length_txt end            
        end 
        
        if idx>1 then
            local dY = math.abs(y2-lastPt2[2])
            if dY < line_space and lastPt2[1]*x1>0 then
                if x0>0 then
                    y2 = line_space+lastPt2[2]
                else
                    y2 = -line_space+lastPt2[2]
                end
                if (y2>y1 and x0>0) or (y2<y1 and x0<0 )  then
                    --x3 is for vertical segment if needed
                    x3,y3=x2,y2                    
                    x2=x1
                    if x3>0 then x3=x3+txt_offset end
                else
                    Z=intercept({x0,y0},{x1,y1},{0,y2},{1,y2})
                    x1,y1=Z[1],Z[2]
                end
            end
        else
            --remind x2,y2 of first value
            x2first,y2first = x2,y2
        end

        if font_color==nil then
            cairo_set_source_rgba(cr,rgb_to_r_g_b(table_colors[idx_color][1],table_colors[idx_color][2]))
        else
            local pat = cairo_pattern_create_linear (x2,y2, x0,y0)
            cairo_pattern_add_color_stop_rgba (pat, 0, rgb_to_r_g_b(font_color,font_alpha))
            cairo_pattern_add_color_stop_rgba (pat, 1, rgb_to_r_g_b(table_colors[idx_color][1],table_colors[idx_color][2]))
            cairo_set_source (cr, pat)
            cairo_pattern_destroy(pat)
        end

        
        cairo_move_to(cr,x0,y0)
        cairo_line_to(cr,x1,y1)
        cairo_line_to(cr,x2,y2)
        if x3~=nil then 
            cairo_line_to(cr,x3,y3)
            x2,y2=x3,y3    
        end
        cairo_set_line_width(cr,line_width)
        cairo_stroke(cr)
        --lastAngle=lastAngle+angle
        return {x2,y2}
    end
    
    function intercept(p11,p12,p21,p22)
        --calculate interscetion of two lines and return coordinates
        a1=(p12[2]-p11[2])/(p12[1]-p11[1])

        a2=(p22[2]-p21[2])/(p22[1]-p21[1])

        b1=p11[2]-a1*p11[1]

        b2=p21[2]-a2*p21[1]

        X=(b2-b1)/(a1-a2)

        Y=a1*X+b1
        return {X,Y}
    end

    --some checks
    if t.first_angle>=t.last_angle then
        local tmp_angle=t.last_angle
        --t.last_angle=t.first_angle
        --t.first_angle=tmp_angle
        print ("inversed angles")
    end

    if t.last_angle-t.first_angle>360 and t.first_angle>0 then
        t.last_angle=360+t.first_angle
        print ("reduce angles")
    end
    
    if t.last_angle+t.first_angle>360 and t.first_angle<=0 then
        t.last_angle=360+t.first_angle
        print ("reduce angles")
    end
    
    if t.int_radius<0 then t.int_radius =0 end
    if t.int_radius>t.radius then
        local tmp_radius=t.radius
        t.radius=t.int_radius
        t.int_radius=tmp_radius
        print ("inversed angles")
    end
    if t.int_radius==t.radius then
        t.int_radius=0
        print ("int radius set to 0")
    end    
    --end of checks
    
    cairo_save(cr)
    cairo_translate(cr,t.xc,t.yc)
    cairo_set_line_join (cr, CAIRO_LINE_JOIN_ROUND)
    cairo_set_line_cap (cr, CAIRO_LINE_CAP_ROUND)
    
    local nbArcs=#tableV
    local anglefull= (t.last_angle-t.first_angle)*math.pi/180
    local fullsize = 0
    for i= 1,nbArcs do
        fullsize=fullsize+tableV[i][4]
    end

    local cb,cf,angle=0,0,anglefull/nbArcs
    lastAngle=t.first_angle*math.pi/180
    lastPt2={nil,nil}

    for i =1, nbArcs do
        if t.proportional then
            angle=tableV[i][4]/fullsize*anglefull
        end
        --set colours
        cb,cf=cb+1,cf+1
        if cb>#t.tablebg then cb=1 end
        if cf>#t.tablefg then cf=1 end
        
        if tableV[i][2]~="" then
            str=string.format('${%s %s}',tableV[i][2],tableV[i][3])
        else
            str = tableV[i][3]
        end
        str=conky_parse(str)
        value=tonumber(str)
        if value==nil then value=0 end
    
        --draw sectors
        draw_sector(t.tablebg,cb,1,lastAngle,angle,t.radius,t.int_radius,t.gradient_effect,t.type_arc,t.inverse_l_arc)
        --print (t.tablefg,cf,tableV[i][2],tableV[i][3],lastAngle,angle,t.radius,t.int_radius)
        --print (cf,tableV[i],tableV[i][2],tableV[i][3])
        draw_sector(t.tablefg,cf,value/tableV[i][4],lastAngle,angle,t.radius,t.int_radius,t.gradient_effect,t.type_arc,t.inverse_l_arc)

        if t.show_text then
            --draw text
            local txt_l   = tableV[i][1]
            local txt_opc = round(100*value/tableV[i][4],t.nb_decimals).."%%"
            local txt_fpc = round(100*(tableV[i][4]-value/tableV[i][4]),t.nb_decimals).."%%"
            local txt_ov,txt_fv,txt_max
            if tableV[i][5]==true then
                txt_ov  = size_to_text(value,t.nb_decimals)
                txt_fv  = size_to_text(tableV[i][4]-value,t.nb_decimals)
                txt_max = size_to_text(tableV[i][4],t.nb_decimals)
            else
                if tableV[i][5]=="%" then tableV[i][5]="%%" end
                txt_ov=string.format("%."..t.nb_decimals.."f ",value)..tableV[i][5]
                txt_fv=string.format("%."..t.nb_decimals.."f",tableV[i][4]-value)..tableV[i][5]
                txt_max=string.format("%."..t.nb_decimals.."f",tableV[i][4])..tableV[i][5]
            end
            txt_pc = string.format("%."..t.nb_decimals.."f",100*tableV[i][4]/fullsize).."%%"
            local txt_out = t.txt_format
            txt_out = string.gsub(txt_out,"&l",txt_l)  --label
            txt_out = string.gsub(txt_out,"&o",txt_opc)--occ. %
            txt_out = string.gsub(txt_out,"&f",txt_fpc)--free %
            txt_out = string.gsub(txt_out,"&v",txt_ov) --occ. value
            txt_out = string.gsub(txt_out,"&n",txt_fv) --free value
            txt_out = string.gsub(txt_out,"&m",txt_max)--max
            txt_out = string.gsub(txt_out,"&p",txt_pc)--percent
            
            local te=cairo_text_extents_t:create()
            cairo_set_font_size(cr,t.font_size)
            cairo_select_font_face(cr, t.txt_font, CAIRO_FONT_SLANT_NORMAL, CAIRO_FONT_WEIGHT_NORMAL)
            cairo_text_extents (cr,txt_out,te)

            --draw lines 
            lastPt2=draw_lines(i,nbArcs,angle,t.tablefg,cf,t.extend_line,t.line_lgth+t.radius, 
                    te.width + te.x_bearing,t.txt_offset,t.radius,t.line_width,t.line_space,t.font_color,t.font_alpha)    
        
            local xA=lastPt2[1]
            local yA=lastPt2[2]-t.line_width-t.txt_offset
            if xA>0 then xA = xA-(te.width + te.x_bearing) end
            cairo_move_to(cr,xA,yA)
            cairo_show_text(cr,txt_out)
        end
        
        lastAngle=lastAngle+angle
    end
    cairo_restore(cr)
end
--[[PIE CHART WIDGET BY WLOURF v1.2 26 may 2010

This widget draw a pie chart or a ring in a conky window.
More info on the parameters with pictures on this page :
http://u-scripts.blogspot.com/2010/04/pie-chart-widget.html


v1.0 10/04/2010  original release
v1.1 15/05/2010  the parameters are in a table (pie_settings), only the values in pie_settings.tableV are mandatory
                 added an option to draw values like a ring (type_arc="l")
v1.2 26/05/2010     add inverse_l parameter (for type_arc="l")
                 bug fix : line_lgth problem
                 read_df function improved
]]

require 'cairo'


--main function
function conky_main_pie()
    if conky_window==nil then return end

    --flag used in this script to display or not text informations
    local file = io.open("/tmp/flag-conky-pie","r")    
    io.close()
    flag_show_text=(file ~= nil)


-- ------------------PARAMETERS TO SET-----------------------
    --all parameters are explained in CIRCLE for RAM bellow
    --theses parameters are called many times so I put them into variables
    local font_name,font_size="FreeSans",14
--    local col0,col1,col2=0x0033FF,0x3300FF,0x6600FF
    local col0,col1,col2=0xFFFFCC,0xCCFF99,0x99FF00
    local colbg=0x99CCFF
        
    --for the clock
    local temp = os.date("*t")
    local hour=temp.hour
    if hour>12 then hour=hour-12 end
    local hpc,mpc,spc=hour/12,temp.min/60,temp.sec/60

    
    pie_settings= {

        {--CIRCLE 3 : DISK SPACE
            tableV=read_df(false,true),
            xc=150,
            yc=400 ,
            int_radius=0,
            radius=45,
            type_arc="r",
            proportional=false,
            first_angle=-90,
            gradient_effect=false,
            last_angle=270,
            show_text=true,
            line_lgth=100,
            txt_format="&l free &n",
            font_color=colbg,    
            tablebg={            
                {colbg,0.5},
                },
            tablefg={            
                {col0,1},
                {col1,1},
                {col2,1},
                },
        },        


        {--CIRCLE 2 : ARCS 1 & 2 INTERNET SPEED
            tableV={
                {"dl","downspeedf","wlan0",2000,"kb/s"},
                {"ul","upspeedf","wlan0",100,"kb/s"},
                },
            xc=100,
            yc=250,
            int_radius=10,
            radius=45,
            first_angle=-30,
            last_angle=210,
            type_arc="r",
            --line_lgth=150,
            line_width=0,
            show_text=true,
            txt_format="&l : &v",
            font_color=colbg,
            tablebg={
                {colbg,0.5},
                },
            tablefg={
                {col0,1},
                {col1,1},
                },
        },        

        
                
        {--CERCLE 2 : ARC 3 = IP ADRESS (invisible circle)
            tableV={
                {conky_parse("${addr wlan0}").."  ","",0,100,""},
--                {conky_parse("192.168.0.1").."  ","",0,100,""},
                },
            xc=100,
            yc=250+5,
            int_radius=0,
            radius=1,
            first_angle=210,
            last_angle=330,
            type_arc="r",
            line_lgth=10,
            line_width=0,
            show_text=true,
            txt_format="&l",
            font_color=colbg,
            tablebg={
                {col2,0},
                },
            tablefg={            
                {col2,1},
                },
                
        },    
        
        
            {--CIRCLE 4 : ARC 1 CPU 0
            tableV={
                {"cpu 0","cpu","cpu 0",100,"%"},
                --{"cpu 1","cpu","cpu 1",100,"%"},
                },
            xc=100,
            yc=550,
            int_radius=30,
            radius=45,
            first_angle=-30,
            last_angle=90,
            type_arc="l",
            --line_lgth=150,
            line_width=0,
            show_text=true,
            txt_format="&l : &v",
            font_color=colbg,
            tablebg={
                {colbg,0.5},
                },
            tablefg={
                {col0,1},
                },
        },        

            {--CIRCLE 4 : ARC 2 CPU 1
            tableV={
                --{"cpu 0","cpu","cpu 0",100,"%"},
                {"cpu 1","cpu","cpu 1",100,"%"},
                },
            xc=100,
            yc=550,
            int_radius=30,
            radius=45,
            first_angle=90,
            last_angle=220,
            type_arc="l",
            inverse_l_arc=true,
            --line_lgth=150,
            line_width=0,
            show_text=true,
            txt_format="&l : &v",
            font_color=colbg,
            tablebg={
                {colbg,0.5},
                },
            tablefg={
                {col0,1},
                },
        },        
        
                

    

        {--CIRCLE  5 : MEMORY : ram
        --I wrote all the possibles parameters available for the script, only tableV is mandatory
            -- table of labels and values {{label,conky_variable,conky_argument,convert to Go-Mo-Ko units (true/false) or unit}, 
            -- this table is mandatory, others parameters are optionals
            tableV={
                {"mem","memperc","",100,"%"},
                },
            --to know disk space, use this line 
            --    tableV=read_df(false,true),    
            --[[ another example
            tableV={ {"cpu0","cpu","cpu0",100,"%"},
                    {"cpu1","cpu","cpu1",100,"%"},
                    {"fan","","${exec sensors | grep 'CPU Fan' | cut -c13-16}",2000," rpm"},
                    {"temp","","${exec sensors | grep 'Sys Temp' | cut -c15-17}",100,"°C"},
                    {"some stuff","",75.5,100,"°C"}
                    },
            ]]                        
            xc=50,                    -- x center of the pie, default = conky_window.width/2
            yc=700,                    -- y center of the pie, default = conky_window.height/2
            int_radius=30,        -- internal radius in pixel, default = conky_window.width/6
            radius=45,            -- external radius in pixel, default = conky_window.width/4
            first_angle=0,        -- first angle of the pie (in degrees), default=0
            last_angle=360,            -- last angle of the pie (in degrees), default=360
            type_arc="l",            -- fill the arc in a linear way (ring) or radial way (pie), values l or r, default=l
            inverse_l_arc=false,    -- inverse arc for rings (true/false), default=false
            proportional=false,        -- display proportional sectors (true/false); default =false
            gradient_effect=true,     -- gradient effect (true/false), default=true
            line_lgth=50,            -- length for horizontal line (from radius to end of line), default=radius
            line_width=0,            -- width of line, default=1
            line_space=10,            -- vertical space between two lines, default=10 pixels
            extend_line=true,       -- grow up the line (true/false) if length of text> line_lgth, default=true
            nb_decimals=0,            -- number of decimals for numbers, default=1
            show_text=true,-- display text (true/false), default=true
            txt_font=font_name,        -- font, default "Japan"
            font_size=12,            -- font size, default=12
            font_color=colbg,    -- font color (for gradient) or nil (for constant color), default = nil
            font_alpha=0.5,            -- font alpha, default=1
            txt_offset=1,            -- space between text and line, default=1
            txt_format="&l &v",        -- string for formatting text, possibles values are :  default = "&l : &v"
                        -- &l for label
                        -- &o for occupied percentage
                        -- &f for free percentage
                        -- &v for value 
                        -- &n for free value (non-occupied)    
                        -- &m for max value
                        -- &p for percentage value of full graph
            tablebg={            -- table of tables of colours for background {colors,alpha}
                {colbg,0.5},
                },
            tablefg={            -- table of tables of colours for foreground {colors,alpha}
                {col2,1},
                },
        },                                
        {--CIRCLE 5 : MEMORY : swap
            tableV={
                {"swap","swapperc",0,100,"%"},
                },
            xc=50,
            yc=700,
            int_radius=15,
            radius=30,
            first_angle=0,
            last_angle=360,
            line_lgth=50+15,
            line_width=0,
            show_text=true,
            font_color=nil,
            nb_decimals=0,
            txt_format="&l &v",
            font_color=colbg,
            font_alpha=0.5,
            tablebg={
                {colbg,0.5},
                },
            tablefg={
                {col2,1},
                },
        },            
        


        





        


    
        {--CLOCK CIRCLE 1 : HOURS
            tableV={
                {"hour.min","",1,1,""},
                {"hour.min","",0,11,""},
                },
            xc=50,yc=100,
            int_radius=0    ,
            radius=15,        
            first_angle=hpc*360,
            last_angle=hpc*360+360,
            show_text=false,
            proportional=true,
            tablebg={
                {colbg,0.5},
                },
            tablefg={
                {col0,1},
                },            
        },                                
        {--CLOCK CIRCLE 2 : MINUTES
            tableV={
                {"hour.min","",1,1,""},
                {"hour.min","",0,59,""},
                },
            xc=50,yc=100,
            int_radius=15    ,
            radius=30,        
            first_angle=hpc*360,
            last_angle=hpc*360+360,
            show_text=false,
            proportional=true,
            tablebg={
                {colbg,0.5},
                },
            tablefg={
                {col1,1},
                },            
        },                                

        {--CLOCK CIRCLE 3 : SECONDS
            tableV={
                {"hour.min","",1,1,""},
                {"hour.min","",0,59,""},
                },
            xc=50,yc=100,
            int_radius=30,        
            radius=45,            
            first_angle=spc*360,
            last_angle=spc*360+360,
            show_text=false,
            proportional=true,
            tablebg={
                {colbg,0.5},
                },
            tablefg={
                {col2,1},
                }
                
        },        



    }
-------------------END OF PARAMETERS ---------------

    local w=conky_window.width
    local h=conky_window.height
    local cs=cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, w, h)
    cr=cairo_create(cs)

    if tonumber(conky_parse('${updates}'))>5 then
        for i in pairs(pie_settings) do
            draw_pie(pie_settings[i])
        end
    end

    cairo_destroy(cr)
end



function string:split(delimiter)
--source for the split function : http://www.wellho.net/resources/ex.php4?item=u108/split
  local result = { }
  local from  = 1
  local delim_from, delim_to = string.find( self, delimiter, from  )
  while delim_from do
    table.insert( result, string.sub( self, from , delim_from-1 ) )
    from  = delim_to + 1
    delim_from, delim_to = string.find( self, delimiter, from  )
  end
  table.insert( result, string.sub( self, from  ) )
  return result
end


function rgb_to_r_g_b(colour, alpha)
    return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
end

function round(num, idp)
    local mult = 10^(idp or 0)
    return math.floor(num * mult + 0.5) / mult
end

function size_to_text(size,nb_dec)
    local txt_v
    if nb_dec<0 then nb_dec=0 end
    size = tonumber(size)
    if size>1024*1024*1024 then
        txt_v=string.format("%."..nb_dec.."f Go",size/1024/1024/1024)
    elseif size>1024*1024 then 
        txt_v=string.format("%."..nb_dec.."f Mo",size/1024/1024)
    elseif size>1024 then 
        txt_v=string.format("%."..nb_dec.."f Ko",size/1024)
    else
        txt_v=string.format("%."..nb_dec.."f o",size)
    end
    return txt_v
end



function read_df(show_media,sort_table)
    --read output of command df and return arrays of value for files systems
    --reurn array of table {file syst, "", occupied space , total space , convert to G, M, K ...}
    
    local f = io.popen("df")

    local results={}

    while true do
         local line = f:read("*l")
         if line == nil then break end
         while string.match(line,"  ") do
             line=string.gsub(line,"  "," ")
         end
        local arr_l=string.split(line," ")
        local match = string.match(arr_l[1],"/")
        
        if string.match(arr_l[1],"/") then
            if not show_media then arr_l[6]=string.gsub(arr_l[6],"/media/","",1) end
            table.insert(results,{arr_l[6],"",(arr_l[2]-arr_l[4])*1024,arr_l[2]*1024,true})
        end
    end

    f:close()
    
    if sort_table then
        --how to sort table into table?
        local flagS=true
        while flagS do
            for k=2, #results do 
                flagS=false
                if tonumber(results[1][3])>tonumber(results[2][3]) then
                    local tmpV = results[1]
                    results[1] = results[2]
                    results[2] = tmpV
                    flagS=true
                end
                if tonumber(results[k][3])<tonumber(results[k-1][3]) then
                    local tmpV = results[k-1]
                    results[k-1] = results[k]
                    results[k] = tmpV
                    flagS=true
                end
            end
        end
    end
    
    return results --array {file syst, occupied space , total space }
end


function draw_pie(t)
    
    if t.tableV==nil then 
        print ("No input values ...") 
        return
    else
        tableV=t.tableV
    end

    if t.xc==nil then t.xc=conky_window.width/2 end
    if t.yc==nil then t.yc=conky_window.height/2 end
    if t.int_radius ==nil then t.int_radius =conky_window.width/6 end
    if t.radius ==nil then t.radius =conky_window.width/4 end
    if t.first_angle==nil then t.first_angle =0 end
    if t.last_angle==nil then t.last_angle=360 end
    if t.proportional==nil then t.proportional=false end
    if t.tablebg==nil then t.tablebg={{0xFFFFFF,0.5},{0xFFFFFF,0.5}} end
    if t.tablefg==nil then t.tablefg={{0xFF0000,1},{0x00FF00,1}} end
    if t.gradient_effect==nil then t.gradient_effect=true end
    if t.show_text==nil then t.show_text=true end
    if t.line_lgth==nil then t.line_lgth=t.int_radius end
    if t.line_space==nil then t.line_space=10 end
    if t.line_width==nil then t.line_width=1 end
    if t.extend_line==nil then t.extend_line=true end
    if t.txt_font==nil then t.txt_font="Japan" end
    if t.font_size==nil then t.font_size=12 end
    --if t.font_color==nil then t.font_color=0xFFFFFF end
    if t.font_alpha==nil then t.font_alpha = 1 end
    if t.txt_offset==nil then t.txt_offset = 1 end
    if t.txt_format==nil then t.txt_format = "&l : &v" end
    if t.nb_decimals==nil then t.nb_decimals=1 end
    if t.type_arc==nil then t.type_arc="l" end
    if t.inverse_l_arc==nil then t.inverse_l_arc=false end
    
    
    local function draw_sector(tablecolor,colorindex,pc,lastAngle,angle,radius,int_radius,gradient_effect,type_arc,inverse_l_arc)
        --draw a portion of arc
        radiuspc=(radius-int_radius)*pc+int_radius
        angle0=lastAngle
        val=1
        if type_arc=="l" then 
            val=pc;radiuspc=radius
        end
        angle1=angle*val

        if type_arc=="l" and inverse_l_arc then 

            cairo_save(cr)
    
            cairo_rotate(cr,angle0+angle)
            
            if gradient_effect then        
                local pat = cairo_pattern_create_radial (0,0, int_radius, 0,0,radius)
                cairo_pattern_add_color_stop_rgba (pat, 0, rgb_to_r_g_b(tablecolor[colorindex][1],0))
                cairo_pattern_add_color_stop_rgba (pat, 0.5, rgb_to_r_g_b(tablecolor[colorindex][1],tablecolor[colorindex][2]))
                cairo_pattern_add_color_stop_rgba (pat, 1, rgb_to_r_g_b(tablecolor[colorindex][1],0))
                cairo_set_source (cr, pat)
                cairo_pattern_destroy(pat)
            else
                cairo_set_source_rgba(cr,rgb_to_r_g_b(tablecolor[colorindex][1],tablecolor[colorindex][2]))
            end
            cairo_move_to(cr,0,-int_radius)
            cairo_line_to(cr,0,-radiuspc)
            cairo_rotate(cr,-math.pi/2)
        
            cairo_arc_negative(cr,0,0,radiuspc,0,-angle1)
            cairo_rotate(cr,-math.pi/2-angle1)
            cairo_line_to(cr,0,int_radius)
            cairo_rotate(cr,math.pi/2)
            cairo_arc(cr,0,0,int_radius,0,angle1)
            cairo_close_path (cr);
            cairo_fill(cr)

            cairo_restore(cr)
        else
        
            cairo_save(cr)
    
            cairo_rotate(cr,angle0)

            if gradient_effect then        
                local pat = cairo_pattern_create_radial (0,0, int_radius, 0,0,radius)
                cairo_pattern_add_color_stop_rgba (pat, 0, rgb_to_r_g_b(tablecolor[colorindex][1],0))
                cairo_pattern_add_color_stop_rgba (pat, 0.5, rgb_to_r_g_b(tablecolor[colorindex][1],tablecolor[colorindex][2]))
                cairo_pattern_add_color_stop_rgba (pat, 1, rgb_to_r_g_b(tablecolor[colorindex][1],0))
                cairo_set_source (cr, pat)
                cairo_pattern_destroy(pat)
            else
                cairo_set_source_rgba(cr,rgb_to_r_g_b(tablecolor[colorindex][1],tablecolor[colorindex][2]))
            end
            cairo_move_to(cr,0,-int_radius)
            cairo_line_to(cr,0,-radiuspc)
            cairo_rotate(cr,-math.pi/2)
        
            cairo_arc(cr,0,0,radiuspc,0,angle1)
            cairo_rotate(cr,angle1-math.pi/2)
            cairo_line_to(cr,0,int_radius)
            cairo_rotate(cr,math.pi/2)
            cairo_arc_negative(cr,0,0,int_radius,0,-angle1)
            cairo_close_path (cr);
            cairo_fill(cr)

            cairo_restore(cr)
        end
        

    end

    function draw_lines(idx,nbArcs,angle,table_colors,idx_color,adjust,line_lgth,length_txt,txt_offset,radius,line_width,line_space,font_color,font_alpha)
        --draw lines
        
        local x0=radiuspc*math.sin(lastAngle+angle/2)
        local y0=-radiuspc*math.cos(lastAngle+angle/2)
        local x1=1.2*radius*math.sin(lastAngle+angle/2)
        local y1=-1.2*radius*math.cos(lastAngle+angle/2)

        local x2=line_lgth
        local y2=y1
        local x3,y3=nil,nil
        if x0<=0 then
            x2=-x2
        end

        if adjust then
            if x0>0 and x2-x1<length_txt then x2=x1+length_txt end
            if x0<=0 and x1-x2<length_txt then x2=x1-length_txt end            
        end 
        
        if idx>1 then
            local dY = math.abs(y2-lastPt2[2])
            if dY < line_space and lastPt2[1]*x1>0 then
                if x0>0 then
                    y2 = line_space+lastPt2[2]
                else
                    y2 = -line_space+lastPt2[2]
                end
                if (y2>y1 and x0>0) or (y2<y1 and x0<0 )  then
                    --x3 is for vertical segment if needed
                    x3,y3=x2,y2                    
                    x2=x1
                    if x3>0 then x3=x3+txt_offset end
                else
                    Z=intercept({x0,y0},{x1,y1},{0,y2},{1,y2})
                    x1,y1=Z[1],Z[2]
                end
            end
        else
            --remind x2,y2 of first value
            x2first,y2first = x2,y2
        end

        if font_color==nil then
            cairo_set_source_rgba(cr,rgb_to_r_g_b(table_colors[idx_color][1],table_colors[idx_color][2]))
        else
            local pat = cairo_pattern_create_linear (x2,y2, x0,y0)
            cairo_pattern_add_color_stop_rgba (pat, 0, rgb_to_r_g_b(font_color,font_alpha))
            cairo_pattern_add_color_stop_rgba (pat, 1, rgb_to_r_g_b(table_colors[idx_color][1],table_colors[idx_color][2]))
            cairo_set_source (cr, pat)
            cairo_pattern_destroy(pat)
        end

        
        cairo_move_to(cr,x0,y0)
        cairo_line_to(cr,x1,y1)
        cairo_line_to(cr,x2,y2)
        if x3~=nil then 
            cairo_line_to(cr,x3,y3)
            x2,y2=x3,y3    
        end
        cairo_set_line_width(cr,line_width)
        cairo_stroke(cr)
        --lastAngle=lastAngle+angle
        return {x2,y2}
    end
    
    function intercept(p11,p12,p21,p22)
        --calculate interscetion of two lines and return coordinates
        a1=(p12[2]-p11[2])/(p12[1]-p11[1])

        a2=(p22[2]-p21[2])/(p22[1]-p21[1])

        b1=p11[2]-a1*p11[1]

        b2=p21[2]-a2*p21[1]

        X=(b2-b1)/(a1-a2)

        Y=a1*X+b1
        return {X,Y}
    end

    --some checks
    if t.first_angle>=t.last_angle then
        local tmp_angle=t.last_angle
        --t.last_angle=t.first_angle
        --t.first_angle=tmp_angle
        print ("inversed angles")
    end

    if t.last_angle-t.first_angle>360 and t.first_angle>0 then
        t.last_angle=360+t.first_angle
        print ("reduce angles")
    end
    
    if t.last_angle+t.first_angle>360 and t.first_angle<=0 then
        t.last_angle=360+t.first_angle
        print ("reduce angles")
    end
    
    if t.int_radius<0 then t.int_radius =0 end
    if t.int_radius>t.radius then
        local tmp_radius=t.radius
        t.radius=t.int_radius
        t.int_radius=tmp_radius
        print ("inversed angles")
    end
    if t.int_radius==t.radius then
        t.int_radius=0
        print ("int radius set to 0")
    end    
    --end of checks
    
    cairo_save(cr)
    cairo_translate(cr,t.xc,t.yc)
    cairo_set_line_join (cr, CAIRO_LINE_JOIN_ROUND)
    cairo_set_line_cap (cr, CAIRO_LINE_CAP_ROUND)
    
    local nbArcs=#tableV
    local anglefull= (t.last_angle-t.first_angle)*math.pi/180
    local fullsize = 0
    for i= 1,nbArcs do
        fullsize=fullsize+tableV[i][4]
    end

    local cb,cf,angle=0,0,anglefull/nbArcs
    lastAngle=t.first_angle*math.pi/180
    lastPt2={nil,nil}

    for i =1, nbArcs do
        if t.proportional then
            angle=tableV[i][4]/fullsize*anglefull
        end
        --set colours
        cb,cf=cb+1,cf+1
        if cb>#t.tablebg then cb=1 end
        if cf>#t.tablefg then cf=1 end
        
        if tableV[i][2]~="" then
            str=string.format('${%s %s}',tableV[i][2],tableV[i][3])
        else
            str = tableV[i][3]
        end
        str=conky_parse(str)
        value=tonumber(str)
        if value==nil then value=0 end
    
        --draw sectors
        draw_sector(t.tablebg,cb,1,lastAngle,angle,t.radius,t.int_radius,t.gradient_effect,t.type_arc,t.inverse_l_arc)
        --print (t.tablefg,cf,tableV[i][2],tableV[i][3],lastAngle,angle,t.radius,t.int_radius)
        --print (cf,tableV[i],tableV[i][2],tableV[i][3])
        draw_sector(t.tablefg,cf,value/tableV[i][4],lastAngle,angle,t.radius,t.int_radius,t.gradient_effect,t.type_arc,t.inverse_l_arc)

        if t.show_text then
            --draw text
            local txt_l   = tableV[i][1]
            local txt_opc = round(100*value/tableV[i][4],t.nb_decimals).."%%"
            local txt_fpc = round(100*(tableV[i][4]-value/tableV[i][4]),t.nb_decimals).."%%"
            local txt_ov,txt_fv,txt_max
            if tableV[i][5]==true then
                txt_ov  = size_to_text(value,t.nb_decimals)
                txt_fv  = size_to_text(tableV[i][4]-value,t.nb_decimals)
                txt_max = size_to_text(tableV[i][4],t.nb_decimals)
            else
                if tableV[i][5]=="%" then tableV[i][5]="%%" end
                txt_ov=string.format("%."..t.nb_decimals.."f ",value)..tableV[i][5]
                txt_fv=string.format("%."..t.nb_decimals.."f",tableV[i][4]-value)..tableV[i][5]
                txt_max=string.format("%."..t.nb_decimals.."f",tableV[i][4])..tableV[i][5]
            end
            txt_pc = string.format("%."..t.nb_decimals.."f",100*tableV[i][4]/fullsize).."%%"
            local txt_out = t.txt_format
            txt_out = string.gsub(txt_out,"&l",txt_l)  --label
            txt_out = string.gsub(txt_out,"&o",txt_opc)--occ. %
            txt_out = string.gsub(txt_out,"&f",txt_fpc)--free %
            txt_out = string.gsub(txt_out,"&v",txt_ov) --occ. value
            txt_out = string.gsub(txt_out,"&n",txt_fv) --free value
            txt_out = string.gsub(txt_out,"&m",txt_max)--max
            txt_out = string.gsub(txt_out,"&p",txt_pc)--percent
            
            local te=cairo_text_extents_t:create()
            cairo_set_font_size(cr,t.font_size)
            cairo_select_font_face(cr, t.txt_font, CAIRO_FONT_SLANT_NORMAL, CAIRO_FONT_WEIGHT_NORMAL)
            cairo_text_extents (cr,txt_out,te)

            --draw lines 
            lastPt2=draw_lines(i,nbArcs,angle,t.tablefg,cf,t.extend_line,t.line_lgth+t.radius, 
                    te.width + te.x_bearing,t.txt_offset,t.radius,t.line_width,t.line_space,t.font_color,t.font_alpha)    
        
            local xA=lastPt2[1]
            local yA=lastPt2[2]-t.line_width-t.txt_offset
            if xA>0 then xA = xA-(te.width + te.x_bearing) end
            cairo_move_to(cr,xA,yA)
            cairo_show_text(cr,txt_out)
        end
        
        lastAngle=lastAngle+angle
    end
    cairo_restore(cr)
end

--[[END OF PIE CHART WIDGET]]

```the conkyrc :
```

# -- Conky settings -- #
background no
update_interval 1

cpu_avg_samples 2
net_avg_samples 2

override_utf8_locale yes

double_buffer yes
no_buffers yes

text_buffer_size 2048
imlib_cache_size 0

own_window_type desktop
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below
own_window yes
own_window_transparent no
own_window_title pie-chart v1.2

border_inner_margin 0
border_outer_margin 0

minimum_size 300 800
alignment tl

# -- Graphics settings -- #
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no


# -- Lua load -- #
lua_load ~/ll/pie1.2/piechart.lua
lua_draw_hook_post main_pie

#at least one line after TEXT
TEXT

```The output :
_[[IMG]http://pix.toile-libre.org/upload/img/1275342758.png[/IMG]]("http://pix.toile-libre.org/?img=1275342758.png")_
  
This is the set-up I use for my little notebook, from top to bottom : 
1-clock (yes it is !)
2-adress and speeds for wlan0 (adapt the Lua script if you don't use wlan0)
3-disk usage (note that if your system automatically mount the external drives, this ring is updated, nothing else to do !)
4-cpu usage (cpu0 and cpu1)
5-memory and swap

Fell free to ask if you have more problems or suggestions !

---

### Post by Jaa(c) on 2010-06-01
Thanks for all the help, it works.. Lua does seem quite easy, I managed to do some adjustments... Thanks, I realy like it :)

---

### Post by acbatman54 on 2010-06-03
Hey all... just wanted to throw my Conky setup out there in case anyone needed some ideas or code. I admit it may not be the flashiest looking or the best scripted configs but it does what I want it to do. I take partial credit for it since a lot of the code is copied and pasted from several others but I managed to get it all working together. It took a lot of Trial and Error with plenty of Time and Frustration but I think it came out pretty nice.

Notes: I installed conkyforecast for the weather stuff. Also, I didn't like having Conky using several scripts to get things done so I did most of the stuff within the config files.

P.S. I have my Conky scripts autostart using "sudo" so they get full functionality. I know I have a major security violation leaving a password in a .txt file but I just haven't gotten around to changing it yet. I dare not post the line that does the auto start as "sudo" with password because it's just a bad way to do business.

Good Luck to everyone!

Edit: Reattached conkyrc_timedateweather.txt file to fix an issue. Sorry.

---

### Post by dk75 on 2010-08-14
Regarding **Mahngiel**@ forum script from **.conkyrc** thread here is my RAW engine for that.


> **Mahngiel said:**
> care to put your fingers to use and give me an example? i've never bothered with lua, but i've taken care of all the piping via curl:

isolate the forum - check
```
curl -s 'http://www.linux-hardcore.com/forum/index.php' | grep -n '<td class="middletext' | awk -F'a>' '{print $3}' | awk -F'">' '{print $2}' | awk -F '<' '{print $1}' | sed -n '1p'
```

identify the new post - check
```
curl -s 'http://www.linux-hardcore.com/forum/index.php' | grep -n '<td class="middletext' | awk -F'">Re:' '{print $2}' | awk -F'</a>' '{print $1}' | sed -n -e '1 p'
```

identify the author - check
```
curl -s 'http://www.linux-hardcore.com/forum/index.php' | grep -n '<td class="middletext' | sed -n '1 p' | awk -F'</b>' '{print $2}' | awk -F'">' '{print $2}' | awk -F'</a>' '{print $1}'
```

identify the time - check
```
curl -s 'http://www.linux-hardcore.com/forum/index.php' | grep -n '<td class="middletext' | awk -F'</b> at' '{print $2}' | sed -n '2 p' | awk -F'<' '{print $1}'
```

Now, to put it to file, objectify it, and output specific results via a stdout - uncheck. 
:help:

There is my more efficient code.
Only one curl, only one bash command (awk), no file save and no file read:

```
#!/bin/bash
curl -s 'http://www.linux-hardcore.com/forum/index.php' |awk --posix -F"\">" -v new1=$1 'BEGIN{for (x=1; x<new1; x++) y=(y+2); var0=1} /<td class=\"middletext\"/ {if (var0==(y+1)) {sub(/<.*/,"",$NF); sub(/<.*/,"",$(NF-1)); sub(/<.*/,"",$(NF-2)); farr[1]=$NF; farr[2]=$(NF-1); farr[3]=$(NF-2)}; if (var0==(y+2)) {gsub(/\<.{1,3}\>/,"",$NF); farr[4]=$NF; exit}; ++var0} END{print farr[4],".:.",farr[1],".:.",farr[2],".:.",farr[3]}'
```

save as lhf.sh file and use as:
```
lhf.sh 1
```
and this gives you first new forum post from linux-hardcore
```
Today at 01:43:28 PM .:. Conky Hardcore! Support Forum .:. Mahngiel .:. Re: Conk Hardcore has moved - New Owner, New Domain
```

---

### Post by pt123 on 2010-08-14
see my signature for more info

---

### Post by Mahngiel on 2010-08-14
> **dk75 said:**
> Regarding **Mahngiel**@ forum script from **.conkyrc** thread here is my RAW engine for that.




There is my more efficient code.
Only one curl, only one bash command (awk), no file save and no file read:

```
#!/bin/bash
curl -s 'http://www.linux-hardcore.com/forum/index.php' |awk --posix -F"\">" -v new1=$1 'BEGIN{for (x=1; x<new1; x++) y=(y+2); var0=1} /<td class=\"middletext\"/ {if (var0==(y+1)) {sub(/<.*/,"",$NF); sub(/<.*/,"",$(NF-1)); sub(/<.*/,"",$(NF-2)); farr[1]=$NF; farr[2]=$(NF-1); farr[3]=$(NF-2)}; if (var0==(y+2)) {gsub(/\<.{1,3}\>/,"",$NF); farr[4]=$NF; exit}; ++var0} END{print farr[4],".:.",farr[1],".:.",farr[2],".:.",farr[3]}'
```save as lhf.sh file and use as:
```
lhf.sh 1
```and this gives you first new forum post from linux-hardcore
```
Today at 01:43:28 PM .:. Conky Hardcore! Support Forum .:. Mahngiel .:. Re: Conk Hardcore has moved - New Owner, New Domain
```

That's pretty sexy. Thanks a ton for that. :kudos:

Mind having a look [ [here]("http://ubuntuforums.org/showpost.php?p=9718211&postcount=13490") ] and let me know what you think?

---

### Post by guriinii on 2010-08-27
Hi, I've just added arpinux's 'zen-lua' script to conky (which works to a certain degree). After adding it to my start up script it takes control of my desktop, making me unable access anything.

When I run the script via terminal this is what I get:
```
:~$ conseg.sh
Conky: desktop window (9a) is root window
Conky: window type - override
Conky: drawing to created window (0x2200001)
Conky: drawing to double buffer
Conky: llua_do_call: function conky_ring_stats execution failed: /home/greenys/scripts/zen-rings1.lua:157: attempt to perform arithmetic on local 'value' (a nil value)
Conky: desktop window (9a) is root window
Conky: window type - override
Conky: drawing to created window (0x2400001)
Conky: drawing to double buffer
Conky: llua_do_call: function conky_ring_stats execution failed: /home/greenys/scripts/zen-rings2.lua:131: attempt to perform arithmetic on local 'value' (a nil value)
Conky: llua_do_call: function conky_ring_stats execution failed: /home/greenys/scripts/zen-rings2.lua:131: attempt to perform arithmetic on local 'value' (a nil value)


```

Can anyone help?
Oh, thanks to arpinux for his mini how to and scripts from deviant art, lua and cairo has had me stumped for ages, and now I get it (kind of).

---

### Post by dk75 on 2010-08-27
yeah... you have some empty value... but without actual script it's hard to say...

---

### Post by guriinii on 2010-08-27
> **dk75 said:**
> yeah... you have some empty value... but without actual script it's hard to say...

Here you go, first rc

```
# — Conky settings — #
background no
update_interval 1

cpu_avg_samples 2
net_avg_samples 2

override_utf8_locale yes

double_buffer yes
no_buffers yes

text_buffer_size 2048
imlib_cache_size 0

# — Window specifications — #

own_window yes
own_window_type override
own_window_transparent yes
own_window_colour 3B3B3B
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below

border_inner_margin 0
border_outer_margin 0

minimum_size 300 620
maximum_width 300

alignment tl
gap_x 55
gap_y 110

# — Graphics settings — #
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no

# — Text settings — #
use_xft yes
xftfont D3 Euronism:size=44
xftalpha 0.8

uppercase no

default_color A0A0A0

# — Lua Load — #
lua_load ~/scripts/zen-rings1.lua
lua_draw_hook_pre ring_stats

TEXT
${alignr 7}${color 467F77}${time %H}
${voffset -20}${alignr 7}${color 828282}${time %M}
${voffset 10}${goto 70}${font Aller:size10:italic}up: ${uptime_short}${alignr 42}${voffset -5}${time %S}${color}${font}
${voffset 105}${font D3 Euronism:size=16:italic}    ${color}${time %a}
    ${time %d}   
    ${time %b}  
${voffset 75}${goto 160}${if_match ${battery_percent BAT1} > 20}${color 60ADA2}PW${color}${endif}${if_match ${battery_percent BAT1} <= 20}${color red}PW${color}${endif}
${goto 150}${if_match ${battery_percent BAT1} > 10}${color 7ECCC0}${battery_percent BAT1}%${color}${endif}${if_match ${battery_percent BAT1} <= 10}${color red}${battery_percent BAT1}%${color}${endif}
```

lua1:
```

settings_table = {
	{
		name='time',
		arg='%I',
		max=12,
		bg_colour=0xffffff,
		bg_alpha=0,
		fg_colour=0x74C2B7,
		fg_alpha=0.8,
		x=113, y=92,
		radius=25,
		thickness=15,
		angle=0
	},
	{
		name='time',
		arg='%M',
		max=60,
		bg_colour=0x000000,
		bg_alpha=0.1,
		fg_colour=0xffffff,
		fg_alpha=0.6,
		x=113, y=92,
		radius=40,
		thickness=10,
		angle=0
	},
	{
		name='time',
		arg='%S',
		max=60,
		bg_colour=0x000000,
		bg_alpha=0.1,
		fg_colour=0x4D4D4D,
		fg_alpha=0.8,
		x=249.5, y=170,
		radius=36,
		thickness=8,
		angle=35
	},
	{
		name='battery_percent BAT1',
		arg='',
		max=100,
		bg_colour=0xffffff,
		bg_alpha=0.1,
		fg_colour=0x2BBCFF,
		fg_alpha=0.8,
		x=187.5, y=546,
		radius=55,
		thickness=6,
		angle=51
	},
	{
		name='swapperc',
		arg='',
		max=100,
		bg_colour=0x000000,
		bg_alpha=0.1,
		fg_colour=0x000000,
		fg_alpha=0.6,
		x=63, y=255,
		radius=54,
		thickness=3,
		angle=51
	},
	{
		name='fs_used_perc',
		arg='/',
		max=100,
		bg_colour=0xffffff,
		bg_alpha=0,
		fg_colour=0xffffff,
		fg_alpha=0.2,
		x=63, y=255,
		radius=24,
		thickness=16,
		angle=0
	},
	{
		name='fs_used_perc',
		arg='/home',
		max=100,
		bg_colour=0xffffff,
		bg_alpha=0,
		fg_colour=0xffffff,
		fg_alpha=0.4,
		x=63, y=255,
		radius=42,
		thickness=13,
		angle=0
	},
}

require 'cairo'

function rgb_to_r_g_b(colour,alpha)
	return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
end

function draw_ring(t, pt)
	if conky_window==nil then return end
	local w,h=conky_window.width,conky_window.height
	local cs=cairo_xlib_surface_create(conky_window.display,conky_window.drawable,conky_window.visual,w,h)
	
	cr=cairo_create(cs)
	
	local xc,yc,ring_r,ring_w,angle=pt['x'],pt['y'],pt['radius'],pt['thickness'],pt['angle']
	local bgc, bga, fgc, fga=pt['bg_colour'], pt['bg_alpha'], pt['fg_colour'], pt['fg_alpha']

	local angle_0=angle*(2*math.pi/360)-math.pi/2
	local t_arc=t*2*math.pi

	-- Draw background ring

	cairo_arc(cr,xc,yc,ring_r,0,2*math.pi)
	cairo_set_source_rgba(cr,rgb_to_r_g_b(bgc,bga))
	cairo_set_line_width(cr,ring_w)
	cairo_stroke(cr)
	
	-- Draw indicator ring

	cairo_arc(cr,xc,yc,ring_r,angle_0,angle_0+t_arc)
	cairo_set_source_rgba(cr,rgb_to_r_g_b(fgc,fga))
	cairo_stroke(cr)		
	
	cairo_destroy(cr)
	cr = nil
end

function conky_cairo_cleanup()
	cairo_surface_destroy(cs)
	cs = nil
end

function conky_ring_stats()
	local function setup_rings(pt)
		local str=''
		local value=0
		
		str=string.format('${%s %s}',pt['name'],pt['arg'])
		str=conky_parse(str)
		
		value=tonumber(str)
		pct=value/pt['max']
		
		draw_ring(pct,pt)
	end
	
	-- Check that Conky has been running for at least 5s
	
	local updates=conky_parse('${updates}')
	update_num=tonumber(updates)
	
	if update_num>5 then
		for i in pairs(settings_table) do
			setup_rings(settings_table[i])
		end
	end
end
```

second rc:
```
# — Conky settings — #
background no
update_interval 1

cpu_avg_samples 2
net_avg_samples 2

override_utf8_locale yes

double_buffer yes
no_buffers yes

text_buffer_size 2048
imlib_cache_size 0

# — Window specifications — #

own_window yes
own_window_type override
own_window_transparent yes
own_window_colour grey20
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below

border_inner_margin 0
border_outer_margin 0

minimum_size 200 420
maximum_width 200

alignment br
gap_x 5
gap_y 0

# — Graphics settings — #
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no

# — Text settings — #
use_xft yes
xftfont D3 Euronism:size=14
xftalpha 0.8

uppercase no

default_color A0A0A0

# — Lua Load — #
lua_load ~/scripts/zen-rings2.lua
lua_draw_hook_pre ring_stats

TEXT
${voffset 330}${goto 127}${font cellpic:size=50}u${font}
```

lua2:
```

settings_table = {
	{
		-- Edit this table to customise your rings.
		-- You can create more rings simply by adding more elements to settings_table.
		-- "name" is the type of stat to display; you can choose from 'cpu', 'memperc', 'fs_used_perc', 'battery_used_perc'.
		name='cpu',
		-- "arg" is the argument to the stat type, e.g. if in Conky you would write ${cpu cpu0}, 'cpu0' would be the argument. If you would not use an argument in the Conky variable, use ''.
		arg='cpu0',
		-- "max" is the maximum value of the ring. If the Conky variable outputs a percentage, use 100.
		max=100,
		-- "bg_colour" is the colour of the base ring.
		bg_colour=0xffffff,
		-- "bg_alpha" is the alpha value of the base ring.
		bg_alpha=0.1,
		-- "fg_colour" is the colour of the indicator part of the ring.
		fg_colour=0xD94600,
		-- "fg_alpha" is the alpha value of the indicator part of the ring.
		fg_alpha=0.8,
		-- "x" and "y" are the x and y coordinates of the centre of the ring, relative to the top left corner of the Conky window.
		x=62, y=63,
		-- "radius" is the radius of the ring.
		radius=38,
		-- "thickness" is the thickness of the ring, centred around the radius.
		thickness=20,
		-- "angle" is the starting angle of the ring, in degrees, clockwise from top. Value can be either positive or negative.
		angle=51
	},
	{
		name='memperc',
		arg='',
		max=100,
		bg_colour=0xffffff,
		bg_alpha=0,
		fg_colour=0x30DEFF,
		fg_alpha=0.4,
		x=62, y=63,
		radius=19,
		thickness=13,
		angle=90
	},
	{
		name='upspeedf',
		arg='wlan0',--upspeed
		max=600,
		bg_colour=0x000000,
		bg_alpha=0.1,
		fg_colour=0x28FAFF,
		fg_alpha=0.6,
		x=148, y=347,
		radius=18,
		thickness=12,
		angle=-120
	},
	{
		name='downspeedf',
		arg='wlan0',--upspeed
		max=1500,
		bg_colour=0xffffff,
		bg_alpha=0.1,
		fg_colour=0x284EFF,
		fg_alpha=0.6,
		x=148, y=390,
		radius=18,
		thickness=12,
		angle=60
	},
}

require 'cairo'

function rgb_to_r_g_b(colour,alpha)
	return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
end

function draw_ring(t, pt)
	if conky_window==nil then return end
	local w,h=conky_window.width,conky_window.height
	local cs=cairo_xlib_surface_create(conky_window.display,conky_window.drawable,conky_window.visual,w,h)
	
	cr=cairo_create(cs)
	
	local xc,yc,ring_r,ring_w,angle=pt['x'],pt['y'],pt['radius'],pt['thickness'],pt['angle']
	local bgc, bga, fgc, fga=pt['bg_colour'], pt['bg_alpha'], pt['fg_colour'], pt['fg_alpha']

	local angle_0=angle*(2*math.pi/360)-math.pi/2
	local t_arc=t*2*math.pi

	-- Draw background ring

	cairo_arc(cr,xc,yc,ring_r,0,2*math.pi)
	cairo_set_source_rgba(cr,rgb_to_r_g_b(bgc,bga))
	cairo_set_line_width(cr,ring_w)
	cairo_stroke(cr)
	
	-- Draw indicator ring

	cairo_arc(cr,xc,yc,ring_r,angle_0,angle_0+t_arc)
	cairo_set_source_rgba(cr,rgb_to_r_g_b(fgc,fga))
	cairo_stroke(cr)		
	
	cairo_destroy(cr)
	cr = nil
end

function conky_cairo_cleanup()
	cairo_surface_destroy(cs)
	cs = nil
end

function conky_ring_stats()
	local function setup_rings(pt)
		local str=''
		local value=0
		
		str=string.format('${%s %s}',pt['name'],pt['arg'])
		str=conky_parse(str)
		
		value=tonumber(str)
		pct=value/pt['max']
		
		draw_ring(pct,pt)
	end
	
	-- Check that Conky has been running for at least 5s
	
	local updates=conky_parse('${updates}')
	update_num=tonumber(updates)
	
	if update_num>5 then
		for i in pairs(settings_table) do
			setup_rings(settings_table[i])
		end
	end
end
```

Hope this helps.

---

### Post by dk75 on 2010-08-27
OK.
In bot cases it is fault in expression ```
str=conky_parse(str)
``` which takes non numeric value in first loop (first loop of function with **conky_parse**) and expression ```
value=tonumber(str)
``` gives **[COLOR="DarkOrange"]NIL[/COLOR]** as a result.

After that ```
pct=value/pt['max']
``` ends with error (you can't do arithmetics with **[COLOR="DarkOrange"]NIL[/COLOR]**).

So, in both LUA scripts you must change lines
```
value=tonumber(str)
pct=value/pt['max']
```
to
```
value=tonumber(str)
[COLOR="Red"]if value==nil then value=0 end[/COLOR]
pct=value/pt['max']
```

---

### Post by guriinii on 2010-08-27
@dk75 Thanks, that's sorted it. 

I have another issue. When I add my script to the start up, conky becomes my entire desktop and unable to do anything. Apart from Alt+F1 to comment the script out.

---

### Post by dk75 on 2010-08-27
Evaluate.

Conky can be transparent but you can't have access to the desktop beneath.
If you wan't it then either resize Conky and move it to place were it won't block your icons or... don't use Conky at all.

---

### Post by guriinii on 2010-08-27
Problem resolved, Thanks for your help.

---

### Post by Sector11 on 2010-09-22
> **wlourf said:**
> Hi folks !

The 3 files are in the attachment.

Happy conkying :P

Ummm... what attachment?

---

### Post by wlourf on 2010-09-23
well , the 3 files are in the post, you have to copy them!

But I found another method for rounded images with a script 
[http://ubuntuforums.org/showpost.php?p=8117609&postcount=9846](http://ubuntuforums.org/showpost.php?p=8117609&postcount=9846)
it only use convert form ImageMagik but it seems the image is not so "clean" with this method  (ie : convert add some noise to the image ).
I can post the script to get moon/earth used with conky if you want

---

### Post by Xsoldier2000 on 2010-11-23
Wow, you weren't kidding about the other thread being over run...

So, I'm posting here also in hopes someone can help.

Conky Clock Help 

--------------------------------------------------------------------------------

So, I've got this conky clock setup, and have everything functional except the eth0 bar graph. If you take a look at the desktop attached, you'll see what everything represents, and where I need the help.

Where you see the eth0 up/dn is where I would like the graph to display, but when I use the code:


```
{
		name='upspeedf',
		arg='eth0',
		max=-100,
		bg_colour=0xffffff,
		bg_alpha=0.2,
		fg_colour=0xffffff,
		fg_alpha=0.5,
		x=160, y=155,
		radius=75.5,
		thickness=4.5,
		start_angle=-27,
		end_angle=85
	},
	{
		name='downspeedf',
		arg='eth0',
		max=-100,
		bg_colour=0xffffff,
		bg_alpha=0.2,
		fg_colour=0xffffff,
		fg_alpha=0.5,
		x=160, y=155,
		radius=80.5,
		thickness=4.5,
		start_angle=-27,
		end_angle=85
	},
```

It maxes out and overwrites the other graphs. (In this case my CPU's)I've also tried setting the name to upspeedgraph and upspeed (For the uploading part) and get nothing.

Am I using the right command? How do I keep it within the start and end angles?

P.S. The clock_rings.zip contains the clock_rings.lua

---

### Post by Lancro on 2010-11-23
I dont know anything about conky, I have it, I execute it, and then Its shows me the uname -a, the cpu and ram ussage, but background is not transparent, and it blicks each second, so I have to killall, anyone can recomend me a link or something to get started with conky?, I like it with transparent background, without blinking each second, and the rest of stuff.

Thanks.

---

### Post by dmillerct on 2010-11-23
> **Lancro said:**
> I dont know anything about conky, I have it, I execute it, and then Its shows me the uname -a, the cpu and ram ussage, but background is not transparent, and it blicks each second, so I have to killall, anyone can recomend me a link or something to get started with conky?, I like it with transparent background, without blinking each second, and the rest of stuff.

Thanks.

Everything you need to know: [http://conky-pitstop.wikidot.com/]("http://conky-pitstop.wikidot.com/")

Variables (old?): [http://conky.sourceforge.net/variables.html]("http://conky.sourceforge.net/variables.html")

---

### Post by Lancro on 2010-11-23
A bad tutorial or a bad student, dont know, but I cant get it working.

---

### Post by wlourf on 2010-11-23
> **Lancro said:**
> A bad tutorial or a bad student, dont know, but I cant get it working.
Did you try this trick : [http://conky-pitstop.wikidot.com/howto-s#toc16](http://conky-pitstop.wikidot.com/howto-s#toc16) ?
Or post your conky in the mega thread :
[http://ubuntuforums.org/showthread.php?t=281865&page=12090](http://ubuntuforums.org/showthread.php?t=281865&page=12090)

> **Xsoldier2000 said:**
> Wow, you weren't kidding about the other thread being over run...

So, I'm posting here also in hopes someone can help.

Conky Clock Help 

--------------------------------------------------------------------------------

So, I've got this conky clock setup, and have everything functional except the eth0 bar graph. If you take a look at the desktop attached, you'll see what everything represents, and where I need the help.

Where you see the eth0 up/dn is where I would like the graph to display, but when I use the code:


```
{
        name='upspeedf',
        arg='eth0',
        max=-100,
        bg_colour=0xffffff,
        bg_alpha=0.2,
        fg_colour=0xffffff,
        fg_alpha=0.5,
        x=160, y=155,
        radius=75.5,
        thickness=4.5,
        start_angle=-27,
        end_angle=85
    },
    {
        name='downspeedf',
        arg='eth0',
        max=-100,
        bg_colour=0xffffff,
        bg_alpha=0.2,
        fg_colour=0xffffff,
        fg_alpha=0.5,
        x=160, y=155,
        radius=80.5,
        thickness=4.5,
        start_angle=-27,
        end_angle=85
    },
```It maxes out and overwrites the other graphs. (In this case my CPU's)I've also tried setting the name to upspeedgraph and upspeed (For the uploading part) and get nothing.

Am I using the right command? How do I keep it within the start and end angles?


yes, you're using the right command : downspeed**f** but is there a reason that your max argument is negative. Usually, it is :
```
max=xx,
``` where xx is your maximum bandwidth (1000 for 1000 k/s for example) : downspeedf doesn't display a percentage but a speed, try it in a conky and you will see !

---

### Post by Xsoldier2000 on 2010-11-23
> **wlourf said:**
> 
yes, you're using the right command : downspeed**f** but is there a reason that your max argument is negative. Usually, it is :
```
max=xx,
``` where xx is your maximum bandwidth (1000 for 1000 k/s for example) : downspeedf doesn't display a percentage but a speed, try it in a conky and you will see !

It was set at max=100 but when it overshot the end angle, I thought the 100 meant %... so I started decreasing the max argument...now it makes more sense. So my max down load speed is 4mb/s max=4000 correct?
 (@ work at the moment, will try it tonight.)

EDIT: That did it! Thanks so much! Funny how one little thing can set the universe right again, huh?

---

### Post by miegiel on 2010-11-24
> **Lancro said:**
> I dont know anything about conky, I have it, I execute it, and then Its shows me the uname -a, the cpu and ram ussage, but background is not transparent, and it blicks each second, so I have to killall, anyone can recomend me a link or something to get started with conky?, I like it with transparent background, without blinking each second, and the rest of stuff.

Thanks.

While **Xsoldier2000**'s post was better placed here, yours is better placed in [http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865) ;)

> **Lancro said:**
> A bad tutorial or a bad student, dont know, but I cant get it working.

See "[When &#8220;blinking&#8221; isn&#8217;t!]("http://conky-pitstop.wikidot.com/howto-s#toc16")" for inspiration. I tink [maximum_width and minimum_size]("http://conky.sourceforge.net/config_settings.html") will be your friends, or enemies. In any case keep them closer.

There's stuff on transparency on those sites too. I Use this conky to make a empty transparent panel.

```
# You can find info on the stuff above TEXT here : http://conky.sourceforge.net/config_settings.html
# You can find info on the stuff below TEXT here : http://conky.sourceforge.net/variables.html
#
minimum_size 1024 24
maximum_width 1024
gap_x 0
gap_y 0
alignment tm
update_interval 1440.0
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
uppercase no
own_window yes
[COLOR="Blue"]own_window_argb_visual yes[/COLOR] # Boolean, use ARGB visual? ARGB can be used for real transparency, note that a composite manager is required for real transparency. This option will not work as desired (in most cases) in conjunction with 'own_window_type override'.
# own_window_argb_value # When ARGB visuals are enabled, this use this to modify the alpha value used. Valid range is 0-255, where 0 is 0% opacity, and 255 is 100% opacity.
own_window_type [COLOR="Red"]panel[/COLOR] # normal(default), desktop, dock, panel or override
[COLOR="blue"]own_window_transparent yes[/COLOR] # needs 'own_window_argb_visual yes'
own_window_hints undecorated,below,sticky # undecorated,above,below,sticky,skip_taskbar,skip_pager
#own_window_colour black
double_buffer yes
use_xft yes
xftfont sans:size=2
default_color 999999

TEXT

```

---

### Post by labinnsw on 2010-12-31
Apart from the title and the start date, what's the difference between this thread and [the one found here?]("http://ubuntuforums.org/showthread.php?t=281865")

---

### Post by mobilediesel on 2010-12-31
> **labinnsw said:**
> Apart from the title and the start date, what's the difference between this thread and [the one found here?]("http://ubuntuforums.org/showthread.php?t=281865")

The other thread was meant to show off what you have. This one is meant more for getting help making something work.

---

### Post by labinnsw on 2010-12-31
> **mobilediesel said:**
> This one is meant more for getting help making something work. You are aware that the other thread also covers this?

---

### Post by mobilediesel on 2010-12-31
> **labinnsw said:**
> You are aware that the other thread also covers this?

Since I've been following that thread for almost three years I would say yes.

---

### Post by matcatc on 2011-01-15
I wrote a simply python script to check for updates via apt-get. Its available here: [http://github.com/matcatc/ubuntu_updates_avail]("https://github.com/matcatc/ubuntu_updates_avail")

Here is a screen shot (the part towards the bottom):

[IMG]http://matcatc.github.com/ubuntu_updates_avail/conky.png[/IMG]
[http://matcatc.github.com/ubuntu_updates_avail/conky.png](http://matcatc.github.com/ubuntu_updates_avail/conky.png)

Matthew Todd

---

### Post by mrpeachy on 2011-05-24
so we can write functions in a lua script and send them variables via the conkyrc

like
```

function conky_draw_x(a, b, c)
do something
end

```in conkyrc
```

${lua conky_draw_x a b c}

```so a nice simple example
```

function conky_draw_text(text,x,y)
local cs = cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, conky_window.width, conky_window.height)
local cr = cairo_create(cs)
font="Mono"
fontsize=14
cairo_set_source_rgba (cr,1,1,1,1)
cairo_select_font_face (cr, font, CAIRO_FONT_SLANT_NORMAL, CAIRO_FONT_WEIGHT_BOLD);
cairo_set_font_size (cr, fontsize);
cairo_move_to (cr,x,y)
cairo_show_text (cr,text)
cairo_stroke (cr)
return ""
end

```in conkyrc
```

${lua conky_draw_text hello 100 200}

```displays hello at coordinates 100,200

but
```

 ${lua conky_draw_text hello world 100 200}
 
```wouldnt work because the space between hello and world is a delimiter
question - is there any way to prevent this?  putting "hello world" doesn't work



Then say i wanted to display the output of ${cpu cpu0} through lua
```

${lua conky_draw_text ${cpu cpu0} 100 200}

```doesnt work... (i didnt really expect it to :) )
right now the function is taking ${cpu as the text, and giving me an error because it is taking cpu0} as the x coordinate

if we wanted to do something like a ring setup from the conkyrc for example

edit... i guess a conky variable should be expected by the lua function, taken and parsed in lua to get the data out...

---

### Post by kit_oz on 2011-12-14
> **mrpeachy said:**
> 

You may use construction like this
```
function conky_test (...)
    local t={}
    for k, v in string.gmatch(table.concat(arg, ' '), '--([_a-zA-Z0-9]+)=([-_a-z0-9 ]+) ') do
        t[k] = v
    end
    ...
end
```
with this call from conkyrc
```
${lua test --text=blah blah blah --x=10 --y=20}
```
If add here filling missing variables
```
    if t.text == nil then t.text = 'blah blah blah' end
```
then we get pretty quick way to call functions from TEXT section

---

### Post by dk75 on 2012-04-05
OK.
I'm reviving thread because I'm doing something with LUA and I think it might interest few LUA devs.
Thing is thought that this project is in ALPHA state so it's no quiet ready for main Conky thread to post (thought I did it yesterday or so ;P ).

So there it is, one4all project and that's what it can do:
I've copied "londonali1010_airclock.module" from "/available" directory to "/active" 5 times with different names and the only thing I did was to change colors and placing of each clock.

There is conkyrc:
```
#-----Conky settings
background no
no_buffers yes
out_to_console no
top_cpu_separate yes
cpu_avg_samples 10
net_avg_samples 10
max_port_monitor_connections 10
update_interval 1
total_run_times 0

#-----Text setings
use_xft yes
xftfont Bitstream Vera Sans Mono:size=9
xftalpha 0.8
uppercase no
override_utf8_locale yes
format_human_readable no
#short_units
#max_user_text 64
#text_buffer_size 256

#-----Window settings
own_window yes
own_window_type override
#own_window_argb_visual yes
#own_window_argb_value 255
own_window_transparent yes
own_window_colour hotpink
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_class Conky
own_window_title ConkyMRClock

#----Layout settings
minimum_size 600 600
maximum_width 800
alignment top_right
use_spacer right
gap_x 50
gap_y 50

#-----Graphics settings
draw_shades no
draw_outline no
draw_borders yes
draw_graph_borders yes
stippled_borders 0
#border_inner_margin 16
border_width 1
double_buffer yes
#max_specials 64
imlib_cache_size 0

#-----Color settings
default_color white
default_shade_color black
default_outline_color black

#-----LUA load
lua_load one4all.lua
lua_draw_hook_post conky_main

TEXT
```


there is a settings of "londonali1010_ariclock.module":
```
--[[
###############################################################################
###                              SETTINGS                                   ###
###############################################################################
--]]
local settings_table = {
	{
		-- What radius should the clock face (not including border) be, in pixels?
		clock_r=100,
	
		-- x and y coordinates, relative to the top left corner of Conky, in pixels
		xc=300,
		yc=300,
	
		-- Extent of the shadow, in pixels
		shadow_width=5,
		
		-- x and y offsets of the drop shadow, relative to the centre of the clock face, in pixels. Can be positive (downward) or negative (upward)
		shadow_xoffset=2,
		shadow_yoffset=4,
		
		-- Do you want to show the second hand? Use this if you use a Conky update_interval > 1s. Can be true or false.
		show_seconds=true,
		
		-- Shadow colors
		shadow_color1 = 0x000000,
		shadow_alpha1 = 0.2,
		shadow_color2 = 0x000000,
		shadow_alpha2 = 0,
		
		-- Border colors
		border_color1 = 0x808080, border_alpha1 = 0.2, --rim arround a border
		border_color2 = 0xffaf00, border_alpha2 = 0.7,
		border_color3 = 0xffaf00, border_alpha3 = 0,
		border_color4 = 0xffaf00, border_alpha4 = 0,
		border_color5 = 0xffaf00, border_alpha5 = 0,
		border_color6 = 0xffaf00, border_alpha6 = 0.7,
		
		-- Face colors
		face_color1 = 0x00e0ff, face_alpha1 = 0.8,
		face_color2 = 0x00e0ff, face_alpha2 = 0.6,
		face_color3 = 0x00b0ef, face_alpha3 = 0.4,
		face_color4 = 0x808080, face_alpha4 = 0.2, --rim arround a face
		
		-- Hands color
		hands_color = 0xff0000, hands_alpha = 0.5
	},
}
--[[
###############################################################################
###                           END OF SETTINGS                               ###
###############################################################################
--]]

```


there is a settings of "londonali1010_airclock_1.module":
```
--[[
###############################################################################
###                              SETTINGS                                   ###
###############################################################################
--]]
local settings_table = {
	{
		-- What radius should the clock face (not including border) be, in pixels?
		clock_r=60,
	
		-- x and y coordinates, relative to the top left corner of Conky, in pixels
		xc=100,
		yc=100,
	
		-- Extent of the shadow, in pixels
		shadow_width=5,
		
		-- x and y offsets of the drop shadow, relative to the centre of the clock face, in pixels. Can be positive (downward) or negative (upward)
		shadow_xoffset=0,
		shadow_yoffset=2,
		
		-- Do you want to show the second hand? Use this if you use a Conky update_interval > 1s. Can be true or false.
		show_seconds=true,
		
		-- Shadow colors
		shadow_color1 = 0x000000,
		shadow_alpha1 = 0.2,
		shadow_color2 = 0x000000,
		shadow_alpha2 = 0,
		
		-- Border colors
		border_color1 = 0x808080, border_alpha1 = 0.2, --rim arround a border
		border_color2 = 0x00ffff, border_alpha2 = 0.7,
		border_color3 = 0x00ffff, border_alpha3 = 0,
		border_color4 = 0x00ffff, border_alpha4 = 0,
		border_color5 = 0x00ffff, border_alpha5 = 0,
		border_color6 = 0x00ffff, border_alpha6 = 0.7,
		
		-- Face colors
		face_color1 = 0x00ffff, face_alpha1 = 0.8,
		face_color2 = 0x00ffff, face_alpha2 = 0.6,
		face_color3 = 0x00ffff, face_alpha3 = 0.4,
		face_color4 = 0x808080, face_alpha4 = 0.2, --rim arround a face
		
		-- Hands color
		hands_color = 0x000000, hands_alpha = 0.5
	},
}
--[[
###############################################################################
###                           END OF SETTINGS                               ###
###############################################################################
--]]

```


there is a settings of "londonali1010_airclock_2.module":
```
--[[
###############################################################################
###                              SETTINGS                                   ###
###############################################################################
--]]
local settings_table = {
	{
		-- What radius should the clock face (not including border) be, in pixels?
		clock_r=60,
	
		-- x and y coordinates, relative to the top left corner of Conky, in pixels
		xc=500,
		yc=100,
	
		-- Extent of the shadow, in pixels
		shadow_width=5,
		
		-- x and y offsets of the drop shadow, relative to the centre of the clock face, in pixels. Can be positive (downward) or negative (upward)
		shadow_xoffset=0,
		shadow_yoffset=2,
		
		-- Do you want to show the second hand? Use this if you use a Conky update_interval > 1s. Can be true or false.
		show_seconds=true,
		
		-- Shadow colors
		shadow_color1 = 0x000000,
		shadow_alpha1 = 0.2,
		shadow_color2 = 0x000000,
		shadow_alpha2 = 0,
		
		-- Border colors
		border_color1 = 0x808080, border_alpha1 = 0.2, --rim arround a border
		border_color2 = 0xff00ff, border_alpha2 = 0.7,
		border_color3 = 0xff00ff, border_alpha3 = 0,
		border_color4 = 0xff00ff, border_alpha4 = 0,
		border_color5 = 0xff00ff, border_alpha5 = 0,
		border_color6 = 0xff00ff, border_alpha6 = 0.7,
		
		-- Face colors
		face_color1 = 0xff00ff, face_alpha1 = 0.8,
		face_color2 = 0xff00ff, face_alpha2 = 0.6,
		face_color3 = 0xff00ff, face_alpha3 = 0.4,
		face_color4 = 0x808080, face_alpha4 = 0.2, --rim arround a face

		-- Hands color
		hands_color = 0x000000, hands_alpha = 0.5
	},
}
--[[
###############################################################################
###                           END OF SETTINGS                               ###
###############################################################################
--]]

```


there is a settings of "londonali1010_airclock_3.module":
```
--[[
###############################################################################
###                              SETTINGS                                   ###
###############################################################################
--]]
local settings_table = {
	{
		-- What radius should the clock face (not including border) be, in pixels?
		clock_r=60,
	
		-- x and y coordinates, relative to the top left corner of Conky, in pixels
		xc=100,
		yc=500,
	
		-- Extent of the shadow, in pixels
		shadow_width=5,
		
		-- x and y offsets of the drop shadow, relative to the centre of the clock face, in pixels. Can be positive (downward) or negative (upward)
		shadow_xoffset=0,
		shadow_yoffset=2,
		
		-- Do you want to show the second hand? Use this if you use a Conky update_interval > 1s. Can be true or false.
		show_seconds=true,
		
		-- Shadow colors
		shadow_color1 = 0x000000,
		shadow_alpha1 = 0.2,
		shadow_color2 = 0x000000,
		shadow_alpha2 = 0,
		
		-- Border colors
		border_color1 = 0x808080, border_alpha1 = 0.2, --rim arround a border
		border_color2 = 0xffff00, border_alpha2 = 0.7,
		border_color3 = 0xffff00, border_alpha3 = 0,
		border_color4 = 0xffff00, border_alpha4 = 0,
		border_color5 = 0xffff00, border_alpha5 = 0,
		border_color6 = 0xffff00, border_alpha6 = 0.7,
		
		-- Face colors
		face_color1 = 0xffff00, face_alpha1 = 0.8,
		face_color2 = 0xffff00, face_alpha2 = 0.6,
		face_color3 = 0xffff00, face_alpha3 = 0.4,
		face_color4 = 0x808080, face_alpha4 = 0.2, --rim arround a face
		
		-- Hands color
		hands_color = 0x000000, hands_alpha = 0.5
	},
}
--[[
###############################################################################
###                           END OF SETTINGS                               ###
###############################################################################
--]]

```


and there is a settings of "londonali1010_airclock_4.module":
```
--[[
###############################################################################
###                              SETTINGS                                   ###
###############################################################################
--]]
local settings_table = {
	{
		-- What radius should the clock face (not including border) be, in pixels?
		clock_r=60,
	
		-- x and y coordinates, relative to the top left corner of Conky, in pixels
		xc=500,
		yc=500,
	
		-- Extent of the shadow, in pixels
		shadow_width=5,
		
		-- x and y offsets of the drop shadow, relative to the centre of the clock face, in pixels. Can be positive (downward) or negative (upward)
		shadow_xoffset=0,
		shadow_yoffset=2,
		
		-- Do you want to show the second hand? Use this if you use a Conky update_interval > 1s. Can be true or false.
		show_seconds=true,
		
		-- Shadow colors
		shadow_color1 = 0x000000,
		shadow_alpha1 = 0.2,
		shadow_color2 = 0x000000,
		shadow_alpha2 = 0,
		
		-- Border colors
		border_color1 = 0x808080, border_alpha1 = 0.2, --rim arround a border
		border_color2 = 0x000000, border_alpha2 = 0.7,
		border_color3 = 0x000000, border_alpha3 = 0,
		border_color4 = 0x000000, border_alpha4 = 0,
		border_color5 = 0x000000, border_alpha5 = 0,
		border_color6 = 0x000000, border_alpha6 = 0.7,
		
		-- Face colors
		face_color1 = 0x000000, face_alpha1 = 0.8,
		face_color2 = 0x000000, face_alpha2 = 0.6,
		face_color3 = 0x000000, face_alpha3 = 0.4,
		face_color4 = 0x808080, face_alpha4 = 0.2, --rim arround a face
		
		-- Hands color
		hands_color = 0xffffff, hands_alpha = 0.5
	},
}
--[[
###############################################################################
###                           END OF SETTINGS                               ###
###############################################################################
--]]

```



Everything included in tar.gz archive and there is image how it looks.

---

### Post by djyoung4 on 2012-04-05
yes I ran the .sh and there is a module in the active folder.

---

### Post by mrpeachy on 2012-04-05
@dk75 this is an interesting idea
do you think there will be cpu and memory usage issues by having 4 differently named complete lua scripts running making , for example 4 clocks, as opposed to a single lua script that contains 4 setup sections generating the 4 clocks?

would it be possible to maintain the central lua script so that it contains all the script code from all of the various modules...

then instead of users copying multiple instances of the whole script into the active folder, they just copy multiple instances of text files containing only the setups

the main lua, where all the code is, then reads all the setup files and runs them

---

### Post by dk75 on 2012-04-05
> **djyoung4 said:**
> yes I ran the .sh and there is a module in the active folder.

Then download one4all-0.1.2.tar.gz (if you don't have it already) and then download this debug pack and copy it to one4all main folder.
Run it from SH script that's inside and wait 5s.

I have such output in a terminal:
```
Path to one4all:	/home/kitsune/.conky/one4all/
defining active list array
number of files:	0
Module found:	londonali1010_airclock_1.module
Module name:	londonali1010_airclock_1	module extension:	1
number of files:	1
Module found:	londonali1010_airclock_2.module
Module name:	londonali1010_airclock_2	module extension:	1
number of files:	2
Module found:	londonali1010_airclock_3.module
Module name:	londonali1010_airclock_3	module extension:	1
number of files:	3
Module found:	londonali1010_airclock_4.module
Module name:	londonali1010_airclock_4	module extension:	1
number of files:	4
Module found:	londonali1010_airclock.module
Module name:	londonali1010_airclock	module extension:	1
number of files:	5
Module [1]:	londonali1010_airclock_1
Module [2]:	londonali1010_airclock_2
Module [3]:	londonali1010_airclock_3
Module [4]:	londonali1010_airclock_4
Module [5]:	londonali1010_airclock

Conky: desktop window (27a) is root window
Conky: window type - override
Conky: drawing to created window (0x4600001)
Conky: drawing to double buffer
```



> **mrpeachy said:**
> @dk75 this is an interesting idea
do you think there will be cpu and memory usage issues by having 4 differently named complete lua scripts running making , for example 4 clocks, as opposed to a single lua script that contains 4 setup sections generating the 4 clocks?

would it be possible to maintain the central lua script so that it contains all the script code from all of the various modules...

then instead of users copying multiple instances of the whole script into the active folder, they just copy multiple instances of text files containing only the setups

the main lua, where all the code is, then reads all the setup files and runs them
The module idea is that it is included to main script so it is like part of the script, yet with private variables. So it is like one big script.
If I aggregate 100 scripts and user use only 4 of them then it will be exaggeration. If it's like right now, only used/copied modules are included into a script and only it's arrays/variables are using more memory than for example one airclock script (thought right now it is like 5 ariclock scripts copied one by one into one single script).
So running 5 airclock module eat more CPU and memory than 1 airclock script drawing 1 clock but you have 5 clock as a result and scripts aren't run simultaneously but one after another, like one bigger, more eye candy script.
Of course I didn't do resource test yet.
I think 5 clock in one Conky is to little to test - when I port v9000 and a weather script then we could do test with 4 or 8 weather modules loaded at once for few hour (I need to find some test environment first thought).

---

### Post by dk75 on 2012-04-06
Now I further changed main LUA script in preparation for future development.
Now modules aren't integral part of package - it could be downloaded and installed as requested.

---

### Post by dk75 on 2012-04-06
Module packages - first batch.

---

### Post by dk75 on 2012-04-06
Module packages - second batch.

---

### Post by dk75 on 2012-04-07
Small update on one of function library file and mrpeachy_12_24_hours clock.

---

### Post by dk75 on 2012-04-18
Some minor changes to core one4all code and directory structure.

My LUA module to draw my working schedule for 3 month, but it turned out as calendar and schedule for any other amount of months.
It needs data/schedule-x.txt files where 'x' is number of file (for 3 months you need 3 files: data/schedule-1.txt, data/schedule-2.txt, data/schedule-3.txt).

If no schedule text file is available then it is not displayed over a calendar.

What's important, that it is completely locale dependent so for me week starts with Monday and when run with English locales
```
env LC_ALL="en_US.UTF-8" ~/.conky/one4all/one4all-start.sh
```
then week starts with Sunday.

---

### Post by Sector11 on 2012-04-18
> **dk75 said:**
> What's important, that it is completely locale dependent so for me week starts with Monday and when run with English locales
```
env LC_ALL="en_US.UTF-8" ~/.conky/one4all/one4all-start.sh
```
then week starts with Sunday.

NOW that's impressive.
I must make time to explore these more.  I have everything - just been occupied with other stuff. Real Life and conky related as well.

---

### Post by dk75 on 2012-04-19
Yeah. 5 hour a day to do everything in a life including meal preparation ( -2 hour a day ).

Can't do much of Conky/LUA at this point.

PS: need to modify schedule module to do less I/O operation...

---

### Post by dk75 on 2012-04-19
one4all update.

one4all-start.sh script: it will wait for Compiz but no longer than 30s

schedule.module: it will update calendar at startup and then every 300 Conky updates (number of Conky updates could be changed in settings) - before it was reading from disk every second

---

### Post by dk75 on 2012-04-19
New version of schedule.module:
- changed schedule text file naming scheme from number of months to display to actual date of schedule
- small changes in errors handling code

---

### Post by Ergatif on 2012-04-19
About Post 221 of this thread : 

[http://http://ubuntuforums.org/showpost.php?p=8944570&postcount=221]("http://http//ubuntuforums.org/showpost.php?p=8944570&postcount=221")

On my  openbox 3.4.10 the script wasn't showing any shortcut. I had to change the  2 lignes in **shortcuts.py** from : ```
strRoot="{http://openbox.org/3.4/rc}"
``` to ```
strRoot=""
``` to make it work.

However, I found the script very usefull...

Thanks to wlourf :)

> **wlourf said:**
> Hi all !

I am an Openbox + Ubuntu user  but sometimes, I can't remember some shortcuts. So I wrote a script to display the shorcuts (keyboard+mouse) from rc.xml in a conky window, and this window is called with a shortcut (!) only when I need it. Maybe this kind of script already exist but I didn't find it :P.

First I need a conkyrc template . The python script will use this file to create a conkyrc in a new file.
The only thing to do in this file is to choose yours colors.
The name of the file is **conky_template.**

The python script **shortcuts.py** read the openbox's rc.xml file.
There are some parameters to set at the beginning of the script :
```
#!/usr/bin/env python
# coding=utf-8

#this script read the file rc.xml for OpenBox configuration
#and returns the shortcuts for Mouse ou Keyboard in a file called by conky
#wlourf 07/03/2010  http://u-scripts.blogspot.com/

import sys
import xml.etree.ElementTree as etree

#full path and name of the rc.xml file
rc_path_file="/home/ll/.config/openbox/rc.xml"
#template of conkyrc to use
conkytemplate_path_file ="/home/ll/scripts/raccourcis/conky_template"

#column width (Ms = souris, Kb= clavier)
lgColMs=50
lgColKb=40

#Number of lines per Column (Ms = souris, Kb= clavier)
nbLnMs=30
nbLnKb=30

#in "Keyboard" array, "appliFirst" will display application name before shorcut
appliFirst=True

#END OF THE PARAMETERS !


```Next, a little bash script **launcher.sh** needed to run the python script and to call conky. Don't forget to make it executable.

The 3 files are in the attchment.

In your rc.xml, you have to add two shortcuts to run launcher.sh with parameters

```
    <keybind key="W-r">
      <action name="Execute">
        <name>shortcuts for desktop</name>
        <command>/home/ll/scripts/raccourcis/launcher.sh /tmp/conky_kb k</command>
      </action>
    </keybind>    
    <keybind key="W-s">
      <action name="Execute">
        <name>shortcuts for mouse</name>
        <command>/home/ll/scripts/raccourcis/launcher.sh /tmp/conky_ms m</command>
      </action>
    </keybind>    

```And the output, for the keyboard :
[[IMG]http://img294.imageshack.us/img294/5571/sckb.th.png[/IMG]]("http://img294.imageshack.us/i/sckb.png/")

and the output for the mouse :
[[IMG]http://img251.imageshack.us/img251/1161/scms.th.png[/IMG]]("http://img251.imageshack.us/i/scms.png/")

Edit : 29/04/2010, v1.1 :
Keyboard shortcuts without commands are no more displayed.
Long command lines are shortened in the dispay to fit the column width.
Edit : 02/05/2010 v1.2 thanks buttate_la _pasta  :)
In keyboard section, when a command string hold the full path to the executable,
it keeps only the name of the executable itself

---

### Post by dk75 on 2012-04-20
schedule.module changes:
- added align settings for date and schedule numbers

---

### Post by dk75 on 2012-04-26
Schedule module:
- added schedule text width check and font resize to fit into day cell box

---

### Post by dk75 on 2012-04-26
Schedule module:
- os.setlocale is called only once instead of every loop

---

