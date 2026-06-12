---
title: "GTK3 Overlay Image fails to display in Numix while fine in Ambience"
date: 2014-06-19
forum: Ubuntu Application Development
---

### Post by michael171 on 2014-06-19
I am developing a python 3.4 gui application that runs on gtk3 pygobject 3.12.0 and I ran into an issue where an overlay widget used to display a background image in my main application window fails to display after changing to numix dark theme.  I do not belive this is a coding error on my part because it displays correctly in Ambience, but as soon as I switch to Numix light , or dark this is what I see: (Numix Dark [Left], Ambience [Right]) Is this a Numix support issue, Gtk3 issue?

[IMG]http://s23.postimg.org/yoj9txfe3/Numix_Problem.png[/IMG][IMG]http://s27.postimg.org/eucc5lx6r/Radiance_OK.png[/IMG]

this is a sniplet of my code

```
class MainWindow(Gtk.Window):
    def __init__(self):
        Gtk.Window.__init__(self, title='GMouse 600')
        self.set_position(Gtk.WindowPosition.CENTER)
        self.set_has_resize_grip(False)
        self.set_resizable(False)
        
        #overlay so we can put widgets ontop of background image
        self.overlay = Gtk.Overlay()
        self.add(self.overlay)
        self.background = Gtk.Image.new_from_file('./images/g600bg.png')
        self.overlay.add(self.background)
        
        #css stylesheet controls button apearance for keypad
        self.cssProvider = Gtk.CssProvider()
        self.cssProvider.load_from_path('./style/main.css')
        self.screen = Gdk.Screen.get_default()
        self.styleContext = Gtk.StyleContext()
        self.styleContext.add_provider_for_screen(self.screen, self.cssProvider, Gtk.STYLE_PROVIDER_PRIORITY_USER)
        
        #absolute positioning of widgets, because buttons have to be placed over background
        self.fixed = FixedWidget(self, 575, 120)
        
        #row 0
        self.fixed.add_button(' '*3,'g11', 12, 16)
        self.fixed.add_button(' '*3,'g14', 50, 8)
        self.fixed.add_button(' '*3,'g17', 90, 3)
        self.fixed.add_button(' '*3,'g20', 122, 1)
        #row 1
        self.fixed.add_button(' '*3,'g10', 15, 49)
        self.fixed.add_button(' '*3,'g13', 55, 43)
        self.fixed.add_button(' '*3,'g16', 95, 38)
        self.fixed.add_button(' '*3,'g18', 130, 34)
        #row 2
        self.fixed.add_button(' '*3,'g9', 23, 85)
        self.fixed.add_button(' '*3,'g12', 60, 81)
        self.fixed.add_button(' '*3,'g15', 100, 76)
        self.fixed.add_button(' '*3,'g16', 135, 72)
        self.overlay.add_overlay(self.fixed)
        self.show_all()
        #import pdb; pdb.set_trace()
```

---

