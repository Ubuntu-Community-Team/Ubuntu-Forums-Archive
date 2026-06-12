---
title: "USP not working anymore (frozen)"
date: 2008-06-28
forum: Ubuntu System Panel
---

### Post by Skyy on 2008-06-28
Hi guys,
I had USP running smoothly by following the instructions here:
[http://code.google.com/p/ubuntu-system-panel/wiki/Installation](http://code.google.com/p/ubuntu-system-panel/wiki/Installation)

However now it won't work anymore, I noticed the WINE Menu was empty even though it should not, so I removed USP from my GNOME Bar and readded it to see if it would fix the empty menu.

Well afrer I readded USP it was only a 1x1 black pixel, however if I move my GNOME Bar around, from top to bottom the USP pixel would turn into "System" again but USP wont react on clicks nor can I access the config through the right-click menu, the only options I have are:

Remove
Move
Lock

uspconfig in terminal still works but wont help me to fix the problem.

I uninstalled USP through "./usp_update uninstall complete" and even purge removed it afterwards, deleted the .usp folder from my Home folder and then tried to redo all from scratch, still the same.

That's the output of usp run-in-window:

```
*********** Keybind Failure **************
Using Standard Menu
No User Picture Specified or File Not Found
uspuser: loaded successfully
system_management: loaded successfully
applications: loaded successfully
recent: loaded successfully
Traceback (most recent call last):
  File "/usr/bin/usp", line 1093, in <module>
    menu_factory(app, None)
  File "/usr/bin/usp", line 1078, in menu_factory
    MenuWin(applet, iid)
  File "/usr/bin/usp", line 784, in __init__
    self.mainwin = MainWindow()
  File "/usr/bin/usp", line 70, in __init__
    self.PopulatePlugins()
  File "/usr/bin/usp", line 478, in PopulatePlugins
    self.plugins[plugin].do_plugin()
  File "/usr/lib/python2.4/site-packages/usp/plugins/applications.py", line 791, in do_plugin
    self.Todos()
  File "/usr/lib/python2.4/site-packages/usp/plugins/applications.py", line 423, in Todos
    self.BuildLowerFiles(child)
  File "/usr/lib/python2.4/site-packages/usp/plugins/applications.py", line 517, in BuildLowerFiles
    openfile = open( GetFilePath( path ), 'r' )
  File "/usr/lib/python2.4/site-packages/usp/plugins/easyfiles.py", line 72, in GetFilePath
    path = urllib.url2pathname(uri) # escape special chars
  File "/usr/lib/python2.5/urllib.py", line 55, in url2pathname
    return unquote(pathname)
  File "/usr/lib/python2.5/urllib.py", line 1153, in unquote
    res = s.split('%')
AttributeError: 'NoneType' object has no attribute 'split'
```

I hope someone can help me to get USP back running, it's great!

Btw. I'm a total Linux newb and running Ubuntu 8.04 Hardy Heron 64bit

Thanks for any help in advance!

---

### Post by Malac on 2008-07-01
Sorry for the delay in getting back to you.
```
File "/usr/lib/python2.4/site-packages/usp/plugins/easyfiles.py", line 72, in GetFilePath
    path = urllib.url2pathname(uri) # escape special chars
```This is where USP modules stop, as it were.
After that it looks like it is a problem within the urllib.py file.
```
 File "/usr/lib/python2.5/urllib.py", line 55, in url2pathname
    return unquote(pathname)
  File "/usr/lib/python2.5/urllib.py", line 1153, in unquote
    res = s.split('%')
AttributeError: 'NoneType' object has no attribute 'split'
```This is not one written for USP. Looks like you are using python2.5 at this stage, they must have changed something from python2.4. Can you try installing python2.4 urllib module and see if that sorts it.
I will check what the differences are between the two versions tomorrow if I can and report a bug if it is such. Will get back to you asap.

Hope this helps.

---

### Post by Malac on 2008-07-03
Looks like they took out some error checking so I'll have to do my own.
Will do this tonight and update SVN by tomorrow.

---

