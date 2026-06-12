---
title: "Conky"
date: 2015-07-03
forum: Ubuntu Development Version
---

### Post by QDR06VV9 on 2015-07-03
Conky seems to have a new feature Windows with the ability to Move and Maximize and Minimize
He He! I almost like it. This came in on yesterdays updates, and remains with today's 7/3/2015 updates. Again just reporting.
Regards

---

### Post by QDR06VV9 on 2015-07-03
> **runrickus said:**
> Conky seems to have a new feature Windows with the ability to Move and Maximize and Minimize
He He! I almost like it. This came in on yesterdays updates, and remains with today's 7/3/2015 updates. Again just reporting.
Regards

:oops: Sometimes I just have to laugh at myself, Don't know how I did it but in the .conkyrc file it had "Create own_window"
With that commented out all is good, But the plus side of things I can now Move and Place conky faster.;)
But it is strange in trusty I do not get a windowed cony with "Create own_window"?
I will dig around some more if not I am sure a fix will come in soon enough.
Regards

---

### Post by Chanath on 2015-07-04
Tell us more about what you find out, okay?:popcorn:

---

### Post by QDR06VV9 on 2015-07-06
Ok got things sorted out! I have about 10 conky configs that I like to use but hated having to change my startup when wanting to change conky,
So I just installed conky-manager to deal with that. But it had changed my config files with different extensions, Like .sh
And also changed Text in my config's
```
own_window yes 
own_window_type panel
own_window_hints above
```
Witch will reproduce the windowed conky? Maybe a bug? I'm unsure.
But it seems to be behaving so far. But I am still unable to reproduce the same on Trusty.
If someone else can reproduce the windowed effect let me know.Please.
Regards

---

### Post by QDR06VV9 on 2015-07-06
```
# Conky settings #
background yes
update_interval 1
double_buffer yes
no_buffers yes

# Window specifications #
gap_x 40
gap_y 70
minimum_size 600 600
maximum_width 430
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below
#border_margin 0
#border_inner_margin 0
#border_outer_margin 0
alignment top_left

# Graphics settings #
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no

# Text settings #
use_xft yes
xftalpha 0
xftfont Open Sans Light:size=10

override_utf8_locale yes

imlib_cache_size 0

# Color scheme #
default_color FFFFFF

color1 FFFFFF
color2 666666
color3 AAAAAA
[COLOR=#006400]own_window yes[/COLOR]
own_window_type yes
own_window_hints below
own_window_argb_value 0
own_window_argb_visual no
own_window_colour 000000
TEXT
${execi 300 curl -s "http://weather.yahooapis.com/forecastrss?w=2487610&u=F" -o ~/.cache/weather.xml}${image ~/.conky-weather/assets/right-bar-blue.png -p 283,20 -s 148x560}${image ~/.conky-weather/assets/shadow-2.png -p 1,17 -s 433x566}${image ~/.conky-weather/assets/shadow.png -p 303,20 -s 54x560}${image ~/.conky-weather/assets/fav-color-orange.png -p 4,20 -s 299x560}
${color1}${font Droid Sans :size=12}${alignr 10}${voffset 17}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "low=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==1'}°${alignr 10}/${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "high=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==1'}°
${color1}${font Droid Sans :size=12}${voffset 10}${alignr 10}Today
${color1}${font Droid Sans :size=12}${alignr 10}${voffset 72}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "low=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==2'}°${alignr 10}/${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "high=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==2'}°
${color1}${font Droid Sans :size=12}${voffset 10}${alignr 10}Tomorrow
${color1}${font Droid Sans :size=12}${voffset 72}${alignr 10}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "low=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==3'}°${alignr 10}/${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "high=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==3'}°
${color1}${font Droid Sans :size=12}${alignr 10}${voffset 10}${execi 3600 LANG=en_US date -d +2day +%A}
${color1}${font Droid Sans :size=12}${alignr 10}${voffset 72}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "low=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==4'}°${alignr 10}/${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "high=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==4'}°
${color1}${font Droid Sans :size=12}${voffset 10}${alignr 10}${execi 3600 LANG=en_US date -d +3day +%A}
${color1}${font Droid Sans :size=12}${alignr 10}${voffset 72}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "low=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==5'}°${alignr 10}/${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "high=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==5'}°
${color1}${font Droid Sans :size=12}${voffset 10}${alignr 10}${execi 3600 LANG=en_US date -d +4day +%A}${font Droid Sans :size=12}
${color1}${goto 20}${voffset -136}Humidity:  ${color4}${execi 300 grep "yweather:atmosphere" ~/.cache/weather.xml | grep -o "humidity=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}%
${color1}${goto 20}${voffset 20}Wind:  ${color4}${execi 300 grep "yweather:wind" ~/.cache/weather.xml | grep -o "speed=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}${execi 300 grep "yweather:units" ~/.cache/weather.xml | grep -o "speed=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}
${color1}${goto 20}${voffset 20}Pressure:  ${color4}${execi 300 grep "yweather:atmosphere" ~/.cache/weather.xml | grep -o "pressure=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}${execi 300 grep "yweather:units" ~/.cache/weather.xml | grep -o "pressure=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}
${color1}${goto 20}${voffset 20}Visibility:  ${color4}${execi 300 grep "yweather:atmosphere" ~/.cache/weather.xml | grep -o "visibility=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}${execi 300 grep "yweather:units" ~/.cache/weather.xml | grep -o "distance=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}
${color1}${font Raleway:weight=Light :size=120}${alignr 131}${voffset -360}${execi 300 grep "yweather:condition" ~/.cache/weather.xml | grep -o "temp=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}°
${font Droid Sans :size=16}${alignr 140}${voffset -429}${execi 300 grep "yweather:condition" ~/.cache/weather.xml | grep -o "text=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}
${execi 300 cp -f ~/.conky-weather/weather-icons-big/$(grep "yweather:condition" ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*").png ~/.cache/weather.png}${image ~/.cache/weather.png -p 36,56 -s 128x128}${execi 300 cp -f ~/.conky-weather/weather-icons/$(grep "yweather:forecast" ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==1').png ~/.cache/weather-1.png}${image ~/.cache/weather-1.png -p 316,30 -s 32x32}${execi 300 cp -f ~/.conky-weather/weather-icons/$(grep "yweather:forecast" ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==2').png ~/.cache/weather-2.png}${image ~/.cache/weather-2.png -p 316,150 -s 32x32}${execi 300 cp -f ~/.conky-weather/weather-icons/$(grep "yweather:forecast" ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==3').png ~/.cache/weather-3.png}${image ~/.cache/weather-3.png -p 316,270 -s 32x32}${execi 300 cp -f ~/.conky-weather/weather-icons/$(grep "yweather:forecast" ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==4').png ~/.cache/weather-4.png}${image ~/.cache/weather-4.png -p 316,390 -s 32x32}${voffset 20}
${execi 300 cp -f ~/.conky-weather/weather-icons/$(grep "yweather:forecast" ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==5').png ~/.cache/weather-5.png}${image ~/.cache/weather-5.png -p 316,510 -s 32x32}${voffset 20}${font}
```

