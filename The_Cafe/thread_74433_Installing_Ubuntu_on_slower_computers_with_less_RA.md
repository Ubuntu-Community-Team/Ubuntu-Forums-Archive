---
title: "Installing Ubuntu on slower computers with less RAM"
date: 2005-10-11
forum: The Cafe
---

### Post by PatrickMay16 on 2005-10-11
Recently, I've been reading on this forum about people who've installed Ubuntu on computers with low RAM by doing the server installation, then doing something like this:

```

apt-get install xserver-xorg
apt-get install xfce4

```

I'd like to ask, which packages exactly do you need to install when you do that? I think there's more than just that needed to get it working. I searched the forum but I wasn't able to find the post that I had read about this in.
Also, for people who've done this, what were the results like?
Let's discuss this.

---

### Post by John.Michael.Kane on 2005-10-11
[http://www.ubuntuforums.org/showthread.php?t=42873](http://www.ubuntuforums.org/showthread.php?t=42873)
[https://wiki.ubuntu.com/Installation/LowMemorySystems?highlight=%28install%29](https://wiki.ubuntu.com/Installation/LowMemorySystems?highlight=%28install%29)
[http://www.ubuntuforums.org/showthread.php?t=30896](http://www.ubuntuforums.org/showthread.php?t=30896)

---

### Post by SilentCacophony on 2005-10-11
I'll bite. I keep a small partition alongside my breezy partition for a 'server' install, pretty much as a sandbox to try different setups with. It currently wieghs in at about 850 MB, with openbox, pypanel, firefox, thunderbird, rox-filer, leafpad, xterminal, menu and some other utilities and themes ([screenshot]("http://ubuntuforums.org/gallery/displayimage.php?imageid=997&original=1").) I use this when I feel like delving more into the inner workings of gnu/linux, which is quite often. Here's what I do:

After doing a 'server' install of Ubuntu, immediatlely fire up aptitude. The advantage of aptitude is that you can install and try out many different packages, and when you uninstall them, it cleans out any unneeded dependancies. You don't really need much other than the basics, if you're decent at editing configuration files.

Here are just a few of the possibilies I've tried:

menu - for 'debian menu' access, recommended
mc and htop - because I like them :)
xdm or wdm - for a light display manager, optionally
x-window-system-core - X!
xscreensaver - optionally
xterm or xterminal - two good terminal emulators, recommended

WWW Browser of choice (w3m is installed):
lynx, links, elinks, links2 - console
links2, dillo, firefox, mozilla - graphical

Email Client of choice (mutt is installed):
sylpheed, evolution, thunderbird, mozilla - graphical

File Manager of choice (the commandline is installed ;) ):
mc - console
worker, emelfm, gentoo, rox-filer - graphical

Finally, 'The Desktop', if you will:

openbox - really light
obconf - if you want a configuration frontend for openbox
fspanel, fbpanel, pypanel, or perlpanel - if you want a panel with openbox

blackbox, icewm, fluxbox, windowmaker - a bit heavier, but not much

xfce4 - also one that I like, with goodies of course

apmd, acpi, and/or acpid - if you miss any powermanagement

gtk-theme-switch - nice for setting gtk and gtk2 themes

Then any other utilities you want, installed as needed...

Even without X at all:
htop - sysmon, frienlier than top
mc - filemanager, reader, and editor
gpm - mouse support for console
screen - console multiplexer
centericq - messaging
mp3blaster - music
elinks - www
mutt - email (installed)
nano - editor (installed)

Of course, the are far more choices than what is listed here.

---

### Post by poofyhairguy on 2005-10-11
I'm on my Ubuntu lite right now. XFCE+kdm+Ubuntu base.

And it rocks.

---

### Post by YourSurrogateGod on 2005-10-11
[QUOTE=poofyhairguy]I'm on my Ubuntu lite right now. XFCE+kdm+Ubuntu base.

And it rocks.[/QUOTE]
Silly question, but what's kdm?

---

### Post by racecat on 2005-10-11
Try this post:

[http://www.ubuntuforums.org/showthread.php?t=30896&highlight=xfce+gnome](http://www.ubuntuforums.org/showthread.php?t=30896&highlight=xfce+gnome)

I loaded up a box with this and added the KDE, Gnome, and other apps that I like. I'm about to switch over to it full time.

KDM- Kde desktop manager? Like GDM, it is the session login screen. Somone correct me if I'm wrong.

Hope this helps,
Bill

---

### Post by poofyhairguy on 2005-10-11
[QUOTE=racecat]
KDM- Kde desktop manager? Like GDM, it is the session login screen. Somone correct me if I'm wrong.

Hope this helps,
Bill[/QUOTE]

Correct.

---

### Post by graabein on 2006-01-08
[QUOTE=SilentCacophony]I'll bite. I keep a small partition alongside my breezy partition for a 'server' install, pretty much as a sandbox to try different setups with. It currently wieghs in at about 850 MB, with openbox, pypanel, firefox, thunderbird, rox-filer, leafpad, xterminal, menu and some other utilities and themes.[/QUOTE]

Hi! I'm trying to do a similar install on an old laptop. I have little experience with setting up X and Openbox. Can you please post your resource files under ~/.config/openbox? I also want to know how you get pypanel running if that is okay.

Cheers!

---

### Post by SilentCacophony on 2006-01-14
[QUOTE=graabein]Hi! I'm trying to do a similar install on an old laptop. I have little experience with setting up X and Openbox. Can you please post your resource files under ~/.config/openbox? I also want to know how you get pypanel running if that is okay.

Cheers![/QUOTE]

Hi. Well, I use the **obconf** utility to configure OpenBox, but here's my ~/.config/openbox/rc.xml file contents, which is all that's in that folder:

```
<?xml version="1.0" encoding="UTF-8"?>
<!-- Do not edit this file, it will be overwritten on install.
        Copy the file to $HOME/.config/openbox/ instead. -->
<openbox_config xmlns="http://openbox.org/" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://openbox.org/                 file:///usr/share/openbox/rc.xsd">

<resistance>
  <strength>20</strength>
  <screen_edge_strength>30</screen_edge_strength>
</resistance>

<focus>
  <focusNew>yes</focusNew>
  <followMouse>yes</followMouse>
  <focusLast>no</focusLast>
  <focusDelay>500</focusDelay>
  <raiseOnFocus>no</raiseOnFocus>
</focus>

<theme>
  <name>curdled2</name>
  <titlelayout>NLIMC</titlelayout>
</theme>

<placement>
  <policy>Smart</policy>
</placement>

<desktops>
  <number>4</number>
  <firstdesk>1</firstdesk>
  <names>
    <name>one</name>
    <name>two</name>
    <name>three</name>
    <name>four</name>
  </names>
</desktops>

<resize>
  <drawContents>yes</drawContents>
</resize>

<dock>
  <position>TopLeft</position>
  <stacking>Top</stacking>
  <direction>Vertical</direction>
  <floatingX>0</floatingX>
  <floatingY>0</floatingY>
  <autoHide>no</autoHide>
  <hideDelay>300</hideDelay>
  <moveButton>A-Left</moveButton>
</dock>

<keyboard>
  <chainQuitKey>C-g</chainQuitKey>

  <keybind key="A-F10">openbox-themes
    <action name="MaximizeFull"/>
  </keybind>
  <keybind key="A-F5">
    <action name="UnmaximizeFull"/>
  </keybind>
  <keybind key="A-F12">
    <action name="ToggleShade"/>
  </keybind>
  <keybind key="C-A-Left">
    <action name="DesktopLeft"><wrap>no</wrap></action>
  </keybind>
  <keybind key="C-A-Right">
    <action name="DesktopRight"><wrap>no</wrap></action>
  </keybind>
  <keybind key="C-A-Up">
    <action name="DesktopUp"><wrap>no</wrap></action>
  </keybind>
  <keybind key="C-A-Down">
    <action name="DesktopDown"><wrap>no</wrap></action>
  </keybind>
  <keybind key="S-A-Left">
    <action name="SendToDesktopLeft"><wrap>no</wrap></action>
  </keybind>
  <keybind key="S-A-Right">
    <action name="SendToDesktopRight"><wrap>no</wrap></action>
  </keybind>
  <keybind key="S-A-Up">
    <action name="SendToDesktopUp"><wrap>no</wrap></action>
  </keybind>
  <keybind key="S-A-Down">
    <action name="SendToDesktopDown"><wrap>no</wrap></action>
  </keybind>
  <keybind key="C-A-d">
    <action name="ToggleShowDesktop"/>
  </keybind>
  <keybind key="A-F4">
    <action name="Close"/>
  </keybind>
  <keybind key="A-Tab">
    <action name="NextWindow"/>
  </keybind>
  <keybind key="A-S-Tab">
    <action name="PreviousWindow"/>
  </keybind>
  <keybind key="A-F7">
    <action name="Move"/>
  </keybind>
  <keybind key="A-F8">
    <action name="Resize"/>
  </keybind>
  <keybind key="A-F9">
    <action name="Iconify"/>
  </keybind>
  <keybind key="A-space">
    <action name="ShowMenu"><menu>client-menu</menu></action>
  </keybind>
</keyboard>

<mouse>
  <dragThreshold>3</dragThreshold>
  <doubleClickTime>200</doubleClickTime>

  <context name="Frame">
    <mousebind button="A-Left" action="Drag">
      <action name="Move"/>
    </mousebind>
    <mousebind button="A-Left" action="Click">
      <action name="Raise"/>
    </mousebind>
    <mousebind button="A-Left" action="Press">
      <action name="Focus"/>
    </mousebind>
    <mousebind button="A-Middle" action="Drag">
      <action name="Resize"/>
    </mousebind> 
    <mousebind button="A-Middle" action="Click">
      <action name="Lower"/>
    </mousebind>
    <mousebind button="A-Right" action="Press">
      <action name="ShowMenu"><menu>client-menu</menu></action>
    </mousebind>
    <mousebind button="A-Up" action="Click">
      <action name="DesktopPrevious"/>
    </mousebind>
    <mousebind button="A-Down" action="Click">
      <action name="DesktopNext"/>
    </mousebind>
    <mousebind button="C-A-Up" action="Click">
      <action name="SendToDesktopPrevious"/>
    </mousebind>
    <mousebind button="C-A-Down" action="Click">
      <action name="SendToDesktopNext"/>
    </mousebind>
  </context>
  <context name="Titlebar">
    <mousebind button="Left" action="Drag">
      <action name="Move"/>
    </mousebind>
    <mousebind button="Left" action="Click">
      <action name="Raise"/>
    </mousebind>
    <mousebind button="Left" action="Press">
      <action name="Focus"/>
    </mousebind>
    <mousebind button="Left" action="DoubleClick">
      <action name="ToggleShade"/>
    </mousebind>
    <mousebind button="Middle" action="Press">
      <action name="Lower"/>
    </mousebind>
    <mousebind button="Up" action="Click">
      <action name="Shade"/>
    </mousebind>
    <mousebind button="Down" action="Click">
      <action name="Unshade"/>
    </mousebind>
    <mousebind button="Right" action="Press">
      <action name="ShowMenu"><menu>client-menu</menu></action>
    </mousebind>
  </context>
  <context name="Handle">
    <mousebind button="Left" action="Drag">
      <action name="Move"/>
    </mousebind>
    <mousebind button="Left" action="Click">
      <action name="Raise"/>
    </mousebind>
    <mousebind button="Left" action="Press">
      <action name="Focus"/>
    </mousebind>
    <mousebind button="Middle" action="Press">
      <action name="Lower"/>
    </mousebind>
  </context>
  <context name="BLCorner">
    <mousebind button="Left" action="Drag">
      <action name="Resize"/>
    </mousebind>
    <mousebind button="Left" action="Press">
      <action name="Focus"/>
    </mousebind>
  </context>
  <context name="BRCorner">
    <mousebind button="Left" action="Drag">
      <action name="Resize"/>
    </mousebind>
    <mousebind button="Left" action="Press">
      <action name="Focus"/>
    </mousebind>
  </context>
  <context name="TLCorner">
    <mousebind button="Left" action="Drag">
      <action name="Resize"/>
    </mousebind>
    <mousebind button="Left" action="Press">
      <action name="Focus"/>
    </mousebind>
  </context>
  <context name="TRCorner">
    <mousebind button="Left" action="Drag">
      <action name="Resize"/>
    </mousebind>
    <mousebind button="Left" action="Press">
      <action name="Focus"/>
    </mousebind>
  </context>
  <context name="Client">
    <mousebind button="Left" action="Press">
      <action name="Focus"/>
      <action name="Raise"/>
    </mousebind>
    <mousebind button="Middle" action="Press">
      <action name="Focus"/>
    </mousebind>
    <mousebind button="Right" action="Press">
      <action name="Focus"/>
    </mousebind>
  </context>
  <context name="Icon">
    <mousebind button="Left" action="Press">
      <action name="Focus"/>
    </mousebind>
    <mousebind button="Right" action="Press">
      <action name="ShowMenu"><menu>client-menu</menu></action>
    </mousebind>
    <mousebind button="Left" action="Press">
      <action name="ShowMenu"><menu>client-menu</menu></action>
    </mousebind>
  </context>
  <context name="AllDesktops">
    <mousebind button="Left" action="Press">
      <action name="Focus"/>
    </mousebind>
    <mousebind button="Left" action="Click">
      <action name="ToggleOmnipresent"/>
    </mousebind>
  </context>
  <context name="Shade">
    <mousebind button="Left" action="Press">
      <action name="Focus"/>
    </mousebind>
    <mousebind button="Left" action="Click">
      <action name="ToggleShade"/>
    </mousebind>
  </context>
  <context name="Iconify">
    <mousebind button="Left" action="Press">
      <action name="Focus"/>
    </mousebind>
    <mousebind button="Left" action="Click">
      <action name="Iconify"/>
    </mousebind>
  </context>
  <context name="Maximize">
    <mousebind button="Left" action="Press">
      <action name="Focus"/>
    </mousebind>
    <mousebind button="Middle" action="Press">
      <action name="Focus"/>
    </mousebind>
    <mousebind button="Right" action="Press">
      <action name="Focus"/>
    </mousebind>
    <mousebind button="Left" action="Click">
      <action name="ToggleMaximizeFull"/>
    </mousebind>
    <mousebind button="Middle" action="Click">
      <action name="ToggleMaximizeVert"/>
    </mousebind>
    <mousebind button="Right" action="Click">
      <action name="ToggleMaximizeHorz"/>
    </mousebind>
  </context>
  <context name="Close">
    <mousebind button="Left" action="Press">
      <action name="Focus"/>
    </mousebind>
    <mousebind button="Left" action="Click">
      <action name="Close"/>
    </mousebind>
  </context>
  <context name="Desktop">
    <mousebind button="Up" action="Press">
      <action name="DesktopPrevious"/>
    </mousebind>
    <mousebind button="Down" action="Press">
      <action name="DesktopNext"/>
    </mousebind>
    <mousebind button="A-Up" action="Press">
      <action name="DesktopPrevious"/>
    </mousebind>
    <mousebind button="A-Down" action="Press">
      <action name="DesktopNext"/>
    </mousebind>
    <mousebind button="Left" action="Press">
      <action name="Focus"/>
      <action name="Raise"/>
    </mousebind> 
    <mousebind button="Middle" action="Press">
      <action name="ShowMenu"><menu>client-list-menu</menu></action>
    </mousebind> 
    <mousebind button="Right" action="Press">
      <action name="ShowMenu"><menu>root-menu</menu></action>
    </mousebind>
  </context>
  <context name="MoveResize">
    <mousebind button="Up" action="Press">
      <action name="DesktopPrevious"/>
    </mousebind>
    <mousebind button="Down" action="Press">
      <action name="DesktopNext"/>
    </mousebind>
    <mousebind button="A-Up" action="Press">
      <action name="DesktopPrevious"/>
    </mousebind>
    <mousebind button="A-Down" action="Press">
      <action name="DesktopNext"/>
    </mousebind>
  </context>
</mouse>

<menu>
  <!-- You can specify more than one menu file in here and they are all loaded,
       just don't make menu ids clash or, well, it'll be kind of pointless -->

  <!-- system menu files on Debian systems -->
  <file>/var/lib/openbox/debian-menu.xml</file>
  <file>debian-menu.xml</file>

  <!-- default menu file (or custom one in $HOME/.config/openbox/) -->
  <file>menu.xml</file>
</menu>

</openbox_config>

```

I find that the fonts in most of the openbox themes are small for my tastes, so I usually edit the font lines at the end of the *themerc* files in the theme folders for larger fonts. If you install the **openbox-themes** package, they will be in the */usr/share/themes* folder.

I like to start in console mode, and issue a 'startx' when/if I want X, so I made an ~/.xinitrc file to handle starting the necessary apps for that. A simple one:

```
eval `cat $HOME/.fehbg` &
pypanel &
exec openbox
```

That uses feh to set a backdrop image, starts pypanel, and finally openbox. Note the & symbol following the commands preceding openbox, so that the commands are forked to the background. You could use this to start other apps that you usally use automatically, as well.

As for pypanel, it requires hand-editing the config file: ~/.pypanelrc

```
#------------------------------------------------------------------------------
#
#                         PyPanel v2.3 Configuration
#
# This configuration file is a Python script that will be executed when
# PyPanel is started.  In order for PyPanel to start properly, make sure that
# this file contains proper Python formatting and no syntax errors.
#------------------------------------------------------------------------------
VERSION         = 2.3           # Config file version

#------------------------------------------------------------------------------
# Colors: Format is hex triplet - 0xrrggbb
#------------------------------------------------------------------------------
BG_COLOR        = "0xd6d6d6"    # Panel background and tinting color
TASK_COLOR      = "0x000000"    # Normal task name color 
FOCUSED_COLOR   = "0x1826de"    # Focused task name color
SHADED_COLOR    = "0x808080"    # Shaded task name color 
MINIMIZED_COLOR = "0x808080"    # Minimized task name color 
DESKTOP_COLOR   = "0x000000"    # Desktop name color
CLOCK_COLOR     = "0x000000"    # Clock text color
LINE_COLOR      = "0x606060"    # Vertical line color

#------------------------------------------------------------------------------
# Panel Spacing and Location Options: Measured in pixels
#------------------------------------------------------------------------------
P_LOCATION      = 1             # Panel placement: 0 = top, 1 = bottom
P_WIDTH         = 0             # Panel width: 0 = Use full screen width
P_START         = 0             # Starting X coordinate of the panel
P_SPACER        = 6             # Spacing between panel objects
P_HEIGHT        = 24            # Panel height

#------------------------------------------------------------------------------
# Icon Size Options: Measured in pixels
#------------------------------------------------------------------------------
I_HEIGHT        = 16            # Panel application icon height
I_WIDTH         = 16            # Panel application icon Width 
APPL_I_HEIGHT   = 24            # Application launcher icon height
APPL_I_WIDTH    = 24            # Application launcher icon width
TRAY_I_HEIGHT   = 24            # System tray icon height (usually 16 or 24)
TRAY_I_WIDTH    = 24            # System tray icon width  (usually 16 or 24)
                                # If TRAY_I_WIDTH is set to 0, then the
                                # width specified by the tray app will be used
                                
#------------------------------------------------------------------------------
# Panel Clock Format: 'man strftime' for detailed formatting options and help
#------------------------------------------------------------------------------
CLOCK_FORMAT    = "%Y-%m-%d %H:%M"    # Ex: 2004-09-25 17:45 

#------------------------------------------------------------------------------
# Clock Delay: Seconds between each clock update during periods of inactivity
#------------------------------------------------------------------------------
CLOCK_DELAY     = 20

#------------------------------------------------------------------------------
# Hidden Application List: Apps listed here will not be display on the panel
# The application name is its WM_CLASS name, use 'xprop' to find WM_CLASS
# Ex: ["xmms", "xine", "gDesklets"]
#------------------------------------------------------------------------------
HIDE_LIST       = []            
                   
#------------------------------------------------------------------------------
# Hidden Panel Size: Size of the panel when it's hidden/minimized
#------------------------------------------------------------------------------
HIDDEN_SIZE     = 2

#------------------------------------------------------------------------------
# Panel Text Font: This option takes either a traditional or Xft font string 
# Ex: "-schumacher-clean-medium-r-normal-*-12-*-*-*-*-*-*-*"
#     "aquafont-8" 
#------------------------------------------------------------------------------
FONT            = "bitstream vera sans-8"

#------------------------------------------------------------------------------
# Show All Applications: Show apps from all desktops or just the current
# 0: Disabled - Only applications on the current desktop will be displayed
# 1: Enabled  - Selected apps are moved to the current desktop
# 2: Enabled  - Current desktop is changed to the selected apps desktop
#------------------------------------------------------------------------------
SHOWALL         = 0             # 0, 1 or 2 - see descriptions above

#------------------------------------------------------------------------------
# Show Minimized/Iconified Applications: Show only minimized apps or all apps
# 0: Disabled - Show all applications on the panel
# 1: Enabled  - Show only minimized apps on the panel
#------------------------------------------------------------------------------
SHOWMINIMIZED   = 0

#------------------------------------------------------------------------------
# Application Icon List: List of custom icons for specific applications
# The application name is its WM_CLASS name, use 'xprop' to find WM_CLASS
#
# The "default" entry is used for applications with no icon.  If left "",
# PyPanel will use the default icon distributed with the source.
#
# Add entries using the following format -
#     "<application name>" : "<full path to icon>",
#------------------------------------------------------------------------------
ICON_LIST       = {
                   "default" : "",
                   "example" : "/usr/share/imlib2/data/images/audio.png",
                  }
                  
#------------------------------------------------------------------------------
# Application Launch List: Ordered list of icons and applications for the
#                          application launcher.
# 
# Add entries using the following format -
#     ("<executable>", "<full path to icon>")
#------------------------------------------------------------------------------
LAUNCH_LIST     = [
                   ("Terminal", "/home/brian/.icons/ROX/48x48/apps/gnome-terminal.png"),
                   ("firefox", "/home/brian/.icons/ROX/48x48/apps/xfce-internet.png"),
                   ("rox-filer", "/home/brian/.icons/ROX/48x48/apps/file-manager.png"),   
                  ]

#------------------------------------------------------------------------------
# Background Alpha/Shade Level: 0 (Fully Translucent) -> 255 (Fully Opaque)
# BG_COLOR is used for tinting
#------------------------------------------------------------------------------
SHADE           = 50

#------------------------------------------------------------------------------
# Misc. Options: 1 = Enabled/Yes, 0 = Disabled/No
#------------------------------------------------------------------------------
ABOVE           = 1             # Panel is always above other apps
APPICONS        = 1             # Show application icons
AUTOHIDE        = 0             # Autohide uses the CLOCK_DELAY timer above
SHOWLINES       = 0             # Show object seperation lines
SHOWBORDER      = 0             # Show a border around the panel

#------------------------------------------------------------------------------
# Desktop Names: Configure the names of your desktops
# If the option is [], PyPanel will attempt to use the desktop name specified
# by the XServer, if that fails it will use the desktop number as its name
# Ex. ["One", "Two", "Three", "Four", "Five", "Six", "Seven", "Eight"]
#------------------------------------------------------------------------------
DESKTOP_NAMES   = []

#------------------------------------------------------------------------------
# Panel Layout:       -----------------------------------
#                     [  1  ][  2  ][  3  ][  4  ][  5  ]
#                     -----------------------------------
#
# The panel layout is split into 5 sections numbered 1, 2, 3, 4 or 5 as shown
# in the diagram above.  Each of the following objects can be enabled by
# assigning it a section number or disabled by assigning it 0:
#------------------------------------------------------------------------------
DESKTOP         = 1             # Desktop name section
TASKS           = 3             # Task names section (cannot be disabled!) 
TRAY            = 4             # System tray section
CLOCK           = 5             # Clock section
LAUNCHER        = 2             # Application launcher section

#------------------------------------------------------------------------------
#                       Button Event Function Definitions
#------------------------------------------------------------------------------
# Left click   - button 1 
# Middle click - button 2
# Right click  - button 3
# Wheel up     - button 4
# Wheel down   - button 5 
#
# changeDesktop(x)
# - Change Desktop: Increase or decrease the current desktop by 'x' amount
# 
# toggleShade(task)
# - Shade or Unshade an application
#
# toggleHidden()
# - Minimize the panel to the top or bottom depending on its start location
#
# toggleMinimize(task, traise=1)
# - Minimize or Unminimize an application and optionally raise it
#
# taskRaise(task, focus=1)
# - Raise an application to the top of the window list and optionally focus it 
#
# taskLower(task, focus=0)
# - Lower an app to the bottom of the window list and optionally focus it
#
# taskFocus(task)
# - Give focus to the selected application, if it has focus then minimize it
#
# showDesktop()
# - Toggle between hiding and unhiding ALL applications
#------------------------------------------------------------------------------

#----------------------------------
def desktopButtonEvent(pp, button):
#----------------------------------
    """ Button event handler for the panel's desktop object """
        
    if button == 1:
        pp.changeDesktop(-1)
    elif button == 2:
        pp.changeDesktop(2)
    elif button == 3:
        pp.changeDesktop(1)
    elif button == 4:
        pp.changeDesktop(1)
    elif button == 5:
        pp.changeDesktop(-1)
        
#--------------------------------
def clockButtonEvent(pp, button):
#--------------------------------
    """ Button event handler for the panel's clock object """
    
    if button == 1:
        os.system("xclock &")
    elif button == 2:
        pass
    elif button == 3:
        pp.toggleHidden()  
    elif button == 4:
        pp.showDesktop()
    elif button == 5:
        pp.showDesktop()
        
#--------------------------------
def panelButtonEvent(pp, button):
#--------------------------------
    """ Button event handler for the panel with no active tasks """
    
    if button == 1:
        pass
    elif button == 2:
        pass
    elif button == 3:
        pass
    elif button == 4:
        pass
    elif button == 5:
        pass
        
#-------------------------------------
def taskButtonEvent(pp, button, task):
#-------------------------------------
    """ Button event handler for the panel's tasks """
    
    if button == 1:
        pp.taskFocus(task)
    elif button == 2:
        # Destroy the application
        task.obj.destroy()
    elif button == 3:
        # Ex. - XMMS doesn't shade, so we want to minimize it instead and
        #       still use button 3 to shade other applications
        #       task.tclass is the tasks class name (WM_CLASS)
        if "xmms" in task.tclass:
            pp.toggleMinimize(task)
        else:
            pp.toggleShade(task)
    elif button == 4:
        pp.taskRaise(task, focus=1)
    elif button == 5:
        pp.taskLower(task, focus=0)
        

```

While it's fairly usable in it's default state, it's also quite customizable. The above has had some color and transparency changes, along with a few custom lauchers added. It's fairly well commented, so is not terribly difficult to edit.

Note that the laucher icons listed specify my home directory, and applications which may or may not be present, so would need to be changed.

The 'Panel Layout' section has the launchers turned off in the default mode, while I have set them to the second position in mine.

You can even set a 'Hide List' if there are applications that you don't want to have displayed on the panel when executed.

Anyway, it's not for everyone, but I enjoy customizing my 'linux experience'. :) I had some better examples awhile back, but I hosed them to do a fresh breezy install some time ago, so it's a pretty simple setup now.

---

### Post by Iandefor on 2006-01-14
[quote=PatrickMay16]Recently, I've been reading on this forum about people who've installed Ubuntu on computers with low RAM by doing the server installation, then doing something like this:

```

apt-get install xserver-xorg
apt-get install xfce4

``` 
I'd like to ask, which packages exactly do you need to install when you do that? I think there's more than just that needed to get it working. I searched the forum but I wasn't able to find the post that I had read about this in.
Also, for people who've done this, what were the results like?
Let's discuss this.[/quote] 
There are a lot of dependencies to get X and XFCE running. My suggestion would be to look at the dependencies in Synaptic.

The results were usable, but, on the whole, I prefer GNOME. I had a magnificently old computer I installed Xubuntu on (64 megs of ram) and it was still slow. I did some hacking and managed to make Enlightenment the default WM, which really made it faster. Check [here]("http://www.ubuntuforums.org/showthread.php?t=101066") for instructions on how to do it.

---

### Post by graabein on 2006-01-17
Thanks for the reply SilentCacophony. I got mine pretty much up and running as I want it now. One of my biggest problems was configuring xterm to open with Midnight Commander, Irssi and Emacs with larger fonts. Got that solved now. 

One thing that bothers me is my PS/2 mouse sometimes runs amock like a little kitten it suddenly goes into a fit. Then my desktop gets cluttered with xclock apps and other crazy behaviour. I don't know how to catch this? Could it be as simple as reconfiguring xorg? 

I managed to delete the file .xsession-errors (I wanted a clean one cause I think X just appended to it) and even though I've created a new one I can't seem to catch events from X (what gets printed to tty1). 

Anyway, I've learned quite a bit and it's been fun! I'm going to have a look at Window Maker now.

---

### Post by simon_is_learning on 2006-01-20
I have after numerous reinstallations :-\"  started to do as follows:

server installation
(uncomment /etc/apt/sources.list + apt-get update)

sudo apt-get install x-window-system-core
sudo apt-get install xterminal 
sudo apt-get install xfce4

startx

after that, well you are free to do as you like...
gdm, kdm, xdm if you want to... But after what I have understood, a login manager also uses up memory - and if you don't are terribly lazy... startx isn't too bad ;)

thunar is the file manager that i prefer rather than rox-filer (wich is default when installing xubuntu)

---

### Post by fuscia on 2006-01-20
i took the approach of doing the default installation, replacing gdm, gnome, etc. with wdm, openbox and flwm, etc. and then just getting rid of everything i knew i could get rid of without killing my machine. even when running firefox, my ram usage is rarely above 100mbs and my swap file usage is very low (i did something about 'swappiness', but i don't recall what it was). i had given the server install a chance, but i really didn't know what i was doing.

---

### Post by vincebs on 2006-01-20
I managed to install Red Hat 9 two years ago on a Pentium Classic 133MHz w/ 32 MB of RAM. Not a good idea, it took 5 min to load up GNOME. I later installed Slackware 10 on it with few problems (except the CD-ROM drive often failing but I suspect it was also a hardware issue). So the trick is to use a lightweight (i.e. less bloatware) distribution and try to use the console instead of booting into X. If you must use X, use a lightweight window manager instead of GNOME and KDE.

I run Debian Sarge, w/ default settings, on a PIII 700 MHz w/ 256MB RAM  with no problem.

---

### Post by franklee on 2006-01-20
Im currently running Breezy on a 1ghz compaq with 256meg of sdram and its very comfortable, tho I would prefer to have more than the onboard video with 16meg as the opengl games arent too flash for me.

Suffice to say Ive also installed Ubuntu Hoary on a 500mhz machine with 64meg of ram and had it run, with an alternate wm like fluxbox or blackbox.

---

