---
title: "HOWTO: The power of Fluxbox keys"
date: 2007-11-19
forum: Tutorials
---

### Post by cknight on 2007-11-19
This how-to is all about discovering the power of key binding in Fluxbox, helping you understand the syntax and possibilities, and providing a wealth of examples to wet your appetite. I hope that it will entice those who never really thought much about using fluxbox's keys to give it a shot.  In my best attempt at encouraging you to use fluxbox keys, **I've even included a sample keys file below** with just about every flavor key-binding possible (including many of the examples in this how-to) so you can start playing around straight away.

All of the text below is based on V1.0 of Fluxbox.  However, most of this should work with previous versions.  If you want to upgrade to V1.0 (which has fixes to numerous bugs related to key binding) and its not in the repository, please check out [[COLOR="Blue"]Red Squirrel's how-to for compiling  fluxbox from source[/COLOR]]("http://ubuntuforums.org/showthread.php?t=371144"). This how-to has been tested on Edgy, but should work for all versions of Ubuntu.  

The driving force for this how-to came about after discovering that there are many users out there who have never modified their 'keys' file, **which is a crying shame!** Also, while the existing documentation out there is very thorough, its a bit like a dictionary.  Great for reference, but not so great on how to build useful sentences with all those words.

[SIZE="4"][COLOR="Red"]**Table of contents:**[/COLOR]
[LIST=1]
[*]Why use keys?
[*]The basics and simple examples
[*]How to identify keys on your keyboard (and mouse)
[*]More advanced examples and inspiration.
[*]Common Mistakes/Gotcha's/Troubleshooting
[*]Further info/Credits
[/LIST][/SIZE]

[SIZE="4"][COLOR="Red"]**1) Why use keys?**[/COLOR][/SIZE]

Quite simply, because its *so* fast and provides a level of power and customization not possible otherwise.  Mastering fluxbox's keys file will enhance your user experience and give you a raft of tools and actions not easily achievable through other methods, while still keeping fluxbox light and fast.  Using keys in a windowing environment is akin to using the CLI (Command Line Interface, aka Terminal).  Its not technically necessary most of the time and it has a definite learning curve (since you have to teach yourself to use the key-combination and not the mouse). However, the trade-off is that you can often do things a lot more easily and quickly with keys.  Some things (such as CustomMenu) just can't be reproduced easily (or even at all) through other methods.  Oh, and there's a definite cool-factor too :)

Use Firefox all the time?  Traditionally, people store a quick-launch icon on their toolbar, or a shortcut on their desktop to launch Firefox (or other app).  Or perhaps you've modified your menu file so that when you right-click on the desktop 'Firefox' appears in the root menu.  Not to bad, but thinking semantically, you have to get to your mouse, move the mouse pointer and concentrate and aim for the icon or menu item and click.  If your fluxbox setup doesn't have a desktop manager (e.g. default fluxbox) you have to go even further by finding a free bit of desktop to right click on to get your menu.  These icons, desktop shortcuts and menu items also have the downside of unnecessary 'clutter' which is arguably against the Fluxbox philosophy  of light-weight, simple and fast.  

Faster, simpler and more minimalistic is to bind a key combination, such as Mod4-f (Mod4 is the windows key), to launch Firefox.  Pressing these two keys will launch Firefox.  No icons needed, no menu items required and if you can touch-type, no concentration needed either.  

With the right key bindings you can do away with menus, icons, toolbars and window titlebars if you wanted, leaving you with a workspace consisting of your (optional!) background image only and still be more productive than your desktop/icon/menu/mouse bound friends.

But launching applications is just the beginning.  You can do much more with keys...


[SIZE="4"][COLOR="Red"]**2) The basics and simple examples**[/COLOR][/SIZE]

Right, enough yaking.  First things first.  Backup your existing keys file:
```
cp ~/.fluxbox/keys ~/.fluxbox/keys.backup
```

All Fluxbox key bindings are by default stored in ~/.fluxbox/keys.  Lines in this file beginning with a # or ! are considered comments and ignored by fluxbox.  Any changes to the keys file requires you to reconfigure fluxbox.  The easiest way to do this is via your root menu which should have a 'Reconfigure' option in there. Alternatively, you can use the following from the command line:

```
kill -s USR2 `xprop -root _BLACKBOX_PID | awk '{print $3}'`
```

The basic format of this file is as such:
```
<mod> [<mod> <mod>] key :command <operation>
```


Where <mod> is a modifier such as the Control (Ctrl), Windows (usually located between the control and alt keys), or Alt keys (often known to the fluxbox keys file as 'Control', 'Mod4'  and 'Mod1' respectively) and <key> is a normal key ('f', '3', 'F6', etc.).

<mod> itself is optional, in which case the 'None' keyword is used (e.g. None F12  :Exec someProgram)

Examples:
```
Control Mod4 f :Exec firefox
```

You can also assign multiple key sequences for actions (press Mod4 e, then Mod4 F1).  It is the complete sequence which launches Firefox here.
```
Mod4 e Mod4 F1 :Exec firefox
```

Thing you can assign to keys:

**- Window commands**
Allows you to do pretty much anything the window menu can do (e.g. the right-click menu on the window title-bar) with more control.  Think move, resize, minimize, maximize, shade, close, etc.  See [[COLOR="Blue"]this part of the fluxbox wiki[/COLOR]]("http://fluxbox-wiki.org/index.php/Keyboard_shortcuts#Currently_Focused_Window_Commands") for a full list of window commands. A few samples:
```
#The 'Close' command will close the active window.  The 'Fullscreen' key binding will toggle the window between its current and fullscreen state
Mod4 F4	 		:Close                               
Control Mod1 f	:Fullscreen 
```  

**- Fluxbox commands**
Commands specific to fluxbox such as "Restart", "Reconfigure" and "ReloadStyle". See [[COLOR="Blue"]this part of the fluxbox wiki[/COLOR]]("http://fluxbox-wiki.org/index.php/Keyboard_shortcuts#Window_Manager_Commands") for a full list of fluxbox commands.
```
#'Restart' will restart fluxbox.  'RootMenu' will pull up the root menu (e.g. what you get when you right-click on the desktop)
Mod4 Shift r	 :Restart 
Mod4 Shift m	 :RootMenu
```

**- Shell executable commands (programs, scripts, etc.)**.  These take the format of "<mod> <key> :Exec command".  Or the verbose "<mod> <key> :ExecCommand <command>"
where '<command>' is anything you can execute on the terminal command line.  
```
#Launches Firefox
MOd4 f			:Exec firefox

#Creates a backup of your keys file
Mod4 i    		:Exec cp ~/.fluxbox/keys ~/.fluxbox/keys.backup
```

**- Workspace commands**
Allows you to do pretty much anything the workspace menu can do (e.g. the middle click menu on the desktop). See [[COLOR="Blue"]this part of the fluxbox wiki[/COLOR]]("http://fluxbox-wiki.org/index.php/Keyboard_shortcuts#Workspace_Commands") for a full list of workspace commands
```
#Jump to workspace 2
Mod4 2	 		 :Workspace 2

#Minimize all windows on the current workspace
Control Mod4 s	 :ShowDesktop
```                 

**- Special commands**
Unique stuff like Marco (one key biding to multiple actions), Toggle (one key binding to two actions, toggling between them).  See [[COLOR="Blue"]this part of the fluxbox wiki[/COLOR]]("http://fluxbox-wiki.org/index.php/Keyboard_shortcuts#Special_Commands") for a full list of special commands
```
#Move AND resize the window
Control Mod1 r 	 :MacroCmd {MoveTo 15 15} {ResizeTo 1115 810} 

#Swap back and forth between 2 different sizes for the current window, anchored at the top left corner
Mod4 d 		 	 :ToggleCmd {ResizeTo 557 405} {ResizeTo 1115 810}
```

