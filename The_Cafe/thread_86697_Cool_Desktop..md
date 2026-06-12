---
title: "Cool Desktop."
date: 2005-11-06
forum: The Cafe
---

### Post by nSTKo on 2005-11-06
Hi!
I Just Love This Desktop - [http://www.UbuntuForums.Org/gallery/showimage.php?i=1235&c=5](http://www.UbuntuForums.Org/gallery/showimage.php?i=1235&c=5)
Does Somebody Know What He Is Using? (gDesklets e.t.c.)

---

### Post by nSTKo on 2005-11-06
Damn, I'm Stupid :mad:
> Only had Ubuntu for about 2 weeks!
Much more freedom in linux for themeing than windows ever was!.

gDesklets-Calendar & FTB system info, d3a icons ,edge desktop theme, wallpaper found online, i added the ubuntu logo to it!

But Where Can I Get This Cool Wallpaper? :???:

---

### Post by endersshadow on 2005-11-06
You don't just want to copy somebody's desktop, do you!?!

Just kidding :)

Check out [http://art.gnome.org](http://art.gnome.org) or [http://art.ubuntu.com](http://art.ubuntu.com) for a huge assortment of wallpapers.

---

### Post by kverde on 2005-11-06
What is this "edge desktop theme"?  Is that what makes the "Applications Places System" appear in a tab-like interface?  I like that...

---

### Post by endersshadow on 2005-11-06
[QUOTE=kverde]What is this "edge desktop theme"?  Is that what makes the "Applications Places System" appear in a tab-like interface?  I like that...[/QUOTE]

I suppose, though I couldn't find an "Edge" theme at either art.gnome.org or art.ubuntu.com :?

I don't know if you'd like some more ideas, but [**this is my desktop**]("http://www.politicalcrossfire.com/temp/enderavsig/themes/Screenshot-3.png").  I use a custom wallpaper, I modified the GnomeBar applet quite a bit to fit my needs, I use the FTB desklet for the CPU, the Memory and the clock.  I use MilkMint as my Application theme, and Creme as my window theme from [http://art.gnome.org](http://art.gnome.org) (both of them).    I also use Dropline Nuovo as my icon set (from art.gnome.org).   This is just to give you some ideas and show how absolutely customized you can make your desktop :-D

---

### Post by Sutekh on 2005-11-06
[Edge Desktop Theme]("http://www.gnome-look.org/content/show.php?content=18631")

This makes the Menu Bar "tabbed" as you say (from gnome-look.org)

---

### Post by Dr. Nick on 2005-11-06
[QUOTE=nSTKo]Damn, I'm Stupid :mad:


But Where Can I Get This Cool Wallpaper? :???:[/QUOTE]

Not sure if you saw  but it is linked on one of the replies under the picture

---

### Post by pickarooney on 2005-11-06
I don't understand fancying up the desktop - it's visible to me for about 4 seconds every day. When do other people look at their wallpapers etc?

---

### Post by endersshadow on 2005-11-06
[QUOTE=pickarooney]I don't understand fancying up the desktop - it's visible to me for about 4 seconds every day. When do other people look at their wallpapers etc?[/QUOTE]

Yeah, I'm not too worried about my background, but I do love my GnomeBar and my FTB desklets at the bottom.  Plus, you see the Application, Icon, and Window themes all the time :-D

---

### Post by pickarooney on 2005-11-06
I tried gnomebar, it looks snazy, but doesn't work. When I click on the fooprint it asks permission to launch something. I tell it to always launch it and that's the last I ever see of it, i.e. no start menu ever pops up.

---

### Post by endersshadow on 2005-11-06
[QUOTE=pickarooney]I tried gnomebar, it looks snazy, but doesn't work. When I click on the fooprint it asks permission to launch something. I tell it to always launch it and that's the last I ever see of it, i.e. no start menu ever pops up.[/QUOTE]

Oh, yeah, I've editted mine almost beyond recognition.  You can't launch a menu from it in Breezy.  It uses the gnome-panel-control --main-menu command that's disabled in Breezy.  I just removed the foot, added more icons since the Notification Area doesn't work in Breezy as well.  Basically, I just adapted it to Breezy and used my system icons to it.  It works great and looks even better now :-D

---

### Post by pickarooney on 2005-11-06
got a screenshot? it sounds a bit useless if none of the bits work... although the start menu in gnome itself is really crap, so I barely use that either.

---

### Post by endersshadow on 2005-11-06
[QUOTE=pickarooney]got a screenshot? it sounds a bit useless if none of the bits work... although the start menu in gnome itself is really crap, so I barely use that either.[/QUOTE]


Sure, [here]("http://www.politicalcrossfire.com/temp/enderavsig/themes/Screenshot-3.png").

Then, I set it up so that little bar in the lower left hand corner is my panel that shoots out with just the Main Menu, and the lower right hand corner is my System Tray.

Here's my GnomeBar.display file, you can edit it how you wish...I did!

```
<?xml version="1.0" encoding="UTF-8"?>

<display id="win" anchor="ne"
         window-flags="sticky, below" desktop-borders=",0">

  <meta name="GnomeBar 2"
        version="2.22"
        preview="preview.png"
        author="Mark Dillavou and Sparrowhawk"
        description="A Replacement for the Gnome Panels"
	category="toolbar"/>

<!-- ********************************************************************** -->


<group id="border" y="0cm">

  <group id="slider"
         on-click="if (vc_behavior == 'click'): slide(self, SC_IN, SC_OUT)"
         on-doubleclick="if (vc_behavior == 'double'): slide(self, SC_IN, SC_OUT)"
         on-enter="if (vc_behavior == 'enter'): slide(self, SC_IN, SC_OUT)"
         on-leave="if (vc_behavior == 'enter'): slide(self, SC_IN, SC_OUT)">

    <group id="panel" width="560" height="60">

<!-- ********************************************************************** -->

      <!-- the background image -->
      <group id="bg" width="100%" height="100%" bg-uri=""/>

      <group id="info_group" y="0" width="100%">
<!-- **********************************************************************
     * This is the main area of the display.
     * Put your stuff in here:
     ********************************************************************** -->
	
	<!-- Left image with menu -->
	<!--<image id="menuBg" uri="gfx/menubg.png"
		x="0" y="0"
		width="667" height="60"/>-->
	<!-- Foot Icon -->
	<!--<image id="logo" uri="gfx/menu.png"
		x="4" y="3"
		image-width="1" image-height="1"
		on-enter="self.scale = 1"
		on-leave="self.scale = 1"/>-->
	
 	<!--<label id="timelabel" font="Sans 10" color="black" x = "135" y="1"/>
 	<label id="datelabel" font="Sans 10" color="black" x = "135" y="18"/>-->

	<!--embed oafiid="OAFIID:GNOME_ClockApplet"
		x="130" y="2"
		width="100" height="48"/-->	

	<!-- Taskbar -->
	<image id="taskBarBg" uri="gfx/middle.png"
		x="77" y="0"/>
	<image id="taskbarEndBg" uri="gfx/middle-end.png"
		x="539" y="0"/>

	<!-- Icons -->
	<image id="iconbarBg" uri="gfx/iconbar-middle.png"
		x="77" y="28"
		width="403"/>
	<image id="icon1"	x="80" y="30"
		width="20" height="20"
		uri="/home/eric/.icons/Nuovo/scalable/apps/file-manager.svg"
		on-enter="self.scale = 1.2"
		on-leave="self.scale = 1"
		on-release="self.scale = 1"/>
	<image id="icon2"	x="110" y="30"
		width="20" height="20"
		uri="/home/eric/.icons/Nuovo/scalable/apps/firefox-icon.svg"
		on-enter="self.scale = 1.2"
		on-leave="self.scale = 1"/>
	<image id="icon3"	x="140" y="30"
		width="20" height="20"
		uri="/home/eric/.icons/Nuovo/scalable/apps/thunderbird-default.svg"
		on-enter="self.scale = 1.2"
		on-leave="self.scale = 1"/>
	<image id="icon4"	x="170" y="30"
		width="20" height="20"
		uri="/home/eric/.icons/Nuovo/scalable/apps/gaim.svg"
		on-enter="self.scale = 1.2"
		on-leave="self.scale = 1"/>
	<image id="icon5"	x="200" y="30"
		width="20" height="20"
		uri="/home/eric/.icons/Nuovo/scalable/apps/gnome-terminal.svg"
		on-enter="self.scale = 1.2"
		on-leave="self.scale = 1"/>
	<image id="icon6"	x="230" y="30"
		width="20" height="20"
		uri="/home/eric/.icons/Nuovo/scalable/apps/gftp.svg"
		on-enter="self.scale = 1.2"
		on-leave="self.scale = 1"/>
	<image id="icon7"	x="260" y="30"
		width="20" height="20"
		uri="/home/eric/.icons/Nuovo/scalable/apps/gnome-gimp.svg"
		on-enter="self.scale = 1.2"
		on-leave="self.scale = 1"/>
	<image id="icon8"	x="290" y="30"
		width="20" height="20"
		uri="/home/eric/.icons/Nuovo/scalable/apps/inkscape.svg"
		on-enter="self.scale = 1.2"
		on-leave="self.scale = 1"/>
	<image id="icon9"	x="320" y="30"
		width="20" height="20"
		uri="/home/eric/.icons/Nuovo/scalable/apps/rhythmbox.svg"
		on-enter="self.scale = 1.2"
		on-leave="self.scale = 1"/>
	<image id="icon10"	x="350" y="30"
		width="20" height="20"
		uri="/home/eric/.icons/Nuovo/scalable/apps/gnome-devel.svg"
		on-enter="self.scale = 1.2"
		on-leave="self.scale = 1"/>
	<image id="icon11"	x="380" y="30"
		width="20" height="20"
		uri="/usr/share/icons/hicolor/48x48/apps/ooo-writer.png"
		on-enter="self.scale = 1.2"
		on-leave="self.scale = 1"/>
	<image id="icon12"	x="410" y="30"
		width="20" height="20"
		uri="/usr/share/icons/hicolor/48x48/apps/ooo-calc.png"
		on-enter="self.scale = 1.2"
		on-leave="self.scale = 1"/>
	<image id="icon13"	x="440" y="30"
		width="20" height="20"
		uri="/usr/share/icons/hicolor/48x48/apps/ooo-impress.png"
		on-enter="self.scale = 1.2"
		on-leave="self.scale = 1"/>
	<!-- Bonobo wickets -->
	<group id="bonobo" height="100%" width="100%">

	<!--<embed id="menu" oafiid="OAFIID:GNOME_Panel_Applet" height="50" width="50" x="4" y="3" />-->
        <embed id="workspace" oafiid="OAFIID:GNOME_PagerApplet!prefs_key=/schemas/apps/workspace_switcher_applet/prefs;size=50;orient=PANEL_ORIENTATION_BOTTOM" 
		x="3" y="3"
		width="72" height="48"/>
	<!--embed id="taskbar" oafiid="OAFIID:GNOME_GWeatherApplet"
		height="24" width="48"
		x="135" y="31"/-->
	<embed id="taskbar" oafiid="OAFIID:GNOME_WindowListApplet"
		height="24" width="460"
		x="82" y="2"/>
	<!--<embed id="notification" oafiid="OAFIID:GNOME_NotificationAreaApplet"
		x="434" y="29"
		height="24" width="110"/>-->
	<embed oafiid="OAFIID:GNOME_Panel_TrashApplet"
		id="trash"
		x="480" y="29"
		height="24" width="20"/>
	<embed oafiid="OAFIID:GNOME_MixerApplet"
		id="volume"
		x="500" y="29"
		height="24" width="20"/>

	</group> 

    <script><![CDATA[

    tb_border = 0
    
    def border_chg(key, value):
        Dsp.win.desktop_borders = [Unit(),Unit(value,PX)]
    

    Dsp.icon1.on_click = "launch('nautilus')"
    Dsp.icon2.on_click = "launch('firefox')"  
    Dsp.icon3.on_click = "launch('mozilla-thunderbird')"
    Dsp.icon4.on_click = "launch('gaim')"
    Dsp.icon5.on_click = "launch('gnome-terminal')"
    Dsp.icon6.on_click = "launch('gftp')"
    Dsp.icon7.on_click = "launch('gimp')"
    Dsp.icon8.on_click = "launch('inkscape')"
    Dsp.icon9.on_click = "launch('rhythmbox')"
    Dsp.icon10.on_click = "launch('tkcvs')"
    Dsp.icon11.on_click = "launch('ooffice2 -writer')"
    Dsp.icon12.on_click = "launch('ooffice2 -calc')"
    Dsp.icon13.on_click = "launch('ooffice2 -impress')"

  ]]></script>

	<!--<image id="iconbarEndBg" uri="gfx/middle-end.png"
		x="400" y="28"/>-->

	<!-- Notification Area -->
	<!--<image id="systrayBg" uri="gfx/iconbar-middle.png"
		x="430" y="28"/>-->
	<image id="systrayEndBg" uri="gfx/middle-end.png"
		x="520" y="28"/>

<!-- ********************************************************************** -->

      </group>

    </group>

  </group>

</group>


  <!-- the preferences dialog -->
  <prefs callback="vc_prefs_cb">

    <page label="GnomeBar">

      <enum label="Stay on top:" bind="vc_on_top">
        <item label="Never" value="never"/>
        <item label="Always" value="always"/>
        <item label="When slid in" value="whenin"/>
        <item label="When slid out" value="whenout"/>
      </enum>
      <title label="Sliding"/>
      <enum label="Orientation:" bind="vc_side"
            help="The orientation of the display.">
        <item label="Up" value="up"/>
        <item label="Down" value="down"/>
      </enum>
      <integer label="Delay:" bind="vc_slide_timer"/>
      <enum label="Behavior:" bind="vc_behavior">
        <item label="Slide on mouse click" value="click"/>
        <item label="Slide on double click" value="double"/>
        <item label="Never slide" value="never"/>
      </enum>

      <title label="Desktop Border" help="Set to -60 to cover entire desklet.
Set to -45 to cover up to slid-in part."/>
      <integer label="Vertical Border Placement:" 
        min="-500" 
        bind="tb_border" callback="border_chg" help="Set to -60 to cover entire desklet.
Set to -45 to cover up to slid-in part."/>

      <title label="Background"/>
      <uri label="Background image:" bind="Dsp.bg.bg_uri"/>
      <boolean label="Show background" bind="Dsp.bg.visible"/>
    </page>

  <page label="General">

    <boolean label="Show Trash" bind="Dsp.trash.visible"/>
    <boolean label="Show Volume" bind="Dsp.volume.visible"/>

  </page>

  <page label="Applications">

    <string label="Application 1:" bind="Dsp.icon1.on_click"/>
    <string label="Application 2:" bind="Dsp.icon2.on_click"/>
    <string label="Application 3:" bind="Dsp.icon3.on_click"/>
    <string label="Application 4:" bind="Dsp.icon4.on_click"/>
    <string label="Application 5:" bind="Dsp.icon5.on_click"/>
    <string label="Application 6:" bind="Dsp.icon6.on_click"/>
    <string label="Application 7:" bind="Dsp.icon7.on_click"/>
    <string label="Application 8:" bind="Dsp.icon8.on_click"/>
    <string label="Application 9:" bind="Dsp.icon9.on_click"/>
    <string label="Application 10:" bind="Dsp.icon10.on_click"/>
    <string label="Application 11:" bind="Dsp.icon11.on_click"/>
    <string label="Application 12:" bind="Dsp.icon12.on_click"/>
    <string label="Application 13:" bind="Dsp.icon13.on_click"/>

  </page>

  <page label="Icons">

  <title label="Program Icons:"/>

    <uri label="Icon 1 Image:" bind="Dsp.icon1.uri"/>
    <uri label="Icon 2 Image:" bind="Dsp.icon2.uri"/>
    <uri label="Icon 3 Image:" bind="Dsp.icon3.uri"/>
    <uri label="Icon 4 Image:" bind="Dsp.icon4.uri"/>
    <uri label="Icon 5 Image:" bind="Dsp.icon5.uri"/>
    <uri label="Icon 6 Image:" bind="Dsp.icon6.uri"/>
    <uri label="Icon 7 Image:" bind="Dsp.icon7.uri"/>
    <uri label="Icon 8 Image:" bind="Dsp.icon8.uri"/>
    <uri label="Icon 9 Image:" bind="Dsp.icon9.uri"/>
    <uri label="Icon 10 Image:" bind="Dsp.icon10.uri"/>
    <uri label="Icon 11 Image:" bind="Dsp.icon11.uri"/>
    <uri label="Icon 12 Image:" bind="Dsp.icon12.uri"/>
    <uri label="Icon 13 Image:" bind="Dsp.icon13.uri"/>

  </page>


<!-- ********************************************************************** -->

  </prefs>


  <!-- this loads the VerticalCandy magic -->
  <script uri="candy.script"/>


</display>
```

Note that I took my icons from my theme (Nuovo) :-D

---

### Post by Roobert on 2005-11-06
[QUOTE=endersshadow]Sure, [here]("http://www.politicalcrossfire.com/temp/enderavsig/themes/Screenshot-3.png").[/QUOTE]
[snip]

Hey man, I get 500'd when I try to view your screenshot. Dead link or something.

~ Roobert.

---

### Post by endersshadow on 2005-11-06
Huh.  Okay, let me see what I can do :)

---

### Post by endersshadow on 2005-11-06
Here you go!!

[http://ubuntuforums.org/gallery/showimage.php?i=1259&original=1&c=2](http://ubuntuforums.org/gallery/showimage.php?i=1259&original=1&c=2)

---

