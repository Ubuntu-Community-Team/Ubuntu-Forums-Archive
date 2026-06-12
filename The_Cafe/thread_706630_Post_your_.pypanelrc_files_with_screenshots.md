---
title: "Post your .pypanelrc files with screenshots"
date: 2008-02-24
forum: The Cafe
---

### Post by dbbolton on 2008-02-24
We needed a pypanel thread :)

[[img]http://box-look.org/CONTENT/content-m1/m75660-1.png[/img]](http://box-look.org/CONTENT/content-pre1/75660-1.jpg)

the .pypanelrc :

```

#------------------------------------------------------------------------------
#
#                         PyPanel v2.4 Configuration
#
# This configuration file is a Python script that will be executed when
# PyPanel is started.  In order for PyPanel to start properly, make sure that
# this file contains proper Python formatting and no syntax errors.
#------------------------------------------------------------------------------
VERSION         = 2.4           # Config file version

#------------------------------------------------------------------------------
# Colors: Format is hex triplet - 0xrrggbb
#------------------------------------------------------------------------------
BG_COLOR        = "0x000000"    # Panel background and tinting color
TASK_COLOR      = "0x000000"    # Normal task name color 
FOCUSED_COLOR   = "0x000000"    # Focused task name color
SHADED_COLOR    = "0x000000"    # Shaded task name color 
MINIMIZED_COLOR = "0x000000"    # Minimized task name color 
DESKTOP_COLOR   = "0xC57E24"    # Desktop name color
CLOCK_COLOR     = "0xcccccc"    # Clock text color
LINE_COLOR      = "0x000000"    # Vertical line color

# Text Shadow Colors
TASK_SHADOW_COLOR      = "0xffffff"
FOCUSED_SHADOW_COLOR   = "0xffffff"
SHADED_SHADOW_COLOR    = "0xffffff"
MINIMIZED_SHADOW_COLOR = "0xffffff" 
DESKTOP_SHADOW_COLOR   = "0xffffff"
CLOCK_SHADOW_COLOR     = "0xffffff"

#------------------------------------------------------------------------------
# Panel Spacing and Location Options: Measured in pixels
#------------------------------------------------------------------------------
P_LOCATION      = 0             # Panel placement: 0 = top, 1 = bottom
P_WIDTH         = 0             # Panel width: 0 = Use full screen width
P_START         = 0             # Starting X coordinate of the panel
P_SPACER        = 16             # Spacing between panel objects
P_HEIGHT        = 16            # Panel height

#------------------------------------------------------------------------------
# Icon Size Options: Measured in pixels
#------------------------------------------------------------------------------
I_HEIGHT        = 0            # Panel application icon height
I_WIDTH         = 0           # Panel application icon Width 
APPL_I_HEIGHT   = 24            # Application launcher icon height
APPL_I_WIDTH    = 24          # Application launcher icon width
TRAY_I_HEIGHT   = 24           # System tray icon height (usually 16 or 24)
TRAY_I_WIDTH    = 24           # System tray icon width  (usually 16 or 24)
                                # If TRAY_I_WIDTH is set to 0, then the
                                # width specified by the tray app will be used
                                
#------------------------------------------------------------------------------
# Panel Clock Format: 'man strftime' for detailed formatting options and help
#------------------------------------------------------------------------------
CLOCK_FORMAT    = "%a %d. %b.  %l:%M %p"  #%Y-%m-%d %H:%M"    # Ex: 2004-09-25 17:45 

#------------------------------------------------------------------------------
# Clock Delay: Seconds between each clock update during periods of inactivity
#------------------------------------------------------------------------------
CLOCK_DELAY     = 1

#------------------------------------------------------------------------------
# Hidden Application List: Apps listed here will not be display on the panel
# The application name is its WM_CLASS name, use 'xprop' to find WM_CLASS
# Ex: ["xmms", "xine", "gDesklets"]
#------------------------------------------------------------------------------
HIDE_LIST       = ["rhythmbox"]            
                   
#------------------------------------------------------------------------------
# Hidden Panel Size: Size of the panel when it's hidden/minimized
#------------------------------------------------------------------------------
HIDDEN_SIZE     = 2

#------------------------------------------------------------------------------
# Panel Text Font: This option takes either a traditional or Xft font string 
# Ex: "-schumacher-clean-medium-r-normal-*-12-*-*-*-*-*-*-*"
#     "aquafont-8" 
#------------------------------------------------------------------------------
FONT            = "gelly"

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
                   #("gnome-terminal", "/home/daniel/.icons/nuoveXT.2.1/16x16/apps/gnome-terminal.png"), 
                   #("leafpad", "/home/daniel/.icons/nuoveXT.2.1/16x16/apps/text-editor.png"),
                   #("firefox", "/home/daniel/.icons/nuoveXT.2.1/16x16/apps/mozilla-firefox.png"),
                   #("gaim", "/usr/share/icons/Tango/16x16/apps/gaim.png"),
                   #("exaile", "/home/daniel/.icons/nuoveXT.2.1/16x16/apps/exaile.png"),
                   #("thunar /home/daniel", "/home/daniel/Art/start-here-48.png")
                  ]

#------------------------------------------------------------------------------
# Background Alpha/Shade Level: 0 (Fully Translucent) -> 255 (Fully Opaque)
# BG_COLOR is used for tinting
#------------------------------------------------------------------------------
SHADE           = 255

#------------------------------------------------------------------------------
# Misc. Options: 1 = Enabled/Yes, 0 = Disabled/No
#------------------------------------------------------------------------------
ABOVE           = 0             # Panel is always above other apps
APPICONS        = 0             # Show application icons
AUTOHIDE        = 0             # Autohide uses the CLOCK_DELAY timer above
SHADOWS         = 0             # Show text shadows
SHOWLINES       = 0             # Show object seperation lines
SHOWBORDER      = 0             # Show a border around the panel

#------------------------------------------------------------------------------
# Desktop Names: Configure the names of your desktops
# If the option is [], PyPanel will attempt to use the desktop name specified
# by the XServer, if that fails it will use the desktop number as its name
# Ex. ["One", "Two", "Three", "Four", "Five", "Six", "Seven", "Eight"]
#------------------------------------------------------------------------------
DESKTOP_NAMES   = ["[Desk 1]", "[Desk 2]", "Three", "Four"]

#------------------------------------------------------------------------------
# Panel Layout:       -----------------------------------
#                     [  1  ][  2  ][  3  ][  4  ][  5  ]
#                     -----------------------------------
#
# The panel layout is split into 5 sections numbered 1, 2, 3, 4 or 5 as shown
# in the diagram above.  Each of the following objects can be enabled by
# assigning it a section number or disabled by assigning it 0:
#------------------------------------------------------------------------------
DESKTOP         = 1            # Desktop name section
TASKS           = 2            # Task names section 
TRAY            = 0            # System tray section
CLOCK           = 3            # Clock section
LAUNCHER        = 0            # Application launcher section

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

---

### Post by uzusan on 2008-03-13
mine at the moment. Need to have a play around with it more. Click for full size (1280 x 76)

[[IMG]http://www.fillermaterial.co.uk/pypanel-small.png[/IMG]]("http://www.fillermaterial.co.uk/pypanel.png")

```

#------------------------------------------------------------------------------
#
#                         PyPanel v2.4 Configuration
#
# This configuration file is a Python script that will be executed when
# PyPanel is started.  In order for PyPanel to start properly, make sure that
# this file contains proper Python formatting and no syntax errors.
#------------------------------------------------------------------------------
VERSION         = 2.4           # Config file version

#------------------------------------------------------------------------------
# Colors: Format is hex triplet - 0xrrggbb
#------------------------------------------------------------------------------
BG_COLOR        = "0xd6d6d6"    # Panel background and tinting color
TASK_COLOR      = "0xffffff"    # Normal task name color 
FOCUSED_COLOR   = "0xff500"    # Focused task name color
SHADED_COLOR    = "0xffffff"    # Shaded task name color 
MINIMIZED_COLOR = "0xffffff"    # Minimized task name color 
DESKTOP_COLOR   = "0xffffff"    # Desktop name color
CLOCK_COLOR     = "0xffffff"    # Clock text color
LINE_COLOR      = "0x606060"    # Vertical line color
SHADE           = 0

# Text Shadow Colors
TASK_SHADOW_COLOR      = "0xffffff"
FOCUSED_SHADOW_COLOR   = "0xffffff"
SHADED_SHADOW_COLOR    = "0xffffff"
MINIMIZED_SHADOW_COLOR = "0xffffff" 
DESKTOP_SHADOW_COLOR   = "0xffffff"
CLOCK_SHADOW_COLOR     = "0xffffff"

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
                   ("/home/uzusan/firefox/firefox", "/home/uzusan/.icons/glass-icons/scalable/apps/firefox-icon.png"),
                   ("evolution", "/home/uzusan/.icons/glass-icons/scalable/apps/thunderbird.png"),
                   ("/home/uzusan/.scripts/urxvt.sh", "/home/uzusan/.icons/glass-icons/scalable/apps/gnome-terminal.png"),
                   ("thunar", "/home/uzusan/.icons/glass-icons/scalable/apps/my-computer.png"),
                   ("amarok", "/usr/share/app-install/icons/amarok.png"),

                  ]

