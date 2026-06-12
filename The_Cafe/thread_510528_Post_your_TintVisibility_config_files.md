---
title: "Post your Tint/Visibility config files"
date: 2007-07-26
forum: The Cafe
---

### Post by dbbolton on 2007-07-26
I really like [Tint Task Manager]("http://code.google.com/p/ttm/") and [Visibility]("http://projects.l3ib.org/trac/visibility"). However, it's sometimes a hassle to change their themes. 

After talking to BOBSONATOR, I thought it would be nice to start a thread similar to "Post your .conkrc files w/screenshots" in order to share themes with others.

Note that the theme file for Tint is:
```
~/.config/tint/tintrc
```and the theme file for visibility is:
```
~/.config/visibility/config
```Here's my current Visibility look:

[IMG]http://i103.photobucket.com/albums/m128/envyouraudience/visibility.png[/IMG]

and here's my config file:
```

orientation top_right
gap_x 05
gap_y 05
image_size 16
spacing 3
border_width 0
desktop_separation 8
show_desktop_names true
single_desktop_mode false
bg_colour 2E2920
border_colour dbcfc1
active_text_colour d43210
inactive_text_colour 544c3f
font MgOpenCosmetica:pixelsize=10
inactive_bg_colour 2E2920
active_bg_colour 2E2920
set_partial_strut false
set_window_type true
tooltip_padding 3
tooltip_time 0.5
tooltip_bg_colour 2E2920
tooltip_border_colour 707070
tooltip_text_colour dbcfc1
tooltip_font MgOpenCosmetica:pixelsize=10
text_spacing 3
active_tint 000000
active_tint_amount 0
inactive_tint 000000
inactive_tint_amount 0.3
iconified_tint 0
iconified_tint_amount 0.55
```

---

### Post by ynnhoj on 2007-07-26
visibility sits at the bottom-left of my screen, beside conky (which displays the time).

```
orientation bottom_left 
gap_x 88  
gap_y 9
image_size 16
spacing 1
border_width 0
desktop_separation 32
show_desktop_names true
single_desktop_mode false
bg_colour cccccc
border_colour 7e7e7e
active_text_colour ff3333
inactive_text_colour 888888
font smoothansi
inactive_bg_colour cccccc
active_bg_colour cccccc
set_partial_strut true
set_window_type true
tooltip_padding 1
tooltip_time 0.5
tooltip_bg_colour cccccc
tooltip_border_colour cccccc
tooltip_text_colour 888888
tooltip_font glisp
text_spacing 3
active_tint 000000
active_tint_amount 0
inactive_tint ffffff
inactive_tint_amount 0.3
iconified_tint 0
iconified_tint_amount 0.55
```

---

### Post by dbbolton on 2007-07-26
so the clock isn't part of visibility? it's a clever illusion!

---

### Post by ynnhoj on 2007-07-26
it took a bit of tinkering to get conky's text centered vertically (as visibility's is), but other than that it's just a matter of setting all the colours and fonts the same and lining them up :)

---

### Post by dbbolton on 2007-07-26
here'e my current tint stuff:

[IMG]http://i103.photobucket.com/albums/m128/envyouraudience/tintrc.png[/IMG]

```
font = gelly
font_color = #636478
font_alpha = 100
font_active_color = #D91000
font_active_alpha = 100
font_shadow = 0
task_text_centered = 1
task_width = 100
task_margin = 3
task_padding = 5
panel_width = 0
panel_height = 30
panel_tasks_centered = 1
panel_background = 0
panel_background_color = #ffffff
panel_background_alpha = 25
task_background = 1
task_background_color = #ECD6BF
task_background_alpha = 10
task_active_background_color = #C08275
task_active_background_alpha = 70
task_background_as_border = 1
```

---

### Post by dbbolton on 2007-07-30
for the few who are so inclined:

i compiled a deb (something that i have never done before) for tint. pal has posted it under the "Downloads" section of the tint project page on google code.

i don't really expect it to work, but please try it out and let me know whether it does :)

---

### Post by felicity on 2007-07-31
The deb works for me, thanks. I'd never heard of this before, it's pretty nifty. :)

---

### Post by el mariachi on 2007-08-02
> **felicity said:**
> The deb works for me, thanks. I'd never heard of this before, it's pretty nifty. :)

I keep getting that nasty PANGO error... I don't get it, since pango is installed.

btw: what's going on with visibility? the website has been down for a few days now

```
Pango-CRITICAL **: pango_font_description_from_string: assertion `str != NULL' failed
```
I already reinstalled everything with the name pango from synaptic. any ideas?

---

### Post by dbbolton on 2007-08-03
> **el mariachi said:**
> I keep getting that nasty PANGO error... I don't get it, since pango is installed.

btw: what's going on with visibility? the website has been down for a few days now

```
Pango-CRITICAL **: pango_font_description_from_string: assertion `str != NULL' failed
```
I already reinstalled everything with the name pango from synaptic. any ideas?
post your problem on the "issues" area of the tint website. pal (staura) will help you.

[http://code.google.com/p/ttm/issues/list](http://code.google.com/p/ttm/issues/list)

---

### Post by shearn89 on 2007-08-06
The Deb worked liked a charm for me! absolutely brilliant, since i'm behind a school firewall (even at home, as i live on campus) and can't use svn to get stuff...  Cheers dbbolton!

anyway, my current tintrc (only just downloaded/installed), so still working on it:
```

font = zekton 10
font_color = #000000
font_alpha = 50
font_active_color = #000000
font_active_alpha = 100
font_shadow = 0

task_text_centered = 0
task_width = 120
task_margin = 0
task_padding = 5

task_background = 1
task_background_color = #ffffff
task_background_alpha = 50
task_active_background_color = #ffffff
task_active_background_alpha = 100
task_background_as_border = 0

panel_width = 0
panel_height = 36
panel_tasks_centered = 0

panel_background = 0
panel_background_color = #ffffff
panel_background_alpha = 0

```

screenshot attached. Any ideas on how to improve, give me a shout. Also, can anyone recommend a good system tray program? I can't seem to get docker to work - i run it, but nothing shows up at all...

---

### Post by dbbolton on 2007-08-06
> **shearn89 said:**
> The Deb worked liked a charm for me! absolutely brilliant, since i'm behind a school firewall (even at home, as i live on campus) and can't use svn to get stuff...  Cheers dbbolton!

anyway, my current tintrc (only just downloaded/installed), so still working on it:
```

font = zekton 10
font_color = #000000
font_alpha = 50
font_active_color = #000000
font_active_alpha = 100
font_shadow = 0

task_text_centered = 0
task_width = 120
task_margin = 0
task_padding = 5

task_background = 1
task_background_color = #ffffff
task_background_alpha = 50
task_active_background_color = #ffffff
task_active_background_alpha = 100
task_background_as_border = 0

panel_width = 0
panel_height = 36
panel_tasks_centered = 0

panel_background = 0
panel_background_color = #ffffff
panel_background_alpha = 0

```screenshot attached. Any ideas on how to improve, give me a shout. Also, can anyone recommend a good system tray program? I can't seem to get docker to work - i run it, but nothing shows up at all...
you might give pypanel a try. you can make it into just a system tray by editing your ~/.pypanelrc file. there is a section that looks like this:

```
#------------------------------------------------------------------------------
# Panel Layout:       -----------------------------------
#                     [  1  ][  2  ][  3  ][  4  ][  5  ]
#                     -----------------------------------
#
# The panel layout is split into 5 sections numbered 1, 2, 3, 4 or 5 as shown
# in the diagram above.  Each of the following objects can be enabled by
# assigning it a section number or disabled by assigning it 0:
#------------------------------------------------------------------------------
DESKTOP         = 0             # Desktop name section
TASKS           = 0             # Task names section 
TRAY            = 1            # System tray section
CLOCK           = 0             # Clock section
LAUNCHER        = 0             # Application launcher section

```

---

### Post by shearn89 on 2007-08-06
yeah - i was using that, but i couldn't see it: i realised i had it hidden underneath the tint panel. All sorted now - looking good. Just posting latest desktop with tint to the desktop thread!

---

### Post by dbbolton on 2007-08-06
> **shearn89 said:**
> yeah - i was using that, but i couldn't see it: i realised i had it hidden underneath the tint panel. All sorted now - looking good. Just posting latest desktop with tint to the desktop thread!
did you find where you can put pypanel at the top of the screen?

---

### Post by el mariachi on 2007-08-08
I'm trying tint (finally it's working)
Any idea how can I make windows don't expand further than tint's height? So that I can still use right-click on my desktop (like I used to do with xfce panel)

