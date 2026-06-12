---
title: "Tkinter clear screen"
date: 2013-07-11
forum: Ubuntu Application Development
---

### Post by Iain Banks on 2013-07-11
```

from tkinter import *  rGui = Tk() rGui.title("Recipe's") rGui.geometry("400x300") rGui.resizable(0,0)  rNameLabel = Label(rGui, text="What is your Recipe called?").grid(row=1, column=1) rEnt = Entry(rGui) rEnt.grid(row=1, column=2)   def RecipeName():     f = open(rEnt.get()+'.txt','a')     f.write("Recipe name: "+str(rEnt.get())+"\n")     f.close() rConButton = Button(rGui, text="Confirm", command=RecipeName).grid(row=1, column=3)


```  Hello, this code here opens a GUI with buttons. Now once the user has  input their recipe name I'd like it to clear the screen so I can add  more buttons. Now I&#8217;m not sure how to get the grid_forget working so if  someone could edit the code so it forgets it so I can look at it for  next time I'd appreciate it.

---

