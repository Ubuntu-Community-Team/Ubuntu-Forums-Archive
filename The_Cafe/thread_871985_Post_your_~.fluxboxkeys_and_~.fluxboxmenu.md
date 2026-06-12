---
title: "Post your ~/.fluxbox/keys and ~/.fluxbox/menu"
date: 2008-07-27
forum: The Cafe
---

### Post by billgoldberg on 2008-07-27
I'm looking for ideas and I thought why not start a "Post your ~/.fluxbox/keys and ~/.fluxbox/menu" similar to the conkyrc thread.

I'll start.

***keys***

```

OnDesktop Mouse1 :HideMenus
OnDesktop Mouse2 :WorkspaceMenu
OnDesktop Mouse3 :RootMenu
OnDesktop Mouse4 :NextWorkspace
OnDesktop Mouse5 :PrevWorkspace
Mouse8 :NextWorkspace # top button side mouse -> next workspace
Mouse9 :PrevWorkspace # bottom button side mouse -> previous workspace

Mod1 Tab :NextWindow 
Mod1 Shift Tab :PrevWindow

# Launch programs

F12 :ExecCommand xterm # opens a cli client
F11 :ExecCommand firefox # opens the firefox webbrowser client
F10 :ExecCommand pcmanfm # opens the thunar file manager
F9 :ExecCommand mousepad # opens the mousepad text editor
F8 :ExecCommand sonata # opens the sonata music player
Mod1 F2 :Exec fbrun # opens a "run" dialog window, similar to "alt+f2" in gnome

# Media keys

#	System Volume
F2 :Exec amixer sset Master,0 5%- # lower volume by 5%
F3 :Exec amixer sset Master,0 5%+ # raise volume by 5%
F4 :Exec amixer sset Master,0 toggle # mute volume

#	MPC (music player command for music player deamon)
F6 :Exec mpc next # plays next song in playlist
F5 :Exec mpc prev # plays previous songs in playlist
F7 :Exec mpc toggle # pauses or play the song

# Visual

F1 :ToggleDecor # removes or adds window decoration

# screenshot:

Control F12 :Exec scrot -e 'mv $f ~/Desktop' # takes a screenshot of the screen


```

***menu***

```
[begin] (Fluxbox)
[exec] (Xterm) {xterm}
[separator]
[submenu] (Tools)      
      [exec] (File Roller) {file-roller}     
      [exec] (Feh Image Viewer) {feh}
      [exec] (Synaptic) {gksu synaptic}
[end]
[submenu] (Internet)
      [exec] (Firefox) {firefox}
      [exec] (Emesene) {emesene}
      [exec] (Transmission) {transmission}
      [exec] (Xchat) {xchat}
      [exec] (Frostwire) {frostwire}
      [exec] (Nicotine Plus) {nicotine}
[end]
[submenu] (Editors)
      [exec] (Mousepad) {mousepad}
      [exec] (Abiword) {abiword}
      [exec] (Gnumeric) {gnumeric}
[end]
[submenu] (Multimedia)
      [exec] (VLC Media Player) {vlc}
      [exec] (Sonata) {sonata}
      [exec] (Brasero) {brasero}
      [exec] (Audio Tag Tool) {tagtool}
      [exec] (Avidemux) {avidemux}
[end]
[submenu] (Graphics)
      [exec] (Gimp) {gimp}
      [exec] (Xpdf) {xpdf}
[end]
[separator]
[submenu] (Fluxbox Menu)
      [config] (Configure)
[submenu] (Styles) {Choose a Style...}
      [stylesdir] (/usr/X11R6/share/fluxbox/styles)
[end]
      [workspaces] (Workspace List)
[submenu] (Tools)
      [exec] (Window name) {xprop WM_CLASS|cut -d \" -f 2|xmessage -file - -center}
[end]
      [commanddialog] (Fluxbox Command)
      [reconfig] (Reload config)
      [restart] (Restart Fluxbox)
      [exec] (About) {fluxbox -v 2>/dev/null | head -n1 | xmessage -file - -center}
      [exit] (Exit Fluxbox)
      [separator]
      [exec] (Reboot) {shutdown -r now}
      [exec] (Shutdown) {shutdown -p now}
[end]
[end]


```
[URL="http://linuxowns.files.wordpress.com/2008/07/flux123.png"]
[IMG]http://linuxowns.files.wordpress.com/2008/07/flux123.png?w=300&h=240[/IMG][/URL]
*(click for full resolution)*

Please include a screen shot showing the menu.

---

### Post by Diabolis on 2008-07-27
Keys:
```
!mouse actions added by fluxbox-update_configs
OnDesktop Mouse1 :hideMenus
OnDesktop Mouse2 :workspaceMenu
OnDesktop Mouse3 :rootMenu
OnDesktop Mouse4 :nextWorkspace
OnDesktop Mouse5 :prevWorkspace

!mouse actions added by fluxbox-update_configs
OnDesktop Mouse1 :hideMenus
OnDesktop Mouse2 :workspaceMenu
OnDesktop Mouse3 :rootMenu
OnDesktop Mouse4 :nextWorkspace
OnDesktop Mouse5 :prevWorkspace

#programas
Control Mod1 t	:ExecCommand gnome-terminal
Control Mod1 f	:ExecCommand firefox
Control Mod1 n	:ExecCommand nautilus --no-desktop
Control Mod1 h	:ExecCommand thunar
Control Mod1 j	:ExecCommand firefox JAVA/doc/jdk-6-doc/api/index.html
Control Mod1 e	:ExecCommand JAVA/bin/eclipse/./eclipse
Control Mod1 r	:ExecCommand rhythmbox
Control Mod1 i	:ExecCommand emesene
Control Mod1 x	:ExecCommand xchat
Control Mod1 b	:ExecCommand netbeans-6.1/bin/netbeans
**Control Mod1 Return	:ExecCommand ./misDocumentos/bin/dmenu.sh**

#acciones
Mod1 Tab 		:NextWindow
Mod1 masculine	:PrevWindow
Mod1 F1			:Workspace 1
Mod1 F2 		:Workspace 2
Mod1 F3 		:Workspace 3
Control Mod1 d	:ShowDesktop
Control Mod1 s	:Deiconify All OriginQuiet
None 176		:ExecCommand amixer set Master 1%+
None 174		:ExecCommand amixer set Master 1%-
None 160		:ExecCommand amixer set Master toggle
Mod1 Print 		:Exec import -window root ~/Desktop/screenshot.jpg
Mod1 F4			:Close
Super_L			:RootMenu

**#Windows**
Control Mod1 m		:MaximizeWindow
Control Shift 100	:ResizeHorizontal -14
Control Shift 102	:ResizeHorizontal +14
Control Shift 98	:ResizeVertical -14
Control Shift 104	:ResizeVertical +14		
Control Mod1 102	:MoveLeft -14
Control Mod1 100	:MoveRight -14
Control Mod1 104	:MoveUp -14
Control Mod1 98		:MoveDown -14

```

I don't use the fluxbox menu, instead I use [dmenu]("http://www.suckless.org/programs/dmenu.html")

I started a dmenu thread, but I just realized that is not that much configurable... hopefully that'll change.