#------------------------------------------------------------------------------
# Background Alpha/Shade Level: 0 (Fully Translucent) -> 255 (Fully Opaque)
# BG_COLOR is used for tinting
#------------------------------------------------------------------------------


#------------------------------------------------------------------------------
# Misc. Options: 1 = Enabled/Yes, 0 = Disabled/No
#------------------------------------------------------------------------------
ABOVE           = 1             # Panel is always above other apps
APPICONS        = 1             # Show application icons
AUTOHIDE        = 0             # Autohide uses the CLOCK_DELAY timer above
SHADOWS         = 0             # Show text shadows
SHOWLINES       = 1             # Show object seperation lines
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
DESKTOP         = 0             # Desktop name section
TASKS           = 2             # Task names section 
TRAY            = 4             # System tray section
CLOCK           = 5             # Clock section
LAUNCHER        = 1             # Application launcher section

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

---

### Post by canistra on 2008-03-18
```
#------------------------------------------------------------------------------
#
#                         PyPanel v2.4 Configuration
#
# This configuration file is a Python script that will be executed when
# PyPanel is started.  In order for PyPanel to start properly, make sure that
# this file contains proper Python formatting and no syntax errors.
#------------------------------------------------------------------------------
VERSION         = 2.4           # Config file version

#------------------------------------------------------------------------------
# Colors: Format is hex triplet - 0xrrggbb
#------------------------------------------------------------------------------
#BG_COLOR        = "0xffffff"    # Panel background and tinting color
#TASK_COLOR      = "0xffffff"    # Normal task name color 
#FOCUSED_COLOR   = "0xffffff"    # Focused task name color
#SHADED_COLOR    = "0xffffff"    # Shaded task name color 
#MINIMIZED_COLOR = "0xffffff"    # Minimized task name color 
#DESKTOP_COLOR   = "0xffffff"    # Desktop name color
#CLOCK_COLOR     = "0xffffff"    # Clock text color
#LINE_COLOR      = "0x606060"    # Vertical line color
BG_COLOR        = "0x0b093a"    # Panel background and tinting color
TASK_COLOR      = "0x0b093a"    # Normal task name color 
FOCUSED_COLOR   = "0x0b093a"    # Focused task name color
SHADED_COLOR    = "0x0b093a"    # Shaded task name color 
MINIMIZED_COLOR = "0x0b093a"    # Minimized task name color 
DESKTOP_COLOR   = "0x0b093a"    # Desktop name color
CLOCK_COLOR     = "0x0b093a"    # Clock text color
LINE_COLOR      = "0x606060"    # Vertical line color
SHADE           = 0

# Text Shadow Colors
TASK_SHADOW_COLOR      = "0xffffff"
FOCUSED_SHADOW_COLOR   = "0xffffff"
SHADED_SHADOW_COLOR    = "0xffffff"
MINIMIZED_SHADOW_COLOR = "0xffffff" 
DESKTOP_SHADOW_COLOR   = "0xffffff"
CLOCK_SHADOW_COLOR     = "0xffffff"

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
#FONT            = "bitstream vera sans-8"
#FONT            = "sans-8:bold"
FONT		 = "domestic manners-9:bold"

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
                   ("/home/uzusan/firefox/firefox", "/home/uzusan/.icons/glass-icons/scalable/apps/firefox-icon.png"),
                   ("evolution", "/home/uzusan/.icons/glass-icons/scalable/apps/thunderbird.png"),
                   ("/home/uzusan/.scripts/urxvt.sh", "/home/uzusan/.icons/glass-icons/scalable/apps/gnome-terminal.png"),
                   ("thunar", "/home/uzusan/.icons/glass-icons/scalable/apps/my-computer.png"),
                   ("amarok", "/usr/share/app-install/icons/amarok.png"),

                  ]

#------------------------------------------------------------------------------
# Background Alpha/Shade Level: 0 (Fully Translucent) -> 255 (Fully Opaque)
# BG_COLOR is used for tinting
#------------------------------------------------------------------------------


#------------------------------------------------------------------------------
# Misc. Options: 1 = Enabled/Yes, 0 = Disabled/No
#------------------------------------------------------------------------------
ABOVE           = 1             # Panel is always above other apps
APPICONS        = 0             # Show application icons
AUTOHIDE        = 0             # Autohide uses the CLOCK_DELAY timer above
SHADOWS         = 0             # Show text shadows
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
DESKTOP         = 0             # Desktop name section
TASKS           = 1             # Task names section 
TRAY            = 0             # System tray section
CLOCK           = 0             # Clock section
LAUNCHER        = 0             # Application launcher section

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
        pp.taskRaise(task, focus=1)
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

    if button == 1:
        pp.taskFocus(task)
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
[[img]http://img291.imageshack.us/img291/9610/200803181620051024x768swc7.th.png[/img]](http://img291.imageshack.us/my.php?image=200803181620051024x768swc7.png)

---

### Post by dbbolton on 2008-06-05
My current pypanel setup:

[[IMG]http://i103.photobucket.com/albums/m128/envyouraudience/th_pypanel5june08.png[/IMG]](http://i103.photobucket.com/albums/m128/envyouraudience/pypanel5june08.png)

.pypanelrc
```