Finally, there is a utility called 'fluxkeys' which will 'help' build a keys file. [COLOR="Red"] [SIZE="3"]BEWARE[/SIZE][/COLOR]: [COLOR="Red"] This program will corrupt your keys file [/COLOR]changing any desktop mouse binding to 'Mousetop1' 'Mousetop2', etc.  Doing this will disable your ability to correclty use your mouse properly, which can be a real hinderance in Fluxbox if your other keys don't work yet.  Also, be aware that when you save your changes with fluxkeys, it will remove any comments and blank lines from your keys file.  Additionally, any command which fluxkeys doesn't recognize is removed from your keys file.  This includes keymodes, custom menus and others..  It also appeared to have truncated my keys file removing a large chunk at the end of my file. My advice is to stay away from this program and build your keys file in a text editor (nano, kate, gedit, etc.).


[SIZE="4"][COLOR="Red"]**3) How to identify keys on your keyboard (and mouse)**[/COLOR][/SIZE]

identify key names with 'xev'.  From a console, enter 'xev' on the command line.  This will then output to the screen any key events (Press, release, hold, etc) and mouse events.  Control-c quits 'xev' (or close the little white window). We're interested in the key events.  To find out the name of the key to use in the keys file, simply press the key you are interested in which will output event info to the terminal window.  In the example below, I pressed the multimedia back arrow key on my keyboard and got the following output:
```

	KeyRelease event, serial 32, synthetic NO, window 0xc00001,
    root 0x45, subw 0x0, time 4196058985, (353,248), root:(386,303),
    state 0x10, keycode 234 (keysym 0x1008ff26, XF86Back), same_screen YES,
    XLookupString gives 0 bytes:
    XFilterEvent returns: False
```
The important bits here are the "keycode 234 (keysym 0x1008ff26, XF86Back)" which uniquely identifies the key.  There are two ways we can identify the above key.  The first is the numeric keycode (234 in this case), or the key literal (XF86Back).  So, to assign this key to Firefox, we would use one of the following:
```
None 234 		:Exec firefox
None XF86Back	:Exec firefox
```
	
Note that some keys won't show up properly in xev if you've already got them bound in the keys file.
	
identify modifiers with 'xmodmap -pm'.  As you can see from the output of my 'xmodmap -pm' below, I have 8 modifiers.  From one of the fluxbox developers: "Fluxbox ignores any modifier containing num_lock or scroll_lock, and it also ignores the lock modifier, (although if caps_lock is bound to another modifier, like Mod3, it can be used)".  This leaves 5 usable ones.  Super_L (Mod4) is that Windows key found between the Ctrl and Alt keys.  ISO_Level3_Shift is labeled 'Alt Gr' on my keyboard and is located just to the right of my space bar.

```
xmodmap:  up to 3 keys per modifier, (keycodes in parentheses):

shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x6d)
mod1        Alt_L (0x40),  Alt_L (0x7d),  Meta_L (0x9c)
mod2        Num_Lock (0x4d)
mod3      
mod4        Super_L (0x7f),  Hyper_L (0x80)
mod5        Mode_switch (0x5d),  ISO_Level3_Shift (0x71),  ISO_Level3_Shift (0x7c)
```


For more information or help in setting up your multimedia keyboard, check out this very useful website:  [[COLOR="Blue"]http://gentoo-wiki.com/HOWTO_Use_Multimedia_Keys[/COLOR]]("http://gentoo-wiki.com/HOWTO_Use_Multimedia_Keys")

Many mice these days have '5' buttons.  That is, they have 2 primary buttons and a mouse wheel as follows:
Mouse1 = left click
Mouse2 = middle click (e.g. mouse wheel click)
Mouse3 = right click
Mouse4 = mouse wheel up
Mouse5 = mouse wheel down

Here's the output of 'xev' with mouse clicks:

```
ButtonPress event, serial 32, synthetic NO, window 0x1a00001,
    root 0x45, subw 0x0, time 475499353, (92,108), root:(693,462),
    state 0x10, button 5, same_screen YES
```

This identified a mouse wheel down event (button 5), but is known to the keys file as Mouse5.


[SIZE="4"][COLOR="Red"]**4) More advanced examples and inspiration.**[/COLOR][/SIZE]

Right.  Enough of the basics which are well covered elsewhere.  Lets look at some more useful and diverse examples. 

**-Audio**.  Use your keyboard to control the master volume.
```
#Volume.  Will lower or raise volume by 5%.  The third key binding will toggle mute.
None XF86AudioLowerVolume       :Exec amixer sset Master,0 5%-
None XF86AudioRaiseVolume       :Exec amixer sset Master,0 5%+
None XF86AudioMute              :Exec amixer sset Master,0 toggle
```


Most music players support command line interaction.  Some provide quite a rich command line interface allowing you to create a customized command only interface to do most things the music player GUI could have done.
```
#Amarok.  '-f' will forward one track. '-r' will reverse one track. '--pause' will toggle playback pause
#XMMS.	  'xmms -f' will forward one track. 'xmms -r' will reverse one track. 'xmms -t' will toggle pause/play. 'xmms -s' will stop.    
Mod4 Control Right              :Exec amarok -f
Mod4 Control Left               :Exec amarok -r
Mod4 Control Down               :Exec amarok --pause
```

**-On screen text display (and visually displaying volume changes)**  
'osdsh' is a little daemon which allows you to write text to an unshaped, unmanaged window on the desktop.  Think super-basic conky.  The effect is similar to TV volume/channel change updating on the screen in green text.  This utility has the ability to automatically monitor changes to the amixer Master volume and dynamically display a volume bar on your screen when it changes.  It can also display a clock or any two lines of text, really.  osdsh is controlled by the ostctl utility which can also start other monitoring daemons, including one for monitoring laptop batteries. The 'osdshconfig' utility will allow you to set a theme/style to your text and control other aspects like position and color.

To install (if required, you may already have this):
```
sudo aptitude install osdsh
```
Then create the following script to add to your fluxbox startup file.  Don't forget to change it to executable (chmod a+x <scriptname>).
```
#!/bin/bash
#Load the daemon
osdsh

#give it time to start
sleep 1

#Load a style/theme. Optional.  This is my theme and does NOT come with osdsh, so it will need changing to your own custom theme if you want to use one.
osdctl -S ~/.osdTheme

#Load the volume change daemon.  CAUTION:  THIS MAY SEND CPU TO 100% IN GUTSY GIBBON.  WORKS IN EDGY EFT. (SEE WORKAROUND BELOW)
osdctl -m 1
```

Then modify ~/.fluxbox/startup to include this script.  Make sure to put this before the fluxbox command at the bottom and don't forget to do this in the background (i.e. append '&' to the end of the script name).

Once osdsh is running, entering 
```
osdctl -s "Your text here" 
```
will output the text to the screen.

To display a second line of text, add a ',' to separate the two lines (e.g. "Your text,here").  There's also a small bug which sometimes displays random text on the second line (if you've only specified one line of text).  To get around this, use osdctl -s "text to display,"  forcing a blank second line.

Note that there appears to be an issue using the various daemons (volume and battery) in Gutsy Gibbon, though they work fine in Edgy Eft.  I haven't fully confirmed this yet, so keep an eye on your CPU if you use those.  Here's a workaround for the volume daemon so you can still get the same effect (where keys 160, 174 and 176 are my mute, volume down and volume up keys respectively):
```
None 160       :ToggleCmd {Exec amixer sset Master,0 toggle && osdctl -s "Mute on"} {Exec amixer sset Master,0 toggle && osdctl -s "Mute off"}
None 174	:Exec osdctl -b "Master Volume",$(amixer sset Master,0 5%-|grep "Front Left:"|cut -d "[" -f2|cut -d "%" -f1)
None 176	:Exec osdctl -b "Master Volume",$(amixer sset Master,0 5%+|grep "Front Left:"|cut -d "[" -f2|cut -d "%" -f1)

```

