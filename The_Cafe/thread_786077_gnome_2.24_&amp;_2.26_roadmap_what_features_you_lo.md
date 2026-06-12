---
title: "gnome 2.24 &amp; 2.26 roadmap: what features you looking forward to?"
date: 2008-05-07
forum: The Cafe
---

### Post by madjr on 2008-05-07
Basically the future of Ubuntu is written here (or at least 70% of it)

so what features you think will be interesting or help improve gnome in a big way?

maybe some of these features will have a bigger overall impact than we can imagine right now.

Do you think the gnome devs are heading in the right direction? 

any particular aspect you think needs major work?

here are the features for 12 month development
[http://live.gnome.org/RoadMap](http://live.gnome.org/RoadMap)


> **GNOME 2.24**

For Users

Artwork

    * New GNOME default wallpapers
    * Dark widget theme
    * Flat widget theme
    * Compact widget theme for small screens
    * Provide color variations on some of the existing themes
    * Initial set of 256x256 icons
    * Nicer GNOME Panel icons
    * Update outdated desktop emblems
    * Convert more applications to use names from the icon-spec 

Cheese

    *

      OpenGL backend and new effects
    * Improved integration with the desktop
    * Usability improvements
    * Data synchronisation 

Deskbar Applet

    * Capuchin support: easy download of additional plugins from internet
    * Performance improvements
    * Improved del.ico.us support
    * Support for Firefox 3 

Evince Document Viewer

    *

      Annotations support (Google Summer of Code 2007)
    * Performance improvements
    * User interface improvements:
          o Progress feedback when loading a remote file
          o Progress feedback when printing
          o More intuitive sidebar pages 
    *

      Improved accessibility support (GNOME Outreach Program: Accessibility) 

Epiphany Web Browser

    *

      Migration to WebKit 

Evolution Groupware

    * Unified Account Management
    *

      Exchange 2007 support (Pending on licensing resolution)
    * Windows support for Evolution
    * Improved stability and protocol usage (IMAP+Exchange)
    * Disk summary (Means very less memory consumption)
    * Custom header support while sending mails
    * New Bonobo-less composer for Evolution 

Eye of GNOME Image Viewer

    * PNG metadata support (XMP and color profiles)
    * Performance improvements
    * Set of default plugins
    * UI polishing based on users' feedback
    * Migration to gio/vfs 

File Roller Archive Manager

    * Migration to gio/vfs 

Gedit Text Editor

    * Improved startup time
    * Migration to gio/gvfs 

GNOME Control Center

    * New screen resolution settings with support for XRandR 1.2/multihead
    * Migration to gio/gvfs
    * Improved themes/thumbnails handling 

GNOME Calculator

    *

      Improved Q&A and bug fixes
    * GCalctool website 

GNOME Desktop (libgnome-desktop)

    * API for randr management
    *

      Deprecate GnomeDesktopItem, replace it with a proper implementation in GTK+
    * Move docs to GNOME User Guide
    * Deprecate all icons which are not used anymore 

GNOME Developer Docs

    *

      Accessibility Guide for Developers (GNOME Outreach Program: Accessibility)
    * Updated GNOME Documentation Style Guide (to be renamed to GNOME Style Guide) to reflect current technologies and trends
          o Revised terminology recommendations 

GNOME Games

    * General:
          o Online highscores 
    * Aisleriot
          o Theming: backgrounds and card localisation
          o Game layout improvements (ex. adapting to smaller screen size)
          o Keyboard dealing for all games
          o Misc game improvements 
    * Chess
          o Use of libgames-support for Python games
          o Split the GGZ GUI code out of glChess 
    * Gnometris
          o Performance fixes on new theme
          o Graphical indication of rotation point and direction 
    * Robots
          o Resizeable/translateable robots 
    * Sudoku
          o Support for hand-edited puzzles
          o Support for import/export puzzles
          o Puzzle generation performance improvements 

GNOME Keyboard Handling (libgnomekbd)

    * User interface for choosing layouts not only per-country but also per-language 

GNOME Keyring

    * Allow Seahorse to manage encryption keys and certificates
    * Complete the PKCS#11 integration work
    * Support for encryption key unlock and usage constraints (such as timeouts and prompts) 

GNOME Media

    *

      Better integration with PulseAudio
    * Migration to gio/gvfs
    * Improved gstreamer-properties and gnome-audio-profiles-editor (similar to Banshee profiles)
    * Disable GNOME-CD/CDDBSlave/VUMeter by default 

GNOME On-screen Keyboard

    * Possible migration to Python 

GNOME Panel

    * Positioning fixes of applets when Panel size changes
    * Support for setting menubar layout, not only the items in the Applications menu
    * Integration with new GNOME Session Manager 

GNOME Power Manager

    * Improvements on backlight brightness control
    * Allow changing the backlights of all monitors 

GNOME Session Manager

    * Better integration with Autostart
    * More flexibility and convenience for distributors on defining their default session applications
    * D-Bus API for log out/reboot/shutdown (with save session) operations 

GNOME Terminal

    *

      Port to GtkUIManager 

GNOME Utils

    * Baobab
          o Migration to gio/gvfs 
    * Dictionary
          o Support for local files (dict and possibly stardict)
          o Custom definitions to a local database
          o Wikipedia support
          o Show and select sources from the sidebar 
    * GFloppy
          o Replace with the GNOME Formatter, a true media formatter 
    * Screenshot
          o Desktop area grabbing
          o Support actions: save, copy to clipboard, and open with
          o

            Switch save dialog to a pure GtkFileChooser
          o Rewrite the capture logic and make it work properly under Compiz
          o Migration to gio/gvfs 
    * System Log Viewer
          o Plugin system to handle different log sources 

HTTP stack (libsoup)

    * Cookies
    * Caching
    * Better proxy support / use GConf proxy information
    * Gnome Keyring integration
    * Content-Encoding
    * Better SSL support 

Libwnck Window Management Library

    * Better integration with Compiz and other window managers
    * API stabilization work
    * Unified handling virtual desktops and viewports the same way
    * Improved developer docs 

Nautilus File Manager

    * Column-wise view
    * Tabbed interface
    * Key-binding support for Nautilus extensions 

Orca Screen Reader

    * Java platform support
    *

      OpenOffice enhancements and improvements
    * Thunderbird enhancements and improvements
    * Enhancements for people with low vision
    * Better support for control via braille devices
    * Improved developer documentation
    *

      Accessible install for OpenSolaris 

Seahorse Encryption Keys Manager

    * Evolution integration (e-d-s integration, auto-contact creation, photo ID synchronization)
    * Management of gnome-keyring encryption keys and certificates
    * Python bindings for libcryptui
    * Refreshed icons 

Soundjuicer Audio CD Extractor

    * User interface improvements
    * Migration to libmusicbrainz3 

Tomboy Notes

    * Support for attachments, embedded images, etc.
    * Cross-platform improvements 

Totem Movie Player

    * Better DVB support
    * Migration to gio/vfs 

Vinagre Remote Desktop Client

    * Improved bookmarking
          o Allow folders
          o Automatically show Avahi-discovered machines
          o Import/Export bookmarks 
    * Panel applet: quick access to bookmarked and avahi-discovered connections
    * Tabbed interface
    * Better fullscreen mode
    * Send custom keys (like Ctrl-Alt-Del) to the server
    * Control the properties of a connection (like depth color, read-only mode, etc) 

Vino Desktop Remote Access

    * Support for reverse connections
    * Support for connection logging
    * Ability to choose which interface to listen to 

Zenity

    * Multi-task support for progressbar dialog
    * Support for setting label names
    * Improvements on notification icon 

For Developers

Anjuta Integrated Development Environment

    *

      Improvements on GtkSourceView-based editor
    * Easy start-up wizard
    * Improved program execution interface
    * Improved build plugin
    * Port GTK+ 2.10 deprecated APIs
    * Migration to gio/gvfs 

Gail

    * Move Gail into GTK+ 

Glade User Interface Designer

    * New parser, allows plugin backends to define widget-class level definitions of the XML format
    * Allow plugins to define editors for custom properties
    *

      Support for both formats libglade/GtkBuilder, with UI feedback and error summaries regarding incompatibilities in conversions
    * Support targeting of specific toolkit versions
    * New builder features
          o

            Support for GtkLabel attributes property with editor
          o

            Integration of GtkUIManager and GtkActions
          o

            Integration of GtkSizeGroup
          o

            Integration of GtkListStore/GtkTreeStore editors
          o

            Integration of GtkTreeView editor (packing of columns and cell renderers) 

GVFS

    *

      Fix regressions introduced by the transition from GnomeVFS
    * Support for Proxy Auto-configuration (PAC)
    * Configure options for mount points
    * Possible emblems support on gio/gvfs level 

Pango

    *

      Merge all shapers with the ones from Qt in HarfBuzz
    *

      Remove all script shapers, add a single HarfBuzz shaper 

For Everyone

Infrastructure

    *

      Decide on a new Distributed Version Control System (This is not about switching, just deciding and understanding implications)
    * Move buildbot master to elsewhere
    * Add loads more buildbots (needs changes in buildbot)
    * Setup new GNOME website on GNOME servers, if ready
    * Upgrade svn.gnome.org to SVN 1.4+ and setup readonly SVN mirror on container
    * Complete move of sysadmin.gnome.org content to the wiki
    * Document everything; policies, servers, etc
    * Setup slave DNS server on socket
    * Upgrade socket, progress to new Ubuntu LTS 

Proposed modules

Keep in mind that there's no guarantee that the proposed modules will actually be integrated into GNOME.

    *

      Empathy: a rich set of reusable instant messaging widgets, and a GNOME client using those widgets.
    *

      Conduit: a synchronization architecture for the GNOME desktop.
    *

      Hamster: a time tracking applet for the GNOME desktop. 


===========================================


**GNOME 2.26**

For Users

Evolution Groupware

    * IMAP relook/revamp
    * More plugin loaders
    *

      WebKit or GtkMoz* integration
    * Full fledged logging support 

GNOME Control Center

    * Support for launching arbitrary commands via keybindings 

GNOME Media

    *

      Replace gnome-volume-control with a PulseAudio mixer, and/or a higher-level device control UI 

GNOME Power Manager

    *

      Better ConsoleKit and PolicyKit integration 

Gucharmap

    * Ability to print charts of characters with pangocairo 

Nautilus File Manager

    * Toolbar editor
    * Improved list view interaction 

Seahorse Encryption Keys Manager

    * Possibly a Pidgin/Telepathy encryption plugin
    * Digitally signed documents in Evince 

Tomboy Notes

    * Complete cross-platform support 

Vinagre Remote Desktop Client

    * Support for RDP (Microsoft Terminal Services) connections 

Vino Desktop Remote Access

    * Ability to disable wallpaper 

For Developers

Anjuta Integrated Development Environment

    * New Symbol database plugin
    * Improved symbol autocompletion
    * Better Glade integration
    * Automated UI testing
    * Git plugin

---

### Post by techrush on 2008-05-07
Surprised this hasnt picked up more replies so far as this is -literally- the future direction ubuntu will be headed as a gnome based distro. There seems to be a pretty common misconception that most of the changes and new things in ubuntu are contruibuted by canonical itself. In reality its mostly coming from upstream projects like gnome and openoffice.org. 

Anyways it looks like a lot of small refinements that will make the gnome experience better overall. The tabbed interface for nautilus did catch my eye. Will be interesting to see how they implement it.

---

### Post by FuturePilot on 2008-05-07
Looks like they are trying to make the DE even more integrated which is great. I'm looking forward to the completion of the GVFS migration, better PulseAudio support/integration, Webkit, and Nautilus tabs and column views. And hopefully maybe a Restore from Trash feature.[-o<
Looks like some good stuff. :)

