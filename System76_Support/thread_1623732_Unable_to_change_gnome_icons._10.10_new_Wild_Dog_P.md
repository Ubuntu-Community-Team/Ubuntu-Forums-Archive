---
title: "Unable to change gnome icons. 10.10 new Wild Dog Performance"
date: 2010-11-17
forum: System76 Support
---

### Post by Mike Buksas on 2010-11-17
Hello, System 76 support!

I have a brand-new Wild Dog performance with an odd Gnome problem. I can't change the icons for any of the themes. E.g. under System->Preferences->Appearance. Edit a theme and select an icon set.

I can change everything else, e.g. the Controls, Colors, Window borders and Pointer. But not the icons.

Here's some of the things I tried already: Logging out/in. Restarting. Installing new themes. Installing new icon sets. Pulling hair. Swearing. 

Please help. The icons I'm stuck with are kinda ugly.

Thanks.

---

### Post by isantop on 2010-11-17
Are they the default icons or are they different? Could you take a screen shot with PrtSc?

Also, have you ever been able to change the icons on this system in 10.10?

---

### Post by Mike Buksas on 2010-11-17
I've attached the screenshot. I don't recognise the particular icon set.

This problem appeared the first time I logged into the machine. Occasionally, I'll get the correct set of icons when logging in. Other times, it reverts back to this one.

Thanks for your help.

---

### Post by Flyers2391 on 2010-11-23
I think I've seen that icon set before when there was a problem loading some gnome settings.  I can't remember exactly but I know that I saw a pop-up message about it on boot.  It eventually went away on a reboot so I never troubleshot it further but maybe looking at gnome settings could help.

---

### Post by isantop on 2010-11-23
Those look like the default gtk icons. Do you have the proprietary Nvidia Drivers loaded?

---

### Post by Mike Buksas on 2010-11-23
The problem seems to have auto-resolved. I can change icon sets, see the results immediately, and the changes persist even after logout/login or restart.

So, this is embarrassing, but in a good way. 

Thanks for the suggestions.

Mike

---

### Post by cecilrhayduke on 2010-11-28
Install lxappearance.  For some reason, that will change the icon themes.  I was stuck with gnome default also.

---

### Post by haggan on 2010-12-07
I had the same problem installing LXAppearance help me.

---

### Post by joesnose on 2010-12-22
i am also experiencing this problem, using 10.10 64bit, was fine then all of a sudden me icons have changed and changing the theme seemingly has no effect! what gives? did anyone find a solution yet or is it jus affecting a mere handfull of folks.

edit: sorry i think i have posted in the wrong section, i don't even know what system 76 is! but i am having the problem.

---

### Post by Maverick7687 on 2011-01-06
I also have a similar problem. Seems like every time I turn my laptop on (Not sure about how long the inactivity has to be) it will load with that default icon set and theme, if I log out, or reboot, it will load the settings I have defined. Rebooting or logging out and back in has worked consistently, just a nuisance that I would like to resolve.

---

### Post by isantop on 2011-01-07
This bug is actually related to the Nvidia Driver. To get it fixed without logging out, press Alt+F2, then enter this in the dialog box:
```
killall -9 gnome-settings-daemon && gnome-settings-daemon
```
Ironically, this bug only appears on "fast" systems. At least there's good news there, right?

---

### Post by Maleiro on 2011-03-18
> **isantop said:**
> This bug is actually related to the Nvidia Driver. To get it fixed without logging out, press Alt+F2, then enter this in the dialog box:
```
killall -9 gnome-settings-daemon && gnome-settings-daemon
```Ironically, this bug only appears on "fast" systems. At least there's good news there, right?

Hi, i was having a similar problem, i couldn't change for any new icon set i had installed prior to system installation, but i could change between the ones that come with 10.10. Them i tried the above command and now i can't even change to the ones i could...Anyone have any idea on this. Ah and yes i have a Nvidia GFX card.

---

### Post by isantop on 2011-03-18
Try running the two parts of the command individually. So, in the Alt+F2 dialog, run:

```
killall -9 gnome-settings-daemon
```

Then open it back up and run:

```
gnome-settings-daemon
```

Did that help?

---

### Post by Maleiro on 2011-03-18
No mate it's the same...now not only the icons but the hole theme doesn't change...

---

### Post by isantop on 2011-03-21
Can you try the same thing from the Terminal? Send any output here so we can have a look.

---

