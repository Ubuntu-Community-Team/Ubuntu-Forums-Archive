---
title: "Tweaking?"
date: 2009-07-23
forum: The Cafe
---

### Post by kickwin on 2009-07-23
I started using Ubuntu two months earlier and I pretty much can do all I did while I was on Windows. I often see in many forum posts that one main advantage of Linux is that you can tweak or customize your system to fit your needs. Other than changing look and appearance/adding new apps, I have not made any big changes to my installation. Also I do not seem to understand what a normal user like me can do in the name of customization to better my computer using experience. In other words, what are the tweaks you have made to your Ubuntu. Thanks.

---

### Post by bryonak on 2009-07-23
The panel:
Right click any panel object, select "move" and drag it where you want.
Right click on empty panel space and select "Properties" to customise various aspects.
Right click on empty panel space, select "Add to Panel" and choose some objects. More are installable via Synaptic.
Right click on empty panel space and delete the panel, or add a new one.
You can have two panels, one panel, some side panels, two next to each other where ones is autohiding and the other isn't, or any other combination of 0-xxx panels ;)

Compiz:
Install ccsm with ```
sudo aptitude install compizconfig-settings-manager
```
Start it up with either System -> Preferences -> CompizConfig Settings Manager, or by pressing Alt+F2 and typing "ccsm".
Spend an hour there ;)

Docks:
Install one of the various docks... My favourite is cairo-dock, though there are many others like AWN or Gnome-Do.
If you want to try cairo-dock, preferably use the new version [2.0]("http://webupd8.blogspot.com/2009/05/cairo-dock-200-is-here-linux-dock-menu.html") (the repositories only offer 1.x). It is *very* customisable.

Themes:
There is an alternate theme manager called Emerald, which offers "advanced" (for the lack of a better description) themes.
```
sudo aptitude install emerald
```
Visit [http://gnome-look.org](http://gnome-look.org) for themes (themes in the categories "Compiz" and "Beryl" are meant for Emerald).

Workflow:
Streamline your workflow.
One option is using Compiz additions like Expose, Scale, ... and keyboard/mouse/screen shortcuts in the Commands section.
If you want to get a bit more "techy", look up xbindkeys, which will let you optimise your whole input exactly to your needs.


I'm done for now, but bear in mind that this was just the obvious/easy stuff ;)
You can fine tune lot's of things in separate applications, with additional tools or in the /sys virtual file system. But the above should get you started ;)

---

### Post by SunnyRabbiera on 2009-07-23
I have added values to my xorg.conf file to get a brighter screen.

---