---

### Post by nrs on 2008-05-07
All good, nothing in particular.

---

### Post by yatt on 2008-05-07
While I didn't read the whole thing (long changelogs are long), but tabbed browsing in Nautilus is the only thing that really stood out.

What I would like to see is a feature where if you hold a dragged item over a open folder, it opens that folder.

EDIT: It seems they are expanding there set of default themes, which I like the sounds of too. Particularly repeating the same theme in several colors. This is something I have wished most distros would do for a while.

---

### Post by swoll1980 on 2008-05-07
WOW new wallpapers!! I can't wait!!!!111!one

---

### Post by FuturePilot on 2008-05-07
> **yatt said:**
> 

What I would like to see is a feature where if you hold a dragged item over a open folder, it opens that folder.

That would be great.

---

### Post by klange on 2008-05-07
They don't appear to have any intention of giving Nautilus proper multiple wallpaper support, I don't care about much of the other stuff...

---

### Post by madjr on 2008-05-08
> **yatt said:**
> 

What I would like to see is a feature where if you hold a dragged item over a open folder, it opens that folder.



as an option or key-combo it would be cool, but i wouldn't like it on as default.

---

### Post by D-EJ915 on 2008-05-08
> **swoll1980 said:**
> WOW new wallpapers!! I can't wait!!!!111!one
gnome always has had rather lackluster wallpapers compared to KDE, I think gnome's wallpaper support sucks compared to KDE in general, though.  Hopefully they fix that, and that horrid new appearance crap.

