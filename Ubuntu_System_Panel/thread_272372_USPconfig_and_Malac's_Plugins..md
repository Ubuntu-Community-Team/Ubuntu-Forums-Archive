---
title: "USPconfig and Malac's Plugins."
date: 2006-10-06
forum: Ubuntu System Panel
---

### Post by Malac on 2006-10-06
[SIZE=4]**PLEASE DO NOT POST ON THIS THREAD.**[/SIZE]
[SIZE=4]For USP upto 0.41 _only_.[/SIZE]
[SIZE=4]DO NOT USE WITH ALPHA USP 1.9x(or above).[/SIZE]
[SIZE=4]USP 1.9x and above now have USPconfig incorporated in the .deb package.[/SIZE]
[SIZE=4]Go here for instructions on how to get the latest SVN version [/SIZE][http://code.google.com/p/ubuntu-system-panel/](http://code.google.com/p/ubuntu-system-panel/)
Or here [http://ubuntuforums.org/showpost.php?p=7277941&postcount=6](http://ubuntuforums.org/showpost.php?p=7277941&postcount=6) for a .deb package.
 
(Please remember these are all beta versions and as such are subject to periodic change as bugs are removed and new "features" are added.)
[SIZE=4]
[SIZE=4]I started this thread as a few people have been complaining they have to trawl the forums for the USP plugins and USPconfig application.[/SIZE]
[SIZE=4]This thread is a single location for the latest versions of USPconfig and the plugins.[/SIZE]
[SIZE=4]They will be listed one plugin per post with relevant information on GConf Keys and what they do.[/SIZE]
[SIZE=4]A version number has been assigned so you know if you have the latest version these have been started at 0.4.[/SIZE]
 
[SIZE=4]**If you have any support requests or problems please do not post them here.**[/SIZE]
**[SIZE=4]If you have any plugins you'd like put here, please e-mail them to Malac[at]tiscali[dot]co[dot]uk[/SIZE]**
**[SIZE=4]where [at]=@ and [dot]=. with subject line "USP plugin".[/SIZE]**
[SIZE=4]Or post ideas for plugins on the USP "Plugin Development" thread here:[/SIZE]
[SIZE=4][http://www.ubuntuforums.org/showthread.php?t=235090](http://www.ubuntuforums.org/showthread.php?t=235090)[/SIZE]
[SIZE=4]and I'll see if I can do them. :)[/SIZE]
 
[SIZE=4]Thanks, Malac.[/SIZE]
 
[/SIZE]

---

### Post by Malac on 2006-10-06
**_[SIZE=3]This is NOT for use on Version 1.9x or Later[/SIZE]_**
 
**_[SIZE=3]USPconfig Application[/SIZE]_**
An application to configure USP without using gconf-editor.
[ATTACH]16990[/ATTACH]
 
Untar the files into /usr/bin or /usr/sbin as root
or your home folder somewhere.
 
Create a launcher (in Alacarte if you want) then drag it to USP.
 
**VERSION 0.71**
 
**UPDATED : Sunday, 10 December 2006**
_Very_ minor upgrade to .deb file only.
This includes a .desktop menu file which should mean USPconfig appears under Applications->System Tools. (I hope) :)
It should appear in Synaptic also, which should aid with removing it or upgrading to the 1.0 version when that comes out.
Includes USP as a dependency and checks that you have the correct version installed.
As usual any problems pm me to let me know and I'll try to sort them asap.

---

### Post by Malac on 2006-10-06
[SIZE=3]_**USPtime**_
[SIZE=2]A Date/Time plugin with display format[/SIZE][/SIZE][SIZE=3][SIZE=2] options.
[/SIZE][/SIZE][ATTACH]16971[/ATTACH]

[SIZE=2]_ Gconf Keys:_[/SIZE]
/apps/usp/plugins/datetime/eu_date_format
/apps/usp/plugins/datetime/settings_date_bold
/apps/usp/plugins/datetime/settings_date_font_size
/apps/usp/plugins/datetime/settings_date_sep
/apps/usp/plugins/datetime/settings_date_string
/apps/usp/plugins/datetime/settings_day_string
/apps/usp/plugins/datetime/settings_time_12_hour
/apps/usp/plugins/datetime/settings_time_bold
/apps/usp/plugins/datetime/settings_time_font_size
/apps/usp/plugins/datetime/settings_time_hide_seconds
/apps/usp/plugins/datetime/system_command1
 /apps/usp/plugins/datetime/analog_clock
 /apps/usp/plugins/datetime/analog_clock_diameter
  /apps/usp/plugins/datetime/analog_clock_edge_color
    /apps/usp/plugins/datetime/analog_clock_face_color
    /apps/usp/plugins/datetime/analog_clock_second_color
 
**VERSION 0.71**
With choice of Analog Clock
[ATTACH]18700[/ATTACH]
/apps/usp/plugins/datetime/settings_time_hide_seconds works on this clock too.
Values for these GConf Keys :
/apps/usp/plugins/datetime/analog_clock_edge_color
     /apps/usp/plugins/datetime/analog_clock_face_color
     /apps/usp/plugins/datetime/analog_clock_second_color
can be set using "#FFFFFF" type notation or /etc/X11/rgb.txt names i.e. black, white, DarkSlateGrey, etc.
  However due to dithering effects some colours may not show correctly i.e. grey second hand on black face color.
Usually names/colours like, 'red', 'green', 'blue', '#FF0000', '#00FF00', '#0000FF' are okay.
You'll just have to experiment. :)

Credit to: Lawrence Oluyede's Python port of Davyd Madeley's original C analog clock.

---

### Post by Malac on 2006-10-06
[U][SIZE=3][B]USPterm
[/B][/SIZE][/U][SIZE=3][SIZE=2]Terminal Plugin.
[/SIZE][/SIZE][ATTACH]16972[/ATTACH]
[SIZE=3][SIZE=2]
_Gconf Keys_
[/SIZE][/SIZE]/apps/usp/plugins/terminal/background_color
/apps/usp/plugins/terminal/back_picture
/apps/usp/plugins/terminal/foreground_color
/apps/usp/plugins/terminal/height
/apps/usp/plugins/terminal/use_back_picture
/apps/usp/plugins/terminal/width
 /apps/usp/plugins/terminal/transparent_background
  /apps/usp/plugins/terminal/background_saturation
 
[B]VERSION 0.51
[/B][ATTACH]17551[/ATTACH]
Added transparent background.
Saturation is a percentage of transparency i.e. 100=fully, 10=barely transparent.
Saturation also works on the picture. i.e. 100= full picture, 10=barely there.

[SIZE=2]_Please Note_[/SIZE]:
The transparency is the same as gnome-terminal transparency(i.e. it will show the desktop through it but not the other windows, on metacity), unless you have used the true transparency hack. Can someone let me know if this works on compiz/beryl.
If you are using gconf-editor then *transparent_background* overrides *use_back_picture* be sure to unset *transparent_background* if you want to see you're picture again

---

### Post by Malac on 2006-10-06
[SIZE=3]_**USPuser**_
[SIZE=2]User Display Plugin
[/SIZE][/SIZE][ATTACH]16975[/ATTACH][SIZE=3][SIZE=2]
[U]
Gconf Keys[/U]
[/SIZE][/SIZE]/apps/usp/plugins/user/hide_logged_on
/apps/usp/plugins/user/hide_name
/apps/usp/plugins/user/name_below
/apps/usp/plugins/user/settings_font_bold
/apps/usp/plugins/user/settings_font_size
/apps/usp/plugins/user/animated_picture

[B]VERSION 0.7
Uploaded: Monday, 08 January 2007
[/B]Can now use a custom user picture which may be animated (only tested with gif format) anyone want to test others and pm me with the details feel free.
 if /apps/usp/plugins/user/animated_picture is left blank the users .face file will be used if not then the file name entered will be used instead this can be static or animated.
Update for multi-user bug not showing correct user.

---

### Post by Malac on 2006-10-06
[U][B][SIZE=3]USPcomputer
[/SIZE][/B][/U]Settings Plugin
[ATTACH]16980[/ATTACH]
[SIZE=3][SIZE=2][U]Gconf Keys
[/U][/SIZE][/SIZE]/apps/usp/plugins/computer/hide_computer
/apps/usp/plugins/computer/hide_control
/apps/usp/plugins/computer/hide_date
/apps/usp/plugins/computer/hide_net
/apps/usp/plugins/computer/hide_screen
/apps/usp/plugins/computer/hide_theme
/apps/usp/plugins/computer/network_interface
/apps/usp/plugins/computer/settings_font_size
/apps/usp/plugins/computer/system_command1
/apps/usp/plugins/computer/system_command2
/apps/usp/plugins/computer/system_command4
/apps/usp/plugins/computer/system_command5
/apps/usp/plugins/computer/system_command6

_Note_
/apps/usp/plugins/computer/system_command3
Has been moved to /apps/usp/plugins/datetime/system_command1

**VERSION 0.4**

---

### Post by Malac on 2006-10-06
_**[SIZE=3]USPrecent[/SIZE]**_[SIZE=3]
[/SIZE]Recent Documents Plugin
[ATTACH]18607[/ATTACH]
Uses the Gnome .recently-used list
Dapper Version checks it every 1 seconds by default. As some people have recorded around 5% cpu usage when this check is done every 1 seconds, you can change this by setting poll_interval to the number of seconds between checks using either gconf-editor or the recent tab in USPconfig to lessen this load. :)

[SIZE=2]_Gconf Keys_[/SIZE]
/apps/usp/plugins/recent/height
/apps/usp/plugins/recent/num_entries (Set this to -1 to view all entries, * This is only in the Edgy Version.)
/apps/usp/plugins/recent/recent_font_size
/apps/usp/plugins/recent/width
 /apps/usp/plugins/recent/poll_interval (*This is removed in the Edgy Version and may be deleted in gconf-editor)
  /apps/usp/plugins/recent/show_fullpath_tips(* This is only in the Edgy Version.)

**VERSION 0.6 Dapper Version **USPrecent_Dapper.tar.gz
Fix for URI spaces in file and not showing recent list until first poll_interval.
Have decided to leave this on as a couple of people have reported that the Edgy one doesn't work in Dapper.
(My thanks to those prepared to test and pm me with results.)

**VERSION 0.74 Edgy Version** USPrecent.tar.gz
**Updated : Tuesday, 31 October 2006**
Using Gnome's recent list manager. No longer polls but waits for the list to change so should lessen cpu load.
Fixed "special" characters showing %20 for space, %26 for ampersand, %3A for colon, etc.

---

### Post by Malac on 2006-10-06
[B][U][SIZE=3]USPcalc
[/SIZE][/U][/B]Simple Calculator
[ATTACH]16984[/ATTACH]
[SIZE=2]_Gconf Keys_[/SIZE]
None

**VERSION 0.4**

---

### Post by Malac on 2006-10-06
[U][B][SIZE=3]USPnotes
[/SIZE][/B][/U]Small Quick Notes Plugin
[ATTACH]16987[/ATTACH]
[SIZE=2]_Gconf Keys_[/SIZE]
/apps/usp/plugins/notes/height
/apps/usp/plugins/notes/width

**VERSION 0.4**

---

### Post by Malac on 2006-10-07
[SIZE=3]_**USPcalendar**_[/SIZE]
Same as the standard calendar but opens evolution when clicked.
(USPremind is the seperate tasks and appointments plugin or use USPcalrem which combines both.)
[ATTACH]17020[/ATTACH]
[SIZE=2][U]GConf Keys
[/U][/SIZE]None

The previous key 
/apps/usp/plugins/calendar/system_command1
is no longer used.
You may unset it in gconf-editor

**VERSION 0.4**
** Note: This plugin now opens evolution on the date clicked**. :)

