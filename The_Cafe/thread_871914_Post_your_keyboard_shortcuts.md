---
title: "Post your keyboard shortcuts"
date: 2008-07-27
forum: The Cafe
---

### Post by markp1989 on 2008-07-27
im many window managers/Desktop environments you can set short cuts.

wondering what shortcuts people on this forum have set.

just post any short cuts you have set along with what they do 
 
Il start 

```
<Control><Alt><A> AMSN
<Control><Alt><C> Toggle Conky
<Control><Alt><F> Firefox
<Control><Alt><M> Mousepad
<Control><Alt><P> Pcmanfm
<Control><Alt><R> Rhythmbox
<Control><Alt><T> UXterm
<Control><Alt><V> VLC
```

---

### Post by billgoldberg on 2008-07-27
From my fluxbox setup (see link in signature).

```
OnDesktop Mouse1 :HideMenus
OnDesktop Mouse2 :WorkspaceMenu
OnDesktop Mouse3 :RootMenu
OnDesktop Mouse4 :NextWorkspace
OnDesktop Mouse5 :PrevWorkspace
Mouse8 :NextWorkspace # top button side mouse -> next workspace
Mouse9 :PrevWorkspace # bottom button side mouse -> prev workspace

Mod1 Tab :NextWindow 
Mod1 Shift Tab :PrevWindow

# Launch programs

F12 :ExecCommand xterm # opens a cli client
F11 :ExecCommand firefox # opens the firefox webbrowser client
F10 :ExecCommand thunar # opens the thunar file manager
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
F5 :Exec mpc stop # plays previous songs in playlist
F7 :Exec mpc toggle # pauses or play the song

# Visual

F1 :ToggleDecor # removes or adds window decoration


```

Mod1 = Alt

---

### Post by RiceMonster on 2008-07-27
Here's the one's I added to openbox:

Ctrl-Tab = Open a terminal
Windows-e = open Thunar
Windows-f = open Firefox
Alt-ESC = Minimize
Alt-F1 = Toggle-Maximize
ALt-F2 = gmrun

The rest are default openbox shortcuts.

---

### Post by cardinals_fan on 2008-07-27
```
<Alt><Shift>Enter: open a terminal
<Alt>P: open dmenu
<Alt><Shift>*#*: move window to workspace #
<Alt>*#*: move to workspace #
<Alt><Shift>Q: end session
```
It's like a little bit of Xmonad on Xfce :)

---

### Post by Kingsley on 2008-07-27
I know of gconf-editor, but is there another pain-free way to set application shortcuts in GNOME?

---

### Post by markp1989 on 2008-07-27
> **Kingsley said:**
> I know of gconf-editor, but is there another pain-free way to set application shortcuts in GNOME?

if your using compiz your can set it in ccsm.....thats what i did

if just gnome i dont know how to

---

### Post by urukrama on 2008-07-27
Here are my Openbox keybindings (taken from [a recent post on my blog]("http://urukrama.wordpress.com/2008/07/22/my-openbox-keybindings/")):

