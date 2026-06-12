---
title: "Applications plugin, submenus"
date: 2007-06-09
forum: Ubuntu System Panel
---

### Post by ADRez on 2007-06-09
As it seems the development of usp is a little bit stopped, so I've started trying to show submenus in applications, but haven't been able to find how to create them in python. I looked at usp's code, but the popup menus it uses are defined "statically" (menu always shows "add to favourites" or "unmount" or something like this) and the font they use is smaller; I wanted something like the menus that are shown in gnome's Main menu applet. Someone knows how they are created in python?

PD: I attach what I've been able to do until now

---

### Post by Quikee on 2007-06-09
> **ADRez said:**
> As it seems the development of usp is a little bit stopped, so I've started trying to show submenus in applications, but haven't been able to find how to create them in python. I looked at usp's code, but the popup menus it uses are defined "statically" (menu always shows "add to favourites" or "unmount" or something like this) and the font they use is smaller; I wanted something like the menus that are shown in gnome's Main menu applet. Someone knows how they are created in python?

PD: I attach what I've been able to do until now

You can create menu programmatically if you wish. I have created a "helper" function that can do it for you if you provide the correct data:

```

def showMenuWith(event, menuItems):
	menu = gtk.Menu()
	for menuItem in menuItems:
		item = gtk.MenuItem(menuItem[0], True)
		item.show()
		if menuItem[2] is None:
			item.connect( "activate", menuItem[1])
		else:
			item.connect( "activate", menuItem[1], menuItem[2])
		menu.add(item)
	menu.popup( None, None, None, event.button, event.time )

```

to use it you have to provide the event which usually available if you do it in a "buttonClicked" method. The second thing you have to provide is a structure like this one:

```

menu = [['popup description', self.callbackMethod, parameter], 
  ['popup description 2', self.callbackMethod2, parameter] ]
showMenuWith(event, menu)

```

It would be cool if you would extend it to also show an icon in the menu. =)

---

### Post by ADRez on 2007-06-11
^ Thanks! Until now, I've been able to show items with icons, it's getting good...

---

### Post by ADRez on 2007-06-18
I'm blocked because I don't know how to get a button's position (left, width and top) to show submenus at button's right. Someone knows the function / property to know them?

---

### Post by Malac on 2007-06-18
> **ADRez said:**
> I'm blocked because I don't know how to get a button's position (left, width and top) to show submenus at button's right. Someone knows the function / property to know them?
```
        MyRect = BTN.get_allocation()
        print MyRect.x, MyRect.y, MyRect.width, MyRect.height,

``` where BTN is the widget, in this case a button, that has called the "clicked" or "released" routine.
Gives a gtk.gdk.Rectangle (MyRect) where:
```
"x"        Read-Write    The X coordinate of the top left corner of the rectangle.
"y"        Read-Write    The Y coordinate of the top left corner of the rectangle.
"width"    Read-Write    The width of the rectangle.
"height"   Read-Write    The height of the rectangle.
```

Hope this helps.

---

### Post by ADRez on 2007-06-19
Thanks!
It was helpful, although I need to know usp's position too to know the real button position on the screen. I attach the applications.py file as I have it know

---