#------------------------------------------------------------------------------
#
#                         PyPanel v2.4 Configuration
#
# This configuration file is a Python script that will be executed when
# PyPanel is started.  In order for PyPanel to start properly, make sure that
# this file contains proper Python formatting and no syntax errors.
#------------------------------------------------------------------------------
VERSION         = 2.4           # Config file version

#------------------------------------------------------------------------------
# Colors: Format is hex triplet - 0xrrggbb
#------------------------------------------------------------------------------
BG_COLOR        = "0x000000"    # Panel background and tinting color
TASK_COLOR      = "0x909090"    # Normal task name color 
FOCUSED_COLOR   = "0xffffff"    # Focused task name color
SHADED_COLOR    = "0x909090"    # Shaded task name color 
MINIMIZED_COLOR = "0x909090"    # Minimized task name color 
DESKTOP_COLOR   = "0xFF8800"    # Desktop name color
CLOCK_COLOR     = "0x000000"    # Clock text color
LINE_COLOR      = "0xc0c0c0"    # Vertical line color

# Text Shadow Colors
TASK_SHADOW_COLOR      = "0x101010"
FOCUSED_SHADOW_COLOR   = "0x101010"
SHADED_SHADOW_COLOR    = "0x101010"
MINIMIZED_SHADOW_COLOR = "0x101010" 
DESKTOP_SHADOW_COLOR   = "0x101010"
CLOCK_SHADOW_COLOR     = "0x000000"

#------------------------------------------------------------------------------
# Panel Spacing and Location Options: Measured in pixels
#------------------------------------------------------------------------------
P_LOCATION      = 1             # Panel placement: 0 = top, 1 = bottom
P_WIDTH         = 900           # Panel width: 0 = Use full screen width
P_START         = 62            # Starting X coordinate of the panel
P_SPACER        = 8             # Spacing between panel objects
P_HEIGHT        = 18            # Panel height

#------------------------------------------------------------------------------
# Icon Size Options: Measured in pixels
#------------------------------------------------------------------------------
I_HEIGHT        = 16            # Panel application icon height
I_WIDTH         = 16            # Panel application icon Width 
APPL_I_HEIGHT   = 24            # Application launcher icon height
APPL_I_WIDTH    = 24            # Application launcher icon width
TRAY_I_HEIGHT   = 16            # System tray icon height (usually 16 or 24)
TRAY_I_WIDTH    = 16            # System tray icon width  (usually 16 or 24)
                                # If TRAY_I_WIDTH is set to 0, then the
                                # width specified by the tray app will be used
                                
#------------------------------------------------------------------------------
# Panel Clock Format: 'man strftime' for detailed formatting options and help
#------------------------------------------------------------------------------
CLOCK_FORMAT    = " "   # good: %a %d %b  %l:%M %p

#------------------------------------------------------------------------------
# Clock Delay: Seconds between each clock update during periods of inactivity
#------------------------------------------------------------------------------
CLOCK_DELAY     = 1

#------------------------------------------------------------------------------
# Hidden Application List: Apps listed here will not be display on the panel
# The application name is its WM_CLASS name, use 'xprop' to find WM_CLASS
# Ex: ["xmms", "xine", "gDesklets"]
#------------------------------------------------------------------------------
HIDE_LIST       = ["xmms", "gmrun", "quodlibet", "gmplayer"]            
                   
#------------------------------------------------------------------------------
# Hidden Panel Size: Size of the panel when it's hidden/minimized
#------------------------------------------------------------------------------
HIDDEN_SIZE     = 2

#------------------------------------------------------------------------------
# Panel Text Font: This option takes either a traditional or Xft font string 
# Ex: "-schumacher-clean-medium-r-normal-*-12-*-*-*-*-*-*-*"
#     "aquafont-8" 
#------------------------------------------------------------------------------
FONT            = "nu" # "myriadweb:pixelsize=12"

#------------------------------------------------------------------------------
# Show All Applications: Show apps from all desktops or just the current
# 0: Disabled - Only applications on the current desktop will be displayed
# 1: Enabled  - Selected apps are moved to the current desktop
# 2: Enabled  - Current desktop is changed to the selected apps desktop
#------------------------------------------------------------------------------
SHOWALL         = 2             # 0, 1 or 2 - see descriptions above

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
                   #("gnome-terminal", "/home/daniel/.icons/nuoveXT.2.1/16x16/apps/gnome-terminal.png"), 
                   #("leafpad", "/home/daniel/.icons/nuoveXT.2.1/16x16/apps/text-editor.png"),
                   #("firefox", "/home/daniel/.icons/nuoveXT.2.1/16x16/apps/mozilla-firefox.png"),
                   #("gaim", "/usr/share/icons/Tango/16x16/apps/gaim.png"),
                   #("exaile", "/home/daniel/.icons/nuoveXT.2.1/16x16/apps/exaile.png"),
                   ("thunar /home/daniel", "/home/daniel/Art/start-here-48.png")
                  ]