And here's a way to show battery power without the battery daemon:
```
osdctl -b "Battery Power",$(acpi|cut -d "," -f2|cut -d "%" -f1|cut -d " " -f2)
```

-show date and time - great if you don't use a panel or the slit for a clock
```
Mod4 KP_5					:Exec osdctl -s $(date)
#or define a date/time format for osdctl and use this instead.  2 is the number of seconds to show the clock.
Mod4 KP_6					:Exec osdctl -t 2
```

What else can this program do for your keys file?  Consider using it for visual feedback.  Reconfiguring fluxbox provides no visual feedback that its actually done anything, so how about this:
```
Mod4 Escape		 		 :MacroCmd {Exec osdctl -s "Reconfiguring,"} {Reconfigure}
```

Same goes for turning off your keys (though I haven't found a way to provide feedback when turning the keys back on):
```
Control Escape     		 :MacroCmd {Exec osdctl -s "Keys off,"} {keyMode KeysOff Control Escape} 
```

Other ideas include dynamic display of currently playing artist/album/etc.  Most music players offer a command line interface (possbily through add-ons) to access this information:
```
Mod4 p					:Exec osdctl -s "$(<command_to_get_music_info_string>)"
```

or notification of long running processes:
```
Mod4 p					:MacroCmd {osdctl -s "start"} {<start_long_running_process_command>} {osdctl -s "finished"}
```

I'm sure there are many other possibilities, but its truly worth it for the volume adjustment alone.

**-toggle conky**.  

I don't need conky most of the time, but now its available at a key press.  And when I'm finished the same key will turn it off.  Why waste resources when you don't need to?
```
Mod4 c							:ToggleCmd {Exec conky} {pkill conky}
```

**-show (Mod4 s ...) and edit (Mod4 e ...) Fluxbox config files.** Quick access to your fluxbox files in read-only or edit modes. NOTE:  The show lines require 'gmessage' which can be found in the repositories.  Alternatively, I believe you should have xmessage installed by default.  To use xmessage change 'gmessage' to 'xmessage' and '--file' to '-file'
```
Mod4 s Mod4 k   		 :Exec gmessage --file ~/.fluxbox/keys -buttons "Close" -font "monospace 8" -geometry 500x800 -default "Close" -center
Mod4 s Mod4 a   		 :Exec gmessage --file ~/.fluxbox/apps -buttons "Close" -font "monospace 8" -geometry 500x800 -default "Close" -center
Mod4 s Mod4 m   		 :Exec gmessage --file ~/.fluxbox/menu -buttons "Close" -font "monospace 8" -geometry 800x800 -default "Close" -center
Mod4 s Mod4 i   		 :Exec gmessage --file ~/.fluxbox/init -buttons "Close" -font "monospace 8" -geometry 500x800 -default "Close" -center
Mod4 s Mod4 o   		 :Exec gmessage --file ~/.fluxbox/overlay -buttons "Close" -font "monospace 8" -geometry 800x800 -default "Close" -center

#These require a $CONSOLE path variable to exist.  Alternatively, replace '$CONSOLE nano' below with the name of your favorite text editor.
#e.g. Mod4 e Mod4 k  		  :Exec gedit ~/.fluxbox/keys
Mod4 e Mod4 k   		 :Exec $CONSOLE nano ~/.fluxbox/keys
Mod4 e Mod4 a   		 :Exec $CONSOLE nano ~/.fluxbox/apps
Mod4 e Mod4 m   		 :Exec $CONSOLE nano ~/.fluxbox/menu
Mod4 e Mod4 i   		 :Exec $CONSOLE nano ~/.fluxbox/init
Mod4 e Mod4 o   		 :Exec $CONSOLE nano ~/.fluxbox/overlay
```

**-launch fbrun** (you can also prepopulate some or all of the text fbrun is to execute) This allows quick access to a command prompt/launcher
```
Mod4 r   :Exec fbrun
Mod4 r   :Exec fbrun -text "Pre loaded text string goes here"
```

**-Custom menus** (available since v1.0rc3).  This has real possibilities, especially for people like me who tend to forget less common key bindings.  The custom menu allows you to construct a new menu from scratch and attach it to a key binding.  It combines the power of key binding access with a focused GUI interface.  For example, I have a session menu (lock, reboot, shutdown, switch user, etc.), file manager menu (open my GUI file manager (Thunar) at various locations), and a music player menu (stop, play, rewind, forward, choose playlists, etc..).  See screenshots below for what these menus look like.

```
#The 'Menu' key is located to the left of my right Ctrl key on my keyboard and has a picture of a drop down menu on it.
Shift Menu					  :CustomMenu ~/.fluxbox/customMenus/Session
Control Menu		 		  :CustomMenu ~/.fluxbox/customMenus/Thunar
None Menu			 		  :CustomMenu ~/.fluxbox/customMenus/Amarok
```

Here's the menu code for the Amarok menu in the screenshot below
```
[begin] (Amarok) 
		 [exec] (Show OSD) {/usr/bin/dcop amarok player showOSD} <>
		 [exec] (Previous) {/usr/bin/dcop amarok player prev} </usr/share/icons/gnome/16x16/actions/player_rew.png>
		 [exec] (Stop) {/usr/bin/dcop amarok player stop} </usr/share/icons/gnome/16x16/actions/player_stop.png>
		 [exec] (Pause) {/usr/bin/dcop amarok player pause} </usr/share/icons/gnome/16x16/actions/player_pause.png>
		 [exec] (Play) {/usr/bin/dcop amarok player play} </usr/share/icons/gnome/16x16/actions/player_play.png>
		 [exec] (Next) {/usr/bin/dcop amarok player next} </usr/share/icons/gnome/16x16/actions/player_fwd.png>
   		 [submenu] (PlayLists) {}
		 		 [exec] (Newest Tracks) {/usr/bin/dcop amarok playlistbrowser loadPlaylist "Newest Tracks"} <>
		 		 [exec] (Never Played) {/usr/bin/dcop amarok playlistbrowser loadPlaylist "Never Played"} <>
		 		 [exec] (Most Played) {/usr/bin/dcop amarok playlistbrowser loadPlaylist "Most Played"} <>
		 		 [exec] (Electronica) {/usr/bin/dcop amarok playlistbrowser loadPlaylist "Electronica"} <>
		 		 [exec] (Chillout) {/usr/bin/dcop amarok playlistbrowser loadPlaylist "Chillout"} <>
		 		 [exec] (Favorite Tracks) {/usr/bin/dcop amarok playlistbrowser loadPlaylist "Favorite Tracks"} <>
		 		 [exec] (All Collection) {/usr/bin/dcop amarok playlistbrowser loadPlaylist "All Collection"} <>
		 		 [exec] (50 Random Tracks) {/usr/bin/dcop amarok playlistbrowser loadPlaylist "50 Random Tracks"} <>
		 [end]
 		 [separator]
		 [exec] (Quit) {/usr/bin/dcop amarok MainApplication-Interface quit} </usr/share/icons/gnome/16x16/actions/gtk-close.png>
[end]
```


**-Toggle between ShowDesktop and restore view**
```
Mod4 m :ToggleCmd {ShowDesktop} {DeIconify all originquiet}
```

**-Move and Resize Active Window to a set position and size.**  Setup a bunch of these to quickly arrange windows to any size/location you want
```
Mod1 u :MacroCmd {Moveto 10 5} {ResizeTo 1260 590}
```

**-Take to workspace.**  Take the active window and yourself to specified workspace.  This is great if you like using multiple workspaces (which you should!).  Often, one workspace gets quite cluttered.  Simple press the right key combo and you and your window are instantly transported to a nice clean workspace
```
Mod4 F3 	  :TakeToWorkspace 3
```


**-Dynamically modify the alpha (aka Transparency) of the window decor, or turn the decor on and off completely**
```
Mod4 Mod1 bracketright 	:SetAlpha +5 +5
Mod4 Mod1 bracketleft  	:SetAlpha -5 -5
Mod4 Mod1 0	 			:ToggleDecor
```


**-KeyMode** - Turn on and off sets of keys.    These help simplify the need to store lots of key bindings using the same set of keys.  Consider resizing and moving.  Its useful to use the arrow keys to do this, but you will quickly burn through modifiers attempting to do this.  Consider KeyModes instead.  For the keyset below, press Mod4 w Mod4 r  (w for window, r for resize). then use the arrows to resize your window.  When finished press Escape to remove these temporary keybinding.  Thus the same arrow/shift arrow keys can be used for both resizing and moving windows, but with different keymode activators. See [[COLOR="Blue"]the wiki entry[/COLOR]]("http://fluxbox-wiki.org/index.php/Keymodes") for more detail.

```
## ResizeMode (Window, Resize) - when Mod4 w Mod4 r is pressed, all keys except the arrow keys are disabled.  Press escape to exit this mode.
Mod4 w Mod4 r               :KeyMode ResizeMode
ResizeMode: None Up         :ResizeVertical -2
ResizeMode: None Down       :ResizeVertical +2
ResizeMode: None Left       :ResizeHorizontal -2
ResizeMode: None Right      :ResizeHorizontal +2

## MoveMode (Window, Move) - when Mod4 w Mod4 m is pressed, all keys except the arrow keys are disabled.  Press escape to exit this mode.
Mod4 w Mod4 m               :KeyMode MoveMode
MoveMode: None Up           :MoveUp 2
MoveMode: None Down         :MoveDown 2
MoveMode: None Left         :MoveLeft 2
MoveMode: None Right        :MoveRight 2
```

**-Toggle and SetResourceValue have nice possibilities of changing boolean values in the init file.**  However, a change to the resource values requires a reconfigure for them to take effect.  Unfortunately, reconfiguring within a toggle command resets the toggle command, meaning you'll never make it to the 'second' toggle.  This 'feature' may get fixed in an upcoming SVN/GIT release.  Get around this by binding two different keys:
```
#Hide/Show toolbar with 2 macro commands until Toggle/Reconfigure bug/feature is fixed
Mod4 comma		 		 :MacroCmd {SetResourceValue session.screen0.toolbar.visible false} {Reconfigure}
Mod4 period		 		 :MacroCmd {SetResourceValue session.screen0.toolbar.visible true} {Reconfigure}
```


**-Swap style and/or backgrounds with key**
Some days you might like your simple background and accompanying style, other days the flashy background and matching style.  Assign keys to swap these for you:
```
Mod4 shift 1			:Exec fbsetbg <path_to_image_including_imageName>
Mod4 shift 2			:SetStyle <path_to_style_file_or_style_directory>
#or combine both to change the entire look of your desktop at a key press (note: this won't work for you unless you have this background and style in those locations!)
Mod4 shift 1        :MacroCmd {SetStyle /usr/local/share/fluxbox/styles/bora_black} {Exec fbsetbg ~/.fluxbox/backgrounds/stOrmgreen--0}
```

**-Use wmctrl to manage applications.**  This little program will allow you to assign a key binding to an application such that if you press the key binding and the application is already running, then you will be taken to the instance already running, otherwise it will launch a new application.  Great for a quick way to jump to an already open instance of an application.  Find details here:  [[COLOR="Blue"]http://fluxbox-wiki.org/index.php/Keyboard_shortcuts#Using_wmctrl[/COLOR]]("http://fluxbox-wiki.org/index.php/Keyboard_shortcuts#Using_wmctrl")

**-Turn off key-bindings temporarily ** (e.g. if one of your keys conflicts with an application you are using).  Pressing Control-Escape will turn off all key-bindings until Control-Escape is pressed again.  This is useful if you use Xnest (which allows you to have multiple running X-sessions each in their own window) where you don't want Fluxbox intercepting key strokes meant for the other sessions.  Or perhaps an application uses the same keys as the ones you've bound.  Either way, its quick and easy to turn them off.  NOTE: The second line preserves the right-click root menu so you're not trapped without a way to get to your Fluxbox root menu.
```
Control Escape              :keyMode Xnest Control Escape
Xnext: Control Mod1 Mod4 Mouse3		:RootMenu
```

**-Screen shots** - Print the entire screen  (None Print) or just the active window (Mod4 Print).  The ~/screenshots directory must exist or this will fail.  These also require imageMagick package to be installed (which contains the import utility).  To install this use:
```
sudo aptitude install imagemagick
```
 Alternatively, install scrot and swap the correct screenshot commands below.
```
None Print     :Exec import -window root ~/screenshots/desktop_screenshot$(date +%F,%T).png
Mod4 Print     :Exec import -frame -window $(xprop _NET_ACTIVE_WINDOW -root | awk '{print $5}') ~/screenshots/active_window_screenshot$(date +%F,%T).png
```

**-Quick calendar** for this month, 3 months (previous month, this month and next month), or a full year
```
Mod4 KP_1 :Exec zenity --calendar --text=""
Mod4 KP_2 :Exec (date +'Today: %A %b %d';echo;cal -3)| gmessage --file - -buttons "GTK_STOCK_CLOSE" -font "monospace 8" -geometry 500x190 --borderless -default "GTK_STOCK_CLOSE" -center
Mod4 KP_3 :Exec (date +'Today: %A %b %d';echo;cal -y)| gmessage --file - -buttons "GTK_STOCK_CLOSE" -font "monospace 8" -geometry 500x525 --borderless -default "GTK_STOCK_CLOSE" -center

```
**-Get root menu anywhere with the mouse.**  If you like to use the mouse right-click to pull up the root menu, add this to your keys file.  Now you can pull up a root menu anywhere without having to hunt for some free desktop space.
```
Mod4 Mouse3			:RootMenu
```

**-Turn on power-save mode on the monitor**  This will blank your monitor and put it into power save mode.  I also use this on my laptop to activate the turn monitor off when the lid closes.  Run 'xev' to find out what key binding to use for laptop lid closure.
```
#Keyboard controlled turn monitor off
None Pause		 		 :Exec xset dpms force off

#214 is the keycode associated with my laptop lid closure/opening
None 214	                           :Exec xset dpms force off

```

One final keyboard/mouse shortcut I'll point out has nothing to do with the keys file.  I love fluxbox, but the styles I use have small resize handles and thin window titlebars.  This makes resizing and moving windows a pain, especially with my focus on mouse over policy (since if you overshoot the resize-handle you raise the window beneath it).  Try this instead:

Press  Alt and Left mouse click anywhere in a window, then drag the mouse.  This will now allow you to move the window
Press  Alt and Right mouse click anywhere in a window, then drag the mouse.  This will now allow you to resize the window (anchored at the top left corner).


[SIZE="4"][COLOR="Red"]**5) Common Mistakes/Gotcha's/Troubleshooting**[/COLOR][/SIZE]

If you plan on making changes to your keys file, I'd recommend turning on logging in fluxbox. This will output (by default) a log file to ~/.fluxbox/log which will tell you if fluxbox failed to bind any of the keys in your file.  Very handy if your keys file is large like mine and you accidentally bind an action to an identical key sequence.  To turn on logging, look at the last few lines of ~/.fluxbox/startup.  There should already be a commented out line which contains the correct command to turn on logging.  Simply comment out the current non-logging line and uncomment out the logging line.  Be aware, however, that if you've compiled fluxbox from source, the path to fluxbox may not be correct in the logging line.  So make sure that the path of your new fluxbox command matches the same path as the one you've just commented out.

```
#Executable for logging:  exec <path_to_fluxbox_executable> -log "<path_to_log_file>"
#This is MY path to fluxbox.  Yours will be different if you haven't compiled it from source.
exec /usr/local/bin/fluxbox -log "/home/cknight/.fluxbox/log"
```

If you get stuck and truly muck up your keys file, you may find yourself in a situation where you can't access your root menu to reconfigure any changes you make.  Or maybe you can't even launch a terminal to make the changes!  To fix this, press Ctl-Alt F1 to access a virtual terminal, log in, and type:
```
nano ~/.fluxbox/keys
``` at the command prompt if you need to edit your keys file, or perhaps restore the old keys file from a backup copy.  In either case, after making corrections or restoring backups, type
```
kill -s USR2 `xprop -root _BLACKBOX_PID | awk '{print $3}'`
	OR (if you have session.screen<N>.allowRemoteActions set to true in your init file)
fluxbox-remote "Reconfigure"
``` to force fluxbox to reconfigure.  Ctl-Alt F7 should take you back to the fluxbox GUI and your right-click root menu should now hopefully be back and working (assuming you fixed the problem!).  This command isn't available on all fluxbox versions.

Here are a list of things which might go wrong with your keys.  Heh, I've made most of these :)

[LIST=1]
[*]Try to avoid these syntax pitfalls:
[LIST]
[*]```
Mod4 f 	: Exec firefox
```  Make sure there are no spaces between the ':' and the start of the action otherwise you're biding won't work
[*]```
Mod4 f:Exec firefox
```  Make sure there *is* at least one space between the shortcut key ('f' in this instance) and the ':'
[*]```
Mod4 f 	:Exec "firefox"
```  Though double quotes (") appear to work on some commands, but they won't on all.  Leave quotes out of the command, they aren't necessary.
[/LIST]

[*] Careful to not use the same key combo.  In this scenario, fluxbox will discard the second key mapping as Mod4 f is already bound.
```
Mod4 f  :Exec firefox
Mod4 f Mod4 1 :Exec Thunar
```

[*] Avoid using Mousetop1, Mousetop2, etc. in your keys file.  These are put there by fluxkeys (see the warning about this program above) and cause fluxbox problems with your mouse clicks.  To fix this, change these to Mouse1, Mouse2, etc.

[*] Key literals from 'xev' are case sensitive.  So, 'Backspace' is not the same as 'BackSpace', 'backspace', etc.

[*] Applications to launch are case sensitive.  'Firefox' won't work because the actual command is 'firefox'.  Try testing any command on the command line to ensure it works.

[*] Some key combinations just don't work.  I setup one combination where the modifiers worked with other keys, the key worked with other modifiers and the command to execute worked with other combinations.  Moral of the story, if it just won't work, try a different key combination/binding

[*] Perhaps avoid Control Backspace or Mod1 Backspace as a binding, since you might, like me :) accidentally  press Control Mod1 Backspace instead which restarts X.  Oops!

[*] If you have emacs-style multiple key bindings specified (e.g. Mod4 f Mod4 a :Exec firefox) in your keys file and at some point you find that none of your key bindings work, try pressing escape.  You may have accidentally triggered Mod4 f and Fluxbox is waiting for a valid completion of the sequence.  Escape should cancel multi-bound sequences.

[*] It appears that applications will override your keys file, so be sure to choose safe key combinations.  E.g. Amarok binds 'Mod4 m' to mute, overriding my key-binding to launch my mail program.  To fix this I just turned off all the key bindings in Amarok, since I've rebound them in fluxbox anyway.

[*] Reconfiguring will reset all of your toggles back to the first state, so if a toggle doesn't do what you think it should, keep this in mind.  In particular, avoid placing the reconfigure command within a toggle, as this will continuously  reset the toggle.
[/LIST]


[SIZE="4"][COLOR="Red"]**6) Further info/Credits**[/COLOR][/SIZE]
[[COLOR="Blue"]fluxbox wiki[/COLOR]]("http://fluxbox-wiki.org/index.php/Fluxbox-wiki") -  some good how-to articles and more documentation on the keys file
fluxbox man page - 'man fluxbox' - one of the best documented man pages I've seen, this covers all of the commands available to the keys file in reasonable detail
[[COLOR="Blue"]fluxbox web documentation[/COLOR]]("http://fluxbox.sourceforge.net/docs/en/newdoc.keybindings.php") 
[[COLOR="Blue"]Multimedia keys tutorial[/COLOR]]("http://gentoo-wiki.com/HOWTO_Use_Multimedia_Keys") 
IRC channel on freenode: #fluxbox
[[COLOR="Blue"]How to install fluxbox from source[/COLOR]]("http://ubuntuforums.org/showthread.php?t=371144") 

