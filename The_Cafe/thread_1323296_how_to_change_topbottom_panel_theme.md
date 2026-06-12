---
title: "how to change top/bottom panel theme"
date: 2009-11-11
forum: The Cafe
---

### Post by redfoxkt on 2009-11-11
hello im sorry if this thread has already been posted i searched for it but didnt find. im trying to change the theme on the top and bottom panels for ubuntu running gnome desktop...i used emerald theme manager and after i reboot my window themes go back to wat they were and my panels never changed. thanks for the help..oh and is there a site i can go to, to get tuts on how to code linux and such i wana learn how to make small distros

---

### Post by Ex0suit on 2009-11-11
> **redfoxkt said:**
> hello im sorry if this thread has already been posted i searched for it but didnt find. im trying to change the theme on the top and bottom panels for ubuntu running gnome desktop...i used emerald theme manager and after i reboot my window themes go back to wat they were and my panels never changed. thanks for the help..oh and is there a site i can go to, to get tuts on how to code linux and such i wana learn how to make small distros

I'm not sure about the gnome panels, I'm sure someone else will, but if you want to learn how to create your own distros, then I think Linux From Scrath (LFS) has tutorials, but get familiar with Linux first before trying to make your own, good luck with your panels :)

---

### Post by SunnyRabbiera on 2009-11-11
Hmm, how were you theming your panels?
What did you do to them?
I just want to see what you did as I have no issues theming panels personally and want to see if you did anything fancy.

---

### Post by redfoxkt on 2009-11-11
> **SunnyRabbiera said:**
> Hmm, how were you theming your panels?
What did you do to them?
I just want to see what you did as I have no issues theming panels personally and want to see if you did anything fancy.
 
im sure im doing something wrong i added a theme called 105311-BlackFrame.emerald thats the file actually. but in order for me to get the themes to change had to enter a terminal command i dont remember but it might have been "emerald -- replace" or somthing. i rebooted a while ago to scan my windows partition with malwarebytes came back to ubuntu and themes went back to wat they was before...but while emerald was working it only replaced the window themes not the panels. and thanks for the suggestion of malwarebytes i think that was u that suggested it...found 3 infections >_<

---

### Post by redfoxkt on 2009-11-11
> **Ex0suit said:**
> I'm not sure about the gnome panels, I'm sure someone else will, but if you want to learn how to create your own distros, then I think Linux From Scrath (LFS) has tutorials, but get familiar with Linux first before trying to make your own, good luck with your panels :)

yeah im trying to find tuts on how to code and such first get used to all of ubuntus inside workings and possibly in the future make a live cd distro off of debian

---

### Post by FuturePilot on 2009-11-11
> **redfoxkt said:**
> im sure im doing something wrong i added a theme called 105311-BlackFrame.emerald thats the file actually. but in order for me to get the themes to change had to enter a terminal command i dont remember but it might have been "emerald -- replace" or somthing. i rebooted a while ago to scan my windows partition with malwarebytes came back to ubuntu and themes went back to wat they was before...but while emerald was working it only replaced the window themes not the panels. and thanks for the suggestion of malwarebytes i think that was u that suggested it...found 3 infections >_<

Emerald only themes the window borders. You need a GTK+ theme to theme panels and other things. You can find many GTK themes at [http://www.gnome-look.org/]("http://www.gnome-look.org/")

---

### Post by redfoxkt on 2009-11-11
> **FuturePilot said:**
> Emerald only themes the window borders. You need a GTK+ theme to theme panels and other things. You can find many GTK themes at [http://www.gnome-look.org/](http://www.gnome-look.org/)

what would i use to theme it ? I.E. what's the GTK equivalent to emerald theme and is there a better theme manager for the windows cause emerald didnt save the theme as i said when i rebooted it went back to wat it was

---

### Post by SunnyRabbiera on 2009-11-11
> **redfoxkt said:**
> what would i use to theme it ? I.E. what's the GTK equivalent to emerald theme and is there a better theme manager for the windows cause emerald didnt save the theme as i said when i rebooted it went back to wat it was

You mean emerald is not coming up in each session right?
This does not have to do with panels actually, you need to do some minor configuration.
First I suggest you install compizconfig settings manager:
[http://packages.ubuntu.com/karmic/compizconfig-settings-manager](http://packages.ubuntu.com/karmic/compizconfig-settings-manager)
Open up your compiz settings manager after its installed.
go to "window decoration"
in that window there is a box that says "command"
replace whatever is in there with emerald --replace
That should allow emerald to replace your normal metacity window border (metacity is the name of the default window border of ubuntu)

---

### Post by FuturePilot on 2009-11-11
> **SunnyRabbiera said:**
> You mean emerald is not coming up in each session right?
This does not have to do with panels actually, you need to do some minor configuration.
First I suggest you install compizconfig settings manager:
[http://packages.ubuntu.com/karmic/compizconfig-settings-manager](http://packages.ubuntu.com/karmic/compizconfig-settings-manager)
Open up your compiz settings manager after its installed.
go to "window decoration"
in that window there is a box that says "command"
replace whatever is in there with emerald --replace
That should allow emerald to replace your normal metacity window border (metacity is the name of the default window border of ubuntu)

Or better yet, just [click to install compizconfig settings manager]("apt://compizconfig-settings-manager")

---

### Post by SunnyRabbiera on 2009-11-11
> **FuturePilot said:**
> Or better yet, just [click to install compizconfig settings manager]("apt://compizconfig-settings-manager")

That too :D

---

### Post by redfoxkt on 2009-11-11
> **SunnyRabbiera said:**
> You mean emerald is not coming up in each session right?
This does not have to do with panels actually, you need to do some minor configuration.
First I suggest you install compizconfig settings manager:
[http://packages.ubuntu.com/karmic/compizconfig-settings-manager](http://packages.ubuntu.com/karmic/compizconfig-settings-manager)
Open up your compiz settings manager after its installed.
go to "window decoration"
in that window there is a box that says "command"
replace whatever is in there with emerald --replace
That should allow emerald to replace your normal metacity window border (metacity is the name of the default window border of ubuntu)

i already had compiz but i had to replace wat was in the command like u said with "emerald --replace" thanks...now how would i got about changing the panels i know i have to download GTK 2.0 themes but is there a manager to easly click on the theme and apply it to the panels ?

---

### Post by FuturePilot on 2009-11-11
> **redfoxkt said:**
> i already had compiz but i had to replace wat was in the command like u said with "emerald --replace" thanks...now how would i got about changing the panels i know i have to download GTK 2.0 themes but is there a manager to easly click on the theme and apply it to the panels ?

System > Preferences > Appearance. Just drag and drop the theme archive right onto the window.

---

### Post by redfoxkt on 2009-11-11
> **FuturePilot said:**
> System > Preferences > Appearance. Just drag and drop the theme archive right onto the window.

ok thanks for the help

---

