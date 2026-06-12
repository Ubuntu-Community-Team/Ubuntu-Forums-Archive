---
title: "[light version of KDE] Using Kwin only as Window manager"
date: 2006-12-17
forum: The Cafe
---

### Post by patrick295767 on 2006-12-17
Hello, 

This purpose of this project is to use KDE on an old Laptop. 
If you would like to help in having light version of KDE wiht processes and soo on, please post your scripts !!
 
Nota: the kcontrol works great !!!
You can change everythg as keyboard; desktops, keyboard bindings, styles, ;...  Then, enjoy this [link]("http://www.kde-look.org/")

 
------------------------------
Installation Steps
------------------------------
1/ ```
apt-get -f install kdeartwork kdeartwork-theme-window styleclock kwin kcontrol  pypanel  
```
  
2/ then add this file:
/usr/share/xsessions/kwin.desktop:
```
[Desktop Entry]
Encoding=UTF-8
Name=kwin
Comment=Kwin from KDE Highly configurable and low resource X11 Window manager
Exec=/usr/bin/startkwin
Terminal=True
TryExec=/usr/bin/startkwin
Type=Application

[Window Manager]
SessionManaged=true

```
 
3/ then add this file:
/usr/bin/startkwin
```
#!/bin/sh
# $Id: startkwin.in 4081 2005-07-12 04:56:05Z mathias $

command="`basename \"$0\"`"
startup=~/.kwin/startup

mkdir ~/.kwin


while [ $# -gt 0 ]; do
    case "$1" in
        -c|--config)
            if [ $# -lt 2 ]; then
                echo "$command:error, missing argument"
                exit 1
            fi
            shift
            startup=$1
        ;;
        -h|--help) cat <<EOF
Usage: $command [-h] [-c startupfile]
EOF
        exit
        ;;
    esac
    shift
done

if [ -x "$startup" ]; then
    exec "$startup"
elif [ -r "$startup" ]; then
    exec sh "$startup"
else
    if [ ! -d ~/.kwin ]; then
	mkdir -p ~/.kwin/{backgrounds,styles,pixmaps}
    fi
    if [ ! -r "$startup" ]; then
        ( cat << EOF
# kwin startup-script:
#
# Lines starting with a '#' are ignored.

# You can set your favourite wallpaper here if you don't want
# to do it from your style.
#
# bsetbg -f ~/pictures/wallpaper.png
#
# This sets a black background

/usr/bin/fbsetroot -solid black

# This shows the kwin-splash-screen
# fbsetbg -C /usr/share/kwin/splash.jpg

# Other examples. Check man xset for details.
#
# Turn off beeps:
# xset -b
#
# Increase the keyboard repeat-rate:
# xset r rate 195 35
#
# Your own fonts-dir:
# xset +fp $HOME/.font
#
# Your favourite mouse cursor:
# xsetroot -cursor_name right_ptr
#
# Change your keymap:
# xmodmap ~/.Xmodmap



# Applications you want to run with kwin.
# MAKE SURE THAT APPS THAT KEEP RUNNING HAVE AN ''&'' AT THE END.
#
# unclutter -idle 2 &
# wmnd &
# wmsmixer -w &
# idesk &

pypanel &

# And last but not least we start kwin.
# Because it is the last app you have to run it with ''exec'' before it.

exec /usr/bin/kwin
# or if you want to keep a log:
# exec /usr/bin/kwin -log ~/.kwin/log
EOF
    ) > "$startup"
    fi
    chmod 755 "$startup"
    exec "$startup"
fi

```
  
4/ then add this file:
/usr/bin/logoutkwin
```
#!/bin/sh
# $Id: startkwin.in 4081 2005-07-12 04:56:05Z mathias $
kwin --replace

```
  
4.5/ 
```
chmod uog+rx /usr/bin/startkwin 
chmod uog+rx /usr/bin/logoutkwin
```

  5/ You can use kicker or gnome-panel ... 
... but I prefer pypanl because of its lightweight :
so add if you would like:
/home/myusername/.pypanelrc
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
TASK_COLOR      = "0x009900"    # Normal task name color 
FOCUSED_COLOR   = "0x00FF00"    # Focused task name color
SHADED_COLOR    = "0x009900"    # Shaded task name color 
MINIMIZED_COLOR = "0x00AA00"    # Minimized task name color 
DESKTOP_COLOR   = "0x00FF00"    # Desktop name color
CLOCK_COLOR     = "0x00FF00"    # Clock text color
LINE_COLOR      = "0x0000FF"    # Vertical line color

#------------------------------------------------------------------------------
# Panel Spacing and Location Options: Measured in pixels
#------------------------------------------------------------------------------
P_LOCATION      = 1             # Panel placement: 0 = top, 1 = bottom
P_WIDTH         = 750             # Panel width: 0 = Use full screen width
P_START         = 75             # Starting X coordinate of the panel
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
FONT            = "bitstream vera sans-12"

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
                   ("aterm", "/usr/share/icons/crystalsvg/48x48/apps/terminal.png"),
                   ("firefox", "/usr/share/icons/crystalsvg/48x48/apps/firefox.png"),
                   ("rox", "/usr/share/icons/crystalsvg/48x48/apps/systemtray.png"),   
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
CLOCK           = 2             # Clock section
LAUNCHER        = 5             # Application launcher section

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
        
    if button == 3:
        pp.changeDesktop(-1)
    elif button == 2:
        pp.changeDesktop(2)
    elif button == 1:
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

6/ /etc/init.d/gdm restart

------------------------------- 
Enjoy !
   
   to exit: 
In console, type :
logoutkwin


[SIZE="4"]**Enjoy KCONTROL of KDE !!!!!!!!!!!!!!!!!!!**[/SIZE]

    
  
---------------
Further work:
( Please help)
 - A better logout feature !
 - the pager that should be for me horizontal, I dont know how to make it as :    desk1  desk2 desk3 desk4
 - by default, you will have:
desk1 desk3
desk2 desk4

---