Keys files from some of the folk closely related with Fluxbox
[[COLOR="Blue"]Tenr's key file[/COLOR]]("http://tenr.de/files/keys")
[[COLOR="Blue"]Mark Tiefenbruck's keys file[/COLOR]]("http://mark.tiefenbruck.org/fluxbox/configs/keys")
[[COLOR="Blue"]Mathias Gumz (aka akira) keys file[/COLOR]]("http://darkshed.net/files/rcs/fluxbox/keys.html")

[[COLOR="Blue"]Menu and other fluxbox customizations[/COLOR]]("http://ubuntuforums.org/showthread.php?t=371144")

Final note on the attached keys file.  This forum doesn't allow upload of files without extension.  So, the easiest thing to do was upload it as a tar file.  To use the keys file attached below (as a .tar file), please perform the following steps:
```
cd ~/.fluxbox
cp keys keys.original
cp <location_of_tar_file>/keys.tar ~/.fluxbox
tar -xvvf keys.tar

```

This will create a new keys file, overwriting your old one.  Don't forget to reconfigure or your keys file won't be updated.

Phew. You made it.  Thanks for reading! Please contribute any of your own key bindings below.  I'd love to see what things you've come up with.  I'm quite positive that there's a lot of untapped potential from keys out there, so show us what you've got :)

File list:
1) Screenshot of custom menus
2) Screenshot of osd (on screen display) of volume change
3) keys.tar - contains my (large!) 'keys' file.  See instructions above.