The Code Highlighted in Green as shown above produces the window in conky, and by simply remmoving the "yes" removes the window.
One can waste a lot of time on Conky!:rolleyes:
I can picture a new sub-forum  "conky-anonymous" Hi my name is runrickus and I have been conky free for 30 days!):P
Smile. Kind Regards

---

### Post by ventrical on 2015-07-07
I'm going to try this.:)  I got three days off  (2 already gone)... not much else to do ..and I have a special machine already set up .. so I'll be back :)

regards..

---

### Post by ventrical on 2015-07-07
> **runrickus said:**
> [CODE]# Conky settings #

One can waste a lot of time on Conky!:rolleyes:
I can picture a new sub-forum  "conky-anonymous" Hi my name is runrickus and I have been conky free for 30 days!):P
Smile. Kind Regards

Doh... I didn't see that part :)  Started already ... might as well finish .. :)

---

### Post by ventrical on 2015-07-07
@runrickus

Can you give me a few simple steps to get conky going.. I installed 'conky' from software center and 

```

ventrical@ventrical-RK574AA-ABA-a1730n:~$ conky
Conky: desktop window (16001ad) is subwindow of root window (28d)
Conky: window type - desktop
Conky: drawing to created window (0x3600001)
Conky: drawing to single buffer


```

and it did nothing .. 

I am not conky pro or anything..:)

Regards..

---

### Post by QDR06VV9 on 2015-07-07
> **ventrical said:**
> @runrickus

Can you give me a few simple steps to get conky going.. I installed 'conky' from software center and 

```

ventrical@ventrical-RK574AA-ABA-a1730n:~$ conky
Conky: desktop window (16001ad) is subwindow of root window (28d)
Conky: window type - desktop
Conky: drawing to created window (0x3600001)
Conky: drawing to single buffer


```

and it did nothing .. 

I am not conky pro or anything..:)

Regards..
ventrical I would'nt waste your time I really am convinced now that those anomalies are coming from conky-manager.  But thank you for using your time to confirm or un-confirm the problem!
I have been reading up on conky-manager a bit now. and I suspect that it is a possibility that his API's need updating at least for wily, But performs well on trusty.
Now I am not sure this thread is even relevant to this section of the forums?
But if you are sincere in learning more on conky I am willing to help.:D But No Way am I a guru on the matter.(Like our absent member VinDSL)
Kind Regards