---

### Post by gsmanners on 2008-05-08
> GNOME Panel

* Positioning fixes of applets when Panel size changes
* Support for setting menubar layout, not only the items in the Applications menu
* Integration with new GNOME Session Manager

"When Panel size changes"?

This is why I don't use Gnome anymore. Even the developers don't understand their own screw ups. It's a very well documented fact that the positioning of applets varies wildly even when the panel doesn't change in size.

I dare them to fix the bug, but not what they imagine the bug is. Fix the real bugs, then I'll be impressed.

How about fixing the clock so that you can stylize the text in it too? Are Gnome developers even capable of listening?

---

### Post by Sukarn on 2008-05-08
Tabbed nautilus is what I'm looking forward to the most.

---

### Post by graabein on 2008-05-08
I'm still trying to configure xorg to have two separate xscreens and this caused my screen resolution to take a serious hit last night. I noticed that quite a few of the GNOME 2.18/Tango icons in the settings menu don't look good at all at minimum size. I hope some of the GNOME artists put time into completing one or two icon sets. Little things like these affect the overall feel of the DE...

I'm also anxious to try Nautilus with column view. Hope they improve the startup speed of it also. It should also be easier to clean up and decide what applications to launch filetypes with.

About time to fix the panel clock yes...


Update: I use PCManFM instead of Nautilus btw.