---

### Post by n8bounds on 2007-11-28
Just wanted to say thanks for what was obviously a lot of work. I didn't want to go as deep down the rabbit hole as you, but the defaults stunk so bad I had to do something. I read your post before I read the official wiki, which seemed make the wiki easier to understand...so thanks again!

Here's my key file after a few hours of reading and playing:
```

OnDesktop Mouse1        :HideMenus
OnDesktop Mouse2        :WorkspaceMenu
OnDesktop Mouse3        :RootMenu

Mod1 Tab                :NextWindow
Mod1 Shift Tab          :PrevWindow
Mod1 Control Right      :NextWorkspace
Mod1 Control Left       :PrevWorkspace
Control q               :Close
Control Alt d           :ToggleCmd {ShowDesktop} {DeIconify all originquiet}

Mod4 e                  :RootMenu
Mod4 l                  :ExecCommand "xlock -mode matrix"
Mod4 r                  :ExecCommand grun

None XF86AudioLowerVolume       :Exec amixer sset PCM,0 5%-
None XF86AudioRaiseVolume       :Exec amixer sset PCM,0 5%+
None XF86AudioMute              :Exec amixer sset PCM,0 toggle

```

---

### Post by cknight on 2007-11-29
> **n8bounds said:**
> Just wanted to say thanks for what was obviously a lot of work. I didn't want to go as deep down the rabbit hole as you, but the defaults stunk so bad I had to do something. I read your post before I read the official wiki, which seemed make the wiki easier to understand...so thanks again!

Glad it helped! The deep rabit hole, as it were, is mostly to show the breadth and depth of possibilities.  I hope others, like you, pick and choose what works best for them.

---

### Post by rjmdomingo2003 on 2007-12-01
How do you access the osdshconfig utility?

---

### Post by cknight on 2007-12-01
> **rjmdomingo2003 said:**
> How do you access the osdshconfig utility?

You should just be able to type this on the command line:
```
osdshconfig
```

If not give me a shout and I can post my theme

---

### Post by urukrama on 2007-12-02
Wow. Thank you very much. This is a great guide  -- plenty of good ideas!

