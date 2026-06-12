---
title: "USP2 - new core and plugins"
date: 2007-11-04
forum: Ubuntu System Panel
---

### Post by Quikee on 2007-11-04
[SIZE="6"]This is a thread about USP2 - a core rewrite of the original USP[/SIZE]

Core and all plugins are designed to be without any fixed size - everything is scalable and as simple as possible (so no visual screws can occur). 
It is build to extensively use drag and drop (+easy keyboard access in the future).

Configuration of plugins and the core application is done directly in USP2 itself and without need to restarts USP2 if this is possible.

Changelog:
[LIST]

[*]usp2_1.0.0-preview5 (latest)
[LIST]
[*]Utils: Bug in thumbnailing fixed. 
[/LIST]

[*]usp2_1.0.0-preview4
[LIST]
[*]Core: Added keybind ctrl-F12 to show/hide the applet (needs deskbar applet because it uses its keybinding library) 
[*]Application and Favorites: gconf option to hide the applet if a program is launched
[*]Recent: fixed problems with executing .desktop files
[/LIST]

[*]usp2_1.0.0-preview3
[LIST]
[*]Core: various fixes
[*]Core: plugin boxes can now be moved around by drag and dropping
[*]Added utils for common utils used by the core and plugins
[*]UspRecent: parse .desktop files and use its data instead of default
[*]UspRecent: many bugfixes
[*]Applications plugin: clicked applications are added to recent list
[*]Applications plugin: introduced movable separator between categories and applications
[*]Applications plugin: applications use smaller icons and show only the name (will be an option)
[*]System info plugin: values are displayed in non-editable entry boxes
[*]Various fixes to other plugins
[/LIST]

[*]usp2_1.0.0-preview2
[LIST]
[*]fixed recent plugin not loading properly because of "nonlocal" URLs
[/LIST]

[*]usp2_1.0.0-preview1
[LIST]
[*]initial release
[/LIST]
[/LIST]

