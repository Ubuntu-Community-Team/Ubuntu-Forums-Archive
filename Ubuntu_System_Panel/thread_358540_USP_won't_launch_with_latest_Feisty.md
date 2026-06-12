---
title: "USP won't launch with latest Feisty"
date: 2007-02-10
forum: Ubuntu System Panel
---

### Post by PWill on 2007-02-10
When I try to run USP with the latest Feisty upgrades, it gives me this error:```
paul@bel-air:~$ usp run-in-window
Using Standard Menu
Loading plugin 'uspuser' : successful
Loading plugin 'system_management' : successful
Loading plugin 'applications' : successful
Loading plugin 'recent' : successful
Traceback (most recent call last):
  File "/usr/bin/usp", line 771, in ?
    menu_factory(app, None)
  File "/usr/bin/usp", line 761, in menu_factory
    MenuWin(applet, iid)
  File "/usr/bin/usp", line 550, in __init__
    self.mainwin = MainWindow()
  File "/usr/bin/usp", line 58, in __init__
    self.PopulatePlugins()
  File "/usr/bin/usp", line 345, in PopulatePlugins
    self.plugins[plugin].do_plugin()
  File "/usr/lib/python2.4/site-packages/usp/plugins/applications.py", line 605, in do_plugin
    self.Todos()
  File "/usr/lib/python2.4/site-packages/usp/plugins/applications.py", line 335, in Todos
    openfile = open( GetFilePath( path ), 'r' )
UnboundLocalError: local variable 'path' referenced before assignment

```
When I comment out line 605 in applications.py, it loads, but clicking All Applications does noting, and the search function does not work.

---

### Post by chanders on 2007-02-11
Ok, I am at a windows machine right now but if you change the according lines like so, you should be fine.

applications.py

                 >        if grandchild.get_type() == gmenu.TYPE_ENTRY:[INDENT]path = grandchild.get_desktop_file_path() [/INDENT][INDENT]openfile = open( GetFilePath( path ), 'r' )
[/INDENT][INDENT]datalist = openfile.readlines()
[/INDENT][INDENT]                         for i in range( len( datalist ) ):
[/INDENT][INDENT][INDENT]                             datalist[i] = datalist[i].strip( '\r\n\x00' )

                            if datalist[i][0:5] == "Name=":[INDENT]                                 PlaceName = datalist[i][5:]
[/INDENT][INDENT]                                 BTip = datalist[i][5:]
[/INDENT]if datalist[i][0:8] == "Comment=":[INDENT]                                 PlaceComment = datalist[i][8:]
[/INDENT]if datalist[i][0:5] == "Exec=":[INDENT]                                 execstring = datalist[i][5:].replace( "%u", "" )[/INDENT][INDENT]                                 execstring = execstring.replace( "%U", "" )
                                execstring = execstring.replace( "%F", "" )
                                PlaceExec = execstring
[/INDENT]if datalist[i][0:5] == "Icon=":[INDENT]                                 PlaceIconName = datalist[i][5:]
                                iconfound = True
[/INDENT]if datalist[i][0:12] == "GenericName=":[INDENT]                                 GenericName = datalist[i][12:][/INDENT][/INDENT][/INDENT]

---

### Post by PWill on 2007-02-11
> **chanders said:**
> Ok, I am at a windows machine right now but if you change the according lines like so, you should be fine.

applications.py

Getting closer!
I made those changes, and got this error: ```
Traceback (most recent call last):
  File "/usr/bin/usp", line 616, in <module>
    menu_factory(app, None)
  File "/usr/bin/usp", line 606, in menu_factory
    MenuWin(applet, iid)
  File "/usr/bin/usp", line 398, in __init__
    self.mainwin = MainWindow()
  File "/usr/bin/usp", line 53, in __init__
    self.PopulatePlugins()
  File "/usr/bin/usp", line 254, in PopulatePlugins
    self.plugins[plugin].do_plugin()
  File "/usr/lib/python2.4/site-packages/usp/plugins/applications.py", line 643, in do_plugin
    self.Todos()
  File "/usr/lib/python2.4/site-packages/usp/plugins/applications.py", line 410, in Todos
    ItemButton.MyButtonName = path
UnboundLocalError: local variable 'path' referenced before assignment

```
So I commented out line 410, which read "ItemButton.MyButtonName = path"
It then launches fine, with the Applications plugin, and I can browse all of my applications. However, when I right click on an program and choose Add to Favorites, it obviously can't find the MyButtonName line, and it gives me this: ```
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/usp/plugins/applications.py", line 624, in AddFavourite
    self.AddToFavourites( button.MyButtonName )
AttributeError: 'gtk.Button' object has no attribute 'MyButtonName'

```

---

### Post by PWill on 2007-02-12
Am I the only one having this problem?

---

### Post by PWill on 2007-02-12
Hooray! Latest Feisty Python updates fixed it. Not sure what happened, but it works now.

---