---

### Post by cknight on 2007-12-02
> **urukrama said:**
> Wow. Thank you very much. This is a great guide  -- plenty of good ideas!

Thanks!  Glad it helped.  As an openbox user, I'd be curious to know how much of this is portable to openbox and how the key bindings compare.

---

### Post by rjmdomingo2003 on 2007-12-04
> **cknight said:**
> You should just be able to type this on the command line:
```
osdshconfig
```

If not give me a shout and I can post my theme
Yay! Got my osdtheme to work! Thanks cknight :popcorn:
I've attached a screenie of the osdtheme.. Master volume for now..

---

### Post by bodhi.zazen on 2007-12-06
> **cknight said:**
>  Wow 

Thank you for this detailed guide. I posted a link on the Fluxbuntu forums.

---

### Post by cknight on 2007-12-06
> **rjmdomingo2003 said:**
> Yay! Got my osdtheme to work! Thanks cknight :popcorn:
I've attached a screenie of the osdtheme.. Master volume for now..

Looks great!  I like how you've matched the color to your style...

---

### Post by cknight on 2007-12-06
> **bodhi.zazen said:**
> Thank you for this detailed guide. I posted a link on the Fluxbuntu forums.

Thanks :).  I've been meaning to give the heads up on this to the fluxbuntu community.

---

### Post by rjmdomingo2003 on 2007-12-06
> **cknight said:**
> Looks great!  I like how you've matched the color to your style...
I've modified my conky to match the osd: [http://ubuntuforums.org/attachment.php?attachmentid=52354&d=1196879846](http://ubuntuforums.org/attachment.php?attachmentid=52354&d=1196879846)

---

### Post by userundefine on 2007-12-06
What a great and thorough post.  I am a new convert to Fluxbox (so fast!) and this just adds to my liking it.  Thanks.

---

### Post by cknight on 2007-12-06
> **userundefine said:**
> What a great and thorough post.  I am a new convert to Fluxbox (so fast!) and this just adds to my liking it.  Thanks.
No problem.  Glad you found it useful.  I'm rather new to Fluxbox too and have found it really gives me a computing experience I've never had before, with speed and control I've not had before either!

---

### Post by cknight on 2007-12-10
Added a few updates to the tutorial:
1) Osdsh seems to be conflicting with something in Gutsy Gibbon causing it to shoot CPU to 100%.  I've added a few workarounds for the volume and battery daemon's to avoid this.
2) Added a warning about fluxkeys which can corrupt your keys file.
3) Added a new keybinding for turning the screen off when closing the laptop lid.
4) Added reminder that gmessage isn't installed by default, so you'll need to get it from the repositories.  In the meantime, feel free to use xmessage, its uglier cousin.

---

### Post by mark-t on 2007-12-17
Thanks for making this. I appreciate the effort. I've got some comments and answers for you.

> though I'd probably avoid using num_lock or caps_lock as modifiers

Actually, fluxbox ignores any modifier containing num_lock or scroll_lock, and it also ignores the lock modifier, (although if caps_lock is bound to another modifier, like Mod3, it can be used) so this statement could be stricter.

Your command to toggle conky is:
> :Toggle {Exec conky} {pkill conky}

That won't work. It needs to be ToggleCmd.

You suggested using the command: fluxbox-remote "Reconfigure". This requires the user to enable session.screen<N>.allowRemoteActions, which is disabled by default (for a reason). The right way to reconfigure fluxbox from the command line is by sending the process a USR2 signal: kill -s USR2 `xprop -root _BLACKBOX_PID | awk '{print $3}'` .

You mentioned that this command won't work: "None F11 None F12 :Exec firefox" . It should work, and it works for me, but actually the None "modifier" is never needed now, not even on the first one. It's assumed until you specify an actual modifier.

> Avoid using Mousetop1, Mousetop2, etc. in your keys file. I'm not sure where they come from and appear to be undocumented, but they cause problems with mouse clicks. Best change these to Mouse1, Mouse2, etc.

They come from fluxconf, which should really never be used, as it's outdated and tends to break things. It should probably be removed from the repos. Mouse1top, Mouse2top, etc. were never intended to work in fluxbox, but because of the way it parses the mouse buttons, they end up being equivalent to Mouse1, Mouse2, etc. The real problem is that the word "OnDesktop" gets removed, so fluxbox grabs them everywhere.

> Some key combinations just don't work. I setup one combination where the modifiers worked with other keys, the key worked with other modifiers and the command to execute worked with other combinations. Moral of the story, if it just won't work, try a different key combination/binding

Report them, please.

Again, thanks for your work. If you don't mind, I'd appreciate it if you did some work on the fluxbox-wiki keyboard shortcuts page. Forum threads get lost and outdated; the wiki is where this sort of documentation/howto should be.

---

### Post by cknight on 2007-12-18
> **mark-t said:**
> Thanks for making this. I appreciate the effort. I've got some comments and answers for you.

> though I'd probably avoid using num_lock or caps_lock as modifiers

Actually, fluxbox ignores any modifier containing num_lock or scroll_lock, and it also ignores the lock modifier, (although if caps_lock is bound to another modifier, like Mod3, it can be used) so this statement could be stricter.

Your command to toggle conky is:
> :Toggle {Exec conky} {pkill conky}

That won't work. It needs to be ToggleCmd.

You suggested using the command: fluxbox-remote "Reconfigure". This requires the user to enable session.screen<N>.allowRemoteActions, which is disabled by default (for a reason). The right way to reconfigure fluxbox from the command line is by sending the process a USR2 signal: kill -s USR2 `xprop -root _BLACKBOX_PID | awk '{print $3}'` .

You mentioned that this command won't work: "None F11 None F12 :Exec firefox" . It should work, and it works for me, but actually the None "modifier" is never needed now, not even on the first one. It's assumed until you specify an actual modifier.

> Avoid using Mousetop1, Mousetop2, etc. in your keys file. I'm not sure where they come from and appear to be undocumented, but they cause problems with mouse clicks. Best change these to Mouse1, Mouse2, etc.

They come from fluxconf, which should really never be used, as it's outdated and tends to break things. It should probably be removed from the repos. Mouse1top, Mouse2top, etc. were never intended to work in fluxbox, but because of the way it parses the mouse buttons, they end up being equivalent to Mouse1, Mouse2, etc. The real problem is that the word "OnDesktop" gets removed, so fluxbox grabs them everywhere.

> Some key combinations just don't work. I setup one combination where the modifiers worked with other keys, the key worked with other modifiers and the command to execute worked with other combinations. Moral of the story, if it just won't work, try a different key combination/binding

Report them, please.

Again, thanks for your work. If you don't mind, I'd appreciate it if you did some work on the fluxbox-wiki keyboard shortcuts page. Forum threads get lost and outdated; the wiki is where this sort of documentation/howto should be.

Thanks for your feedback Mark.  I've edited the original post above with your suggestions, comments and corrections.  I'd be happy to update the wiki and will be in touch in due course.  

Finally, many thanks to you and the other fluxbox developers for all your hard work on Fluxbox.  Its a truly fantastic window manager.

---

### Post by mark-t on 2007-12-20
More comments.  8)

> The easiest way to do this is via your root menu which should have a 'Reconfigure' option in there. Alternatively, you can use the following from the command line:

Well, actually, as you point out in the first section, a keybinding is the easiest way to do it. 8)

> (though I haven't found a way to provide feedback when turning the keys back on)

You might try something like this:
# just {KeyMode KeysOff} would bind "None Escape" for you -- we'll set it to something impossible instead
Control Escape     		 :MacroCmd {Exec osdctl -s "Keys off,"} {KeyMode KeysOff None 2384}
KeysOff: Control Escape :MacroCmd {Exec osdctl -s "Keys on,"} {KeyMode default}

You now have two sections about turning off keybindings. You should probably merge them.

---

### Post by mark-t on 2007-12-20
Hey, they replaced my smiley faces with pictures. I hate those things.  8)

