---
title: "[Elementary OS] Problems installing network printer attached to DSL moded"
date: 2015-10-27
forum: Ubuntu/Debian BASED
---

### Post by ais2020 on 2015-10-27
Hello,
I just moved to linux 2 weeks ago. I have just installed eOS Freya and I love it.


  I want to set up my network printer (HP LaserJet P2015) using CUPS  web interface. I tried all protocols but none of them gets the result. I  see printer installed but it fails to print a test page. Printer was  working fine when it was connected directly to usb port in my pc.
It is now connected to my dsl modem which supports print server and  working fine with my windows xp.

Printer Address is: 192.168.1.1:631/printers/hp1

  It is recognised by CUPS and I can see it when I click on PRINTERS in System Settings but it is not printing at all

I tried to run```
 sudo system-config-printer
``` and I got this:

  > ** (system-config-printer.py:4062): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-nUAgjecdir: Connection refused

/usr/share/system-config-printer/system-config-printer.py:2067: Warning: Source ID 126 was not found when attempting to remove it

GLib.source_remove (self.populateList_timer)
Unknown value for media-col: (unknown IPP value tag 0x34)
Choices: [u'media-bottom-margin', u'media-left-margin', u'media-right-margin', u'media-size', u'media-source', u'media-top-margin', u'media-type']
Selecting from choices: media-bottom-margin

/usr/share/system-config-printer/monitor.py:757: Warning: Source ID 225 was not found when attempting to remove it

GLib.source_remove (self.update_timer)
/usr/share/system-config-printer/monitor.py:190: Warning: Source ID 1381 was not found when attempting to remove it

GLib.source_remove (timer)
ais@ais-EOS:~$  
  
 I tried ```
hp-setup
``` and I got this 

  > hp-setup

  HP Linux Imaging and Printing System (ver. 3.14.3)
Printer/Fax Setup Utility ver. 9.0

Copyright (c) 2001-13 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Gtk-Message: Failed to load module "pantheon-filechooser-module"
Gtk-Message: Failed to load module "canberra-gtk-module"

(python:5459): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed

(python:5459): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed

Done.

I  googled and read many post trying to find a solution and I got lost and stopped trying to apply some of suggested solution because I did not to worsen my problem.  
Any help will be highly appreciated.

---