---

### Post by urukrama on 2007-08-08
> **el mariachi said:**
> I'm trying tint (finally it's working)
Any idea how can I make windows don't expand further than tint's height? So that I can still use right-click on my desktop (like I used to do with xfce panel)

That is one of the reasons I don't use tint. It looks nice and is useful, but if you maximise windows, tint covers the bottom part of it (it doesn't use a strut), which is very annoying if you actually use that bottom part (statusbars, etc.). I searched, but couldn't find a way around it.

---

### Post by el mariachi on 2007-08-08
> **urukrama said:**
> That is one of the reasons I don't use tint. It looks nice and is useful, but if you maximise windows, tint covers the bottom part of it (it doesn't use a strut), which is very annoying if you actually use that bottom part (statusbars, etc.). I searched, but couldn't find a way around it.
Yeah it's very troublesome. I find the little free space left by the panel very useful to quickly open apps, tint doesn't allow this.
It makes my desktop gorgeous though, so I'll take screenshots with it but I'll use xfce panel most of the time, because I can't get pypanel to work

---

### Post by picpak on 2007-08-10
How does one install Visibility? I can't find an official site, a deb, or SVN anywhere. Can somebody help me out here?

---

### Post by dbbolton on 2007-08-10
> **picpak said:**
> How does one install Visibility? I can't find an official site, a deb, or SVN anywhere. Can somebody help me out here?
you can get the source code from subversion:

```
svn co http://svn.l3ib.org/visibility/trunk visibility
```

---

### Post by picpak on 2007-08-10
All that gave me was 403 errors.

Anyway, I've figured out how to do it and posted instructions [here](http://ubuntuforums.org/showthread.php?p=3168072#post3168072), as well as a .deb.

---

### Post by dbbolton on 2007-08-10
here is a tangerine-style theme for visibility

```
orientation bottom_left        
gap_x 640                       
gap_y 05image_size 16
spacing 5
border_width 1
desktop_separation 8 
show_desktop_names true
single_desktop_mode false
bg_colour f6f6f6          
border_colour fcaf3e      
active_text_colour f57900  
inactive_text_colour a1a1a1 
font BitstreamVeraSans:size=9
inactive_bg_colour f6f6f6  
active_bg_colour f6f6f6    
set_partial_strut false    
set_window_type true        
tooltip_padding 3           
tooltip_time 0.5           
tooltip_bg_colour f57900   
tooltip_border_colour fcaf3e
tooltip_text_colour f6f6f6 
tooltip_font BitstreamVeraSans:size=9             
text_spacing 3             
active_tint 000000          
active_tint_amount 0       
inactive_tint 000000       
inactive_tint_amount 0.3   
iconified_tint 000000           
iconified_tint_amount 0.55
```

i'll post an image in a bit.

---

### Post by juxtaposed on 2007-08-10
Installed Tint .deb, got this error:

tint: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by tint)

I guess i'll have to try compiling it myself.

---

### Post by dbbolton on 2007-08-10
> **juxtaposed said:**
> Installed Tint .deb, got this error:

tint: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by tint)

I guess i'll have to try compiling it myself.
i think you need libglib2.4-dev installed first.

---

### Post by juxtaposed on 2007-08-10
> **dbbolton said:**
> i think you need libglib2.4-dev installed first.

apt-get install libglib2.4-dev
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libglib2.4-dev

I tried to compile it before this but I didn't have checkinstall installed. I tried to install it but it wasn't in etch's repos. I did just find a .deb of checkinstall on the checkinstall site though. I'll try it now.

EDIT: Installed it, but when I try to run it:

Could not grab wallpaper, panel background alpha will be disabled
Segmentation fault

Probably because I have no wallpaper. I'll use feh to get wallpaper then...

EDIT: Did that;

(process:1203): Pango-CRITICAL **: pango_font_description_from_string: assertion `str != NULL' failed
Segmentation fault

EDIT: I guess it is this:

[http://code.google.com/p/ttm/issues/detail?id=7](http://code.google.com/p/ttm/issues/detail?id=7)

---

### Post by dbbolton on 2007-08-10
> **juxtaposed said:**
> apt-get install libglib2.4-dev
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libglib2.4-dev

I tried to compile it before this but I didn't have checkinstall installed. I tried to install it but it wasn't in etch's repos. I did just find a .deb of checkinstall on the checkinstall site though. I'll try it now.

EDIT: Installed it, but when I try to run it:

Could not grab wallpaper, panel background alpha will be disabled
Segmentation fault

Probably because I have no wallpaper. I'll use feh to get wallpaper then...

EDIT: Did that;

(process:1203): Pango-CRITICAL **: pango_font_description_from_string: assertion `str != NULL' failed
Segmentation fault

EDIT: I guess it is this:

[http://code.google.com/p/ttm/issues/detail?id=7](http://code.google.com/p/ttm/issues/detail?id=7)
sorry, i think the correct package name would be libglibmm-2.4-dev or possibly libglib2.0-dev

but it would probably be much easier to compile it anyhow. el mariachi had a similar pango error. he can probably tell you what's happening.

---

### Post by picpak on 2007-08-14
Is there any way to place tint at the top of the screen?

---

### Post by el mariachi on 2007-08-14
I didn't find anything in tintrc that does that, maybe there is a way to do it, but it can't be done with the default tintrc

---

### Post by dbbolton on 2007-08-14
> **el mariachi said:**
> I didn't find anything in tintrc that does that, maybe there is a way to do it, but it can't be done with the default tintrc
not yet, anyhow

---

### Post by dbbolton on 2007-08-15
I made a visibility theme generator. As easy as it is to make the visibility config file, a theme generator may seem somewhat superfluous. This is just something that I wanted to play around with. Eventually, I would like to make a GTK app with a color picker and a live preview.

Anyway, if anyone would like to put it on his server, here it is.

visgen.html
```

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">
<html>
<head>
<title>Visibility Theme Generator</title>
<meta name="author" content="Daniel Bolton">
<meta http-equiv="content-type" content="text/html; charset=UTF-8">
<meta http-equiv="content-type" content="application/xhtml+xml; charset=UTF-8">
</head>
<body>
<form action="visgen.php" method="post">
Position on screen: <input type="text" name="orient" value="bottom_left"/><br />
Pixels from the side of the screen: <input type="text" name="gapx" value="5" /><br />
Pixels from the top/bottom of the screen: <input type="text" name="gapy" value="5" /><br />
Icon square size: <input type="text" name="iconsize" value="16" /><br />
Pixels between icons: <input type="text" name="spacing" value="5" /><br />
Border width: <input type="text" name="bordwid" value="1" /><br />
Pixels between desktops: <input type="text" name="desksep" value="8" /><br />
Show desktop names: <input type="text" name="deskname" value="true" /><br />
Only show icons from current desktop: <input type="text" name="singdesk" value="false" /><br />
Background colour: <input type="text" name="bkgdcol" value="ff0000" /><br />
Border colour: <input type="text" name="bordcol" value="00ff00"/><br />
Active text colour: <input type="text" name="acttxt" value="00ff00" /><br />
Inactive text colour: <input type="text" name="inacttxt" value="686868"/><br />
Xft font: <input type="text" name="font" value="BitStreamVeraSans:size=8"/><br />
Inactive desktop background colour: <input type="text" name="inactdesk" value="8f8f8f" /><br />
Active desktop background colour: <input type="text" name="actdesk" value="f0f0f0" /><br />
Reserve space on the desktop edge: <input type="text" name="strut" value="false" /><br />
Panel/dock mode: <input type="text" name="windowtype" value="true"/><br />
Padding inside tooltips: <input type="text" name="tippad" value="3" /><br />
Tooltip delay in seconds: <input type="text" name="tiplay" value="0.5" /><br />
Tooltip background colour: <input type="text" name="bkgdtip"value="00ff00" /><br />
Tooltip border colour: <input type="text" name="bordtip" value="ff00ff" /><br />
Tooltip text colour: <input type="text" name="txttip" value="ffffff" /><br />
Tooltip Xft font: <input type="text" name="fonttip" value="BitStreamVeraSans:size=8"/><br />
Pixels between desktop name and first icon: <input type="text" name="txtspace" value="3" /><br />
Active window tint colour: <input type="text" name="acttint" value="000000"/><br />
Active tint amount (from 0 to 1): <input type="text" name="acttintamt" value="0.0" /><br />
Inactive window tint colour: <input type="text" name="inacttint" value="a6a6a6"/>
Inactive tint amount: <input type="text" name="inacttintamt" value="0.3"/><br />
Iconified/hidden window tint colour: <input type="text" name="ictint" value="000000"/><br />
Iconified/hidden tint amount: <input type="text" name="ictintamt" value="0.6" /><br />
<input type="submit" value="Create Theme" />
</form>
</body>
</html>

```

visgen.php
```

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">
<html>
<head>
<title>Your Visibility Theme</title>
<meta name="author" content="Daniel Bolton">
<meta http-equiv="content-type" content="text/html; charset=UTF-8">
<meta http-equiv="content-type" content="application/xhtml+xml; charset=UTF-8">
</head>
<body>
# Copy and paste this as a file called '~/.config/visibility/config'
orientation <?php echo $_POST["orient"]; ?><br />
gap_x <?php echo $_POST["gapx"]; ?><br />
gap_y <?php echo $_POST["gapy"]; ?><br />
image_size <?php echo $_POST["iconsize"]; ?><br />
spacing <?php echo $_POST["spacing"]; ?><br />
border_width <?php echo $_POST["bordwid"]; ?><br />
desktop_separation <?php echo $_POST["desksep"]; ?><br />
show_desktop_names <?php echo $_POST["deskname"]; ?><br />
single_desktop_mode <?php echo $_POST["desksing"]; ?><br />
bg_colour <?php echo $_POST["bkgdcol"]; ?><br />
border_colour <?php echo $_POST["bordcol"]; ?><br />
active_text_colour <?php echo $_POST["acttxt"]; ?><br />
inactive_text_colour <?php echo $_POST["inacttxt"]; ?><br />
font <?php echo $_POST["font"]; ?><br />
inactive_bg_colour <?php echo $_POST["inactdesk"]; ?><br />
active_bg_colour <?php echo $_POST["actdesk"]; ?><br />
set_partial_strut <?php echo $_POST["strut"]; ?><br />
set_window_type <?php echo $_POST["windowtype"]; ?><br />
tooltip_padding <?php echo $_POST["tippad"]; ?><br />
tooltip_time <?php echo $_POST["tiplay"]; ?><br />
tooltip_bg_colour <?php echo $_POST["bkgdtip"]; ?><br />
tooltip_border_colour <?php echo $_POST["bordtip"]; ?><br />
tooltip_text_colour <?php echo $_POST["txttip"]; ?><br />
tooltip_font <?php echo $_POST["fonttip"]; ?><br />
text_spacing <?php echo $_POST["txtspace"]; ?><br />
active_tint <?php echo $_POST["acttint"]; ?><br />
active_tint_amount <?php echo $_POST["inacttintamt"]; ?><br />
inactive_tint <?php echo $_POST["inacttint"]; ?><br />
inactive_tint_amount <?php echo $_POST["inacttintamt"]; ?><br />
iconified_tint <?php echo $_POST["ictint"]; ?><br />
iconified_tint_amount <?php echo $_POST["ictintamt"]; ?><br />
</body>
</html>

```

---

### Post by dbbolton on 2007-08-19
here's a theme generator for tint:

ttmgen.html
[HTML]<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">
<html>
<head>
<title>TTM Theme Generator</title>
<meta name="author" content="Daniel Bolton">
<meta http-equiv="content-type" content="text/html; charset=UTF-8">
<meta http-equiv="content-type" content="application/xhtml+xml; charset=UTF-8">
</head>
<body>
<form action="ttmgen.php" method="post">
<h3>Font</h3>
Face: <input type="text" name="font" value="BitStreamVeraSans Bold 10"/><br />
Color: <input type="text" name="font_color" value="#666666"/><br />
Alpha (%): <input type="text" name="font_alpha" value="90"/><br />
Active color: <input type="text" name="font_active_color" value="#ffffff"/><br />
Active alpha (%): <input type="text" name="font_active_alpha" value="100"/><br />
Shadow (0 = no, 1 = yes): <input type="text" name="font_shadow" value="0"/><br />
<br />
<h3>Tasks</h3>
Center labels (0 = no, 1 = yes): <input type="text" name="task_text_centered" value="1"/><br />
Task width (pixels): <input type="text" name="task_width" value="100"/><br />
Task margin (pixels): <input type="text" name="task_margin" value="3"/><br />
Task padding (pixels): <input type="text" name="task_padding" value="5"/><br />
<br />
<h3>Panel</h3>
Width (pixels [0 = full width]): <input type="text" name="panel_width" value="0"/><br />
Height (pixels): <input type="text" name="panel_height" value="30"/><br />
Center Tasks (0 = no, 1 = yes): <input type="text" name="panel_tasks_centered" value="1"/><br />
<br />
<h3>Panel Background</h3>
Draw panel background (0 = no, 1 = yes): <input type="text" name="panel_background" value="0"/><br />
(If there is no panel background, the next two fields will be ignored.)<br />
Color: <input type="text" name="panel_background_color" value="#ffffff"/><br />
Alpha (%): <input type="text" name="panel_background_alpha" value="0"/><br />
<br />
<h3>Task Background</h3>
Draw task background (0 = no, 1 = yes): <input type="text" name="task_background" value="1"/><br />
(If there is no task background, the next five fields will be ignored.)<br />
Color: <input type="text" name="task_background_color" value="#ff0000"/><br />
Alpha (%): <input type="text" name="task_background_alpha" value="50"/><br />
Active color: <input type="text" name="task_active_background_color" value="#ff0000"/><br />
Active alpha (%): <input type="text" name="task_active_background_alpha" value="90"/><br />
Background appears below text (0 = no, 1 = yes): <input type="text" name="task_background_as_border" value="0"/><br />
<br />
<input type="submit" value="Create Theme" />
</form>
</body>
</html>[/HTML]


ttmgen.php
[PHP]<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">
<html>
<head>
<title>Your TTM Theme</title>
<meta name="author" content="Daniel Bolton">
<meta http-equiv="content-type" content="text/html; charset=UTF-8">
<meta http-equiv="content-type" content="application/xhtml+xml; charset=UTF-8">
</head>
<body>
<h4># Copy and paste this as a file called '~/.config/tint/tintrc'</h4>
<p>
font = <?php echo $_POST["font"]; ?><br />
font_color = <?php echo $_POST["font_color"]; ?><br />
font_alpha = <?php echo $_POST["font_alpha"]; ?><br />
font_active_color = <?php echo $_POST["font_active_color"]; ?><br />
font_active_alpha = <?php echo $_POST["font_active_alpha"]; ?><br />
font_shadow = <?php echo $_POST["font_shadow"]; ?><br />
</p>
task_text_centered = <?php echo $_POST["task_text_centered"]; ?><br />
task_width = <?php echo $_POST["task_width"]; ?><br />
task_margin = <?php echo $_POST["task_margin"]; ?><br />
task_padding = <?php echo $_POST["task_padding"]; ?><br />
<p>
panel_width = <?php echo $_POST["panel_width"]; ?><br />
panel_height = <?php echo $_POST["panel_height"]; ?><br />
panel_tasks_centered = <?php echo $_POST["panel_tasks_centered"]; ?><br />
</p>
panel_background = <?php echo $_POST["panel_background"]; ?><br />
panel_background_color = <?php echo $_POST["panel_background_color"]; ?><br />
panel_background_alpha = <?php echo $_POST["panel_background_color"]; ?><br />
<p>
task_background = <?php echo $_POST["task_background"]; ?><br />
task_background_color = <?php echo $_POST["task_background_color"]; ?><br />
task_background_alpha = <?php echo $_POST["task_background_alpha"]; ?><br />
task_active_background_color = <?php echo $_POST["task_active_background_color"]; ?><br />
task_active_background_alpha = <?php echo $_POST["task_active_background_alpha"]; ?><br />
task_background_as_border = <?php echo $_POST["task_background_as_border"]; ?><br />
</p>
</body>
</html>[/PHP]

---

### Post by shearn89 on 2007-08-24
> **dbbolton said:**
> here's a theme generator for tint:
ttmgen.html


cheers db - makes it easier!

---

### Post by el mariachi on 2007-09-01
is there a way to choose the font size? Mine is too big for my taste

---

### Post by dbbolton on 2007-09-01
> **el mariachi said:**
> is there a way to choose the font size? Mine is too big for my taste
yeah, are you using tint or visibility?

---

### Post by el mariachi on 2007-09-01
> **dbbolton said:**
> yeah, are you using tint or visibility?
forgot to say it's tint :p

---

### Post by dbbolton on 2007-09-01
the formula for the font is like this:

font = [FAMILY-LIST] [STYLE-OPTIONS] [SIZE]

so you could say:

font = BitstreamVeraSans 10

---

### Post by el mariachi on 2007-09-01
> **dbbolton said:**
> the formula for the font is like this:

font = [FAMILY-LIST] [STYLE-OPTIONS] [SIZE]

so you could say:

font = BitstreamVeraSans 10
It seems that TTF fonts don't work, or is it just me?

---

### Post by dbbolton on 2007-09-01
what's the name of the font that you're trying to use?

---

### Post by el mariachi on 2007-09-01
MgOpen Modata

---

### Post by dbbolton on 2007-09-01
> **el mariachi said:**
> MgOpen Modata
did you put a space in the name in your rc file? if so, putting "MgOpenModata 8" should work.

---

### Post by el mariachi on 2007-09-01
it still doesn't work. Dreamspeak doesn't work either so it must mustn't support ttf fonts

---

### Post by dbbolton on 2007-09-01
> **el mariachi said:**
> it still doesn't work. Dreamspeak doesn't work either so it must mustn't support ttf fonts
hmm, it's worked for me with TTF fonts like MgOpenCosmetica and HandelGotDLig...

i don't know why it's not working for you

---

### Post by el mariachi on 2007-09-01
Maybe there's a package missing :confused: I'm on an Ubuntu server so that's not impossible.

---

### Post by shearn89 on 2007-09-14
> **dbbolton said:**
> hmm, it's worked for me with TTF fonts like MgOpenCosmetica and HandelGotDLig...

i don't know why it's not working for you

Which version of tint are you using? I can only get some fonts to work - MgOpenCosmetica works but HandelGotDLig doesn't, neither does Zekton.

---

### Post by el mariachi on 2007-09-14
I got it from a deb in it's site (I think dbbolton did it [?]). I don't know if it's the latest version.
No TTF font works for me. I can change the font size and use Linux fonts like Monospace though.

---

### Post by shearn89 on 2007-09-14
yeah - it seems to only not work with fonts i've installed (zekton, handelgotdlig, etc..). With zekton I get a "pango-warning shape engine failure"?? With the others, it just reverts to a default font.

---

### Post by el mariachi on 2007-09-14
It seems the .deb isn't the latest version. I installed from svn and now I can change fonts and the 'untitled' windows bug is gone, but it looks like this (see attachment) weird:confused:

---

### Post by shearn89 on 2007-09-14
hmm. very strange. I can't download the svn - behind a corporate firewall, so no joy... Looks like i'll have to wait til we get Orange Broadband.

---

### Post by el mariachi on 2007-09-14
uhmm.... I filed a bug. The response time is not that great but the guy must have a RL too lol

---

### Post by dbbolton on 2007-09-18
here's a tint theme that will go nicely with victrola (or maybe GSM too):

```

#---------------------------------------------
# TTM CONFIG FILE
#
# colors: hex format
# booleans: 0 or 1 
# alpha: 0 to 100 percent
# font: [FAMILY-LIST] [STYLE-OPTIONS] [SIZE]
# panel_width: 0 == use full width
#---------------------------------------------

#---------------------------------------------
# FONT
#---------------------------------------------
font = HandelGotDLig 08
font_color = #B8D2CF
font_alpha = 90
font_active_color = #2A1E12
font_active_alpha = 100
font_shadow = 0

#---------------------------------------------
# TASKS
#---------------------------------------------
task_text_centered = 1
task_width = 100
task_margin = 3
task_padding = 5

#---------------------------------------------
# PANEL
#---------------------------------------------
panel_width = 0
panel_height = 30
panel_tasks_centered = 1

#---------------------------------------------
# PANEL BACKGROUND
#---------------------------------------------
panel_background = 0
panel_background_color = #ffffff
panel_background_alpha = 25

#---------------------------------------------
# TASK BACKGROUND
#---------------------------------------------
task_background = 1
task_background_color = #a0a0a0
task_background_alpha = 0
task_active_background_color = #2A1E12
task_active_background_alpha = 100
task_background_as_border = 1

```[[IMG]http://i103.photobucket.com/albums/m128/envyouraudience/th_screenshot_180907.jpg[/IMG]]("http://i103.photobucket.com/albums/m128/envyouraudience/screenshot_180907.jpg")

---

### Post by shearn89 on 2007-09-24
> **dbbolton said:**
> here's a tint theme that will go nicely with victrola (or maybe GSM too):


nice. What OB theme are you using?

---

### Post by dbbolton on 2007-09-24
victrola: [http://gnome-look.org/content/show.php/Rezlooks-Victrola?content=49444](http://gnome-look.org/content/show.php/Rezlooks-Victrola?content=49444)

---

### Post by PurposeOfReason on 2007-09-30
Is it possible to make tint stay in the bottom left but not take up the whole bottom part of the screen?

---

### Post by el mariachi on 2007-09-30
Yes it is. Just change it's width variable.

---

### Post by PurposeOfReason on 2007-09-30
I tried that, but then it moves it to the center and takes the width off both sides.

---

### Post by dbbolton on 2007-09-30
> **PurposeOfReason said:**
> I tried that, but then it moves it to the center and takes the width off both sides.
you need to turn off the center option:

```
panel_tasks_centered = 0
```

---

### Post by PurposeOfReason on 2007-09-30
I've done that too. . .

---

### Post by dbbolton on 2007-09-30
maybe it's:

task_text_centered = 0

---

### Post by rjmdomingo2003 on 2007-10-04
I can't seem to remove the borders & window when I 

```
$tint
```

what gives? I'm using fluxbox as my WM.

Here's my tintrc
> 
font = HandelGotDLig 09
font_color = #B8D2CF
font_alpha = 40
font_active_color = #ACACAC
font_active_alpha = 150
font_shadow = 0
task_text_centered = 1
task_width = 100
task_margin = 3
task_padding = 5
panel_width = 0
panel_height = 25
panel_tasks_centered = 1
panel_background = 0
panel_background_color = #ffffff
panel_background_alpha = 20
task_background = 0
task_background_color = #A0A0A0
task_background_alpha = 0
task_active_background_color = #2A1E12
task_active_background_alpha = 70
task_background_as_border = 1

Did I miss something?

---

### Post by Vansinnesvisan on 2007-10-16
Is there a proper fix for the 'untitled' bug? I still have it in the latest svn.

The bug is listed as [fixed]("http://code.google.com/p/ttm/issues/detail?id=8&can=1")  but the issue persists for me.

---

### Post by el mariachi on 2007-10-16
> **Vansinnesvisan said:**
> Is there a proper fix for the 'untitled' bug? I still have it in the latest svn.

The bug is listed as [fixed]("http://code.google.com/p/ttm/issues/detail?id=8&can=1")  but the issue persists for me.
It's fixed for me. I think I used a .deb (if there is no deb then I used SVN lol I just can't remember)

---

### Post by spupy on 2007-10-30
Hi! I am sorry i have to bump this thread! I installed tint and copied some tintrc from you guys. Just wanted to ask if it is possible to make tint display the windows from all workspaces? What about all non minimized windows from all workspaces? (Yeah, i got some strange fluxbox habits!)

---

### Post by arbulus on 2007-11-07
> **rjmdomingo2003 said:**
> I can't seem to remove the borders & window when I 

```
$tint
```

what gives? I'm using fluxbox as my WM.

Here's my tintrc


Did I miss something?



I'm wondering an answer to this one as well.  I can't get the window title bar or borders to go away.  

And there really is almost no info available on the net about Tint.

---

### Post by PurposeOfReason on 2007-11-22
Is there a way to get an earlier version of tint? I'd like the same version as the .deb, but as the computer I want it for uses arch that doesn't help me much. The newest svn always tries to draw an icon.

EDIT - and if anyone could help me achieve the middle tint on this page I'd be grateful.
[http://code.google.com/p/ttm/](http://code.google.com/p/ttm/)

---

### Post by alphane on 2007-11-23
Little bit of playing for 30 mins:

```
font = TlgwMono 8
font_color = #9a9a9a
font_alpha = 100
font_active_color = #FFFFFF
font_active_alpha = 100
font_shadow = 0
task_text_centered = 1
task_width = 100
task_margin = 3
task_padding = 5
panel_width = 0
panel_height = 30
panel_tasks_centered = 0
panel_background = 1
panel_background_color = #000000
panel_background_alpha = 15
task_background = 1
task_background_color = #000000
task_background_alpha = 30
task_active_background_color = #C08275
task_active_background_alpha = 70
task_background_as_border = 1
```

gives you 30% black bar 100% width, left aligned tasks, faded non-active.

need to work on fonts next, nothing is changing at the min.

---

### Post by fedex1993 on 2007-12-29
can anyone help me setup tint i have it installed and what not but i dont understand on how to start using it and what not

---

### Post by el mariachi on 2007-12-29
to start tint you need to issue the command *tint.*
it's best to issue it from a prompt like grun or any 'run program' prompt your Desktop Environment has.

The configuration file sits in ~/.config/tint/tint.rc
I think the default one is commented so it's easy to mod to your taste. If not, just thinker with it or try some settings posted on this thread.

Please tell us what Desktop Environment are you using, so that we can tell you how to set up tint to be launched on startup (if you want that, of course)

:KS

---

### Post by dbbolton on 2007-12-30
> **el mariachi said:**
> to start tint you need to issue the command *tint.*
it's best to issue it from a prompt like grun or any 'run program' prompt your Desktop Environment has.

The configuration file sits in ~/.config/tint/tint.rc
I think the default one is commented so it's easy to mod to your taste. If not, just thinker with it or try some settings posted on this thread.

Please tell us what Desktop Environment are you using, so that we can tell you how to set up tint to be launched on startup (if you want that, of course)

:KS
actually i think it's ~/.config/tint/tintrc

(no dot)

---

### Post by el mariachi on 2007-12-30
you must be right ;) I haven't got tint installed

---

### Post by urukrama on 2008-06-10
Here is my visibility config file:

```
# a sample config file for visibility.
# this file goes in ~/.config/visibility/config
# it can be used to set a theme and override specific options.

# uncomment this option to use the theme 'magicaltheme'
# themes are stored in ~/.themes/theme_name/visibility/theme
# theme syntax is identical to the syntax of this config file.
# (yes, a theme could 'inherit' from another theme by specifying a theme!)

#theme magicaltheme

orientation bottom_left    # set this to the corner of the desktop that you
                            # would like visibility to be placed. valid options:
                            # top_left, top_right, bottom_left, bottom_right
                            
gap_x 55                    # the amount of space to leave between the pager and
                            # the side of the desktop.
                            
gap_y 3                    # the amount of space to leave between the pager and
                            # the top or bottom of the desktop.

image_size 12               # the pixel size of an icon; icons are square.

spacing 5                   # the amount of space to leave between icons as well
                            # as between the edge of the window and the icons.

border_width 1              # the width of the border around the window. can be 
                            # set to 0 if your window manager (like openbox!) 
                            # can provide its own borders for borderless
                            # windows.

desktop_separation 10        # the amount of space to leave between desktops.

show_desktop_names true     # whether or not to show desktop names. these names
                            # are specified by your window manager. valid
                            # options are 'true' and 'false'.

single_desktop_mode false   # whether or not to show only windows from the
                            # current desktop.

bg_colour 3C4746            # the background colour

border_colour 758C8A       # the border colour

active_text_colour DCD5C0   # the colour of the name of the active desktop.

inactive_text_colour 758C8A # the colour of the name an inactive desktop.

font AvantGarde LT Medium-7                     # the name of the font to use. this is an xft name,
                            # so one could use 'verdana:pixelsize=10' or
                            # 'verdana-10'.
                            
inactive_bg_colour 3C4746   # the background colour of inactive desktops.

active_bg_colour 3C4746     # the background colour of active desktops.
                            # if you hate this setting, set it to the same as
                            # bg_colour and inactive_bg_colour, and you will
                            # probably be a happy camper.

set_partial_strut true     # whether or not to reserve space on the desktop
                            # edge. this is useful if you do not want windows
                            # to maximize over visibility.

set_window_type true        # if true, visibility sets itself to be of 'dock'
                            # type, which is meant for panels. this is useful if
                            # you want it to be 'always on top', and other
                            # panel-like things.

tooltip_padding 3           # the amount of padding to have inside tooltips.

tooltip_time 0.5            # the number of seconds before a tooltip shows up.

tooltip_bg_colour  3C4746    # the tooltip background colour.

tooltip_border_colour 758C8A # the tooltip border colour.

tooltip_text_colour 758C8A   # the colour of text in tooltips

tooltip_font AvantGarde LT Medium-7             # the font to use in tooltips

text_spacing 3              # the amount of spacing to leave between the
                            # desktop name and first icon.

active_tint 000000          # the colour to tint the active window with

active_tint_amount 0        # the amount to tint the active window (0..1)

inactive_tint 3C4746        # the colour to tint inactive windows with

inactive_tint_amount 0    # the amount to tint active windows (0..1)

iconified_tint 0            # the colour to tint iconified (and 'hidden')
                            # windows with

iconified_tint_amount 0.2  # the amount to tint iconified windows (0..1)

```

And here is a screenshot:

(The pypanel and conky configurations can be found [here]("http://ubuntuforums.org/showthread.php?p=5156621#post5156621") and [here]("http://ubuntuforums.org/showthread.php?p=5156646#post5156646"))

---

### Post by PoopSlayer on 2008-06-12
Well I know it's probably kind of late, but to make tint not cover the bottom of maximize windows, just set a margin at the bottom of your screen in your window manager settings.

As for my tintrc:

```
#---------------------------------------------
# TTM CONFIG FILE
#
# colors: hex format
# booleans: 0 or 1 
# alpha: 0 to 100 percent
# font: [FAMILY-LIST] [STYLE-OPTIONS] [SIZE]
# panel_width: 0 == use full width
#---------------------------------------------

#---------------------------------------------
# FONT
#---------------------------------------------
font = nu 10
font_color = #B52F62
font_alpha = 100
font_active_color = #0D8778
font_active_alpha = 100
font_shadow = 0

#---------------------------------------------
# TASKS
#---------------------------------------------
task_text_centered = 1
task_width = 150
task_margin = 3
task_padding = 5

#---------------------------------------------
# PANEL
#---------------------------------------------
panel_width = 0
panel_height = 25
panel_tasks_centered = 0

#---------------------------------------------
# PANEL BACKGROUND
#---------------------------------------------
panel_background = 1
panel_background_color = #000000
panel_background_alpha = 50

#---------------------------------------------
# TASK BACKGROUND
#---------------------------------------------
task_background = 1
task_background_color = #ffffff
task_background_alpha = 25
task_active_background_color = #ffffff
task_active_background_alpha = 50
task_background_as_border = 0
```

Screen: [http://i26.tinypic.com/2mg4dh3.png](http://i26.tinypic.com/2mg4dh3.png)

Using the openbox theme twm (which is what the colors are based off of). It's here: [link](http://box-look.org/content/show.php/twm+theme?content=77853)

I like to be color coordinated :)

---

### Post by dbbolton on 2008-07-08
Trying out the new version of tint ( [http://code.google.com/p/tint2/](http://code.google.com/p/tint2/) )

[[IMG]http://i103.photobucket.com/albums/m128/envyouraudience/th_tint2080708.png[/IMG]](http://i103.photobucket.com/albums/m128/envyouraudience/tint2080708.png)

tintrc:
```

#---------------------------------------------
# TTM CONFIG FILE
#
# colors: hex format
# booleans: 0 or 1 
# alpha: 0 to 100 percent
# font: [FAMILY-LIST] [STYLE-OPTIONS] [SIZE]
# panel_width: 0 == use full width
#---------------------------------------------

#---------------------------------------------
# FONT
#---------------------------------------------
font = myriad pro 10
font_color = #ececec
font_alpha = 50
font_active_color = #ffffff
font_active_alpha = 80
font_shadow = 0

#---------------------------------------------
# PANEL
# panel_position : bottom left, bottom right, bottom center, top left, top right, top center
# panel_show_all_desktop = 0 : tint show one taskbar from current desktop
# panel_show_all_desktop = 1 : tint show all taskbar
#---------------------------------------------
panel_show_all_desktop = 1
panel_width = 1100
panel_height = 30
panel_margin = 3
panel_position = bottom center

#---------------------------------------------
# PANEL BACKGROUND
#---------------------------------------------
panel_background = 1
panel_background_color = #000000
panel_background_alpha = 50
panel_border_width = 1
panel_border_color = #ffffff
panel_border_alpha = 10
panel_rounded = 10

#---------------------------------------------
# TASKS
#---------------------------------------------
task_text_centered = 1
task_width = 110
task_margin = 2
task_padding = 3
task_icon = 1
task_icon_size = 16

#---------------------------------------------
# TASK BACKGROUND AND BORDER
#---------------------------------------------
task_background = 1
task_background_color = #ffffff
task_background_alpha = 0

task_active_background_color = #ffffff
task_active_background_alpha = 15

task_border_width = 0
task_border_color = #d2d2d2
task_border_alpha = 0

task_rounded = 10

task_active_border_width = 1
task_active_border_color = #d2d2d2
task_active_border_alpha = 15
task_active_rounded = 10

#---------------------------------------------
# MOUSE ACTION
# configure mouse action with
# (none, close, toggle, iconify, shade, toggle_iconify)
#---------------------------------------------
mouse_middle = none
mouse_right = close
mouse_scroll_up = toggle
mouse_scroll_down = iconify

```

---

### Post by urukrama on 2008-07-08
> **dbbolton said:**
> Trying out the new version of tint ( [http://code.google.com/p/tint2/](http://code.google.com/p/tint2/) )

I didn't know it was out yet. Thanks for letting us know. I'll try it out soon. Are some of the "Tint panel features" already implemented (if so, what are they?), or is this planned for the future?

---

### Post by dbbolton on 2008-07-08
> **urukrama said:**
> I didn't know it was out yet. Thanks for letting us know. I'll try it out soon. Are some of the "Tint panel features" already implemented (if so, what are they?), or is this planned for the future?
The new features I see are rounded edges, panel and task borders, multiple desktops, and custom mouse actions

---

### Post by elmer_42 on 2008-07-21
I'm failing at compiling Tint. Is there a deb available anywhere?

---

### Post by jjgomera on 2008-07-21
> **elmer_42 said:**
> I'm failing at compiling Tint. Is there a deb available anywhere?

downloads code from here: [http://code.google.com/p/tint2/downloads/list](http://code.google.com/p/tint2/downloads/list)
and umpack it

install depends:
sudo aptitude install libcairo2-dev libpango1.0-dev libglib2.0-dev libimlib2-dev

open a terminal in directory /...../tint/src

make
checkinstall to do deb

---

### Post by RavUn on 2008-07-23
Is it not possible to make the icons clickable?  The config file I have doesn't let me click anything.  I didn't know if that's how it's supposed to be or if I'm missing something.

---

### Post by elmer_42 on 2008-07-24
Curses! They removed the 'panel_tasks_centered' option. Does anybody know if they plan on adding something similar it sometime soon?

and to stay on topic:
[[img]http://arch.kimag.es/resized/46458182.png[/img]](http://arch.kimag.es/share/46458182.png)
```
#---------------------------------------------
# TINT CONFIG FILE
#---------------------------------------------

#---------------------------------------------
# PANEL
#---------------------------------------------
panel_mode = single_desktop
panel_monitor = 1
panel_position = bottom left
panel_size = 1000 25
panel_margin = 1 0
panel_padding = 0 1
font_shadow = 0

#---------------------------------------------
# PANEL BACKGROUND AND BORDER
#---------------------------------------------
panel_rounded = 9
panel_border_width = 1
panel_background_color = #000000 0
panel_border_color = #000000 0

#---------------------------------------------
# TASKS
#---------------------------------------------
task_text_centered = 1
task_width = 200
task_margin = 2
task_padding = 1
task_icon_size = 0
task_font = Existence 11
task_font_color = #ffffff 59
task_active_font_color = #ffffff 90

#---------------------------------------------
# TASK BACKGROUND AND BORDER
#---------------------------------------------
task_rounded = 3
task_background_color = #000000 50
task_active_background_color = #000000 55
task_border_width = 0
task_border_color = #d1d1d1 34
task_active_border_color = #d1d1d1 40

#---------------------------------------------
# CLOCK
#---------------------------------------------
#time1_format = %H:%M
time1_font = sans bold 8
#time2_format = %A %d %B
time2_font = sans 6
clock_font_color = #ffffff 75

#---------------------------------------------
# MOUSE ACTION ON TASK
#---------------------------------------------
mouse_middle = close
mouse_right = none
mouse_scroll_up = toggle
mouse_scroll_down = none
```
**e:**Code tags! GAH!

---

### Post by Fufkin on 2008-07-25
Just installed tint2 and really like it - just what I've been looking for. :)

However I have an annoying problem: the first time I click a task the whole tint panel 'jumps' upwards by the same amount as its own height.

(If I set the panel to be at the top it jumps downwards instead.)

After this initial jump it stays in the same place when clicked, but if I move the panel back to where it's meant to be at the bottom of the screen it will jump away again.

It's almost like it tries to reserve a place for itself on the desktop and move everything else out of the way, but for some reason ends up moving itself. :confused:

I am left with a blank space at the bottom of the screen which windows won't fill when maximised, and the actual tint panel hidden behind open windows.

Any ideas about what's going on?

---

### Post by thil77 on 2008-07-25
> However I have an annoying problem ...

Hi Fufkin,

can you post your config file ?
and witch window manager you are using ?

if you define margin in your window manager config, try to remove margin.

---

### Post by Fufkin on 2008-07-25
> **thil77 said:**
> > However I have an annoying problem ...

Hi Fufkin,

can you post your config file ?
and witch window manager you are using ?

if you define margin in your window manager config, try to remove margin.

Hi :)

This happens even with the default config file :(

I am using compiz... I guess I could switch to openbox but I'd rather not lose my compiz setup...

edit: Just tried with openbox and it works fine.  I guess it's a compiz thing.  I know tint is designed for openbox, but the site does say it should work with other window managers...

> **thil77 said:**
> > However I have an annoying problem ...
if you define margin in your window manager config, try to remove margin.

Don't think I have a margin set in compiz, but not really sure where to look.

---

### Post by Pogeymanz on 2008-07-26
Hey guys. I have a question for you.

I'm running Openbox with tint. How can I make tint stay above other windows?

I already have a margin set so that maximized windows don't cover it, but I'm referring to dragging a window around. I don't want it to cover tint. I could've sworn it already had this behavior until a recent update. Or maybe I'm crazy.


```
#---------------------------------------------
# TINT CONFIG FILE
#---------------------------------------------

#---------------------------------------------
# PANEL
#---------------------------------------------
panel_mode = single_desktop
panel_monitor = 1
panel_position = bottom center
panel_size = 900 24
panel_margin = 0 0
panel_padding = 1 1
font_shadow = 0

#---------------------------------------------
# PANEL BACKGROUND AND BORDER
#---------------------------------------------
panel_rounded = 0
panel_border_width = 1
panel_background_color = #000000 70
panel_border_color = #000000 100

#---------------------------------------------
# TASKS
#---------------------------------------------
task_text_centered = 1
task_width = 110
task_margin = 1
task_padding = 1
task_icon_size = 12
task_font = sagar 8
task_font_color = #ffffff 75
task_active_font_color = #ffffff 95

#---------------------------------------------
# TASK BACKGROUND AND BORDER
#---------------------------------------------
task_rounded = 4
task_background_color = #ffffff 15
task_active_background_color = #ffffff 30
task_border_width = 1
task_border_color = #000000 35
task_active_border_color = #000000 40

#---------------------------------------------
# CLOCK
#---------------------------------------------
#time1_format = %H:%M
time1_font = sans bold 8
#time2_format = %A %d %B
time2_font = sans 6
clock_font_color = #ffffff 75

#---------------------------------------------
# MOUSE ACTION ON TASK
#---------------------------------------------
mouse_middle = close
mouse_right = none
mouse_scroll_up = toggle
mouse_scroll_down = iconify



```

---

### Post by thil77 on 2008-07-27
> I already have a margin set so that maximized windows don't cover it, but I'm referring to dragging a window around. I don't want it to cover tint. I could've sworn it already had this behavior until a recent update. Or maybe I'm crazy.

No, you are not crazy !
With the next release, tint is always behind other's window.

This is because tint use fake transparency.
So if tint is in top and you drag a window behind, tint will always show the background.
It's not beautiful...

---

### Post by Pogeymanz on 2008-07-27
While that is true, I still find it more useful to have a non-beautiful task bar above the windows, than a beautiful bar behind them. Oh well.

---

### Post by dbbolton on 2008-07-27
> **Pogeymanz said:**
> Hey guys. I have a question for you.

I'm running Openbox with tint. How can I make tint stay above other windows?

I already have a margin set so that maximized windows don't cover it, but I'm referring to dragging a window around. I don't want it to cover tint. I could've sworn it already had this behavior until a recent update. Or maybe I'm crazy.


Try adding this to your rc.xml in the <applications> section (probably around line 382):

```

<application class="panel">
    <layer>above</layer>
  </application>

```

---

### Post by PurposeOfReason on 2008-07-29
I'm running gnome/compiz and was wondering if it was possibly to get tint2 to only display the running aps for each workspace. I know XFCE often has troubles with conflicting workspaces and compiz but I'm not sure about gnome.

---

### Post by urukrama on 2008-07-29
> **dbbolton said:**
> Try adding this to your rc.xml in the <applications> section (probably around line 382):

```

<application class="panel">
    <layer>above</layer>
  </application>

```

I tried that, but it didn't have any effect. 

Tint2 doesn't have a WM_CLASS or WM_WINDOW_ROLE, so you can't specify those either in the rc.xml.

---

### Post by sergex on 2008-07-30
tint doesn't show gedit task :(

---

### Post by toozler on 2008-08-28
As of tint2 displaing window decorations if you're using Compiz, open the CompizConfigSettingsManager (ccsm), go on "Windows Decorations" and on the "Decoration Windows", use: **(any) & !(title=tint)**

The problem is that if you open your tint folder or edit your tintrc, the window decorations won't show for that window. Not a real problem.

Now my turn seek help.. I'm running tint on Ubuntu 8.04, replacing the gnome-panel. I'm running compiz aswell. I'm getting these gliches, no matter what tintrc config I try.

Also, my first click on it, moves it down and it stays there. Any ideas?

---

### Post by toozler on 2008-08-28
Instead of **(any) & !(title=tint)**, use **(any) & !(type=dock)**, works better!

Still, any suggestion on how to solve tint transparency glich? And moving after click?

---

### Post by thil77 on 2008-08-30
tint have a bug with transparency...

the move after click is not done by tint. I think it's a bug in compiz.

check [http://ubuntuforums.org/showthread.php?t=875971&highlight=tint](http://ubuntuforums.org/showthread.php?t=875971&highlight=tint)
and report if it solve the problem.

---

### Post by Mark76 on 2008-09-23
I'm having a problem with Tint. As you can see from the screenshots below it tends to divide the first task panel into two rather than create a new task panel for each task.

[[img]http://xs231.xs.to/xs231/08392/gkrellshoot_09-23-08_122520447.png[/img]](http://xs.to)

[[img]http://xs231.xs.to/xs231/08392/gkrellshoot_09-23-08_122106721.png[/img]](http://xs.to)

My panel is 1000 pixels long, so I defintely have enough room for more than one task panel (or whatever they're called).

---

### Post by jjgomera on 2008-09-23
> **Mark76 said:**
> I'm having a problem with Tint. As you can see from the screenshots below it tends to divide the first task panel into two rather than create a new task panel for each task.

[[img]http://xs231.xs.to/xs231/08392/gkrellshoot_09-23-08_122520447.png[/img]](http://xs.to)

[[img]http://xs231.xs.to/xs231/08392/gkrellshoot_09-23-08_122106721.png[/img]](http://xs.to)

My panel is 1000 pixels long, so I defintely have enough room for more than one task panel (or whatever they're called).
if you post your tintrc is easier look for the error ;)

---

### Post by Mark76 on 2008-09-23
Okay

> #---------------------------------------------
# TINT CONFIG FILE
#---------------------------------------------

#---------------------------------------------
# PANEL
#---------------------------------------------
panel_mode = multi_desktop
panel_monitor = 1
panel_position = bottom left
panel_size = 1000 30
panel_margin = 0 0
panel_padding = 3 3
font_shadow = 0

#---------------------------------------------
# PANEL BACKGROUND AND BORDER
#---------------------------------------------
panel_rounded = 0
panel_border_width = 0
panel_background_color = #000000 50
panel_border_color = #ffffff 10

#---------------------------------------------
# TASKS
#---------------------------------------------
task_text_centered = 1
task_width = 200
task_margin = 2
task_padding = 3
task_icon_size = 16
task_font = verdana bold 10
task_font_color = #ececec 50
task_active_font_color = #ffffff 80

#---------------------------------------------
# TASK BACKGROUND AND BORDER
#---------------------------------------------
task_rounded = 7
task_background_color = #d6d6d6 14
task_active_background_color = #d6d6d6 30
task_border_width = 1
task_border_color = #d1d1d1 0
task_active_border_color = #d1d1d1 14

#---------------------------------------------
# CLOCK
#---------------------------------------------
#time1_format = %H:%M
time1_font = sans bold 8
#time2_format = %A %d %B
#time2_font = sans 6
#clock_font_color = #ffffff 75

#---------------------------------------------
# MOUSE ACTION ON TASK
#---------------------------------------------
mouse_middle = none
mouse_right = close
mouse_scroll_up = toggle
mouse_scroll_down = iconify




---

### Post by dbbolton on 2008-09-23
@ Mark76:

It's not an error- it's the panel mode. Tint is putting windows from one workspace on one area of the bar. Try changing panel mode from "multi_desktop" to "normal".

---

### Post by Mark76 on 2008-09-23
Ah yes, that worked.

I think I got a bit confused because I have it so perfectly blended into the background that if I go to a desktop with no windows open it doesn't appear to be running there.

---

### Post by Mark76 on 2008-10-07
My newest tint and a question.

W(here)TF is the visibility rc? :confused:

> #---------------------------------------------
# TINT CONFIG FILE
#---------------------------------------------

#---------------------------------------------
# PANEL
#---------------------------------------------
panel_mode = normal
panel_monitor = 1
panel_position = bottom centre
panel_size = 1200 28
panel_margin = 0 0
panel_padding = 1 1
font_shadow = 0

#---------------------------------------------
# PANEL BACKGROUND AND BORDER
#---------------------------------------------
panel_rounded = 7
panel_border_width = 0
panel_background_color = #000000 0
panel_border_color = #ffffff 10

#---------------------------------------------
# TASKS
#---------------------------------------------
task_text_centered = 0
task_width = 0
task_margin = 2
task_padding = 3
task_icon_size = 24
task_font = urw_gothic_L bold 10
task_font_color = #FFFFFF 70
task_active_font_color = #FFFFFF 100

#---------------------------------------------
# TASK BACKGROUND AND BORDER
#---------------------------------------------
task_rounded = 7
task_background_color = #30825A 0
task_active_background_color = #30825A 5
task_border_width = 1
task_border_color = #d1d1d1 60
task_active_border_color = #d1d1d1 90

#---------------------------------------------
# CLOCK
#---------------------------------------------
time1_format = %I:%M.%S %p %Z
time1_font = urw_gothic_l bold 10
time2_format = %A %d %B %Y
time2_font = urw_gothic_l italic 8
clock_font_color = #ffffff 75

#---------------------------------------------
# MOUSE ACTION ON TASK
#---------------------------------------------
mouse_middle = maximise
mouse_right = close
mouse_scroll_up = toggle
mouse_scroll_down = iconify


---

### Post by dbbolton on 2008-10-08
> **Mark76 said:**
> My newest tint and a question.

W(here)TF is the visibility rc? :confused:
Check the first post.

---

### Post by Killeroid on 2009-02-04
Hey, letting you guys know tint development is active again and bugs are being squashed and new features being added.

For example, the "window title not updating" bug has been fixed. That and a couple of other bugs.

There is a repository containing the latest svn builds. You can find it here:  [https://launchpad.net/~killeroid/+archive/ppa](https://launchpad.net/~killeroid/+archive/ppa)

---

### Post by Wsh on 2009-02-06
Hi guys, im new in the forum, and sorry about my english, spanish is my native language ^^. 
I installed tint, and im using the Vorta theme. The only thing is that, the tasks don't flash if something is happening, like when i chat, and somebody talks to me, it keeps en the same color and i don't know if somebody talked to me or not. Is there any solution to this? Thank you

---

### Post by Visibility on 2010-08-13
You should now be able to launch tint as you would any other application (e.g. Alt+F2 -> tint). To run it at startup, you can add it to the ~/.xinitrc, or ~/.config/openbox/autostart.sh file, for example: 
xscreensaver -no-splash &
eval `cat $HOME/.fehbg` &
conky &
[visibility]("http://www.visibilityacceleration.com") &
***tint &***
exec openbox-session

---

### Post by kerry_s on 2010-08-13
using tint2 on netbook remix, set to blend in with the netbook launcher.

```
#---------------------------------------------
# TINT2 CONFIG FILE
#---------------------------------------------

#---------------------------------------------
# BACKGROUND AND BORDER
#---------------------------------------------
rounded = 4
border_width = 1
background_color = #000000 60
border_color = #ffffff 18

rounded = 4
border_width = 1
background_color = #000000 50
border_color = #ffffff 100

rounded = 4
border_width = 1
background_color = #000000 50
border_color = #ffffff 18

#---------------------------------------------
# PANEL
#---------------------------------------------
panel_monitor = all
#panel_position = center left vertical
panel_position = top center horizontal
panel_size = 100% 48
panel_margin = 0 0
panel_padding = 0 0 0
font_shadow = 0
panel_background_id = 0
wm_menu = 0

#---------------------------------------------
# TASKBAR
#---------------------------------------------
taskbar_mode = multi_desktop
#taskbar_mode = single_desktop
taskbar_padding = 4 4 4
taskbar_background_id = 1

#---------------------------------------------
# TASKS
#---------------------------------------------
task_icon = 1
task_text = 0
task_width = 48
task_centered = 1
task_padding = 4 4
task_font = sans 7
task_font_color = #ffffff 50
task_active_font_color = #ffffff 100
task_background_id = 3
task_active_background_id = 2

#---------------------------------------------
# SYSTRAYBAR
#---------------------------------------------
systray_padding = 0 0
systray_background_id = 1

#---------------------------------------------
# CLOCK
#---------------------------------------------
time1_format = %l:%M %P
time1_font = sans bold 12
time2_format = %a %d %b
time2_font = sans 10
clock_font_color = #ffffff 100
clock_padding = 10 0
clock_background_id = 1
clock_lclick_command = zenity --calendar
clock_rclick_command = exit-options

#---------------------------------------------
# MOUSE ACTION ON TASK
#---------------------------------------------
mouse_middle = close
mouse_right = none
mouse_scroll_up = none
mouse_scroll_down = none

```

system tray launchers are done with "gtrayicon".


```
#!/bin/bash

sleep 5

icon1="/usr/share/icons/Humanity/places/48/user-desktop.svg"

gtrayicon --tooltip="Show Desktop" --activate="wmctrl -k on" --deactivate="wmctrl -k off" --activate-icon="$icon1" --deactivate-icon="$icon1" &

sleep 1

icon2="/usr/share/icons/Humanity/actions/48/add.svg"
icon3="/usr/share/icons/Humanity/actions/48/remove.svg"
menu="/usr/local/etc/volume-menu"

gtrayicon --tooltip="Volume Up" --activate="amixer set Master 5+" --deactivate="amixer set Master 5+" --activate-icon="$icon2" --deactivate-icon="$icon2" --menu-file="$menu" &

sleep 1

gtrayicon --tooltip="Volume Down" --activate="amixer set Master 5-" --deactivate="amixer set Master 5-" --activate-icon="$icon3" --deactivate-icon="$icon3" --menu-file="$menu" &

exit 0

```

volume icons right click menu:
```

[main]
Mute All = amixer set Master toggle
Sound Preferences = gnome-volume-control

```

you can also use "apwal" set to the clock click for launchers. i already removed mine so no screen shots of that.

exit-options script:

```
#!/bin/bash

zenity --question --title="Exit Options" --text="Make your selection" --cancel-label="Shutdown" --ok-label="Log Out"

if [ $? = 0 ]; then
	gnome-session-save --logout-dialog
elif [ $? = 1 ]; then
	gnome-session-save --shutdown-dialog
fi
exit 0

```

---

### Post by kerry_s on 2010-08-14
here's what apwal looks like on the clock click. i put mine going down, but you can put it any way you want.

---

### Post by Slayer. on 2010-08-25
I'm having problems with mine. I keep getting errors when I try to add battery to the panel.

```

#---------------------------------------------
# TINT CONFIG FILE
#---------------------------------------------

#---------------------------------------------
# PANEL
#---------------------------------------------
panel_mode = multi_monitor
panel_monitor = 1
panel_position = bottom center
panel_size = 900 28
panel_margin = 15 0
panel_padding = 9 3
font_shadow = 0

#---------------------------------------------
# PANEL BACKGROUND AND BORDER
#---------------------------------------------
panel_rounded = 7
panel_border_width = 1
panel_background_color = #000000 60
panel_border_color = #ffffff 18

#---------------------------------------------
# TASKS
#---------------------------------------------
task_text_centered = 1
task_width = 120
task_margin = 2
task_padding = 6
task_icon_size = 13
task_font = sans 7
task_font_color = #ffffff 70
task_active_font_color = #ffffff 85

#---------------------------------------------
# TASK BACKGROUND AND BORDER
#---------------------------------------------
task_rounded = 5
task_background_color = #111111 30
task_active_background_color = #111111 50
task_border_width = 0
task_border_color = #ffffff 18
task_active_border_color = #ffffff 70

#---------------------------------------------
# BATTERY
#---------------------------------------------
battery = 1
battery_low_status = 10
battery_low_cmd = notify-send "battery low"
bat1_font = sans 8
bat2_font = sans 6
batter_font_color = #ffffff 75
battery_padding = 1 0
battery_background_id = 0

#---------------------------------------------
# CLOCK
#---------------------------------------------
time1_format = %H:%M:%S
time1_font = sans 7
time2_format = %A %d %B
time2_font = sans 5
clock_font_color = #666666 76

#---------------------------------------------
# MOUSE ACTION ON TASK
#---------------------------------------------
mouse_middle = none
mouse_right = close
mouse_scroll_up = toggle
mouse_scroll_down = iconify

```I get the following errors:

```

Invalid option: "battery", correct your config file
Invalid option: "battery_low_status", correct your config file
Invalid option: "battery_low_cmd", correct your config file
Invalid option: "bat1_font", correct your config file
Invalid option: "bat2_font", correct your config file
Invalid option: "batter_font_color", correct your config file
Invalid option: "battery_padding", correct your config file
Invalid option: "battery_background_id", correct your config file

```

---

### Post by kerry_s on 2010-08-25
it looks like battery is not supported in the version your using.
what version number is it?

[https://launchpad.net/~killeroid/+archive/ppa](https://launchpad.net/~killeroid/+archive/ppa)

---