---

### Post by ventrical on 2015-07-07
> **runrickus said:**
> 
I have been reading up on conky-manager a bit now. and I suspect that it is a possibility that his API's need updating at least for wily, But performs well on trusty.
Kind Regards

Thanks .. this answers my question for the moment..

Regards..

---

### Post by Chanath on 2015-07-07
What about the ~/.conky-weather folder etc?

---

### Post by Cavsfan on 2015-07-08
I don't recommend using conky version 1.10 myself. 

It probably has it's pluses but it doesn't contain the $pre_exec command and probably others that VinDSL's conky uses to pull some information.

I had to get the deb file from here [http://pkgs.org/download/conky-all](http://pkgs.org/download/conky-all) and use Ubuntu Sofware Center to install it. But if you just lock it in SPM, it will still upgrade the next time you do an upgrade.

You have to do this to get it to actually lock the version:

```
sudo apt-mark hold conky-all
```

I have this on both my Wily installs, my Mint 17.2 Rafaela install as well as my new Arch Linux install.

This is on Arch Linux: (4 conkys BTW)

[[IMG]http://en.zimagez.com/miniature/screenshot2015-07-0817-38-30.png[/IMG]]("http://en.zimagez.com/zimage/screenshot2015-07-0817-38-30.php")

But the cool thing about all of this is it's entirely up to you which version you use. I just thought I'd add my 2 shillings. :p

---

### Post by QDR06VV9 on 2015-07-09
> **Cavsfan said:**
> I don't recommend using conky version 1.10 myself. 

It probably has it's pluses but it doesn't contain the $pre_exec command and probably others that VinDSL's conky uses to pull some information.

I had to get the deb file from here [http://pkgs.org/download/conky-all](http://pkgs.org/download/conky-all) and use Ubuntu Sofware Center to install it. But if you just lock it in SPM, it will still upgrade the next time you do an upgrade.

You have to do this to get it to actually lock the version:

```
sudo apt-mark hold conky-all
```

I have this on both my Wily installs, my Mint 17.2 Rafaela install as well as my new Arch Linux install.

This is on Arch Linux: (4 conkys BTW)

[[IMG]http://en.zimagez.com/miniature/screenshot2015-07-0817-38-30.png[/IMG]]("http://en.zimagez.com/zimage/screenshot2015-07-0817-38-30.php")

But the cool thing about all of this is it's entirely up to you which version you use. I just thought I'd add my 2 shillings. :p

Good Job cavsfan!:D Thanks for your 2 shillings worth that sorted out my problems, No More windows around conky.
I would not have noticed that conky got a new version untill you made mention of it.=d>

I owe you a Beer or an Iced Tea!
Regards

---

### Post by Cavsfan on 2015-07-09
> **runrickus said:**
> Good Job cavsfan!:D Thanks for your 2 shillings worth that sorted out my problems, No More windows around conky.
I would not have noticed that conky got a new version untill you made mention of it.=d>

I owe you a Beer or an Iced Tea!
Regards

Always glad to help! :) My VinDSL conky displays the conky version. That is how I found out.

I'm using **own_window_type override** on Arch which I couldn't do with Ubuntu. I have to use **own_window_type normal** and **own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager** there. 

Also in Arch you have to set the window hints up in CCSM Window Rules like this:

[ATTACH=CONFIG]263108[/ATTACH] 

I need to go see how my 2 Wily installs are doing. I see we're into the alpha1 stage on Wily. I have the exact same conkys on all 4 systems.

Cheers

---

### Post by QDR06VV9 on 2015-07-09
> **Cavsfan said:**
> Always glad to help! :) _My VinDSL conky displays the conky version_. That is how I found out. 

Cheers
I have been chasing my tail for 2 Days Now When a simple line of code would of helped.
```
apt-cache policy conky-all
```
Some tester I am](*,) Sheesh! The Older I get the better I was.
Regards

---

### Post by Cavsfan on 2015-07-09
> **runrickus said:**
> I have been chasing my tail for 2 Days Now When a simple line of code would of helped.
```
apt-cache policy conky-all
```
Some tester I am](*,) Sheesh! The Older I get the better I was.
Regards

LoL! Thanks for my daily funny LoLoL! :D You should try installing Arch if you want to test yourself!

You start out with a text based system and slowly build it from looking at an app called Arch Wiki on your cell phone. :P :lol:

Noticed the 4.0 kernel finally hit Wily and nary a glitch. :p

```
cavsfan@cavsfan-MS-7529:~$ uname -a
Linux cavsfan-MS-7529 4.0.0-4-generic #6-Ubuntu SMP Tue Jun 30 20:49:28 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```

Pretty smooth and then I looked at my Galaxy S6 phone and it has the 5.0.2 kernel lol!

---

