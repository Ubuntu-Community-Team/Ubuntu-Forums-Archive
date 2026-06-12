---
title: "New Release!!"
date: 2006-08-03
forum: Ubuntu System Panel
---

### Post by chanders on 2006-08-03
Seriously.. **DO NOT POST IN THIS THREAD**


Date: Thu,  03 Aug 2006 21:10:20 -0400
Ver 0.32
   * Applet name and icon changes on the fly
   * Metacity Focus bug fixed (quick hack)
   * USP now loads gtk bookmarks on first start (thanks Mat)
   * System menu 'flash while change' fixed (thanks vonpng)
   * Search bar can now be hidden
   * Search bar is now full length and auto-sizes
   * Search button replaced with search icon

---

### Post by chanders on 2006-08-07
**DO NOT POST IN THIS THREAD**

Date: Mon,  07 Aug 2006 02:15:43 -0400
Ver 0.33
   * Quit dismisses panel before showing quit options
   * Added option to set 'Places' font size
   * Changes in icon sizes and text sizes no longer require a restart
   * Fixed apps opening in root directory
   * Logout command configurable (For XFCE/KDE) users
   * 'All Applications' now show the GNOME menu EXACTLY
   * Custom icons can now be set for 'Places' and 'Applications'
   * Translation added for es, fr_FR, nl_BE, hu, el_GR
   * swap_generic_icons no longer require a restart

---

### Post by chanders on 2006-08-12
**DO NOT POST IN THIS THREAD**

Date: Sat,  12 Aug 2006 12:15:47 -0400
Ver 0.40
   * Added plugin support
   * Added some missing changes to support strings with  quotes in .desktop files
   * Fixed Bug #55793 (.desktop files with spaces and reserved chars (%f,%F...)
   * Fixed Bug #54938 (Using Pango.Ellipsize now to shorten words)
   * Swapped all the spaces for tabs to make developement easier
   * If favourites list is empty or on first start, USP now opens to the 'All Applications' section
   * Upgraded Hungarian translation files

I just want to thank all the developers for taking time off to help with USP, without them it would have taken much longer to get all this done
Now on to the good news! The Plugin System is finally here. Please read the following carefully to avoid asking the same questions over and over.

Notes:
* USP is now all plugin based. Every item in USP is now a plugin.
* USP comes with seven (7) plugins pre-installed with three (3) loaded as the default
* The plugins are Places, Applications, System Management, Computer, Time, Calendar and Weather
* There is a known issue where the pane separators dont get hidden if all the plugins are hidden. This will be fixed in a subsequent release

Compiz users should be familar with the loading of the plugins but I will explain for the benefit of the others..

1. The plugins list is stored in /apps/usp/plugins_list
2. Plugins load in the order they are in the list
3. Plugins load one after the other in a VERTICAL fashion
4. To have a plugin start in a new pane, insert "newpane" in the plugins list 
5. Plugin names are CASE SENSITIVE
6. Clicking on the plugin title causes it to be minimized into the plugin tray (previously known as the toggle pane)
7. Clicking on the buttons in the plugin tray causes the plugin to be restored



Here is a list of the plugins and some info

_Places_
This is the standard Places pane that was in the older versions on USP, and no functionality has changed. 

Plugin Name: **places**
Plugin Settings: Todo - move config into /apps/usp/plugins


_Applications_
This is the standard Applications pane that was in the older versions on USP, and no functionality has changed.

Plugin Name: **applications**
Plugin Settings: Todo - move config into /apps/usp/plugins


_System Management_
This is the standard System Management pane that was in the older versions on USP, and no functionality has changed.

Plugin Name: **system_management**
Plugin Settings: Todo - move config into /apps/usp/plugins


_Computer_
This is the standard Computer pane that was in the older versions on USP, and no functionality has changed.

Plugin Name: **USPcomputer**
Plugin Settings: Settings are stored in /apps/usp/plugins/computer


_Time_
This is a new time plugin displaying the time and date in a digital format

Plugin Name: **USPtime**
Plugin Settings: No settings at this time

[IMG]http://img227.imageshack.us/img227/4426/usptimefs5.jpg[/IMG]

_Calendar_
This is a new calendar plugin displaying the time and date in a digital format

Plugin Name: **USPcalendar**
Plugin Settings: No settings at this time

[IMG]http://img227.imageshack.us/img227/366/uspcalendarba3.jpg[/IMG]

_Weather_
This is a new weather plugin displaying the weather in a digital format

Plugin Name: **weather**
Plugin Settings: No settings at this time
Notes: This is _experimental_ and if your internet connection is not fast it will cause USP to wait until it gets data. It is just a test.

[IMG]http://img227.imageshack.us/img227/6195/weatherfm8.jpg[/IMG]

Custom Screenshots