#------------------------------------------------------------------------------
# Background Alpha/Shade Level: 0 (Fully Translucent) -> 255 (Fully Opaque)
# BG_COLOR is used for tinting
#------------------------------------------------------------------------------
SHADE           = 255

#------------------------------------------------------------------------------
# Misc. Options: 1 = Enabled/Yes, 0 = Disabled/No
#------------------------------------------------------------------------------
ABOVE           = 0             # Panel is always above other apps
APPICONS        = 1             # Show application icons
AUTOHIDE        = 0             # Autohide uses the CLOCK_DELAY timer above
SHADOWS         = 1             # Show text shadows
SHOWLINES       = 0           # Show object seperation lines
SHOWBORDER      = 1             # Show a border around the panel

#------------------------------------------------------------------------------
# Desktop Names: Configure the names of your desktops
# If the option is [], PyPanel will attempt to use the desktop name specified
# by the XServer, if that fails it will use the desktop number as its name
# Ex. ["One", "Two", "Three", "Four", "Five", "Six", "Seven", "Eight"]
#------------------------------------------------------------------------------
#DESKTOP_NAMES   = ["[1]", "[2]", "[3]", "[4]"]

#------------------------------------------------------------------------------
# Panel Layout:       -----------------------------------
#                     [  1  ][  2  ][  3  ][  4  ][  5  ]
#                     -----------------------------------
#
# The panel layout is split into 5 sections numbered 1, 2, 3, 4 or 5 as shown
# in the diagram above.  Each of the following objects can be enabled by
# assigning it a section number or disabled by assigning it 0:
#------------------------------------------------------------------------------
DESKTOP         = 1            # Desktop name section
TASKS           = 2            # Task names section 
TRAY            = 3            # System tray section
CLOCK           = 4            # Clock section
LAUNCHER        = 0            # Application launcher section

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

---

### Post by urukrama on 2008-06-10
Very simple pypanel :-) I only use the system tray. Note that you need to apply [this patch]("http://bbs.archlinux.org/viewtopic.php?pid=261501") to pypanel for this configuration to work.

Here is the config file:

```
#------------------------------------------------------------------------------
#
#                         PyPanel v2.4 Configuration
#
# This configuration file is a Python script that will be executed when
# PyPanel is started.  In order for PyPanel to start properly, make sure that
# this file contains proper Python formatting and no syntax errors.
#------------------------------------------------------------------------------
VERSION         = 2.4           # Config file version

#------------------------------------------------------------------------------
# Colors: Format is hex triplet - 0xrrggbb
#------------------------------------------------------------------------------
BG_COLOR        = "0x3C4746"    # Panel background and tinting color
TASK_COLOR      = "0x859F9C"    # Normal task name color 
FOCUSED_COLOR   = "0x3C4746"    # Focused task name color
SHADED_COLOR    = "0x859F9C"    # Shaded task name color 
MINIMIZED_COLOR = "0x859F9C"    # Minimized task name color 
DESKTOP_COLOR   = "0x3C4746"    # Desktop name color
CLOCK_COLOR     = "0x3C4746"    # Clock text color
LINE_COLOR      = "0x758C8A"    # Vertical line color

# Text Shadow Colors
TASK_SHADOW_COLOR      = "0x010100"
FOCUSED_SHADOW_COLOR   = "0x010100"
SHADED_SHADOW_COLOR    = "0x010100"
MINIMIZED_SHADOW_COLOR = "0x010100" 
DESKTOP_SHADOW_COLOR   = "0x871706"
CLOCK_SHADOW_COLOR     = "0x871706"

#------------------------------------------------------------------------------
# Panel Spacing and Location Options: Measured in pixels
#------------------------------------------------------------------------------
P_LOCATION      = 1            # Panel placement: 0 = top, 1 = bottom
P_WIDTH         = 50             # Panel width: 0 = Use full screen width
P_START         = 4             # Starting X coordinate of the panel
P_SPACER        = 12             # Spacing between panel objects
P_HEIGHT        = 22            # Panel height

P_L_BUFF        = 3
P_R_BUFF        = 0
P_T_BUFF        = 0
P_B_BUFF        = 3


#------------------------------------------------------------------------------
# Icon Size Options: Measured in pixels
#------------------------------------------------------------------------------
I_HEIGHT        = 16            # Panel application icon height
I_WIDTH         = 16            # Panel application icon Width 
APPL_I_HEIGHT   = 16            # Application launcher icon height
APPL_I_WIDTH    = 16            # Application launcher icon width
TRAY_I_HEIGHT   = 16            # System tray icon height (usually 16 or 24)
TRAY_I_WIDTH    = 0            # System tray icon width  (usually 16 or 24)
                                # If TRAY_I_WIDTH is set to 0, then the
                                # width specified by the tray app will be used
                                
#------------------------------------------------------------------------------
# Panel Clock Format: 'man strftime' for detailed formatting options and help
#------------------------------------------------------------------------------
CLOCK_FORMAT    = "%H:%M"    # Ex: 2004-09-25 17:45 

#------------------------------------------------------------------------------
# Clock Delay: Seconds between each clock update during periods of inactivity
#------------------------------------------------------------------------------
CLOCK_DELAY     = 5

#------------------------------------------------------------------------------
# Hidden Application List: Apps listed here will not be display on the panel
# The application name is its WM_CLASS name, use 'xprop' to find WM_CLASS
# Ex: ["xmms", "xine", "gDesklets"]
#------------------------------------------------------------------------------
HIDE_LIST       = ["netwmpager"]            
                   
#------------------------------------------------------------------------------
# Hidden Panel Size: Size of the panel when it's hidden/minimized
#------------------------------------------------------------------------------
HIDDEN_SIZE     = 2

#------------------------------------------------------------------------------
# Panel Text Font: This option takes either a traditional or Xft font string 
# Ex: "-schumacher-clean-medium-r-normal-*-12-*-*-*-*-*-*-*"
#     "aquafont-8" 
#------------------------------------------------------------------------------
FONT            = "Corbel-8:bold"

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
                   ("gnome-volume-control", "/usr/share/icons/gnome/24x24/stock/media/stock_volume.png")
                  ]

#------------------------------------------------------------------------------
# Background Alpha/Shade Level: 0 (Fully Translucent) -> 255 (Fully Opaque)
# BG_COLOR is used for tinting
#------------------------------------------------------------------------------
SHADE           = 255

#------------------------------------------------------------------------------
# Misc. Options: 1 = Enabled/Yes, 0 = Disabled/No
#------------------------------------------------------------------------------
ABOVE           = 0             # Panel is always above other apps
APPICONS        = 0             # Show application icons
AUTOHIDE        = 0             # Autohide uses the CLOCK_DELAY timer above
SHADOWS         = 0             # Show text shadows
SHOWLINES       = 0             # Show object seperation lines
SHOWBORDER      = 1             # Show a border around the panel

#------------------------------------------------------------------------------
# Desktop Names: Configure the names of your desktops
# If the option is [], PyPanel will attempt to use the desktop name specified
# by the XServer, if that fails it will use the desktop number as its name
# Ex. ["One", "Two", "Three", "Four", "Five", "Six", "Seven", "Eight"]
#------------------------------------------------------------------------------
DESKTOP_NAMES   = ["one", "two", "three"]

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
TRAY            = 1          	# System tray section
CLOCK           = 0             # Clock section
LAUNCHER        = 0             # Application launcher section

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
        pp.showDesktop()
    elif button == 3:
        os.system("tabble &")
    elif button == 4:
        pp.changeDesktop(1)
    elif button == 5:
        pp.changeDesktop(-1)
        
#--------------------------------
def clockButtonEvent(pp, button):
#--------------------------------
    """ Button event handler for the panel's clock object """
    
    if button == 1:
        os.system("/home/urukrama/.scripts/dzen_calendar &")
    elif button == 2:
        pass
    elif button == 3:
        os.system("orage &") 
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
        #if "xmms" in task.tclass:
        #    pp.toggleMinimize(task)
        #else:
        #    pp.toggleShade(task)
	os.system("wmctrl -r :ACTIVE: -t 2 &")
    elif button == 4:
        pp.taskRaise(task, focus=1)
    elif button == 5:
        pp.taskLower(task, focus=0)
        

```

