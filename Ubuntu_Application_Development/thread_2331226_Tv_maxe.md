---
title: "Tv maxe"
date: 2016-07-19
forum: Ubuntu Application Development
---

### Post by Seth-666 on 2016-07-19
I installed tv-maxe, works fine, but in terminal when i start it , i recive i little error, how can i repaire it ?

```
sudo add-apt-repository ppa:trebelnik-stefina/tv-maxe
sudo apt-get update
sudo apt-get install tv-maxe
```
```
tvmaxe 
[B]Init petrodava...
tvmaxe.py:2656: GtkWarning: gtk_menu_attach_to_widget(): menu already attached to GtkMenuItem
  self.gui.get_object('menuitem41').set_submenu(radios)
tvmaxe.py:1327: Warning: Source ID 516 was not found when attempting to remove it
  gobject.source_remove(self.cursorTimeout)[/B]
SopCast: Incoming port: 23250
SopCast: Outgoing port: 19380
tvmaxe.py:1327: Warning: Source ID 766 was not found when attempting to remove it
  gobject.source_remove(self.cursorTimeout)
tvmaxe.py:1327: Warning: Source ID 1046 was not found when attempting to remove it
  gobject.source_remove(self.cursorTimeout)
```

---

### Post by michael210 on 2016-07-19
Locate the file tvmaxe.py, open it and search this lines:
> 
        self.gui.get_object('menuitem38').remove_submenu()
        self.gui.get_object('menuitem38').set_submenu(radios)
        self.gui.get_object('menuitem41').remove_submenu()
        self.gui.get_object('menuitem41').set_submenu(radios)
        self.gui.get_object('menuitem39').remove_submenu()
        self.gui.get_object('menuitem39').set_submenu(tvs)


and comment the `[COLOR=#000000]*menuitem41'*[/COLOR]:
> 
        self.gui.get_object('menuitem38').remove_submenu()
        self.gui.get_object('menuitem38').set_submenu(radios)
        # self.gui.get_object('menuitem41').remove_submenu()
        # self.gui.get_object('menuitem41').set_submenu(radios)
        self.gui.get_object('menuitem39').remove_submenu()
        self.gui.get_object('menuitem39').set_submenu(tvs)


Close and open your APP again.

---

### Post by Seth-666 on 2016-07-20
thx you

---