Long across
[IMG]http://img227.imageshack.us/img227/9615/acrossrh2.jpg[/IMG]

Vertical
[IMG]http://img227.imageshack.us/img227/7193/verticalpa5.jpg[/IMG]


Some keys in USP are depreciated so you can go ahead and unset them (right click -> unset key)

/apps/usp/pane_order
/apps/usp/system_command1
/apps/usp/system_command2
/apps/usp/system_command3
/apps/usp/system_command4
/apps/usp/system_command5
/apps/usp/eu_date_format
/apps/usp/network_interface
/apps/usp/settings_font_size
/apps/usp/hide_applications
/apps/usp/hide_places
/apps/usp/hide_system
there may be more... I will update the list later...

---

### Post by chanders on 2006-08-13
**DO NOT POST IN THIS THREAD**

Date: Sun, 13 Aug 2006 23:06:47 -0400
Ver 0.41
  * Added height setting for places and applications plugins

---

### Post by thelinux_guy on 2006-10-17
Wow,I really like this application! Nice work guys,It installed with no problems and works great with my desktop :-D I think this is one of those key applications that ubuntu is missing :)

---

### Post by installer on 2006-11-15
[QUOTE=chanders;1376873]**DO NOT POST IN THIS THREAD**




[COLOR="Sienna"][SIZE="7"]OK ![/SIZE][/COLOR]

---

### Post by Malac on 2008-04-28
[B]DO NOT POST IN THIS THREAD

[/B]I know it says don't post but sorry chanders :).
As some people have been installing the old version from posts 1-4 and having problems.
 
The latest version of USP and install instructions are available via the SVN here:
[http://code.google.com/p/ubuntu-system-panel/w/list](http://code.google.com/p/ubuntu-system-panel/w/list)
Please install this version instead of the one higher up using the instructions on the Installation page.

---

### Post by Malac on 2009-05-14
[B]DO NOT POST IN THIS THREAD

[/B]Okay I have finally compiled a .deb file for usp2 this does not contain the unsupported extra plugins which still need to be downloaded from the SVN.
 
This is the Final Release as I wish to start concentrating any effort on USP3.
There are still one or two outstanding bugs but I don't see any benefit in delaying the release for these few as they only effect one or two people in specific circumstances.
 
Anyway here it is : [ATTACH]117875[/ATTACH]
Please let me know if this does not install as all my test systems already have usp on so I have not had a chance to test it.
 
deskbar-applet has been added as a dependancy to enable use of their keybinder code as this is compatible with 64 bit systems as well and doesn't depend on libgnome-desktop.so.xx.x being linked to. This is hopefully a temporary dependancy until I can figure out compiling just their keybinder code as part of the .deb

---

### Post by OldManRiver on 2009-05-29
All,

Link to or Sticky with project description and documentation please.

I may want to help, but can't say without review.

OMR

---

### Post by Malac on 2009-06-20
[B]DO NOT POST IN THIS THREAD

[/B]Update deb file version 2.00.05

Added mount command to right-click menu in places. Drives don't disappear when unmounted.
Plus translations and a few tweaks.

Here it is : [ATTACH]119027[/ATTACH]

---

### Post by Malac on 2009-07-12
[B]DO NOT POST IN THIS THREAD

[/B]Update deb file version 2.00.05-4ubuntu1
Fix for menu not closing or re-opening on hotkey regression
Fix for computer plugin showing screen frequency as 0

Here it is : [ATTACH]120974[/ATTACH]

And the unsupported extra/add-on plugins : [ATTACH]122167[/ATTACH]

---

### Post by Malac on 2009-07-26
[B]DO NOT POST IN THIS THREAD

[/B]Update deb file version 2.00.05-5ubuntu1
Fix for non-fatal crash on start of login, self.client not registered before first call.
Updated calculator layout in extras.

Here it is : [ATTACH]122498[/ATTACH]

And the unsupported extra/add-on plugins : [ATTACH]122499[/ATTACH]

---

### Post by Malac on 2009-08-24
[B]DO NOT POST IN THIS THREAD

[/B]Update deb file version 2.00.06-2ubuntu1
Added French translations and bug fix for icon size 2 defaulting to size 1.
Added Missing translation file usp2.po and .mo for all languages.
Extras Unchanged
Here it is :[ATTACH]126439[/ATTACH]

And the unsupported/untranslated extra/add-on plugins : [ATTACH]126107[/ATTACH]

---

### Post by Malac on 2009-11-23
[B]DO NOT POST IN THIS THREAD

[/B]Update deb file version 2.00.07-1ubuntu1
Added translations for it_IT, nl_NL, pt_BR.
Added option to stop favourites appearing in Recent.
Extras Unchanged
Here it is : [ATTACH]137322[/ATTACH]

And the unsupported/untranslated extra/add-on plugins : [ATTACH]137323[/ATTACH]

---

