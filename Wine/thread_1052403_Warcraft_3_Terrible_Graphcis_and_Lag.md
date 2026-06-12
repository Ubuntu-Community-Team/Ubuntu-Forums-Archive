---
title: "Warcraft 3 Terrible Graphcis and Lag"
date: 2009-01-27
forum: Wine
---

### Post by Squegee on 2009-01-27
When I load W3 the graphics are terrible and there is about a 10 second lag time, I have no mouse and I have to use the keyboard to navigate.The graphics seem like they are from a developmental stage of W3, the colors are not right sometimes I can see the shapes without color and everything is pixely, I tested a game from the editor and my town hall and peasants were completely black. I am using Kubuntu 8.10 and a geforce fx 5200 graphics card. I am a noob to linux and wine and I dont know what to do, any help is appreciated 

Also how do you open W3 in a window and not in full screen?

---

### Post by budaslap on 2009-01-30
Well, it seems you have 2 problems here, both of them I have had to deal with.

first is your graphics situation. 

I found that running compiz did this to me, and I found a handy program called compiz-switch that lets you turn off compiz with a single click. (apt-get compiz-switch I think. I don't know about kubuntu as I'm using Ubuntu) 

Also I set WINE to run as a virtual desktop(Wine config > graphics tab > emulate a virtual desktop)

Finally create a shortcut to your WC3 on your desktop, right click on it and select properties. In the properties window under the basic tab in the "command" box add -opengl to the end of the text there, not in qoutes.

Should look like this 
*env WINEPREFIX="/home/dave/.wine" wine "C:\Program Files\Warcraft III\Frozen Throne.exe" -opengl*
Note: Don't copy and paste this, as it won't work for you unless your username happens to be dave . :P


Second is the running in windows, this is easy.
Just like before, you need to go to the properties menu for the WC3 shortcut, into the same command box in the basic tab, and add -windowed to the end. I would create a second shortcut for this, as it is very tedious to have to change the shortcut command every time you want to run in windowed or not. 

If you have WINE set to run as a virtual desktop, you wont be able to see your normal desktop as well. You don't NEED to make it a virtual desktop, it just makes it safe to ALT+Tab back and forth without messing up your graphics.  Making WINE run as a virtual desktop allows you to ALT + Tab out without messing up your game as well as the windowed WC3, you will just see the blank desktop that WINE creates.

Should look like this if you did both
*env WINEPREFIX="/home/dave/.wine" wine "C:\Program Files\Warcraft III\Frozen Throne.exe" -opengl -windowed*
Again, don't copy and paste this as it wont work for you.

---

### Post by RaiCoss on 2009-01-31
> **budaslap said:**
> Well, it seems you have 2 problems here, both of them I have had to deal with.

first is your graphics situation. 

I found that running compiz did this to me, and I found a handy program called compiz-switch that lets you turn off compiz with a single click. (apt-get compiz-switch I think. I don't know about kubuntu as I'm using Ubuntu) 

Also I set WINE to run as a virtual desktop(Wine config > graphics tab > emulate a virtual desktop)

Finally create a shortcut to your WC3 on your desktop, right click on it and select properties. In the properties window under the basic tab in the "command" box add -opengl to the end of the text there, not in qoutes.

Should look like this 
*env WINEPREFIX="/home/dave/.wine" wine "C:\Program Files\Warcraft III\Frozen Throne.exe" -opengl*
Note: Don't copy and paste this, as it won't work for you unless your username happens to be dave . :P


Second is the running in windows, this is easy.
Just like before, you need to go to the properties menu for the WC3 shortcut, into the same command box in the basic tab, and add -windowed to the end. I would create a second shortcut for this, as it is very tedious to have to change the shortcut command every time you want to run in windowed or not. 

If you have WINE set to run as a virtual desktop, you wont be able to see your normal desktop as well. You don't NEED to make it a virtual desktop, it just makes it safe to ALT+Tab back and forth without messing up your graphics.  Making WINE run as a virtual desktop allows you to ALT + Tab out without messing up your game as well as the windowed WC3, you will just see the blank desktop that WINE creates.

Should look like this if you did both
*env WINEPREFIX="/home/dave/.wine" wine "C:\Program Files\Warcraft III\Frozen Throne.exe" -opengl -windowed*
Again, don't copy and paste this as it wont work for you.

Yeah setting it to OpenGL should make it like 3 times faster.

---

### Post by binbash on 2009-01-31
disable compiz and run the war3 with -opengl as mentioned above.It will be fine

---

### Post by Squegee on 2009-02-01
I used virtual desktop and opened with -opengl. The color is right but it is still lagy. I installed compiz-switch but it doesn't work. The icon just bounces then it stops, I also installed Compiz Fusion, which works but when i disable compiz it is still lagy

---

### Post by Squegee on 2009-02-01
I am good, I just messed around with my drivers and I got everything to work thank you very much for your help

---