[http://ubuntuforums.org/showthread.php?t=869146](http://ubuntuforums.org/showthread.php?t=869146)

Why do you have a key binding that adds/removes window decoration?

---

### Post by RiceMonster on 2008-07-27
What about Openbox? Here's my menu.xml:

```
<?xml version="1.0" encoding="UTF-8"?>

<openbox_menu xmlns="http://openbox.org/3.4/menu" label="ArchBox">

<menu id="root-menu" label="Openbox">

	<separator label="Archbox" />

	<item label="Terminal">
		<action name="Execute"><execute>terminal</execute></action>
	</item>
	<item label="Firefox">
		<action name="Execute"><execute>firefox</execute></action>
	</item>
	<item label="Emesene">
		<action name="Execute"><execute>emesene</execute></action>
	</item>
	<item label="Amarok">
		<action name="Execute"><execute>amarok</execute></action>
	</item>

	<separator label="Menus" />

	<menu id="client-list-menu" />

	<!-- APPS -->

	<menu id="apps" label="Apps">
	
	<!-- EDITORS -->	
	<menu id="edit" label="Editors">
		<item label="gVIM">
			<action name="Execute"><execute>gvim</execute></action>
		</item>
		<item label="SciTE">
			<action name="Execute"><execute>scite</execute></action>
		</item>
	</menu>

	<!-- GAMES -->
	<menu id="games" label="Games"> 
		<item label="DOSBox">
			<action name="Execute"><execute>dosbox</execute></action>
		</item>
		<item label="Extreme TuxRacer">
			<action name="Execute"><execute>etracer</execute></action>
		</item>
		<item label="Neverball">
			<action name="Execute"><execute>neverball</execute></action>
		</item>
		<item label="Frozen Bubble">
			<action name="Execute"><execute>frozen-bubble</execute></action>
		</item>
	</menu>

	<!-- INTENET -->

	<menu id="net" label="Internet">
		<item label="Deluge">
			<action name="Execute"><execute>deluge</execute></action>
		</item>
		<item label="Emesene">
			<action name="Execute"><execute>emesene</execute></action>
		</item>
		<item label="Firefox">
			<action name="Execute"><execute>firefox</execute></action>
		</item>
		<item label="Google Earth">
			<action name="Execute"><execute>googleearth</execute></action>
		</item>
    <item label="Nicotine+">
      <action name="Execute"><execute>nicotine</execute></action>
		</item>
	</menu>

	<!-- SOUND & VIDEO -->
	<menu id="s+v" label="Sound/Vid">
		<item label="Amarok">
			<action name="Execute"><execute>amarok</execute></action>
		</item>
		<item label="Audacious">
			<action name="Execute"><execute>audacious</execute></action>
		</item>
		<item label="Asunder">
			<action name="Execute"><execute>asunder</execute></action>
		</item>
		<item label="Exaile">
			<action name="Execute"><execute>exaile</execute></action>
		</item>
		<item label="Methlab">
			<action name="Execute"><execute>~/methlab/methlab</execute></action>
		</item>
		<item label="Mplayer">
			<action name="Execute"><execute>gnome-mplayer</execute></action>
		</item>
		<item label="K3b">
			<action name="Execute"><execute>k3b</execute></action>
		</item>
		<item label="TuxGuitar">
			<action name="Execute"><execute>tuxguitar</execute></action>
		</item>
	</menu>

	<separator />

  	<item label="The GIMP">
    	<action name="Execute"><execute>gimp</execute></action>
    </item>
  </menu>

  <menu id="places" label="Places">
    <item label="Home">
      <action name="Execute"><execute>thunar</execute></action>
    </item>
    <item label="Documents">
      <action name="Execute"><execute>thunar ~/Documents</execute></action>
    </item>
    <item label="Downloads">
      <action name="Execute"><execute>thunar ~/Downloads</execute></action>
    </item>
    <item label="Music">
      <action name="Execute"><execute>thunar ~/Music</execute></action>
    </item>
    <item label="Pictures">
      <action name="Execute"><execute>thunar ~/Pictures</execute></action>
    </item>
    <separator />
    <item label="External HD">
      <action name="Execute"><execute>thunar /media/ExternalHD</execute></action>
    </item>
	</menu>

	<separator />

  <menu id="admin" label="Admin">
    <item label="Lxappearance">
      <action name="Execute"><execute>lxappearance</execute></action>
    </item>
    <item label="Nitrogen">
      <action name="Execute"><execute>nitrogen ~/Pictures/Walls --sort="alpha"</execute></action>
		</item>
    <item label="VirtualBox">
      <action name="Execute"><execute>virtualbox</execute></action>
    </item>
    <item label="Xscreensaver">
      <action name="Execute"><execute>xscreensaver-demo</execute></action>
    </item>
  </menu>

	<!--<separator />-->

  <menu id="ob" label="Openbox">
    <item label="Obconf">
      <action name="Execute"><execute>obconf</execute></action>
    </item>
    <item label="Reconfigure">
      <action name="Reconfigure" />
    </item>
    <item label="Restart">
      <action name="Restart" />
    </item>
  </menu>

  <separator />

  <menu id="leave" label="Leave">
    <item label="Hibernate">
      <action name="Execute"><execute>sudo pm-hibernate</execute></action>
    </item>
    <item label="Suspend">
      <action name="Execute"><execute>sudo pm-suspend</execute></action>
    </item>
    <item label="Shutdown">
      <action name="Execute"><execute>sudo shutdown -h now</execute></action>
    </item>
    <item label="Reboot">
      <action name="Execute"><execute>sudo shutdown -r now</execute></action>
    </item>
  </menu>

</menu>
</openbox_menu>
```

---

### Post by billgoldberg on 2008-07-27
> Why do you have a key binding that adds/removes window decoration?

Don't laugh, but I find that watching movies without window decoration and menu's (it's like the video is embedded in the wallpaper) looks better.

---

### Post by Diabolis on 2008-07-27
> **billgoldberg said:**
> Don't laugh, but I find that watching movies without window decoration and menu's (it's like the video is embedded in the wallpaper) looks better.

Hehe , thats a good idea. I'll use it, someday, I don't watch a lot of movies in my pc...

Here is the screenshot:
[[IMG]http://farm4.static.flickr.com/3223/2707637070_f893a83424_m.jpg[/IMG]]("http://www.flickr.com/photos/silvag/2707637070/")

---

### Post by billgoldberg on 2008-07-27
Your desktop looks great.

---

### Post by billgoldberg on 2008-07-30
Adjusted my keys file a bit.

---

### Post by cl0ckwork on 2008-07-31
heres mine, nothing too fancy

menu file
```
# Generated by fluxbox-generate_menu
#
# If you read this it means you want to edit this file manually, so here
# are some useful tips:
#
# - You can add your own menu-entries to ~/.fluxbox/usermenu
#
# - If you miss apps please let me know and I will add them for the next
#   release.
#
# - The -r option prevents removing of empty menu entries and lines which
#   makes things much more readable.
#
# - To prevent any other app from overwriting your menu
#   you can change the menu name in .fluxbox/init to:
#     session.menuFile: /home/you/.fluxbox/my-menu
[begin] (Fluxbox)
      [exec] (xterm) {xterm}
      [exec] (Thunar) {thunar}
[submenu] (Terminals)
      [exec] (xterm) {xterm} 
      [exec] (gnome-terminal) {gnome-terminal} 
      [exec] (konsole) {konsole}
[end]
[submenu] (Net)
[submenu] (Browsers)
      [exec] (firefox) {firefox} 
      [exec] (flock) {/usr/share/flock/flock}
[end]
[submenu] (IM)
      [exec] (pidgin) {pidgin} 
[end]
[submenu] (ftp)
      [exec] (ncftp) {xterm -e ncftp} 
      [exec] (kftpgrabber) {kftpgrabber}
[end]
[submenu] (p2p)
      [exec] (deluge) {deluge}
      [exec] (amule) {amule}
      [exec] (ktorrent) {ktorrent}
      [exec] (kmldonkey) {kmldonkey}
[end]
      [exec] (skype) {skype} 
[end]
[submenu] (Editors)
[submenu] (Fluxbox edit)
      [exec] (menu) {gedit /home/clockwork/.fluxbox/menu}
      [exec] (init) {gedit /home/clockwork/.fluxbox/init}
      [exec] (keys) {gedit /home/clockwork/.fluxbox/keys}
      [exec] (startup) {gedit /home/clockwork/.fluxbox/startup}
      [exec] (overlay) {gedit /home/clockwork/.fluxbox/overlay}
      [exec] (slitlist) {gedit /home/clockwork/.fluxbox/slitlist}
      [exec] (wallpaper) {gedit /home/clockwork/.fluxbox/lastwallpaper}
[end]
      [exec] (gedit) {gedit} 
      [exec] (mouspad) {mousepad}
      [exec] (nano) {xterm -e nano} 
[end]
[submenu] (Package)
      [exec] (Spritz) {spritz} 
[end]
[submenu] (File utils)
      [exec] (nautilus) {nautilus --no-desktop --browser} 
      [exec] (thunar) {thunar}
[end]
[submenu] (Multimedia)
[submenu] (Graphics)
      [exec] (gimp) {gimp} 
      [exec] (gimp-2.2) {gimp-2.2} 
      [exec] (xscreensaver-demo) {xscreensaver-demo} 
[end]
[submenu] (Audio)
      [exec] (Amarok) {amarok}
      [exec] (xmms) {xmms} 
      [exec] (beep-media-player) {beep-media-player} 
      [exec] (alsamixer) {xterm -e alsamixer} 
[end]
[submenu] (Video)
      [exec] (totem) {totem}
      [exec] (xine) {xine} 
      [exec] (aviplay) {aviplay} 
      [exec] (gtv) {gtv} 
      [exec] (gmplayer) {gmplayer} 
[end]
[submenu] (X-utils)
      [exec] (xclock) {xclock} 
[end]
[end]
[submenu] (Office)
      [exec] (xclock) {xclock} 
      [exec] (abiword) {abiword} 
      [exec] (kword) {kword} 
      [exec] (dia) {dia}
[end]
[submenu] (Games)
      [exec] (sauerbraten) {sauerbraten}
      [exec] (fortune) {fortune}
      [exec] (wesnoth) {wesnoth}
[submenu] (kde)
      [exec] (atlantik) {atlantic}
      [exec] (kasteriods) {kasteroids}
      [exec] (kblackbox) {kblackbox}
      [exec] (kbounce) {kbounce}
      [exec] (kfourinline) {kfourinline}
      [exec] (kgoldrunner) {kgoldrunner}
      [exec] (khangman) {khangman}
      [exec] (kjumpingcube) {kjumpingcube}
      [exec] (kmines) {kmines}
      [exec] (knetwalk) {knetwalk}
      [exec] (kolf) {kolf}
      [exec] (konquest) {konquest}
      [exec] (kpoker) {kpoker}
      [exec] (kshisen) {kshisen}
      [exec] (ksnake) {ksnake}
      [exec] (ktron) {ktron}
      [exec] (ktuberling) {ktuberling}
      [exec] (kwin4) {kwin4}
[end]
[submenu] (gnome)
      [exec] (gnibbles) {gnibbles} 
      [exec] (gnobots2) {gnobots2} 
      [exec] (gataxx) {gataxx} 
      [exec] (glines) {glines} 
      [exec] (gnect) {gnect} 
      [exec] (mahjongg) {mahjongg} 
      [exec] (gnomine) {gnomine} 
      [exec] (gnome-stones) {gnome-stones} 
      [exec] (gnometris) {gnometris} 
      [exec] (gnotravex) {gnotravex} 
      [exec] (gnotski) {gnotski} 
      [exec] (iagno) {iagno}
      [exec] (gtali) {gtali} 
      [exec] (same-gnome) {same-gnome}
      [exec] (sol) {sol} 
      [exec] (blackjack) {blackjack} 
[end]
[end]
[submenu] (fluxbox menu)
      [config] (Configure) 
[submenu] (Styles)
      [include] (/usr/share/fluxbox/menu.d/styles/) 
[end]
      [workspaces] (Workspace List) 
[submenu] (Tools)
      [exec] (Screenshot - JPG) {import screenshot.jpg && display -resize 50% screenshot.jpg} 
      [exec] (Screenshot - PNG) {import screenshot.png && display -resize 50% screenshot.png} 
[end]
[submenu] (Window)
      [restart] (gnome) {gnome-session} 
[end]
      [exec] (Lock screen) {xscreensaver-command -lock} 
      [commanddialog] (Fluxbox Command) 
      [reconfig] (Reload config) 
      [restart] (Restart) 
      [exec] (About) {(fluxbox -v; fluxbox -info | sed 1d) 2> /dev/null | xmessage -file - -center} 
      [separator]
      [exit] (Exit)
      [separator] 
      [exec] (Reboot) {shutdown -r now}
      [exec] (Shutdown) {shutdown -p now}

[end]
[end]
```


keys file
```
!mouse actions added by fluxbox-update_configs
OnDesktop Mouse1 :hideMenus
OnDesktop Mouse2 :workspaceMenu
OnDesktop Mouse3 :rootMenu
OnDesktop Mouse6 :nextWorkspace
OnDesktop Mouse7 :prevWorkspace

Mod1 Tab :NextWindow
Mod1 Shift Tab :PrevWindow
Mod1 F1 :Workspace 1
Mod1 F2 :Workspace 2
Mod1 F3 :Workspace 3
Mod1 F4 :Workspace 4
Mod1 F5 :Workspace 5
Mod1 F6 :Workspace 6
Mod1 F7 :Workspace 7
Mod1 F8 :Workspace 8
Mod1 F9 :Workspace 9
Mod1 F10 :Workspace 10
Mod1 F11 :Workspace 11
Mod1 F12 :Workspace 12

Mod4 1 :exec firefox #mod4=win key
Mod4 2 :exec pidgin
Mod4 3 :exec amarok

#Volume.  Will lower or raise volume by 5%.  The third key binding will toggle mute.
None XF86AudioLowerVolume       :Exec amixer sset Master,0 5%-
None XF86AudioRaiseVolume       :Exec amixer sset Master,0 5%+
None XF86AudioMute              :Exec amixer sset Master,0 toggle

#Amarok.  '-f' will forward one track. '-r' will reverse one track. '--pause' will toggle playback pause
#XMMS.	  'xmms -f' will forward one track. 'xmms -r' will reverse one track. 'xmms -t' will toggle pause/play. 'xmms -s' will stop.    
None XF86AudioNext              :Exec amarok -f
None XF86AudioPrev              :Exec amarok -r
None XF86AudioPlay              :Exec amarok --play-pause

#The 'Menu' key is located to the left of my right Ctrl key on my keyboard and has a picture of a drop down menu on it.

None Menu			 		  :CustomMenu ~/.fluxbox/customMenus/Amarok
```

---

### Post by Diabolis on 2008-07-31
I like your wallpaper, it looks good.

---

### Post by cl0ckwork on 2008-07-31
> **Diabolis said:**
> I like your wallpaper, it looks good.

haha thanks. it take forever for me to find a wallpaper i like cuz i only have about 1000 to choose from on my laptop.

so i usually change it every week ^_^

---

### Post by init1 on 2008-07-31
I've never edited my fluxbox config file; I've never had a reason to. All I do is make the panel longer, and change the theme to Twice.

---

### Post by cknight on 2008-09-04
Heh, you asked for it!  I certainly don't always remember most of these, but I had great fun creating this for my fluxbox keys how-to.  I don't really use the menu much.  Mostly launch things via fbrun (that's "Mod4 r" :))
```
#
#   This keys file is licensed public domain.  There is no support or warranty for it.  This file should be considered untested and
#   to be used at your own risk.
#
#
#	Created November 2007 by Chris Knight
#
###########################################################################################################################################
#
#  Lines beginning with '#' are comments and ignored by fluxbox.  Alternatively the '!' comment delimiter may be used.
#
#  Use 'xev' on the command line to identify the name (or keycode) of the key.
#  Use 'xmodmap -m' to identify the various modifiers on your keyboard
#
#  The following modifiers are used in this key file:
#		 Mod1    == Alt
#		 Mod4    == Windows key
#		 Control == Ctrl
#		 shift   == Shift
#
#  Some notes on the keys use:
#		 1) Your milage may vary.  **** These keys are for my keyboard. ****  While I've tried to avoid special keys, 
#		    your keyboard may be different.		 
#  		 2) KP_4 refers to "4"/Left arrow on the keypad.  If your keyboard does not have a keypad, you will likely have to remap these keys.
#		 3) Several commands may require you to pull in additional programs (e.g. gmessage) or create custom Menu files to work properly
#
#  The following commands are not implemented in this keys file:
#		 1) SetWorkspaceName		# Changes the name of the current workspace
#		 2) SetHead <int>               # Sets the default head for a window --> xinerama
#		 3) NextGroup <by-number>	#????
#		 4) NextGroup <by-number>	#????
#		 5) RightWorkspace <by-number>  # Switches "number" workspaces to the right
#		 6) LeftWorkspace <by-number>   # Switches "number" workspaces to the left
#		 7) NextWindow <bitmask>        # Allows fine tuned control of window switching.  See the fluxbox wiki or man page for further info
#		 8) PrevWindow <bitmask>        # Allows fine tuned control of window switching.  See the fluxbox wiki or man page for further info
#		 9) HideMenu 			# ????
#
#  Commands with 'osdctl' in them require the utility osdsh to be installed, and for osdsh to be running.
#
###########################################################################################################################################


#Control-Escape will turn off all key bindings in this file, until Control-Escape is pressed again.  Note the one exception for this is the root menu.
Control Escape		               	:MacroCmd {Exec osdctl -s "Keys off,"} {keyMode KeysOff Control Escape} 
KeysOff: Control Mod4 Mod1 Mouse3 	:rootMenu

###########################################################################################################################################
#		 		 		 Desktop Actions
# 
# Controlled by mouse clicks/wheel on desktop
#
# OnDesktop means a mouse press on the desktop
# Mouse 1=left click, 2=middle click, 3=right click, 4=mouse wheel down, 5=mouse wheel up
###########################################################################################################################################

OnDesktop Mouse1 :hideMenus
OnDesktop Mouse2 :workspaceMenu
OnDesktop Mouse3 :rootMenu
#OnDesktop Mouse4 :nextWorkspace
#OnDesktop Mouse5 :prevWorkspace

###########################################################################################################################################
#		 		 		 Fluxbox Window Manager commands
#
# Controlled mostly by Mod4 and Shift keys
#
# Restart takes optional <argument> of which window manager to restart to (default is fluxbox, of course)
# Reload style allows you to make changes to the current style and then quickly reload it.
###########################################################################################################################################

Mod4 shift r		:Restart 
Mod4 shift q		:Quit
Mod4 shift e		:Exit
Mod4 shift Escape	:MacroCmd {Exec osdctl -s "Reconfiguring,"} {Reconfigure}
Mod4 shift 1		:MacroCmd {SetStyle /usr/local/share/fluxbox/styles/bora_black} {Exec fbsetbg ~/Wallpapers/wallpaper102.jpg}
Mod4 shift 2		:MacroCmd {SetStyle /usr/local/share/fluxbox/styles/bloe} {Exec fbsetbg ~/Wallpapers/Lion-clear.jpg} 
Mod4 shift Delete	:MacroCmd {Exec osdctl -s "Reloading current style,"} {ReloadStyle} 
Mod4 shift m		:RootMenu
Mod4 Mouse3		:RootMenu
Mod4 shift w		:WorkspaceMenu
Mod4 shift t		:WindowMenu
Mod4 shift p            :RootMenu
###########################################################################################################################################
#		 		 Window commands
#
# Controlled (mostly) by Mod4 and Mod1 keys
###########################################################################################################################################

#Window Menu commands (Controlled by Mod4 <Mod1>)
Mod1 F4	 		:Close
Mod4 Mod1 Delete	:KillWindow
Mod4 Mod1 space  	:Shade
Mod4 Mod1 s		:Stick
Mod4 Mod1 0		:ToggleDecor

#Send-to (Controlled by Mod4 Mod1 Fn)
Mod4 Mod1 F1		:SendToWorkspace 1
Mod4 Mod1 F2		:SendToWorkspace 2
Mod4 Mod1 F3		:SendToWorkspace 3
Mod4 Mod1 F4		:SendToWorkspace 4
Mod4 Mod1 shift F2	:SendToNextWorkspace 1
Mod4 Mod1 shift F1	:SendToPrevWorkspace -1

#Take-to (Controlled by Mod4 Fn)
Mod4 F1		 	:TakeToWorkspace 1
Mod4 F2		 	:TakeToWorkspace 2
Mod4 F3		 	:TakeToWorkspace 3
Mod4 F4		 	:TakeToWorkspace 4
Mod4 shift F6		:TakeToNextWorkspace 1
Mod4 shift F5		:TakeToPrevWorkspace -1

#Tabs (Controlled by Mod4 Mod1)
Mod4 Mod1 F9 		:PrevTab
Mod4 Mod1 F10		:NextTab
Mod4 Mod1 F11		:MoveTabLeft
Mod4 Mod1 F12		:MoveTabRight
Mod4 Mod1 Escape	:DetachClient

###########################################################################################################################################
#		 		 Window Layer/Focus/Alpha commands
#
# Controlled (mostly) by Mod4 Mod1
#
###########################################################################################################################################
Mod4 Mod1 End		:Lower
Mod4 Mod1 Home		:Raise
Mod4 Mod1 comma		:LowerLayer
Mod4 Mod1 period	:RaiseLayer
Mod4 Mod1 Up		:FocusUp
Mod4 Mod1 Down		:FocusDown
Mod4 Mod1 Left		:FocusLeft
Mod4 Mod1 Right		:FocusRight
Mod4 Mod1 bracketright	:SetAlpha +5 +5
Mod4 Mod1 bracketleft	:SetAlpha -5 -5
Mod4 Right		:NextWindow
Mod4 Left		:PrevWindow
Mod1 Tab		:NextWindow

###########################################################################################################################################
#		 		 Window Moving/Sizing commands
#
# Controlled by Control Mod1 (and primarly the numeric keypad) for move and Control Mod4 (keypad) for resize
#
###########################################################################################################################################
Control Mod1 f		:Fullscreen
Control Mod1 minus	:Minimize
Control Mod1 equal	:Maximize
Control Mod1 h		:MaximizeHorizontal
Control Mod1 v		:MaximizeVertical

#Moving
Control Mod1 KP_Divide	:MoveTo 10 10
Control Mod1 KP_1	:Move -5 +5
Control Mod1 KP_9	:Move +5 -5
Control Mod1 KP_7	:Move -5 -5
Control Mod1 KP_3	:Move +5 +5
Control Mod1 KP_6	:MoveRight 2
Control Mod1 KP_4	:MoveLeft 2
Control Mod1 KP_8	:MoveUp 2
Control Mod1 KP_2 	:MoveDown 2
Control Mod1 shift KP_6	  :MoveRight 10
Control Mod1 shift KP_4	  :MoveLeft 10
Control Mod1 shift KP_8	  :MoveUp 10
Control Mod1 shift KP_2	  :MoveDown 10
Control Mod1 KP_5 	:MacroCmd {MoveTo 15 15} {ResizeTo 1115 810}
Control Mod1 8 	:MacroCmd {MoveTo -1 -88} {ResizeTo 728 745}
#### Alternate moving using key modes. (i.e. Mod4 w(indow) Mod4 m(ove)).MoveMode 
Mod4 w Mod4 m               :KeyMode MoveMode
MoveMode: None Up           :MoveUp 2
MoveMode: None Down         :MoveDown 2
MoveMode: None Left         :MoveLeft 2
MoveMode: None Right        :MoveRight 2
MoveMode: shift Up          :MoveUp 10
MoveMode: shift Down        :MoveDown 10
MoveMode: shift Left        :MoveLeft 10
MoveMode: shift Right       :MoveRight 10


#Resizing
Control Mod4 KP_Divide		:ResizeTo 800 600
Control Mod4 KP_Multiply	:MacroCmd {MoveTo 20 20} {ResizeTo 1350 985}
Control Mod4 KP_Subtract	:Resize -5 -5
Control Mod4 KP_Add		:Resize +5 +5
Control Mod4 KP_4		:ResizeHorizontal -2
Control Mod4 KP_6		:ResizeHorizontal +2
Control Mod4 KP_8		:ResizeVertical -2
Control Mod4 KP_2		:ResizeVertical +2
Control Mod4 shift KP_4		:ResizeHorizontal -10
Control Mod4 shift KP_6		:ResizeHorizontal +10
Control Mod4 shift KP_8		:ResizeVertical -10
Control Mod4 shift KP_2		:ResizeVertical +10
###Alternate resizing using key modes. (i.e. Mod4 w(indow) Mod4 r(esize)). ResizeMode
Mod4 w Mod4 r               :KeyMode ResizeMode
ResizeMode: None Up         :ResizeVertical -2
ResizeMode: None Down       :ResizeVertical +2
ResizeMode: None Left       :ResizeHorizontal -2
ResizeMode: None Right      :ResizeHorizontal +2
ResizeMode: shift Up         :ResizeVertical -10
ResizeMode: shift Down       :ResizeVertical +10
ResizeMode: shift Left       :ResizeHorizontal -10
ResizeMode: shift Right      :ResizeHorizontal +10

###########################################################################################################################################
#		 		 Workspace commands
#
# Controlled by <Control> Mod4 keys
# Arrange Windows will tile windows vertically
###########################################################################################################################################

Control Mod4 Right	:NextWorkspace
Control Mod4 Left	:PrevWorkspace
Mod4 1		 	:Workspace 1
Mod4 2		 	:Workspace 2
Mod4 3		 	:Workspace 3
Mod4 4		 	:Workspace 4
Mod4 5		 	:Workspace 5
Mod4 6		 	:Workspace 6
Control Mod4 a		:ArrangeWindows
Control Mod4 s		:ShowDesktop
Control Mod4 Up		:Deiconify LastWorkspace
Control Mod4 Down	:Deiconify All OriginQuiet
#Deiconify Last OriginQuiet  # Uniconifies minimized windows
#Deiconify All OriginQuiet   # Uniconifies all minimized windows

###########################################################################################################################################
###########################################################################################################################################
###########################################################################################################################################
###
###   		 		 Custom actions 		 	
###
###########################################################################################################################################
###########################################################################################################################################
###########################################################################################################################################

###########################################################################################################################################
# 		 		 Volume
#
#  Will lower or raise volume by 5%.  The third key binding will toggle mute on and off.
#  Note that this key binding is specific to my multi-media keyboard.  Check 'xev' output for your specific key
###########################################################################################################################################

#None 174       :Exec amixer sset Master,0 5%-
#None 176       :Exec amixer sset Master,0 5%+
None 160       :ToggleCmd {Exec amixer sset Master,0 toggle && osdctl -s "Mute on"} {Exec amixer sset Master,0 toggle && osdctl -s "Mute off"}
None 174	:Exec osdctl -b "Master Volume",$(amixer sset Master,0 5%-|grep "Front Left:"|cut -d "[" -f2|cut -d "%" -f1)
None 176	:Exec osdctl -b "Master Volume",$(amixer sset Master,0 5%+|grep "Front Left:"|cut -d "[" -f2|cut -d "%" -f1)

###########################################################################################################################################
#		 		 Music Player.  
#
#  Amarok.  '-f' will forward one track. '-r' will reverse one track. '--pause' will toggle playback pause
###########################################################################################################################################
Control Mod4 Mod1 Right 	:Exec amarok -f;~/scripts/amarokOsd
Control Mod4 Mod1 Left 		:Exec amarok -r;~/scripts/amarokOsd
Control Mod4 Mod1 Down          :Exec amarok --pause
Control Mod4 Mod1 Up		:Exec amarok --play
Control Mod4 Mod1 o		:Exec ~/scripts/amarokOsd
Control Mod4 Mod1 a		:MacroCmd {Exec feh -x --zoom 200 $(dcop amarok player coverImage)}{Exec sleep 3;kill -9 $(ps -ef|grep albumcovers/cache|grep feh|cut -d " " -f4)}
Control Mod4 Mod1 shift Right	:Exec dcop amarok player seekRelative 7;osdctl -s "$(dcop amarok player currentTime) of $(dcop amarok player totalTime)"
None Menu		 	:CustomMenu ~/.fluxbox/customMenus/Amarok

###########################################################################################################################################
#		 		 Battery Info
###########################################################################################################################################
Control 69:			:Exec osdctl -b "Battery Power",$(acpi|cut -d "," -f2|cut -d "%" -f1|cut -d " " -f2)

###########################################################################################################################################
#		  		 Show/Edit fluxbox files.  
#    	Show (Mod4 s ...)		Read-only display
#	Edit (Mod4 e ...)		Edit in nano.  Terminal running will close after exiting nano.
#					Alternatively, you could use gedit:
#					  Mod4 e Mod4 k   	:Exec gedit ~/.fluxbox/keys
#
#  This shows an emacs style binding of pressing one key sequence and then the next, as well as using environment variables
#  Show commands require 'gmessage' to be installed (sudo aptitude install gmessage)
###########################################################################################################################################
Mod4 s Mod4 k   	:Exec gmessage --file ~/.fluxbox/keys -buttons "Close" -font "monospace 8" -geometry 500x800 -default "Close" -center
Mod4 s Mod4 a   	:Exec gmessage --file ~/.fluxbox/apps -buttons "Close" -font "monospace 8" -geometry 500x800 -default "Close" -center
Mod4 s Mod4 m   	:Exec gmessage --file ~/.fluxbox/menu -buttons "Close" -font "monospace 8" -geometry 800x800 -default "Close" -center
Mod4 s Mod4 i   	:Exec gmessage --file ~/.fluxbox/init -buttons "Close" -font "monospace 8" -geometry 500x800 -default "Close" -center
Mod4 s Mod4 o   	:Exec gmessage --file ~/.fluxbox/overlay -buttons "Close" -font "monospace 8" -geometry 800x800 -default "Close" -center
Mod4 e Mod4 k   	:Exec $CONSOLE nano ~/.fluxbox/keys
Mod4 e Mod4 a   	:Exec $CONSOLE nano ~/.fluxbox/apps
Mod4 e Mod4 m   	:Exec $CONSOLE nano ~/.fluxbox/menu
Mod4 e Mod4 i   	:Exec $CONSOLE nano ~/.fluxbox/init
Mod4 e Mod4 o   	:Exec $CONSOLE nano ~/.fluxbox/overlay

###########################################################################################################################################
#		 		 File Manager  (Mod4 f Mod4 ...)
#
# Thunar is used in the example below, but others will work too
# Custom menu uses a menu of pre-defined locations to open in Thunar (e.g. home, music, video, etc.)
# Mod4 f Mod4 <1..9> are individual key bindings to specific locations
###########################################################################################################################################
Control Menu		:CustomMenu ~/.fluxbox/customMenus/Thunar
Mod4 f Mod4 1		:Exec Thunar ~/.fluxbox
Mod4 f Mod4 2   	:Exec Thunar /usr/bin
Mod4 f Mod4 3   	:Exec Thunar ~/downloads
#Mod4 f Mod4 4   	:Exec Thunar <another-location>
#etc...
#Prepopulate fbrun with text "Thunar ".  Simply supply the directory to go to
Mod4 f Mod4 r   	:Exec fbrun -text "Thunar "

###########################################################################################################################################
#		 		 Common Programs  (Mod4 a Mod4 ...)  ('a' stands for application)
###########################################################################################################################################
Mod4 a Mod4 f		 :Exec ~/Firefox3/firefox
Mod4 a Mod4 t		 :Exec Thunar
Mod4 a Mod4 o		 :Exec opera
Mod4 a Mod4 x		 :Exec xmms
Mod4 a Mod4 a		 :Exec amarok
Mod4 a Mod4 m		 :Exec mozilla-thunderbird
Mod4 a Mod4 p		 :Exec pidgin
Mod4 t		 	 :Exec xfce4-terminal
Mod4 r   		 :Exec fbrun
Mod4 c  		 :ToggleCmd {Exec conky} {Exec pkill conky}

###########################################################################################################################################
#		 		 Session Menu  
#
#  Offers menu with choices lock session, reboot, logout, and shutdown
###########################################################################################################################################
Control Mod1 s		 	 :CustomMenu ~/.fluxbox/customMenus/session

###########################################################################################################################################
#		 		 Screen Shots  
#
# These will create a screenshot in your ~/misc directory.  ("mkdir ~/misc" if you need to create one)
# The first command will take a screenshot of your entire desktop
# The second command will take a screenshot of the active window only
###########################################################################################################################################
None Print             :Exec import -window root ~/screenshots/screen$(date +%F_%H.%M).png
Mod4 Print             :Exec import -frame -window $(xprop _NET_ACTIVE_WINDOW -root | awk '{print $5}') ~/screenshots/window$(date +%F_%H.%M).png

###########################################################################################################################################
#		 		 		 		 Commonly Used Websites  
###########################################################################################################################################
Mod4 x Mod4 b           :Exec ~/firefox/firefox http://news.bbc.co.uk
Mod4 x Mod4 w           :Exec ~/firefox/firefox http://www.metoffice.gov.uk/weather/uk/dg/edinburgh_forecast_weather.html
Mod4 x Mod4 u           :Exec ~/firefox/firefox http://ubuntuforums.org/
Mod4 x Mod4 y           :Exec ~/firefox/firefox http://news.yahoo.com
Mod4 x Mod4 m           :Exec ~/firefox/firefox http://webmail.nildram.co.uk
Mod4 x Mod4 g           :Exec ~/firefox/firefox http://mail.google.com/mail/#inbox

###########################################################################################################################################
#		 		 		 		 Misc actions  
###########################################################################################################################################

#Toggle between empty workspace (i.e. desktop) and open windows
Mod4 d 			:ToggleCmd {ShowDesktop} {DeIconify all originquiet}

#This is currently broken as Reconfigure resets the Toggle, so will never reach the 'other' toggle.
#Mod4 v :ToggleCmd (MacroCmd (SetResourceValue session.screen0.toolbar.visible true) (Reconfigure)) (MacroCmd (SetResourceValue session.screen0.toolbar.visible false) (Reconfigure))

#Hide/Show toolbar with 2 macro commands until Toggle/Reconfigure bug is fixed
Mod4 comma		:MacroCmd {SetResourceValue session.screen0.toolbar.visible false} {Reconfigure}
Mod4 period		:MacroCmd {SetResourceValue session.screen0.toolbar.visible true} {Reconfigure}

#Turn monitor off
None Pause		:Exec xset dpms force off
None 214		:Exec xset dpms force off

#Print Calendar for this month (KP_1), prev/this/next month (KP_2), or for the year (KP_3)
Mod4 KP_1 :Exec zenity --calendar --text=""
Mod4 KP_2 :Exec (date +'Today: %A %b %d';echo;cal -3)| gmessage --file - -buttons "GTK_STOCK_CLOSE" -font "monospace 8" -geometry 505x229 --borderless -default "GTK_STOCK_CLOSE" -center
Mod4 KP_3 :Exec (date +'Today: %A %b %d';echo;cal -y)| gmessage --file - -buttons "GTK_STOCK_CLOSE" -font "monospace 8" -geometry 505x570 --borderless -default "GTK_STOCK_CLOSE" -center
Mod4 KP_5 :Exec osdctl -s "$(date +'%A %d %b %H:%M,')"


#Show Edinburgh current weather
Mod4 s Mod4 w :Exec feh http://xweb.geos.ed.ac.uk/weather/station/minute.gif

Mod4 7 :Exec wmctrl -r :ACTIVE: -e 0,0,0,1400,525
Mod4 8 :Exec wmctrl -r :ACTIVE: -e 0,0,525,1400,525

```

---

### Post by easybake on 2008-11-09
Here is my set up. [[IMG]http://img143.imageshack.us/img143/6219/screenshotwy9.th.png[/IMG]](http://img143.imageshack.us/img143/6219/screenshotwy9.png)
Not much to my keys file. Here's my tree'd out menu.```
#easybake


[begin]
	[exec] (Firefox 3) {/usr/bin/firefox-3.0}
	[separator]
	[exec] (Terminal) {gnome-terminal}
	[exec] (Rhythmbox) {rhythmbox}
	[exec] (/Home) {/usr/bin/nautilus --no-desktop}
	[submenu] (Games)
	       	[exec] (Nibbles) {/usr/games/gnibbles} </usr/share/pixmaps/gnibbles.xpm>
		[exec] (Frozen-Bubble) {/usr/games/frozen-bubble} </usr/share/pixmaps/frozen-bubble.xpm>
		[exec] (Tetris) {/usr/games/gnometris} </usr/share/pixmaps/gnometris.xpm>
		[exec] (Four-in-a-row) {/usr/games/gnect} </usr/share/pixmaps/gnect.xpm>
		[exec] (Chess) {/usr/games/glchess} </usr/share/pixmaps/glchess.xpm>
		[exec] (Yahtzee) {/usr/games/gtali} </usr/share/pixmaps/gtali.xpm>
		[exec] (Lagno) {/usr/games/iagno} </usr/share/pixmaps/iagno.xpm>
		[exec] (Lines) {/usr/games/glines} </usr/share/pixmaps/glines.xpm>
		[exec] (Mahjongg) {/usr/games/mahjongg} </usr/share/pixmaps/gnome-mahjongg.xpm>
		[exec] (Blackjack) {/usr/games/blackjack} </usr/share/pixmaps/blackjack.xpm>
		[exec] (FreeCell) {/usr/games/sol --variation freecell} </usr/share/pixmaps/freecell.xpm>
		[exec] (Solitaire) {/usr/games/sol} </usr/share/pixmaps/aisleriot.xpm>
		[exec] (Klotski) {/usr/games/gnotski} </usr/share/pixmaps/gnotski.xpm>
		[exec] (Robots) {/usr/games/gnobots2} </usr/share/pixmaps/gnobots2.xpm>
		[exec] (Sudoku) {/usr/games/gnome-sudoku} </usr/share/pixmaps/gnome-sudoku.xpm>
		[exec] (Tetravex) {/usr/games/gnotravex} </usr/share/pixmaps/gnotravex.xpm>
		[exec] (Mine) {/usr/games/gnomine} </usr/share/pixmaps/gnomine.xpm>
		[exec] (Same) {/usr/games/same-gnome} </usr/share/pixmaps/gsame.xpm>
		[exec] (Type) {tuxtype}
		[exec] (SNes) {/usr/bin/snes9express}
		[exec] (Steam) {env WINEPREFIX="/home/easybake/.wine" wine "C:\Program Files\Steam\Steam.exe"}
		[exec] (Unreal GOTY) {wine /home/easybake/Documents/UnrealTournament/UnrealTournament/System/UnrealTournament.exe}
		[submenu] (Unreal 2004)
	         	[exec] (Play) {./unreal.sh}
			[exec] (Kill) {./killunreal.sh}
		[end]
	[end]
	[submenu] (System)
		[submenu] (Fluxbox)
			[submenu] (Edit)
				[exec] (Menu) {gedit ~/.fluxbox/menu}
				[exec] (Keys) {gedit ~/.fluxbox/keys}
				[exec] (Apps) {gedit ~/.fluxbox/apps}
				[exec] (Startup) {gedit ~/.fluxbox/startup}
			[end]
			[separator]
			[exec] (Themes) {gtk-chtheme}
			[submenu] (Styles) {}
				[stylesdir] (/usr/share/fluxbox/styles)
				[stylesdir] (~/.fluxbox/styles)
			[end]
			[config] (Configuration)
			[workspaces] (Workspaces)
			[separator]
			[restart] (Restart)  {/usr/bin/startfluxbox}
		[end]
		[submenu] (Wallpapers)
			[wallpapers] (/home/easybake/Pictures/Wallpapers/Best) {feh –bg-scale}
		[end]
		[separator]
		[exec] (System Monitor) {gnome-system-monitor}
		[exec] (Control Center) {/usr/bin/gnome-control-center}
		[separator]
		[exec] (Googlizer) {googlizer --url http://www.google.com/search?q=}
		[submenu] (Conky)
			[exec] (Refresh) {./conkyrefresh}
			[exec] (Toggle) {./conkytoggle}
			[separator]
			[exec] (Edit) {gedit /home/easybake/.conkyscripts/conkyscript1 & gedit /home/easybake/.conkyscripts/conkyscript2 & gedit /home/easybake/.conkyscripts/conkyscript3 & gedit /home/easybake/.conkyscripts/conkyscript4 & gedit .conkyrc}
		[end]
		[submenu] (A.V.)
			[exec] (GIMP) {gimp}
			[exec] (PhotoPrint) {/usr/bin/photoprint} 
			[exec] (VLC) {vlc}
			[exec] (Cinelerra) {cinelerra}
			[exec] (Webcam) {webcambin}
			[exec] (Audacity) {audacity}
			[exec] (Volume) {/usr/bin/gnome-volume-control}
			[exec] (GRecord) {/usr/bin/gnome-sound-recorder}
			[exec] (Screenshot) {/usr/bin/gnome-panel-screenshot} 
			[exec] (RecordMyDesktop) {/usr/bin/gtk-recordMyDesktop}
		[end]
		[submenu] (Network)
			[exec] (IPblock) {sudo ipblock -g}
			[exec] (Pidgin) {pidgin}
			[exec] (Skype) {skype}
			[exec] (Ekiga) {/usr/bin/ekiga} 
			[exec] (Azureus) {/usr/bin/azureus}
			[exec] (CheckGMail)
			[exec] (Evolution) {/usr/bin/evolution} 
		[end]
		[submenu] (Office) {}
			[exec] (Gedit) {gedit}
			[exec] (Calculator) {/usr/bin/gcalctool}
			[exec] (OpenOffice.org Writer) {/usr/bin/oowriter} </usr/share/icons/gnome/32x32/apps/openofficeorg24-writer.xpm>
			[exec] (OpenOffice.org Calc) {/usr/bin/oocalc} </usr/share/icons/gnome/32x32/apps/openofficeorg24-calc.xpm>
			[exec] (OpenOffice.org Draw) {/usr/bin/oodraw} </usr/share/icons/gnome/32x32/apps/openofficeorg24-draw.xpm>
			[exec] (OpenOffice.org Impress) {/usr/bin/ooimpress} </usr/share/icons/gnome/32x32/apps/openofficeorg24-impress.xpm>
	       		[exec] (Notes) {/usr/bin/tomboy} 
			[exec] (FontForge) {/usr/bin/fontforge}
			[exec] (Character map) {/usr/bin/gucharmap}
		[end]
		[submenu] (Control) {}
			[submenu] (Screen)
				[exec] (On) {./screenon}
				[exec] (Off) {./screenoff}
			[end]
			[exec] (NVidia) {/usr/bin/nvidia-settings}
			[exec] (EnvyNG) {/usr/share/envy/launcher}
			[exec] (Printing) {/usr/bin/system-config-printer}
			[exec] (Network Tool) {/usr/bin/gnome-nettool} 
			[exec] (Alsaconf) { x-terminal-emulator -T "alsaconf" -e su-to-root -p root -c /usr/sbin/alsaconf} <>
			[exec] (Aptitude) { x-terminal-emulator -T "Aptitude" -e /usr/bin/aptitude} <>
			[exec] (Network) {/usr/bin/network-admin} 
			[exec] (Time) {/usr/bin/time-admin} 
			[exec] (User Accounts) {/usr/bin/users-admin} 
			[exec] (Services) {/usr/bin/services-admin}
			[exec] (Shares) {/usr/bin/shares-admin}
			[exec] (AcetoneISO) {acetoneiso2}
			[exec] (K9Copy) {k9copy}
			[exec] (DVDRip) {/usr/bin/dvdrip}
		[end]
		[submenu] (Wine)
			[exec](Config) {winecfg}
			[exec](C:// Drive) {nautilus --no-desktop /home/easybake/.wine/drive_c}
		[end]
		[submenu] (Update)
			[exec] (Check) {update-manager}
			[exec] (Synaptic) {/usr/bin/gksu /usr/sbin/synaptic}
			[exec] (Add/Remove) {gnome-app-install}
		[end]
		[separator]
		[exit] (Quit)
	[end]
	[separator]
	[exec] (Lock) {xlock -mode laser}
[end]
```

---

### Post by -grubby on 2008-11-09
Back when I loved Fluxbox I had those files really customized.. right now it's :

Also, a note about the menu: I'm aware [nop] exists, I just like something I can hover over

Menu:
```

[begin] (linda)

    # Most frequently used apps
    [exec] (Opera)        {opera}           <>
    [exec] (Xterm)        {xterm}           <>
    [exec] (------------)
    [exec] (Gajim)        {gajim}           <>
    [exec] (Pidgin)       {pidgin}          <>
    [exec] (------------)
    [exec] (Konversation) {konversation}    <>
    [exec] (Irssi)        {xterm "irssi"}   <>

# Useless unless  I need a default apps list
!    [exec] (------------)

!    [submenu] (Default)
!        [include] (/etc/X11/fluxbox/fluxbox-menu)
!    [end]

    [exec] (------------)

    [submenu] (Misc)
        [exec] (Firefox) {firefox}
        [exec] (Geany)        {geany}           <>
    [end]

    [exec] (------------)

    [submenu] (Fluxbox)
        [config] (Config)

        [submenu] (Styles)
            [submenu] (Default)
                [stylesdir] (/usr/share/fluxbox/styles)
            [end]
            [submenu] (Custom)
                [stylesdir] (~/.fluxbox/styles)
            [end]
        [end]
        [workspaces] (Workspaces)
        [reconfig] (Reconfigure)
        [restart] (Restart)
    [end]

    [exec] (------------)

    [exit] (Exit)

[end]

```

Keys (as far as I know; not modified) :
```

OnDesktop Mouse1 :HideMenus
OnDesktop Mouse2 :WorkspaceMenu
OnDesktop Mouse3 :RootMenu
OnDesktop Mouse4 :NextWorkspace
OnDesktop Mouse5 :PrevWorkspace

Mod1 Tab :NextWindow
Mod1 Shift Tab :PrevWindow
Mod1 F1 :Workspace 1
Mod1 F2 :Workspace 2
Mod1 F3 :Workspace 3
Mod1 F4 :Workspace 4
Mod1 F5 :Workspace 5
Mod1 F6 :Workspace 6
Mod1 F7 :Workspace 7
Mod1 F8 :Workspace 8
Mod1 F9 :Workspace 9
Mod1 F10 :Workspace 10
Mod1 F11 :Workspace 11
Mod1 F12 :Workspace 12

```

---

### Post by Le-Froid on 2008-11-09
Keys:
```

OnDesktop Mouse1 :HideMenus
OnDesktop Mouse2 :WorkspaceMenu
OnDesktop Mouse3 :RootMenu
OnDesktop Mouse4 :NextWorkspace
OnDesktop Mouse5 :PrevWorkspace

Mod1 Tab :NextWindow
Mod1 Shift Tab :PrevWindow
Mod1 F1 :Workspace 1
Mod1 F2 :Workspace 2
Mod1 F3 :Workspace 3
Mod1 F4 :Workspace 4
Mod1 F5 :Workspace 5
Mod1 F6 :Workspace 6
Mod1 F7 :Workspace 7
Mod1 F8 :Workspace 8
Mod1 F9 :Workspace 9
Mod1 F10 :Workspace 10
Mod1 F11 :Workspace 11
Mod1 F12 :Workspace 12
Mod1 x :ExecCommand xterm &

```

Menu:
```

[begin] (fluxbox)
[exec] (Nautilus) {/usr/bin/nautilus --no-desktop} </usr/share/pixmaps/nautilus>
[include] (/etc/X11/fluxbox/fluxbox-menu)
[end]

```

-- /etc/X11/fluxbox/fluxbox-menu
```

# This is an automatically generated file.
# Please see <file:/usr/share/doc/menu/README> for information.

# to use your own menu, copy this to ~/.fluxbox/menu, then edit
# ~/.fluxbox/init and change the session.menuFile path to ~/.fluxbox/menu

[begin] (Fluxbox)

# Automatically generated file. Do not edit (see /usr/share/doc/menu/html/index.html)

   [submenu] (Applications) {}
      [submenu] (Accessibility) {}
         [exec] (Xmag) {xmag} <>
      [end]
      [submenu] (Data Management) {}
         [exec] (Tomboy) {/usr/bin/tomboy} <>
      [end]
      [submenu] (Editors) {}
         [exec] (Emacs 22 (GTK\)) {/usr/bin/emacs22-gtk} </usr/share/emacs/22.2/etc/emacs.xpm>
         [exec] (Emacs 22 (text\)) { x-terminal-emulator -T "Emacs 22 (text)" -e /usr/bin/emacs22 -nw} </usr/share/emacs/22.2/etc/emacs.xpm>
         [exec] (Gedit) {/usr/bin/gedit} </usr/share/pixmaps/gedit-icon.xpm>
         [exec] (GVIM) {/usr/bin/vim.gnome -g -f} </usr/share/pixmaps/vim-32.xpm>
         [exec] (Nano) { x-terminal-emulator -T "Nano" -e /bin/nano} </usr/share/nano/nano-menu.xpm>
         [exec] (Xedit) {xedit} <>
      [end]
      [submenu] (Emulators) {}
         [exec] (VirtualBox OSE) {/usr/bin/virtualbox} </usr/share/pixmaps/virtualbox-ose.xpm>
      [end]
      [submenu] (File Management) {}
         [exec] (Baobab) {/usr/bin/baobab} </usr/share/pixmaps/baobab.xpm>
         [exec] (Brasero) {/usr/bin/brasero} <>
         [exec] (File-Roller) {/usr/bin/file-roller} </usr/share/pixmaps/file-roller.xpm>
         [exec] (GNOME Search Tool) {/usr/bin/gnome-search-tool} </usr/share/pixmaps/gsearchtool.xpm>
         [exec] (K3b) {/usr/bin/k3b} </usr/share/pixmaps/k3b.xpm>
         [exec] (Nautilus) {/usr/bin/nautilus} </usr/share/pixmaps/nautilus.xpm>
         [exec] (Tracker Search Tool) {/usr/bin/tracker-search-tool} <>
      [end]
      [submenu] (Graphics) {}
         [exec] (GNOME Screenshot Tool) {/usr/bin/gnome-panel-screenshot} <>
         [exec] (ImageMagick) {/usr/bin/display logo:} <>
         [exec] (OpenOffice.org Draw) {/usr/bin/oodraw} </usr/share/icons/gnome/32x32/apps/openofficeorg30-draw.xpm>
         [exec] (The GIMP) {/usr/bin/gimp} </usr/share/pixmaps/gimp.xpm>
         [exec] (XSane) {/usr/bin/xsane} </usr/share/pixmaps/xsane.xpm>
         [exec] (X Window Snapshot) {xwd | xwud} <>
      [end]
      [submenu] (Network) {}
         [submenu] (Communication) {}
            [exec] (Ekiga) {/usr/bin/ekiga} </usr/share/pixmaps/ekiga-logo-icon.png>
            [exec] (Evolution) {/usr/bin/evolution} </usr/share/pixmaps/evolution.xpm>
            [exec] (Konversation IRC Client) {/usr/bin/konversation} </usr/share/pixmaps/konversation32x32.xpm>
            [exec] (Pidgin) {/usr/bin/pidgin} </usr/share/pixmaps/pidgin-menu.xpm>
            [exec] (Terminal Server Client) {/usr/bin/tsclient -f} </usr/share/pixmaps/tsclient.xpm>
            [exec] (Xbiff) {xbiff} <>
         [end]
         [submenu] (File Transfer) {}
            [exec] (KTorrent) {ktorrent} </usr/share/pixmaps/ktorrent.xpm>
            [exec] (Transmission BitTorrent Client) {/usr/bin/transmission} </usr/share/pixmaps/transmission.xpm>
         [end]
         [submenu] (Monitoring) {}
            [exec] (KNetworkManager) {/usr/bin/knetworkmanager} <>
         [end]
         [exec] (Telnet) { x-terminal-emulator -T "Telnet" -e /usr/bin/telnet} <>
         [submenu] (Web Browsing) {}
            [exec] (Firefox 3 Browser) {/usr/bin/firefox-3.0} </usr/share/pixmaps/firefox-3.0.png>
            [exec] (w3m) { x-terminal-emulator -T "w3m" -e /usr/bin/w3m /usr/share/doc/w3m/MANUAL.html} <>
         [end]
      [end]
      [submenu] (Office) {}
         [exec] (HPLIP Fax address book) {/usr/bin/hp-fab} </usr/share/pixmaps/HPmenu.xpm>
         [exec] (HPLIP Fax utility) {/usr/bin/hp-sendfax} </usr/share/pixmaps/HPmenu.xpm>
         [exec] (OpenOffice.org Calc) {/usr/bin/oocalc} </usr/share/icons/gnome/32x32/apps/openofficeorg30-calc.xpm>
         [exec] (OpenOffice.org Impress) {/usr/bin/ooimpress} </usr/share/icons/gnome/32x32/apps/openofficeorg30-impress.xpm>
         [exec] (OpenOffice.org Writer) {/usr/bin/oowriter} </usr/share/icons/gnome/32x32/apps/openofficeorg30-writer.xpm>
      [end]
      [submenu] (Programming) {}
         [exec] (anjuta) {/usr/bin/anjuta} </usr/share/pixmaps/anjuta.xpm>
         [exec] (ccmake) { x-terminal-emulator -T "ccmake" -e /usr/bin/ccmake} </usr/share/pixmaps/cmake.xpm>
         [exec] (codeblocks) {/usr/bin/codeblocks} <>
         [exec] (GDB) { x-terminal-emulator -T "GDB" -e /usr/bin/gdb} <>
         [exec] (Geany) {/usr/bin/geany} </usr/share/pixmaps/geany.xpm>
         [exec] (KDevelop) {/usr/bin/kdevelop} </usr/share/pixmaps/kdevelop.xpm>
         [exec] (Qt Assistant) {/usr/bin/assistant-qt4} <>
         [exec] (Qt Designer) {/usr/bin/designer-qt4} <>
         [exec] (Qt Linguist) {/usr/bin/linguist-qt4} <>
         [exec] (SpiderMonkey JavaScript Interpreter) { x-terminal-emulator -T "SpiderMonkey JavaScript Interpreter" -e /usr/bin/smjs} <>
         [exec] (Sun Java 6 Web Start) {/usr/lib/jvm/java-6-sun-1.6.0.10/bin/javaws -viewer} </usr/share/pixmaps/sun-java6.xpm>
         [exec] (Tclsh8.4) { x-terminal-emulator -T "Tclsh8.4" -e /usr/bin/tclsh8.4} <>
      [end]
      [submenu] (Science) {}
         [submenu] (Mathematics) {}
            [exec] (Bc) { x-terminal-emulator -T "Bc" -e /usr/bin/bc} <>
            [exec] (Dc) { x-terminal-emulator -T "Dc" -e /usr/bin/dc} <>
            [exec] (GCalcTool) {/usr/bin/gcalctool} </usr/share/pixmaps/gcalctool.xpm>
            [exec] (OpenOffice.org Math) {/usr/bin/oomath} </usr/share/icons/gnome/32x32/apps/openofficeorg30-math.xpm>
            [exec] (SpeedCrunch) {/usr/bin/speedcrunch} <speedcrunch.xpm>
            [exec] (Xcalc) {xcalc} <>
         [end]
      [end]
      [submenu] (Shells) {}
         [exec] (Bash) { x-terminal-emulator -T "Bash" -e /bin/bash --login} <>
         [exec] (Csh) { x-terminal-emulator -T "Csh" -e /bin/bsd-csh -l} <>
         [exec] (Dash) { x-terminal-emulator -T "Dash" -e /bin/dash -i} <>
         [exec] (Python (v2.4\)) { x-terminal-emulator -T "Python (v2.4)" -e /usr/bin/python2.4} </usr/share/pixmaps/python2.4.xpm>
         [exec] (Python (v2.5\)) { x-terminal-emulator -T "Python (v2.5)" -e /usr/bin/python2.5} </usr/share/pixmaps/python2.5.xpm>
         [exec] (Sh) { x-terminal-emulator -T "Sh" -e /bin/sh --login} <>
      [end]
      [submenu] (Sound) {}
         [exec] (Amarok) {/usr/bin/amarok} <>
         [exec] (Banshee) {/usr/bin/banshee} </usr/share/pixmaps/banshee.xpm>
         [exec] (gmix (Gnome 2.0 Mixer\)) {/usr/bin/gnome-volume-control} </usr/share/pixmaps/gnome-mixer.xpm>
         [exec] (grecord (GNOME 2.0 Recorder\)) {/usr/bin/gnome-sound-recorder} </usr/share/pixmaps/gnome-grecord.xpm>
         [exec] (Rhythmbox) {/usr/bin/rhythmbox} </usr/share/pixmaps/rhythmbox.xpm>
         [exec] (Sound Juicer) {/usr/bin/sound-juicer} </usr/share/pixmaps/sound-juicer.xpm>
         [exec] (vumeter (Gnome 2.0 Volume Meter\)) {/usr/bin/vumeter} </usr/share/pixmaps/gnome-vumeter.xpm>
      [end]
      [submenu] (System) {}
         [submenu] (Administration) {}
            [exec] (alsaconf) { x-terminal-emulator -T "alsaconf" -e su-to-root -p root -c /usr/sbin/alsaconf} <>
            [exec] (Aptitude) { x-terminal-emulator -T "Aptitude" -e /usr/bin/aptitude} <>
            [exec] (Debian Task selector) { x-terminal-emulator -T "Debian Task selector" -e su-to-root -c tasksel} <>
            [exec] (DSL/PPPoE configuration tool) { x-terminal-emulator -T "DSL/PPPoE configuration tool" -e /usr/sbin/pppoeconf} </usr/share/pixmaps/pppoeconf.xpm>
            [exec] (Editres) {editres} <>
            [exec] (GDM flexiserver) {gdmflexiserver} </usr/share/pixmaps/gdm.xpm>
            [exec] (GDM flexiserver in Xnest) {gdmflexiserver -n} </usr/share/pixmaps/gdm.xpm>
            [exec] (GDM Photo Setup) {gdmphotosetup} </usr/share/pixmaps/gdm.xpm>
            [exec] (GDM Setup) {su-to-root -X -p root -c /usr/sbin/gdmsetup} </usr/share/pixmaps/gdm.xpm>
            [exec] (Gnome Control Center) {/usr/bin/gnome-control-center} </usr/share/pixmaps/control-center2.xpm>
            [exec] (GNOME partition editor) {su-to-root -X -c /usr/sbin/gparted} </usr/share/pixmaps/gparted.xpm>
            [exec] (GTK+ 2.0 theme manager) {/usr/bin/gtk-chtheme} </usr/share/pixmaps/gtk-chtheme.xpm>
            [exec] (HPLIP File printing) {/usr/bin/hp-print} </usr/share/pixmaps/HPmenu.xpm>
            [exec] (OpenJDK Java 6 Console) {/usr/lib/jvm/java-6-openjdk/bin/jconsole} </usr/share/pixmaps/openjdk-6.xpm>
            [exec] (OpenJDK Java 6 Policy Tool) {/usr/lib/jvm/java-6-openjdk/bin/policytool} </usr/share/pixmaps/openjdk-6.xpm>
            [exec] (pppconfig) { x-terminal-emulator -T "pppconfig" -e su-to-root -p root -c /usr/sbin/pppconfig} <>
            [exec] (QtConfig) {/usr/bin/qtconfig-qt4} <>
            [exec] (Services Admin) {/usr/bin/services-admin} </usr/share/gnome-system-tools/pixmaps/services.xpm>
            [exec] (Shares Admin) {/usr/bin/shares-admin} </usr/share/gnome-system-tools/pixmaps/shares.xpm>
            [exec] (Sun Java 6 Plugin Control Panel) {/usr/lib/jvm/java-6-sun-1.6.0.10/bin/ControlPanel} </usr/share/pixmaps/sun-java6.xpm>
            [exec] (Time Admin) {/usr/bin/time-admin} </usr/share/gnome-system-tools/pixmaps/time.xpm>
            [exec] (User accounts Admin) {/usr/bin/users-admin} </usr/share/gnome-system-tools/pixmaps/users.xpm>
            [exec] (Xclipboard) {xclipboard} <>
            [exec] (Xfontsel) {xfontsel} <>
            [exec] (Xkill) {xkill} <>
            [exec] (Xrefresh) {xrefresh} <>
         [end]
         [exec] (GNOME Network Tool) {/usr/bin/gnome-nettool} </usr/share/pixmaps/gnome-nettool.xpm>
         [exec] (GNOME system monitor) {/usr/bin/gnome-system-monitor} <>
         [submenu] (Hardware) {}
            [exec] (GNOME Floppy Formatter) {/usr/bin/gfloppy} </usr/share/pixmaps/gfloppy.xpm>
            [exec] (HPLIP Toolbox) {/usr/bin/hp-toolbox} </usr/share/pixmaps/HPmenu.xpm>
            [exec] (Windows Wireless Drivers) {su-to-root -X -c /usr/sbin/ndisgtk} </usr/share/pixmaps/ndisgtk.xpm>
            [exec] (Xvidtune) {xvidtune} <>
         [end]
         [submenu] (Monitoring) {}
            [exec] (Conky) { x-terminal-emulator -T "Conky" -e /usr/bin/conky} <>
            [exec] (GNOME Log Viewer) {/usr/bin/gnome-system-log} </usr/share/pixmaps/gnome-system-log.xpm>
            [exec] (Pstree) { x-terminal-emulator -T "Pstree" -e /usr/bin/pstree.x11} </usr/share/pixmaps/pstree16.xpm>
            [exec] (Top) { x-terminal-emulator -T "Top" -e /usr/bin/top} <>
            [exec] (Xconsole) {xconsole -file /dev/xconsole} <>
            [exec] (Xev) {x-terminal-emulator -e xev} <>
            [exec] (Xload) {xload} <>
         [end]
         [submenu] (Package Management) {}
            [exec] (Synaptic Package Manager) {/usr/bin/gksu /usr/sbin/synaptic} </usr/share/synaptic/pixmaps/synaptic_32x32.xpm>
         [end]
         [exec] (ROX Filer) {/usr/bin/rox} <>
         [submenu] (Security) {}
            [exec] (Seahorse) {/usr/bin/seahorse} </usr/share/pixmaps/seahorse.xpm>
            [exec] (Sun Java 6 Policy Tool) {/usr/lib/jvm/java-6-sun-1.6.0.10/bin/policytool} </usr/share/pixmaps/sun-java6.xpm>
         [end]
      [end]
      [submenu] (Terminal Emulators) {}
         [exec] (Eterm) {/usr/bin/Eterm} <>
         [exec] (Gnome Terminal) {/usr/bin/gnome-terminal} </usr/share/pixmaps/gnome-terminal.xpm>
         [exec] (XTerm) {xterm} </usr/share/pixmaps/xterm-color_32x32.xpm>
         [exec] (X-Terminal as root (GKsu\)) {/usr/bin/gksu -u root /usr/bin/x-terminal-emulator} </usr/share/pixmaps/gksu-debian.xpm>
         [exec] (XTerm (Unicode\)) {uxterm} </usr/share/pixmaps/xterm-color_32x32.xpm>
      [end]
      [submenu] (Text) {}
         [exec] (Character map) {/usr/bin/gucharmap} <>
         [exec] (Fortune) {sh -c 'while /usr/games/fortune | col -x | xmessage -center -buttons OK:1,Another:0 -default OK -file - ; do :; done'} <>
         [exec] (GNOME Dictionary) {/usr/bin/gnome-dictionary} </usr/share/pixmaps/gdict.xpm>
      [end]
      [submenu] (Video) {}
         [exec] (totem (GStreamer\)) {/usr/bin/totem-gstreamer} </usr/share/pixmaps/totem.xpm>
      [end]
      [submenu] (Viewers) {}
         [exec] (Evince) {/usr/bin/evince} </usr/share/pixmaps/evince.xpm>
         [exec] (Eye of GNOME) {/usr/bin/eog} </usr/share/pixmaps/gnome-eog.xpm>
         [exec] (F-Spot) {/usr/bin/f-spot} <>
         [exec] (Xditview) {xditview} <>
         [exec] (xine Media Player) {/usr/bin/xine} </usr/share/pixmaps/xine.xpm>
      [end]
   [end]
   [submenu] (Games) {}
      [submenu] (Action) {}
         [exec] (Gnibbles) {/usr/games/gnibbles} </usr/share/pixmaps/gnibbles.xpm>
      [end]
      [submenu] (Blocks) {}
         [exec] (Gnometris) {/usr/games/gnometris} </usr/share/pixmaps/gnometris.xpm>
      [end]
      [submenu] (Board) {}
         [exec] (Four-in-a-row) {/usr/games/gnect} </usr/share/pixmaps/gnect.xpm>
         [exec] (GL Chess) {/usr/games/glchess} </usr/share/pixmaps/glchess.xpm>
         [exec] (Gnome GYahtzee) {/usr/games/gtali} </usr/share/pixmaps/gtali.xpm>
         [exec] (Gnome Iagno) {/usr/games/iagno} </usr/share/pixmaps/iagno.xpm>
         [exec] (Gnome Lines) {/usr/games/glines} </usr/share/pixmaps/glines.xpm>
         [exec] (Gnome Mahjongg) {/usr/games/mahjongg} </usr/share/pixmaps/gnome-mahjongg.xpm>
      [end]
      [submenu] (Card) {}
         [exec] (Gnome Blackjack) {/usr/games/blackjack} </usr/share/pixmaps/blackjack.xpm>
         [exec] (Gnome FreeCell) {/usr/games/sol --variation freecell} </usr/share/pixmaps/freecell.xpm>
         [exec] (Gnome Solitaire Games) {/usr/games/sol} </usr/share/pixmaps/aisleriot.xpm>
      [end]
      [submenu] (Puzzles) {}
         [exec] (Gnome Klotski) {/usr/games/gnotski} </usr/share/pixmaps/gnotski.xpm>
         [exec] (Gnome Robots) {/usr/games/gnobots2} </usr/share/pixmaps/gnobots2.xpm>
         [exec] (Gnome Sudoku) {/usr/games/gnome-sudoku} </usr/share/pixmaps/gnome-sudoku.xpm>
         [exec] (Gnome Tetravex) {/usr/games/gnotravex} </usr/share/pixmaps/gnotravex.xpm>
         [exec] (Gnomine) {/usr/games/gnomine} </usr/share/pixmaps/gnomine.xpm>
         [exec] (Same Gnome) {/usr/games/same-gnome} </usr/share/pixmaps/gsame.xpm>
      [end]
      [submenu] (Toys) {}
         [exec] (Oclock) {oclock} <>
         [exec] (Xclock (analog\)) {xclock -analog} <>
         [exec] (Xclock (digital\)) {xclock -digital -update 1} <>
         [exec] (Xeyes) {xeyes} <>
         [exec] (Xlogo) {xlogo} <>
      [end]
   [end]
   [submenu] (Help) {}
      [exec] (Info) { x-terminal-emulator -T "Info" -e info} <>
      [exec] (Xman) {xman} <>
      [exec] (yelp) {/usr/bin/yelp} <>
   [end]
   [submenu] (Window Managers) {}
      [restart] (FluxBox)  {/usr/bin/startfluxbox}
   [end]

   [config] (Configuration)
   [submenu] (Styles) {}
      [stylesdir] (/usr/share/fluxbox/styles)
      [stylesdir] (~/.fluxbox/styles)
   [end]
   [workspaces] (Workspaces)
   [reconfig] (Reconfigure)
   [restart] (Restart)
   [exit] (Exit)

[end]

```

edit: screenshot:

---

### Post by p_quarles on 2008-11-09
> **cknight said:**
> Heh, you asked for it!  I certainly don't always remember most of these, but I had great fun creating this for my fluxbox keys how-to.  I don't really use the menu much.  Mostly launch things via fbrun (that's "Mod4 r" :))
Thanks for posting this. I hadn't known about osdsh/osdctl before now, but I'm liking it. 

What settings do you use for that? More specifically, I'm wondering if there's any way to make the bar displays "smoother."

---

### Post by spupy on 2008-11-09
> **easybake said:**
> Here is my set up. [[IMG]http://img143.imageshack.us/img143/6219/screenshotwy9.th.png[/IMG]](http://img143.imageshack.us/img143/6219/screenshotwy9.png)
Can you tell me what theme are you using? I just put that same wallpaper today and wondered for a good fluxbox theme to go with it.

[My desktop (link)]("http://vesso.marv.lafka.net/screens/screens28/2008-11-10-033206_1280x800_scrot.png")

My menu, which I don't use very much. The more interesting stuff is in the Utils submenu.
```

[begin] (Fluxbox)
[encoding] {UTF-8}
      [exec] (htop) {aterm +sb -e htop} 
      [exec] (aterm) {aterm +sb -bg black -fg white -sh 60}
      [exec] (leafpad) {leafpad}
[separator]
[submenu] (Apps)
      [exec] (pidgin) {pidgin}
      [exec] (skype) {skype}
      [exec] (rtorrent) {aterm +sb -e rtorrent}      
      [exec] (firefox) {firefox}
      [exec] (thunderbird) {thunderbird}
      [exec] (liferea) {liferea}
[end]
[submenu] (Apps2) 
	[exec] (Sonata) {sonata}
	[exec] (Gimp) {gimp}     
	[exec] (ExFalso) {exfalso}
	[exec] (Config XScreensaver) {xscreensaver-demo}
	[exec] (Graveman) {graveman}
	[exec] (Calculator) {gcalctool}
	[exec] (File-roller) {file-roller}
	[separator]
	[exec] (Evince) {evince}
	[exec] (Inkscape) {inkscape}
	[exec] (gRip) {grip}
	[exec] (gFTP) {gftp}
	[exec] (OpenOffice) {ooffice}
[end]
[submenu] (Utils)
	[exec] (Toggle xcompmgr) {/home/uibxn/Scripts/ToggleXComp.sh}
	[exec] (ServiceManager) {/home/uibxn/Scripts/ServiceManager.sh}
	[exec] (Switch mouse) {/home/uibxn/Scripts/mouseSwitch.sh}
	[exec] (Toggle xscreensaver) {/home/uibxn/Scripts/ToggleXScreenSaver.sh}
[end]
[separator]
      [exec]   (tune) {/home/uibxn/Scripts/tune ask} 
      [exec]   (untune) {/home/uibxn/Scripts/untune}
[separator]
[submenu] (fluxbox)
      [config] (Configure) 
[submenu] (System Styles) {Choose a style...}
      [stylesdir] (/usr/local/share/fluxbox/styles) 
[end]
[submenu] (User Styles) {Choose a style...}
      [stylesdir] (~/.fluxbox/styles) 
[end]
      [workspaces] (Workspace List) 
[submenu] (Tools)
      [exec] (Screenshot) {scrot}
      [exec] (Screenshot area) {scrot -s}
      [exec] (Run) {fbrun } 
      [exec] (gtk-chtheme) {gtk-chtheme} 
[end]
      [exec] (Lock screen) {xscreensaver-command -lock} 
      [commanddialog] (Fluxbox Command) 
      [reconfig] (Reload config) 
      [restart] (Restart) 
      [exec] (About) {(fluxbox -v; fluxbox -info | sed 1d) | xmessage -file - -center} 
      [separator] 
      [exit] (Exit) 
[end]
[separator]
[exec] (Lock) {xscreensaver-command -lock} 
[endencoding]
[end]
```

And my keys file, which is bloated beyond repair. I don't even know all combos.
There are some interesting scripts after the "!other stuff" line.
```
# start tabbing windows together
OnTitlebar Control Mouse1 :StartTabbing
OnTitlebar Mouse2 :Lower

!mouse actions added by fluxbox-update_configs
OnTitlebar Double Mouse3 :Shade
OnTitlebar Mouse3 :WindowMenu

!mouse actions added by fluxbox-update_configs
OnWindow Mod1 Mouse1 :StartMoving
OnWindow Mod1 Mouse3 :StartResizing BottomRight

!mouse actions added by fluxbox-update_configs
OnDesktop Mouse1 :hideMenus
OnDesktop Mouse2 :workspaceMenu
OnDesktop Mouse3 :rootMenu
!OnDesktop Mouse4 :nextWorkspace
!OnDesktop Mouse5 :prevWorkspace
Mod4 Mouse3 :RootMenu
Mod4 Mouse2 :workspaceMenu
Mod4 Mouse1 :hideMenus


Mod1 F2 :ExecCommand gmrun
None F12 :ExecCommand aterm -tr +sb -bg black -fg white -sh 50
Mod4 F12 :ExecCommand aterm -tr +sb -bg black -fg white -sh 30

!custom menus
Shift Menu :CustomMenu ~/.fluxbox/menus/music
Control Menu :CustomMenu ~/.fluxbox/menus/places
Mod4 Menu :RootMenu
!end custom menus

!window management
None F10 :MaximizeWindow
Mod4 F10 :Fullscreen
Control F10 :ToggleDecor
None F11 :MinimizeWindow
Control F11 :Shade
Mod1 F4 :Close
Mod1 Tab :NextGroup
Control Tab :NextTab
Mod4 W :ToggleCmd {MacroCmd {ResizeTo 1280 750} {MoveTo 0 0}} {MacroCmd {ResizeTo 1280 800} {MoveTo 0 0}}
Mod4 plus :RaiseLayer
Mod4 minus :LowerLayer
!Move to prev/next workspace WITH the window
Control Mod4 Left  :MacroCmd {StickWindow} {PrevWorkspace} {StickWindow}
Control Mod4 Right :MacroCmd {StickWindow} {NextWorkspace} {StickWindow}
!end window management

!workspaces
Mod4 Right :NextWorkspace
Mod4 Left :PrevWorkspace
Mod4 F1 :SendToWorkspace 1
Mod4 F2 :SendToWorkspace 2
Mod4 F3 :SendToWorkspace 3
Mod4 F4 :SendToWorkspace 4
None F1 :Workspace 1
None F2 :Workspace 2
None F3 :Workspace 3
None F4 :Workspace 4
!Send the window to workspace and go there
Control Mod4 F1 :MacroCmd {SendToWorkspace 1} {Workspace 1}
Control Mod4 F2 :MacroCmd {SendToWorkspace 2} {Workspace 2}
Control Mod4 F3 :MacroCmd {SendToWorkspace 3} {Workspace 3}
Control Mod4 F4 :MacroCmd {SendToWorkspace 4} {Workspace 4}
!end workspaces

!mpd
None F6 :ExecCommand mpc prev
None F8 :ExecCommand mpc next
!None F7 :ExecCommand mpc toggle
None F7 :ExecCommand /home/uibxn/Scripts/dock/mpd/toggle
Mod4 F6 :ExecCommand mpc seek -00:00:05
Mod4 F8 :ExecCommand mpc seek +00:00:05
Mod4 V :ExecCommand /home/uibxn/Scripts/setVolume
Mod4 + :ExecCommand amixer sset PCM 10%+
Mod4 - :ExecCommand amixer sset PCM 10%-
!end mpd

!other stuff
Mod4 Y :ExecCommand rox
Mod4 A :ExecCommand rox /home/uibxn/Apps
Mod4 Q :ExecCommand rox /home/uibxn/Downloads
Mod4 S :ExecCommand catfish
Mod4 F :ExecCommand /home/uibxn/Scripts/dock/unicon Firefox firefox last
Mod4 E :ExecCommand /home/uibxn/Scripts/dock/mail/thunderbird
Control Mod4 E :ExecCommand thunderbird -compose
Control Shift E :ExecCommand /home/uibxn/Scripts/dock/checkForNew true
Mod4 L :ExecCommand leafpad
Control Mod4 L :ExecCommand Edit
Control Mod4 Q :ExecCommand xkill -button 1
Mod4 M :ExecCommand /home/uibxn/Scripts/mouseSwitch.sh
Mod4 R :ExecCommand /home/uibxn/Scripts/setWinTitle
Mod4 T :EXecCommand /home/uibxn/Scripts/dock/unicon Sonata "/home/uibxn/Scripts/tune ask"
Control Mod4 P :ExecCommand /etc/acpi/powerbtn.sh
Control Mod1 L :ExecCommand xscreensaver-command -lock
None Print :ExecCommand scrot
Mod4 C :ExecCommand osmo -cal


```

---

### Post by easybake on 2008-11-09
> **spupy said:**
> Can you tell me what theme are you using? I just put that same wallpaper today and wondered for a good fluxbox theme to go with it.

It's a modified version of the Mire Blue Theme. I changed up the pixmap buttons. (The maximize button is still there)

---

### Post by stanca on 2009-08-23
Here's mine too:;)
```
[begin] (fluxbox)
   [exec] (Shell) {xterm} </home/stanca/.icons/Cryo64-Mixed/apps/terminal.png>
   [exec] (Browser) {firefox} </home/stanca/.icons/Cryo64-Mixed/apps/web-browser.png>
   [exec] (File Manager) {pcmanfm} </home/stanca/.icons/Cryo64-Mixed/apps/nautilus.png>
   [exec] (Package Manager) {synaptic} </home/stanca/.icons/Cryo64-Mixed/apps/synaptic.png>
[include] (/etc/X11/fluxbox/fluxbox-menu)
   [exec] (Reboot) {shutdown -r now}
   [exec] (Shutdown) {shutdown -p now}
[end]
```
And this is my conky script:

---

### Post by tweaksource on 2010-01-09
This may be an old thread, but I'm a new fluxbox usr and I am HOOKED!!!

I'll probably never use Gnome or KDE again (XFCE maybe, and I do use thunar because of the Configurable Actions and thunar-volman, although it does need tabs :(  )

Fluxbox rocks! Window tabbing is the bees knees!!!

Anyway, here's my ~./fluxbox/keys file:

```

# click on the desktop to get menus
OnDesktop Mouse1	:HideMenus
OnDesktop Mouse2	:Exec fbrun
OnDesktop Mouse3	:RootMenu

# scroll on the desktop to change workspaces
OnDesktop Mouse4	: PrevWorkspace
OnDesktop Mouse5	: NextWorkspace

# alternate workspace change
OnDesktop Mod1 Mouse1	:PrevWorkspace
OnDesktop Mod1 Mouse3	:NextWorkspace

# scroll on the toolbar to change workspaces
OnToolbar Mouse4	:PrevWorkspace
OnToolbar Mouse5	:NextWorkspace

# alt + left/right click to move/resize a window
OnWindow Mod1 Mouse1	:MacroCmd {Raise} {Focus} {StartMoving}
OnWindow Mod1 Mouse3	:MacroCmd {Raise} {Focus} {StartResizing NearestCorner}

# middle click a window's titlebar and drag to attach windows
OnTitlebar Mouse2	:StartTabbing

# double click on the titlebar to shade
OnTitlebar Double Mouse1 :Shade

# right click on the titlebar for a menu of options
OnTitlebar Mouse3	:WindowMenu

# alt-tab
Mod1 Tab		:NextWindow {groups}
Mod1 Shift Tab		:PrevWindow {groups}

# cycle through tabs in the current window
Mod4 Tab		:NextTab
Mod4 Shift Tab		:PrevTab

# go to a specific tab in the current window
Mod4 1			:Tab 1
Mod4 2			:Tab 2
Mod4 3			:Tab 3
Mod4 4			:Tab 4
Mod4 5			:Tab 5
Mod4 6			:Tab 6
Mod4 7			:Tab 7
Mod4 8			:Tab 8
Mod4 9			:Tab 9

# open a terminal
Mod1 F1			:Exec xfce4-terminal

# open a dialog to run programs
Mod1 F2			:Exec fbrun

# volume settings, using common keycodes
# if these don't work, use xev to find out your real keycodes
Control Mod4 Up		:Exec amixer sset Master,0 1+
Control Mod4 Down	:Exec amixer sset Master,0 1-
160			:Exec amixer sset Master,0 toggle

# current window commands
Mod1 F4			:Close
Mod1 F9			:Minimize 
Mod1 F10		:Maximize
Mod1 F11		:Fullscreen

# open the window menu
Mod1 space		:Workspace
Menu

# exit fluxbox
Control Mod1 Delete	:Exit

# change to a specific workspace
Control F1		:Workspace 1
Control F2		:Workspace 2
Control F3		:Workspace 3
Control F4		:Workspace 4
Control F5		:Workspace 5
Control F6		:Workspace 6
Control F7		:Workspace 7
Control F8		:Workspace 8
Control F9		:Workspace 9
Control F10		:Workspace 10
Control F11		:Workspace 11
Control F12		:Workspace 12

# send the current window to a specific workspace
Mod4 F1		:SendToWorkspace 1
Mod4 F2		:SendToWorkspace 2
Mod4 F3		:SendToWorkspace 3
Mod4 F4		:SendToWorkspace 4
Mod4 F5		:SendToWorkspace 5
Mod4 F6		:SendToWorkspace 6
Mod4 F7		:SendToWorkspace 7
Mod4 F8		:SendToWorkspace 8
Mod4 F9		:SendToWorkspace 9
Mod4 F10	:SendToWorkspace 10
Mod4 F11	:SendToWorkspace 11
Mod4 F12	:SendToWorkspace 12

# send the current window and change to a specific workspace
Control Mod4 F1 :TakeToWorkspace 1
Control Mod4 F2 :TakeToWorkspace 2
Control Mod4 F3 :TakeToWorkspace 3
Control Mod4 F4 :TakeToWorkspace 4
Control Mod4 F5 :TakeToWorkspace 5
Control Mod4 F6 :TakeToWorkspace 6
Control Mod4 F7 :TakeToWorkspace 7
Control Mod4 F8 :TakeToWorkspace 8
Control Mod4 F9 :TakeToWorkspace 9
Control Mod4 F10 :TakeToWorkspace 10
Control Mod4 F11 :TakeToWorkspace 11
Control Mod4 F12 :TakeToWorkspace 12


```

and ~/.fluxbox/menu:

```

# My fluxbox menu file RAWKS!!!

[begin] (Fluxbox)

    [exec] (Command) {fbrun} </usr/share/wbar/iconpack/wbar.osx/gnome-run.png>	
    [exec] (PcMan) {pcmanfm} </usr/share/wbar/iconpack/wbar.osx/48/file-manager.png>
    [exec] (Xfe) {xfe} </usr/share/wbar/iconpack/wbar.osx/computer.png>
    [exec] (Thunar) {thunar} </usr/share/icons/hicolor/48x48/apps/Thunar.png>
    [exec] (Root File Manager) {gksu thunar} </usr/share/wbar/iconpack/wbar.osx/gnome-system-config.png>
    [exec] (Terminal) {xfce4-terminal} </usr/share/wbar/iconpack/wbar.osx/gnome-terminal.png>
    [exec] (SwiftFox) {swiftfox} </usr/share/wbar/iconpack/wbar.osx/firefox.png>
    [exec] (MEdit) {medit} </usr/share/wbar/iconpack/wbar.osx/editor.png>
    [exec] (Synaptic) {gksu synaptic} </usr/share/wbar/iconpack/wbar.osx/file-roller.png>
    [exec] (Gimp) {gimp} </usr/share/icons/hicolor/48x48/apps/gimp.png>
    [exec] (VirtualBox) {VirtualBox} </usr/share/wbar/iconpack/wbar.osx/48/gnome-multimedia.png>
    [exec] (VLC) {vlc} </usr/share/wbar/iconpack/wbar.osx/vlcCone.png>
    [exec] (Sagasu) {sagasu} </usr/share/wbar/iconpack/wbar.osx/gthumb.png>
    [exec] (Catfish) {catfish} </usr/share/wbar/iconpack/wbar.osx/gnome-searchtool.png>
    [exec] (Remote) {filerunner} </usr/share/wbar/iconpack/wbar.osx/shares.png>
    [exec] (Xkill) {xkill} </usr/share/wbar/iconpack/wbar.osx/xkill.png>
    
   # [submenu] (news) </usr/share/wbar/iconpack/wbar.osx/gnome-window-manager.png>
   #    [include] (~/.fluxbox/news)
   # [end]


[separator]
     

	[submenu] (Debian Menu) </usr/share/pixmaps/debian-logo.png>
		[include] (/etc/X11/fluxbox/menudefs.hook)
	[end]

[separator]

	[submenu] (Backgrounds)
		 [wallpapers] (/usr/share/backgrounds)
		 [wallpapers] (~/.fluxbox/backgrounds)
		 #[wallpapers] (~/misc/wallpapers)
	[end]

[separator]

   [config] (Configuration) </usr/share/wbar/iconpack/wbar.osx/48/gnome-system2.png>
   [submenu] (Styles) {}
      [stylesdir] (/usr/share/fluxbox/styles)
      [stylesdir] (~/.fluxbox/styles)
   [end]
   [workspaces] (Workspaces) </usr/share/wbar/iconpack/wbar.osx/workspace.png>
   [reconfig] (Reconfigure) </usr/share/wbar/iconpack/wbar.osx/48/palm-pilot-sync.png>
   [restart] (Restart) </usr/share/wbar/iconpack/wbar.osx/software-properties.png>
   [exec] (Reboot) {gksu reboot} </usr/share/wbar/iconpack/wbar.osx/timemachine.png>
   [exec] (Shutdown) {gksu shutdown now} </usr/share/wbar/iconpack/wbar.osx/gnome-session-halt.png>	
   [exit] (Exit) </usr/share/wbar/iconpack/wbar.osx/gnome-logout.png>

[end]


```

---

