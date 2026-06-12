---
title: "Ubuntu 9.10 - Show what your news desktop looks like!"
date: 2009-10-09
forum: The Cafe
---

### Post by evilaim on 2009-10-09
Ya, I've installed 9.10 Beta, it's fully operational, had a few kinks to work out but nothing I couldn't handle.  I finally set it up how I like it and this is what she looks like:

---

### Post by BrokenKingpin on 2009-10-09
I have the same wallpaper on my work computer.

What theme is that?

---

### Post by wojox on 2009-10-09
Looks sweet.

---

### Post by evilaim on 2009-10-09
Well, luckily, it's a stock theme that comes with ubuntu.  It's called 'Dust'.  Just look in your "Appearance".  Also, I'm using a ballin' icon set. Here's the link: [http://www.deviantart.com/download/73276755/black_white_2_Style_by_DBGtheKafu.tar](http://www.deviantart.com/download/73276755/black_white_2_Style_by_DBGtheKafu.tar)

And, for the menu I've used Gnome-Do.  Took a bit of tweaking but I think it looks good.

---

### Post by darco on 2009-10-09
Heres my stock desktop....I dont like those large conky screens tho...mine is nice!

darco

---

### Post by clonne4crw on 2009-10-09
> **darco said:**
> Heres my stock desktop....I dont like those large conky screens tho...mine is nice!

darco

IMO, green kind of ruins the whole thing. I think black or white toolbar would look better there. :popcorn:

---

### Post by NoaHall on 2009-10-09
Yes, that green is disgusting in my eyes.

---

### Post by Boom!!! on 2009-10-09
I feel a merge coming on :lolflag:

---

### Post by darco on 2009-10-09
Ya I know...I changed my wallpaper but didnt change the panel color...


darco

---

### Post by evilaim on 2009-10-09
I wish they'd stop merging me freakin' topics. hahaha, this if for 9.10 only!

---

### Post by PhoHammer on 2009-10-09
I'm loving 9.10!!

---

### Post by evilaim on 2009-10-09
That's a very nice lookin' desktop bro.  Simplicity is the key IMO.

---

### Post by Tipped OuT on 2009-10-09
> **Boom!!! said:**
> I feel a merge coming on :lolflag:

In 3.. 2... 1...

---

### Post by darkmatter247 on 2009-10-09
heres mine  file:///home/judson/Desktop/Screenshot.png

---

### Post by darkmatter247 on 2009-10-09
nvm lol

---

### Post by evilaim on 2009-10-09
Failz!

---

### Post by PhoHammer on 2009-10-11
> **evilaim said:**
> Failz!

If only I had a "judson" directory...;)

---

### Post by Eisenwinter on 2009-10-11
Users of this bottom bunch of big 3D icons: do you not find this a waste of space on the screen?

How exactly does this work?

Show me a screenshot of you running a maximized application please, thanks.

---

### Post by slakkie on 2009-10-11
> **PhoHammer said:**
> I'm loving 9.10!!

The disk/CPU thing is done with Conky right? Could you post your conkyrc and lua scripts? I wanna see how you did it... 