And here is a screenshot:

(The conky and visibility configs can be found [here]("http://ubuntuforums.org/showthread.php?p=5156646#post5156646") and [here]("http://ubuntuforums.org/showthread.php?p=5156614#post5156614"))

---

### Post by Totalchaos02 on 2008-06-15
How do you get pypanel to have a top and bottom panel?

---

### Post by BeachBum on 2008-06-19
I've almost got my ideal pypanel but need help with one more thing.  I'm sure this is possible but I cannot get it to work.  

If I have firefox, for example, raised and focused, what do I need to change in the config so that if I click on Firefox in the taskbar, it becomes minimized/ lowered to taskbar?  XFCE panel does this, and I miss it.

```

# taskFocus(task)
# - Give focus to the selected application, if it has focus then minimize it
```

```

    """ Button event handler for the panel's tasks """
    
    if button == 1:
        pp.taskFocus(task)
```

By the looks of it, this should happening already, but if I click on Firefox in the taskbar when it already has focus, the window just flickers for a split second.  

Any ideas?

---

### Post by dbbolton on 2008-06-19
> **Totalchaos02 said:**
> How do you get pypanel to have a top and bottom panel?
I'm not sure if this is possible. In order to do it, you would have to run 2 instances of pypanel, with the second instance loading a different config file. Since 'pypanel' doesn't have any command line arguments, I don't think you can make it use a config file other than the default. It might be possible to edit the source code and create a new binary that reads a different file, but that seems like more trouble than it's worth.

> **BeachBum said:**
> I've almost got my ideal pypanel but need help with one more thing. I'm sure this is possible but I cannot get it to work. 

If I have firefox, for example, raised and focused, what do I need to change in the config so that if I click on Firefox in the taskbar, it becomes minimized/ lowered to taskbar? XFCE panel does this, and I miss it.

```

# taskFocus(task)
# - Give focus to the selected application, if it has focus then minimize it
``````

    """ Button event handler for the panel's tasks """
    
    if button == 1:
        pp.taskFocus(task)
```By the looks of it, this should happening already, but if I click on Firefox in the taskbar when it already has focus, the window just flickers for a split second. 

Any ideas?
I wonder if there is something wrong with your pypanel setup. Mine seems to have this feature by default.

---

### Post by PrimoTurbo on 2008-06-25
Using a wallpaper with an image of a taskbar, pypanel is on top and is transparent.