---

### Post by TuxCrafter on 2008-02-01
Thanks for this howto it looks really great for fluxbox.

I am looking for a way to create short keys for Linux is a more general way detached from the desktop environment. 

So a solution that only depends on the xserver. This solution will then work on xfce,fluxbox,kde,gnome etcetera.

Does anybody have some idea's?

---

### Post by kaiju on 2008-02-02
@TuxCrafter:

you might want to take a look at xbindkeys
[http://hocwp.free.fr/xbindkeys/xbindkeys.html](http://hocwp.free.fr/xbindkeys/xbindkeys.html)


@cknight: thank you very much for your great howto :)

---

### Post by TuxCrafter on 2008-02-02
> **kaiju said:**
> @TuxCrafter:

you might want to take a look at xbindkeys
[http://hocwp.free.fr/xbindkeys/xbindkeys.html](http://hocwp.free.fr/xbindkeys/xbindkeys.html)


@cknight: thank you very much for your great howto :)

Yea, i know of xbindkeys i am using it now. But I was looking for a more direct way config xorg directly. I found a few how-to for gentoo that maps generic keys to xorg config maps but you cant connect commands to it. xbindkeys is the way to go on this moment until i find a better solution.

---

### Post by kaiju on 2008-02-02
oh, i see.
i sort of have a question though. i don't know about kde or non-blackbox-like window managers, but since gnome already has (though very limited) support for keybindings and fluxbox is so great at it, and besides there is xbindkeys, a very powerful app for its purpose (that you can load with any wm/de), why would you want to build your keybindings into x itself?

---

### Post by TuxCrafter on 2008-02-02
> **kaiju said:**
> oh, i see.
i sort of have a question though. i don't know about kde or non-blackbox-like window managers, but since gnome already has (though very limited) support for keybindings and fluxbox is so great at it, and besides there is xbindkeys, a very powerful app for its purpose (that you can load with any wm/de), why would you want to build your keybindings into x itself?

Now I at it this way, xbindkeys, is nice but it creates an other config file and an demon running al the time and needs to be loaded during boot.

X is already getting loaded and it also handles keys event. Isn't there a system in X than can easily created key bindings? If not then xbindkeys is the way.