Subversion repository: [http://ubuntu-system-panel.googlecode.com/svn/trunk/usp2](http://ubuntu-system-panel.googlecode.com/svn/trunk/usp2)

Screen cast: [here]("http://freeweb.siol.net/tvajng/usp2.ogg")

---

### Post by Quikee on 2007-11-04
Screencast of USP2's basic features can be found here (deleted)

---

### Post by zekopeko on 2007-11-04
may i suggest launchpad.net for this project?

EDIT: just tried it and it looks great.

few suggestions:

1. can you make the menu attached to the button?
2. how to change font size and make the menu borders non-rounded

---

### Post by Quikee on 2007-11-05
> **zekopeko said:**
> may i suggest launchpad.net for this project?

I will think about it when it is more stable. 

> **zekopeko said:**
> 
1. can you make the menu attached to the button?

Isn't the menu attached to the button for you - Like in attached video (it's zipped because I couldn't attach it otherwise)?

> **zekopeko said:**
> 
2. how to change font size and make the menu borders non-rounded

I will add both as an option.


I'm glad you like it. ;)

---

### Post by delfick on 2007-11-05
I suggest contacting chanders and seeing if you can help him work on usp3........

EDIT : Just watched the screencast....wow :D
that looks really nice.

EDIT 2 : just tried installing the deb on ubuntu gutsy...... it made my gnome-panel freeze....

---

### Post by Quikee on 2007-11-05
> **delfick said:**
> I suggest contacting chanders and seeing if you can help him work on usp3........

I will do this eventually as duplicating effort is not good.. but currently I want to explore my own ideas for the panel.

> **delfick said:**
> 
EDIT : Just watched the screencast....wow
that looks really nice.

It's even nicer with compiz as it supports transparency / opacity (needs to be enabled in gconf), but my main focus currently is not eyecandy. I have done this only because it was easy. 

> **delfick said:**
> 
EDIT 2 : just tried installing the deb on ubuntu gutsy...... it made my gnome-panel freeze....


Try to run it in terminal with "usp2 run-in-window" and tell me if it works. There is no problem here in Gutsy but maybe you are missing a dependency as I haven't put all needed dependencies into the package.

---

### Post by zekopeko on 2007-11-05
> **Quikee said:**
> 
Isn't the menu attached to the button for you - Like in attached video (it's zipped because I couldn't attach it otherwise)?


It looks just like in the video but the rounded corners and the gap between the USP2 button in the panel and the window make it look like 
window and not a menu(i know that it's a window programming wise).

On a side note the screenshot with opacity/blur looks amazing. Will it be possible in the future to do bluring "vista style" like in this screenshot (look at the window background):

[IMG]http://beans.seartipy.com/wp-content/uploads/2006/06/vista/GadgetsAdded2.PNG.jpg[/IMG]

---

### Post by Quikee on 2007-11-05
> **zekopeko said:**
> It looks just like in the video but the rounded corners and the gap between the USP2 button in the panel and the window make it look like 
window and not a menu(i know that it's a window programming wise).

I see... the gap should go away if round corners are removed I only need to make this an option. 

> **zekopeko said:**
> 
On a side note the screenshot with opacity/blur looks amazing. Will it be possible in the future to do bluring "vista style" like in this screenshot (look at the window background):


I hope it will be possible. :)

---

### Post by delfick on 2007-11-06
```
iambob@bob:~$ usp2 run-in-window
Compositing:  False
Opacity:  -1
Loaded:  /usr/share/usp2/plugins/favourites.py
Loaded:  /usr/share/usp2/plugins/uspSystemManagement.py
Loaded:  /usr/share/usp2/plugins/applications.py
Loaded:  /usr/share/usp2/plugins/uspSysInfo.py
Loaded:  /usr/share/usp2/plugins/uspSearch.py
Loaded:  /usr/share/usp2/plugins/uspUser.py
Traceback (most recent call last):
  File "/usr/bin/usp2", line 346, in <module>
    factory(applet, None)
  File "/usr/bin/usp2", line 335, in factory
    button = AppletButton(applet)
  File "/usr/bin/usp2", line 251, in __init__
    self.mainWindow = MainWindow()
  File "/usr/bin/usp2", line 114, in __init__
    self.reload()
  File "/usr/bin/usp2", line 158, in reload
    self.pluginsByName = self.initPlugins()
  File "/usr/bin/usp2", line 171, in initPlugins
    pluginInstance = plugin.UspPlugin()
  File "/usr/share/usp2/plugins/uspRecent.py", line 82, in __init__
    self.userView = RecentView(self.widgetTree, self.window, self.content_holder)
  File "/usr/share/usp2/plugins/uspRecent.py", line 29, in __init__
    self.fillRecentBox(manager)
  File "/usr/share/usp2/plugins/uspRecent.py", line 43, in fillRecentBox
    path = gnomevfs.get_local_path_from_uri(uri)
RuntimeError: unknown error

```

.....

(as for blur, the blur plugin should already do that..... doesn't it ??)

---

### Post by sweetthdevil on 2007-11-06
Looks fantastic and is fantastic!

Could you please think of a shortcut management like usp, to open the menu on a shortcut. 

Many thanks!

---

### Post by Quikee on 2007-11-06
I have attached a new version which should fix delfick error (which is very strange BTW - looks like there is an invalid entry in recent which causes a crash) and it fixes remembering of defined plugin sizes in right click on plugin name. 

> **delfick said:**
> 
(as for blur, the blur plugin should already do that..... doesn't it ??)

It does as you can see in my screenshot but I think he meant that the widgets should look as transparent as they do in vista. Maybe I misunderstood. To have it almost completely transparent and blured should not be a problem - see the new screenshot.


> 
Could you please think of a shortcut management like usp, to open the menu on a shortcut. 

You mean like super + F1 - yes I have this planned. ;)

---

### Post by sweetthdevil on 2007-11-06
Great many thanks, i just update it and it work great! however; when i start an apps from your menu, the apps open in the back ground but usp2 doesn't disappear as it should. 

Looking forward for the next version!!

---

### Post by delfick on 2007-11-06
cool :D

now it works :D

thnx


though it doesn't see that I'm running compiz/compiz-fusion......
(the attached screenshot shows me using wobbly on the menu)


(also, how possible is it to get the original (and your new version) usp as an applet on the awn ([https://launchpad.net/awn](https://launchpad.net/awn)))

:D

---

### Post by Quikee on 2007-11-07
> **sweetthdevil said:**
> Great many thanks, i just update it and it work great! however; when i start an apps from your menu, the apps open in the back ground but usp2 doesn't disappear as it should. 

Looking forward for the next version!!

Yes I am aware of this. The thing is that I'm unsure what kind of core -> plugin communication should I use and have not implemented this. But it is always good to remind me what I still need to do. ;)

> **delfick said:**
> 
though it doesn't see that I'm running compiz/compiz-fusion......
(the attached screenshot shows me using wobbly on the menu)


This is because by default the transparency/opacity is disabled. You have to set it in gconf (/apps/usp2) to your desired value. I am working on core configuration, where you will be able to set this from the USP2 itself (possibly by a slider). Another issue is also that USP2 must start after compiz as otherwise it doesn't detect it is running and will disable transparency/opacity.

> **delfick said:**
> 
(also, how possible is it to get the original (and your new version) usp as an applet on the awn ([https://launchpad.net/awn](https://launchpad.net/awn)))


This should not be too hard to do. I looked at the example code for a applet and will try to make one when I have time. Hmm... I think I slowly need a TODO list. ;)

---

### Post by delfick on 2007-11-07
> **Quikee said:**
> This is because by default the transparency/opacity is disabled. You have to set it in gconf (/apps/usp2) to your desired value. I am working on core configuration, where you will be able to set this from the USP2 itself (possibly by a slider). Another issue is also that USP2 must start after compiz as otherwise it doesn't detect it is running and will disable transparency/opacity.

ahh, ok then..
will test that later when I'm finished with windows
(need it to write notes for my calculator for my exam :()

> This should not be too hard to do. I looked at the example code for a applet and will try to make one when I have time. Hmm... I think I slowly need a TODO list. ;)

wicked :D
(especially if you get the original one working as well :D)
(if that isn't too much more effort than getting yours to work, of course :))

---

### Post by superdeivid on 2007-11-07
this is great, best than usp 1


can you agree, an preferences like de usp 1?

---

### Post by shafin on 2007-12-01
it feels great,thank you.

---

### Post by cmost on 2007-12-03
The screenshots of this look fantastic.  I wouldn't know from personal experience though.  Does this not work on Feisty?  I installed the deb for preview 2 but when I tried to add it to the panel, I got this error:

The panel encountered a problem while loading "OAFIID:Ubuntu_System_panel..."
Delete / Don't Delete

My panel completely locks up / crashes.  I removed the deb.  Is there a source tree I can compile my own deb from?  If so, how would I get it?  Thanks.

---

### Post by cmost on 2007-12-05
Knock, knock, knock...

"Hello!"  Anybody home????

:confused:

---

### Post by delfick on 2007-12-05
> **cmost said:**
> Knock, knock, knock...

"Hello!"  Anybody home????

:confused:

I am :D

not that, that will help you :p

---

### Post by Quikee on 2007-12-11
Sorry - I was away the last week.

There is no "source tree" as USP2 is written in python - which means the actual program/executable is the source. 

When I was testing the first, I also tested it on Feisty but this could change in the later versions. 

To pinpoint what is wrong you should start usp2 in terminal with "usp2 run-in-window". If something is wrong it should show you that an error occurred. If everything is OK - something else is wrong.

---

### Post by direk_ on 2007-12-13
I've got problems too. On Gusty, when i'm trying to run it under console:

```

[12:12:51] direk@direk-lap:~$ usp2 run-in-window
Compositing:  False
Opacity:  -1
/usr/share/usp2/iconFactory.py:38: GtkWarning: Theme directory 48x48/status of theme black-white has no size field

  info = self.iconTheme.lookup_icon(iconNameModified, iconSize, gtk.ICON_LOOKUP_FORCE_SVG | gtk.ICON_LOOKUP_USE_BUILTIN)
/usr/share/usp2/iconFactory.py:38: GtkWarning: Theme directory 64x64/status of theme black-white has no size field

  info = self.iconTheme.lookup_icon(iconNameModified, iconSize, gtk.ICON_LOOKUP_FORCE_SVG | gtk.ICON_LOOKUP_USE_BUILTIN)
Loaded:  /usr/share/usp2/plugins/applications.py
Loaded:  /usr/share/usp2/plugins/uspSysInfo.py
Loaded:  /usr/share/usp2/plugins/uspSystemManagement.py
Loaded:  /usr/share/usp2/plugins/favourites.py
Loaded:  /usr/share/usp2/plugins/uspUser.py
Traceback (most recent call last):
  File "/usr/bin/usp2", line 346, in <module>
    factory(applet, None)
  File "/usr/bin/usp2", line 335, in factory
    button = AppletButton(applet)
  File "/usr/bin/usp2", line 251, in __init__
    self.mainWindow = MainWindow()
  File "/usr/bin/usp2", line 114, in __init__
    self.reload()
  File "/usr/bin/usp2", line 158, in reload
    self.pluginsByName = self.initPlugins()
  File "/usr/bin/usp2", line 171, in initPlugins
    pluginInstance = plugin.UspPlugin()
  File "/usr/share/usp2/plugins/uspRecent.py", line 82, in __init__
    self.userView = RecentView(self.widgetTree, self.window, self.content_holder)
  File "/usr/share/usp2/plugins/uspRecent.py", line 29, in __init__
    self.fillRecentBox(manager)
  File "/usr/share/usp2/plugins/uspRecent.py", line 43, in fillRecentBox
    path = gnomevfs.get_local_path_from_uri(uri)
RuntimeError: unknown error

```

---

### Post by sweetthdevil on 2007-12-13
What's the status of dev? i wouldn't to see this project left alone like his big brother....

Have you though of the shortcut management?

many thanks for the work!

---

### Post by Quikee on 2007-12-17
Yes I know.. my response time sux. ;)
 
> **direk_ said:**
> I've got problems too. On Gusty, when i'm trying to run it under console:

Do you have usp2-preview1(on the first page) or usp2-preview2(somewhere on the second page if I am not mistaken). I thought I fixed this in usp2-preview2.

> **sweetthdevil said:**
> What's the status of dev? i wouldn't to see this project left alone like his big brother....

Have you though of the shortcut management?

many thanks for the work!

Development is currently slow as I am also working on another project. However I will try to bring usp2 to a next stage and fix/implement all the reported bugs and wishes during Christmas/new year "holiday".

---

### Post by direk_ on 2007-12-17
You're right, "preview-2" is working fine ;-)

I think that there is a good idea to put changelog and all versions on first page of this topic.

---

### Post by sweetthdevil on 2007-12-17
great news, looking forward for the next release!

---

### Post by Quikee on 2007-12-17
> **direk_ said:**
> You're right, "preview-2" is working fine ;-)

I think that there is a good idea to put changelog and all versions on first page of this topic.

Yes.. sorry - I forgot that I can edit my posts - all forums where I attached files did not allow this.

---

### Post by sweetthdevil on 2008-01-20
Hope every one had a good time over the holidays!

taking the liberty of asking for an update on your project? 

many thanks again for your work and time.

---

### Post by Quikee on 2008-01-21
> **sweetthdevil said:**
> Hope every one had a good time over the holidays!

taking the liberty of asking for an update on your project? 

many thanks again for your work and time.

I am working more on USP2 lately. Generally I am not satisfied how "applications" and "favorites" plugins are coded so I plan to rewrite them. I also need to create some sort of "places" plugin and beautify "system settings". 

Once the code stabilizes I will release the first "beta" version, which I hope it will be soon.

---

### Post by sweetthdevil on 2008-01-21
Great news, looking forward for it!

---

### Post by hyperair on 2008-02-16
I'm having a bit of a problem with USP-2.. It seems to be thumbnailing all my videos! And since I've got quite a lot, including many movies.. it takes ages to load. But when it does, it's good.

---

### Post by Quikee on 2008-02-17
> **hyperair said:**
> I'm having a bit of a problem with USP-2.. It seems to be thumbnailing all my videos! And since I've got quite a lot, including many movies.. it takes ages to load. But when it does, it's good.

Yes.. this is a bug. 

On startup all recent files are read and thumbnailed. The correct behavior would be to read only the last 10 recent files and don't thumbnail them if they a thumbnail is not available. Maybe a variation of this would be better - to still allow thumbnailing but limit the recent files shown only. I will look into this.

---

### Post by tommohawk on 2008-02-25
Nice app.  I have been looking for a good menu to replace the standard GNOME one.  I have tried many including th mint menu, the original USP and others.  This one is really good and it works in Hardy.

Keep up the good work.:)

---

### Post by Quikee on 2008-03-10
Far too long there has not been any updates on USP2. 

I have been doing some work lately and want to present the progress. USP2 preview3 (deb to download and changelog is on the first page) is hopefully the last "preview" version of USP2 as I am now happy how the program behaves - next are the alpha or beta version. 

I hope I will be able to make releases on regular bases from now on (at least once a month) and I will also commit the source to USP SVN repository (will be done ASAP) so others can participate in development if anybody has the interest to do it.

Any comments are welcomed.

---

### Post by sweetthdevil on 2008-03-10
Great!!!

Many thanks for your hard work. 

Just install it, if I may say few details, in order to release a greater usp.

- When I click on a icon for a software the menu is left open, it should close or at least to leave the option
- It really need a shortcut to open like ctrl+u
- I can't open the preference to set it up, don;t know the problem. 

Again many thanks

---

### Post by hyperair on 2008-03-10
Same here. I can't open the preferences. =(

---

### Post by Quikee on 2008-03-10
The preferences are not implemented yet (this is mainly the reason why this is still a preview release). However all the options that are available can be accessed through gconf-editor (only 2 options for the core currently).

For hotkey shortcut I will have to see how can I provide it cleanly.

I will address autohide on application start tomorrow.

Also I forgot to mention - USP2 preview3 has been developed and tested only with Hardy.

---

### Post by delfick on 2008-03-10
> **Quikee said:**
> 

Changelog:
[LIST]

[*]usp2_1.0.0-preview3 (latest)
[list]
[*]Core: plugin boxes can now be moved around by drag and dropping[/list]

cool :)

---

### Post by Quikee on 2008-03-12
Hello!

On the first page there is available USP2 preview4 which addresses the issues / wishes reported by sweetthdevil. 

The library for binding a key to perform an action is used from deskbar applet which means that USP2 is temporary dependent on it.

Have fun. ;)

---

### Post by sweetthdevil on 2008-03-12
Great! I am so happy to see this project evolving so fast again!


I am only trying to improve it y giving some comments...

It would be great to be able to search lets say firefox and then press enter for the software to start (like USp does) 

I guess we will be able to set up the size and shape of all plugins when preferences will be done? 

a place/location plugin is in need, for usp2 to be used on a daily basic 

The search plugin doesn't seem to work? 

Many thanks for your hard work,

---

### Post by sayakb on 2008-03-22
The preferences don't seem to work for me..

---

### Post by sayakb on 2008-03-22
Plus, the menu is too big to fit.. can I remove the recent and search on the right panel?

---

### Post by Quikee on 2008-03-22
As already said preferences are not implemented yet. Sorry.

Included plugins are currently hardcoded. If you want to remove a plugin you have to modify '/usr/bin/usp2'. Search for 'Recent' and  modify: 

```
plugins = [['User', 'System info', 'System management'],
			['Applications','Favourites'],
			['Recent', 'Search']]
```

to:

```
plugins = [['User', 'System info', 'System management'],
			['Applications','Favourites']]

```


Once the preferences are ready you will be able to do this there. ;)

---

### Post by smartboyathome on 2008-03-26
For some reason this doesn't work on hardy, it shows up as a little white dot and nothing.

Edit: Ran usp2 run-in-window, and got this:
```
Traceback (most recent call last):
  File "/usr/bin/usp2", line 486, in <module>
    MainApplet.factory(applet, None)
  File "/usr/bin/usp2", line 445, in factory
    MainApplet(applet)
  File "/usr/bin/usp2", line 449, in __init__
    appletWidget = AppletWidget(applet)
  File "/usr/bin/usp2", line 376, in __init__
    self.mainWindow = MainWindow()
  File "/usr/bin/usp2", line 255, in __init__
    self.reload()
  File "/usr/bin/usp2", line 292, in reload
    self.pluginsByName = self.initPlugins()
  File "/usr/bin/usp2", line 308, in initPlugins
    pluginInstance = plugin.UspPlugin()
  File "/usr/share/usp2/plugins/uspRecent.py", line 112, in __init__
    self.userView = RecentView(recentBox, clearButton)
  File "/usr/share/usp2/plugins/uspRecent.py", line 33, in __init__
    self.refresh()
  File "/usr/share/usp2/plugins/uspRecent.py", line 77, in refresh
    button = self.buttonFactory.create([name], self.iconFactory.iconForURI(uri, 24, True, True), tooltipText)
  File "/usr/share/usp2/utils/IconFactory.py", line 43, in iconForURI
    pix = self.getThumbnailForURI(uri, iconSize, mime, shouldThumbnail)
  File "/usr/share/usp2/utils/IconFactory.py", line 25, in getThumbnailForURI
    return pix.scale_simple(iconSize, iconSize, gtk.gdk.INTERP_HYPER)
AttributeError: 'str' object has no attribute 'scale_simple'
```

---

### Post by Quikee on 2008-03-27
> **smartboyathome said:**
> For some reason this doesn't work on hardy, it shows up as a little white dot and nothing.

Edit: Ran usp2 run-in-window, and got this:
```
Traceback (most recent call last):
  File "/usr/bin/usp2", line 486, in <module>
    MainApplet.factory(applet, None)
  File "/usr/bin/usp2", line 445, in factory
    MainApplet(applet)
  File "/usr/bin/usp2", line 449, in __init__
    appletWidget = AppletWidget(applet)
  File "/usr/bin/usp2", line 376, in __init__
    self.mainWindow = MainWindow()
  File "/usr/bin/usp2", line 255, in __init__
    self.reload()
  File "/usr/bin/usp2", line 292, in reload
    self.pluginsByName = self.initPlugins()
  File "/usr/bin/usp2", line 308, in initPlugins
    pluginInstance = plugin.UspPlugin()
  File "/usr/share/usp2/plugins/uspRecent.py", line 112, in __init__
    self.userView = RecentView(recentBox, clearButton)
  File "/usr/share/usp2/plugins/uspRecent.py", line 33, in __init__
    self.refresh()
  File "/usr/share/usp2/plugins/uspRecent.py", line 77, in refresh
    button = self.buttonFactory.create([name], self.iconFactory.iconForURI(uri, 24, True, True), tooltipText)
  File "/usr/share/usp2/utils/IconFactory.py", line 43, in iconForURI
    pix = self.getThumbnailForURI(uri, iconSize, mime, shouldThumbnail)
  File "/usr/share/usp2/utils/IconFactory.py", line 25, in getThumbnailForURI
    return pix.scale_simple(iconSize, iconSize, gtk.gdk.INTERP_HYPER)
AttributeError: 'str' object has no attribute 'scale_simple'
```

Found what is wrong - thumbnailing is still not done right. 
[Preview5]("http://ubuntuforums.org/attachment.php?attachmentid=63985&stc=1&d=1206597905") should fix this.

---

### Post by EnigMattic on 2008-07-11
Any news?

---

### Post by Malac on 2008-07-23
> **EnigMattic said:**
> Any news?
 [http://ubuntuforums.org/showpost.php?p=5384781&postcount=63](http://ubuntuforums.org/showpost.php?p=5384781&postcount=63)

---