---

### Post by Saint Angeles on 2008-05-08
when will we have direct brain-to-computer interfaces?

i mean... its 2008. COME ON! keyboards and mouses are like, super old.

---

### Post by bash on 2008-05-08
OMG! Tabbed nautilus. That I live to day to witness this!

---

### Post by geoken on 2008-05-08
Tabs in nautilus is welcomed, but I still think the state of nautilus is pretty sad. According to this, in a years time, nautilus still wont have feature parity with the >1 year old Dolphin. And that's assuming Dolphin has no new features introduced in that year. 

The latest dolphin already has tabs and column view. It also has grouped view, split view, the drop-down menu pathbar, integrated terminal, and on and on. 

[IMG]http://polishlinux.org/reviews/kde-4-rev-802150/9abfa10d993b1afaa4e6f866108c9197.jpg[/IMG]

---

### Post by Ub1476 on 2008-05-08
KDE/QT, is superior in technology if you ask me.. Too bad I like things simple (gnome), yet functional (kde).

---

### Post by bigbrovar on 2008-05-08
tab browsing on nautilus and global menu bar ..like the mac menu bar on osx

---

### Post by madjr on 2008-05-08
> **gsmanners said:**
> "When Panel size changes"?

This is why I don't use Gnome anymore. Even the developers don't understand their own screw ups. It's a very well documented fact that the positioning of applets varies wildly even when the panel doesn't change in size.

I dare them to fix the bug, but not what they imagine the bug is. Fix the real bugs, then I'll be impressed.

How about fixing the clock so that you can stylize the text in it too? Are Gnome developers even capable of listening?

hmm i don't get the problem with the clock :confused:

---

### Post by maniacmusician on 2008-05-08
gsmanners is saying that they want to be able to change the font of the text and numbers in the clock applet, like in the KDE clock.

---

### Post by days_of_ruin on 2008-05-08
tabbed nautilus == WIN!

---

### Post by b3n87 on 2008-05-08
slow and steady (development) wins the race...

---

### Post by 23meg on 2008-05-11
> **WindowsSucks said:**
> They don't appear to have any intention of giving Nautilus proper multiple wallpaper support, 

No, there's someone working on it:

[http://gsocblog.jsharpe.net/archives/8](http://gsocblog.jsharpe.net/archives/8)

---

### Post by aamukahvi on 2008-05-11
> **gsmanners said:**
> How about fixing the clock so that you can stylize the text in it too? Are Gnome developers even capable of listening?
/apps/panel/clock_screen0/prefs/custom_format:
```
<span size="small" color="#666">%a %d %b</span> <b>%H:%M </b>
```
Also set the "format" key to "custom".

---

### Post by coolen on 2008-08-27
Biggest features for me:

Empathy will finally be included. I understand the reasons it wasn't included sooner, but it does provide some awesome opportunities.
PA integration is also fantastic. PA has the potential to pull together multimedia on the Linux platform. With proper implementation, it could be far more than just a sound server.
Better desktop integration for Cheese. I love that program (save for one irritating bug, which I think is fixed in this release, too) and would love to see it used more fully.
Broader use of GVFS. This will mean a more cohesive experience, and hopefully more innovation as its benefits are seen across the platform.
Also, the inclusion of Clutter is a promising sign. This could mean richer UIs in the short term, and possibly broader improvements to GTK+ itself in the long term.

I'm not all that thrilled with tabbed Nautilus, to be honest. What I'd love would be split view. That'd be something. As it is, tabs may actually slow me down. Another thing I'd like to see in Nautilus (and please, let me know if it's possible now) is the ability to truncate file names to give even spacing. Files with long names throw the entire display into chaos.

---

### Post by mips on 2008-08-27
> **geoken said:**
> 
The latest dolphin already has tabs and column view. It also has grouped view, split view, the drop-down menu pathbar, integrated terminal, and on and on. 

I've always used konqueror and wanderd what the noise was about with dolphin. Recently started using KDEmod4.1 and I must say I really like dolphin, I use it way more than konqueror these days. When I used Gnome I recall not liking nautilus as it felt like a severely lacking tool.

---

### Post by zekopeko on 2008-08-27
> **coolen said:**
> I'm not all that thrilled with tabbed Nautilus, to be honest. What I'd love would be split view. That'd be something. As it is, tabs may actually slow me down. Another thing I'd like to see in Nautilus (and please, let me know if it's possible now) is the ability to truncate file names to give even spacing. Files with long names throw the entire display into chaos.

agree on the split view. and i think that somebody is working on the name thingy (when the filenames is too long use 3 dots , right?)

> **yatt said:**
> While I didn't read the whole thing (long changelogs are long), but tabbed browsing in Nautilus is the only thing that really stood out.

What I would like to see is a feature where if you hold a dragged item over a open folder, it opens that folder.


they made a patch for that in like 2003 but they can't use it because Apple has a patent on it.

---

### Post by geoken on 2008-08-27
> **mips said:**
> I've always used konqueror and wanderd what the noise was about with dolphin. Recently started using KDEmod4.1 and I must say I really like dolphin, I use it way more than konqueror these days. When I used Gnome I recall not liking nautilus as it felt like a severely lacking tool.

Your recollection would be completely accurate. I think they should take a hint when file managers like Thunar and PCManFM both claim to leave out features because speed is the most important factor to them, yet they still have relative feature parity with Nautilus.

---

### Post by mips on 2008-08-27
> **geoken said:**
> I think they should take a hint when file managers like Thunar and PCManFM both claim to leave out features because speed is the most important factor to them, yet they still have relative feature parity with Nautilus.

Think you hit the nail on the head there. 
When using openbox/lxde i usually install pcmanfm & emelfm2 and would say they 'feel' on par with nautilus from what i recall.

I'm not trying to knock gnome here but nautilus used to frustrate the hell out of me back when I still used gnome. I'm going to install ubuntu in a wm just to experience gnome again.

---

### Post by bruce89 on 2008-08-27
> **zekopeko said:**
> agree on the split view. and i think that somebody is working on the name thingy (when the filenames is too long use 3 dots , right?)

That's done as of 2.23.90:

```
Major changes in 2.23.90 are:
* Truncate long item labels in the icon view and on the desktop
   + icon_view/text_ellipsis_limit and desktop/text_ellipsis_limit GConf
     preferences added (defaults to three lines)
   + expand when hovering, or when selecting a file
[...]

```

---

### Post by mrgnash on 2008-08-27
The emphasis on integration is what keeps my feet firmly planted in the Gnome camp :) The migration of Epiphany to Webkit, and the inclusion of Empathy are probably the features I am most excited about though.

---

### Post by Sugz on 2008-08-27
I would love to see a feature similar to mac where you could put the toolbar inside the Panel.
Yes i know that there is already a applet that lets you do this to an extent, but i mean fully featured.

---

### Post by coolen on 2008-08-28
> **Sugz said:**
> I would love to see a feature similar to mac where you could put the toolbar inside the Panel.
Yes i know that there is already a applet that lets you do this to an extent, but i mean fully featured.

The Gnome devs, unfortunately, are against this feature. You can do it in KDE, but the Gnome guys don't want to imitate OSX.

---

### Post by beniwtv on 2008-08-28
> **gsmanners said:**
> "When Panel size changes"?

This is why I don't use Gnome anymore. Even the developers don't understand their own screw ups. It's a very well documented fact that the positioning of applets varies wildly even when the panel doesn't change in size.


This has been fixed in the Gnome version that is in Hardy. Applets no longer change positions at their will (at least it works here).

What is not fixed in Hardy is that when the size of the panel changes, the applets (again) move at their own will. This is what they're fixing now.

Cheers,

---

### Post by barbedsaber on 2008-08-28
empathy looks good, I tried to install it on my hardy/whatever the default hardy version of gnome is, but I couldn't find the backends for the IM protocols, so, I got an IM client without the IM feature.
Tabbed nautilus sounds good, I followed [this guide]("http://ubuntuforums.org/showthread.php?t=692238") to switch to pcmanfm, but it is not consistent (when I open my home folder with gnome-do, it uses nautilus, when I click the icon on the desktop for a removable drive, it opens in nautilus, etc) (yes, I know there is another guide on the page, I will follow it when I get around to it.)

---

