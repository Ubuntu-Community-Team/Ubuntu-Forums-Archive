---
title: "Zorin OS 12 Tap-To-Click not working"
date: 2017-03-12
forum: Ubuntu/Debian BASED
---

### Post by goostech on 2017-03-12
[COLOR=#000000][FONT=Sans]i went to the settings there is no option for me to enable tap to click is there a way i can add a command into certain folders and or registries to auto run the terminal command "synclient TapButton1=1 TapButton2=3 TapButton3=2" when the computer boots, or make a terminal command to make the command to auto run, its annoying to open a terminal every single time i boot and type in the command letter by letter is there any way i can fix this my spcecs are as follows

CPU: Core 2 Duo T9500 at 2.60 GHz
RAM: 4GB of DDR2
GPU: Quadro FX 570M 256MB
Compuer Model: Lenovo Thinkpad T61P[/FONT][/COLOR]

---

### Post by vasa1 on 2017-03-12
You can add commands to your autostart. How you do so depends on your desktop environment. I have these lines in my autostart:```
synclient VertEdgeScroll=0
synclient RTCornerButton=0
synclient RBCornerButton=0
synclient LBCornerButton=0
synclient LTCornerButton=0
```

---

### Post by goostech on 2017-03-12
i use Zorin OS 12 and i think it uses the Gnome desktop enviroment

---

### Post by vasa1 on 2017-03-12
Run the command```
locate autostart | grep home
``` and post the output here between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags. That should tell us where your autostart file is (maybe).

---

### Post by goostech on 2017-03-12
ok so this showed up
```

giovanni@thinkpad-t61p:~$ locate autostart | grep home
/home/giovanni/.config/autostart
/home/giovanni/.config/autostart/geary-autostart.desktop
/home/giovanni/.config/autostart/psensor.desktop
giovanni@thinkpad-t61p:~$
```

ok i followed the first line of code (/home/giovanni/.config/autostart) thru the file explorer and im inside the "autostart" folder now what?

---

### Post by vasa1 on 2017-03-12
> **goostech said:**
> ok so this showed up
```

giovanni@thinkpad-t61p:~$ locate autostart | grep home
/home/giovanni/.config/autostart
...
```
Now please post the contents of */home/giovanni/.config/autostart* **using code tags** as I requested :)

Edit: Do you see a file called "autostart" inside the autostart folder? Post the contents of *that* file.

---

### Post by goostech on 2017-03-12
Here you go.[ATTACH=CONFIG]274104[/ATTACH]

---

### Post by vasa1 on 2017-03-12
Okay, so you don't have an autostart file in there.

Please run
env | grep XDG_CURRENT_DESKTOP
and
echo $DESKTOP_SESSION

and post that output. Someone may recognize your system and offer specific advice.

---

### Post by goostech on 2017-03-12
here you go.[ATTACH=CONFIG]274105[/ATTACH][ATTACH=CONFIG]274105[/ATTACH]

---

### Post by vasa1 on 2017-03-12
What do you see when you run *gnome-session-properties*?

---

### Post by goostech on 2017-03-12
my laptop loads web pages so slow your reply never showed up im so sorry

this showed up its so edit all the apps that start up.[ATTACH=CONFIG]274108[/ATTACH]

---

### Post by vasa1 on 2017-03-12
So does "Add" allow you to add your synclient command?

---

### Post by goostech on 2017-03-12
Yup :D[ATTACH=CONFIG]274109[/ATTACH]

It works!
Thank You

---

