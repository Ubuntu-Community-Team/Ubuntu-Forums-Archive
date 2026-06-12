---
title: "A little script to change the xorg.conf driver to &quot;vesa&quot;"
date: 2006-07-07
forum: The Cafe
---

### Post by IYY on 2006-07-07
Seems like this is a very common operation that we tell newbies to do, and it scares some people (requires editing a file). Why don't we just give them a simple script like...

```

#!/bin/sh

file="/etc/X11/xorg.conf"
cp $file $file.bak
x=`grep "Section \"Device\"" -A 5 $file | grep Driver`
cat $file | sed s/"$x"/"\tDevice\t\t\"vesa\""/ > $file.2
cp $file.2 $file

```

Nothing fancy... Just replace whatever video driver is currently selected with the safe 'vesa'.

Can even stick a 

```

echo "To restart your X server automatically, type yes. This will shut down all of your programs."
read x
if [ $x = "yes" ]
then
/etc/init.d/gdm restart
fi

```

in the end there, and everything would be completely automated.

---

### Post by LordRaiden on 2006-07-07
Great idea. Also should be able to switch to /etc/init.d/kdm if the user runs KDE.

---

### Post by Iandefor on 2006-07-07
This checks to see if it's running GNOME or KDE, then acts accordingly.

```
if ps -e | grep gnome-panel && ps -e | grep metacity ; then 
sudo /etc/init.d/gdm restart
else
sudo /etc/init.d/kdm restart
fi
```

---

### Post by IYY on 2006-07-07
Or just...

```
if ps -e | grep gdm ; then 
sudo /etc/init.d/gdm restart
else
sudo /etc/init.d/kdm restart
fi
```

---

### Post by Iandefor on 2006-07-07
> **IYY said:**
> Or just...

```
if ps -e | grep gdm ; then 
sudo /etc/init.d/gdm restart
else
sudo /etc/init.d/kdm restart
fi
``` Riight... cause that just detects what's actually running, instead of making assumptions based on what happens to be running.

Works better, yeah :).

---

### Post by LordRaiden on 2006-07-07
Don't know about xfce? Does it run gdm as well?

---

### Post by tseliot on 2006-07-07
> **LordRaiden said:**
> Don't know about xfce? Does it run gdm as well?
Yes it does

---

### Post by tseliot on 2006-07-07
> **IYY said:**
> Or just...

```
if ps -e | grep gdm ; then 
sudo /etc/init.d/gdm restart
else
sudo /etc/init.d/kdm restart
fi
```

I used this step in the previous releases of my Envy script but (I don't know why) using "if ps -e | grep gdm ; then..." when there is a problem (e.g. a driver mismatch or a problem with the Xserver in general) Kubuntu's splash spawns up and remains idle (it doesn't freeze though).

EDIT: I'm not saying that the problem takes place every time you use those commands but I think it's better if the script works in as many cases as possible.

Therefore I hope you will consider mine as constructive (instead of sterile) criticism.

---

### Post by Wallakoala on 2006-07-07
> **Iandefor said:**
> This checks to see if it's running GNOME or KDE, then acts accordingly.

```
if ps -e | grep gnome-panel && ps -e | grep metacity ; then 
sudo /etc/init.d/gdm restart
else
sudo /etc/init.d/kdm restart
fi
```

The problem whith that one is if the user isn't using gnome-panel in gnome, which some people don't. The bigger problem is if they are using a different window manager that is not metacity. A lot of people do that (compiz, openbox, etc.)

---

### Post by Iandefor on 2006-07-07
> **Wallakoala said:**
> The problem whith that one is if the user isn't using gnome-panel in gnome, which some people don't. The bigger problem is if they are using a different window manager that is not metacity. A lot of people do that (compiz, openbox, etc.) Yeah, see IYY's response right after that... and then my own response.

---

### Post by rexmollc on 2008-03-17
Look I don't need a script could you guys just give me  the command line entries and a quick how-to on the editor?   I just need to change the video back to a safer VESA mode so I can access the desktop....   
Please email me at   [email]rexmollc@sbcglobal.net[/email]    THANK YOU I really really appreciate ur help!

---