---

### Post by Malac on 2006-10-08
[SIZE=3]**_USPremind_**[/SIZE]
Tasks and Appointments from Evolution
[ATTACH]17126[/ATTACH]
_[SIZE=2]Gconf Keys[/SIZE]_
/apps/usp/plugins/calendar/heading_font_size
/apps/usp/plugins/calendar/height
/apps/usp/plugins/calendar/height_appoints
/apps/usp/plugins/calendar/height_tasks
/apps/usp/plugins/calendar/item_font_size
/apps/usp/plugins/calendar/width

[B]VERSION 0.5
Updated : Tuesday, 19 December 2006[/B]
It seems Evolution has changed the format of the .ics files and the way it stores the dates so I have changed this to reflect the change.
Please pm me if this stops working for you with the new version.

---

### Post by Malac on 2006-10-08
[SIZE=3]**_USPcalrem_**[/SIZE]
Combination of USPcalender and USPremind
[ATTACH]17128[/ATTACH]
_[SIZE=2]Gconf Keys[/SIZE]_
/apps/usp/plugins/calendar/heading_font_size
/apps/usp/plugins/calendar/height
/apps/usp/plugins/calendar/height_appoints
/apps/usp/plugins/calendar/height_tasks
/apps/usp/plugins/calendar/item_font_size
/apps/usp/plugins/calendar/show_tasks_appoints
/apps/usp/plugins/calendar/width

