---
title: "Patches for alpha"
date: 2007-01-05
forum: Ubuntu System Panel
---

### Post by DBO on 2007-01-05
Some applications wont launch out of the normal menus.  Just a simple issue with failing to split things properly.

Fix is fairly simple:
line 347 in applications.py reads:

> ItemButton.connect( "button_press_event", self.ButtonClicked, [PlaceExec] )

it should read:

> ItemButton.connect( "button_press_event", self.ButtonClicked, PlaceExec.split() )
Now we all know hes going to come in and mention he fixed that two days ago =P  *always late is DBO*
This is the only major issue I have come across so far, as I come across more (or if I do) I will put my patches in this thread.

---

### Post by Strash on 2007-01-05
It's in application**s**.py
It's take me a while to find this file, so I try to help... :D 

Thank's for the patch

---

### Post by hanzomon4 on 2007-01-08
I made the change but I still have apps refusing to launch from usp

---

### Post by chanders on 2007-01-08
> **hanzomon4 said:**
> I made the change but I still have apps refusing to launch from usp

Can you provide a little more information on the apps? How are they installed? Are you using a custom .desktop file? A custom launcher??

---

### Post by hanzomon4 on 2007-01-08
I've noticed it with a few apps. [list][*]urxvt - custome .desktop(worked with the old usp)[*]Brasero - installed via synaptic[/list]
I tried running usp in a window and clicking on the non-launching apps but that gave me nothing...

---

### Post by perfran on 2007-01-09
Brasero does not work either for me, even with the patch above.:-k

---

### Post by hanzomon4 on 2007-01-09
[list][*]This is what I changed my 347 line to>                         ItemButton.connect( "button_press_event", self.ButtonClicked, PlaceExec.split() )It still doesn't work but maybe I missed something

[*]This a cut and past of DBO's edit > ItemButton.connect( "button_press_event", self.ButtonClicked, PlaceExec.split() ) Seems to match[/list]

---

### Post by DBO on 2007-01-12
> **hanzomon4 said:**
> I've noticed it with a few apps. [list][*]urxvt - custome .desktop(worked with the old usp)[*]Brasero - installed via synaptic[/list]
I tried running usp in a window and clicking on the non-launching apps but that gave me nothing...

can you give me your urxvt desktop file please

---

### Post by hanzomon4 on 2007-01-12
No can do I had to reinstall edgy(new hard drive) and usp-alpha won't work anymore(it's just blank)

---

### Post by DBO on 2007-01-13
mmmmm anything when you run it from a terminal?  usp run-in-window

---

### Post by Malac on 2007-01-15
Thought I'd post this here chanders, et al to save time.
Here's a patched uspuser.py file which allows it to be minimized to the sidepane.
Just extract it over the original in /usr/lib/python2.4/site-packages/usp/plugins.

---

### Post by chanders on 2007-01-15
Cool! It works great..

---

### Post by Malac on 2007-01-15
A quick patch for USP not hiding if you choose "Preferences" from the right click menu.
Around Line 438 (in my copy) of /usr/bin/usp
Just change:
```
    def uspconfig(self,event,data=None):
        os.system("uspconfig &")
```to this:
```
    def uspconfig(self,event,data=None):
        os.system("uspconfig &")
        if self.mainwin.pinmenu == False:
            self.mainwin.wTree.get_widget("window1").hide()
            self.toggle.set_active(False)
```Also a patch for the applications.py that needs testing to check it now takes notice of the appname_font_size and appgeneric_font_size gconf/uspconfig values.

EDIT: I forgot to include a slightly changed easybuttons.py in the first tar file, so I've uploaded a new one.

---

