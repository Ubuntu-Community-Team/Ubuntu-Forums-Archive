---
title: "Python 3 program logic ok, some unexpected screen behaviour"
date: 2013-04-28
forum: Ubuntu Application Development
---

### Post by vmsda on 2013-04-28
Trying to learn Python 3. The following program logic seems ok, but if I remove the *print*() from the **motion** function, behaviour becomes erratic. Any hints, please?

```
#!/usr/bin/env python3
# -*- coding:Utf-8 -*-
from tkinter import *
from tkinter import ttk
from random import randrange

class OvalsCanvas(Frame):
    
    """ Exercise with images on labels on canvas windows. On canvas, draw some\
ovals, compute their centres; each oval raised when image label lands (adapted\
from Apprender a programmer avec Python 3, by Gerard Swinnen)"""
    
    def __init__(self, boss, width=400, height=300, bg='white', bd=2,\
                 relief=SUNKEN):
        Frame.__init__(self, boss, bd=bd, relief=relief)
        self.can = Canvas(self, width=width-20, height=height-20, bg=bg, bd=1)
        self.can.grid(row=0, column=0)

class MainWindow(Tk):
    def __init__(self):
        Tk.__init__(self)
        self.lb = Label(text ='Jumping Icon')
        self.lb.pack(pady=3)
        playGround = OvalsCanvas(self, width=500, height=300, relief=SOLID)
        playGround.pack(expand=YES, fill=BOTH, padx=6, pady=6)
        self.can = playGround.can
        clrs = ('sienna','maroon','brown','pink','tan','wheat','gold','orange',\
                'plum','red','khaki','indian red','thistle','firebrick',\
                'salmon','coral','yellow','cyan','blue','green')
        self.oval_centers = []
        self.oval_ids = []
        for r in range(10):              # build the ovals
            x1, y1 = randrange(0,500)/2, randrange(0,300)/2
            x2, y2 = randrange(0,500), randrange(300)
            colour = clrs[randrange(20)]
            this_oval = self.can.create_oval(x1, y1, x2, y2,\
                                                      fill=colour,\
                                                      outline='black')
            self.oval_ids.append(this_oval)   # keep id
            this_center = [round((x1+x2)/2), round((y1+y2)/2)]
            self.oval_centers.append(this_center)   # keep pos for icon
        self.tux = PhotoImage(file='/home/vasco/gif/Mini-babytux.gif')
        self.lbl = Label(bg='white', image=self.tux)
        
    def anim(self):
        x, y = 250, 150            # icon starting positon
        self.lbltux = self.can.create_window(x, y, window=self.lbl) # first tux
        for addr, id in zip(self.oval_centers, self.oval_ids):
            x1, y1 = addr[0], addr[1]
            dx = x1 - x
            dy = y1 - y
            self.motion(dx, dy)     # call to move icon to new position
            self.can.tag_raise(id)  # raise respective oval
            x, y = x1, y1
        self.after(1500, self.anim)

    def motion(self, dx, dy):
        print(dx, dy, end='')
        self.can.move(self.lbltux, dx, dy)
        self.after(1000)
        return
        
if __name__ == "__main__":
    app = MainWindow()
    app.anim()
    app.mainloop()

```

---

### Post by linuxonbute on 2013-04-30
Shouldn't
```

from tkinter import ttk

```
be
```

from ttk import *

```

---

