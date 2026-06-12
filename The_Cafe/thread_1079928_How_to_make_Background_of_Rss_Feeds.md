---
title: "How to make Background of Rss Feeds"
date: 2009-02-24
forum: The Cafe
---

### Post by jamesey on 2009-02-24
I tried searching for the answer to this but just got a lot of links with backgrounds and wallpapers. I'm curious how I can make my desktop background black with rss feeds in white text (colors dont really matter, that's just an example.)

is there an app or plugin or trick to doing this?

---

### Post by Grant A. on 2009-02-24
At the moment, I do not think so. You could, however, download a program to display a little bar on your desktop to show rss feeds, or an add-on to make a drop-down menu of them on your panel.

---

### Post by smartboyathome on 2009-02-24
Actually, you can. Use Conky, look up some configs with it. I have a few RSS feeds on my desktop.

---

### Post by etnlIcarus on 2009-02-25
Conky is your best option: light weight, few dependencies. The only drawbacks are it isn't interactive/doesn't support click-events (ie you can't click on a feed to load it in your web browser) and getting your head around the config files takes a bit of getting used to.

I've been using the following setup for a while:
[[IMG]http://img152.imageshack.us/img152/5617/rss.th.jpg[/IMG]](http://img152.imageshack.us/img152/5617/rss.jpg)

```
own_window_title conkyrss

max_user_text 20000

use_xft yes
xftfont Lucida Grande:size=6.3
override_utf8_locale yes
xftalpha 1

update_interval 1
draw_shades no
default_shade_color ffffff
draw_outline no
default_outline_color 252525
draw_borders no
stippled_borders no
border_margin 0
border_width 1

no_buffers yes
uppercase no
double_buffer yes
use_spacer none

default_color ffffff
color0 ffffff
color1 afafaf #bfbfbf #cfcfcf
color2 bfbfbf
color3 111111 #1a1a1a #720000
color4 0a0a0a #101010

own_window yes
own_window_colour 0a0a0a
own_window_transparent no
own_window_type dock
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below
background yes
alignment bottom_left
gap_x -3
gap_y 20 #14
minimum_size 1440 0

TEXT
${voffset -2}${color3}${hr 1}
${voffset -2}${font LucidaMacBold:size=7}${color}${goto 20}SBS News | World${goto 105}${color ff7e00}${voffset 1}${fs_bar 6,15 /fakelol/}${color}${goto 106}${voffset -2}rss${voffset 1}${goto 220}SBS News | Aust${goto 300}${color ff7e00}${voffset 1}${fs_bar 6,15 /fakelol/}${color}${goto 301}${voffset -2}rss${voffset 1}${goto 420}ABC News | World${goto 509}${color ff7e00}${voffset 1}${fs_bar 6,15 /fakelol/}${color}${goto 510}${voffset -2}rss${voffset 1}${goto 620}ABC News | Aust${goto 704}${color ff7e00}${voffset 1}${fs_bar 6,15 /fakelol/}${color}${goto 705}${voffset -2}rss${voffset 1}${goto 820}BBC News | World${goto 908}${color ff7e00}${voffset 1}${fs_bar 6,15 /fakelol/}${color}${goto 909}${voffset -2}rss${voffset 1}${goto 1020}News Ltd Garbage | SA${goto 1129}${color ff7e00}${voffset 1}${fs_bar 6,15 /fakelol/}${color}${goto 1130}${voffset -2}rss${voffset 1}${goto 1220}Slashdot | Geek${goto 1297}${color ff7e00}${voffset 1}${fs_bar 6,15 /fakelol/}${color}${goto 1298}${voffset -2}rss${voffset 1}
${voffset -4}${font}${goto 20}${color1}${rss http://www.sbs.com.au/news/rss/Section/Top%20Stories 10 item_title 0}${goto 210}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 220}${rss http://www.sbs.com.au/news/rss/Section/National 10 item_title 0}${goto 410}${color4}$${fs_bar 10,100 /fakelol/}${color1}${goto 420}${rss http://www.abc.net.au/news/indexes/world/rss.xml 10 item_title 0}${goto 610}${color4}{fs_bar 10,100 /fakelol/}${color1}${goto 620}${rss http://www.abc.net.au/news/indexes/idx-australia/rss.xml 10 item_title 0}${goto 810}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 820}${rss http://newsrss.bbc.co.uk/rss/newsonline_world_edition/front_page/rss.xml 10 item_title 0}${goto 1010}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 1020}${rss http://feeds.news.com.au/public/rss/2.0/anow_state_191.xml 10 item_title 0}${goto 1210}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 1220}${rss http://rss.slashdot.org/Slashdot/slashdot 10 item_title 0}${goto 1420}${color4}${fs_bar 10,100 /fakelol/}${color1}
${goto 20}${rss http://www.sbs.com.au/news/rss/Section/Top%20Stories 10 item_title 1}${goto 210}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 220}${rss http://www.sbs.com.au/news/rss/Section/National 10 item_title 1}${goto 410}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 420}${rss http://www.abc.net.au/news/indexes/world/rss.xml 10 item_title 1}${goto 610}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 620}${rss http://www.abc.net.au/news/indexes/idx-australia/rss.xml 10 item_title 1}${goto 810}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 820}${rss http://newsrss.bbc.co.uk/rss/newsonline_world_edition/front_page/rss.xml 10 item_title 1}${goto 1010}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 1020}${rss http://feeds.news.com.au/public/rss/2.0/anow_state_191.xml 10 item_title 1}${goto 1210}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 1220}${rss http://rss.slashdot.org/Slashdot/slashdot 10 item_title 1}${goto 1420}${color4}${fs_bar 10,100 /fakelol/}${color1}
${goto 20}${rss http://www.sbs.com.au/news/rss/Section/Top%20Stories 10 item_title 2}${goto 210}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 220}${rss http://www.sbs.com.au/news/rss/Section/National 10 item_title 2}${goto 410}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 420}${rss http://www.abc.net.au/news/indexes/world/rss.xml 10 item_title 2}${goto 610}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 620}${rss http://www.abc.net.au/news/indexes/idx-australia/rss.xml 10 item_title 2}${goto 810}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 820}${rss http://newsrss.bbc.co.uk/rss/newsonline_world_edition/front_page/rss.xml 10 item_title 2}${goto 1010}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 1020}${rss http://feeds.news.com.au/public/rss/2.0/anow_state_191.xml 10 item_title 2}${goto 1210}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 1220}${rss http://rss.slashdot.org/Slashdot/slashdot 10 item_title 2}${goto 1420}${color4}${fs_bar 10,100 /fakelol/}${color1}
${goto 20}${rss http://www.sbs.com.au/news/rss/Section/Top%20Stories 10 item_title 3}${goto 210}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 220}${rss http://www.sbs.com.au/news/rss/Section/National 10 item_title 3}${goto 410}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 420}${rss http://www.abc.net.au/news/indexes/world/rss.xml 10 item_title 3}${goto 610}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 620}${rss http://www.abc.net.au/news/indexes/idx-australia/rss.xml 10 item_title 3}${goto 810}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 820}${rss http://newsrss.bbc.co.uk/rss/newsonline_world_edition/front_page/rss.xml 10 item_title 3}${goto 1010}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 1020}${rss http://feeds.news.com.au/public/rss/2.0/anow_state_191.xml 10 item_title 3}${goto 1210}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 1220}${rss http://rss.slashdot.org/Slashdot/slashdot 10 item_title 3}${goto 1420}${color4}${fs_bar 10,100 /fakelol/}${color1}
${goto 20}${rss http://www.sbs.com.au/news/rss/Section/Top%20Stories 10 item_title 4}${goto 210}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 220}${rss http://www.sbs.com.au/news/rss/Section/National 10 item_title 4}${goto 410}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 420}${rss http://www.abc.net.au/news/indexes/world/rss.xml 10 item_title 4}${goto 610}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 620}${rss http://www.abc.net.au/news/indexes/idx-australia/rss.xml 10 item_title 4}${goto 810}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 820}${rss http://newsrss.bbc.co.uk/rss/newsonline_world_edition/front_page/rss.xml 10 item_title 4}${goto 1010}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 1020}${rss http://feeds.news.com.au/public/rss/2.0/anow_state_191.xml 10 item_title 4}${goto 1210}${color4}${fs_bar 10,100 /fakelol/}${color1}${goto 1220}${rss http://rss.slashdot.org/Slashdot/slashdot 10 item_title 4}${goto 1420}${color4}${fs_bar 10,100 /fakelol/}${color1}${voffset 4}${goto 0}${color3}______________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________ 
${goto 1000}__________________________________________________________________________________________________________________________________
```

If you link me to the specific feeds you want and tell me how many headlines from each feed (I use the top 5 headlines for each feed) and how you want them them laid out (eg vertical, horizontal), I could whip up a custom conky RSS config in a jiffy.

Edit: I can also use whatever font faces, sizes, etc you want as well.

Edit edit: would also be really helpful if you told me what your screen resolution is.

---

### Post by Crinos512 on 2009-02-25
+1 for conky

---

### Post by jamesey on 2009-02-25
I definitely want it to be clickable. I know conky wont do that, but I'll give it a try.
My vision was a stream of data traveling from the bottom to the top of the screen, updating every couple minutes with whatever RSS headlines I had selected.

---

### Post by jamesey on 2009-02-27
[http://lifehacker.com/299410/use-a-screensaver-as-desktop-wallpaper](http://lifehacker.com/299410/use-a-screensaver-as-desktop-wallpaper)

I found this article on how to make a screen saver your desktop background. That leads me to my next question. Is there a Linux screensaver that displays rss feeds?

---

### Post by Amstell on 2009-03-06
I have been having a lot of problems trying to get conky to display some buoy and weather reports for me on my desktop.  Would anyone be able to help me out?  I have copied the conky file that enthl posted but I don't know how to integrate what I need into it.  Any help would be great.  Thanks

RSS URLS:

[http://rss.wunderground.com/auto/rss_full/CA/San_Diego.xml?units=english](http://rss.wunderground.com/auto/rss_full/CA/San_Diego.xml?units=english)
[http://www.ndbc.noaa.gov/data/latest_obs/46231.rss](http://www.ndbc.noaa.gov/data/latest_obs/46231.rss)

For some reason whenever I tried doing this it won't display any of the descriptions.  All I get is the title.

Here is what I put into my conkyrc:

${rss [http://rss.wunderground.com/auto/rss_full/CA/San_Diego.xml?units=english](http://rss.wunderground.com/auto/rss_full/CA/San_Diego.xml?units=english) 60 feed_title 50 item_title 50 item_titles item_desc 50}

${rss [http://www.ndbc.noaa.gov/data/latest_obs/46231.rss](http://www.ndbc.noaa.gov/data/latest_obs/46231.rss) 60 feed_title 50 item_title 50 item_titles item_desc 50}


Thanks for any help.  

Amstell

---

### Post by diskotek on 2009-03-06
conky is cool! i'm sure you'll ask for weather forecast next :)

---

### Post by etnlIcarus on 2009-03-06
> **Amstell said:**
> I have been having a lot of problems trying to get conky to display some buoy and weather reports for me on my desktop.  Would anyone be able to help me out?  I have copied the conky file that enthl posted but I don't know how to integrate what I need into it.  Any help would be great.  Thanks

RSS URLS:

[http://rss.wunderground.com/auto/rss_full/CA/San_Diego.xml?units=english](http://rss.wunderground.com/auto/rss_full/CA/San_Diego.xml?units=english)
[http://www.ndbc.noaa.gov/data/latest_obs/46231.rss](http://www.ndbc.noaa.gov/data/latest_obs/46231.rss)

For some reason whenever I tried doing this it won't display any of the descriptions.  All I get is the title.

Here is what I put into my conkyrc:

${rss [http://rss.wunderground.com/auto/rss_full/CA/San_Diego.xml?units=english](http://rss.wunderground.com/auto/rss_full/CA/San_Diego.xml?units=english) 60 feed_title 50 item_title 50 item_titles item_desc 50}

${rss [http://www.ndbc.noaa.gov/data/latest_obs/46231.rss](http://www.ndbc.noaa.gov/data/latest_obs/46231.rss) 60 feed_title 50 item_title 50 item_titles item_desc 50}


Thanks for any help.  

Amstell

From conky documentation:
> Action may be **one of the following**: feed_title, item_title (with num par), item_desc (with num par) and item_titles
You need to do the title/items separately.

---

### Post by Amstell on 2009-03-07
I have tried to do it separately and it won't work either.  Any other suggestions?

Here is what I have tried:
${rss [http://rss.wunderground.com/auto/rss...?units=english](http://rss.wunderground.com/auto/rss...?units=english) 60 feed_title 50 }

${rss [http://rss.wunderground.com/auto/rss...?units=english](http://rss.wunderground.com/auto/rss...?units=english) 60 item_title 50 }

${rss [http://rss.wunderground.com/auto/rss...?units=english](http://rss.wunderground.com/auto/rss...?units=english) 60 item_desc 50 }

---

### Post by etnlIcarus on 2009-03-07
> **Amstell said:**
> I have tried to do it separately and it won't work either.  Any other suggestions?

Here is what I have tried:
${rss [http://rss.wunderground.com/auto/rss...?units=english](http://rss.wunderground.com/auto/rss...?units=english) 60 feed_title 50 }

${rss [http://rss.wunderground.com/auto/rss...?units=english](http://rss.wunderground.com/auto/rss...?units=english) 60 item_title 50 }

${rss [http://rss.wunderground.com/auto/rss...?units=english](http://rss.wunderground.com/auto/rss...?units=english) 60 item_desc 50 }

Can you put your conky code in [ code ][ /code ] brackets? The URL I'm getting isn't for an RSS feed.

Also, it should be:
```
${rss URL 60 feed_title}
${rss URL 60 item_title X}
${rss URL 60 item_desc X}

```
[X = value 0-4 for item 1-5 eg item_title 0 for first headline, item_title 1 for second, etc]

---

### Post by Amstell on 2009-03-07
Here is my conky file.  I made the adjustments you mentioned and it works a little better but its still coming up with <strong> March6 </strong>

Is there a way to get rid of that so it just prints out the actual description.  Also, how would I adjust it so it looks like your conky.  I like the black background across the screen.  Thanks for your help.

```
use_xft yes
xftfont verdana:size=8
alignment top_right
xftalpha 0.8
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
default_color BADCDD
use_spacer none
no_buffers yes
uppercase no
color1 F8DF58


TEXT


${rss http://www.ndbc.noaa.gov/data/latest_obs/46231.rss 60 feed_title}

${rss http://www.ndbc.noaa.gov/data/latest_obs/46231.rss 60 item_title 0}

${rss http://www.ndbc.noaa.gov/data/latest_obs/46231.rss 60 item_desc 0}

```

---

### Post by etnlIcarus on 2009-03-07
> **Amstell said:**
> Here is my conky file.  I made the adjustments you mentioned and it works a little better but its still coming up with <strong> March6 </strong>

Is there a way to get rid of that so it just prints out the actual description.  Also, how would I adjust it so it looks like your conky.  I like the black background across the screen.  Thanks for your help.

```
use_xft yes
xftfont verdana:size=8
alignment top_right
xftalpha 0.8
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
default_color BADCDD
use_spacer none
no_buffers yes
uppercase no
color1 F8DF58


TEXT


${rss http://www.ndbc.noaa.gov/data/latest_obs/46231.rss 60 feed_title}

${rss http://www.ndbc.noaa.gov/data/latest_obs/46231.rss 60 item_title 0}

${rss http://www.ndbc.noaa.gov/data/latest_obs/46231.rss 60 item_desc 0}

```

You don't appear to be doing anything wrong. The formatting of the feed body seems to be too much for conky's primitive RSS support. 

You might be able to get around this with one of the manual RSS scripts floating around but I had a lot of trouble with them and you'd have more luck asking in the [conkyrc thread](http://ubuntuforums.org/showthread.php?t=281865).

---

### Post by Amstell on 2009-03-07
Thanks for your help.  I have posted something over on the conkrc thread to see if anyone will help me out.  I wonder why gnome doesn't have an easier rss agregator for the desktop.  The widgets and screenlets don't seem to ever work and conky is the next best option(although not a bad option consider its power)

Anyways.  Thanks again

Cheers

Amstell

---