Anyhows, my karmic screenshots:
[http://opperschaap.net/~wesleys/ubuntu/karmic/](http://opperschaap.net/~wesleys/ubuntu/karmic/)

---

### Post by rifak on 2009-10-11
just threw away 8.04 and replaced it with 9.10 last night. such a good release.

---

### Post by cguy on 2009-10-11
> **PhoHammer said:**
> I'm loving 9.10!!

How did you make that awesome panel at the bottom? :D

---

### Post by PhoHammer on 2009-10-11
> **slakkie said:**
> The disk/CPU thing is done with Conky right? Could you post your conkyrc and lua scripts? I wanna see how you did it... 

Anyhows, my karmic screenshots:
[http://opperschaap.net/~wesleys/ubuntu/karmic/]("http://opperschaap.net/%7Ewesleys/ubuntu/karmic/")

**My lua script goes**:
```
--[[
Ring Meters by londonali1010 (2009)

This script draws percentage meters as rings. It is fully customisable; all options are described in the script.

IMPORTANT: if you are using the 'cpu' function, it will cause a segmentation fault if it tries to draw a ring straight away. The if statement on line 145 uses a delay to make sure that this doesn't happen. It calculates the length of the delay by the number of updates since Conky started. Generally, a value of 5s is long enough, so if you update Conky every 1s, use update_num>5 in that if statement (the default). If you only update Conky every 2s, you should change it to update_num>3; conversely if you update Conky every 0.5s, you should use update_num>10. ALSO, if you change your Conky, is it best to use "killall conky; conky" to update it, otherwise the update_num will not be reset and you will get an error.

To call this script in Conky, use the following (assuming that you save this script to ~/scripts/rings.lua):
    lua_load ~/scripts/rings.lua
    lua_draw_hook_pre ring_stats
    
Changelog:
+ v1.1 -- Added options for the starting angle of the rings, and added the "max" variable, to allow for variables that output a numerical value rather than a percentage (29.09.2009)
+ v1.0 -- Original release (28.09.2009)
]]

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
        fg_colour=0xffffff,
        -- "fg_alpha" is the alpha value of the indicator part of the ring.
        fg_alpha=0.5,
        -- "x" and "y" are the x and y coordinates of the centre of the ring, relative to the top left corner of the Conky window.
        x=940, y=100,
        -- "radius" is the radius of the ring.
        radius=50,
        -- "thickness" is the thickness of the ring, centred around the radius.
        thickness=5,
        -- "angle" is the starting angle of the ring, in degrees, clockwise from top. Value can be either positive or negative.
        angle=270
    },
    {
        name='memperc',
        arg='',
        max=100,
        bg_colour=0xffffff,
        bg_alpha=0.1,
        fg_colour=0xffffff,
        fg_alpha=0.5,
        x=940, y=240,
        radius=50,
        thickness=5,
        angle=270
    },
    {
        name='fs_used_perc',
        arg='/',
        max=100,
        bg_colour=0xffffff,
        bg_alpha=0.1,
        fg_colour=0xffffff,
        fg_alpha=0.5,
        x=940, y=380,
        radius=50,
        thickness=5,
        angle=270
    },
    {       name='fs_used_perc',
                arg='/home',
                max=100,
                bg_colour=0xffffff,
                bg_alpha=0.1,
                fg_colour=0xffffff,
                fg_alpha=0.5,
                x=940, y=520,
                radius=50,
                thickness=5,
                angle=270
        },
    {
        name='battery_percent',
        arg='BAT1',
        max=100,
        bg_colour=0xffffff,
        bg_alpha=0.1,
        fg_colour=0xffffff,
        fg_alpha=0.5,
        x=940, y=660,
        radius=50,
        thickness=5,
        angle=270
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
```**My conky.conf**:
```
    # -- Conky settings -- #
    background no
    update_interval 2

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

    minimum_size 1020 800
    maximum_width 1000
    
    # -- Alignment -- #
    alignment tr
    gap_x 10
    gap_y 0

    # -- Graphics settings -- #
    draw_shades no
    draw_outline no
    draw_borders no
    draw_graph_borders no

    # -- Text settings -- #
    use_xft yes
    xftfont Santana:size=8
    xftalpha 0.8

    uppercase no

    default_color FFFFFF

    # -- Lua Load -- #
    lua_load /etc/conky/lua/rings.lua
    lua_draw_hook_pre ring_stats

    TEXT







    ${offset 916}CPU
    ${offset 916}${acpitemp} C
    ${offset 916}$cpu%









    ${offset 916}RAM
    ${offset 916}$memperc%








    ${offset 924}/
    ${offset 883}${fs_used /}/${fs_size /}









    ${offset 910}/home
    ${offset 883}${fs_used /home}/${fs_size /home}









    ${offset 908}Battery
    ${offset 918}${battery_percent BAT1}%



```99.9% of credit goes to [londonali1010]("http://ubuntuforums.org/member.php?u=779759")
Her work at Conky Hardcore! is how I did this, I just edited it to my tastes :)

> How did you make that awesome panel at the bottom? :grin:It's tint2: ```
sudo apt-get install tint2
```I got the idea from #! Crunchbang Linux, which uses tint2 as the default panel.
I want to have a system tray in it, but have yet to figure it out. If anyone has any
tips, shoot me a config file or something!

---

### Post by evilaim on 2009-10-11
Well, I took a chance, and I love it.  

The Window List on the bottom is an app called "Tint2".

sudo apt-get install tint2

Configs are in ~/.config/tint/tintrc

Easily edited and it's very very light weight.  I'd suggest just making it a tid bit bigger, which you can do in the config. I'm totally happy with it.

Here's the screens!

---

### Post by cdwillis on 2009-10-12
> **Eisenwinter said:**
> Users of this bottom bunch of big 3D icons: do you not find this a waste of space on the screen?

How exactly does this work?

Show me a screenshot of you running a maximized application please, thanks.

Are you talking about the dock? You can set your applications to cover it or you can have it hide automatically.

---

### Post by Kristofer Gustafsson on 2009-11-09
[http://nephnic.com/pictures/Screenshot.png](http://nephnic.com/pictures/Screenshot.png)

---

### Post by Captain_Glen on 2009-11-19
Check out my awesome aquarium desktop!

Not quite as cool as what you can do on a Mac but hey it'll get there.

---