```
#------------------------------------------------------------------------------
#
#                         PyPanel v2.4 Configuration
#
# This configuration file is a Python script that will be executed when
# PyPanel is started.  In order for PyPanel to start properly, make sure that
# this file contains proper Python formatting and no syntax errors.
#------------------------------------------------------------------------------
VERSION         = 2.4           # Config file version

#------------------------------------------------------------------------------
# Colors: Format is hex triplet - 0xrrggbb
#------------------------------------------------------------------------------
BG_COLOR        = "0xFFFFFF"    # Panel background and tinting color
TASK_COLOR      = "0xFFFFFF"    # Normal task name color 
FOCUSED_COLOR   = "0x9FC6FF"    # Focused task name color
SHADED_COLOR    = "0xFFFFFF"    # Shaded task name color 
MINIMIZED_COLOR = "0xFFFFFF"    # Minimized task name color 
DESKTOP_COLOR   = "0xFFFFFF"    # Desktop name color
CLOCK_COLOR     = "0xFFFFFF"    # Clock text color
LINE_COLOR      = "0x656565"    # Vertical line color

# Text Shadow Colors
TASK_SHADOW_COLOR      = "0x000000"
FOCUSED_SHADOW_COLOR   = "0x000000"
SHADED_SHADOW_COLOR    = "0x000000"
MINIMIZED_SHADOW_COLOR = "0x000000" 
DESKTOP_SHADOW_COLOR   = "0x000000"
CLOCK_SHADOW_COLOR     = "0x000000"

#------------------------------------------------------------------------------
# Panel Spacing and Location Options: Measured in pixels
#------------------------------------------------------------------------------
P_LOCATION      = 1             # Panel placement: 0 = top, 1 = bottom
P_WIDTH         = 1120          # Panel width: 0 = Use full screen width
P_START         = 60             # Starting X coordinate of the panel
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
CLOCK_FORMAT    = "%I:%M %p"    # Ex: 2004-09-25 17:45 - "%Y-%m-%d %H:%M" 

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
                  }
                  
#------------------------------------------------------------------------------
# Application Launch List: Ordered list of icons and applications for the
#                          application launcher.
# 
# Add entries using the following format -
#     ("<executable>", "<full path to icon>")
#------------------------------------------------------------------------------
LAUNCH_LIST     = [
                   ("gnome-volume-control", "/home/primo/Files/System/Customize/Icons/Single/AudioSmall.png"), 
                  ]

#------------------------------------------------------------------------------
# Background Alpha/Shade Level: 0 (Fully Translucent) -> 255 (Fully Opaque)
# BG_COLOR is used for tinting
#------------------------------------------------------------------------------
SHADE           = 0

#------------------------------------------------------------------------------
# Misc. Options: 1 = Enabled/Yes, 0 = Disabled/No
#------------------------------------------------------------------------------
ABOVE           = 1             # Panel is always above other apps
APPICONS        = 1             # Show application icons
AUTOHIDE        = 0             # Autohide uses the CLOCK_DELAY timer above
SHADOWS         = 1             # Show text shadows
SHOWLINES       = 0             # Show object seperation lines
SHOWBORDER      = 0             # Show a border around the panel

#------------------------------------------------------------------------------
# Desktop Names: Configure the names of your desktops
# If the option is [], PyPanel will attempt to use the desktop name specified
# by the XServer, if that fails it will use the desktop number as its name
# Ex. ["One", "Two", "Three", "Four", "Five", "Six", "Seven", "Eight"]
#------------------------------------------------------------------------------
DESKTOP_NAMES   = ["One", "Two", "Three", "Four"]

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
TASKS           = 1             # Task names section 
TRAY            = 2             # System tray section
CLOCK           = 4             # Clock section
LAUNCHER        = 3             # Application launcher section

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
        pp.changeDesktop(1)
    elif button == 2:
        pp.changeDesktop(1)
    elif button == 3:
        pp.changeDesktop(-1)
    elif button == 4:
        pp.changeDesktop(1)
    elif button == 5:
        pp.changeDesktop(1)
        
#--------------------------------
def clockButtonEvent(pp, button):
#--------------------------------
    """ Button event handler for the panel's clock object """
    
    if button == 1:
        os.system("/home/primo/Files/System/Scripts/dzen_calendar &")
    elif button == 2:
        pass
    elif button == 3:
        os.system("osmo &")
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
        pp.taskFocus(task)
    elif button == 2:
	pass
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

---

### Post by PrimoTurbo on 2008-06-25
> **BeachBum said:**
> I've almost got my ideal pypanel but need help with one more thing.  I'm sure this is possible but I cannot get it to work.  

If I have firefox, for example, raised and focused, what do I need to change in the config so that if I click on Firefox in the taskbar, it becomes minimized/ lowered to taskbar?  XFCE panel does this, and I miss it.

```

# taskFocus(task)
# - Give focus to the selected application, if it has focus then minimize it
```

```

    """ Button event handler for the panel's tasks """
    
    if button == 1:
        pp.taskFocus(task)
```

By the looks of it, this should happening already, but if I click on Firefox in the taskbar when it already has focus, the window just flickers for a split second.  

Any ideas?

Yes I think you need to have 2 instances of pp.taskFocus(task).  

So it should be like this:
```
if button == 1:
        pp.taskFocus(task)
        pp.taskFocus(task)
```

More info: [http://wiki.archlinux.org/index.php/PyPanel#Tips.26Tricks](http://wiki.archlinux.org/index.php/PyPanel#Tips.26Tricks)

I hope this is what you are looking for, I know that by default pypanel acts kind of odd and not like a traditional task bar.

---

### Post by BeachBum on 2008-06-25
> **PrimoTurbo said:**
> 
I hope this is what you are looking for, I know that by default pypanel acts kind of odd and not like a traditional task bar.

Thats exactly it!  Thanks!  And now for my contribution:

```
#------------------------------------------------------------------------------
#
#                         PyPanel v2.4 Configuration
#
# This configuration file is a Python script that will be executed when
# PyPanel is started.  In order for PyPanel to start properly, make sure that
# this file contains proper Python formatting and no syntax errors.
#------------------------------------------------------------------------------
VERSION         = 2.4           # Config file version

#------------------------------------------------------------------------------
# Colors: Format is hex triplet - 0xrrggbb
#------------------------------------------------------------------------------
BG_COLOR        = "0x000000"    # Panel background and tinting color
TASK_COLOR      = "0x858585"    # Normal task name color 
FOCUSED_COLOR   = "0xffffff"    # Focused task name color
SHADED_COLOR    = "0x858585"    # Shaded task name color 
MINIMIZED_COLOR = "0x858585"    # Minimized task name color 
DESKTOP_COLOR   = "0xffffff"    # Desktop name color
CLOCK_COLOR     = "0xffffff"    # Clock text color
LINE_COLOR      = "0x606060"    # Vertical line color

# Text Shadow Colors
TASK_SHADOW_COLOR      = "0xffffff"
FOCUSED_SHADOW_COLOR   = "0xffffff"
SHADED_SHADOW_COLOR    = "0xffffff"
MINIMIZED_SHADOW_COLOR = "0xffffff" 
DESKTOP_SHADOW_COLOR   = "0xffffff"
CLOCK_SHADOW_COLOR     = "0xffffff"

#------------------------------------------------------------------------------
# Panel Spacing and Location Options: Measured in pixels
#------------------------------------------------------------------------------
P_LOCATION      = 1             # Panel placement: 0 = top, 1 = bottom
P_WIDTH         = 0             # Panel width: 0 = Use full screen width
P_START         = 0             # Starting X coordinate of the panel
P_SPACER        = 6             # Spacing between panel objects
P_HEIGHT        = 18            # Panel height

#------------------------------------------------------------------------------
# Icon Size Options: Measured in pixels
#------------------------------------------------------------------------------
I_HEIGHT        = 16            # Panel application icon height
I_WIDTH         = 16            # Panel application icon Width 
APPL_I_HEIGHT   = 16            # Application launcher icon height
APPL_I_WIDTH    = 16            # Application launcher icon width
TRAY_I_HEIGHT   = 16            # System tray icon height (usually 16 or 24)
TRAY_I_WIDTH    = 16            # System tray icon width  (usually 16 or 24)
                                # If TRAY_I_WIDTH is set to 0, then the
                                # width specified by the tray app will be used
#------------------------------------------------------------------------------
# Panel Floating Parameters
#------------------------------------------------------------------------------
P_L_BUFF        = 4
P_R_BUFF        = 4
P_T_BUFF        = 0
P_B_BUFF        = 3
                                
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
FONT            = "bauhaus-6.5"

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
                   ("gimp-2.2", "/usr/share/imlib2/data/images/paper.png"), 
                  ]

