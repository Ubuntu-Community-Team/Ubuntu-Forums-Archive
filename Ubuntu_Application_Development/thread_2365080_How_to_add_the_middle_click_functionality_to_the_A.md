---
title: "How to add the middle click functionality to the Appindicator"
date: 2017-07-02
forum: Ubuntu Application Development
---

### Post by apollothethird on 2017-07-02
This is a very simple form of the Appindicator, take from [Python examples]("https://pythonexample.com/snippet/myappindicator_v5py_andreipetcu_python").

I have edited it to remove the initial compiler warnings such as imports and version notices.

I'm trying to add the middle click functionality which is provided in the library by the **set_secondary_activate_target()** method.

**The Code**

```
#!/usr/bin/python

import os
import signal
import subprocess
import gi
gi.require_version('Gtk', '3.0')
from gi.repository import Gtk as gtk
gi.require_version('AppIndicator3', '0.1')
from gi.repository import AppIndicator3 as appindicator

APPINDICATOR_ID = 'appreveallauncher'

def main():
    indicator = appindicator.Indicator.new(APPINDICATOR_ID,
                                            os.path.abspath('sample_icon.svg'),
                                            appindicator.IndicatorCategory.SYSTEM_SERVICES)
    indicator.set_status(appindicator.IndicatorStatus.ACTIVE)
    indicator.set_menu(build_menu())
    gtk.main()

def build_menu():
    menu = gtk.Menu()

    item_quit1 = gtk.MenuItem('Quit')
    item_quit1.connect('activate', quit)

    item_reveallauncher = gtk.MenuItem('Reveal Launcher')
    item_reveallauncher.connect('activate', reveallauncher)
    
    # This is my attempt to add the middle click functionality
    
    # menu_items = gtk.MenuItem("Reveal Launcher Middle Click")
    # menu.append(menu_items)
    # menu_items.connect("activate", menu_items)
    # menu_items.indicator.set_secondary_activate_target(menu_items)    

    menu.append(item_reveallauncher)
    menu.append(item_quit1)
    menu.show_all()
    return menu

def menu_items(_):
    subprocess.call("xdotool key alt+F1", shell=True) 

def reveallauncher(_):
    subprocess.call("xdotool key alt+F1", shell=True) 

def quit1(_):
    gtk.main_quit()

if __name__ == "__main__":
    signal.signal(signal.SIGINT, signal.SIG_DFL)
    main()

#   last = self.get_last_menuitem(self.app_menu) 
#   self.app.set_secondary_activate_target(last)
```

**Middle click feature block**
My attempt to add the middle click feature is commented out.  These are the lines:

```
menu_items = gtk.MenuItem("Reveal Launcher Middle Click")
menu.append(menu_items)
menu_items.connect("activate", menu_items)
menu_items.indicator.set_secondary_activate_target(menu_items)
```

**Runtime Errors**
When uncommenting the block, there are no compiler errors.  The runtime errors are:

```
Traceback (most recent call last):
  File "/home/users/l/j/ljames/workspace/pythontest/src/basic.py", line 58, in <module>
    main()
  File "/home/users/l/j/ljames/workspace/pythontest/src/basic.py", line 20, in main
    indicator.set_menu(build_menu())
  File "/home/users/l/j/ljames/workspace/pythontest/src/basic.py", line 36, in build_menu
    menu_items.connect("activate", menu_items)
TypeError: second argument must be callable
```

Thanks in advance for any input on this.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/~ljames")

---

