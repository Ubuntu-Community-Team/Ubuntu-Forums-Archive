---
title: "Screen Shot Application?"
date: 2019-05-21
forum: Ubuntu, Linux and OS Chat
---

### Post by makitso on 2019-05-21
I am a big fan of the shutter application (although I hate the .386 libraries required to run it).  

The primary reason is that after capturing an area of the screen I can immediately send it to the printer -- simple workflow.
I have tried several other apps including gnome-screenshot, flameshot but all require that you copy the image to the clipboard and then put it into an app to print.

Am I missing something obvious?
Any other apps I have missed?

---

### Post by TheFu on 2019-05-21
I use **import**, which is part of ImageMagick  tools.  It would be trivial to setup a tiny script to capture something, drop the file into /tmp/, print it, then delete it.  Just need the correct printer filter installed from CUPs.

With **xdotool**, you could assign a key just for this purpose.  Perhaps the "PrintScn" button?  Plus, import lets you select the rectangle to be included.

Also, beware that Wayland breaks many screen/window capture programs.

---

### Post by maglin2 on 2019-05-21
Spectacle has a Print option under Save & Exit (Ctrl+P). I've only ever used it to print to pdf.
It would likely pull in quite a few kde depenencies to your Budgie desktop.
(Edit - curiosity got the better of me - yes it will print a captured area directly to paper.)

---

### Post by makitso on 2019-05-22
Turns out that the solution was right under my nose so to speak.  
I use Ubuntu Budgie and there is an Screen shot applet.  I installed it and by clicking on the captured image it opens gThumbs with the image.  Then a Ctl P and it prints.

---