#------------------------------------------------------------------------------
# Background Alpha/Shade Level: 0 (Fully Translucent) -> 255 (Fully Opaque)
# BG_COLOR is used for tinting
#------------------------------------------------------------------------------
SHADE           = 200

#------------------------------------------------------------------------------
# Misc. Options: 1 = Enabled/Yes, 0 = Disabled/No
#------------------------------------------------------------------------------
ABOVE           = 1             # Panel is always above other apps
APPICONS        = 0             # Show application icons
AUTOHIDE        = 0             # Autohide uses the CLOCK_DELAY timer above
SHADOWS         = 0             # Show text shadows
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
DESKTOP         = 0             # Desktop name section
TASKS           = 1             # Task names section 
TRAY            = 2             # System tray section
CLOCK           = 3             # Clock section
LAUNCHER        = 0             # Application launcher section

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
        os.system("orage &")
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

---

### Post by elmer_42 on 2008-07-04
Alright, I got a personal message about my pypanel, so I'm posting it here.

[[img]http://arch.kimag.es/resized/96729365.png[/img]]("http://arch.kimag.es/share/96729365.png")

.pypanelrc:
```
#------------------------------------------------------------------------------
#
#                         PyPanel v2.4 Configuration
#
# This configuration file is a Python script that will be executed when
# PyPanel is started.  In order for PyPanel to start properly, make sure that
# this file contains proper Python formatting and no syntax errors.
#------------------------------------------------------------------------------
VERSION         = 2.4           # Config file version

#------------------------------------------------------------------------------
# Colors: Format is hex triplet - 0xrrggbb
#------------------------------------------------------------------------------
BG_COLOR        = "0xd6d6d6"    # Panel background and tinting color
TASK_COLOR      = "0xe6e6e6"    # Normal task name color 
FOCUSED_COLOR   = "0xFFFFFF"    # Focused task name color
SHADED_COLOR    = "0x808080"    # Shaded task name color 
MINIMIZED_COLOR = "0x808080"    # Minimized task name color 
DESKTOP_COLOR   = "0xe6e6e6"    # Desktop name color
CLOCK_COLOR     = "0xe6e6e6"    # Clock text color
LINE_COLOR      = "0xe6e6e6"    # Vertical line color

# Text Shadow Colors
TASK_SHADOW_COLOR      = "0xffffff"
FOCUSED_SHADOW_COLOR   = "0xffffff"
SHADED_SHADOW_COLOR    = "0xffffff"
MINIMIZED_SHADOW_COLOR = "0xffffff" 
DESKTOP_SHADOW_COLOR   = "0xffffff"
CLOCK_SHADOW_COLOR     = "0xffffff"

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
                   ("gimp-2.2", "/usr/share/imlib2/data/images/paper.png"), 
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
SHADOWS         = 0             # Show text shadows
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
TASKS           = 2             # Task names section 
TRAY            = 3             # System tray section
CLOCK           = 4             # Clock section
LAUNCHER        = 0             # Application launcher section

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

---

### Post by rtom on 2008-08-13
Any idea, what command to put into pypanelrc to get the openbox menu opened? I would like to add this to the desktop section instead of switching to the next dektop.

---

### Post by dbbolton on 2008-08-13
> **rtom said:**
> Any idea, what command to put into pypanelrc to get the openbox menu opened? I would like to add this to the desktop section instead of switching to the next dektop.
Follow this guide: [http://crunchbang.org/archives/2008/03/14/invoke-openboxs-menu-with-xdotool/](http://crunchbang.org/archives/2008/03/14/invoke-openboxs-menu-with-xdotool/)

Then create a pypanel launcher with the command "xdotool key ctrl+alt+q", like so (starting at line 111):

```

#------------------------------------------------------------------------------
# Application Launch List: Ordered list of icons and applications for the
#                          application launcher.
# 
# Add entries using the following format -
#     ("<executable>", "<full path to icon>")
#------------------------------------------------------------------------------
LAUNCH_LIST     = [
                   ("xdotool key ctrl+alt+q", "/usr/share/pixmaps/openbox.xbm"), 
                  ]

```

Then you need to include the launch list in the panel layout section (line 146):
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
TASKS           = 2             # Task names section 
TRAY            = 3             # System tray section
CLOCK           = 4             # Clock section
LAUNCHER        = 1             # Application launcher section

```

---

### Post by rtom on 2008-08-15
That's working, thank you, now I have the Openbox menu klicking the panel. I just added the command to the desktop section

```
if button == 1:
        os.system("xdotool key ctrl+alt+q")
```

---

### Post by ddnev45 on 2008-08-26
> **urukrama said:**
> Very simple pypanel :-) I only use the system tray. Note that you need to apply [this patch]("http://bbs.archlinux.org/viewtopic.php?pid=261501") to pypanel for this configuration to work.

Here is the config file:

```
#------------------------------------------------------------------------------
#
#                         PyPanel v2.4 Configuration
#
# This configuration file is a Python script that will be executed when
# PyPanel is started.  In order for PyPanel to start properly, make sure that
# this file contains proper Python formatting and no syntax errors.
#------------------------------------------------------------------------------
VERSION         = 2.4           # Config file version

#------------------------------------------------------------------------------
# Colors: Format is hex triplet - 0xrrggbb
#------------------------------------------------------------------------------
BG_COLOR        = "0x3C4746"    # Panel background and tinting color
TASK_COLOR      = "0x859F9C"    # Normal task name color 
FOCUSED_COLOR   = "0x3C4746"    # Focused task name color
SHADED_COLOR    = "0x859F9C"    # Shaded task name color 
MINIMIZED_COLOR = "0x859F9C"    # Minimized task name color 
DESKTOP_COLOR   = "0x3C4746"    # Desktop name color
CLOCK_COLOR     = "0x3C4746"    # Clock text color
LINE_COLOR      = "0x758C8A"    # Vertical line color

# Text Shadow Colors
TASK_SHADOW_COLOR      = "0x010100"
FOCUSED_SHADOW_COLOR   = "0x010100"
SHADED_SHADOW_COLOR    = "0x010100"
MINIMIZED_SHADOW_COLOR = "0x010100" 
DESKTOP_SHADOW_COLOR   = "0x871706"
CLOCK_SHADOW_COLOR     = "0x871706"

#------------------------------------------------------------------------------
# Panel Spacing and Location Options: Measured in pixels
#------------------------------------------------------------------------------
P_LOCATION      = 1            # Panel placement: 0 = top, 1 = bottom
P_WIDTH         = 50             # Panel width: 0 = Use full screen width
P_START         = 4             # Starting X coordinate of the panel
P_SPACER        = 12             # Spacing between panel objects
P_HEIGHT        = 22            # Panel height

P_L_BUFF        = 3
P_R_BUFF        = 0
P_T_BUFF        = 0
P_B_BUFF        = 3


#------------------------------------------------------------------------------
# Icon Size Options: Measured in pixels
#------------------------------------------------------------------------------
I_HEIGHT        = 16            # Panel application icon height
I_WIDTH         = 16            # Panel application icon Width 
APPL_I_HEIGHT   = 16            # Application launcher icon height
APPL_I_WIDTH    = 16            # Application launcher icon width
TRAY_I_HEIGHT   = 16            # System tray icon height (usually 16 or 24)
TRAY_I_WIDTH    = 0            # System tray icon width  (usually 16 or 24)
                                # If TRAY_I_WIDTH is set to 0, then the
                                # width specified by the tray app will be used
                                
#------------------------------------------------------------------------------
# Panel Clock Format: 'man strftime' for detailed formatting options and help
#------------------------------------------------------------------------------
CLOCK_FORMAT    = "%H:%M"    # Ex: 2004-09-25 17:45 

#------------------------------------------------------------------------------
# Clock Delay: Seconds between each clock update during periods of inactivity
#------------------------------------------------------------------------------
CLOCK_DELAY     = 5

#------------------------------------------------------------------------------
# Hidden Application List: Apps listed here will not be display on the panel
# The application name is its WM_CLASS name, use 'xprop' to find WM_CLASS
# Ex: ["xmms", "xine", "gDesklets"]
#------------------------------------------------------------------------------
HIDE_LIST       = ["netwmpager"]            
                   
#------------------------------------------------------------------------------
# Hidden Panel Size: Size of the panel when it's hidden/minimized
#------------------------------------------------------------------------------
HIDDEN_SIZE     = 2

#------------------------------------------------------------------------------
# Panel Text Font: This option takes either a traditional or Xft font string 
# Ex: "-schumacher-clean-medium-r-normal-*-12-*-*-*-*-*-*-*"
#     "aquafont-8" 
#------------------------------------------------------------------------------
FONT            = "Corbel-8:bold"

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
                   ("gnome-volume-control", "/usr/share/icons/gnome/24x24/stock/media/stock_volume.png")
                  ]

#------------------------------------------------------------------------------
# Background Alpha/Shade Level: 0 (Fully Translucent) -> 255 (Fully Opaque)
# BG_COLOR is used for tinting
#------------------------------------------------------------------------------
SHADE           = 255

#------------------------------------------------------------------------------
# Misc. Options: 1 = Enabled/Yes, 0 = Disabled/No
#------------------------------------------------------------------------------
ABOVE           = 0             # Panel is always above other apps
APPICONS        = 0             # Show application icons
AUTOHIDE        = 0             # Autohide uses the CLOCK_DELAY timer above
SHADOWS         = 0             # Show text shadows
SHOWLINES       = 0             # Show object seperation lines
SHOWBORDER      = 1             # Show a border around the panel

#------------------------------------------------------------------------------
# Desktop Names: Configure the names of your desktops
# If the option is [], PyPanel will attempt to use the desktop name specified
# by the XServer, if that fails it will use the desktop number as its name
# Ex. ["One", "Two", "Three", "Four", "Five", "Six", "Seven", "Eight"]
#------------------------------------------------------------------------------
DESKTOP_NAMES   = ["one", "two", "three"]

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
TRAY            = 1          	# System tray section
CLOCK           = 0             # Clock section
LAUNCHER        = 0             # Application launcher section

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
        pp.showDesktop()
    elif button == 3:
        os.system("tabble &")
    elif button == 4:
        pp.changeDesktop(1)
    elif button == 5:
        pp.changeDesktop(-1)
        
#--------------------------------
def clockButtonEvent(pp, button):
#--------------------------------
    """ Button event handler for the panel's clock object """
    
    if button == 1:
        os.system("/home/urukrama/.scripts/dzen_calendar &")
    elif button == 2:
        pass
    elif button == 3:
        os.system("orage &") 
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
        #if "xmms" in task.tclass:
        #    pp.toggleMinimize(task)
        #else:
        #    pp.toggleShade(task)
	os.system("wmctrl -r :ACTIVE: -t 2 &")
    elif button == 4:
        pp.taskRaise(task, focus=1)
    elif button == 5:
        pp.taskLower(task, focus=0)
        

```

And here is a screenshot:

(The conky and visibility configs can be found [here]("http://ubuntuforums.org/showthread.php?p=5156646#post5156646") and [here]("http://ubuntuforums.org/showthread.php?p=5156614#post5156614"))

I'm only using the system tray as well with openbox; will the update notification work in pypanel, or is that strictly a gnome feature?

---

### Post by ddnev45 on 2008-08-26
the screenshots that didn't load.

---

### Post by jjgomera on 2008-08-27
> **ddnev45 said:**
> I'm only using the system tray as well with openbox; will the update notification work in pypanel, or is that strictly a gnome feature?
for me dont work with pypanel and trayer

I have add yo autostart file this command to check when system start:

xterm -e "sudo aptitude update && sudo aptitude upgrade"

---

### Post by ddnev45 on 2008-08-27
I thought that might be the case, and I'd have to use a solution similar to yours.

---

### Post by cardiel on 2008-09-19
> **ddnev45 said:**
> the screenshots that didn't load.

What kind of panel do you use it bottom of the screen??

---

### Post by ddnev45 on 2008-09-19
Tint

[http://code.google.com/p/tint2/](http://code.google.com/p/tint2/)

---

### Post by cardiel on 2008-09-20
> **ddnev45 said:**
> Tint

[http://code.google.com/p/tint2/](http://code.google.com/p/tint2/)

Could you share your tintrc file?

---

### Post by ddnev45 on 2008-09-21
Here's the current one.

---

### Post by Stan_1936 on 2008-09-21
I thought that pypanel was no longer being actively developed.  It's a real shame because it has a very minimalistic feel...I really liked using it.

---

### Post by dbbolton on 2008-09-21
> **Stan_1936 said:**
> I thought that pypanel was no longer being actively developed.  It's a real shame because it has a very minimalistic feel...I really liked using it.
As far as I know, pypanel is no longer in development, but there have been a few patches released for it. However, tint2 is still in development.

---

