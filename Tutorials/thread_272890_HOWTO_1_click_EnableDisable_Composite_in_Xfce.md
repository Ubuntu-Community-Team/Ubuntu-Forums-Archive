---
title: "HOWTO: 1 click Enable/Disable Composite in Xfce"
date: 2006-10-07
forum: Tutorials
---

### Post by Emanuel Felipe on 2006-10-07
[SIZE="5"][COLOR="Navy"]**Before we start...**[/COLOR][/SIZE]

**First of all, what is "Composite" and how to get working?**
*[http://www.ubuntuforums.org/showthread.php?t=75527]("http://www.ubuntuforums.org/showthread.php?t=75527")*

**So, why Enable/Disable the Xfce compositor?**
*Here I got a problem: When the composite is enabled: 3d acceleration wont works.*

As I want to use 3d acceleration and have nice effects, I found a way to not have both together, but easily switch composite on/off. This [post]("http://www.ubuntuforums.org/showpost.php?p=992618&postcount=3")  gimme the idea to create this howto.

[SIZE="5"][COLOR="Navy"]**Lets begin:**[/COLOR][/SIZE]

**[SIZE="3"]1.[/SIZE]** Create a file called **composite-on** on **/usr/bin** (you can replace **nano** with your favorite text editor):

```
sudo nano /usr/bin/composite-on
```

**[SIZE="3"]2.[/SIZE]** Fill that with the following:
```
#!/bin/bash

killall xfwm4 && xfwm4 --compositor=on &
exit

```

**[SIZE="3"]3.[/SIZE]** Create a second file called **composite-off** in **/usr/bin** too (you can replace **nano** with your favorite text editor):

```
sudo nano /usr/bin/composite-off
```

**[SIZE="3"]4.[/SIZE]** Fill with the following:

```
#!/bin/bash

killall xfwm4 && xfwm4 --compositor=off &
exit

```

**[SIZE="3"]5.[/SIZE]** Now make then executable:

```
sudo chmod +x /usr/bin/composite-on /usr/bin/composite-off
```

**[SIZE="3"]6.[/SIZE]** Time to 1 click switch, right click on your panel and choose **Add New Iten** (Dont know if is exactly that, my system is in pt_BR) choose the first option **Launcher** (dont know exactly again) and then click **add**.

You can name it yourself, and choose a nice icon too (the icons I used are attached at the end of the post), just put **composite-on** in the **command** option and that will be the turn on icon.

Do that twice, but in the second put **composite-off** in the **command** camp.

[SIZE="5"][COLOR="Navy"]**Thats done...**[/COLOR][/SIZE]

Now you got an easy on/off switcher for composite in xfce without have to restart X. Hope that this will help someone...

*Tips, questions and comments will be apreciated, thats just my first howto. And sorry for my bad english, I need to pratice it more :p *

---

### Post by Emanuel Felipe on 2006-10-07
any comment? :neutral:

---

### Post by trincamckee on 2006-10-15
I was wondering for a while how to disable/enable composite on xfwm...
Now i can easly switch composite and use opengl apps without that annoying transparency, tank you for this nice how-to.
Take care.

---

### Post by Wangsta on 2007-01-01
so now that i have it turned on, how do i activate it's effects?

---

### Post by 1337 on 2007-07-13
Great work, this is exactly what I was looking for :)

---

### Post by RubenGarcia on 2008-10-04
> **Emanuel Felipe said:**
> any comment? :neutral:

There is one caveat with your approach. When you disable compositing with the script, xfce-settings-show won't show the composite window to reenable them, they must be reenabled also by script.

I just found another approach:

Write a script which parses 
$(HOME)/.config/xfce4/mcs_settings/wmtweaks.xml
and changes the line
 <option name="Xfwm/UseCompositing" type="int" value="0"/>
to 
 <option name="Xfwm/UseCompositing" type="int" value="1"/>
or viceversa.

Then 
killall -USR1 xfce-mcs-manager

This way you don't end and restart the process, so it should be faster, and xfce-setting-show is not affected, since --compositor=off is never used.

---

### Post by vor0nwe on 2010-06-07
In Xubuntu 10.04 (Lucid Lynx), in Settings / Settings Editor, select 'wfwm4' and 'General / use_compositing', click the 'edit' button, check the 'Enabled' button and click 'Save'.

Works perfectly for me!

---

### Post by TheReg on 2012-02-28
> **vor0nwe said:**
> In Xubuntu 10.04 (Lucid Lynx), in Settings / Settings Editor, select 'wfwm4' and 'General / use_compositing', click the 'edit' button, check the 'Enabled' button and click 'Save'.

Works perfectly for me!


Works for me too. Thanks for this thread all!

---

### Post by DoritosBR on 2012-05-11
Great solution.
Composite is awesome, but kill performance in games.

BTW, you can achieve the same thing (at least in Xubuntu 12.04) with those commands:

xfwm4 --compositor=on --replace &
xfwm4 --compositor=off --replace &

---

### Post by Jose Catre-Vandis on 2012-05-14
I believe this is the best way to do it:

You can do this from the command line and / or create a launcher to turn it on and off if this is the problem.

To turn off
```
xfconf-query --channel=xfwm4 --property=/general/use_compositing --set=false
```

To turn on
```
xfconf-query --channel=xfwm4 --property=/general/use_compositing --set=true
```


Just show the flexibility of linux/xfce 5 different ways to do the same thing :)

---