[http://www.freedesktop.org/wiki/Software/XKeyboardConfig](http://www.freedesktop.org/wiki/Software/XKeyboardConfig)

---

### Post by eriqjaffe on 2008-02-12
So...following the tutorial on the first page of this thread, I got osdctl working with my old laptop, but I get volume level indicators on both the top and bottom of my screen:

[[IMG]http://img508.imageshack.us/img508/268/desktopscreenshot200802gp4.th.png[/IMG]](http://img508.imageshack.us/my.php?image=desktopscreenshot200802gp4.png)

The keys, script and startup information was copied verbatim from the example...ideally, I'd like it to just appear at the bottom of my screen (and, ideally, centered).  Not a big deal, but any tips would be appreciated

---

### Post by cknight on 2008-02-13
> **eriqjaffe said:**
> So...following the tutorial on the first page of this thread, I got osdctl working with my old laptop, but I get volume level indicators on both the top and bottom of my screen:

[[IMG]http://img508.imageshack.us/img508/268/desktopscreenshot200802gp4.th.png[/IMG]](http://img508.imageshack.us/my.php?image=desktopscreenshot200802gp4.png)

The keys, script and startup information was copied verbatim from the example...ideally, I'd like it to just appear at the bottom of my screen (and, ideally, centered).  Not a big deal, but any tips would be appreciated

My best guess is that your ~/.osdTheme file is corrupted.  Try replacing yours with this one and see if it fixes your problem:
```
#This osdsh theme was created for osdsh-0.6.0
#with Tkosdshconfig, by Lord Darth Moultak
dset(d,5)
dset(f,-*-lucidatypewriter-bold-*-*-*-*-120-*-*-*-*-*-*)
dset(C,red)
dset(k,black)
dset(o,0)
dset(O,0)
dset(x,0)
dset(y,0)
dset(l)
dset(t)
smix(d,5)
smix(f,fixed)
smix(C,green)
smix(k,black)
smix(o,0)
smix(O,0)
smix(x,0)
smix(y,0)
smix(l)
smix(t)
sppp(d,5)
sppp(f,fixed)
sppp(C,green)
sppp(k,black)
sppp(o,0)
sppp(O,0)
sppp(x,0)
sppp(y,0)
sppp(l)
sppp(t)
sapm(d,5)
sapm(f,fixed)
sapm(C,green)
sapm(k,black)
sapm(o,0)
sapm(O,0)
sapm(x,0)
sapm(y,0)
sapm(l)
sapm(t)
sclk(d,5)
sclk(f,fixed)
sclk(C,green)
sclk(k,black)
sclk(o,0)
sclk(O,0)
sclk(x,0)
sclk(y,0)
sclk(l)
sclk(t)
pdev(ppp0)
clkf(%H:%M:%S)
clck(0)
mixr(0)
apmw(0)
pppw(0)
connecting(,)
connected(,)
disconnected(,)
```

Good luck!

---

### Post by eriqjaffe on 2008-02-15
Thanks, that worked, now I only have the one line.  The last hurdle is positioning it the way I want - that can be done when I launch osdsh, right?

Also, a minor thing, but which line in the .osdTheme sets the shadow?  It's a bit tricky to read the text against some backgrounds, and a shadow offset by a pixel or two would go a long way into making it readable.

---

### Post by cknight on 2008-02-15
> **eriqjaffe said:**
> Thanks, that worked, now I only have the one line.  The last hurdle is positioning it the way I want - that can be done when I launch osdsh, right?

Also, a minor thing, but which line in the .osdTheme sets the shadow?  It's a bit tricky to read the text against some backgrounds, and a shadow offset by a pixel or two would go a long way into making it readable.

No problem.  Glad to help.  Try looking into 'osdshconfig' which will allow you to specify posiiton, shadown offset and other things too via a (rather crude) GUI.

---

### Post by eriqjaffe on 2008-02-16
> **cknight said:**
> No problem.  Glad to help.  Try looking into 'osdshconfig' which will allow you to specify posiiton, shadown offset and other things too via a (rather crude) GUI.That does the trick, although it took a bit of trial & error to get the drop shadow to work properly...but now I have it working and looking the way I want (or, at least, as best it can since the Fn keys on my ancient laptop don't seem to work at all).

By the way, this looks **really** interesting, especially since it allows for images and anti-aliased text...I'm not much of a programmer or a Perl guy, but this definitely sounds like it might be a nice next step for this sort of thing:

[http://www.ibm.com/developerworks/library/os-ghosd/index.html](http://www.ibm.com/developerworks/library/os-ghosd/index.html)

---

### Post by tmadsen on 2008-02-25
Thank you for this post cknight, very comprehensible. Keys in fb are so nice! :)

I have a question though. I see it is possible to launch applications in the center of the screen. Is it possible to move an active window to the center of the screen as well? As far as I can tell, there is no keys command for it, so perhaps someone knows of a command that does the same?

---

### Post by cknight on 2008-02-25
> **tmadsen said:**
> Thank you for this post cknight, very comprehensible. Keys in fb are so nice! :)

I have a question though. I see it is possible to launch applications in the center of the screen. Is it possible to move an active window to the center of the screen as well? As far as I can tell, there is no keys command for it, so perhaps someone knows of a command that does the same?

You're very welcome!  And I agree, Fluxbox keys are very nice indeed.

As for you suggestion, this can mostly be accomplished with a utility called wmctrl.
```
sudo aptitude install wmctrl
```

Here's the keybinding you would use to resize and relocate the active window:
```
Mod4 r :Exec wmctrl -r :ACTIVE: -e 0,100,100,500,500
```

In terms of the arguments, "-r :ACTIVE:" means target the active window.  You could also specify named windows instead. For the -e option, leave the 0 as it is.  100,100 is the x,y coordinates you wish to move the upper left corner of the window to and 500,500 is the width,height geomerty of the window.  If you want to keep the current geometry (or location), you would use -1 instead  (e.g. -e 0,100,100,-1,-1).

While you can't specificy "center" of the screen you can work this out by specifying exact location and geometry.

---

### Post by cl0ckwork on 2008-07-23
first of all, great how-to, it really helped me.

i found it after using fluxbox for a week or so and it really let me get into fluxbox.

one thing though, i have an HP multimedia laptop with music function keys on top.  is there any way to toggle play/pause with amarok instead of just a pause option?

---

### Post by mojoman on 2008-07-27
> **cl0ckwork said:**
> is there any way to toggle play/pause with amarok instead of just a pause option?

Yup. In keys-file, use:
```

[KEY] :ExecCommand amarok -t
```

---

### Post by val3xiv on 2008-09-03
> **rjmdomingo2003 said:**
> Yay! Got my osdtheme to work! Thanks cknight :popcorn:
I've attached a screenie of the osdtheme.. Master volume for now..

Hi!. May you attach your osdsh theme file?
Thanks in advance.

VAL3XIV

---

### Post by verdigris on 2008-09-07
Hello!

Thank you for the tutorial, it was definitely a lot less intimidating than the page on the Fluxbox wiki!

Following the link to the Gentoo Wiki on mapping raw scan codes to key codes (for multimedia keys), it says that I have to edit the /etc/conf.d/local.start file, but I have been unable to find it (I'm on Hardy). I've done a locate conf.d but found a lot of files and I'm not sure which one I should be editing. Any help would be greatly appreciated.

Thanks!

---

### Post by RedSquirrel on 2008-09-07
> **verdigris said:**
> Hello!

Thank you for the tutorial, it was definitely a lot less intimidating than the page on the Fluxbox wiki!

Following the link to the Gentoo Wiki on mapping raw scan codes to key codes (for multimedia keys), it says that I have to edit the /etc/conf.d/local.start file, but I have been unable to find it (I'm on Hardy). I've done a locate conf.d but found a lot of files and I'm not sure which one I should be editing. Any help would be greatly appreciated.

Thanks!
Try /etc/rc.local.

---

### Post by movaxes on 2008-12-30
Thanks a lot :D I now have a great keys file, I am still experimenting with it.

---

### Post by wowshailen on 2009-03-17
Thank you. I have changed some key sequences to standard ones such as Alt+Ctrl+D=show desktop, Alt+F4=Close.

How do I copy and paste on the console? First Ctrl+C does not work, and normally if I press this sequence, it breaks the operation.

Fedora's console allows me to configure Ctrl+Shift+C for Copy, etc..

Also, how do I change the Delete sequence from Ctrl+X to Del (key)?

Thank you.

---

### Post by pw_f100_220 on 2009-04-06
What _exactly_ does the BindKey function do, and can you give an example?  On the wiki it says: "BindKey will append key string and action to your keys file and bind the key."

 BindKey <key><value>: <action>       #creates an "on the fly" keycommand


Just curious and more in a mood to ask than figure it out...
Thanks!

---

### Post by mojoman on 2009-07-05
Hi,

I use the menu key to invoke the root menu. All very nice but I'd rather like to use the menu key too toogle the root menu, i.e. invoke it if it isn't visible and hide it if it is visible. Is that possible at all? I can't find anything in the documentation that indicates it but it would really be an improvement.

cheers
mojoman

---

### Post by Lampi on 2009-08-05
I experience something odd with keymappings in fluxbox version 1.0.0 on Debian/Lenny:

I simply like my left windows key to open the root menu, this is done with the following entry (and it works!)

```
None Super_L :RootMenu
```

the weird thing is: now the mouse keybinding (**None Mouse3top :RootMenu**) no longer works. It's like you could only use one keybinding to RootMenu at a time - wouldn't make much sense, but it's what I observe.

Can someone try this on his fluxbox, tell me if it works better with his version?

Lenny sometimes ships old packages, thus carrying nasty bugs fixed in later versions and so on ... I wouldn't mind compiling a newer version, just need to know if it is a bug that has been fixed in a more current version.

Thanks

---

### Post by cknight on 2009-08-05
> **Lampi said:**
> I experience something odd with keymappings in fluxbox version 1.0.0 on Debian/Lenny:

I simply like my left windows key to open the root menu, this is done with the following entry (and it works!)

```
None Super_L :RootMenu
```

the weird thing is: now the mouse keybinding (**None Mouse3top :RootMenu**) no longer works. It's like you could only use one keybinding to RootMenu at a time - wouldn't make much sense, but it's what I observe.

Can someone try this on his fluxbox, tell me if it works better with his version?

Lenny sometimes ships old packages, thus carrying nasty bugs fixed in later versions and so on ... I wouldn't mind compiling a newer version, just need to know if it is a bug that has been fixed in a more current version.

Thanks

I think what you are looking for (and may already have found) is this:
```
OnDesktop Mouse3 :rootMenu
```

Avoid fluxkeys like the plauge.  It will reek havoc on your keys file.  Mouse3Top is an old no longer supported format.

---

### Post by mojoman on 2009-10-17
> **mojoman said:**
> Hi,

I use the menu key to invoke the root menu. All very nice but I'd rather like to use the menu key too toogle the root menu, i.e. invoke it if it isn't visible and hide it if it is visible. Is that possible at all? I can't find anything in the documentation that indicates it but it would really be an improvement.

cheers
mojoman

Duh!

I found the solution (some time ago actually) but thought I'd post it just in case someone else have the same problem. It's fairly obvious so I don't know why I overlooked it. 

The menu key *on my system* is key 135, so I have:
```

None 135 :ToggleCmd {RootMenu} {HideMenus}
```

This toggles the menu nice and easy.

---

### Post by Rodney9 on 2010-01-16
Thank You cknight.

---

### Post by rayburn on 2011-06-14
Another big thank you for this HOWTO, I was actually looking for something else and stumbled across this accidentally. Most useful.

---

### Post by vomv1988 on 2012-03-01
Hey. You 4got 2 mention that, if u have some wickid shell scripting 5killz & wanna automate or script fluxbox internal commands, you can always, 4 example...

```
$ xdotool key Alt+F5
```...to arrange your windows, given that you add...

```
Mod1 F5 :ArrangeWindows
```...to your ~/.fluxbox/keys 1st, ofcourse.

---

### Post by kerryhall on 2012-04-12
This is awesome. This tutorial was extremely helpful for me, and I just found it today!

Question: Is there any community consensus on a generally productive set of keybindings? I guess I'm wondering more what folks are using day to day for productivity increases.

---

### Post by kerryhall on 2012-04-13
Trying to find the best key combo for open a new terminal. I think Ctrl+n might be a good one.

*are folks more productive with multiple tabs, multiple windows, or screen with regard to the terminal?
*using gnome terminal right now, but I don't like ctrl+shift+c to copy, would rather it be the standard ctrl+c, but that is already used of course. What do folk like to use here? What are really quick ways to copy and paste terminal text?
*whats the shutdown command for the keys file? 

Only been messing around with this for like 15 minutes so far and already I feel more productive haha. 

I think the next step in productivity would be to get a separate keyboard for *just* the macros and label the keys with pretty pictures! 

(lol one button for "killall -9 firefox")

---

### Post by chickenPie4breakfast on 2012-04-14
I dont get it - you can do key bindings in Gnome,and other window managers so why Fluxbox? The reason I stick with Gnome2 and havent used others is because although I have switched off nearly all compiz effects (I dont go for eycandy) I love the zoom feature and others desktop evironments seem to not have one or a very crude type of zoom.

---

### Post by kerryhall on 2012-04-19
I like fluxbox because it is waaayyy faster and uses waaayy less ram.

---