```
#########################
		## Launchers and Menus ##
		#########################
		Alt F1	:	root menu
		Alt F2	:	gmrun
		Alt F3	:	dmenu
		Alt F5	:	dmenu for configuration files
		Alt F6	:	client-combined-list

		Win F1	:	mousepad
		Win F2	:	notecase
		Win F3	:	xfce4-terminal (script)
		Win F4	:	thunar (script)
		Win F5	:	gmpc
		Win F6	:	epiphany
		Win F7	:	ooffice writer
		Win F8	:	opera (script)
		Win F9	:	stardict
		Win F10	:	gedit
		Win F11	:	gnome-alsamixer
		Win F12	:	Lock screen (xlock)

		Ctrl Alt Del :	htop

		#########
		## MPD ##
		#########
		Ctrl Alt space :	mpc toggle (with osdsh)
		Ctlr Alt Prior :	mpc next (with osdsh)
		Ctlr Alt Next :	mpc previous (with osdsh)

		####################
		## Volume control ##
		####################
		Ctrl Up	:	Volume up (PMC) (with osdsh)
		Ctrl Down:	Volume down (PMC) (with osdsh)
		Ctrl Shift Up :	Volume up (Master) (with osdsh)
		Ctrl Shift Down :	Volume down (Master) (with osdsh)
		Ctrl Alt End :	Volume mute (with osdsh)

		####################
		## Window actions ##
		####################
		**Win a**	 **Keychain**	Window actions
			m :	Toggle maximize full
			v :	Toggle maximize vertical
			h :	Toggle maximize horizontal
			i :	Iconify
			c :	Close
			s :	Toggle Shade
			t :	Toggle always on top
			b :	Send to bottom
			Shift b :	Toggle always below
			Shift l	: Send to normal layer
			Shift d	: Toggle omnipresent
			d : Toggle decorations
			l :	Lower, focus to bottom, unfocus
			p :	Send to previous workspace
			n :	Send to next workspace
			Shift p :	Follow to previous workspace
			Shift n	: Follow to next workspace

			**g****	sub-Keychain **GrowTo
				Left :	GrowToEdgeWest
				Right :	GrowToEdgeEast
				Down :	GrowToEdgeSouth
				Up :	GrowToEdgeNorth

		Win space :	Show client-menu

		#############
		## Openbox ##
		#############
		**Win o	Keychain	**Openbox actions
			r :	Reconfigure (with osdsh)
			c :	Edit rc.xml
			m :	Edit menu.xml
			s :	Shutdown (gmessage)
			e :	Exit/logout (gmessage)
			l :	Lock screen (xlock)

		###############
		## Worspaces ##
		###############
		Ctrl Alt Left :	Go to the workspace on the left
		Ctrl Alt Right :	Go to the workspace on the right
		Alt Shift Left :	Send window to the workspace on the left
		Alt Shift Right	: Send window to the workspace on the right

		Win Shift F1 :	Send window to workspace 1
		Win Shift F2 :	Send window to workspace 2
		Win Shift F3 :	Send window to workspace 3

		Win d	:	Show desktop

		######################
		## Window switching ##
		######################
		Alt Tab	:	Next window
		Alt Shift Tab :	Previous window
		Win Tab	:	Next window (all desktops)
		Win Shift Tab :	Previous window (all desktops)

		##################
		## Move Windows ##
		##################
		Win Left :	Move window left
		Win Right :	Move window right
		Win Down :	Move window down
		Win Up	:	Move window up

		Win Prior :	Move window to top right corner
		Win Next :	Move window to bottom right corner
		Win Home :	Move window to top left corner
		Win End	 :	Move window to bottom left corner

		####################
		## Resize Windows ##
		####################
		Alt Left :	Increase left edge
		Alt Right :	Increase right edge
		Alt Up	:	Increase top edge
		Alt Down :	Increase bottom edge

		Alt Shift Left :	Decrease right edge
		Alt Shift Right :	Decrease left edge
		Alt Shift  Up :	Decrease bottom edge
		Alt Shift Down :	Decrease top edge

		Alt F12	:	Toggle fullscreen

		Ctrl Alt d :	Toggle autohide dock
```

---

### Post by Alasdair on 2008-07-27
Here's my keybindings for Xmonad. I'm using the EZConfig module which allows for emacs style key notation. I still need to set up more shortcuts for launching applications, all these shortcuts really do is control the window manager.

```
prefix :: String -> String
prefix key = "C-e " ++ key

workspaceKeys :: [String]
workspaceKeys = ["<F2>","<F3>","<F4>","<F5>","<F6>","<F7>"]
 
myKeymap = [ (prefix "c", spawn term)
           , (prefix "<Return>", spawn term)
           , (prefix "S-w", spawn browser)
           , (prefix "f", sendMessage NextLayout)
           , (prefix "<Space>", sendMessage NextLayout)
           , (prefix "w", windows W.focusUp)
           , (prefix "r", windows W.focusDown)
           , (prefix "e", windows W.focusMaster)
           , (prefix "s", windows W.swapMaster)
           , (prefix "d", windows W.swapDown)
           , (prefix "3", windows W.swapUp)
           , (prefix "'", withFocused $ windows . W.sink)
           , (prefix "1", sendMessage Shrink)
           , (prefix "2", sendMessage Expand)
           , (prefix "k", kill)
           , (prefix "p", restart "xmonad" True) ]
           ++ --workspace stuff
           zip (map (prefix) workspaceKeys) 
               (map (withNthWorkspace W.greedyView) [0..])
           ++
           zip (map (\k -> prefix "g " ++ k) workspaceKeys)
               (map (withNthWorkspace W.shift) [0..])
           ++
           zip (map (\k -> prefix "m " ++ k) workspaceKeys)
               (map (\x -> withNthWorkspace W.shift x >>
                           withNthWorkspace W.greedyView x)
                    [0..])
```

---

### Post by red_Marvin on 2008-07-27
When using awesome, I launched apps with

Super + Enter -> Xfce4-terminal on current tag
Super + Ctrl +
"m" -> pidgin on tag 2
"c" -> xchat on tag 2
"w" -> firefox on current tag
"g" -> gedit on current tag
"t" -> thunar on current
"r" -> rhythmbox on tag 9

Since I use dvorak-se I'd press Super + Ctrl with my left hand and have all the other keys in reach for my right hand (I only have one Super key)

---