[B]VERSION 0.5
Updated : Tuesday, 19 December 2006[/B]
It seems Evolution has changed the format of the .ics files and the way it stores the dates so I have changed this to reflect the change.
Please pm me if this stops working for you with the new version.

Couldn't decide what to do with this one. At the moment the tasks and appointment window disappears if there are no tasks or appointments but if this causes your menu to "jump" about you may be better with the seperate USPcalendar and USPremind.
If you don't mind the "wasted" space then set the height to allow for when the tasks and appointments are there.

---

### Post by Malac on 2006-11-01
[SIZE=3]**_USPclock_**[/SIZE]
Analog Clock Display
[ATTACH]18687[/ATTACH]
_[SIZE=2]Gconf Keys[/SIZE]_
/apps/usp/plugins/clock/height
/apps/usp/plugins/clock/width

**VERSION 0.5**

Credit to: Lawrence Oluyede's Python port of Davyd Madeley's original C analog clock. :)
Thanks to them.

Also added this functionality to the USPtime plugin. See Page 1

---

### Post by Malac on 2006-11-08
[SIZE=3]**_USPweb_**[/SIZE]
Firefox Browser Bookmarks
[ATTACH]19095[/ATTACH]
_[SIZE=2]Gconf Keys[/SIZE]_
/apps/usp/plugins/internet/height
/apps/usp/plugins/internet/width
/apps/usp/plugins/internet/internet_font_size
/apps/usp/plugins/internet/back_color
/apps/usp/plugins/internet/font_color
 /apps/usp/plugins/internet/bookmark_file

[B]VERSION 0.71
[/B]Fix for displaying the wrong long name instead of the Description.

Works with mozilla-firefox browser.
It works with the bookmarks.html file in the  ~/.mozilla/firefox/<random name>/ folder
Added error checking for opening default files and, if this error occurs, the ability to specify the location of the file manually by placing full path to file in /apps/usp/plugins/internet/bookmark_file or using USPconfig Application

---

